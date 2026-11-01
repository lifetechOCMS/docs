# Create a Module Controller

[Previous](create-a-module-service.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](define-module-routes-and-endpoints.md)

*Section: Creating module components*

MdBlog's category controller delegates work to `TbBlogCategoryService`.

```php
use Lt\Modules\MdBlog\Services\TbBlogCategoryService;
use Lt\Modules\MdLt\Services\LtResponse;

public function index() {
    $service = new TbBlogCategoryService();
    $rows = $service->index();
    return LtResponse::json('success', 201, 200, $rows);
}
```

This is an extract from the current [MdBlog controller](https://github.com/adedayoAdetunji/MdBlog/blob/main/Controllers/TbBlogCategoryController.php), not a complete controller. For new code, follow the [four-digit response-code policy](../../appcore/LtResponse_Codes_and_Response_Groups.md) rather than copying its legacy `201` response code.

---

[Previous](create-a-module-service.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](define-module-routes-and-endpoints.md)
