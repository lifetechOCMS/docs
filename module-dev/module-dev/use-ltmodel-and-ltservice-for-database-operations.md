# Use LtModel and LtService for Database Operations

[Previous](return-api-responses-with-ltresponse.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](manage-authentication-sessions-and-permissions.md)

*Section: Working with Core Services (MdLt)*

The `TbBlogCategory` Model extends `\LtModel`. The corresponding `TbBlogCategoryService` is a plain PHP class and uses the Model's query methods.

```php
$query = $this->_blogModel->select();
$query->where('status', '=', $status);
return $query->get();
```

The sample property name uses the newly agreed underscore convention. In the existing MdBlog source the property may have a different name.

The Model for `tb_blog_category` is named `TbBlogCategory`; its Controller and Service are `TbBlogCategoryController` and `TbBlogCategoryService`. See [LtModel](../appcore/LtModel.md) and [LtService](../appcore/LtService.md).

---

[Previous](return-api-responses-with-ltresponse.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](manage-authentication-sessions-and-permissions.md)
