# tableManagementService — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/tableManagementService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/tableManagementService.php)

## Overview

Perform administrative database table operations.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\tableManagementService;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

This service depends on application-specific models or setup. Start by locating a controller that already uses it, and inspect the arguments supplied there. A made-up call could mislead beginners or change application data.

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `__construct()` | Confirm in source | `None` | Perform administrative database table operations. Exact method behavior, visibility and return type require checking the linked implementation. |
| `checkTableExist($tableName)` | Confirm in source | `$tableName` | Perform administrative database table operations. Exact method behavior, visibility and return type require checking the linked implementation. |
| `indexTable()` | Confirm in source | `None` | Perform administrative database table operations. Exact method behavior, visibility and return type require checking the linked implementation. |
| `browseTable()` | Confirm in source | `None` | Perform administrative database table operations. Exact method behavior, visibility and return type require checking the linked implementation. |
| `tableStructure()` | Confirm in source | `None` | Perform administrative database table operations. Exact method behavior, visibility and return type require checking the linked implementation. |
| `truncateTable()` | Confirm in source | `None` | Perform administrative database table operations. Exact method behavior, visibility and return type require checking the linked implementation. |
| `dropTable()` | Confirm in source | `None` | Perform administrative database table operations. Exact method behavior, visibility and return type require checking the linked implementation. |
| `deleteTableRecord()` | Confirm in source | `None` | Perform administrative database table operations. Exact method behavior, visibility and return type require checking the linked implementation. |
| `createTable()` | Confirm in source | `None` | Perform administrative database table operations. Exact method behavior, visibility and return type require checking the linked implementation. |
| `sqlExecute()` | Confirm in source | `None` | Perform administrative database table operations. Exact method behavior, visibility and return type require checking the linked implementation. |

### `__construct()` — understanding this method

**Purpose:** Part of the `tableManagementService` service's responsibility: perform administrative database table operations.

**How to study it:** Open the source and find `__construct(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `checkTableExist()` — understanding this method

**Purpose:** Part of the `tableManagementService` service's responsibility: perform administrative database table operations.

**How to study it:** Open the source and find `checkTableExist(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `indexTable()` — understanding this method

**Purpose:** Part of the `tableManagementService` service's responsibility: perform administrative database table operations.

**How to study it:** Open the source and find `indexTable(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `browseTable()` — understanding this method

**Purpose:** Part of the `tableManagementService` service's responsibility: perform administrative database table operations.

**How to study it:** Open the source and find `browseTable(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `tableStructure()` — understanding this method

**Purpose:** Part of the `tableManagementService` service's responsibility: perform administrative database table operations.

**How to study it:** Open the source and find `tableStructure(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `truncateTable()` — understanding this method

**Purpose:** Part of the `tableManagementService` service's responsibility: perform administrative database table operations.

**How to study it:** Open the source and find `truncateTable(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `dropTable()` — understanding this method

**Purpose:** Part of the `tableManagementService` service's responsibility: perform administrative database table operations.

**How to study it:** Open the source and find `dropTable(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `deleteTableRecord()` — understanding this method

**Purpose:** Part of the `tableManagementService` service's responsibility: perform administrative database table operations.

**How to study it:** Open the source and find `deleteTableRecord(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `createTable()` — understanding this method

**Purpose:** Part of the `tableManagementService` service's responsibility: perform administrative database table operations.

**How to study it:** Open the source and find `createTable(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `sqlExecute()` — understanding this method

**Purpose:** Part of the `tableManagementService` service's responsibility: perform administrative database table operations.

**How to study it:** Open the source and find `sqlExecute(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

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

## Common mistakes

1. Calling an instance method statically, or creating an object when only a static method is needed.
2. Guessing method arguments or return values instead of inspecting the implementation.
3. Running data-changing operations without permissions, validation, and error handling.
4. Assuming a service method is safe to expose as an unauthenticated endpoint.
5. Copying an example without adapting it to your module's model and route configuration.

**Source-specific caution:** These operations can change or delete database structures and data. Restrict to authorized administrators and back up first.

## Summary

Perform administrative database table operations. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/tableManagementService.php)
- [Back to MdLt Services index](README.md)
- [Previous: displayError](displayError.md)
- Next: none

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
