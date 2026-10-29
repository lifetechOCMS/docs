# LtNavigate — Developer Guide

**Navigation:** [Previous: LtRoute](LtRoute.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtAuth](LtAuth.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtNavigate.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtNavigate.php)

## Overview

Build navigation URLs and redirects.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtNavigate;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$result = LtNavigate::to();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `to($pageName = "", $moduleName = "")` | Static | `$pageName, $moduleName` | Resolve a page URL and create a navigation builder. |
| `__construct($pageName = "", $moduleName = "")` | Instance | `$pageName, $moduleName` |   construct in the service. |
| `__toString()` | Instance | `None` |   to string in the service. |
| `withQuery(array $queryParams)` | Instance | `$queryParams` | Append query parameters to the navigation URL. |
| `withData($key, $value)` | Instance | `$key, $value` | Save data to the session while building navigation. |
| `getUrl()` | Instance | `None` | Read the URL constructed by the navigation builder. |
| `redirect()` | Instance | `None` | Redirect in the service. |

## Public methods with examples

### `to()` — resolve a page URL and create a navigation builder

**Call style:** Static. **Parameters:** `$pageName = "", $moduleName = ""`.

```php
$result = LtNavigate::to();
```

### `__construct()` — initialize the service

The constructor prepares the service and its dependencies.

```php
$service = new LtNavigate();
```

### `__toString()` —   to string in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = LtNavigate::to('Dashboard', 'MdExample');
$result = $service->__toString();
```

### `withQuery()` — append query parameters to the navigation URL

**Call style:** Instance. **Parameters:** `array $queryParams`.

```php
$service = LtNavigate::to('Dashboard', 'MdExample');
$result = $service->withQuery(['page' => 2]);
```

### `withData()` — save data to the session while building navigation

**Call style:** Instance. **Parameters:** `$key, $value`.

```php
$service = LtNavigate::to('Dashboard', 'MdExample');
$result = $service->withData('dashboardTheme', 'yes');
```

### `getUrl()` — read the URL constructed by the navigation builder

**Call style:** Instance. **Parameters:** `none`.

```php
$service = LtNavigate::to('Dashboard', 'MdExample');
$result = $service->getUrl();
```

### `redirect()` — redirect in the service

**Call style:** Instance. **Parameters:** `none`.

```php
$service = LtNavigate::to('Dashboard', 'MdExample');
$result = $service->redirect();
```

## Practical LifeTech module example: build a link to an existing module page

**Scenario:** A developer is building an `MdExample` module and wants to use `LtNavigate` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\LtNavigate;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // 'Dashboard' must already be registered as a LifeTech page.
        $url = LtNavigate::to('Dashboard', 'MdExample')->getUrl();
        return LtResponse::json('Page link resolved', '2000', '200', [
            'url' => $url
        ]);
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Build navigation URLs and redirects. See the method reference and practical module scenario for usage.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtNavigate.php)

---

**Navigation:** [Previous: LtRoute](LtRoute.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtAuth](LtAuth.md)
