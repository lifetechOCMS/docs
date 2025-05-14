
# Routing & Navigation Page
_A modern PHP backend framework for secure and modular applications._

## 📖 Table of Contents
1. [Go back](readme.md)
2. [ltRoute Developer Documentation](#-ltroute-developer-documentation)
3. [`LtNavigate` Class](#navigation-class)
 

# 🚦LtRoute Developer Documentation

`LtRoute` is a lightweight PHP routing system designed to support HTTP method-based routing with optional middleware and controller invocation. It supports method spoofing (for PUT/DELETE in HTML forms or AJAX), parameter-based dispatching, and flexible syntax for defining routes.

---

## 📦 Usage Overview

To define routes, simply call the HTTP method statically on `LtRoute`. Supported methods include:
- `get()`
- `post()`
- `put()`
- `delete()`
- `patch()`

Each method accepts two arguments: the `first` parameter defines how the route is matched — either by the HTTP method parameter or directly by the URL — while the `second` parameter specifies the controller and method (or function) to invoke when the route matches.

```php
LtRoute::post('update@save', 'UserController@saveUser');
LtRoute::put('id@42', 'ModuleName@UserController@updateUser');
LtRoute::get('showUser', function(){
    echo ltResponse::json('User Showed');
});
```

### Route Matching Logic

#### Key Matching (`param@value`)
- When the key contains an `@`, it is interpreted as:
  - **Parameter**: the part before `@`
  - **Expected Value**: the part after `@`

  ```php
  LtRoute::put('update@action', 'UserController@updateUser');
  // $_REQUEST['update'] === 'action' triggers the route
  ```

- When the key has **no `@`**, it defaults to:
  - **Parameter**: `'action'`
  - **Expected Value**: the key itself

  ```php
  LtRoute::post('submitForm', 'FormController@handle');
  // $_REQUEST['action'] === 'submitForm' triggers the route
  ```

#### Direct URL Path Matching
If the key contains a forward slash (`/`), it will be matched against the current URL path.

```php
LtRoute::get('/home', 'HomeController@index');
// $_SERVER['REQUEST_URI'] === '/home' triggers the route
```

---

## 💡 Example
```php
LtRoute::post('submit@form', function() {
    echo "Form submitted!";
});

LtRoute::put('edit@user', 'UserController@edit');
LtRoute::delete('/user/delete', 'UserController@delete');
```

---

## 🔁 Method Spoofing
To support PUT, DELETE, PATCH in HTML forms or JS requests:

### HTML Form
```html
<form method="POST">
  <input type="hidden" name="_method" value="PUT">
  <input type="hidden" name="update" value="action">
  <button type="submit">Update</button>
</form>
```

### Axios Example (JS)
```js
axios({
  method: 'put',
  url: '/route',
  data: {
    update: 'action'
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
LtRoute::get('load@page', 'PageController@load');
LtRoute::post('submit@module', 'App\Module\Controller@submit');
```

---

## 🔐 Middleware
You can chain a middleware to a route:
```php
LtRoute::post('save@data', 'DataController@save')
    ->middleware('AuthMiddleware@handle');
```
Middleware can be:
- A closure
- A `Class@method` pair

If the middleware returns `false`, the request is halted.

---

## ⚙️ Custom Handlers
You can pass closures directly for quick testing or simple responses:
```php
LtRoute::get('ping@pong', function() {
    echo "Pong!";
});
```

---

## 🧠 Internal Notes
- JSON payloads (`application/json`) are parsed from `php://input`
- For PUT, PATCH, DELETE, request data is parsed manually.
- If the key has no match or the method doesn’t align, the route silently fails.

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
