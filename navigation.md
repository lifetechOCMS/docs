
# Routing & Navigation Page
_A modern PHP backend framework for secure and modular applications._

## 📖 Table of Contents
1. [Go back](readme.md)
2. [ltRoute Documentation](#-ltroute-documentation)
3. [`LtNavigate` Class](#navigation-class)

## 🚦 ltRoute Documentation
A smart, modular routing system in LifetechOCMS for mapping user requests to appropriate controllers.

📌 Overview
ltRoute is LifetechOCMS’s internal router system that connects frontend view requests to controller actions within a specific module. Each module has its own routing file (e.g., mdPosProductRoute.php) that maps view requests to controller functions.

🧾 Route File Format
A routing file uses PHP conditionals to bind a specific action (based on view input or URL) to a controller function.
## 🧱 Routing Syntax
```
if (LtRoute::post('action', 'createBranch')) {
    //call on your controller class or return json value to the front-end
}
```
Example
```php
if (LtRoute::post('action', 'createBranch')) {
    ob_end_clean();
    ltImport('mdPosCore', 'TbPosBranchController.php');
    $branchCtrl = new TbPosBranchController();
    echo $branchCtrl->create();
    exit();
}
```
LtRoute::post('action', 'createBranch'):
Checks if the incoming request is a POST where the action=createBranch.

ltImport('mdPosCore', 'TbPosBranchController.php'):
Loads the controller securely using Data Defacing Model.

Controller method is executed and its result echoed.

exit() ensures no further code runs after handling the request.

## 🔀 Available Routing Methods
Method	Description
LtRoute::post(key, value)	Handles a POST request with a specific key/value pair
LtRoute::get(key, value)	Handles a GET request with a specific key/value pair

## `Navigation` Class

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
