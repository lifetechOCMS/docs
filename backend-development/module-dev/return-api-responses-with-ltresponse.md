# Return API Responses with LtResponse

[Previous](validate-input-with-ltvalidator.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](use-ltmodel-and-ltservice-for-database-operations.md)

*Section: Working with Core Services (MdLt)*

## Purpose

`LtResponse` gives LifeTech OCMS modules a consistent way to return JSON results from controllers and services. A module View, theme, or external API client can read the same response field names for success and failure outcomes.

Import the service:

```php
use Lt\Modules\MdLt\Services\LtResponse;
```

## Return a successful API response

```php
return LtResponse::json(
    'Categories loaded successfully',
    '4000',
    '200',
    [
        ['ltId' => 'cat-01', 'categoryName' => 'Technology'],
        ['ltId' => 'cat-02', 'categoryName' => 'Education']
    ]
);
```

The example above illustrates the response format; the sample records are not retrieved from a database.

The resulting JSON has this structure:

```json
{
  "responseResult": "Categories loaded successfully",
  "responseCode": "4000",
  "responseCategory": "200",
  "responseData": [
    {"ltId": "cat-01", "categoryName": "Technology"},
    {"ltId": "cat-02", "categoryName": "Education"}
  ]
}
```

`LtResponse::json()` returns a **JSON-encoded string**, not a PHP array. The application's HTTP response layer must send it as JSON; do not encode the returned string a second time.

## Understand the response fields

| Field | Meaning | Example |
|---|---|---|
| `responseResult` | Human-readable outcome or message | `Categories loaded successfully` |
| `responseCode` | Four-digit LifeTech application code | `4000` |
| `responseCategory` | Outcome category: `200` success, `100` failure | `200` |
| `responseData` | Optional returned records or other data | An array of categories |

**Response codes:** For a new module-specific response, it is **compulsory** to supply an explicit **exactly four-digit** code in the **Customized range `4000–5999`** and register it before use. The `4000`–`4002` examples in this guide are illustrative placeholders, not proof that those codes are available; consult the [Response Codes and Response Groups guide](../../appcore/LtResponse_Codes_and_Response_Groups.md) before assigning codes in production. The current PHP method does not enforce the four-digit rule by itself.

**HTTP status:** `responseCode` and `responseCategory` are application fields; they do not automatically set the HTTP response status (for example, HTTP 200 or 404).

**Optional data:** The current implementation omits `responseData` when the argument is `[]` or `null`.

```php
return LtResponse::json('Operation completed', '4000', '200');
```

The result has `responseResult`, `responseCode`, and `responseCategory`, without `responseData`.

## Response groups and customizable response codes

LifeTech OCMS organizes its **four-digit response codes into response groups**. A response group reserves a range for a framework feature or a developer-defined feature. This keeps codes organized and helps avoid assigning the same code to different outcomes.

**Mandatory for module developers:** Every new LifeTech OCMS module **must use the Customized response-code group (`4000–5999`) for its module-specific responses**. Every response code **must contain exactly four digits**. Codes outside this range are reserved for the framework and their assigned subsystems; a module must not use them for its own new response definitions. Existing framework-generated responses may still use their registered framework codes. The `LtResponse` PHP methods do not currently enforce these rules automatically, so module developers must follow them and register codes appropriately. Select a unique four-digit code in the Customized group, enter the response message, select its success/failure category, and optionally add a solution for errors. Developers should check existing records before reusing any code.

| Response group | Assigned range |
|---|---|
| Authentication | `1000–1099` |
| Lw-token | `1100–1199` |
| API | `1200–1299` |
| Router | `1300–1399` |
| Menu | `1500–1599` |
| File | `1900–1999` |
| Maplite | `2000–2999` |
| User | `3000–3099` |
| Response | `3100–3149` |
| Role | `3200–3299` |
| Package | `3300–3399` |
| Page | `3400–3499` |
| Content | `3500–3599` |
| **Customized** | **`4000–5999`** |

The Customized range is **compulsory for new module-specific responses**, not optional. All code examples using `4000`, `4001`, or `4002` are **illustrative placeholders**, not confirmed available or registered codes: check Response Management and register unique codes before using them. These are the documented group allocations, not a claim that every number is registered. Other ranges are reserved or unassigned and should not be used without defining a group.

### Response group versus response category

These terms serve different purposes:

- **Response group:** the feature's allocated code range, such as `File` (`1900–1999`) or `Customized` (`4000–5999`).
- **Response code:** a unique four-digit outcome identifier within that range, such as the registered File code `1992`.
- **Response category:** whether that outcome succeeded (`'200'`) or failed (`'100'`). A group may contain **both** successful and failed responses.

For example, the registered File response code `1992` represents successful file creation and uses category `'200'`:

