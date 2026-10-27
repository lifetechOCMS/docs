# CaseConverter — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/CaseConverter.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/CaseConverter.php)

## Overview

Convert names between snake_case, camelCase and PascalCase.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\CaseConverter;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

The following illustrates a common use. Run it within a correctly configured LifeTech OCMS application.

```php
<?php
use Lt\Modules\MdLt\Services\CaseConverter;

CaseConverter::snakeToPascal('tb_card_profile');
```

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `snakeToCamel($string)` | Confirm in source | `$string` | Convert names between snake_case, camelCase and PascalCase. Exact method behavior, visibility and return type require checking the linked implementation. |
| `pascalToSnake($string)` | Confirm in source | `$string` | Convert names between snake_case, camelCase and PascalCase. Exact method behavior, visibility and return type require checking the linked implementation. |
| `camelToSnake($string)` | Confirm in source | `$string` | Convert names between snake_case, camelCase and PascalCase. Exact method behavior, visibility and return type require checking the linked implementation. |
| `snakeToPascal($string)` | Confirm in source | `$string` | Convert names between snake_case, camelCase and PascalCase. Exact method behavior, visibility and return type require checking the linked implementation. |
| `pascalToCamel($string)` | Confirm in source | `$string` | Convert names between snake_case, camelCase and PascalCase. Exact method behavior, visibility and return type require checking the linked implementation. |
| `camelToPascal($string)` | Confirm in source | `$string` | Convert names between snake_case, camelCase and PascalCase. Exact method behavior, visibility and return type require checking the linked implementation. |
| `toCamelCaseArray(array $data)` | Confirm in source | `array $data` | Convert names between snake_case, camelCase and PascalCase. Exact method behavior, visibility and return type require checking the linked implementation. |
| `arrayToCamelCaseArray(array $data)` | Confirm in source | `array $data` | Convert names between snake_case, camelCase and PascalCase. Exact method behavior, visibility and return type require checking the linked implementation. |
| `arrayToCamelCase(array $data)` | Confirm in source | `array $data` | Convert names between snake_case, camelCase and PascalCase. Exact method behavior, visibility and return type require checking the linked implementation. |

### `snakeToCamel()` — understanding this method

**Purpose:** Part of the `CaseConverter` service's responsibility: convert names between snake_case, camelCase and PascalCase.

**How to study it:** Open the source and find `snakeToCamel(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `pascalToSnake()` — understanding this method

**Purpose:** Part of the `CaseConverter` service's responsibility: convert names between snake_case, camelCase and PascalCase.

**How to study it:** Open the source and find `pascalToSnake(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `camelToSnake()` — understanding this method

**Purpose:** Part of the `CaseConverter` service's responsibility: convert names between snake_case, camelCase and PascalCase.

**How to study it:** Open the source and find `camelToSnake(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `snakeToPascal()` — understanding this method

**Purpose:** Part of the `CaseConverter` service's responsibility: convert names between snake_case, camelCase and PascalCase.

**How to study it:** Open the source and find `snakeToPascal(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `pascalToCamel()` — understanding this method

**Purpose:** Part of the `CaseConverter` service's responsibility: convert names between snake_case, camelCase and PascalCase.

**How to study it:** Open the source and find `pascalToCamel(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `camelToPascal()` — understanding this method

**Purpose:** Part of the `CaseConverter` service's responsibility: convert names between snake_case, camelCase and PascalCase.

**How to study it:** Open the source and find `camelToPascal(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `toCamelCaseArray()` — understanding this method

**Purpose:** Part of the `CaseConverter` service's responsibility: convert names between snake_case, camelCase and PascalCase.

**How to study it:** Open the source and find `toCamelCaseArray(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `arrayToCamelCaseArray()` — understanding this method

**Purpose:** Part of the `CaseConverter` service's responsibility: convert names between snake_case, camelCase and PascalCase.

**How to study it:** Open the source and find `arrayToCamelCaseArray(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `arrayToCamelCase()` — understanding this method

**Purpose:** Part of the `CaseConverter` service's responsibility: convert names between snake_case, camelCase and PascalCase.

**How to study it:** Open the source and find `arrayToCamelCase(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

## Practical LifeTech module example: convert a database field name for an api response

**Scenario:** A developer is building an `MdExample` module and wants to use `CaseConverter` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\CaseConverter;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        $modelName = CaseConverter::snakeToPascal('tb_card_profile');
        return LtResponse::json('Model name converted', '2000', '200', [
            'modelName' => $modelName
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

**Source-specific caution:** Some methods require a model, configured database connection or application context. The source method names alone do not establish standalone usage.

## Summary

Convert names between snake_case, camelCase and PascalCase. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/CaseConverter.php)
- [Back to MdLt Services index](README.md)
- Previous: none
- [Next: LtAuth](LtAuth.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
