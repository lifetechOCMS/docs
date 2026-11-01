# Create a Module Service

[Previous](create-database-table-and-model.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-a-module-controller.md)

*Section: Creating module content*

## What is Service content?

A **Service** is module content that implements the operations and business rules of a feature. A Service can use a Model to work with database records and can be called by a Controller when an API request arrives.

For example, the MdBlog category Service works with the `TbBlogCategory` Model to retrieve, create, update and delete blog categories.

```text
Route → Controller → Service → Model → Database
```

A Service is not itself a database table. Create the table and its Model first when your Service needs stored data.

## Create Service content in LifeTechOCMS

1. Open **Modules** in the LifeTechOCMS backend.
2. Select the module you want to develop, such as `MdStudent`.
3. On the **Module Content** page, click **Add Content**.
4. Enter a content name, such as `TbStudentService.php`, and a short description.
5. Under **MVC Type**, select **Service**.
6. Choose the appropriate **Store Type** and, optionally, enter a content category.
7. Click **Add**, then open the created content to write or review its PHP code.

Alternatively, use **Auto Create**: select an existing database table, check **Create with: Service**, and click **Create Content**. Review the generated Service before adding business rules.

## Service naming conventions

| Item | Example |
| --- | --- |
| Module | `MdStudent` |
| Database table | `tb_student` |
| Model | `TbStudent` |
| Service content | `TbStudentService.php` |
| Service folder | `Services/` |
| Namespace | `Lt\Modules\MdStudent\Services` |

Use **PascalCase** for class names and **camelCase** for methods. Business Service classes should end with `Service`. The module's automatically created route file, such as `MdStudentRoutes.php`, serves a different purpose.

## Practical example: MdBlog category Service

MdBlog provides a real example in [`Services/TbBlogCategoryService.php`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php).

Its PHP namespace and imports include:

```php
<?php

namespace Lt\Modules\MdBlog\Services;

use Lt\Modules\MdBlog\Models\TbBlogCategory;
use Lt\Modules\MdLt\Services\LtRequest;
use Lt\Modules\MdLt\Services\LtResponse;
use Lt\Modules\MdLt\Services\LtSession;
```

The existing Service creates its Model and request helper in its constructor:

```php
$this->blogModel = new TbBlogCategory();
$this->request = new LtRequest;
```

Its public methods include:

| Method | Responsibility |
| --- | --- |
| `index()` | Retrieve categories, optionally filtered by status |
| `selectFilter()` | Retrieve category identifiers and names for selection |
| `store()` | Validate and create a category |
| `update($ltId)` | Update an existing category |
| `toggleActive($ltId)` | Change a category's active status |
| `destroy($ltId)` | Delete a category |

For example, the existing `index()` method starts a Model query, applies a status condition when provided, and retrieves the results:

```php
public function index()
{
    $status = $this->request->status;
    $query = $this->blogModel->select();

    if ($status !== null && $status !== '') {
        $query->where('status', '=', $status);
    }

    return $query->get();
}
```

This example is taken from the MdBlog implementation, with formatting adjusted for readability. Other methods perform validation and write operations; inspect the linked source before adapting them.

## A simple Service for your own module

The following **illustrative starting structure** shows a Service using the Model you created in the previous lesson. The exact query and response methods depend on your installed LifeTechOCMS version.

```php
<?php

namespace Lt\Modules\MdStudent\Services;

use Lt\Modules\MdStudent\Models\TbStudent;

class TbStudentService
{
    private TbStudent $_studentModel;

    public function __construct()
    {
        $this->_studentModel = new TbStudent();
    }

    public function index()
    {
        return $this->_studentModel->select()->get();
    }
}
```

Here, `index()` asks the Model for student records. A Controller can call the Service rather than repeating the database query itself.

### Optional: dependency injection

For improved testability, you can also supply the Model to the Service through its constructor rather than creating it internally. This is an **optional PHP design approach**, not a claim that LifeTechOCMS automatically resolves constructor dependencies.

```php
public function __construct(TbStudent $studentModel)
{
    $this->_studentModel = $studentModel;
}
```

When using this form, the calling code must provide a `TbStudent` instance unless a dependency container is configured to do so.

## Before moving on

- Confirm the required database table and Model already exist.
- Check the Service filename, namespace and class name.
- Keep business rules in the Service and database access through Models where practical.
- Validate inputs and use LifeTechOCMS response conventions, including **four-digit response codes** for new code.
- Test the Service's operations before exposing them through routes.

See [LtModel](../../appcore/LtModel.md), [LtRequest](../../appcore/LtRequest.md), and [LtResponse](../../appcore/LtResponse.md) for related framework services.

Next, learn how to [Create a Module Controller](create-a-module-controller.md) that calls Service methods.

---

[Previous](create-database-table-and-model.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-a-module-controller.md)
