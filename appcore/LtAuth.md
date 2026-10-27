# LtAuth — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/LtAuth.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtAuth.php)

## Overview

Authenticate users and manage login state.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\LtAuth;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

The following illustrates a common use. Run it within a correctly configured LifeTech OCMS application.

```php
<?php
use Lt\Modules\MdLt\Services\LtAuth;

// In a controller where authentication has already been configured:
$auth = new LtAuth();
$isLoggedIn = $auth->check();
```

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `__construct()` | Confirm in source | `None` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `hidInitiate()` | Confirm in source | `None` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `activateUser($lifetech_general_id)` | Confirm in source | `$lifetech_general_id` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `login($username, $password = '')` | Confirm in source | `$username, $password = ''` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `loginWithAudit($username, $password = '', $loginFrom = '')` | Confirm in source | `$username, $password = '', $loginFrom = ''` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `loginWithEmail($email, $password = '')` | Confirm in source | `$email, $password = ''` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `loginWithUsername($username, $password = '')` | Confirm in source | `$username, $password = ''` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `handleLoginAttempt($input, $password, $getter)` | Confirm in source | `$input, $password, $getter` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `getUserByUsernameOrEmail($username)` | Confirm in source | `$username` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `getUserByEmail($email)` | Confirm in source | `$email` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `getUserByUsername($username)` | Confirm in source | `$username` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `getFormRole($formName)` | Confirm in source | `$formName` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `loginAnalysis()` | Confirm in source | `None` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `user()` | Confirm in source | `None` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `check()` | Confirm in source | `None` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `logout()` | Confirm in source | `None` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `setLtSession($user, $id)` | Confirm in source | `$user, $id` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `updateLastAccess($id, $key = '')` | Confirm in source | `$id, $key = ''` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |
| `loginWithId($id, $password)` | Confirm in source | `$id, $password` | Authenticate users and manage login state. Exact method behavior, visibility and return type require checking the linked implementation. |

### `__construct()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `__construct(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `hidInitiate()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `hidInitiate(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `activateUser()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `activateUser(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `login()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `login(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `loginWithAudit()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `loginWithAudit(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `loginWithEmail()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `loginWithEmail(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `loginWithUsername()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `loginWithUsername(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `handleLoginAttempt()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `handleLoginAttempt(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `getUserByUsernameOrEmail()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `getUserByUsernameOrEmail(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `getUserByEmail()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `getUserByEmail(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `getUserByUsername()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `getUserByUsername(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `getFormRole()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `getFormRole(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `loginAnalysis()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `loginAnalysis(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `user()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `user(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `check()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `check(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `logout()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `logout(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `setLtSession()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `setLtSession(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `updateLastAccess()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `updateLastAccess(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `loginWithId()` — understanding this method

**Purpose:** Part of the `LtAuth` service's responsibility: authenticate users and manage login state.

**How to study it:** Open the source and find `loginWithId(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

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

## Common mistakes

1. Calling an instance method statically, or creating an object when only a static method is needed.
2. Guessing method arguments or return values instead of inspecting the implementation.
3. Running data-changing operations without permissions, validation, and error handling.
4. Assuming a service method is safe to expose as an unauthenticated endpoint.
5. Copying an example without adapting it to your module's model and route configuration.

**Source-specific caution:** Treat credentials and tokens as secrets. Avoid logging them or returning them in public API responses.

## Summary

Authenticate users and manage login state. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtAuth.php)
- [Back to MdLt Services index](README.md)
- [Previous: CaseConverter](CaseConverter.md)
- [Next: LtComponentMgt](LtComponentMgt.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
