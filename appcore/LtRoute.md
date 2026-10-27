# LtRoute — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/LtRoute.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtRoute.php)

## Overview

Register and handle module HTTP routes.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\LtRoute;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

The following illustrates a common use. Run it within a correctly configured LifeTech OCMS application.

```php
<?php
use Lt\Modules\MdLt\Services\LtRoute;

LtRoute::get('/blog/posts', 'MdBlog@TbBlogController@index');
```

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `__callStatic($method, $args)` | Confirm in source | `$method, $args` | Register and handle module HTTP routes. Exact method behavior, visibility and return type require checking the linked implementation. |
| `middleware($callback = null)` | Confirm in source | `$callback = null` | Register and handle module HTTP routes. Exact method behavior, visibility and return type require checking the linked implementation. |
| `handle()` | Confirm in source | `None` | Register and handle module HTTP routes. Exact method behavior, visibility and return type require checking the linked implementation. |
| `register($packageName = '', $contentName = '', $contentBody = '')` | Confirm in source | `$packageName = '', $contentName = '', $contentBody = ''` | Register and handle module HTTP routes. Exact method behavior, visibility and return type require checking the linked implementation. |

### `__callStatic()` — understanding this method

**Purpose:** Part of the `LtRoute` service's responsibility: register and handle module HTTP routes.

**How to study it:** Open the source and find `__callStatic(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `middleware()` — understanding this method

**Purpose:** Part of the `LtRoute` service's responsibility: register and handle module HTTP routes.

**How to study it:** Open the source and find `middleware(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `handle()` — understanding this method

**Purpose:** Part of the `LtRoute` service's responsibility: register and handle module HTTP routes.

**How to study it:** Open the source and find `handle(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `register()` — understanding this method

**Purpose:** Part of the `LtRoute` service's responsibility: register and handle module HTTP routes.

**How to study it:** Open the source and find `register(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

## Practical LifeTech module example: register a blog route for a module controller

In a LifeTech module, routes connect an HTTP URL to a controller action. Place this in the module's route registration, not in the controller itself:

```php
<?php

use Lt\\Modules\\MdLt\\Services\\LtRoute;

// Put this registration in the module's route-registration file,
// not inside a controller action.
LtRoute::get('/blog/posts', 'MdBlog@TbBlogController@index');
```

A corresponding controller class and method must exist. Adapt the package name, path, and handler to your installed module.

## Common mistakes

1. Calling an instance method statically, or creating an object when only a static method is needed.
2. Guessing method arguments or return values instead of inspecting the implementation.
3. Running data-changing operations without permissions, validation, and error handling.
4. Assuming a service method is safe to expose as an unauthenticated endpoint.
5. Copying an example without adapting it to your module's model and route configuration.

**Source-specific caution:** The dynamic HTTP methods are implemented via `__callStatic`; routes can also be registered with the framework's page synchronization mechanism.

## Summary

Register and handle module HTTP routes. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtRoute.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtResponse](LtResponse.md)
- [Next: LtService](LtService.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
