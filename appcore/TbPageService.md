# TbPageService — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/TbPageService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPageService.php)

## Overview

Create and manage pages, publishing, routes and page regions.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\TbPageService;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

This service depends on application-specific models or setup. Start by locating a controller that already uses it, and inspect the arguments supplied there. A made-up call could mislead beginners or change application data.

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `__construct()` | Confirm in source | `None` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |
| `store($model)` | Confirm in source | `$model` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |
| `publishedContent($model)` | Confirm in source | `$model` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |
| `publishedRegion($model)` | Confirm in source | `$model` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |
| `publishedRoute($model)` | Confirm in source | `$model` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |
| `toggleRoute($model)` | Confirm in source | `$model` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |
| `fetchPublishPages()` | Confirm in source | `None` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |
| `deletePages($ltId = null, $params = null)` | Confirm in source | `$ltId = null, $params = null` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |
| `publishedToRegion()` | Confirm in source | `None` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |
| `togglePublished($packageName, $isPublished)` | Confirm in source | `$packageName, $isPublished` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |
| `dashboardAnalysis()` | Confirm in source | `None` | Create and manage pages, publishing, routes and page regions. Exact method behavior, visibility and return type require checking the linked implementation. |

### `__construct()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `__construct(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `store()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `store(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `publishedContent()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `publishedContent(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `publishedRegion()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `publishedRegion(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `publishedRoute()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `publishedRoute(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `toggleRoute()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `toggleRoute(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `fetchPublishPages()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `fetchPublishPages(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `deletePages()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `deletePages(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `publishedToRegion()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `publishedToRegion(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `togglePublished()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `togglePublished(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `dashboardAnalysis()` — understanding this method

**Purpose:** Part of the `TbPageService` service's responsibility: create and manage pages, publishing, routes and page regions.

**How to study it:** Open the source and find `dashboardAnalysis(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

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

## Common mistakes

1. Calling an instance method statically, or creating an object when only a static method is needed.
2. Guessing method arguments or return values instead of inspecting the implementation.
3. Running data-changing operations without permissions, validation, and error handling.
4. Assuming a service method is safe to expose as an unauthenticated endpoint.
5. Copying an example without adapting it to your module's model and route configuration.

**Source-specific caution:** Some methods require a model, configured database connection or application context. The source method names alone do not establish standalone usage.

## Summary

Create and manage pages, publishing, routes and page regions. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbPageService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbPageSerice](TbPageSerice.md)
- [Next: TbResponseService](TbResponseService.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
