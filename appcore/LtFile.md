# LtFile — Developer Guide

**Navigation:** [Previous: tableManagementService](tableManagementService.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtMail](LtMail.md)

> **LifeTech OCMS core service** · `MdLt`
>
> Source: [Services/LtFile.php](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtFile.php)

## Overview

Manage files and directories, including uploads, writing, copying and ZIP archives.

## Import the class

```php
<?php

use Lt\Modules\MdLt\Services\LtFile;
```

## Quick start

A small illustration of a public method (adapt the sample values to your application):

```php
$result = LtFile::path('packages/modules/MdExample/Storage');
```

## Method reference

| Public method | Call style | Arguments | Purpose / result |
|---|---|---|---|
| `path(string $basePath="",string $createPathIfNotExist = '')` | Static | `$basePath, $createPathIfNotExist` | Create a file manager for a base path; declared return `self`. |
| `size($value)` | Instance | `$value` | Configure the maximum upload size; declared return `self`. |
| `ext($extensions)` | Instance | `$extensions` | Configure permitted file extensions; declared return `self`. |
| `overwrite(bool $yes = true)` | Instance | `$yes` | Configure whether existing files may be replaced; declared return `self`. |
| `uploadFile($file)` | Instance | `$file` | Process an uploaded file. |
| `createFile(string $fileName, string $initialContent = '')` | Instance | `$fileName, $initialContent` | Create a file with initial content. |
| `writeFile(string $fileName, string $content)` | Instance | `$fileName, $content` | Write content to a file. |
| `deleteFile(string $fileName)` | Instance | `$fileName` | Delete a file. |
| `createFolder(string $folderName)` | Instance | `$folderName` | Create a directory. |
| `deleteFolder(string $folderName, bool $recursive = false)` | Instance | `$folderName, $recursive` | Delete a directory. |
| `download(string $fileName)` | Instance | `$fileName` | Prepare or serve a file download. |
| `createZip($folder, &$zipFile, $target)` | Instance | `$folder, $zipFile, $target` | Create a ZIP archive. |
| `copy($dst)` | Instance | `$dst` | Copy a file or directory. |
| `copyFolder($src, $dst)` | Instance | `$src, $dst` | Copy folder in the service. |
| `move($dst)` | Instance | `$dst` | Move a file or directory. |
| `moveFolder(string $src, string $dest, bool $overwrite = true)` | Instance | `$src, $dest, $overwrite` | Move folder in the service. |
| `deleteFolder2(string $dir)` | Instance | `$dir` | Delete folder2; declared return `void`. |
| `runUnlink($folderPath, $deleteMainFolder="yes")` | Instance | `$folderPath, $deleteMainFolder` | Run unlink in the service. |
| `unlink($fileName, $deleteMainFolder="yes")` | Instance | `$fileName, $deleteMainFolder` | Unlink in the service. |

## Public methods with examples

### `path()` — create a file manager for a base path

**Call style:** Static. **Parameters:** `string $basePath="",string $createPathIfNotExist = ''`.

```php
$result = LtFile::path('packages/modules/MdExample/Storage');
```

### `size()` — configure the maximum upload size

**Call style:** Instance. **Parameters:** `$value`.

```php
$service = LtFile::path('packages/modules/MdExample/Storage');
$result = $service->size('2MB');
```

### `ext()` — configure permitted file extensions

**Call style:** Instance. **Parameters:** `$extensions`.

```php
$service = LtFile::path('packages/modules/MdExample/Storage');
$result = $service->ext(['jpg', 'png']);
```

### `overwrite()` — configure whether existing files may be replaced

**Call style:** Instance. **Parameters:** `bool $yes = true`.

```php
$service = LtFile::path('packages/modules/MdExample/Storage');
$result = $service->overwrite();
```

### `uploadFile()` — process an uploaded file

**Call style:** Instance. **Parameters:** `$file`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->uploadFile('example.txt');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `createFile()` — create a file with initial content

**Call style:** Instance. **Parameters:** `string $fileName, string $initialContent = ''`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->createFile('example.txt');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `writeFile()` — write content to a file

**Call style:** Instance. **Parameters:** `string $fileName, string $content`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->writeFile('example.txt', 'Example content');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `deleteFile()` — delete a file

**Call style:** Instance. **Parameters:** `string $fileName`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->deleteFile('example.txt');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `createFolder()` — create a directory

**Call style:** Instance. **Parameters:** `string $folderName`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->createFolder('Exports');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `deleteFolder()` — delete a directory

**Call style:** Instance. **Parameters:** `string $folderName, bool $recursive = false`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->deleteFolder('Exports');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `download()` — prepare or serve a file download

**Call style:** Instance. **Parameters:** `string $fileName`.

```php
$service = LtFile::path('packages/modules/MdExample/Storage');
$result = $service->download('example.txt');
```

### `createZip()` — create a ZIP archive

**Call style:** Instance. **Parameters:** `$folder, &$zipFile, $target`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->createZip('Exports', 'EXAMPLE_VALUE', 'EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `copy()` — copy a file or directory

**Call style:** Instance. **Parameters:** `$dst`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->copy('EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `copyFolder()` — copy folder in the service

**Call style:** Instance. **Parameters:** `$src, $dst`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->copyFolder('EXAMPLE_VALUE', 'EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `move()` — move a file or directory

**Call style:** Instance. **Parameters:** `$dst`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->move('EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `moveFolder()` — move folder in the service

**Call style:** Instance. **Parameters:** `string $src, string $dest, bool $overwrite = true`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->moveFolder('EXAMPLE_VALUE', 'EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `deleteFolder2()` — delete folder2

**Call style:** Instance. **Parameters:** `string $dir`.

```php
// This operation can change application state; review permissions and inputs.
// $service = LtFile::path('packages/modules/MdExample/Storage');
// $result = $service->deleteFolder2('EXAMPLE_VALUE');
```

The call is intentionally commented out because it may modify records, files, sessions, or security state. Supply valid inputs and authorization before enabling it.

### `runUnlink()` — run unlink in the service

**Call style:** Instance. **Parameters:** `$folderPath, $deleteMainFolder="yes"`.

```php
$service = LtFile::path('packages/modules/MdExample/Storage');
$result = $service->runUnlink('EXAMPLE_VALUE');
```

### `unlink()` — unlink in the service

**Call style:** Instance. **Parameters:** `$fileName, $deleteMainFolder="yes"`.

```php
$service = LtFile::path('packages/modules/MdExample/Storage');
$result = $service->unlink('example.txt');
```

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

## Summary

Manage files and directories, including uploads, writing, copying and ZIP archives. See the method reference and practical module scenario for usage.

## Source

- [View the implementation on GitHub](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtFile.php)

---

**Navigation:** [Previous: tableManagementService](tableManagementService.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next: LtMail](LtMail.md)
