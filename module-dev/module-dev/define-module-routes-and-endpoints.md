# Define Module Routes and Endpoints

[Previous](create-a-module-controller.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](create-module-views.md)

*Section: Creating module components*

**LifeTechOCMS automatically creates a module route file when the module is created.** Its name is `{ModuleName}Routes.php`, and it is saved in `Services/`. For `MdBlog`, the file is `Services/MdBlogRoutes.php`.

MdBlog registers endpoints using `LtRoute`:

```php
LtRoute::get('/blogs/categories',
    'MdBlog@TbBlogCategoryController@index')
    ->name('admin-blog-category.index');

LtRoute::post('/blogs/categories',
    'MdBlog@TbBlogCategoryController@store')
    ->name('admin-blog-category.store');
```

These route examples are from [MdBlogRoutes.php](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/MdBlogRoutes.php). Route actions reference the Controller, which delegates operations to a Service and Model. See [LtRoute](../appcore/LtRoute.md).

---

[Previous](create-a-module-controller.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](create-module-views.md)
