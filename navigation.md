
# Routing & Navigation Page
_A modern PHP backend framework for secure and modular applications._

## 📖 Table of Contents
1. [Go back](readme.md)
2. [ltRoute Documentation](#-ltroute-documentation)
3. [Go back](readme.md)

## 🚦 ltRoute Documentation
A smart, modular routing system in LifetechOCMS for mapping user requests to appropriate controllers.




# Documentation for `LtNavigate` Class

The `LtNavigate` class is designed to help with page navigation, building URLs with query parameters, storing session data, and handling redirects.

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

#### **1. `to($page_name = "", $module_name = "")`**
This sets the base path for redirection or URL building.

```php
$navigate = new LtNavigate();
$navigate->to('book_regg.html', 'md_library');
echo $navigate->getUrl();
```

#### **2. `withQuery(array $queryParams)`**
Appends query string parameters.

```php
$navigate->to('book_regg.html', 'md_library')->withQuery(['id' => 5]);
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
```

---

## 🧪 Usage Examples

### ✅ Example 1: Use `getUrl()` to Manually Link
```php
$url = ltNavigateTo('book_list.html', 'md_library')
        ->withQuery(['category' => 'fiction'])
        ->getUrl();

echo "<a href='$url'>View Fiction Books</a>";
```

### ✅ Example 2: Use `redirect()` After Form Submission
```php
ltNavigateTo('book_list.html', 'md_library')
    ->withQuery(['status' => 'success'])
    ->withData('message', 'Book saved successfully!')
    ->redirect();
```

---

## 🔧 Helper Functions

### `ltNavigateTo($page_name, $module_name)`
Returns an instance of `LtNavigate`.

```php
ltNavigateTo('book_regg.html', 'md_library')->getUrl();
```

### `ltNavigateData($key)`
Retrieves data from session.

```php
echo ltNavigateData('user');
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
ltNavigateTo('book_regg.html', 'md_library')
    ->withQuery(['id' => 5])
    ->withData('status', 'success')
    ->redirect();
```
