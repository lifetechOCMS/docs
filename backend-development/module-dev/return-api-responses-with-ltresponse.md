# Return API Responses with LtResponse

[Previous](validate-input-with-ltvalidator.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](use-ltmodel-and-ltservice-for-database-operations.md)

*Section: Working with Core Services (MdLt)*

MdBlog's category controller uses `LtResponse::json()` to return a standard response envelope.

```php
use Lt\Modules\MdLt\Services\LtResponse;

return LtResponse::json('success', 201, 200, $rows);
```

This is a source extract. For new modules, **use the mandatory four-digit application response codes** defined in the [Response Codes and Response Groups guide](../../appcore/LtResponse_Codes_and_Response_Groups.md). The `responseCategory` is distinct from the response code: `200` indicates success, `100` indicates failure.

Read [LtResponse](../../appcore/LtResponse.md) for the method behavior.

---

[Previous](validate-input-with-ltvalidator.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](use-ltmodel-and-ltservice-for-database-operations.md)
