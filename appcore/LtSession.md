# LtSession — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/LtSession.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtSession.php)

## Overview

A **session** lets a PHP application remember information between HTTP requests from the same visitor. For example, a module might remember a temporary preference or read an authenticated user's ID that the LifeTech OCMS login system has already placed in the session.

`LtSession` is a small wrapper around PHP's `$_SESSION` and session functions. It does **not** perform authentication or authorization by itself. Never assume that setting a user ID manually means a user has securely logged in.

## Import the class

Inside your module's controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\LtSession;
```

Most frequently used methods are **static**: call `LtSession::get(...)`, not `(new LtSession())->get(...)`.

## Quick start: store, read, and remove a preference

```php
<?php

use Lt\Modules\MdLt\Services\LtSession;

// Assumes LifeTech has already started the PHP session.
LtSession::set('preferredLanguage', 'en');

if (LtSession::has('preferredLanguage')) {
    $language = LtSession::get('preferredLanguage');
    echo 'Selected language: ' . htmlspecialchars((string) $language, ENT_QUOTES, 'UTF-8');
}

LtSession::forget('preferredLanguage');
```

Expected output before removal:

```text
Selected language: en
```

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `start()` | Instance | None | Calls `session_start()` and returns `true` on success, otherwise `false`. |
| `set($key, $value)` | Static | Session key and value | Assigns `$_SESSION[$key] = $value`; returns the assigned value. |
| `get($key)` | Static | Session key | Returns the stored value, or `false` if the key is not set. |
| `has($key)` | Static | Session key | Uses `isset()`; returns `true` or `false`. Keys storing `null` are treated as absent. |
| `forget($key)` | Static | Session key | Returns `false` if absent; otherwise unsets the key and implicitly returns `null`. |
| `all()` | Static | None | Returns the entire `$_SESSION` array. |
| `destroy()` | Static | None | Calls `session_destroy()`; the method does not return PHP's result. |
| `end()` | Instance | None | Attempts to start if needed, then destroys/unsets the session and expires its cookie. **See implementation warning below.** |

### `set()` — save a value

```php
LtSession::set('dashboardTheme', 'dark');
LtSession::set('itemsPerPage', 20);
```

Use meaningful, consistent key names to avoid collisions with LifeTech's own session keys.

### `get()` — retrieve a value

```php
$theme = LtSession::get('dashboardTheme');

if ($theme === false) {
    $theme = 'light';
}
```

**Important:** This fallback also treats a deliberately stored `false` as missing. Use `has()` if distinguishing those cases matters.

### `has()` — check before reading

```php
if (LtSession::has('itemsPerPage')) {
    $itemsPerPage = LtSession::get('itemsPerPage');
} else {
    $itemsPerPage = 10;
}
```

### `forget()` — remove one key

```php
LtSession::forget('dashboardTheme');
```

This does not log the user out and does not remove other session values.

### `all()` — inspect available values

```php
$keys = array_keys(LtSession::all());
```

Inspecting **keys** is generally safer than exposing all values. Never return all session data to an untrusted client.

### `start()` — begin or resume a session

```php
$session = new LtSession();
$started = $session->start();
```

This is the actual instance method in the source, but **do not call it routinely inside module controllers** when the framework has already started the session. Starting twice can produce warnings or unexpected behavior. Session initialization should occur before output is sent.

### `destroy()` — destroy server-side session data

```php
LtSession::destroy();
```

**Do not treat this alone as a complete logout implementation.** The method does not clear the in-memory `$_SESSION` array or delete the browser cookie. Use the framework's established logout/authentication flow instead.

### `end()` — implementation caution

The current source refers to `$this->status` without declaring that property:

```php
if ($this->status != true) {
    $this->start();
}
```

This may generate a warning and makes the method unsuitable as a recommended logout example until the implementation is corrected. Prefer the application's established logout flow.

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

## Common mistakes

1. **Creating an instance for every operation:** `LtSession::get('key')` is sufficient; `get()` is static.
2. **Starting the session repeatedly:** use the existing LifeTech request/session initialization.
3. **Assuming `get()` returns `null` when absent:** this implementation returns `false`.
4. **Treating `has()` as authentication:** the presence of a key does not establish that the user is authorized.
5. **Using `destroy()` as a complete logout:** rely on the framework's authentication/logout workflow.
6. **Displaying `all()` in production:** session data can contain private or security-sensitive information.

## Summary

For ordinary module development, the most useful calls are `LtSession::set()`, `LtSession::get()`, `LtSession::has()`, and `LtSession::forget()`. Use `all()` sparingly. Leave session initialization and logout to LifeTech OCMS's established lifecycle unless you are working on the framework itself.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtSession.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtService](LtService.md)
- [Next: LtSiteInfo](LtSiteInfo.md)

*This guide documents the `v1.x` implementation reviewed on 25 October 2026. Verify the source again after updating the branch.*
