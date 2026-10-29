# TbThemeService — Developer Guide

**Navigation:** [Previous: TbModuleService](TbModuleService.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: TbResponseService](TbResponseService.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbThemeService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbThemeService.php)

## Overview

Store and manage theme records.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbThemeService;
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
$service = new TbThemeService();
```

### `store()` — save a record using the service and its model

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbThemeService();
// $result = $service->store($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

## Practical LifeTech module example: prepare a theme record for registration

**Scenario:** A developer is building an `MdExample` module and wants to use `TbThemeService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbThemeService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // The store() method needs a populated TbTheme model.
        // $theme = new \Lt\Modules\MdLt\Models\TbTheme();
        // Set required fields after checking your installed schema.
        // $service = new TbThemeService();
        // return $service->store($theme);
        return LtResponse::json('Theme model setup required', '2000', '200');
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Store and manage theme records. See the method reference and practical module scenario for usage.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbThemeService.php)

---

**Navigation:** [Previous: TbModuleService](TbModuleService.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: TbResponseService](TbResponseService.md)
