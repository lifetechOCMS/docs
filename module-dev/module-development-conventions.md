# Module Development Conventions

[Previous](accessing-modules-development.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](add-module-package.md)

LifeTechOCMS follows standardized naming, coding, database, and architectural conventions to ensure consistency, maintainability, and compatibility across module development.

These conventions apply to modules developed within LifeTechOCMS, including their Models, Controllers, Services, database tables, and supporting PHP classes.

## 1. Module Conventions

A module is a package that extends the functionality of LifeTechOCMS.

### Module Naming Rules

1. Module names must use **PascalCase**.
2. All module names must begin with `Md`, representing a LifeTechOCMS module.
3. Module names must clearly describe their purpose.
4. Module names must not contain spaces, hyphens, or underscores.
5. The module package name, directory name, and PHP namespace must use the same module identifier.
6. Every module must include a `package.json` file containing its package information and dependencies.
7. Every module must include a `README.md` file describing its purpose, installation, configuration, and usage.
8. Module PHP classes must follow the `Lt\Modules\ModuleName` namespace convention.

### Module Naming Examples

| Purpose | Module name |
|---|---|
| Blog Management | `MdBlog` |
| Student Management | `MdStudent` |
| Forum Management | `MdForum` |
| Inventory Management | `MdInventory` |
| Learning Management | `MdLmsCourse` |

### Module Namespaces

For a module named `MdBlog`, PHP namespaces follow this pattern (one namespace declaration per file):

```php
namespace Lt\Modules\MdBlog\Controllers;
```

```php
namespace Lt\Modules\MdBlog\Models;
```

```php
namespace Lt\Modules\MdBlog\Services;
```

### Automatically Generated Module Routes

When a new module is created in LifeTechOCMS, its route file is automatically generated.

The route filename follows the convention `{ModuleName}Routes.php` and is stored in the module's `Services/` directory.

| Module | Route file |
|---|---|
| `MdBlog` | `MdBlogRoutes.php` |
| `MdStudent` | `MdStudentRoutes.php` |
| `MdForum` | `MdForumRoutes.php` |

The route file defines routes that connect incoming requests to the appropriate module Controllers. Detailed route configuration is covered separately in the Module Routes documentation.

## 2. Code Style and Naming Conventions

1. Use **4 spaces** for each indentation level. Do not use tabs.
2. Keep lines within **120 characters**.
3. Remove trailing whitespace.
4. Use a space before parentheses in control structures such as `if`, `while`, `for`, and `foreach`.
5. Place opening braces `{` on the same line as the statement, function, method, or class declaration.
6. Use descriptive names for classes, methods, functions, and variables.
7. Use `Lt` or `lt` as the abbreviation for LifeTechOCMS according to the relevant naming convention.

### Example

```php
if ($isActive) {
    foreach ($students as $student) {
        if ($student->hasPermission) {
            // Process student
        }
    }
}
```

### Class and Method Formatting

```php
class TbStudentController {
    public function getStudents() {
        if ($this->hasPermission()) {
            // Retrieve students
        }
    }
}
```

## 3. Database Conventions

LifeTechOCMS requires consistent database naming to support maintainability and predictable relationships between tables and Models.

### Table Naming Rules

1. **All newly created database tables MUST begin with `tb_`.**
2. Table names MUST use **snake_case**.
3. Table names should describe the records they contain.
4. The `tb_` prefix is compulsory for newly created LifeTechOCMS database tables.
5. The only exception is when migrating or integrating existing database tables from another system, where preserving the original name is necessary for compatibility.
6. All database table examples in LifeTechOCMS documentation must use the `tb_` prefix.

### Table Naming Examples

| Purpose | Table name |
|---|---|
| Users | `tb_user` |
| Students | `tb_student` |
| Blog Categories | `tb_blog_category` |
| Blog Posts | `tb_blog_post` |
| Products | `tb_product` |
| Orders | `tb_order` |
| User Roles | `tb_user_role` |

### Column Naming

1. Column names must use **snake_case**.
2. Column names must be descriptive and consistent.
3. Avoid spaces and unnecessary special characters.

Examples: `first_name`, `last_name`, `email_address`, `category_name`, `created_at`, `updated_at`.

### Primary Key Naming

Use `lt_id` as the preferred primary key naming convention for LifeTechOCMS tables.

