
# Routing & Navigation Page
_A modern PHP backend framework for secure and modular applications._

## 📖 Table of Contents
1. [Go back](readme.md)
2. [ltRoute Developer Documentation](#ltroute-developer-documentation)
3. [`LtNavigate` Class](#navigation-class)
 

# LtRoute Developer Documentation

`LtRoute` is a lightweight Lifetechocms routing system designed to support HTTP method-based routing with optional middleware and controller invocation. It supports method spoofing (for PUT/DELETE in HTML forms or AJAX), parameter-based dispatching, and flexible syntax for defining routes.

---

## 📦 Usage Overview

This guide covers how to define and manage routes using the `LtRoute` class in **LifetechOCMS**. It supports RESTful paths, dynamic placeholders, and inline closures.

---

## 📌 Basic Syntax

```php
LtRoute::get('/students', 'ModuleName@ControllerName@methodName');
LtRoute::patch('/students/{id}', 'ModuleName@ControllerName@methodName');
LtRoute::post('/students', function () {
    echo "posting this method";
});
```

---

## 🧭 HTTP Methods

| Method     | Usage Example |
|------------|----------------|
| GET        | `LtRoute::get('/path', 'Module@Controller@method')` |
| POST       | `LtRoute::post('/path', function() {})` |
| POST       | `LtRoute::put('/path{id}', function() {})` |
| PATCH      | `LtRoute::patch('/path/{id}', 'Module@Controller@method')` |
| DELETE     | `LtRoute::delete('/path/{id}', 'Module@Controller@method')` |

---

## 🧩 Dynamic Routes

You can define routes with placeholders using curly braces:

```php
LtRoute::get('/students/{id}', 'ModuleName@StudentController@view');
```

The `{id}` placeholder is automatically extracted and passed as an argument to the controller method.

---

## 🔒 Closure Support

Closures can be used directly in the route handler:

```php
LtRoute::get('/test', function () {
    echo "This is a closure route";
});
```

---

## 🧼 Notes

- All paths should start with a `/`.
- Always use proper `ModuleName@Controller@method` format.
- Supports RESTful design and dynamic parameters.

---

  

## 🔁 Method Spoofing
To support PUT, DELETE, PATCH in HTML forms or JS requests:

### HTML Form
```html
<form method="POST">
  <input type="hidden" name="_method" value="PUT">
  <input type="hidden" name="users" value="profile">
  <button type="submit">Update</button>
</form>
```

### Axios Example (JS)
```js
axios({
  method: 'put',
  url: '/route',
  data: {
    users: 'profile'
  }
});
```

`LtRoute` will recognize the spoofed `_method` and compare it with the route definition.

---

## 🧰 Controller Invocation
Supports the format:
- `'Controller@method'`
- `'Module@Controller@method'`

Example:
```php
LtRoute::get('/students', 'StudentController@load');
LtRoute::post('/students/regoster', 'mdStudent@StudentController@submit');
```

---

## 🔐 Middleware
Lifetechocms already incorporated with RBAC so just publish your route to a the role

---


This makes `LtRoute` a compact and flexible router for PHP projects.




# `Navigation` Class

The `LtNavigate` class is designed to help with page navigation, building URLs with query parameters, storing session data, and handling redirects.

Also the helper function is ltNavigateTo().

## **Class: `LtNavigate`**

### **Output**
---

## 🔁 `redirect()` vs 🌐 `getUrl()`

| Method       | Purpose                                            | Output/Effect                        | Typical Use Case                          |
|--------------|----------------------------------------------------|--------------------------------------|-------------------------------------------|
| `getUrl()`   | Returns the constructed URL as a string            | E.g., `/views/md_library/book_regg.html?id=5` | Use it when you need the URL but don't want to navigate yet. |
| `redirect()` | Immediately redirects the browser to the URL       | Uses `header("Location: ...")` + `exit()` | Use it when you're ready to send the user to the new page. |
 

---

### **Methods**

#### **1. `to($contentName = "", $moduleName = "")`**
This sets the base path for redirection or URL building.

```php
$navigate = new LtNavigate();
$navigate->to('BookRegg.html', 'mdLibrary');
echo $navigate->getUrl();
OR
echo  ltNavigateTo('BookRegg.html', 'mdLibrary')->getUrl();

//this will show something like this
https://www.yourdomain.com/mdLibrary/BookRegister
```

#### **2. `withQuery(array $queryParams)`**
Appends query string parameters.

```php
$navigate->to('BookRegg.html', 'mdLibrary')->withQuery(['id' => 5]);
OR
echo  ltNavigateTo('BookRegg.html', 'mdLibrary')->->withQuery(['id' => 5])->getUrl();

//this will show something like this
https://www.yourdomain.com/mdLibrary/BookRegister?id=5
```

#### **3. `withData($key, $value)`**
Stores session data such as flash messages or objects.

```php
$navigate->withData('message', 'Record saved');
```

#### **4. `getUrl()`**
Returns the constructed URL (does NOT redirect).

```php
echo $navigate->getUrl();
```

#### **5. `redirect()`**
Redirects the user to the constructed URL and exits the script.

```php
$navigate->redirect();
OR
ltNavigateTo('BookRegg.html', 'mdLibrary')->->withQuery(['id' => 5])->redirect();
```

---

## 🧪 Usage Examples

### ✅ Example 1: Use `getUrl()` to Manually Link
```php
$url = ltNavigateTo('BookRegg.html', 'mdLibrary')
        ->withQuery(['category' => 'fiction'])
        ->getUrl();

echo "<a href='$url'>View Fiction Books</a>";
```

### ✅ Example 2: Use `redirect()` After Form Submission
```php
ltNavigateTo('BookRegg.html', 'mdLibrary')
    ->withQuery(['status' => 'success'])
    ->withData('message', 'Book saved successfully!')
    ->redirect();
```

---

## 🔧 Additional Helper Functions

### `ltNavigateTo($ContentName, $ModuleName)`
Returns an instance of `LtNavigate`.

```php
ltNavigateTo('BookRegg.html', 'mdLibrary')->getUrl();
```

### `ltNavigateData($key)`
Retrieves data from session.

```php
echo ltNavigateData('message');
```

### `ltNavigateBack()`
Gets the previous page URL.

```php
echo ltNavigateBack();
```

---

## 📦 Summary

The `LtNavigate` class simplifies URL creation, data passing, and redirection in LifetechOCMS.

```php
ltNavigateTo('BookRegg.html', 'mdLibrary')
    ->withQuery(['id' => 5])
    ->withData('status', 'success')
    ->redirect();
```
