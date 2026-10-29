# LtService — Developer Guide

**Navigation:** [Previous: LtModel](LtModel.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: tableManagementService](tableManagementService.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtService.php)

## Overview

Provide shared utilities for IDs, boolean-like values and database columns.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtService;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$result = LtService::getIsValue('yes');
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `getIsValue($raw)` | Static | `$raw` | Convert common truthy/falsy strings to 1, 0 or null. |
| `generateLtId($length = 12)` | Static | `$length` | Generate a short alphanumeric identifier. |
| `alterTableColumn($tables, $column, $type = 'TINYINT(1)', $default = 0)` | Static | `$tables, $column, $type, $default` | Alter table column in the service. |
| `dropTableColumn($tables, $column)` | Static | `$tables, $column` | Drop table column in the service. |

## Public methods with examples

### `getIsValue()` — convert common truthy/falsy strings to 1, 0 or null

**Call style:** Static. **Parameters:** `$raw`.

```php
$result = LtService::getIsValue('yes');
```

### `generateLtId()` — generate a short alphanumeric identifier

**Call style:** Static. **Parameters:** `$length = 12`.

```php
$result = LtService::generateLtId();
```

### `alterTableColumn()` — alter table column in the service

**Call style:** Static. **Parameters:** `$tables, $column, $type = 'TINYINT(1)', $default = 0`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtService::alterTableColumn(['tb_example'], 'is_enabled');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `dropTableColumn()` — drop table column in the service

**Call style:** Static. **Parameters:** `$tables, $column`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtService::dropTableColumn(['tb_example'], 'is_enabled');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

## Practical LifeTech module example: normalize an enabled flag from a request

**Scenario:** A developer is building an `MdExample` module and wants to use `LtService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\LtService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        $enabled = LtService::getIsValue('yes'); // 1
        return LtResponse::json('Flag normalized', '2000', '200', [
            'enabled' => $enabled
        ]);
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Provide shared utilities for IDs, boolean-like values and database columns. See the method reference and practical module scenario for usage.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtService.php)

---

**Navigation:** [Previous: LtModel](LtModel.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: tableManagementService](tableManagementService.md)
