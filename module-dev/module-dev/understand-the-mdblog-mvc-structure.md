# Understand the MdBlog MVC Structure

[Previous](publishing-and-unpublishing-a-module.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](build-a-blog-category-model-service-and-controller.md)

*Section: Practical MdBlog development*

Study the actual [MdBlog module](https://github.com/adedayoAdetunji/MdBlog) to understand the naming relationship.

| Layer | File |
|---|---|
| Model | `Models/TbBlogCategory.php` |
| Controller | `Controllers/TbBlogCategoryController.php` |
| Service | `Services/TbBlogCategoryService.php` |
| Module routes | `Services/MdBlogRoutes.php` |
| View | `Views/Category.html` |

The Model corresponds to `tb_blog_category`. The route file is named after the **module**, not after the table. Trace `GET /blogs/categories` through the route, Controller, Service and Model.

---

[Previous](publishing-and-unpublishing-a-module.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](build-a-blog-category-model-service-and-controller.md)
