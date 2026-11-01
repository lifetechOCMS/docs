# Handle HTTP Requests with LtRequest

[Previous](connect-views-to-module-apis.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](validate-input-with-ltvalidator.md)

*Section: Working with Core Services (MdLt)*

## What is LtRequest?

`LtRequest` is a LifeTechOCMS core service that makes incoming HTTP request parameters available through object properties. Once you create an `LtRequest` instance, access an incoming parameter using its name:

```php
use Lt\Modules\MdLt\Services\LtRequest;

$request = new LtRequest();

$studentName = $request->studentName;
$email = $request->email;
$ltId = $request->ltId;
```

For example, if the incoming request supplies a parameter named `studentName`, you can read it using `$request->studentName`. This avoids manually retrieving each field from `$_GET` or `$_POST` in your module code. The parameter must actually be present in the request; `LtRequest` does not invent missing values.

For the complete class reference and available methods, see [LtRequest — Developer Guide](../../appcore/LtRequest.md).

## Practical example: MdBlog

The [MdBlog category Controller](https://github.com/adedayoAdetunji/MdBlog/blob/main/Controllers/TbBlogCategoryController.php) creates an `LtRequest` instance and reads the incoming category identifier:

```php
$request = new LtRequest;
$ltId = $request->ltId;

$service = new TbBlogCategoryService();
$result = $service->update($ltId);

return $result;
```

The [MdBlog category Service](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php) also reads a `status` parameter to optionally filter categories:

```php
$status = $this->request->status;
$query = $this->blogModel->select();

if ($status !== null && $status !== '') {
    $query->where('status', '=', $status);
}

return $query->get();
```

These are simplified extracts of actual MdBlog methods, formatted for clarity. The Service creates `$this->request = new LtRequest;` in its constructor.

## Using LtRequest in your own module

For a student module, a Controller can read an identifier and pass it to a Service:

```php
<?php

namespace Lt\Modules\MdStudent\Controllers;

use Lt\Modules\MdLt\Services\LtRequest;
use Lt\Modules\MdStudent\Services\TbStudentService;

class TbStudentController
{
    public function show()
    {
        $request = new LtRequest();
        $ltId = $request->ltId;

        $service = new TbStudentService();
        return $service->show($ltId);
    }
}
```

**Illustrative example:** This assumes your `TbStudentService` implements `show($ltId)`. It is not a claim that this method is automatically generated.

## Working with optional parameters

A request may not include every field. Check optional values before using them:

```php
$request = new LtRequest();
$status = $request->status;

if ($status !== null && $status !== '') {
    // Apply the optional status filter.
}
```

This follows the pattern used by MdBlog. If a field is required, validate it before using it in a database operation. Reading a property does **not** automatically mean its value is safe, correctly typed, or authorised.

## When to use LtRequest

Use `LtRequest` when a Controller or Service needs to read incoming request values such as a record identifier, a search term, a status filter, or form fields. Keep the parameter names consistent between the frontend/API client and the backend code.

For request validation, continue to [Validate Input with LtValidator](validate-input-with-ltvalidator.md). For the core service's method reference, see [LtRequest](../../appcore/LtRequest.md).

---

[Previous](connect-views-to-module-apis.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](validate-input-with-ltvalidator.md)
