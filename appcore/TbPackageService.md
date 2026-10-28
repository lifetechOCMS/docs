# TbPackageService — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbPackageService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPackageService.php)

## Overview

Manage package registration, marketplace installation, dependencies, imports and exports.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbPackageService;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new TbPackageService();
$result = $service->filteredPackages();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `store($model)` | Instance | `$model` | Save a record using the service and its model. |
| `updatePackage($model)` | Instance | `$model` | Update package in the service. |
| `filteredPackages()` | Instance | `None` | Filtered packages in the service. |
| `validateDependency()` | Instance | `None` | Validate dependency in the service. |
| `checkDependencyRequirement($dependencies)` | Instance | `$dependencies` | Check dependency requirement. |
| `browseProductFromMarkePlace()` | Instance | `None` | Browse product from marke place in the service. |
| `installFromMarketplace()` | Instance | `None` | Install from marketplace in the service. |
| `exportTable()` | Instance | `None` | Export table in the service. |
| `exportPackage()` | Instance | `None` | Export package in the service. |
| `zipFolder($folderPath, $zipFilePath)` | Instance | `$folderPath, $zipFilePath` | Zip folder in the service. |
| `importPackage()` | Instance | `None` | Import package in the service. |
| `togglePublish($model)` | Instance | `$model` | Toggle publish. |
| `isDefault($model)` | Instance | `$model` | Check default status. |
| `dashboardAnalysis()` | Instance | `None` | Return dashboard-related summary data. |
| `importPackageAbstract($path)` | Instance | `$path` | Import package abstract in the service. |
| `batchInsertPageContent(array $pageContents, int $batchSize, $userId)` | Instance | `$pageContents, $batchSize, $userId` | Batch insert page content in the service; declared return `void`. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbPackageService();
```

### `store()` — save a record using the service and its model

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPackageService();
// $result = $service->store($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `updatePackage()` — update package in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPackageService();
// $result = $service->updatePackage($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `filteredPackages()` — filtered packages in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbPackageService();
$result = $service->filteredPackages();
```

### `validateDependency()` — validate dependency in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbPackageService();
$result = $service->validateDependency();
```

### `checkDependencyRequirement()` — check dependency requirement

**Call style:** Instance. **Parameters:** `$dependencies`.

```php
$service = new TbPackageService();
$result = $service->checkDependencyRequirement('EXAMPLE_VALUE');
```

### `browseProductFromMarkePlace()` — browse product from marke place in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbPackageService();
$result = $service->browseProductFromMarkePlace();
```

### `installFromMarketplace()` — install from marketplace in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPackageService();
// $result = $service->installFromMarketplace();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `exportTable()` — export table in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPackageService();
// $result = $service->exportTable();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `exportPackage()` — export package in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPackageService();
// $result = $service->exportPackage();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `zipFolder()` — zip folder in the service

**Call style:** Instance. **Parameters:** `$folderPath, $zipFilePath`.

```php
$service = new TbPackageService();
$result = $service->zipFolder('EXAMPLE_VALUE', 'EXAMPLE_VALUE');
```

### `importPackage()` — import package in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPackageService();
// $result = $service->importPackage();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `togglePublish()` — toggle publish

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPackageService();
// $result = $service->togglePublish($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `isDefault()` — check default status

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPackageService();
// $result = $service->isDefault($model);
```

### `dashboardAnalysis()` — return dashboard-related summary data

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbPackageService();
$result = $service->dashboardAnalysis();
```

### `importPackageAbstract()` — import package abstract in the service

**Call style:** Instance. **Parameters:** `$path`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPackageService();
// $result = $service->importPackageAbstract('packages/modules/MdExample/Storage');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `batchInsertPageContent()` — batch insert page content in the service

**Call style:** Instance. **Parameters:** `array $pageContents, int $batchSize, $userId`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPackageService();
// $result = $service->batchInsertPageContent('EXAMPLE_VALUE', 'EXAMPLE_VALUE', 'EXISTING_ID');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

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

## Summary

Manage package registration, marketplace installation, dependencies, imports and exports. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPackageService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbModuleService](TbModuleService.md)
- [Next: TbPageContentService](TbPageContentService.md)
