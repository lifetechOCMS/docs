# TbPageService — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbPageService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPageService.php)

## Overview

Create and manage pages, publishing, routes and page regions.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbPageService;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new TbPageService();
$result = $service->fetchPublishPages();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `store($model)` | Instance | `$model` | Save a record using the service and its model. |
| `publishedContent($model)` | Instance | `$model` | Published content in the service. |
| `publishedRegion($model)` | Instance | `$model` | Published region in the service. |
| `publishedRoute($model)` | Instance | `$model` | Published route in the service. |
| `toggleRoute($model)` | Instance | `$model` | Toggle route. |
| `fetchPublishPages()` | Instance | `None` | Retrieve published pages. |
| `deletePages($ltId = null, $params = null)` | Instance | `$ltId, $params` | Delete pages. |
| `publishedToRegion()` | Instance | `None` | Published to region in the service. |
| `togglePublished($packageName= null, $isPublished)` | Instance | `$packageName, $isPublished` | Toggle published. |
| `dashboardAnalysis()` | Instance | `None` | Return dashboard-related summary data. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbPageService();
```

### `store()` — save a record using the service and its model

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPageService();
// $result = $service->store($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `publishedContent()` — published content in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPageService();
// $result = $service->publishedContent($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `publishedRegion()` — published region in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPageService();
// $result = $service->publishedRegion($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `publishedRoute()` — published route in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPageService();
// $result = $service->publishedRoute($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `toggleRoute()` — toggle route

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPageService();
// $result = $service->toggleRoute($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `fetchPublishPages()` — retrieve published pages

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbPageService();
$result = $service->fetchPublishPages();
```

### `deletePages()` — delete pages

**Call style:** Instance. **Parameters:** `$ltId = null, $params = null`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPageService();
// $result = $service->deletePages();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `publishedToRegion()` — published to region in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPageService();
// $result = $service->publishedToRegion();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `togglePublished()` — toggle published

**Call style:** Instance. **Parameters:** `$packageName= null, $isPublished`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPageService();
// $result = $service->togglePublished('EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `dashboardAnalysis()` — return dashboard-related summary data

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbPageService();
$result = $service->dashboardAnalysis();
```

## Practical LifeTech module example: load published pages for a navigation screen

**Scenario:** A developer is building an `MdExample` module and wants to use `TbPageService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbPageService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        $service = new TbPageService();
        return $service->fetchPublishPages();
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Create and manage pages, publishing, routes and page regions. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPageService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbPageSerice](TbPageSerice.md)
- [Next: TbResponseService](TbResponseService.md)
