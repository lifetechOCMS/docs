# CaseConverter — Developer Guide

**Navigation:** Previous: None · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtDate](LtDate.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/CaseConverter.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/CaseConverter.php)

## Overview

`CaseConverter` converts names between **snake_case**, **camelCase**, and **PascalCase**. It also converts the keys of database result arrays into camelCase, which is useful when PHP models and API consumers use different naming conventions.

All nine methods in this class are **public static** methods. Call them with `CaseConverter::methodName(...)`; no object is needed.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\CaseConverter;
```

## Quick start

```php
$tableName = 'tb_card_profile';
$modelName = CaseConverter::snakeToPascal($tableName);

echo $modelName; // TbCardProfile
```

## Method reference

| Method | Call style | Input | Returns |
|---|---|---|---|
| `snakeToCamel($string)` | Static | `snake_case` string | `camelCase` string |
| `pascalToSnake($string)` | Static | `PascalCase` string | `snake_case` string |
| `camelToSnake($string)` | Static | `camelCase` string | `snake_case` string |
| `snakeToPascal($string)` | Static | `snake_case` string | `PascalCase` string |
| `pascalToCamel($string)` | Static | `PascalCase` string | `camelCase` string |
| `camelToPascal($string)` | Static | `camelCase` string | `PascalCase` string |
| `toCamelCaseArray(array $data)` | Static | Array of associative rows | Array of rows with camelCase keys |
| `arrayToCamelCaseArray(array $data)` | Static | Array of associative rows | Array of rows with camelCase keys |
| `arrayToCamelCase(array $data)` | Static | Array of associative rows | Array of `stdClass` objects with camelCase properties |

## Public methods with examples

### `snakeToCamel()` — snake_case to camelCase

Use this when converting a database field name into a PHP or JSON property name.

```php
$result = CaseConverter::snakeToCamel('user_first_name');
echo $result; // userFirstName
```

### `pascalToSnake()` — PascalCase to snake_case

```php
$result = CaseConverter::pascalToSnake('UserProfile');
echo $result; // user_profile
```

### `camelToSnake()` — camelCase to snake_case

```php
$result = CaseConverter::camelToSnake('createdAt');
echo $result; // created_at
```

### `snakeToPascal()` — snake_case to PascalCase

Useful when generating a class-style name from a table name.

```php
$result = CaseConverter::snakeToPascal('tb_blog_post');
echo $result; // TbBlogPost
```

### `pascalToCamel()` — PascalCase to camelCase

```php
$result = CaseConverter::pascalToCamel('PageTitle');
echo $result; // pageTitle
```

### `camelToPascal()` — camelCase to PascalCase

```php
$result = CaseConverter::camelToPascal('pageTitle');
echo $result; // PageTitle
```

### `toCamelCaseArray()` — convert keys in multiple rows

Pass an **array of associative arrays**, such as database records.

```php
$rows = [
    ['user_id' => 1, 'first_name' => 'Ada'],
    ['user_id' => 2, 'first_name' => 'Tayo'],
];

$result = CaseConverter::toCamelCaseArray($rows);

// [
//     ['userId' => 1, 'firstName' => 'Ada'],
//     ['userId' => 2, 'firstName' => 'Tayo'],
// ]
```

### `arrayToCamelCaseArray()` — convert keys and keep array rows

This method currently performs the same conversion as `toCamelCaseArray()`.

```php
$rows = [
    ['page_name' => 'Home', 'route_path' => '/home'],
];

$result = CaseConverter::arrayToCamelCaseArray($rows);

// [['pageName' => 'Home', 'routePath' => '/home']]
```

### `arrayToCamelCase()` — convert keys and return object rows

Unlike the previous two methods, this returns an array of **`stdClass` objects**, not associative arrays.

```php
$rows = [
    ['page_name' => 'Home', 'is_published' => 1],
];

$result = CaseConverter::arrayToCamelCase($rows);

echo $result[0]->pageName; // Home
echo $result[0]->isPublished; // 1
```

**Input note:** The three array-conversion methods expect a collection of rows. For a single associative record, wrap it in an array first: `[$record]`.

## Practical LifeTech module example: format database records for an API

**Scenario:** An `MdExample` controller receives database-style associative rows with snake_case keys and wants to return camelCase keys in its JSON response.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\Modules\MdLt\Services\CaseConverter;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Illustrative records; replace with your module's model results.
        $records = [
            ['post_id' => 101, 'post_title' => 'Getting Started'],
            ['post_id' => 102, 'post_title' => 'Theme Development'],
        ];

        $posts = CaseConverter::toCamelCaseArray($records);

        return LtResponse::json(
            'Posts loaded successfully',
            '2000',
            '200',
            $posts
        );
    }
}
```

The returned `responseData` contains keys such as `postId` and `postTitle`, instead of `post_id` and `post_title`.

## Summary

Use the six string methods for individual names. Use `toCamelCaseArray()` or `arrayToCamelCaseArray()` for arrays of associative records, and `arrayToCamelCase()` when you need object-style property access. All nine methods are static.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/CaseConverter.php)

---

**Navigation:** Previous: None · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtDate](LtDate.md)
