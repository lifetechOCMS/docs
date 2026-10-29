# LtValidator — Developer Guide

**Navigation:** [Previous: LtLWToken](LtLWToken.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtModel](LtModel.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtValidator.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtValidator.php)

## Overview

Validate submitted data and report field errors.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtValidator;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$result = LtValidator::validate(['name' => 'Ada'], ['name' => 'required|min:2']);
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `validate(array $data, array $rules)` | Static | `$data, $rules` | Validate input against a set of rules. |
| `errors()` | Static | `None` | Read collected validation errors; declared return `array`. |
| `passed()` | Static | `None` | Check whether validation has recorded any errors; declared return `bool`. |

## Public methods with examples

### `validate()` — validate input against a set of rules

**Call style:** Static. **Parameters:** `array $data, array $rules`.

```php
$result = LtValidator::validate(['name' => 'Ada'], ['name' => 'required|min:2']);
```

**Important:** This implementation echoes a JSON response and exits when validation fails.

### `errors()` — read collected validation errors

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtValidator::errors();
```

### `passed()` — check whether validation has recorded any errors

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtValidator::passed();
```

## Practical LifeTech module example: validate a contact form before saving

**Scenario:** A developer is building an `MdExample` module and wants to use `LtValidator` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\LtValidator;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Note: the current validator echoes JSON and exits on failure.
        $data = ['email' => 'visitor@example.com', 'name' => 'Ada'];
        LtValidator::validate($data, [
            'email' => 'required|email',
            'name' => 'required|min:2'
        ]);
        return LtResponse::json('Contact data valid', '2000', '200');
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Validate submitted data and report field errors. See the method reference and practical module scenario for usage.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtValidator.php)

---

**Navigation:** [Previous: LtLWToken](LtLWToken.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtModel](LtModel.md)
