# LtFile — Developer Guide

> **LifeTech OCMS core service** · `MdLt` · `v1.x`
>
> Source: [Services/LtFile.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtFile.php)

## Overview

Manage files and directories, including uploads, writing, copying and ZIP archives.

This guide is written for a developer learning LifeTech OCMS services for the first time. The method inventory is based on the previously inspected `v1.x` source. For methods whose exact return values or visibility have not been established, the guide explicitly asks you to inspect the linked implementation rather than inventing a contract.

## Import the class

Inside a module controller or service:

```php
<?php

use Lt\Modules\MdLt\Services\LtFile;
```

An import only resolves the class name; it does not initialize the class or its dependencies. Check whether a method is `static` before choosing `ClassName::method()` versus an instance call.

## Quick start: a first practical example

The following illustrates a common use. Run it within a correctly configured LifeTech OCMS application.

```php
<?php
use Lt\Modules\MdLt\Services\LtFile;

// Configure a permitted base path and validate filenames before file operations.
```

## Method reference

| Method | Call style | Arguments | Actual behavior / return |
|---|---|---|---|
| `path($basePath, $createPathIfNotExist)` | Confirm in source | `$basePath, $createPathIfNotExist` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `size($value)` | Confirm in source | `$value` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `ext($extensions)` | Confirm in source | `$extensions` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `overwrite($yes)` | Confirm in source | `$yes` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `uploadFile($file)` | Confirm in source | `$file` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `createFile($fileName, $initialContent)` | Confirm in source | `$fileName, $initialContent` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `writeFile($fileName, $content)` | Confirm in source | `$fileName, $content` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `deleteFile($fileName)` | Confirm in source | `$fileName` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `createFolder($folderName)` | Confirm in source | `$folderName` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `deleteFolder($folderName, $recursive)` | Confirm in source | `$folderName, $recursive` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `download($fileName)` | Confirm in source | `$fileName` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `createZip($folder, &$zipFile, $target)` | Confirm in source | `$folder, &$zipFile, $target` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `copy($dst)` | Confirm in source | `$dst` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `copyFolder($src, $dst)` | Confirm in source | `$src, $dst` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `move($dst)` | Confirm in source | `$dst` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `moveFolder($src, $dest, $overwrite)` | Confirm in source | `$src, $dest, $overwrite` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `runUnlink($folderPath, $deleteMainFolder)` | Confirm in source | `$folderPath, $deleteMainFolder` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |
| `unlink($fileName, $deleteMainFolder)` | Confirm in source | `$fileName, $deleteMainFolder` | Manage files and directories, including uploads, writing, copying and ZIP archives. Exact method behavior, visibility and return type require checking the linked implementation. |

### `path()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `path(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `size()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `size(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `ext()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `ext(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `overwrite()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `overwrite(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `uploadFile()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `uploadFile(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `createFile()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `createFile(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `writeFile()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `writeFile(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `deleteFile()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `deleteFile(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `createFolder()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `createFolder(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `deleteFolder()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `deleteFolder(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `download()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `download(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `createZip()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `createZip(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `copy()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `copy(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `copyFolder()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `copyFolder(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `move()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `move(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `moveFolder()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `moveFolder(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `runUnlink()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `runUnlink(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

### `unlink()` — understanding this method

**Purpose:** Part of the `LtFile` service's responsibility: manage files and directories, including uploads, writing, copying and ZIP archives.

**How to study it:** Open the source and find `unlink(`. Check its visibility (`public`, `protected`, or `private`), whether it is static, how its parameters are used, what it returns, and whether it changes stored data. Do not assume a return type based only on the method name.

## Practical LifeTech module example: create a small text asset in a controlled folder

**Scenario:** A developer is building an `MdExample` module and wants to use `LtFile` from a controller. The example shows the service in a real controller-shaped context. Replace sample IDs and paths with actual application values, and ensure the necessary models and permissions are configured.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\\Modules\\MdLt\\Services\\LtFile;
use Lt\Modules\MdLt\Services\LtResponse;

class TbExampleController
{
    public function index()
    {
        // Only use a trusted, application-controlled relative path.
        $result = LtFile::path('packages/modules/MdExample/Storage', 'yes')
            ->createFile('welcome.txt', 'Welcome to MdExample');
        return $result; // Inspect the LtFile response format in your application.
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

**Source-specific caution:** Validate upload types and file paths; do not accept unrestricted user-controlled paths.

## Summary

Manage files and directories, including uploads, writing, copying and ZIP archives. Begin with the quick-start section, then use the method reference as a map to the implementation. Where a contract is not verified, treat it as a point to investigate rather than a promise.

## Source and navigation

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtFile.php)
- [Back to MdLt Services index](README.md)
- [Previous: LtDate](LtDate.md)
- [Next: LtLWToken](LtLWToken.md)

*This guide describes the `v1.x` branch inspected on 25 October 2026. Verify source details again after branch updates.*
