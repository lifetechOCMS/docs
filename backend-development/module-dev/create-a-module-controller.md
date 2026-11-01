# Create a Module Controller

[Previous](create-a-module-service.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](define-module-routes-and-endpoints.md)

*Section: Creating module content*

## What is Controller content?

A **Controller** is PHP module content that receives a request from a route, coordinates the requested operation through a Service, and returns a response. It is the entry point between the module's API routes and its business logic.

```text
Route → Controller → Service → Model → Database
                          ↓
                  Result returned
                          ↓
                 Controller → API response
```

A Controller does **not** need to contain database queries or all the rules for creating and updating records. Those responsibilities generally belong to the Service and Model.

## What should a Controller do?

| Responsibility | Explanation |
| --- | --- |
| Receive routed requests | Expose public methods that a module route can call, such as `index()` or `store()`. |
| Read request information | Retrieve parameters such as a record's `ltId` using the request tools available in LifeTechOCMS. |
| Enforce access rules | Ensure protected operations have the appropriate authentication and authorisation checks, either at the route, controller, or shared middleware layer. |
| Delegate to a Service | Call a Service method instead of duplicating business logic or database operations. |
| Return a response | Return the Service's response or wrap retrieved data using `LtResponse`. |
| Handle failures consistently | Avoid exposing internal errors to API consumers; follow the framework's response and error-handling conventions. |

**Important:** A Controller is not the place to build a theme's HTML layout. Views and frontend assets belong to their respective content types.

## Create Controller content in LifeTechOCMS

1. Open **Modules** in the LifeTechOCMS backend.
2. Select your module, such as `MdStudent`.
3. Open **Module Content** and choose **Add Content**.
4. Enter a name such as `TbStudentController.php`.
5. Select **Controller** as the **MVC Type**.
6. Complete the other applicable content fields and create the content.
7. Open the generated file in the module code editor and implement the controller methods.

Alternatively, use **Auto Create**: select an existing database table, check **Create with: Controller** (and the Model and Service options if needed), then select **Create Content**. Review the generated code before using it.

## Naming and location

| Item | Example |
| --- | --- |
| Module | `MdStudent` |
| Database table | `tb_student` |
| Model | `TbStudent.php` |
| Service | `TbStudentService.php` |
| Controller content | `TbStudentController.php` |
| Folder | `Controllers/` |
| PHP namespace | `Lt\Modules\MdStudent\Controllers` |

Controller classes use **PascalCase** and end with `Controller`. Methods use **camelCase**.

## Practical MdBlog example

The existing [MdBlog category Controller](https://github.com/adedayoAdetunji/MdBlog/blob/main/Controllers/TbBlogCategoryController.php) imports its Service, `LtRequest`, and `LtResponse`:

```php
namespace Lt\Modules\MdBlog\Controllers;

use Lt\Modules\MdBlog\Services\TbBlogCategoryService;
use Lt\Modules\MdLt\Services\LtRequest;
use Lt\Modules\MdLt\Services\LtResponse;
```

Its `index()` operation retrieves categories from the Service and returns them as an API response:

```php
public function index()
{
    $service = new TbBlogCategoryService();
    $rows = $service->index();

    return LtResponse::json('success', 201, 200, $rows);
}
```

This extract reflects the current MdBlog source. **The `201` code is legacy**; new LifeTechOCMS code must follow the [four-digit response-code policy](../../appcore/LtResponse_Codes_and_Response_Groups.md).

For updates, the existing Controller reads `ltId` from `LtRequest`, then delegates to the Service:

```php
$request = new LtRequest();
$ltId = $request->ltId;
$service = new TbBlogCategoryService();

return $service->update($ltId);
```

MdBlog's current Controller also exposes these methods:

| Controller method | Calls Service method | Purpose |
| --- | --- | --- |
| `index()` | `index()` | List categories |
| `selectFilter()` | `selectFilter()` | Get categories for selection |
| `store()` | `store()` | Create a category |
| `update()` | `update($ltId)` | Update a category |
| `toggleActive()` | `toggleActive($ltId)` | Change active status |
| `destroy()` | `destroy($ltId)` | Delete a category |

The linked MdBlog source is an implementation example, not a requirement to copy every detail. For instance, its `exit()` statements after `return` are unreachable and should not be copied into new code.

## A simple Controller for your own module

The following **illustrative** example assumes the `TbStudentService` from the previous lesson exists. It uses a **four-digit example response code**; select the correct defined code from the response-code reference before deploying.

```php
<?php

namespace Lt\Modules\MdStudent\Controllers;

use Lt\Modules\MdStudent\Services\TbStudentService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbStudentController
{
    public function index()
    {
        $service = new TbStudentService();
        $students = $service->index();

        return LtResponse::json('Students retrieved', 2000, 200, $students);
    }
}
```

Here, the Controller coordinates the request; the Service retrieves the student records; and `LtResponse` formats the API result. The `2000` value is illustrative, **not a verified assigned LifeTechOCMS response code**.

### Optional: constructor dependency injection

A Controller can receive its Service through its constructor to simplify testing and replacement:

```php
class TbStudentController
{
    public function __construct(
        private TbStudentService $studentService
    ) {
    }

    public function index()
    {
        return $this->studentService->index();
    }
}
```

This is a general PHP technique. **Do not assume** LifeTechOCMS automatically creates constructor arguments when invoking a Controller from a route; use this approach only when your controller-instantiation setup supports it. Also, the illustrative `index()` above returns raw Service data; wrap it in `LtResponse` when the endpoint requires a standard API response.

## Before moving on

- Confirm the Controller filename, class name, folder, and namespace match.
- Make sure the required Service exists and its methods are public.
- Keep database operations and substantial business rules in the Service/Model layer.
- Check access control for protected endpoints.
- Follow four-digit response codes and consistent API responses.
- Connect the Controller's public methods to module routes in the next lesson.

See [LtRequest](../../appcore/LtRequest.md) and [LtResponse](../../appcore/LtResponse.md) for related framework services.

---

[Previous](create-a-module-service.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](define-module-routes-and-endpoints.md)
