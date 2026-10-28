# TbLoginAuditService — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbLoginAuditService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbLoginAuditService.php)

## Overview

Record login attempts and related audit information.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbLoginAuditService;
```

## Quick start

This service primarily changes application state or needs configured framework models. The examples below show the calling pattern, with potentially destructive calls commented out.

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `logAudit($loginDetails)` | Instance | `$loginDetails` | Log audit in the service. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbLoginAuditService();
```

### `logAudit()` — log audit in the service

**Call style:** Instance. **Parameters:** `$loginDetails`.

```php
// $model must be a populated, validated framework model.
// $service = new TbLoginAuditService();
// $result = $service->logAudit($model);
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

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

## Summary

Record login attempts and related audit information. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbLoginAuditService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbContentService](TbContentService.md)
- [Next: TbMenuService](TbMenuService.md)
