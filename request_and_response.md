
# LifetechOCMS – Request Handling Guide

This document explains how HTTP requests are handled in **LifetechOCMS**, using its built-in `LtRequest` class.

---

## 🚀 Overview

LifetechOCMS uses a class called `LtRequest` to manage and simplify access to HTTP request data. This class encapsulates methods and properties for retrieving query parameters, POST data, uploaded files, request method, and more.

---

## 🧱 Basic Usage

```php
$request = new LtRequest();

// Accessing input parameters (GET or POST)
$username = $request->username;
$password = $request->password;
```

`LtRequest` automatically maps all request parameters as public properties.

---

---

## 🛡 Input Validation Example

```php
if (!filter_var($request->email, FILTER_VALIDATE_EMAIL)) {
    return response()->json(['error' => 'Invalid email']);
}
```

---

## 🔚 Summary

| Feature                 | Method/Usage                     |
|------------------------|----------------------------------|
| Get input field        | `$request->fieldName`            |
| Get request method     | `$request->method()`             |
| Check if AJAX request  | `$request->isAjax()`             |
| Get uploaded file      | `$request->file('input_name')`   |

---

## 📌 Notes

- `LtRequest` unifies GET, POST, PUT, DELETE, PATCH and FILE access for cleaner controller code.
- It's part of LifetechOCMS's secure, MVC-based architecture.

--- 

# LifetechOCMS – Response Handling Guide

# LifetechOCMS – Request & Response Handling Guide

This document explains how HTTP requests and responses are handled in **LifetechOCMS**, using its built-in `LtRequest` and `LtResponse` classes.

---

## 🚀 Overview

LifetechOCMS provides two core classes to simplify web development:

- `LtRequest`: Manages input and request information.
- `LtResponse`: Provides a standardized structure for returning HTTP responses.

---

## 🧱 LtRequest – Basic Usage

```php
$request = new LtRequest();

// Accessing input parameters (GET or POST)
$username = $request->username;
$password = $request->password;
```

`LtRequest` automatically maps all request parameters as public properties.

---

### 📥 Request Method

```php
$method = $request->method(); // 'GET', 'POST', etc.
```

---

### 🧪 Check if Request is AJAX

```php
$isAjax = $request->isAjax(); // Returns true or false
```

---

### 📁 Handling File Uploads

```php
$file = $request->file('avatar');

// Example: move uploaded file
if ($file) {
    $file->moveTo('uploads/');
}
```

---

### 🛡 Input Validation Example

```php
if (!filter_var($request->email, FILTER_VALIDATE_EMAIL)) {
    return response()->json(['error' => 'Invalid email']);
}
```

---

### 🔚 Summary

| Feature                 | Method/Usage                     |
|------------------------|----------------------------------|
| Get input field        | `$request->fieldName`            |
| Get request method     | `$request->method()`             |
| Check if AJAX request  | `$request->isAjax()`             |
| Get uploaded file      | `$request->file('input_name')`   |

---

## 📤 LtResponse – Standardized Response

The `LtResponse` class provides a consistent, structured format for all HTTP responses.

### 📦 Response Structure

```json
{
  "responseResult": "fail",
  "responseCode": 101,
  "responseCategory": 100,
  "responseData": null
}
```

### 🔑 Parameters

| Parameter           | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| `responseResult`    | Indicates success or failure. Default: `"fail"`                             |
| `responseCode`      | Numeric code representing the operation result. Default: `101`              |
| `responseCategory`  | Used to classify the response. `200` for success, `100` for failure         |
| `responseData`      | Any data returned by the request. Default: `null`                           |

---

### ⚙️ Basic Usage

```php
return LtResponse::json();
```

Returns the default failure response.

---

### ✅ Example – Success

```php
return LtResponse::json([
    'responseResult' => 'success',
    'responseCode' => 200,
    'responseCategory' => 200,
    'responseData' => ['user' => $user]
]);
```

---

### ❌ Example – Failure

```php
return LtResponse::json([
    'responseResult' => 'fail',
    'responseCode' => 102,
    'responseCategory' => 100,
    'responseData' => null
]);
```

---

### 📌 Notes

- `LtResponse::json()` always returns a JSON-formatted response.
- Follows a consistent structure to simplify frontend integration and API handling.
- Default values reflect a failure unless explicitly overridden.
