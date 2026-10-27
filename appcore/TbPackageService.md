# TbPackageService — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/TbPackageService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPackageService.php)

## Overview

Manage package registration, marketplace installation, dependencies, imports and exports.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\TbPackageService;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

This service depends on application-specific models or setup. Start by locating a controller that already uses it, and inspect the arguments supplied there. A made-up call could mislead beginners or change application data.

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `__construct()` | Confirm in source | `None` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `store($model)` | Confirm in source | `$model` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `updatePackage($model)` | Confirm in source | `$model` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `filteredPackages()` | Confirm in source | `None` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `validateDependency()` | Confirm in source | `None` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `checkDependencyRequirement($dependencies)` | Confirm in source | `$dependencies` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `browseProductFromMarkePlace()` | Confirm in source | `None` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `installFromMarketplace()` | Confirm in source | `None` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `exportTable()` | Confirm in source | `None` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `exportPackage()` | Confirm in source | `None` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `importPackage()` | Confirm in source | `None` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `togglePublish($model)` | Confirm in source | `$model` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `isDefault($model)` | Confirm in source | `$model` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `dashboardAnalysis()` | Confirm in source | `None` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `importPackageAbstract($path)` | Confirm in source | `$path` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `batchInsertPageContent($pageContents, $batchSize, $userId)` | Confirm in source | `$pageContents, $batchSize, $userId` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `batchUpsert($table, $rows, $skipUpdate)` | Confirm in source | `$table, $rows, $skipUpdate` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `importPackageRecords($table, $records, $columnMap, $fixedValues, $batchSize, $userId)` | Confirm in source | `$table, $records, $columnMap, $fixedValues, $batchSize, $userId` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `insertThemePageRegions($pages, $pageContents, $batchSize, $userId, $now)` | Confirm in source | `$pages, $pageContents, $batchSize, $userId, $now` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |
| `readImportJson($file, $expectList = false)` | Confirm in source | `$file, $expectList = false` | Manage package registration, marketplace installation, dependencies, imports and exports. Exact method behavior, visibility and return type require checking the linked implementation. |

### `__construct()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `__construct(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `store()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `store(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `updatePackage()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `updatePackage(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `filteredPackages()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `filteredPackages(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `validateDependency()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `validateDependency(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `checkDependencyRequirement()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `checkDependencyRequirement(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `browseProductFromMarkePlace()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `browseProductFromMarkePlace(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `installFromMarketplace()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `installFromMarketplace(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `exportTable()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `exportTable(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `exportPackage()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `exportPackage(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `importPackage()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `importPackage(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `togglePublish()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `togglePublish(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `isDefault()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `isDefault(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `dashboardAnalysis()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `dashboardAnalysis(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `importPackageAbstract()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `importPackageAbstract(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `batchInsertPageContent()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `batchInsertPageContent(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `batchUpsert()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `batchUpsert(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `importPackageRecords()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `importPackageRecords(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `insertThemePageRegions()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `insertThemePageRegions(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `readImportJson()` — understanding this method

**Purpose:** Part of the `TbPackageService` service's responsibility: manage package registration, marketplace installation, dependencies, imports and exports.

**How to study it:** Open the source and find `readImportJson(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

## Practical LifeTech module example: display package dashboard statistics

**Scenario:** A developer is building an `MdExample` module and wants to use `TbPackageService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbPackageService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Admin-only action; the service reads package-related records.
        $service = new TbPackageService();
        return $service->dashboardAnalysis();
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

**Source-specific caution:** Package installation/import changes files and database records. Test with backups before production use.

## Summary

Manage package registration, marketplace installation, dependencies, imports and exports. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPackageService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbModuleService](TbModuleService.md)
- [Next: TbPageContentService](TbPageContentService.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
