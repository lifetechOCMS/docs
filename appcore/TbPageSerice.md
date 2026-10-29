# TbPageSerice — Developer Guide

**Navigation:** [Previous: TbPageService](TbPageService.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: TbContentService](TbContentService.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbPageSerice.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPageSerice.php)

## Overview

Legacy or alternate page service with the filename spelling 'Serice'.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbPageSerice;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new TbPageSerice();
$result = $service->fetchPublishPages();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `store($model)` | Instance | `$model` | Save a record using the service and its model. |
| `publishedContent($model)` | Instance | `$model` | Published content in the service. |
| `publishedRegion($model)` | Instance | `$model` | Published region in the service. |
| `fetchPublishPages()` | Instance | `None` | Retrieve published pages. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbPageSerice();
```

### `store()` — save a record using the service and its model

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPageSerice();
// $result = $service->store($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `publishedContent()` — published content in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPageSerice();
// $result = $service->publishedContent($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `publishedRegion()` — published region in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPageSerice();
// $result = $service->publishedRegion($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `fetchPublishPages()` — retrieve published pages

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbPageSerice();
$result = $service->fetchPublishPages();
```

## Practical LifeTech module example: understand the legacy page service

**Scenario:** A developer is building an `MdExample` module and wants to use `TbPageSerice` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbPageSerice;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Legacy file has a similar name to TbPageService.
        // Confirm which implementation your installation actually loads.
        // $service = new TbPageSerice();
        // $pages = $service->fetchPublishPages();
        return LtResponse::json('Review the legacy service before use', '2000', '200');
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Legacy or alternate page service with the filename spelling 'Serice'. See the method reference and practical module scenario for usage.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPageSerice.php)

---

**Navigation:** [Previous: TbPageService](TbPageService.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: TbContentService](TbContentService.md)
