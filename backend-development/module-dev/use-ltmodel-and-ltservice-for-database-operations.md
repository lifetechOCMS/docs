# Use LtModel (Maplite) for Database Operations

[Previous](return-api-responses-with-ltresponse.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](manage-authentication-sessions-and-permissions.md)

*Section: Working with Core Services (MdLt)*

## Overview

**Maplite** is the ORM (Object–Relational Mapping) layer used by LifeTech OCMS. A module works with its database through a model that extends the global `\LtModel` class. The model exposes the database operations used by the module's Service, so the Controller can focus on HTTP input and API responses.

The usual flow is:

```text
HTTP request → Controller → Module Service → Module Model (\LtModel / Maplite) → Database
                                             ← query result ←
```

The following examples use the actual [MdBlog module](https://github.com/adedayoAdetunji/MdBlog) to demonstrate the available operations. They are not a complete reference to every Maplite feature.

## 1. Understand Maplite and LtModel

| Part | Responsibility |
| --- | --- |
| **Maplite** | LifeTech's ORM layer for model-based database access. |
| **`\LtModel`** | Base model inherited by module models to expose ORM operations. |
| **Module model** | Represents a module's database entity, for example `TbBlogCategory`. |
| **Module Service** | Implements business rules and calls model operations. |
| **Controller** | Handles the HTTP endpoint and coordinates the Service and response. |

> **Naming distinction:** The global `\LtModel` inherited by MdBlog models is not the same as the namespaced `Lt\Modules\MdLt\Services\LtModel` file. At the time of review, the latter source file is empty. Use the model pattern demonstrated in MdBlog rather than importing that empty service as an ORM.

## 2. Create a model using `\LtModel`

MdBlog's actual [`Models/TbBlogCategory.php`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Models/TbBlogCategory.php) contains:

```php
<?php
namespace Lt\Modules\MdBlog\Models;

class TbBlogCategory extends \LtModel
{
}
```

Although the model class contains no custom methods, its Service can use the database operations provided through the inherited model behavior. In this pattern, the model is not required to implement its own SQL for routine reads and writes.

## 3. Initialize the Maplite model in MdBlog

The following excerpt shows how MdBlog uses the model; the focus here is the model, not general-purpose services. It is adapted from MdBlog's actual [`TbBlogCategoryService.php`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php):

```php
<?php
namespace Lt\Modules\MdBlog\Services;

use Lt\Modules\MdBlog\Models\TbBlogCategory;
use Lt\Modules\MdLt\Services\LtRequest;

class TbBlogCategoryService
{
    protected $blogModel;
    protected $request;

    public function __construct()
    {
        $this->blogModel = new TbBlogCategory();
        $this->request = new LtRequest();
    }
}
```

The category Service holds the Maplite model instance in `$this->blogModel` and calls its database methods.

## 4. Read records with `select()`, `where()` and `get()`

This is the query pattern in MdBlog's category `index()` method:

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

- `select()` begins a read query.
- `where('status', '=', $status)` adds a condition only when a status filter was supplied.
- `get()` executes the built query and returns the results.

To request particular columns, MdBlog uses:

```php
$query = $this->blogModel->select('lt_id, category_name');
return $query->get();
```

**Column naming:** The `select()` example above uses the actual database column names from MdBlog. Other examples in the same Service refer to model properties such as `categoryName` and `ltId`. Follow the model/Maplite conventions of the installed version rather than assuming raw SQL names and model property names are interchangeable in every context.

## 5. Read a record by identifier

MdBlog checks whether a category exists before updating or deleting it:

```php
$existing = $this->blogModel
    ->select()
    ->where('ltId', '=', $ltId)
    ->get();

if (count($existing) < 1) {
    // Handle missing category before attempting a write.
}
```

This example demonstrates chaining a condition onto a model query. Check for an empty result before accessing a record.

## 6. Insert a record

MdBlog's `store()` method uses the following Maplite-related operations, shown here as an excerpt rather than a complete method:

```php
$this->blogModel->processRequest();

$categoryName = trim((string) $this->blogModel->categoryName);

// Perform required-field and duplicate checks before insertion.

$this->blogModel->ltId = $this->ltId;
$this->blogModel->createdAt = $this->ltNow;
$this->blogModel->updatedAt = $this->ltNow;

$this->blogModel->insert();
return $this->blogModel->responseJson();
```

`processRequest()` populates the model from incoming request data in this implementation. The Service then inspects the populated values, applies business rules, assigns additional fields and calls `insert()`.

**Important:** Validate and authorize input before a database write. Do not pass arbitrary client-supplied fields into persistence without checking which fields are permitted. The snippet intentionally omits MdBlog's surrounding duplicate/required-field logic; see the full source before reusing it.

## 7. Update a record

After confirming the category exists and validating the changes, MdBlog uses:

```php
$this->blogModel->processRequest();
$this->blogModel->updatedAt = $this->ltNow;

$this->blogModel->update('ltId', '=', $ltId);
return $this->blogModel->responseJson();
```

The `update()` arguments identify the record to update. The new values are held by the model. The full Service checks existence first.

## 8. Delete a record

After checking that a category exists, MdBlog deletes it with:

```php
$this->blogModel->delete('ltId', '=', $ltId);
```

The method arguments specify the record condition. Confirm permissions and the intended record before executing destructive operations.

## 9. Update a single field

MdBlog's `toggleActive()` reads the existing record, determines the next status, and updates the model:

```php
$row = $this->blogModel
    ->select()
    ->where('ltId', '=', $ltId)
    ->get();

if (count($row) < 1) {
    // Return an appropriate not-found response.
}

$current = $row[0]->status;
$newVal = ($current == 'isActive') ? 'isNotActive' : 'isActive';

$this->blogModel->status = $newVal;
$this->blogModel->updatedAt = $this->ltNow;
$this->blogModel->update('ltId', '=', $ltId);
```

The important pattern is **read → apply a business rule → set model properties → update**. The example is a partial excerpt; handle the missing-record branch before continuing.

## 11. Recommended module workflow

1. Define the module's database table and create its model class extending `\LtModel`.
2. Create a module Service and instantiate or inject the model.
3. Read incoming parameters through `LtRequest` and validate them with the available validation tools.
4. Apply business rules in the Service, such as required fields, uniqueness and permission checks.
5. Use Maplite model methods to read or write data.
6. Return a consistent API response from the Controller or Service.

**Response-code requirement:** For newly developed modules, use registered **four-digit module-specific response codes in the `4000–5999` customized range**, with response category `200` for success or `100` for failure. MdBlog's existing code includes older response codes, which should not be copied as the standard for new modules.

## 12. Practical example: category list API

A category-list operation can follow this flow:

```text
GET /blogs/categories
    ↓
TbBlogCategoryController@index
    ↓
TbBlogCategoryService@index
    ↓
TbBlogCategory (extends \LtModel)
    ↓
select() → optional where() → get()
    ↓
Records returned to the caller
```

The flow illustrates separation of responsibilities: routing and HTTP handling belong to the Controller, database queries and business rules belong to the Service, and Maplite-powered operations are accessed through the model.

## 13. Further reading and source code

- [MdBlog category model](https://github.com/adedayoAdetunji/MdBlog/blob/main/Models/TbBlogCategory.php)
- [MdBlog category Service](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php)
- [MdBlog tag Service](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogTagService.php)
- [LtModel — AppCore reference](../../appcore/LtModel.md) — currently documents the empty namespaced MdLt service file, **not** the global `\LtModel` ORM implementation.
- [Create a Module Service](create-a-module-service.md)
- [Validate Input with LtValidator](validate-input-with-ltvalidator.md)
- [Return API Responses with LtResponse](return-api-responses-with-ltresponse.md)

> **Scope note:** The MdBlog files verify the Maplite-backed model usage shown here. The underlying implementation of the global `\LtModel` and Maplite's complete API was not established from these sources, so this guide intentionally avoids inventing additional ORM methods or configuration rules.

---

[Previous](return-api-responses-with-ltresponse.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](manage-authentication-sessions-and-permissions.md)
