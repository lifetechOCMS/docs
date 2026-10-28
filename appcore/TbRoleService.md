# TbRoleService — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/TbRoleService.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbRoleService.php)

## Overview

Work with user roles and permission checks.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\TbRoleService;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new TbRoleService();
$result = $service->roleUserPermissionStatus();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `rolePermission()` | Instance | `None` | Role permission in the service. |
| `roleUserPermissionStatus($roles=[])` | Instance | `$roles` | Role user permission status in the service. |
| `dashboardAnalysis()` | Instance | `None` | Return dashboard-related summary data. |
| `roleExist(String $role)` | Instance | `$role` | Check whether a role exists. |
| `getRoleNameById($role)` | Instance | `$role` | Find the name associated with a role identifier. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new TbRoleService();
```

### `rolePermission()` — role permission in the service

**Call style:** Instance. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $service = new TbRoleService();
// $result = $service->rolePermission();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `roleUserPermissionStatus()` — role user permission status in the service

**Call style:** Instance. **Parameters:** `$roles=[]`.

```php
$service = new TbRoleService();
$result = $service->roleUserPermissionStatus();
```

### `dashboardAnalysis()` — return dashboard-related summary data

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new TbRoleService();
$result = $service->dashboardAnalysis();
```

### `roleExist()` — check whether a role exists

**Call style:** Instance. **Parameters:** `String $role`.

```php
$service = new TbRoleService();
$result = $service->roleExist('EXAMPLE_VALUE');
```

### `getRoleNameById()` — find the name associated with a role identifier

**Call style:** Instance. **Parameters:** `$role`.

```php
$service = new TbRoleService();
$result = $service->getRoleNameById('EXAMPLE_VALUE');
```

## Practical LifeTech module example: look up a role name for a dashboard

**Scenario:** A developer is building an `MdExample` module and wants to use `TbRoleService` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\TbRoleService;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Replace with an existing role ID in your installation.
        $roleId = 'EXISTING_ROLE_ID';
        $service = new TbRoleService();
        $roleName = $service->getRoleNameById($roleId);
        return LtResponse::json('Role lookup completed', '2000', '200', [
            'roleName' => $roleName
        ]);
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Work with user roles and permission checks. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbRoleService.php)
- [Back to MdLt Services index](README.md)
- [Previous: TbResponseService](TbResponseService.md)
- [Next: TbThemeService](TbThemeService.md)
