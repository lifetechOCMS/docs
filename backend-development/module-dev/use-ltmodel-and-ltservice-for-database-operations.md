# Use LtModel and LtService for Database Operations

[Previous](return-api-responses-with-ltresponse.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](manage-authentication-sessions-and-permissions.md)

*Section: Working with Core Services (MdLt)*

MdBlog's category model extends `\LtModel`; the category service uses its query methods. A typical read in the source is:

```php
$query = $this->blogModel->select();
$query->where('status', '=', $status);
return $query->get();
```

Other operations in the same service use `processRequest()`, `insert()`, `update()`, and `delete()`. Review the [LtModel](../../appcore/LtModel.md) and [LtService](../../appcore/LtService.md) references before reusing these methods.

This lesson does not assume that every service must inherit from `LtService`: MdBlog's `TbBlogCategoryService` is a plain PHP class.

---

[Previous](return-api-responses-with-ltresponse.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](manage-authentication-sessions-and-permissions.md)
