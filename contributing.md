# Contributing Page 
_A modern PHP backend framework for secure and modular applications._

## 📖 Table of Contents  
1. [Go back](readme.md) 
2. [Code Style & Naming Conventions](#-code-style--naming-conventions)
3. [Class Conventions](#class-conventions)
3. [Function Conventions](#function-conventions)
3. [Database Conventions](#database-conventions)
3. [Module Conventions](#module-conventions)
3. [Theme Conventions](#theme-conventions)
3. [Plugin Conventions](#plugin-conventions)
3. [Plugin Conventions](#varriable-conventions)

## Code Style & Naming Conventions
1. **Indentation**: 4 spaces per level (no tabs).
2. **Line length**: 120 characters max.
3. **No trailing spaces**.
4. **Control structures** (if, while, for, etc.) must have a space before the opening parenthesis.
5. **Opening braces `{`** must be on the same line as the statement.
6. **Consideration** Please consider `lt` as a general abbreviation for lifetechocms


## Variable Conventions

1. **Variable names** should use **camelCase** (e.g., `$userName`, `$itemQty`).
2. **Constant variables** must be in uppercase with underscores (e.g., `define('APP_VERSION', '1.0.0');`).
3. **Boolean variables** should have a prefix of `is`, `has`, or `can` (e.g., `$isActive = true;`).

## Database Conventions

1. **Table Naming** should use **snake_case**  e.g., `tb_user`, `tb_order`.
2. **Column Naming** should use **snake_case**, e.g., `first_name`, `last_name`, `check_last_inf`.  
3. **Primary Key Naming** may use be `lt_id` from v2.5 for consistency.  
4. **Foreign Key Naming** should follow `{tabe_name}_id`, e.g., `tb_user_id`, `tb_product_id`.  
5. **Pivot Table Naming** should use both table names in snake_case, e.g., `user_role`, `order_product`.  
6. **Timestamps** should always have `created_at` and `updated_at`.  
7. **Indexes** should be added to frequently searched columns for optimization.  
8. **Use Normalization** (3rd Normal Form) to avoid redundant data storage.  
9. **NULL Values** should be avoided when possible, use sensible default values.  
10. **Use Prepared Statements**   when interacting with the database without Maplite ORM, e.g.,
   ```php
   $stmt = $pdo->prepare("SELECT * FROM tb_user WHERE email_address = :email");
   $stmt->execute(['email' => $email]); 
   ```
## Model Conventions

1. **Model File Name** must be the same as the table name.
2. **Model File Names** must use Pascal Case (e.g., `TbUser.php`, `TbLmsProduct.php`).
3. **Model File Class** should be associated with a single Class of database table.

### Example 
For a database table named `tb_user`, the corresponding model class should be:

**File Name**: `TbUser.php`
```php
class TbUser extends LtModel {
    // Model for abstracting the tb_user table
}
```

# Controller Conventions

1. **File Naming** - Use **PascalCase** and end with `Controller`.  Example of TbUser table: `TbUserController.php`

2. **Controller Name** - Should be **descriptive** and represent the related functionality. Example: `TbUserController` for user-related actions.

3. **Method Naming** - Use **camelCase** for method names, describing the action. Example: `createUser()`, `updateUser()`

4. **Single Responsibility** - Each Datbase Table or Model should have **specific controller** for its functionality. Example: tb_user table should have its own `TbUserController` as a Controller.

---

### Example

**File Name**: `TbUserController.php`
```php
class TbUserController {
    public function createUser() {
        // Logic to create a user
    }

    public function updateUser() {
        // Logic to update a user
    }
}
```
## Class Conventions

1. **Class names** should use **Pascal Case** (e.g., `MyClass`, `TbUser`).
2. **Class names must start with `Lt`**, except if the class corresponds to a specific package (e.g., a database name). For example, the class name for the session should be `LtSession`. This is to avoid conflicts in the future, as another vendor might also use a `Session` class, and our `Lt` prefix will help prevent class name collisions.
3. You **do not need to use `Lt` as a prefix** if the class connects to a specific package, such as a database name or a module name. For example, `TbUser` indicates that the class corresponds to an existing database table, and `MdBook` indicates a class related to an existing module.
4. **Class methods** should use **camelCase** and should **not** start with `Lt`.  
   - Example: `getUser()`, `findId()`.  
   - A full example: `TbUser->findId()`.
5. **private/protected properties** should be prefix with an underscore **private $_apikey**

## Function Conventions  

1. **Use camelCase for Function Names**  e.g 
  ```php
  function ltGetUserData() { /* ... */ }
  ```
2. **lt** must start all function names e.g **ltCalculator()**
3. **Opening Brace {** Must Be on the Same Line of the function e.g **function ltProcessPayment($amount) {**
4. No Space Between **Function Name** and **Parentheses** e.g **function ltCalculateTax($price) { /* ... */ }**

## Module Conventions  

1. **Use camelCase for Module Names**  e.g  mdForum, mdLmsCourse
2. **md** must start all Module names e.g **mdLogin**
3. **Module** name must correspond to your project
4. **Readme.md** file must be included with the documentation


## Theme Conventions  

1. **Use camelCase for theme Names**  e.g  themeEducation, themeCommerce
2. **theme** must start all Theme names e.g **themeProduct**
3. **Theme** name must correspond to your designs
4. **Readme.md** file must be included with the documentation

## Plugin Conventions  

1. **Use camelCase for plugin Names**  e.g  plgEmail, plgExcel
2. **plg** must start all Plugin names e.g **plgBarcode**
3. **plugin** name must correspond to your plugins
4. **Readme.md** file must be included with the documentation
 