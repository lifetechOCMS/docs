# LtRequest — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/LtRequest.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtRequest.php)

## Overview

Read incoming HTTP request data and validate it.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\LtRequest;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

The following illustrates a common use. Run it within a correctly configured LifeTech OCMS application.

```php
<?php
use Lt\Modules\MdLt\Services\LtRequest;

$request = new LtRequest();
$method = $request->method;
```

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `__construct()` | Confirm in source | `None` | Read incoming HTTP request data and validate it. Exact method behavior, visibility and return type require checking the linked implementation. |
| `loadData(array $source)` | Confirm in source | `array $source` | Read incoming HTTP request data and validate it. Exact method behavior, visibility and return type require checking the linked implementation. |
| `loadRawInput()` | Confirm in source | `None` | Read incoming HTTP request data and validate it. Exact method behavior, visibility and return type require checking the linked implementation. |
| `validateRequest(array $rules = [])` | Confirm in source | `array $rules = []` | Read incoming HTTP request data and validate it. Exact method behavior, visibility and return type require checking the linked implementation. |

### `__construct()` — understanding this method

**Purpose:** Part of the `LtRequest` service's responsibility: read incoming HTTP request data and validate it.

**How to study it:** Open the source and find `__construct(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `loadData()` — understanding this method

**Purpose:** Part of the `LtRequest` service's responsibility: read incoming HTTP request data and validate it.

**How to study it:** Open the source and find `loadData(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `loadRawInput()` — understanding this method

**Purpose:** Part of the `LtRequest` service's responsibility: read incoming HTTP request data and validate it.

**How to study it:** Open the source and find `loadRawInput(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `validateRequest()` — understanding this method

**Purpose:** Part of the `LtRequest` service's responsibility: read incoming HTTP request data and validate it.

**How to study it:** Open the source and find `validateRequest(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

## Practical LifeTech module example: read a submitted blog search query

**Scenario:** A developer is building an `MdExample` module and wants to use `LtRequest` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\LtRequest;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        $request = new LtRequest();
        $query = trim((string) ($request->query ?? ''));
        return LtResponse::json('Search request received', '2000', '200', [
            'query' => $query,
            'method' => $request->method
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

Read incoming HTTP request data and validate it. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtRequest.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtNavigate](LtNavigate.md)
- [Next: LtResponse](LtResponse.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
