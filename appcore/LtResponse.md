# LtResponse — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtResponse.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtResponse.php)

## Overview

Return consistent API responses and log errors.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtResponse;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$result = LtResponse::json('Loaded', '2000', '200', ['count' => 2]);
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `json($responseResult = "Unknown", $responseCode = "101", $responseCategory = "100", $responseData = [], $responseStatus = "fail", $responseOperationType = "others")` | Static | `$responseResult, $responseCode, $responseCategory, $responseData, $responseStatus, $responseOperationType` | Encode a standard LifeTech API response as JSON. |
| `error($responseResult = "Unknown Error",$responseCode = "1043", $responseCategory = "100",$responseData = [], $responseStatus = "fail", $responseOperationType = "others")` | Static | `$responseResult, $responseCode, $responseCategory, $responseData, $responseStatus, $responseOperationType` | Encode an error response, with production masking. |
| `writeLog($message, $context = [])` | Static | `$message, $context` | Write an entry to the application error log. |

## Public methods with examples

### `json()` — encode a standard LifeTech API response as JSON

**Call style:** Static. **Parameters:** `$responseResult = "Unknown", $responseCode = "101", $responseCategory = "100", $responseData = [], $responseStatus = "fail", $responseOperationType = "others"`.

```php
$result = LtResponse::json('Loaded', '2000', '200', ['count' => 2]);
```

### `error()` — encode an error response, with production masking

**Call style:** Static. **Parameters:** `$responseResult = "Unknown Error",$responseCode = "1043", $responseCategory = "100",$responseData = [], $responseStatus = "fail", $responseOperationType = "others"`.

```php
$result = LtResponse::error('Unable to load', '1001', '100');
```

### `writeLog()` — write an entry to the application error log

**Call style:** Static. **Parameters:** `$message, $context = []`.

```php
// This operation can change application state; review permissions and inputs.
// $result = LtResponse::writeLog('EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

## Practical LifeTech module example: return a consistent response from a blog controller

**Scenario:** A developer is building an `MdExample` module and wants to use `LtResponse` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\LtResponse;

class TbExampleController
{
    public function index()
    {
        $posts = [
            ['title' => 'Getting started with LifeTech OCMS'],
            ['title' => 'Building a theme']
        ];
        return LtResponse::json('Posts loaded', '2000', '200', $posts);
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Return consistent API responses and log errors. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtResponse.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtRequest](LtRequest.md)
- [Next: LtRoute](LtRoute.md)
