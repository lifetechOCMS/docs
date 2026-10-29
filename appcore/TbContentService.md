# TbContentService — Developer Guide

**Navigation:** [Previous: TbPageSerice](TbPageSerice.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: TbPageContentService](TbPageContentService.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbContentService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbContentService.php)

## Overview

Manage content resources, publishing, file synchronization and layout assignments.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbContentService;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new TbContentService();
$result = $service->autoCreate();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `store($model, $isService)` | Instance | `$model, $isService` | Save a record using the service and its model. |
| `autoCreate()` | Instance | `None` | Auto create in the service. |
| `autoCreateTemplate(string $packageName, string $contentName, string $type, bool $isService = false, string $contentType)` | Instance | `$packageName, $contentName, $type, $isService, $contentType` | Auto create template in the service; declared return `string`. |
| `publishedPage($model)` | Instance | `$model` | Published page in the service. |
| `fetchPublishContent($ltId = null)` | Instance | `$ltId` | Fetch publish content using the configured models. |
| `deleteContent($ltId = null, $packageName = null)` | Instance | `$ltId, $packageName` | Delete content. |
| `togglePublishedContent($packageName= null, $isPublished)` | Instance | `$packageName, $isPublished` | Toggle published content. |
| `download($model)` | Instance | `$model` | Prepare or serve a file download. |
| `upload($model)` | Instance | `$model` | Upload in the service. |
| `dashboardAnalysis()` | Instance | `None` | Return dashboard-related summary data. |
| `synchronizeContent()` | Instance | `None` | Synchronize content in the service. |
| `scanContent()` | Instance | `None` | Scan content in the service. |
| `getFolders()` | Instance | `None` | Read folders from the configured service. |
| `fetchLayouts()` | Instance | `None` | Fetch layouts using the configured models. |
| `assignLayouts($data)` | Instance | `$data` | Assign layouts in the service. |
| `contentRegions()` | Instance | `None` | Content regions in the service. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbContentService();
```

### `store()` — save a record using the service and its model

**Call style:** Instance. **Parameters:** `$model, $isService`.

```php
// $model must be a populated, validated framework model.
// $service = new TbContentService();
// $result = $service->store($model, 'EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `autoCreate()` — auto create in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbContentService();
$result = $service->autoCreate();
```

### `autoCreateTemplate()` — auto create template in the service

**Call style:** Instance. **Parameters:** `string $packageName, string $contentName, string $type, bool $isService = false, string $contentType`.

```php
$service = new TbContentService();
$result = $service->autoCreateTemplate('MdExample', 'EXAMPLE_VALUE', 'EXAMPLE_VALUE', 'EXAMPLE_VALUE');
```

### `publishedPage()` — published page in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbContentService();
// $result = $service->publishedPage($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `fetchPublishContent()` — fetch publish content using the configured models

**Call style:** Instance. **Parameters:** `$ltId = null`.

```php
$service = new TbContentService();
$result = $service->fetchPublishContent();
```

### `deleteContent()` — delete content

**Call style:** Instance. **Parameters:** `$ltId = null, $packageName = null`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbContentService();
// $result = $service->deleteContent();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `togglePublishedContent()` — toggle published content

**Call style:** Instance. **Parameters:** `$packageName= null, $isPublished`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbContentService();
// $result = $service->togglePublishedContent('EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `download()` — prepare or serve a file download

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbContentService();
// $result = $service->download($model);
```

### `upload()` — upload in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbContentService();
// $result = $service->upload($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `dashboardAnalysis()` — return dashboard-related summary data

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbContentService();
$result = $service->dashboardAnalysis();
```

### `synchronizeContent()` — synchronize content in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbContentService();
// $result = $service->synchronizeContent();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `scanContent()` — scan content in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbContentService();
$result = $service->scanContent();
```

### `getFolders()` — read folders from the configured service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbContentService();
$result = $service->getFolders();
```

### `fetchLayouts()` — fetch layouts using the configured models

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbContentService();
$result = $service->fetchLayouts();
```

### `assignLayouts()` — assign layouts in the service

**Call style:** Instance. **Parameters:** `$data`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbContentService();
// $result = $service->assignLayouts(['name' => 'Ada']);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `contentRegions()` — content regions in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbContentService();
$result = $service->contentRegions();
```

## Practical LifeTech module example: list content regions for a theme page

**Scenario:** A developer is building an `MdExample` module and wants to use `TbContentService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbContentService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Requires the framework models, database, and session context.
        $service = new TbContentService();
        $result = $service->contentRegions();
        return $result; // Inspect this method's actual response before exposing it.
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Manage content resources, publishing, file synchronization and layout assignments. See the method reference and practical module scenario for usage.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbContentService.php)

---

**Navigation:** [Previous: TbPageSerice](TbPageSerice.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: TbPageContentService](TbPageContentService.md)
