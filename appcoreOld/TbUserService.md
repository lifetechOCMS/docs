# TbUserService — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbUserService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbUserService.php)

## Overview

Manage user records and password-reset flows.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbUserService;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new TbUserService();
$result = $service->dashboardAnalysis();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `store($model)` | Instance | `$model` | Save a record using the service and its model. |
| `dashboardAnalysis()` | Instance | `None` | Return dashboard-related summary data. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbUserService();
```

### `store()` — save a record using the service and its model

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbUserService();
// $result = $service->store($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `dashboardAnalysis()` — return dashboard-related summary data

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbUserService();
$result = $service->dashboardAnalysis();
```

## Practical LifeTech module example: show user dashboard analysis to an administrator

**Scenario:** A developer is building an `MdExample` module and wants to use `TbUserService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbUserService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Only expose this action to authorized administrators.
        $service = new TbUserService();
        return $service->dashboardAnalysis();
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Manage user records and password-reset flows. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbUserService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbThemeService](TbThemeService.md)
- [Next: displayError](displayError.md)
