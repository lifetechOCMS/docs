# LtLWToken — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtLWToken.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtLWToken.php)

## Overview

Issue, validate and revoke lightweight user tokens.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtLWToken;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$result = LtLWToken::isValid('TOKEN_FROM_REQUEST');
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `insertLwtToken($userId, $user_role = "", $expireTime = "1100")` | Static | `$userId, $user_role, $expireTime` | Issue and store a lightweight access token. |
| `isValid($token, $expireTime = "1100")` | Static | `$token, $expireTime` | Validate and extend an existing lightweight token. |
| `destroy($token)` | Static | `$token` | Destroy the current PHP session. |
| `destroyExpiredToken()` | Static | `None` | Remove expired token records. |

## Public methods with examples

### `insertLwtToken()` — issue and store a lightweight access token

**Call style:** Static. **Parameters:** `$userId, $user_role = "", $expireTime = "1100"`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtLWToken::insertLwtToken('EXISTING_ID');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `isValid()` — validate and extend an existing lightweight token

**Call style:** Static. **Parameters:** `$token, $expireTime = "1100"`.

```php
$result = LtLWToken::isValid('TOKEN_FROM_REQUEST');
```

### `destroy()` — destroy the current PHP session

**Call style:** Static. **Parameters:** `$token`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtLWToken::destroy('TOKEN_FROM_REQUEST');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `destroyExpiredToken()` — remove expired token records

**Call style:** Static. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtLWToken::destroyExpiredToken();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

## Practical LifeTech module example: validate a token provided to a protected endpoint

**Scenario:** A developer is building an `MdExample` module and wants to use `LtLWToken` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\LtLWToken;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // The controller must first obtain a token from a trusted request.
        $token = (string) ($_SERVER['HTTP_X_API_TOKEN'] ?? '');
        return LtLWToken::isValid($token); // Returns a LifeTech JSON response string.
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Issue, validate and revoke lightweight user tokens. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtLWToken.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtFile](LtFile.md)
- [Next: LtMail](LtMail.md)
