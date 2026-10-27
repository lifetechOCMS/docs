# TbContentService — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/TbContentService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbContentService.php)

## Overview

Manage content resources, publishing, file synchronization and layout assignments.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\TbContentService;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

This service depends on application-specific models or setup. Start by locating a controller that already uses it, and inspect the arguments supplied there. A made-up call could mislead beginners or change application data.

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `store($model, $isService)` | Confirm in source | `$model, $isService` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `autoCreate()` | Confirm in source | `None` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `autoCreateTemplate($packageName, $contentName, $type, $isService, $content)` | Confirm in source | `$packageName, $contentName, $type, $isService, $content` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `publishedPage($model)` | Confirm in source | `$model` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `fetchPublishContent($ltId = null)` | Confirm in source | `$ltId = null` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `deleteContent($ltId = null, $packageName = null)` | Confirm in source | `$ltId = null, $packageName = null` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `togglePublishedContent($packageName, $isPublished)` | Confirm in source | `$packageName, $isPublished` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `download($model)` | Confirm in source | `$model` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `upload($model)` | Confirm in source | `$model` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `dashboardAnalysis()` | Confirm in source | `None` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `parsePathDetails($path)` | Confirm in source | `$path` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `synchronizeContent()` | Confirm in source | `None` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `processPendingLayouts($packageName, $packageType)` | Confirm in source | `$packageName, $packageType` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `scanContent()` | Confirm in source | `None` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `getFolders()` | Confirm in source | `None` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `fetchLayouts()` | Confirm in source | `None` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `assignLayouts($data)` | Confirm in source | `$data` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |
| `contentRegions()` | Confirm in source | `None` | Manage content resources, publishing, file synchronization and layout assignments. Exact method behavior, visibility and return type require checking the linked implementation. |

### `store()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `store(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `autoCreate()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `autoCreate(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `autoCreateTemplate()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `autoCreateTemplate(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `publishedPage()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `publishedPage(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `fetchPublishContent()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `fetchPublishContent(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `deleteContent()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `deleteContent(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `togglePublishedContent()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `togglePublishedContent(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `download()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `download(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `upload()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `upload(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `dashboardAnalysis()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `dashboardAnalysis(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `parsePathDetails()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `parsePathDetails(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `synchronizeContent()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `synchronizeContent(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `processPendingLayouts()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `processPendingLayouts(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `scanContent()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `scanContent(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `getFolders()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `getFolders(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `fetchLayouts()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `fetchLayouts(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `assignLayouts()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `assignLayouts(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `contentRegions()` — understanding this method

**Purpose:** Part of the `TbContentService` service's responsibility: manage content resources, publishing, file synchronization and layout assignments.

**How to study it:** Open the source and find `contentRegions(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

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

## Common mistakes

1. Calling an instance method statically, or creating an object when only a static method is needed.
2. Guessing method arguments or return values instead of inspecting the implementation.
3. Running data-changing operations without permissions, validation, and error handling.
4. Assuming a service method is safe to expose as an unauthenticated endpoint.
5. Copying an example without adapting it to your module's model and route configuration.

**Source-specific caution:** Some methods require a model, configured database connection or application context. The source method names alone do not establish standalone usage.

## Summary

Manage content resources, publishing, file synchronization and layout assignments. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbContentService.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtValidator](LtValidator.md)
- [Next: TbLoginAuditService](TbLoginAuditService.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
