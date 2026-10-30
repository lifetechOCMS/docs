# Handle HTTP Requests with LtRequest

[Previous](connect-views-to-module-apis.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](validate-input-with-ltvalidator.md)

*Section: Working with Core Services (MdLt)*

MdBlog uses `LtRequest` to read incoming values. In its category controller, `update()` constructs `new LtRequest` and reads `$request->ltId`. In the category service, `index()` reads `$this->request->status`.

```php
use Lt\Modules\MdLt\Services\LtRequest;
$request = new LtRequest;
$ltId = $request->ltId;
```

Treat incoming values as untrusted and validate them before database operations. See [LtRequest](../../appcore/LtRequest.md).

---

[Previous](connect-views-to-module-apis.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](validate-input-with-ltvalidator.md)
