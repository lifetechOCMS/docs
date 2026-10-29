# LtAuth — Developer Guide

**Navigation:** [Previous: LtNavigate](LtNavigate.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtLWToken](LtLWToken.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtAuth.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtAuth.php)

## Overview

Authenticate users and manage login state.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtAuth;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$result = LtAuth::hidInitiate();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__construct()` | Instance | `None` |   construct in the service. |
| `hidInitiate()` | Static | `None` | Hid initiate in the service. |
| `activateUser($lifetech_general_id)` | Static | `$lifetech_general_id` | Activate user in the service. |
| `login($username, $password = "")` | Static | `$username, $password` | Attempt to authenticate a user. |
| `loginWithAudit($username, $password = "null", $loginFrom="null")` | Static | `$username, $password, $loginFrom` | Login with audit in the service. |
| `loginWithEmail($email, $password = "")` | Static | `$email, $password` | Login with email in the service. |
| `loginWithUsername($username, $password = "")` | Static | `$username, $password` | Login with username in the service. |
| `getFormRole($formName)` | Static | `$formName` | Read form role from the configured service. |
| `loginAnalysis()` | Instance | `None` | Login analysis in the service. |
| `user()` | Static | `None` | Retrieve current user information. |
| `check()` | Static | `None` | Check the current authentication state. |
| `logout()` | Static | `None` | Log out the current user. |
| `updateLastAccess($id, $key="")` | Static | `$id, $key` | Update last access in the service. |
| `loginWithId($id, $password)` | Static | `$id, $password` | Login with id in the service. |
| `internalActivateUser($user)` | Static | `$user` | Internal activate user in the service. |
| `getActiveUserRole($user)` | Static | `$user` | Read active user role from the configured service. |

## Public methods with examples

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new LtAuth();
```

### `hidInitiate()` — hid initiate in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtAuth::hidInitiate();
```

### `activateUser()` — activate user in the service

**Call style:** Static. **Parameters:** `$lifetech_general_id`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtAuth::activateUser('EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `login()` — attempt to authenticate a user

**Call style:** Static. **Parameters:** `$username, $password = ""`.

```php
$result = LtAuth::login('demo@example.com');
```

### `loginWithAudit()` — login with audit in the service

**Call style:** Static. **Parameters:** `$username, $password = "null", $loginFrom="null"`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtAuth::loginWithAudit('demo@example.com');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `loginWithEmail()` — login with email in the service

**Call style:** Static. **Parameters:** `$email, $password = ""`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtAuth::loginWithEmail('demo@example.com');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `loginWithUsername()` — login with username in the service

**Call style:** Static. **Parameters:** `$username, $password = ""`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtAuth::loginWithUsername('demo@example.com');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `getFormRole()` — read form role from the configured service

**Call style:** Static. **Parameters:** `$formName`.

```php
$result = LtAuth::getFormRole('EXAMPLE_VALUE');
```

### `loginAnalysis()` — login analysis in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new LtAuth();
$result = $service->loginAnalysis();
```

### `user()` — retrieve current user information

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtAuth::user();
```

### `check()` — check the current authentication state

**Call style:** Static. **Parameters:** `none`.

```php
$isAuthenticated = LtAuth::check();
```

### `logout()` — log out the current user

**Call style:** Static. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtAuth::logout();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `updateLastAccess()` — update last access in the service

**Call style:** Static. **Parameters:** `$id, $key=""`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtAuth::updateLastAccess('EXISTING_ID');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `loginWithId()` — login with id in the service

**Call style:** Static. **Parameters:** `$id, $password`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtAuth::loginWithId('EXISTING_ID', 'password-from-secure-login-form');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `internalActivateUser()` — internal activate user in the service

**Call style:** Static. **Parameters:** `$user`.

```php
$result = LtAuth::internalActivateUser('EXAMPLE_VALUE');
```

### `getActiveUserRole()` — read active user role from the configured service

**Call style:** Static. **Parameters:** `$user`.

```php
$result = LtAuth::getActiveUserRole('EXAMPLE_VALUE');
```

## Practical LifeTech module example: check whether a visitor is authenticated

**Scenario:** A developer is building an `MdExample` module and wants to use `LtAuth` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\LtAuth;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Uses the authentication state managed by LifeTech OCMS.
        $isAuthenticated = LtAuth::check();
        return LtResponse::json('Authentication checked', '2000', '200', [
            'authenticated' => (bool) $isAuthenticated
        ]);
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Authenticate users and manage login state. See the method reference and practical module scenario for usage.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtAuth.php)

---

**Navigation:** [Previous: LtNavigate](LtNavigate.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtLWToken](LtLWToken.md)
