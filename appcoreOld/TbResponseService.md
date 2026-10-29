# TbResponseService — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbResponseService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbResponseService.php)

## Overview

Store response records through the response model.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbResponseService;
```

## Quick start

This service primarily changes application state or needs configured framework models. The examples below show the calling pattern, with potentially destructive calls commented out.

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `storeResponse($model)` | Instance | `$model` | Store response in the service. |
| `storeResponse($model)` | Instance | `$model` | Store response in the service. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbResponseService();
```

### `storeResponse()` — store response in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbResponseService();
// $result = $service->storeResponse($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `storeResponse()` — store response in the service

**Call style:** Instance. **Parameters:** `$model`.

```php
// $model must be a populated, validated framework model.
// $service = new TbResponseService();
// $result = $service->storeResponse($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

## Practical LifeTech module example: prepare to store a response record

**Scenario:** A developer is building an `MdExample` module and wants to use `TbResponseService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbResponseService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Requires a valid TbResponse model and its database fields.
        // $response = new \Lt\Modules\MdLt\Models\TbResponse();
        // Populate and validate model properties before calling:
        // $service = new TbResponseService();
        // return $service->storeResponse($response);
        return LtResponse::json('Response model setup required', '2000', '200');
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Store response records through the response model. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbResponseService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbPageService](TbPageService.md)
- [Next: TbRoleService](TbRoleService.md)
