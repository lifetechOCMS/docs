# TbModuleService — Developer Guide

**Navigation:** [Previous: TbPackageService](TbPackageService.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: TbThemeService](TbThemeService.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbModuleService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbModuleService.php)

## Overview

Store and manage module records.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbModuleService;
```

## Quick start

This service primarily changes application state or needs configured framework models. The examples below show the calling pattern, with potentially destructive calls commented out.

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `store($model)` | Instance | `$model` | Save a record using the service and its model. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbModuleService();
```

### `store()` — save a record using the service and its model

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbModuleService();
// $result = $service->store($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

## Practical LifeTech module example: register a module record

**Scenario:** A developer is building an `MdExample` module and wants to use `TbModuleService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbModuleService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Requires a populated TbModule model and authorized admin context.
        // $module = new \Lt\Modules\MdLt\Models\TbModule();
        // Set fields according to your installed schema, then:
        // $service = new TbModuleService();
        // return $service->store($module);
        return LtResponse::json('See the model setup steps above', '2000', '200');
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Store and manage module records. See the method reference and practical module scenario for usage.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbModuleService.php)

---

**Navigation:** [Previous: TbPackageService](TbPackageService.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: TbThemeService](TbThemeService.md)
