# LtRequest — Developer Guide

**Navigation:** [Previous: LtSession](LtSession.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtResponse](LtResponse.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtRequest.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtRequest.php)

## Overview

Read incoming HTTP request data and validate it.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtRequest;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new LtRequest();
$result = $service->validateRequest();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `validateRequest(array $rules = [])` | Instance | `$rules` | Validate fields loaded by the HTTP request. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new LtRequest();
```

### `validateRequest()` — validate fields loaded by the HTTP request

**Call style:** Instance. **Parameters:** `array $rules = []`.

```php
$service = new LtRequest();
$result = $service->validateRequest();
```

**Important:** This delegates to `LtValidator::validate()`, which can exit on validation failure.

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

## Summary

Read incoming HTTP request data and validate it. See the method reference and practical module scenario for usage.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtRequest.php)

---

**Navigation:** [Previous: LtSession](LtSession.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtResponse](LtResponse.md)
