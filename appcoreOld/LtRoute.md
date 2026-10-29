# LtRoute — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtRoute.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtRoute.php)

## Overview

Register and handle module HTTP routes.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtRoute;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$result = LtRoute::__callStatic('EXAMPLE_VALUE', 'EXAMPLE_VALUE');
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `__callStatic($method, $args)` | Static | `$method, $args` |   call static in the service. |
| `trimBasePath()` | Instance | `None` | Trim base path in the service; declared return `string`. |
| `middleware($callback = null)` | Instance | `$callback` | Middleware in the service. |
| `invokeAction($value)` | Static | `$value` | Invoke action in the service. |
| `register($packageName = '' , $contentName='',$contentBody='')` | Static | `$packageName, $contentName, $contentBody` | Register in the service. |

## Public methods with examples

### `__callStatic()` —   call static in the service

**Call style:** Static. **Parameters:** `$method, $args`.

```php
$result = LtRoute::__callStatic('EXAMPLE_VALUE', 'EXAMPLE_VALUE');
```

### `trimBasePath()` — trim base path in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = new LtRoute();
$result = $service->trimBasePath();
```

### `middleware()` — middleware in the service

**Call style:** Instance. **Parameters:** `$callback = null`.

```php
$service = new LtRoute();
$result = $service->middleware();
```

### `invokeAction()` — invoke action in the service

**Call style:** Static. **Parameters:** `$value`.

```php
$result = LtRoute::invokeAction('yes');
```

### `register()` — register in the service

**Call style:** Static. **Parameters:** `$packageName = '' , $contentName='',$contentBody=''`.

```php
$result = LtRoute::register();
```

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

## Summary

Register and handle module HTTP routes. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtRoute.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtResponse](LtResponse.md)
- [Next: LtService](LtService.md)
