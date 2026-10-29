# LtResponse — Developer Guide

**Navigation:** [Previous: LtRequest](LtRequest.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: Response Codes and Response Groups](LtResponse_Codes_and_Response_Groups.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtResponse.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtResponse.php)

## Overview

`LtResponse` provides a consistent JSON response format for LifeTech OCMS modules and APIs. It also provides an environment-aware error method and a method for writing application error logs. **Every response code supplied by a developer must contain exactly four digits** and should belong to the appropriate response group. See [LtResponse Codes and Response Groups — Developer Guide](LtResponse_Codes_and_Response_Groups.md).

Both `LtResponse::json()` and `LtResponse::error()` use the **same response structure**. The important difference is how errors are handled in a production environment.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtResponse;
```

## Quick start

```php
return LtResponse::json(
    'Posts loaded successfully',
    '2000',
    '200',
    ['count' => 2]
);
```

The method returns a **JSON-encoded string**, not a PHP array or object. In an HTTP controller, your application's response handling must send that string with the appropriate JSON content type.

## Understanding the four response fields

A LifeTech OCMS JSON response can contain **four main fields**:

| Field | Purpose | Example |
|---|---|---|
| `responseResult` | Human-readable result or message explaining what happened. | `"Posts loaded successfully"` |
| `responseCode` | Application-defined code identifying the specific outcome. | `"2000"` |
| `responseCategory` | General success or failure category. | `"200"` |
| `responseData` | Optional data returned by the operation, such as a record or list. | `{"count": 2}` |

### 1. `responseResult` — message

This describes the outcome in words. For example, `"Post created successfully"` or `"Post not found"`.

### 2. `responseCode` — specific application code

This identifies a particular outcome within your module or framework. **A response code is compulsory and must be exactly four digits (`0`–`9`)**, such as `1901`, `3301`, or `3402`. Select a code from the appropriate response group and ensure it is not already assigned to a different outcome. See the [Response Codes and Response Groups guide](LtResponse_Codes_and_Response_Groups.md) for the reserved ranges and registered codes.

These are **application response codes**, not automatically HTTP status codes. Store/pass them as strings, for example `'3402'`, and do not confuse them with `responseCategory`. **Note:** The four-digit requirement is a LifeTech OCMS documentation/convention rule; the current method signature accepts a string and does not itself guarantee four-digit validation.

### 3. `responseCategory` — success or failure

LifeTech OCMS uses these two main categories:

| Value | Meaning | Typical use |
|---|---|---|
| `"200"` | Success | Data loaded, record created, operation completed |
| `"100"` | Failure | Validation failed, record not found, operation failed |

`responseCategory` is a LifeTech application field; it does **not** automatically set the HTTP status code.

### 4. `responseData` — optional returned data

Use this field when you want to return a record, a list, a count, or other useful information.

```php
return LtResponse::json(
    'Post loaded',
    '2000',
    '200',
    [
        'id' => 12,
        'title' => 'Welcome to LifeTech OCMS'
    ]
);
```

Expected JSON:

```json
{
  "responseResult": "Post loaded",
  "responseCode": "2000",
  "responseCategory": "200",
  "responseData": {
    "id": 12,
    "title": "Welcome to LifeTech OCMS"
  }
}
```

**Important:** In the current implementation, `responseData` is **omitted** when the supplied value is an empty array (`[]`) or `null`. It is not guaranteed to appear in every response.

For example:

```php
return LtResponse::json('Operation completed', '2000', '200');
```

Expected JSON:

```json
{
  "responseResult": "Operation completed",
  "responseCode": "2000",
  "responseCategory": "200"
}
```

## Method reference

| Public method | Call style | Purpose / return |
|---|---|---|
| `json($responseResult, $responseCode, $responseCategory, $responseData, $responseStatus, $responseOperationType)` | Static | Returns a JSON-encoded string using the LifeTech response format. All arguments have defaults. |
| `error($responseResult, $responseCode, $responseCategory, $responseData, $responseStatus, $responseOperationType)` | Static | Returns the same JSON format, but changes the exposed error message in production. All arguments have defaults. |
| `writeLog($message, $context = [])` | Static | Writes a timestamped entry to an error log file. |

The current method signatures include `$responseStatus` and `$responseOperationType`, but the JSON encoder shown in the source does **not** include those fields in its returned payload. Although the methods have default response codes, developers should explicitly supply a valid **four-digit code** from the correct group.

## Public methods with examples

### `json()` — return a standard response

Use `json()` for normal API responses, including success messages and failures that you deliberately want to return unchanged.

```php
return LtResponse::json(
    'Post created successfully',
    '2001',
    '200',
    ['postId' => 45]
);
```

Expected JSON:

```json
{
  "responseResult": "Post created successfully",
  "responseCode": "2001",
  "responseCategory": "200",
  "responseData": {
    "postId": 45
  }
}
```

`json()` does not check whether the application is in development or production. It encodes the message and other supplied fields directly.

### `error()` — return an environment-aware error

`error()` uses the same four-field response structure, but **checks the application environment** using the `LT_ENV` constant.

**In development:** The original error message, response code, category, and optional data are returned through `json()`. This helps developers diagnose problems.

```php
return LtResponse::error(
    'Unable to load post',
    '3401',
    '100'
);
```

Expected JSON when `LT_ENV` is `development` (or not defined):

```json
{
  "responseResult": "Unable to load post",
  "responseCode": "3401",
  "responseCategory": "100"
}
```

**In production:** The method logs the original error message, then returns a general site-facing error message instead of exposing internal details.

The current implementation returns:

```json
{
  "responseResult": "Something went wrong. Please try again later.",
  "responseCode": "1043",
  "responseCategory": "100"
}
```

The displayed message comes from the class property `LtResponse::$defaultProductionErrorMessage`. It can be customized in the application if needed.

| Behavior | `json()` | `error()` |
|---|---|---|
| Response format | Standard LifeTech JSON | Same standard LifeTech JSON |
| Development | Returns supplied values | Returns supplied error details |
| Production | Still returns supplied values | Logs original message and returns configured general message |
| Suitable for | Standard API outcomes | Errors whose internal details should be hidden from visitors |

**Recommendation:** Use `LtResponse::error()` for unexpected failures or exceptions, especially when an error could expose database, file-system, or other internal details. Use `LtResponse::json()` for expected application outcomes.

### `writeLog()` — write an application error log

Use this method when you need to record diagnostic information without returning it to the visitor.

```php
LtResponse::writeLog(
    'Blog post could not be loaded',
    ['postId' => 45]
);
```

The method creates a daily log file named like `Error-2026-10-28.log`. It uses `LT_LOG_PATH` when defined; otherwise it uses a `logs` directory relative to the service file.

Do not write passwords, access tokens, or other secrets to application logs.

## Practical LifeTech module example: handling blog responses

**Scenario:** A developer creates an `MdBlog` controller that returns a successful response when a post exists and an environment-aware error when an unexpected exception occurs.

```php
<?php

