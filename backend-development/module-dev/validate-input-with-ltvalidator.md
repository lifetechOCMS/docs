# Validate Input with LtValidator

[Previous](handle-http-requests-with-ltrequest.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](return-api-responses-with-ltresponse.md)

*Section: Working with Core Services (MdLt)*

## Purpose

`LtValidator` is a LifeTechOCMS core service for checking submitted data against validation rules. Validate incoming HTTP parameters **before passing them to a module Service or performing other operations**. `LtRequest` already collects incoming request parameters as object properties, so it can also validate those values directly.

**Recommended flow:** `HTTP request → LtRequest → validation → Controller → Service → Model` (the Controller normally initiates the validation step before calling its Service).

For the full API and method signatures, see [LtValidator — Developer Guide](../../appcore/LtValidator.md) and [LtRequest — Developer Guide](../../appcore/LtRequest.md).

## Supported validation rules

The current `MdLt/Services/LtValidator.php` implementation supports the following rules:

| Rule | Purpose | Example |
| --- | --- | --- |
| `required` | Reject an empty value | `'name' => 'required'` |
| `min:N` | Require at least N characters | `'name' => 'required|min:2'` |
| `max:N` | Limit to N characters | `'name' => 'required|max:100'` |
| `email` | Require a valid email address | `'email' => 'required|email'` |
| `numeric` | Require a numeric value | `'age' => 'required|numeric'` |

Use `|` to combine rules for one field. These are the rules confirmed in the current source. Do not assume rules such as `unique`, `confirmed`, `integer`, or `between` are implemented without checking the installed framework version.

## Option 1: Validate incoming HTTP parameters with LtRequest

The simplest approach in a module Controller is to construct `LtRequest` and call its public `validateRequest()` method. This method collects the request object's public properties (excluding `method`) and delegates validation to `LtValidator`.

```php
<?php

namespace Lt\Modules\MdStudent\Controllers;

use Lt\Modules\MdLt\Services\LtRequest;
use Lt\Modules\MdStudent\Services\TbStudentService;

class TbStudentController
{
    public function store()
    {
        $request = new LtRequest();

        // Validate HTTP input before calling the Service.
        $request->validateRequest([
            'studentName' => 'required|min:2|max:100',
            'email'       => 'required|email',
            'age'         => 'required|numeric'
        ]);

        $service = new TbStudentService();
        return $service->store();
    }
}
```

This is an **illustrative `MdStudent` Controller**, not an extract from MdBlog. It assumes `TbStudentService::store()` is implemented and uses the same submitted request. The service still needs to enforce business rules, permissions, and database constraints.

**How it works:**

1. `new LtRequest()` reads incoming HTTP parameters.
2. `validateRequest()` applies the supplied rules to the request values.
3. When the data passes, execution continues to `TbStudentService::store()`.
4. When validation fails, the current validator emits JSON and terminates execution; the Service call is not reached.

For `POST`, `LtRequest` reads `$_POST`; for `GET`, it reads `$_GET`; for `PUT`, `PATCH`, and `DELETE`, it reads the raw request body and parses JSON or URL-encoded input. Check your request's `Content-Type` and the installed implementation when testing.

## Option 2: Validate an array directly with LtValidator

Use `LtValidator::validate()` when you have an array of data rather than relying on the request object's built-in validation method.

```php
<?php

use Lt\Modules\MdLt\Services\LtRequest;
use Lt\Modules\MdLt\Services\LtValidator;

$request = new LtRequest();

$data = [
    'studentName' => $request->studentName ?? null,
    'email'       => $request->email ?? null,
];

LtValidator::validate($data, [
    'studentName' => 'required|min:2|max:100',
    'email'       => 'required|email'
]);

// Continue with the authorised operation only after validation passes.
```

`LtValidator::validate(array $data, array $rules)` is **static**: call it directly on the class, without `new LtValidator()`.

## Practical MdBlog example: validate a category before saving

MdBlog registers `POST /blogs/categories` to `MdBlog@TbBlogCategoryController@store`. Its existing category Service manually checks for an empty category name and a duplicate name; **the current MdBlog source does not use `LtValidator` for those checks**.

The following shows how a developer could add input validation at the Controller boundary while keeping duplicate checking in the Service:

```php
<?php

namespace Lt\Modules\MdBlog\Controllers;

use Lt\Modules\MdLt\Services\LtRequest;
use Lt\Modules\MdBlog\Services\TbBlogCategoryService;

class TbBlogCategoryController
{
    public function store()
    {
        $request = new LtRequest();

        // Match the submitted category field used by the module.
        $request->validateRequest([
            'categoryName' => 'required|min:2|max:100'
        ]);

        $service = new TbBlogCategoryService();
        return $service->store();
    }
}
```

**Illustrative enhancement, not the current MdBlog Controller code.** The Service should still check whether the category already exists and apply other business requirements. `LtValidator` does not currently provide a `unique` rule. Confirm that the actual form field name is `categoryName` and that the field length matches your database schema.

## Return values and validation failures

The current implementation of `LtValidator`:

- Returns `true` when all supplied rules pass.
- Records field-specific messages internally when rules fail.
- On failure, calls `echo LtResponse::json(self::$errors)` and `exit()`; it does **not** return an ordinary `false` result to the Controller.
- Exposes `LtValidator::errors(): array` and `LtValidator::passed(): bool` for inspecting the most recent validation state.

Therefore, do not write code that expects to catch validation failure using `if (LtValidator::validate(...) === false)` in this version. Its failure behaviour is to output and terminate.

**Implementation notes:** The current `required` rule uses PHP `empty()`, which also treats `0` and `'0'` as empty. `min` and `max` use `strlen()` and are character-length checks, not numeric range checks. The current source does not itself guarantee a particular four-digit response code for validation failures; check the response policy before modifying that implementation.

## Recommended development practices

- Validate HTTP input at the Controller boundary before calling the Service.
- Keep business rules, such as duplicate records or ownership checks, in the Service or relevant domain layer.
- Check authorisation separately; valid input does not mean the requester has permission.
- Validate on the server even when the View already performs JavaScript validation.
- Avoid relying on unrecognised validation rules; use only rules confirmed in the installed `LtValidator` version.
- Test both valid submissions and failures, including missing fields, invalid emails, and unexpected values.

## Source references

- [LtValidator — AppCore documentation](../../appcore/LtValidator.md)
- [LtRequest — AppCore documentation](../../appcore/LtRequest.md)
- [LtValidator source](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtValidator.php)
- [LtRequest source](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtRequest.php)
- [MdBlog category Service](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php)
- [MdBlog category Controller](https://github.com/adedayoAdetunji/MdBlog/blob/main/Controllers/TbBlogCategoryController.php)

---

[Previous](handle-http-requests-with-ltrequest.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](return-api-responses-with-ltresponse.md)
