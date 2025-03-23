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

## Code Style & Naming Conventions
1. **Indentation**: 4 spaces per level (no tabs).
2. **Line length**: 120 characters max.
3. **No trailing spaces**.
4. **Control structures** (if, while, for, etc.) must have a space before the opening parenthesis.
5. **Opening braces `{`** must be on the same line as the statement.
6. **Consideration** Please conside `lt` as a general abbreviation for lifetechocms

## Database Conventions

1. **Table Naming** should use **PascalCase** and must be in plural form, e.g., `TbUsers`, `TbOrders`.
2. **Column Naming** should use **camelCase**, e.g., `firstName`, `lastName`, `emailAddress`.  
3. **Primary Key Naming** should always be `ltId` from v3.0 for consistency.  
4. **Foreign Key Naming** should follow `{tableName}Id`, e.g., `userId`, `productId`.  
5. **Pivot Table Naming** should use both table names in PascalCase, e.g., `UserRole`, `OrderProduct`.  
6. **Timestamps** should always have `createdAt` and `updatedAt`.  
7. **Indexes** should be added to frequently searched columns for optimization.  
8. **Use Normalization** (3rd Normal Form) to avoid redundant data storage.  
9. **NULL Values** should be avoided when possible, use sensible default values.  
10. **Use Prepared Statements**   when interacting with the database without Maplite ORM, e.g.,
   ```php
   $stmt = $pdo->prepare("SELECT * FROM TbUsers WHERE emailAddress = :email");
   $stmt->execute(['email' => $email]); 
   ```

## Class Conventions

1. **Class names** should use **Pascal Case** (e.g., `MyClass`, `TbUsers`).
2. **Class names must start with `Lt`**, except if the class corresponds to a specific package (e.g., a database name). For example, the class name for the session should be `LtSession`. This is to avoid conflicts in the future, as another vendor might also use a `Session` class, and our `Lt` prefix will help prevent class name collisions.
3. You **do not need to use `Lt` as a prefix** if the class connects to a specific package, such as a database name or a module name. For example, `TbUsers` indicates that the class corresponds to an existing database table, and `MdBook` indicates a class related to an existing module.
4. **Class methods** should use **camelCase** and should **not** start with `Lt`.  
   - Example: `getUser()`, `findId()`.  
   - A full example: `TbUsers->findId()`.