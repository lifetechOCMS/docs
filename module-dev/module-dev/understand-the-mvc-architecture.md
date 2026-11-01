# Understand the MVC Architecture

[Previous](auto-create-model-controller-service.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](create-database-table-and-model.md)

*Section: Creating module components*

LifeTechOCMS module development uses Models, Controllers and Services, with route definitions and Views.

```text
HTTP request → MdBlogRoutes.php → TbBlogCategoryController
                                      ↓
                             TbBlogCategoryService
                                      ↓
                               TbBlogCategory
                                      ↓
                              tb_blog_category
```

A Controller handles a routed request, a Service coordinates business logic, and a Model accesses its database table. Views can display data returned by the module's endpoints.

**Naming rule:** `tb_blog_category` → `TbBlogCategory` → `TbBlogCategoryController` and `TbBlogCategoryService`. This relationship is visible in the [MdBlog repository](https://github.com/adedayoAdetunji/MdBlog).

---

[Previous](auto-create-model-controller-service.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](create-database-table-and-model.md)
