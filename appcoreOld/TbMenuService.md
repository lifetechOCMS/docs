# TbMenuService — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbMenuService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbMenuService.php)

## Overview

Create, delete and publish navigation menu records.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbMenuService;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new TbMenuService();
$result = $service->getMenuId('MdExample');
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `store($model)` | Instance | `$model` | Save a record using the service and its model. |
| `deleteMenu($ltId = null, $params = null)` | Instance | `$ltId, $params` | Delete menu. |
| `getMenuId($packageName)` | Instance | `$packageName` | Read menu id from the configured service. |
| `dashboardAnalysis()` | Instance | `None` | Return dashboard-related summary data. |
| `togglePublishedMenu($packageName= null, $isPublished)` | Instance | `$packageName, $isPublished` | Toggle published menu. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbMenuService();
```

### `store()` — save a record using the service and its model

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbMenuService();
// $result = $service->store($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `deleteMenu()` — delete menu

**Call style:** Instance. **Parameters:** `$ltId = null, $params = null`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbMenuService();
// $result = $service->deleteMenu();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `getMenuId()` — read menu id from the configured service

**Call style:** Instance. **Parameters:** `$packageName`.

```php
$service = new TbMenuService();
$result = $service->getMenuId('MdExample');
```

### `dashboardAnalysis()` — return dashboard-related summary data

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbMenuService();
$result = $service->dashboardAnalysis();
```

### `togglePublishedMenu()` — toggle published menu

**Call style:** Instance. **Parameters:** `$packageName= null, $isPublished`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbMenuService();
// $result = $service->togglePublishedMenu('EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

## Practical LifeTech module example: find the menu identifier for a package

**Scenario:** A developer is building an `MdExample` module and wants to use `TbMenuService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbMenuService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        $service = new TbMenuService();
        $menuId = $service->getMenuId('MdExample');
        return LtResponse::json('Package menu lookup completed', '2000', '200', [
            'menuId' => $menuId
        ]);
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Create, delete and publish navigation menu records. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbMenuService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbLoginAuditService](TbLoginAuditService.md)
- [Next: TbModuleService](TbModuleService.md)
