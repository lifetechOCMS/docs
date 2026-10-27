# LtSiteInfo — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/LtSiteInfo.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtSiteInfo.php)

## Overview

Read site settings and construct site or package URLs.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\LtSiteInfo;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

The following illustrates a common use. Run it within a correctly configured LifeTech OCMS application.

```php
<?php
use Lt\Modules\MdLt\Services\LtSiteInfo;

// Read the current site configuration through LtSiteInfo methods.
```

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `getSiteInfo()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `dbName()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteName()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteTitle()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `pageTitle()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteAlias()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteCopyright()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteEmail()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteEmail2()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `sitePhone()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `sitePhone2()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteAddress()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteAddress2()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteLogo()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteFavicon()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteOpenHour()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteClosedHour()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteLinkedln()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteInstagram()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteFacebook()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteTwitter()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteYoutube()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteHostAddress()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `isHttps()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `domain()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `baseUrl()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteFaviconUrl()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteLogoUrl()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `siteUrl()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `themePath()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `modulePath()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |
| `pluginPath()` | Confirm in source | `None` | Read site settings and construct site or package URLs. Exact method behavior, visibility and return type require checking the linked implementation. |

### `getSiteInfo()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `getSiteInfo(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `dbName()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `dbName(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteName()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteName(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteTitle()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteTitle(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `pageTitle()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `pageTitle(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteAlias()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteAlias(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteCopyright()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteCopyright(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteEmail()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteEmail(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteEmail2()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteEmail2(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `sitePhone()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `sitePhone(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `sitePhone2()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `sitePhone2(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteAddress()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteAddress(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteAddress2()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteAddress2(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteLogo()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteLogo(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteFavicon()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteFavicon(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteOpenHour()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteOpenHour(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteClosedHour()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteClosedHour(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteLinkedln()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteLinkedln(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteInstagram()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteInstagram(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteFacebook()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteFacebook(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteTwitter()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteTwitter(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteYoutube()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteYoutube(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteHostAddress()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteHostAddress(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `isHttps()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `isHttps(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `domain()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `domain(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `baseUrl()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `baseUrl(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteFaviconUrl()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteFaviconUrl(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteLogoUrl()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteLogoUrl(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `siteUrl()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `siteUrl(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `themePath()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `themePath(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `modulePath()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `modulePath(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `pluginPath()` — understanding this method

**Purpose:** Part of the `LtSiteInfo` service's responsibility: read site settings and construct site or package URLs.

**How to study it:** Open the source and find `pluginPath(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

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

## Common mistakes

1. Calling an instance method statically, or creating an object when only a static method is needed.
2. Guessing method arguments or return values instead of inspecting the implementation.
3. Running data-changing operations without permissions, validation, and error handling.
4. Assuming a service method is safe to expose as an unauthenticated endpoint.
5. Copying an example without adapting it to your module's model and route configuration.

**Source-specific caution:** Some methods require a model, configured database connection or application context. The source method names alone do not establish standalone usage.

## Summary

Read site settings and construct site or package URLs. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtSiteInfo.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtSession](LtSession.md)
- [Next: LtValidator](LtValidator.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
