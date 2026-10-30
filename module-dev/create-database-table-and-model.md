# Create a Database Table and Model

[Previous](understand-the-mvc-architecture.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-a-module-service.md)

*Section: Creating module components*

MdBlog includes the `TbBlogCategory` model:

```php
<?php
namespace Lt\Modules\MdBlog\Models;

class TbBlogCategory extends \LtModel
{
}
```

The model inherits database behavior from `\LtModel`. Its corresponding table is `tb_blog_category`, as identified in the MdBlog repository documentation.

Before creating a new model, define the database columns and confirm the table mapping and schema conventions for your installed version. See [LtModel](../../appcore/LtModel.md).

---

[Previous](understand-the-mvc-architecture.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-a-module-service.md)
