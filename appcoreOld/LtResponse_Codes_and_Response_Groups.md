# LtResponse Codes and Response Groups — Developer Guide

> **LifeTech OCMS core service** · `MdLt`
>
> Related: [LtResponse — Developer Guide](LtResponse.md)

## Overview

LifeTech OCMS uses **four-digit response codes** to identify specific outcomes from framework services, modules, and APIs. Response codes are organized into reserved **response groups** so developers can choose codes consistently and avoid collisions.

The response code is different from the response category: a code identifies *which outcome occurred*, while a category identifies whether the operation succeeded or failed.

## Response code rules

- A response code **must consist of exactly four digits** (`0000` through `9999` in format).
- Use the **assigned group range** for the feature or subsystem generating the response.
- Choose a code not already registered in `tb_response`; do not reuse codes for unrelated outcomes.
- Treat codes as **strings** in PHP and JSON to preserve formatting.
- Use response category `"200"` for success and `"100"` for failure.
- Do not confuse the four-digit application code with the HTTP status code.
- Document a clear response result and, for errors, a useful solution where appropriate.

### Example

```php
return LtResponse::json(
    'File created successfully',
    '1992',
    '200',
    ['filename' => 'example.txt']
);
```

`1992` is registered in the **File** group (`1900–1999`) as a successful file creation response.

## Registered response groups

The following groups are taken from the LifeTech OCMS **Add New Response** interface shown in your screenshot. Counts reflect records in the supplied `tb_response.sql` export, including disabled records.

| Response group | Four-digit range | Registered records in supplied SQL |
|---|---|---:|
| Authentication | `1000-1099` | 6 |
| Lw-token | `1100-1199` | 4 |
| API | `1200-1299` | 7 |
| Router | `1300-1399` | 2 |
| Menu | `1500-1599` | 4 |
| File | `1900-1999` | 25 |
| Maplite | `2000-2999` | 0 |
| User | `3000-3099` | 8 |
| Response | `3100-3149` | 1 |
| Role | `3200-3299` | 7 |
| Package | `3300-3399` | 14 |
| Page | `3400-3499` | 12 |
| Content | `3500-3599` | 6 |
| Customized | `4000-5999` | 0 |

**Note:** A group may reserve a range even when no records have yet been registered. The displayed ranges also leave gaps for future groups. Do not assign those gaps without an agreed group definition.

## Understanding response categories

| Category | Meaning | Example |
|---|---|---|
| `"200"` | Success | `1992` — File created successfully |
| `"100"` | Failure | `1909` — File not found |

A response group does **not** determine success or failure. Both successful and failed outcomes may share the same response group.

## How response codes are stored

The `tb_response` table in the supplied SQL export includes these relevant columns:

| Database column | Meaning |
|---|---|
| `response_code` | Four-digit application response code |
| `response_category` | Success (`200`) or failure (`100`) |
| `response_result` | Default result/message |
| `response_data` | Additional response data stored with the definition |
| `response_solution` | Suggested action or explanation for a failure |
| `response_group` | Numeric range, such as `1900-1999` |
| `response_group_name` | Group identifier, such as `file` |
| `package_name` | Package associated with the response |
| `content_name` | PHP file or content where the response is associated |
| `is_enabled` | Whether the record is enabled |

**Important:** The database currently defines `response_code` as `varchar(8)`, which can hold more than four characters. Therefore, the four-digit requirement is a **documentation/application validation rule**, not a constraint enforced by the shown SQL schema.

## Existing response codes — selected examples

These examples are drawn directly from the supplied `tb_response.sql` records.

| Code | Group | Category | Registered response result |
|---|---|---|---|
| `1001` | `1000-1099` | `100` | Record Not Found |
| `1002` | `1000-1099` | `200` | Login Successfully |
| `1102` | `1100-1199` | `100` | LWT Token Not Found |
| `1203` | `1200-1299` | `100` | API ROUTE &#039;Route Name&#039; is not Published |
| `1301` | `1300-1399` | `200` | Delete Successfully |
| `1501` | `1500-1599` | `200` | Menu parent fetched successfully |
| `1901` | `1900-1999` | `100` | Base path does not exist. |
| `1909` | `1900-1999` | `100` | FIle not found |
| `1992` | `1900-1999` | `200` | File created successfully |
| `3001` | `3000-3099` | `200` | User record fetched successfully. |
| `3102` | `3100-3149` | `100` | The response code already exists. Please enter a different code. |
| `3202` | `3200-3299` | `100` | Role Record Exist |
| `3301` | `3300-3399` | `200` | Package retrieve successfully |
| `3402` | `3400-3499` | `100` | failed to update: route path exist already |
| `3501` | `3500-3599` | `200` | Content moved successfully |

## Practical LifeTech module example: using registered response codes

A blog module should choose a code from its assigned response group. The example below uses **existing File group codes** to demonstrate the format; it is not proposing a new Blog group.

```php
<?php

namespace Lt\Modules\MdExample\Controllers;

use Lt\Modules\MdLt\Services\LtResponse;

class TbFileDemoController
{
    public function fileCreated(): string
    {
        return LtResponse::json(
            'File created successfully',
            '1992',
            '200',
            ['filename' => 'example.txt']
        );
    }

    public function fileMissing(): string
    {
        return LtResponse::error(
            'File not found',
            '1909',
            '100'
        );
    }
}
```

`LtResponse::error()` can replace the exposed message and code in production, as explained in [LtResponse — Developer Guide](LtResponse.md). The registered code remains useful for identifying the intended application outcome in development and internal logging.

## Registering a new response code

1. Open the LifeTech OCMS **Response Management** interface.
2. Select the appropriate **Response Group**.
3. Choose an unused **four-digit code within that group’s range**.
4. Enter a clear **Response Result** and its **Response Category**.
5. Add an appropriate **Response Solution** for errors, where helpful.
6. Save the record and reuse the same code consistently in the relevant service or controller.

Before creating a new code, search the existing records to avoid duplicates.

## Observations from the supplied database export

The following are **existing data observations**, not new response-code rules:

- The exported table has **96 response records**, including disabled records.
- All exported `response_code` values match the four-digit format.
- The table has a primary key on `lt_id`, but **no unique constraint on `response_code`** in the supplied schema.

### Codes outside their stored group range

The following records do not fall within their own `response_group` range:

| Code | Stored group | Result |
|---|---|---|
| `2005` | `1000-1099` | Table exist |
| `2005` | `1300-1399` | Table exist |

### Duplicate codes

These response codes occur more than once in the supplied export:

| Code | Number of records | Notes |
|---|---:|---|
| `2005` | 2 | 1000-1099 (enabled); 1300-1399 (disabled) |

### Possible category inconsistencies

These records use category `100` even though the message appears to describe success. Review their intended outcome before changing them:

| Code | Category | Result |
|---|---|---|
| `3306` | `100` | Module Package created successfully |
| `3309` | `100` | Table data retrieved successfully for export. |

## Source and navigation

- [LtResponse — Developer Guide](LtResponse.md)
- [Back to MdLt Services index](README.md)
- [View LtResponse source](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtResponse.php)
