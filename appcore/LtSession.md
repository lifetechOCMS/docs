# LtSession — Developer Guide

**Navigation:** [Previous: LtSiteInfo](LtSiteInfo.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtRequest](LtRequest.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtSession.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtSession.php)

## Overview

A **session** lets a PHP application remember information between HTTP requests from the same visitor. For example, a module might remember a temporary preference or read an authenticated user's ID that the LifeTech OCMS login system has already placed in the session.

`LtSession` is a small wrapper around PHP's `$_SESSION` and session functions. It does **not** perform authentication or authorization by itself.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtSession;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$service = new LtSession();
$result = $service->start();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `start()` | Instance | `None` | Start or resume the current PHP session. |
| `end()` | Instance | `None` | End the PHP session and expire its cookie (see implementation caveat). |
| `set($key, $value)` | Static | `$key, $value` | Store a value under a session key. |
| `has($key)` | Static | `$key` | Check whether a session key exists. |
| `get($key)` | Static | `$key` | Retrieve a stored value. |
| `forget($key)` | Static | `$key` | Remove one session value. |
| `destroy()` | Static | `None` | Destroy the current PHP session. |
| `all()` | Static | `None` | Read all current session values. |

## Public methods with examples

### `start()` — start or resume the current PHP session

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new LtSession();
$result = $service->start();
```

### `end()` — end the PHP session and expire its cookie (see implementation caveat)

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new LtSession();
$result = $service->end();
```

### `set()` — store a value under a session key

**Call style:** Static. **Parameters:** `$key, $value`.

```php
$result = LtSession::set('dashboardTheme', 'yes');
```

### `has()` — check whether a session key exists

**Call style:** Static. **Parameters:** `$key`.

```php
$result = LtSession::has('dashboardTheme');
```

### `get()` — retrieve a stored value

**Call style:** Static. **Parameters:** `$key`.

```php
$result = LtSession::get('dashboardTheme');
```

### `forget()` — remove one session value

**Call style:** Static. **Parameters:** `$key`.

```php
$result = LtSession::forget('dashboardTheme');
```

### `destroy()` — destroy the current PHP session

**Call style:** Static. **Parameters:** `none`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtSession::destroy();
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `all()` — read all current session values

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSession::all();
```

## Practical LifeTech module example: a temporary dashboard preference

This is an illustrative controller method; adapt its class name and route to your module's existing structure:

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\Modules\MdLt\Services\LtSession;
use Lt\Modules\MdLt\Services\LtResponse;

class TbDashboardController
{
    public function showPreference()
    {
        $theme = LtSession::has('dashboardTheme')
            ? LtSession::get('dashboardTheme')
            : 'light';

        return LtResponse::json(
            'Dashboard preference loaded',
            '2000',
            '200',
            ['theme' => $theme]
        );
    }
}
```

This example **reads a preference**, not a login credential. The exact controller invocation and HTTP response handling depend on the module's route setup.

## Summary

For ordinary module development, the most useful calls are `LtSession::set()`, `LtSession::get()`, `LtSession::has()`, and `LtSession::forget()`. Use `all()` sparingly. Leave session initialization and logout to LifeTech OCMS's established lifecycle unless you are working on the framework itself.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtSession.php)

---

**Navigation:** [Previous: LtSiteInfo](LtSiteInfo.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtRequest](LtRequest.md)
