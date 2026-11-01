# Understand the MVC Architecture

[Previous](auto-create-model-controller-service.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-database-table-and-model.md)

*Section: Creating module components*

MdBlog uses a model–service–controller pattern, with routes and views:

```text
HTTP request
   ↓
MdBlogRoutes.php
   ↓
TbBlogCategoryController
   ↓
TbBlogCategoryService
   ↓
TbBlogCategory model
   ↓
Database
```

A view can call the exposed API and render the result. The controller dispatches the operation, the service performs the application logic, and the model interacts with stored data.

Compare [controller](https://github.com/adedayoAdetunji/MdBlog/blob/main/Controllers/TbBlogCategoryController.php), [service](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php), and [model](https://github.com/adedayoAdetunji/MdBlog/blob/main/Models/TbBlogCategory.php).

---

[Previous](auto-create-model-controller-service.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-database-table-and-model.md)
