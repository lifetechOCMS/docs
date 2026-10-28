# TbPageContentService — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbPageContentService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPageContentService.php)

## Overview

Connect content to pages and regions, and control publication.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbPageContentService;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new TbPageContentService();
$result = $service->fetchPublished('EXISTING_ID');
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `publishPageContent($model)` | Instance | `$model` | Publish page content in the service. |
| `publishPage($id, $type)` | Instance | `$id, $type` | Publish page in the service. |
| `publishContent($id)` | Instance | `$id` | Publish content in the service. |
| `deletePageContent($ltId = null, $packageName = null)` | Instance | `$ltId, $packageName` | Delete page content. |
| `publishPageRegion($dataArr, $contentRecord = null)` | Instance | `$dataArr, $contentRecord` | Publish page region in the service. |
| `fetchPublished($id, $fetchType='page', $source='region')` | Instance | `$id, $fetchType, $source` | Fetch published using the configured models. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbPageContentService();
```

### `publishPageContent()` — publish page content in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbPageContentService();
// $result = $service->publishPageContent($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `publishPage()` — publish page in the service

**Call style:** Instance. **Parameters:** `$id, $type`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPageContentService();
// $result = $service->publishPage('EXISTING_ID', 'EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `publishContent()` — publish content in the service

**Call style:** Instance. **Parameters:** `$id`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPageContentService();
// $result = $service->publishContent('EXISTING_ID');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `deletePageContent()` — delete page content

**Call style:** Instance. **Parameters:** `$ltId = null, $packageName = null`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPageContentService();
// $result = $service->deletePageContent();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `publishPageRegion()` — publish page region in the service

**Call style:** Instance. **Parameters:** `$dataArr, $contentRecord = null`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbPageContentService();
// $result = $service->publishPageRegion('EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `fetchPublished()` — fetch published using the configured models

**Call style:** Instance. **Parameters:** `$id, $fetchType='page', $source='region'`.

```php
$service = new TbPageContentService();
$result = $service->fetchPublished('EXISTING_ID');
```

## Practical LifeTech module example: fetch published content assigned to a page

**Scenario:** A developer is building an `MdExample` module and wants to use `TbPageContentService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbPageContentService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Replace the ID with an existing page ID from your application.
        $pageId = 'EXISTING_PAGE_ID';
        $service = new TbPageContentService();
        return $service->fetchPublished($pageId, 'page', 'region');
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Connect content to pages and regions, and control publication. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPageContentService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbPackageService](TbPackageService.md)
- [Next: TbPageSerice](TbPageSerice.md)
