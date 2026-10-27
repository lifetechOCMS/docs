# TbPageContentService — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/TbPageContentService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPageContentService.php)

## Overview

Connect content to pages and regions, and control publication.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\TbPageContentService;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

This service depends on application-specific models or setup. Start by locating a controller that already uses it, and inspect the arguments supplied there. A made-up call could mislead beginners or change application data.

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `__construct()` | Confirm in source | `None` | Connect content to pages and regions, and control publication. Exact method behavior, visibility and return type require checking the linked implementation. |
| `publishPageContent($model)` | Confirm in source | `$model` | Connect content to pages and regions, and control publication. Exact method behavior, visibility and return type require checking the linked implementation. |
| `publishPage($id, $type)` | Confirm in source | `$id, $type` | Connect content to pages and regions, and control publication. Exact method behavior, visibility and return type require checking the linked implementation. |
| `publishContent($id)` | Confirm in source | `$id` | Connect content to pages and regions, and control publication. Exact method behavior, visibility and return type require checking the linked implementation. |
| `deletePageContent($ltId = null, $packageName = null)` | Confirm in source | `$ltId = null, $packageName = null` | Connect content to pages and regions, and control publication. Exact method behavior, visibility and return type require checking the linked implementation. |
| `publishPageRegion($dataArr, $contentRecord = null)` | Confirm in source | `$dataArr, $contentRecord = null` | Connect content to pages and regions, and control publication. Exact method behavior, visibility and return type require checking the linked implementation. |
| `fetchPublished($id, $fetchType = 'page', $source = 'region')` | Confirm in source | `$id, $fetchType = 'page', $source = 'region'` | Connect content to pages and regions, and control publication. Exact method behavior, visibility and return type require checking the linked implementation. |

### `__construct()` — understanding this method

**Purpose:** Part of the `TbPageContentService` service's responsibility: connect content to pages and regions, and control publication.

**How to study it:** Open the source and find `__construct(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `publishPageContent()` — understanding this method

**Purpose:** Part of the `TbPageContentService` service's responsibility: connect content to pages and regions, and control publication.

**How to study it:** Open the source and find `publishPageContent(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `publishPage()` — understanding this method

**Purpose:** Part of the `TbPageContentService` service's responsibility: connect content to pages and regions, and control publication.

**How to study it:** Open the source and find `publishPage(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `publishContent()` — understanding this method

**Purpose:** Part of the `TbPageContentService` service's responsibility: connect content to pages and regions, and control publication.

**How to study it:** Open the source and find `publishContent(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `deletePageContent()` — understanding this method

**Purpose:** Part of the `TbPageContentService` service's responsibility: connect content to pages and regions, and control publication.

**How to study it:** Open the source and find `deletePageContent(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `publishPageRegion()` — understanding this method

**Purpose:** Part of the `TbPageContentService` service's responsibility: connect content to pages and regions, and control publication.

**How to study it:** Open the source and find `publishPageRegion(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `fetchPublished()` — understanding this method

**Purpose:** Part of the `TbPageContentService` service's responsibility: connect content to pages and regions, and control publication.

**How to study it:** Open the source and find `fetchPublished(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

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

## Common mistakes

1. Calling an instance method statically, or creating an object when only a static method is needed.
2. Guessing method arguments or return values instead of inspecting the implementation.
3. Running data-changing operations without permissions, validation, and error handling.
4. Assuming a service method is safe to expose as an unauthenticated endpoint.
5. Copying an example without adapting it to your module's model and route configuration.

**Source-specific caution:** Some methods require a model, configured database connection or application context. The source method names alone do not establish standalone usage.

## Summary

Connect content to pages and regions, and control publication. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPageContentService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbPackageService](TbPackageService.md)
- [Next: TbPageSerice](TbPageSerice.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