```sql
CREATE TABLE tb_student (
    lt_id VARCHAR(50) PRIMARY KEY,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    created_at DATETIME NOT NULL,
    updated_at DATETIME NOT NULL
);
```

The primary-key data type should match the identifier format used by the application.

### Foreign Key Naming

Foreign key columns should follow the referenced table name with `_id` appended.

| Referenced table | Foreign key column |
|---|---|
| `tb_user` | `tb_user_id` |
| `tb_student` | `tb_student_id` |
| `tb_blog_category` | `tb_blog_category_id` |
| `tb_product` | `tb_product_id` |

### Pivot Table Naming

Pivot tables must also begin with `tb_` and use `snake_case`, such as `tb_user_role`, `tb_order_product`, and `tb_student_course`.

### Additional Database Rules

1. Include `created_at` and `updated_at` timestamps where applicable.
2. Add indexes to frequently searched or joined columns.
3. Prefer Third Normal Form (3NF) to reduce redundant data.
4. Avoid unnecessary nullable columns, but permit `NULL` when data is genuinely optional or unknown.
5. Use Maplite ORM or prepared statements for database operations.
6. Never concatenate untrusted input directly into SQL queries.

### Prepared Statement Example

```php
$stmt = $pdo->prepare(
    "SELECT * FROM tb_user WHERE email_address = :email"
);

$stmt->execute([
    'email' => $email
]);

$users = $stmt->fetchAll(PDO::FETCH_ASSOC);
```

## 4. Model Conventions

Models represent database tables and provide access to database records.

### Model Naming Rules

1. Model filenames must use **PascalCase**.
2. Model class names must use **PascalCase**.
3. **The Model class name must be the PascalCase conversion of the corresponding database table name.**
4. The Model filename must match its class name and end with `.php`.
5. Each Model should represent one primary database table.
6. Models using the LifeTechOCMS ORM must extend `LtModel`.
7. Model methods must use camelCase.
8. Model classes must be stored in the module's `Models/` directory.

### Examples

| Database table | Model class | Model filename |
|---|---|---|
| `tb_user` | `TbUser` | `TbUser.php` |
| `tb_student` | `TbStudent` | `TbStudent.php` |
| `tb_blog_category` | `TbBlogCategory` | `TbBlogCategory.php` |
| `tb_blog_post` | `TbBlogPost` | `TbBlogPost.php` |

### Model Example

**File:** `TbStudent.php`

```php
<?php

namespace Lt\Modules\MdStudent\Models;

class TbStudent extends \LtModel {
}
```

## 5. Controller Conventions

Controllers handle incoming requests and coordinate module operations.

### Controller Naming Rules

1. **All Controller filenames must use PascalCase and end with `Controller.php`.**
2. Controller class names must match their filenames.
3. Controllers associated with a Model must use the corresponding Model class name followed by `Controller`.
4. Controllers not directly associated with a Model must still use descriptive PascalCase names ending with `Controller`.
5. Controller methods must use camelCase.
6. Controllers should focus on request handling and delegate business logic to Services.
7. Controllers must be stored in the module's `Controllers/` directory.

### Model-Based Controller Examples

| Database table | Model class | Controller class |
|---|---|---|
| `tb_user` | `TbUser` | `TbUserController` |
| `tb_student` | `TbStudent` | `TbStudentController` |
| `tb_blog_category` | `TbBlogCategory` | `TbBlogCategoryController` |
| `tb_blog_post` | `TbBlogPost` | `TbBlogPostController` |

### Controller Example

**File:** `TbStudentController.php`

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

The name `TbStudentController` indicates its relationship with the `TbStudent` Model, which represents the `tb_student` table.

## 6. Service Conventions

Services contain reusable business logic and coordinate operations between Controllers, Models, and other framework services.

### Service Naming Rules

1. **All application Service filenames must use PascalCase and end with `Service.php`.**
2. Service class names must match their filenames.
3. Services associated with a Model must use the corresponding Model class name followed by `Service`.
4. Services not directly associated with a Model must use descriptive PascalCase names ending with `Service`.
5. Service methods must use camelCase.
6. Services must be stored in the module's `Services/` directory.
7. Services should contain business logic rather than presentation logic.
8. Services may communicate with Models and other LifeTechOCMS Core Services.

### Model-Based Service Examples

