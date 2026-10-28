# LtSiteInfo — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtSiteInfo.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtSiteInfo.php)

## Overview

Read site settings and construct site or package URLs.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtSiteInfo;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$result = LtSiteInfo::getSiteInfo();
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `getSiteInfo()` | Static | `None` | Read site configuration record. |
| `dbName()` | Static | `None` | Db name in the service. |
| `siteName()` | Static | `None` | Site name in the service. |
| `siteTitle()` | Static | `None` | Site title in the service. |
| `pageTitle()` | Static | `None` | Page title in the service. |
| `siteAlias()` | Static | `None` | Site alias in the service. |
| `siteCopyright()` | Static | `None` | Site copyright in the service. |
| `siteEmail()` | Static | `None` | Site email in the service. |
| `siteEmail2()` | Static | `None` | Site email2 in the service. |
| `sitePhone()` | Static | `None` | Site phone in the service. |
| `sitePhone2()` | Static | `None` | Site phone2 in the service. |
| `siteAddress()` | Static | `None` | Site address in the service. |
| `siteAddress2()` | Static | `None` | Site address2 in the service. |
| `siteLogo()` | Static | `None` | Site logo in the service. |
| `siteFavicon()` | Static | `None` | Site favicon in the service. |
| `siteOpenHour()` | Static | `None` | Site open hour in the service. |
| `siteClosedHour()` | Static | `None` | Site closed hour in the service. |
| `siteLinkedln()` | Static | `None` | Site linkedln in the service. |
| `siteInstagram()` | Static | `None` | Site instagram in the service. |
| `siteFacebook()` | Static | `None` | Site facebook in the service. |
| `siteTwitter()` | Static | `None` | Site twitter in the service. |
| `siteYoutube()` | Static | `None` | Site youtube in the service. |
| `siteHostAddress()` | Static | `None` | Site host address in the service. |
| `isHttps()` | Static | `None` | Check https status. |
| `domain()` | Static | `None` | Domain in the service. |
| `baseUrl()` | Static | `None` | Base url in the service. |
| `siteFaviconUrl()` | Static | `None` | Site favicon url in the service. |
| `siteLogoUrl()` | Static | `None` | Site logo url in the service. |
| `siteUrl()` | Static | `None` | Site url in the service. |
| `themePath()` | Static | `None` | Theme path in the service. |
| `modulePath()` | Static | `None` | Module path in the service. |
| `pluginPath()` | Static | `None` | Plugin path in the service. |

## Public methods with examples

### `getSiteInfo()` — read site configuration record

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::getSiteInfo();
```

### `dbName()` — db name in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::dbName();
```

### `siteName()` — site name in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteName();
```

### `siteTitle()` — site title in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteTitle();
```

### `pageTitle()` — page title in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::pageTitle();
```

### `siteAlias()` — site alias in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteAlias();
```

### `siteCopyright()` — site copyright in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteCopyright();
```

### `siteEmail()` — site email in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteEmail();
```

### `siteEmail2()` — site email2 in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteEmail2();
```

### `sitePhone()` — site phone in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::sitePhone();
```

### `sitePhone2()` — site phone2 in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::sitePhone2();
```

### `siteAddress()` — site address in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteAddress();
```

### `siteAddress2()` — site address2 in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteAddress2();
```

### `siteLogo()` — site logo in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteLogo();
```

### `siteFavicon()` — site favicon in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteFavicon();
```

### `siteOpenHour()` — site open hour in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteOpenHour();
```

### `siteClosedHour()` — site closed hour in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteClosedHour();
```

### `siteLinkedln()` — site linkedln in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteLinkedln();
```

### `siteInstagram()` — site instagram in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteInstagram();
```

### `siteFacebook()` — site facebook in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteFacebook();
```

### `siteTwitter()` — site twitter in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteTwitter();
```

### `siteYoutube()` — site youtube in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteYoutube();
```

### `siteHostAddress()` — site host address in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteHostAddress();
```

### `isHttps()` — check https status

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::isHttps();
```

### `domain()` — domain in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::domain();
```

### `baseUrl()` — base url in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::baseUrl();
```

### `siteFaviconUrl()` — site favicon url in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteFaviconUrl();
```

### `siteLogoUrl()` — site logo url in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteLogoUrl();
```

### `siteUrl()` — site url in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::siteUrl();
```

### `themePath()` — theme path in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::themePath();
```

### `modulePath()` — module path in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::modulePath();
```

### `pluginPath()` — plugin path in the service

**Call style:** Static. **Parameters:** `none`.

```php
$result = LtSiteInfo::pluginPath();
```

## Practical LifeTech module example: display the configured site name in a module

**Scenario:** A developer is building an `MdExample` module and wants to use `LtSiteInfo` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\LtSiteInfo;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        $name = LtSiteInfo::siteName();
        return LtResponse::json('Site information loaded', '2000', '200', [
            'siteName' => $name
        ]);
    }
}
```

**What happens:** The `index()` method demonstrates the service's role in a module request. Methods that read or change database records depend on the installed schema, active session, and appropriate authorization. Some service methods return JSON strings; do not double-encode their responses.

## Summary

Read site settings and construct site or package URLs. See the method reference and practical module scenario for usage.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtSiteInfo.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtSession](LtSession.md)
- [Next: LtValidator](LtValidator.md)
