# tableManagementService — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/tableManagementService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/tableManagementService.php)

## Overview

Perform administrative database table operations.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\tableManagementService;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new tableManagementService();
$result = $service->checkTableExist('EXAMPLE_VALUE');
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `checkTableExist($tableName)` | Instance | `$tableName` | Check table exist. |
| `indexTable()` | Instance | `None` | Index table in the service. |
| `browseTable()` | Instance | `None` | Browse table in the service. |
| `browseTable()` | Instance | `None` | Browse table in the service. |
| `tableStructure()` | Instance | `None` | Table structure in the service. |
| `truncateTable()` | Instance | `None` | Truncate table in the service. |
| `dropTable()` | Instance | `None` | Drop table in the service. |
| `deleteTableRecord()` | Instance | `None` | Delete table record. |
| `createTable()` | Instance | `None` | Create table in the service. |
| `sqlExecute()` | Instance | `None` | Sql execute in the service. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new tableManagementService();
```

### `checkTableExist()` — check table exist

**Call style:** Instance. **Parameters:** `$tableName`.

```php
$service = new tableManagementService();
$result = $service->checkTableExist('EXAMPLE_VALUE');
```

### `indexTable()` — index table in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new tableManagementService();
$result = $service->indexTable();
```

### `browseTable()` — browse table in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new tableManagementService();
$result = $service->browseTable();
```

### `browseTable()` — browse table in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new tableManagementService();
$result = $service->browseTable();
```

### `tableStructure()` — table structure in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new tableManagementService();
$result = $service->tableStructure();
```

### `truncateTable()` — truncate table in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new tableManagementService();
// $result = $service->truncateTable();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `dropTable()` — drop table in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new tableManagementService();
// $result = $service->dropTable();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `deleteTableRecord()` — delete table record

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new tableManagementService();
// $result = $service->deleteTableRecord();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `createTable()` — create table in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new tableManagementService();
// $result = $service->createTable();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `sqlExecute()` — sql execute in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new tableManagementService();
// $result = $service->sqlExecute();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

## Practical LifeTech module example: check whether a database table exists

**Scenario:** A developer is building an `MdExample` module and wants to use `tableManagementService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\tableManagementService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Restrict this controller to database administrators.
        $service = new tableManagementService();
        $exists = $service->checkTableExist('tb_page');
        return LtResponse::json('Table check completed', '2000', '200', [
            'result' => $exists
        ]);
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Perform administrative database table operations. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/tableManagementService.php)
- [Back to MdLt Services index](README.md)
- [Previous: displayError](displayError.md)
- Next: none