| Database table | Model class | Service class |
|---|---|---|
| `tb_user` | `TbUser` | `TbUserService` |
| `tb_student` | `TbStudent` | `TbStudentService` |
| `tb_blog_category` | `TbBlogCategory` | `TbBlogCategoryService` |
| `tb_blog_post` | `TbBlogPost` | `TbBlogPostService` |

### Service Example

**File:** `TbStudentService.php`

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

### Model, Controller, and Service Relationship

| Component | Name |
|---|---|
| Module | `MdStudent` |
| Database table | `tb_student` |
| Model | `TbStudent.php` |
| Controller | `TbStudentController.php` |
| Service | `TbStudentService.php` |
| Route file | `MdStudentRoutes.php` |

**Note:** Route files are stored in the `Services/` directory but follow the `Routes.php` suffix, not `Service.php`.

## 7. Class Conventions

1. Class names must use **PascalCase**.
2. General LifeTechOCMS framework classes must use the `Lt` prefix.
3. Module-specific classes do not require the `Lt` prefix.
4. Database Model classes must follow the Model naming convention.
5. Class methods must use camelCase.
6. Class methods must not automatically begin with `Lt`.
7. Private and protected class properties must begin with an underscore.
8. Classes must use the appropriate PHP namespace.

### Examples

| Class type | Example |
|---|---|
| Framework Service | `LtSession` |
| Framework Request | `LtRequest` |
| Framework Response | `LtResponse` |
| Model | `TbStudent` |
| Controller | `TbStudentController` |
| Service | `TbStudentService` |
| Module Helper | `StudentFormatter` |

```php
class TbStudentService {
    private $_apiKey;
    protected $_studentModel;

    public function getStudents() {
        // Retrieve student records
    }
}
```

## 8. Variable Conventions

1. Variable names must use **camelCase**.
2. Constants must use **UPPER_SNAKE_CASE**.
3. Boolean variables should begin with `is`, `has`, or `can`.
4. Private and protected class properties must begin with an underscore.
5. Use descriptive variable names.

```php
$userName = 'Student';
$itemQty = 10;

$isActive = true;
$hasPermission = false;
$canEdit = true;

define('APP_VERSION', '1.0.0');
```

## 9. Function Conventions

These rules apply to standalone LifeTechOCMS helper functions.

1. Function names must use **camelCase**.
2. LifeTechOCMS-specific global helper functions must begin with lowercase `lt`.
3. Function names must describe their purpose.
4. Opening braces must be placed on the same line as the function declaration.
5. No space should appear between the function name and its parentheses.
6. Class methods do not require the `lt` prefix.

### Global Function Example

```php
function ltCalculateTax($price) {
    return $price * 0.075;
}
```

### Class Method Example

```php
class TbStudentService {
    public function getStudents() {
        // Retrieve student records
    }
}
```

## 10. Recommended Development Practices

### Framework Integration

1. Reuse existing LifeTechOCMS Core Services whenever appropriate.
2. Use `LtRequest` for request handling.
3. Use `LtResponse` for standardized API responses.
4. Use `LtValidator` for input validation where applicable.
5. Use `LtSession` for session-related operations.
6. Use `LtAuth` for authentication and authorization where supported.
7. Use the framework's Model and Service facilities for database operations and business logic.

### Module Architecture

1. Separate Models, Controllers, Services, and Views.
2. Keep Controllers focused on request handling.
3. Keep business logic in Services.
4. Keep database operations within the appropriate data-access layer.
5. Avoid unnecessary dependencies between modules.
6. Document module dependencies and configuration.

### Security

1. Validate incoming data before processing.
2. Use prepared statements or safe ORM methods.
3. Never hardcode passwords, API keys, or access tokens.
4. Apply authentication and authorization checks where required.
5. Avoid exposing sensitive internal error details to end users.

### Documentation and Maintenance

1. Maintain an up-to-date `README.md`.
2. Document installation, configuration, and dependencies.
3. Document public API endpoints where applicable.
4. Use meaningful Git commit messages.
5. Test modules before publishing.
6. Report defects and observations through the LifeTechOCMS issue tracker.

## References

- [LifeTechOCMS Core Services](../../appcore/README.md)
- [MdLt Framework](https://github.com/lifetechOCMS/MdLt)
- [MdBlog Reference Module](https://github.com/adedayoAdetunji/MdBlog)

---

[Previous](accessing-modules-development.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](add-module-package.md)
