# Create a Module Service

[Previous](create-database-table-and-model.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](create-a-module-controller.md)

*Section: Creating module components*

A Service coordinates business operations and calls the Model. A Service associated with `TbStudent` **must** be named `TbStudentService` and saved as `Services/TbStudentService.php`.

```php
<?php
namespace Lt\Modules\MdStudent\Services;

use Lt\Modules\MdStudent\Models\TbStudent;

class TbStudentService {
    protected $_studentModel;

    public function __construct() {
        $this->_studentModel = new TbStudent();
    }

    public function index() {
        return $this->_studentModel->select()->get();
    }
}
```

This is a convention-aligned illustrative implementation. MdBlog's [category service](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php) demonstrates the underlying `select()`, `where()` and `get()` pattern. A route file such as `MdStudentRoutes.php` is stored in `Services/` but is **not** a business Service class.

---

[Previous](create-database-table-and-model.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](create-a-module-controller.md)