namespace Lt\Modules\MdBlog\Controllers;

use Lt\Modules\MdLt\Services\LtResponse;

class TbBlogController
{
    public function showPost()
    {
        try {
            // Example data; replace with your module's model query.
            $post = [
                'id' => 45,
                'title' => 'Getting Started with LifeTech OCMS'
            ];

            return LtResponse::json(
                'Post loaded successfully',
                '2000',
                '200',
                $post
            );
        } catch (\Throwable $e) {
            return LtResponse::error(
                $e->getMessage(),
                '3401',
                '100'
            );
        }
    }
}
```

In development, the developer receives the original exception message. In production, the original message is logged and the visitor receives the general error message instead.

This example demonstrates the response service; it does not implement the actual blog database query or HTTP route.

## Summary

`LtResponse::json()` and `LtResponse::error()` return the **same JSON structure**, with `responseResult`, `responseCode`, `responseCategory`, and optional `responseData`. The distinction is environment-aware error handling: `error()` protects internal details in production, while `json()` returns the values provided to it. Use `writeLog()` for additional diagnostic logging. Always supply a **four-digit response code** from the appropriate group; see the [Response Codes and Response Groups guide](LtResponse_Codes_and_Response_Groups.md).

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtResponse.php)

---

**Navigation:** [Previous: LtRequest](LtRequest.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: Response Codes and Response Groups](LtResponse_Codes_and_Response_Groups.md)
