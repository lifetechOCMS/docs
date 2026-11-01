# Create a Database Table and Model

[Previous](understand-the-mvc-architecture.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-a-module-service.md)

*Section: Creating module content*

A **database table** stores the module's records, while a **Model** is the PHP class used to interact with those records. In LifeTechOCMS, **create the database table in the backend first**, then create its corresponding Model as module content.

## Step 1: Create the database table in the backend

Open the LifeTechOCMS backend database/table management interface and create a table for the information your module needs. Every newly created module table should use the `tb_` prefix and **snake_case** naming.

| Purpose | Database table | Corresponding Model |
| --- | --- | --- |
| Student records | `tb_student` | `TbStudent` |
| Blog categories | `tb_blog_category` | `TbBlogCategory` |
| Blog posts | `tb_blog_post` | `TbBlogPost` |

For example, a student table could contain the following columns (illustrative schema):

| Column | Purpose |
| --- | --- |
| `lt_id` | Primary identifier for the record |
| `student_name` | Student's name |
| `email` | Student's email address |
| `created_at` | Record creation timestamp |
| `updated_at` | Last update timestamp |

Choose the appropriate SQL types, nullability, indexes and constraints in the backend. Save the table and verify that it exists **before** creating the Model. Do not assume the example columns are created automatically.

## Step 2: Create the Model as module content

Once the table exists, open your module's content management area. You can use **Auto-Create Model, Controller and Service** to select the existing database table and generate the Model, or create the Model content manually if appropriate.

For `tb_student`, use:

- **Content type:** Model
- **Model name:** `TbStudent`
- **File location:** `Models/TbStudent.php`
- **PHP namespace:** `Lt\Modules\MdStudent\Models` (for a module named `MdStudent`)

The following minimal Model illustrates the class structure:

```php
<?php

namespace Lt\Modules\MdStudent\Models;

class TbStudent extends \LtModel
{
}
```

The class extends LifeTechOCMS's `\LtModel`, which supplies the framework's shared model behavior. This example demonstrates naming and inheritance; the exact database mapping and supported query methods should be checked against the installed `LtModel` implementation.

## Step 3: Understand how the table and Model work together

```text
Database table: tb_student
          ↑↓
Model: Models/TbStudent.php
          ↑↓
Service: Services/TbStudentService.php
          ↑↓
Controller: Controllers/TbStudentController.php
          ↑↓
Module route / API endpoint
```

- **Table:** Stores the actual student data.
- **Model:** Represents the table in PHP and provides access to database operations through the framework.
- **Service:** Contains application rules, such as validating a student registration workflow or coordinating multiple Models.
- **Controller:** Receives a routed request and delegates the work to the Service.

A Model is **not** the database table itself. Creating a PHP Model file does not, by itself, guarantee that its database table exists.

## Practical MdBlog example

MdBlog follows the same naming convention:

```text
Database table: tb_blog_category
Module: MdBlog
Model file: Models/TbBlogCategory.php
Class: Lt\Modules\MdBlog\Models\TbBlogCategory
```

Its minimal class structure is:

```php
<?php

namespace Lt\Modules\MdBlog\Models;

class TbBlogCategory extends \LtModel
{
}
```

You can examine the [MdBlog repository](https://github.com/adedayoAdetunji/MdBlog) to see the module's Models and related Services and Controllers.

## Before moving to the next lesson

Confirm that your table exists, begins with `tb_`, and has the columns and constraints your module needs. Check that the Model's filename, class name and namespace follow the table naming convention. If you generated the Model using **Auto-Create**, review the generated content before extending it.

For framework-level database operations, see [LtModel — Developer Guide](../../appcore/LtModel.md). The next lesson explains how a **Service** uses the Model to implement module operations.

---

[Previous](understand-the-mvc-architecture.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-a-module-service.md)
