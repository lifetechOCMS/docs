# Build a Blog Category Model, Service and Controller

[Previous](understand-the-mdblog-mvc-structure.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](register-and-test-blog-api-endpoints.md)

*Section: Practical MdBlog development*

This lesson studies **existing MdBlog code** rather than introducing an incompatible replacement.

1. Open [TbBlogCategory.php](https://github.com/adedayoAdetunji/MdBlog/blob/main/Models/TbBlogCategory.php) and note that it extends `\LtModel`.
2. Open [TbBlogCategoryService.php](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php) and locate `index()`, `store()`, `update()`, and `destroy()`.
3. Open [TbBlogCategoryController.php](https://github.com/adedayoAdetunji/MdBlog/blob/main/Controllers/TbBlogCategoryController.php) and identify the corresponding controller methods.
4. Trace `GET /blogs/categories` from its route to the controller's `index()` and the service's `index()`.

For new code, improve input validation and follow the current four-digit response-code policy rather than copying older response codes unchanged.

---

[Previous](understand-the-mdblog-mvc-structure.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](register-and-test-blog-api-endpoints.md)
