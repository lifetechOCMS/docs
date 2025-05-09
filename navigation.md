# Routing & Navigation Page 
_A modern PHP backend framework for secure and modular applications._

## 📖 Table of Contents  
1. [Go back](readme.md) 

# Documentation for `LtNavigate` Class

The `LtNavigate` class is designed to help with page navigation, building URLs with query parameters, storing session data, and handling redirects. Below is an explanation of the class methods and their usage.

---

### **Summary**

The `LtNavigate` class and its helper functions provide an easy way to build navigation links, pass query parameters, store session data, and handle redirects. The following is a simple example of how to use all these features:

```php
// Example usage:
$navigate = new LtNavigate();

// Navigate to a page with query parameters
$navigate->to('book_regg.html', 'md_library')
         ->withQuery(['status' => '21', 'id' => '5'])
         ->withData('user', 'JohnDoe');

// Redirect to the URL
$navigate->redirect();
```

Or use the helper function for quick navigation:

```php
// Using helper function to navigate
ltNavigateTo('book_regg.html', 'md_library')
    ->withQuery(['status' => '21', 'id' => '5'])
    ->redirect();
```

This class simplifies building URLs, passing data, and handling redirection within the application.


## **Class: `LtNavigate`**

### **Properties**
- **`$url`**: The base URL to which the query parameters will be appended.
- **`$queryParams`**: An array of query parameters to be added to the URL.

---

### **Methods**

#### **1. `to($page_name = "", $module_name = "")`**

This method sets the URL for navigation based on the `page_name` and `module_name`. It queries the `Lifepage` model to retrieve the correct URL.

##### **Parameters**
- **`$page_name`** (string, required): The name of the page to navigate to.
- **`$module_name`** (string, optional): The module name associated with the page.

##### **Returns**
- **`$this`**: Returns the current instance of `LtNavigate` for method chaining.

##### **Example Usage**
```php
$navigate = new LtNavigate();
$navigate->to('book_regg.html', 'md_library');
echo $navigate->getUrl();  // Outputs the constructed URL
```

---

#### **2. `withQuery(array $queryParams)`**

This method allows you to append query parameters to the navigation URL.

##### **Parameters**
- **`$queryParams`** (array, required): An associative array of query parameters to add to the URL.

##### **Returns**
- **`$this`**: Returns the current instance of `LtNavigate` for method chaining.

##### **Example Usage**
```php
$navigate = new LtNavigate();
$navigate->to('book_regg.html', 'md_library')->withQuery(['status' => '21', 'id' => '5']);
echo $navigate->getUrl();  // Outputs the URL with query parameters
```

---

#### **3. `withData($key, $value)`**

This method stores data in the session, which can be used later (e.g., for passing flash messages).

##### **Parameters**
- **`$key`** (string, required): The key under which the data is stored in the session.
- **`$value`** (mixed, required): The value to be stored in the session.

##### **Returns**
- **`$this`**: Returns the current instance of `LtNavigate` for method chaining.

##### **Example Usage**
```php
$navigate = new LtNavigate();
$navigate->to('book_regg.html', 'md_library')->withData('user', 'JohnDoe');
```

---

#### **4. `getUrl()`**

This method returns the constructed URL with the query parameters.

##### **Returns**
- **`string`**: The full URL with query parameters.

##### **Example Usage**
```php
$navigate = new LtNavigate();
$navigate->to('book_regg.html', 'md_library')->withQuery(['status' => '21']);
echo $navigate->getUrl();  // Outputs the URL
```

---

#### **5. `redirect()`**

This method redirects the user to the constructed URL and stops the script execution.

##### **Returns**
- **No return value**: The function will send a `Location` header and exit the script.

##### **Example Usage**
```php
$navigate = new LtNavigate();
$navigate->to('book_regg.html', 'md_library')->withQuery(['status' => '21'])->redirect();
```

---

### **Helper Functions**

These helper functions simplify the use of `LtNavigate`.

#### **1. `ltNavigateTo($page_name = "", $module_name = "")`**

This function provides a shorthand for creating an instance of `LtNavigate` and navigating to a page.

##### **Parameters**
- **`$page_name`** (string, required): The name of the page to navigate to.
- **`$module_name`** (string, optional): The module name associated with the page.

##### **Returns**
- **`LtNavigate`**: Returns an instance of `LtNavigate`.

##### **Example Usage**
```php
$navigate = ltNavigateTo('book_regg.html', 'md_library');
echo $navigate->getUrl();  // Outputs the constructed URL
```

---

#### **2. `ltNavigateData($key = "")`**

This function retrieves data stored in the session using a specified key

##### **Parameters**
- **`$key`** (string, required): The key under which the data is stored in the session.

##### **Returns**
- **`mixed`**: The value associated with the key stored in the session, or `null` if the key does not exist.

##### **Example Usage**
```php
$user = ltNavigateData('user');
echo $user;  // Outputs the value of 'user' from session
```

---

#### **3. `ltNavigateBack()`**

This function returns the URL of the previous page (i.e., the referer URL).

##### **Returns**
- **`string`**: The referer URL or `'/'` if no referer is found.

##### **Example Usage**
```php
$backUrl = ltNavigateBack();
echo $backUrl;  // Outputs the previous page URL or '/'
```

---

### **Summary**

The `LtNavigate` class and its helper functions provide an easy way to build navigation links, pass query parameters, store session data, and handle redirects. The following is a simple example of how to use all these features:

```php
// Example usage:
$navigate = new LtNavigate();

// Navigate to a page with query parameters
$navigate->to('book_regg.html', 'md_library')
         ->withQuery(['status' => '21', 'id' => '5'])
         ->withData('user', 'JohnDoe');

// Redirect to the URL
$navigate->redirect();
```

Or use the helper function for quick navigation:

```php
// Using helper function to navigate
ltNavigateTo('book_regg.html', 'md_library')
    ->withQuery(['status' => '21', 'id' => '5'])
    ->redirect();
```

This class simplifies building URLs, passing data, and handling redirection within the application.
