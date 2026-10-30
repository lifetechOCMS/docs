# Create a Module Service

[Previous](create-database-table-and-model.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-a-module-controller.md)

*Section: Creating module components*

The MdBlog category service lives in `Services/TbBlogCategoryService.php`. It creates a `TbBlogCategory` model and an `LtRequest` instance, then implements methods such as `index()`, `store()`, `update()`, `toggleActive()`, and `destroy()`.

## Extract from MdBlog

```php
use Lt\Modules\MdBlog\Models\TbBlogCategory;
use Lt\Modules\MdLt\Services\LtRequest;

$this->blogModel = new TbBlogCategory();
$this->request = new LtRequest;
```

The service's `index()` method builds a query using `select()`, optionally adds `where()`, and returns `get()`.

Read [the service source](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php) alongside [LtRequest](../../appcore/LtRequest.md) and [LtModel](../../appcore/LtModel.md).

---

[Previous](create-database-table-and-model.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-a-module-controller.md)
