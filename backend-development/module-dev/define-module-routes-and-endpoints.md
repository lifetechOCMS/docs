# Define Module Routes and Endpoints

[Previous](create-a-module-controller.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-module-views.md)

*Section: Creating module components*

MdBlog registers routes in `Services/MdBlogRoutes.php`. For example:

```php
LtRoute::get('/blogs/categories',
    'MdBlog@TbBlogCategoryController@index')
    ->name('admin-blog-category.index');

LtRoute::post('/blogs/categories',
    'MdBlog@TbBlogCategoryController@store')
    ->name('admin-blog-category.store');
```

These statements are from the [actual route file](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/MdBlogRoutes.php). A route connects the HTTP method and path to a controller action. See [LtRoute](../../appcore/LtRoute.md).

---

[Previous](create-a-module-controller.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-module-views.md)
