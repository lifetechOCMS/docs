# Create a Database Table and Model

[Previous](understand-the-mvc-architecture.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](create-a-module-service.md)

*Section: Creating module components*

Before writing a Model, define the database table and verify the columns. **Every new LifeTechOCMS table starts with `tb_`.** Only existing tables migrated from another system may be exempt from the naming requirement.

## Example: `tb_student`

```sql
CREATE TABLE tb_student (
    lt_id VARCHAR(50) PRIMARY KEY,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    created_at DATETIME NOT NULL,
    updated_at DATETIME NOT NULL
);
```

The corresponding Model class is the PascalCase conversion of the table name:

```php
<?php
namespace Lt\Modules\MdStudent\Models;

class TbStudent extends \LtModel {
}
```

Use `Models/TbStudent.php`. Check the model-to-table mapping required by your installed ORM; do not assume the example alone establishes all schema metadata. See [LtModel](../appcore/LtModel.md).

---

[Previous](understand-the-mvc-architecture.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](create-a-module-service.md)