```php
return LtResponse::json(
    'File created successfully',
    '1992',
    '200',
    ['filename' => 'example.txt']
);
```

For every new module, register an available **exactly four-digit code between `4000` and `5999`** in the Customized range and then supply **that registered code** to `LtResponse::json()` or `LtResponse::error()`. Merely passing a new code to the method does **not** register it automatically.

See [Response Codes and Response Groups — Developer Guide](../../appcore/LtResponse_Codes_and_Response_Groups.md) for the full group list, database fields, registration steps, and examples.

## Return an expected failure

Use `json()` when you intentionally want the client to see an application message, such as a missing record or a failed business rule:

```php
return LtResponse::json(
    'Category not found',
    '4001',
    '100'
);
```

Unlike `error()`, `json()` returns the supplied message even when the application is in production. Never include sensitive diagnostic details in a client-facing message.

## Handle unexpected errors with `error()`

Use `error()` for unexpected exceptions or internal failures:

```php
try {
    // Perform the module operation here.
} catch (\Throwable $e) {
    return LtResponse::error(
        $e->getMessage(),
        '4002',
        '100'
    );
}
```

The current implementation checks `LT_ENV`:

- **Development (or when `LT_ENV` is undefined):** the original message, code, category, and optional data are returned through `json()`.
- **Production:** the original message is written to the application error log; the client receives `Something went wrong. Please try again later.` with response code `1043` and category `100`.

Both methods use the same response structure. `error()` is not a different JSON format; it is an environment-aware way to avoid exposing internal failures in production.

## Practical module example: controller response after service execution

In this illustrative `MdStudent` controller, the service is responsible for retrieving data; the controller returns a standardized response. Adapt the service and method names to your actual module.

```php
<?php

namespace Lt\Modules\MdStudent\Controllers;

use Lt\Modules\MdLt\Services\LtResponse;
use Lt\Modules\MdStudent\Services\TbStudentService;

class TbStudentController
{
    public function index()
    {
        try {
            $service = new TbStudentService();
            $students = $service->index();

            return LtResponse::json(
                'Students loaded successfully',
                '4000',
                '200',
                $students
            );
        } catch (\Throwable $e) {
            return LtResponse::error(
                $e->getMessage(),
                '4002',
                '100'
            );
        }
    }
}
```

This example assumes `TbStudentService::index()` returns records. If a service already returns an `LtResponse` JSON string, return that string directly instead of wrapping it again.

## How MdBlog uses `LtResponse`

The actual MdBlog category implementation uses `LtResponse::json()` for controller and service outcomes, including responses when a category already exists or cannot be found. For example, its category service includes:

```php
return LtResponse::json('Category already exist', 3004, 100);
```

That example uses four digits but falls in the framework User range (`3000–3099`), so it **does not comply with the new module-specific Customized-range policy**. Other older MdBlog methods still use three-digit codes such as `201`. **Do not copy either pattern into new module-specific responses**: register and use an available code from `4000–5999`, always exactly four digits.

Sources: [MdBlog category service](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php) and [MdBlog category controller](https://github.com/adedayoAdetunji/MdBlog/tree/main/Controllers).

## Log additional diagnostic information

`LtResponse::writeLog()` records a message and optional context, returning a log reference:

```php
$logReference = LtResponse::writeLog(
    'Student record could not be loaded',
    ['operation' => 'student.index']
);
```

The implementation writes daily `Error-YYYY-MM-DD.log` files under `LT_LOG_PATH` when defined, or a fallback `logs` directory relative to the service. Do not log passwords, tokens, or sensitive personal data.

## Public method overview

| Method | Use |
|---|---|
| `LtResponse::json(...)` | Return a normal JSON result, success or expected failure |
| `LtResponse::error(...)` | Return an environment-aware error; log and hide details in production |
| `LtResponse::writeLog($message, $context = [])` | Write diagnostic information to an error log |

The signatures of `json()` and `error()` also accept `$responseStatus` and `$responseOperationType`. The current JSON implementation does not include these two fields in the output payload. For the full method signatures, see [LtResponse — Developer Guide](../../appcore/LtResponse.md).

## Summary

Use `LtResponse::json()` for standard module API outcomes and `LtResponse::error()` for unexpected internal errors. For all new module-specific outcomes, **use a registered, unique, exactly four-digit code from the compulsory Customized range `4000–5999`** and the appropriate success (`200`) or failure (`100`) category. Return the resulting JSON string without encoding it again, and keep internal diagnostics out of production responses.

## References

- [LtResponse — Developer Guide](../../appcore/LtResponse.md)
- [Response Codes and Response Groups](../../appcore/LtResponse_Codes_and_Response_Groups.md)
- [MdLt LtResponse implementation](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtResponse.php)

---

[Previous](validate-input-with-ltvalidator.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](use-ltmodel-and-ltservice-for-database-operations.md)
