# LtComponentMgt — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtComponentMgt.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtComponentMgt.php)

## Overview

Manage publication of theme components.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtComponentMgt;
```

## Quick start

This service primarily changes application state or needs configured framework models. The examples below show the calling pattern, with potentially destructive calls commented out.

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `publish($names="")` | Static | `$names` | Publish in the service. |

## Public methods with examples

### `publish()` — publish in the service

**Call style:** Static. **Parameters:** `$names=""`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtComponentMgt::publish();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

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

## Summary

Manage publication of theme components. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtComponentMgt.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtAuth](LtAuth.md)
- [Next: LtDate](LtDate.md)
