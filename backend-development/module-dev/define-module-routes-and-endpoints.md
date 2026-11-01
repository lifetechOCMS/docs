# Define Module Routes and Endpoints

[Previous](create-a-module-controller.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-module-views.md)

*Section: Creating module components*

A **route** connects an incoming HTTP request to a method in a module Controller. In LifeTechOCMS, each module has its own route definitions in its `Services/` folder. When a module is created, its main route file follows the pattern `Services/{ModuleName}Routes.php`, such as `Services/MdBlogRoutes.php`.

You can optionally organise additional routes into separate files in the same module. **Every route file must end with `Routes.php`**, for example `MdBlogAdminRoutes.php`. Ensure the additional file is included by the module's route-loading mechanism; creating a file alone does not establish that it will be loaded.

## Route syntax

```php
LtRoute::get(
    '/blogs/categories',
    'MdBlog@TbBlogCategoryController@index'
)->name('admin-blog-category.index');
```

A route declaration has **two arguments**, followed by an optional named-route declaration:

| Part | Example | Meaning |
| --- | --- | --- |
| HTTP method | `LtRoute::get` | Which type of request this route accepts |
| First argument | `'/blogs/categories'` | The URL path matched by the router |
| Second argument | `'MdBlog@TbBlogCategoryController@index'` | The module, Controller class and Controller method to execute |
| Route name | `->name('admin-blog-category.index')` | A stable identifier for the route, useful for referring to it in an API contract or endpoint documentation |

### Understand the `@` syntax

```text
MdBlog@TbBlogCategoryController@index
  │              │               │
  │              │               └── Controller method: index()
  │              └────────────────── Controller: TbBlogCategoryController
  └───────────────────────────────── Module: MdBlog
```

The three segments must match the module and an available public Controller method. For this example, the Controller belongs to `Lt\Modules\MdBlog\Controllers` and exposes an `index()` method.

## HTTP route types

| Method | LifeTechOCMS syntax | Typical purpose |
| --- | --- | --- |
| GET | `LtRoute::get()` | Read or list records without changing them |
| POST | `LtRoute::post()` | Submit data, often to create a record or perform an action |
| PATCH | `LtRoute::patch()` | Update part of an existing record |
| DELETE | `LtRoute::delete()` | Delete a record |

These four methods are **verified in MdBlog's route file**. HTTP also defines `PUT` for replacing a resource, but this guide does not claim that `LtRoute::put()` is supported without checking the installed LtRoute implementation.

## Practical MdBlog example: blog categories

The following routes are taken from `Services/MdBlogRoutes.php`:

```php
LtRoute::get('/blogs/categories', 'MdBlog@TbBlogCategoryController@index')
    ->name('admin-blog-category.index');

LtRoute::post('/blogs/categories', 'MdBlog@TbBlogCategoryController@store')
    ->name('admin-blog-category.store');

LtRoute::patch('/blogs/categories/{ltId}', 'MdBlog@TbBlogCategoryController@update')
    ->name('admin-blog-category.update');

LtRoute::patch('/blogs/categories/{ltId}/toggle-active', 'MdBlog@TbBlogCategoryController@toggleActive')
    ->name('admin-blog-category.toggle_active');

LtRoute::delete('/blogs/categories/{ltId}', 'MdBlog@TbBlogCategoryController@destroy')
    ->name('admin-blog-category.delete');
```

`{ltId}` is a route placeholder identifying the record. In MdBlog, the category Controller reads the identifier through `LtRequest` before passing it to the Service. The full API URL can include a framework-defined API prefix; the route path shown above is the path declared in the module file.

### Recommended Controller method names

| Method name | Intended operation | Typical HTTP method | Verified MdBlog usage |
| --- | --- | --- | --- |
| `index()` | Fetch a collection of records | GET | Categories, tags, posts, comments, reports, settings |
| `store()` | Save a new record | POST | Categories, tags, posts, settings |
| `update()` | Modify an existing record | PATCH | Categories, tags, posts, settings |
| `destroy()` | Delete a record | DELETE | Categories, tags, posts, comments, reports, settings |
| `selectFilter()` | Retrieve a filtered or reduced selection | GET | Blog categories |
| `toggleActive()` | Switch a record's active status | PATCH | Categories, tags, settings |

`index`, `store`, `update`, and `destroy` are **recommended conventions**, not mandatory method names imposed by the router. The action in the route must match the actual method on the Controller.

For specialised endpoints, MdBlog also uses `dashboardMetrics()`, `filterPosts()`, `postSlug()`, `updateStatus()`, `signup()`, and `signin()`. Name custom methods for their purpose and choose an appropriate HTTP method.

## Route names and API contracts

A named route gives an endpoint a stable identifier distinct from its URL. For example:

```php
->name('admin-blog-category.index');
```

This can be recorded in an API contract alongside its HTTP method, path, request data, permissions, and expected response. Route names should be descriptive and unique within the application. Do not assume the name automatically generates an API contract; it is an identifier that tooling or documentation can use.

## Adding another route file

A module can organise a larger set of endpoints into files such as:

```text
MdBlog/
└── Services/
    ├── MdBlogRoutes.php
    └── MdBlogAdminRoutes.php
```

Keep the `Routes.php` suffix, avoid registering the same method and path twice, and confirm that the LifeTechOCMS module loader discovers the new file in your installed version.

## Development checklist

- Put route definitions in the module's `Services/` folder.
- Use the required `Routes.php` filename suffix.
- Choose the HTTP method that matches the operation.
- Supply the route path as the first argument and `Module@Controller@Method` as the second.
- Ensure the Controller and its public method exist.
- Give routes consistent, unique names when documenting an API contract.
- Use placeholders such as `{ltId}` when the endpoint targets a specific record.
- Check authentication, authorisation, input validation, and response handling in the appropriate application layers.
- Test each endpoint with the correct HTTP method and request payload.

## References

- [MdBlog route definitions](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/MdBlogRoutes.php)
- [MdBlog category Controller](https://github.com/adedayoAdetunji/MdBlog/blob/main/Controllers/TbBlogCategoryController.php)
- [LtRoute – Developer Guide](../../appcore/LtRoute.md)

---

[Previous](create-a-module-controller.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-module-views.md)
