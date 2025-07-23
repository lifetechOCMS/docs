
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

## 📥 Request Method

```php
$method = $request->method(); // 'GET', 'POST', etc.
```

---

## 🧪 Check if Request is AJAX

```php
$isAjax = $request->isAjax(); // Returns true or false
```

---

## 📁 Handling File Uploads

```php
$file = $request->file('avatar');

// Example: move uploaded file
if ($file) {
    $file->moveTo('uploads/');
}
```

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

- `LtRequest` unifies GET, POST, and FILE access for cleaner controller code.
- It's part of LifetechOCMS's secure, MVC-based architecture.

--- 

# LifetechOCMS – Response Handling Guide

This document explains how HTTP response are handled in **LifetechOCMS**, using its built-in `LtResponse` class.

---

## 🚀 Overview

LifetechOCMS uses a class called `LtResponse` to manage and simplify access to HTTP request data. This class encapsulates methods and properties for retrieving query parameters, POST data, uploaded files, request method, and more.

---

## 🧱 Basic Usage

```php
$response = new LtResponse();

// Accessing input parameters (GET or POST)
$username = $request->username;
$password = $request->password;
```

`Try to worki` automatically maps all request parameters as public properties.

---
