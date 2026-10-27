# TbLoginAuditService — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/TbLoginAuditService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbLoginAuditService.php)

## Overview

Record login attempts and related audit information.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\TbLoginAuditService;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

This service depends on application-specific models or setup. Start by locating a controller that already uses it, and inspect the arguments supplied there. A made-up call could mislead beginners or change application data.

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `__construct()` | Confirm in source | `None` | Record login attempts and related audit information. Exact method behavior, visibility and return type require checking the linked implementation. |
| `logAudit($loginDetails)` | Confirm in source | `$loginDetails` | Record login attempts and related audit information. Exact method behavior, visibility and return type require checking the linked implementation. |

### `__construct()` — understanding this method

**Purpose:** Part of the `TbLoginAuditService` service's responsibility: record login attempts and related audit information.

**How to study it:** Open the source and find `__construct(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `logAudit()` — understanding this method

**Purpose:** Part of the `TbLoginAuditService` service's responsibility: record login attempts and related audit information.

**How to study it:** Open the source and find `logAudit(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

## Practical LifeTech module example: record a login attempt after authentication

**Scenario:** A developer is building an `MdExample` module and wants to use `TbLoginAuditService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbLoginAuditService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Example input; do not store passwords or tokens in audit records.
        $audit = new TbLoginAuditService();
        return $audit->logAudit([
            'username' => 'example.user',
            'status' => 'failed',
            'reason' => 'Invalid credentials',
            'loginFrom' => 'MdExample',
            'userId' => null
        ]);
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

Record login attempts and related audit information. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbLoginAuditService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbContentService](TbContentService.md)
- [Next: TbMenuService](TbMenuService.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
