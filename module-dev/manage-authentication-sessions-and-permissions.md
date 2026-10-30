# Manage Authentication, Sessions and Permissions

[Previous](use-ltmodel-and-ltservice-for-database-operations.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](using-the-module-code-editor.md)

*Section: Working with Core Services (MdLt)*

MdBlog's category service retrieves the user identifier with `LtSession::get('ltUid')`. This demonstrates session access but does **not**, by itself, prove that an endpoint is protected.

```php
use Lt\Modules\MdLt\Services\LtSession;
$userId = LtSession::get('ltUid');
```

For protected operations, consult [LtAuth](../../appcore/LtAuth.md), [LtSession](../../appcore/LtSession.md), and the actual permission configuration. Enforce authorization on the server, not only by hiding buttons in views.

---

[Previous](use-ltmodel-and-ltservice-for-database-operations.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](using-the-module-code-editor.md)
