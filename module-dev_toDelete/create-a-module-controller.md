# Create a Module Controller

[Previous](create-a-module-service.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](define-module-routes-and-endpoints.md)

*Section: Creating module components*

A Controller associated with `TbStudent` must be named `TbStudentController` and saved as `Controllers/TbStudentController.php`. All other Controllers also end in `Controller`.

```php
<?php
namespace Lt\Modules\MdStudent\Controllers;

use Lt\Modules\MdStudent\Services\TbStudentService;

class TbStudentController {
    public function index() {
        $service = new TbStudentService();
        return $service->index();
    }
}
```

This illustrates Controller-to-Service delegation; production endpoints should return the response envelope appropriate to the framework. For a real example, study [MdBlog's category controller](https://github.com/adedayoAdetunji/MdBlog/blob/main/Controllers/TbBlogCategoryController.php). Use **four-digit** response codes from the [response-code guide](../appcore/LtResponse_Codes_and_Response_Groups.md).

---

[Previous](create-a-module-service.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](define-module-routes-and-endpoints.md)
