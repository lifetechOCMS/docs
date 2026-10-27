# LtComponentMgt — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/LtComponentMgt.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtComponentMgt.php)

## Overview

Manage publication of theme components.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\LtComponentMgt;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

The following illustrates a common use. Run it within a correctly configured LifeTech OCMS application.

```php
<?php
use Lt\Modules\MdLt\Services\LtComponentMgt;

// Review role permissions and required database setup before calling publish().
```

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `publish($names = '')` | Confirm in source | `$names = ''` | Manage publication of theme components. Exact method behavior, visibility and return type require checking the linked implementation. |

### `publish()` — understanding this method

**Purpose:** Part of the `LtComponentMgt` service's responsibility: manage publication of theme components.

**How to study it:** Open the source and find `publish(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

## Practical LifeTech module example: check whether a named component may be published

**Scenario:** A developer is building an `MdExample` module and wants to use `LtComponentMgt` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\LtComponentMgt;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Requires the legacy component table and role context.
        $canPublish = LtComponentMgt::publish('DashboardWidget');
        return LtResponse::json('Component publication checked', '2000', '200', [
            'allowed' => $canPublish
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

Manage publication of theme components. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtComponentMgt.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtAuth](LtAuth.md)
- [Next: LtDate](LtDate.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
