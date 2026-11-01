# Build a Blog Category Model, Service and Controller

[Previous](understand-the-mdblog-mvc-structure.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](register-and-test-blog-api-endpoints.md)

*Section: Practical MdBlog development*

This lesson follows **existing MdBlog code**, rather than replacing its implementation.

1. Inspect [`TbBlogCategory.php`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Models/TbBlogCategory.php): its class name is derived from `tb_blog_category`.
2. Inspect [`TbBlogCategoryService.php`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php): identify its business operations.
3. Inspect [`TbBlogCategoryController.php`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Controllers/TbBlogCategoryController.php): identify the Controller actions.
4. Inspect [`MdBlogRoutes.php`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/MdBlogRoutes.php): follow the category route.

**New-code convention:** `tb_blog_category` → `TbBlogCategory` → `TbBlogCategoryController` / `TbBlogCategoryService`. Use four-digit response codes and the agreed private/protected property naming for new code. Existing source may use legacy styles.

---

[Previous](understand-the-mdblog-mvc-structure.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](register-and-test-blog-api-endpoints.md)
