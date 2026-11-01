# Return API Responses with LtResponse

[Previous](validate-input-with-ltvalidator.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](use-ltmodel-and-ltservice-for-database-operations.md)

*Section: Working with Core Services (MdLt)*

Use `LtResponse` to return the standardized LifeTechOCMS response envelope.

```php
use Lt\Modules\MdLt\Services\LtResponse;

// Use an officially assigned four-digit application code.
return LtResponse::json('success', $responseCode, 200, $rows);
```

`responseCode` is the **four-digit application code**, while `responseCategory` indicates success (`200`) or failure (`100`). `$responseCode` must be selected from the [official response-code reference](../appcore/LtResponse_Codes_and_Response_Groups.md).

Older MdBlog source extracts sometimes use shorter legacy codes; do **not** copy those codes into new modules. See [LtResponse](../appcore/LtResponse.md).

---

[Previous](validate-input-with-ltvalidator.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](use-ltmodel-and-ltservice-for-database-operations.md)
