# Module Development Conventions

[Previous](accessing-modules-development.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](add-module-package.md)

*Section: Getting started*

LifeTechOCMS uses consistent naming and coding conventions across modules. These rules apply to **new development**; migrated existing database tables may retain their original names when compatibility requires it.

## Module conventions

1. Module names **must** use PascalCase and start with `Md`, e.g. `MdBlog`, `MdStudent`, `MdForum`.
2. Keep the module directory, package identifier and PHP namespace consistent: `Lt\Modules\MdBlog`.
3. Maintain `package.json` and `README.md` for package metadata and documentation.
4. **A route file is automatically generated when a module is created.** It is named `{ModuleName}Routes.php` and saved in `Services/`, e.g. `Services/MdBlogRoutes.php`.

## Code style

- Use four spaces, no tabs, no trailing whitespace, and aim for lines of 120 characters or fewer.
- Use a space in control statements (`if ($ready)`) and put opening braces on the same line.
- Class names use PascalCase; methods and variables use camelCase.
- Private and protected properties begin with an underscore, e.g. `$_studentModel`.
- Constants use UPPER_SNAKE_CASE; boolean variables preferably begin `is`, `has`, or `can`.
- LifeTechOCMS-specific global helper functions begin with lowercase `lt`; class methods do not require that prefix.

## Database conventions

1. **Every newly created table MUST begin with `tb_`** and use snake_case. This includes pivot tables.
2. The sole naming exception concerns existing tables migrated or integrated from another system.
3. Columns use snake_case; `lt_id` is the preferred primary-key name.
4. Use descriptive foreign keys, e.g. `tb_user_id`, and timestamps `created_at`, `updated_at` where appropriate.
5. Use indexes, appropriate normalization, prepared statements or safe ORM operations.

| Database table | Model class | Controller class | Service class |
|---|---|---|---|
| `tb_user` | `TbUser` | `TbUserController` | `TbUserService` |
| `tb_student` | `TbStudent` | `TbStudentController` | `TbStudentService` |
| `tb_blog_category` | `TbBlogCategory` | `TbBlogCategoryController` | `TbBlogCategoryService` |

## Model conventions

- **Convert the complete table name to PascalCase**: `tb_student` → `TbStudent`.
- The Model class and filename match, e.g. `Models/TbStudent.php`.
- Models using the framework ORM extend `\LtModel`.

```php
<?php
namespace Lt\Modules\MdStudent\Models;

class TbStudent extends \LtModel {
}
```

## Controller conventions

- **Every Controller filename and class ends with `Controller`**.
- A Controller associated with a Model must use the **exact Model name** plus `Controller`, e.g. `TbStudentController.php`.
- Controllers not tied to one Model still use descriptive PascalCase names ending in `Controller`.
- Keep Controllers focused on request handling; delegate business logic to Services.

## Service conventions

- **Every application business Service filename and class ends with `Service`**.
- A Model-associated Service uses the **exact Model name** plus `Service`, e.g. `TbStudentService.php`.
- Other business Services also end in `Service`.
- Route files are an exception to the Service suffix because they are route definitions: `MdStudentRoutes.php` lives in `Services/`.

## Recommended practices

Use `LtRequest`, `LtValidator`, `LtResponse`, `LtSession` and `LtAuth` as appropriate. Keep database operations in Models/data-access code, business logic in Services, and request handling in Controllers. Validate inputs, authorize sensitive operations, avoid hardcoded credentials, and use **four-digit application response codes** from the official reference.

See [Core Services](../appcore/README.md) and [MdBlog](https://github.com/adedayoAdetunji/MdBlog).

---

[Previous](accessing-modules-development.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](add-module-package.md)
