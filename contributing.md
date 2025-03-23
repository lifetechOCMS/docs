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

## Class Conventions

1. **Class names** should use **Pascal Case** (e.g., `MyClass`, `TbUsers`).
2. **Class names must start with `Lt`**, except if the class corresponds to a specific package (e.g., a database name). For example, the class name for the session should be `LtSession`. This is to avoid conflicts in the future, as another vendor might also use a `Session` class, and our `Lt` prefix will help prevent class name collisions.
3. You **do not need to use `Lt` as a prefix** if the class connects to a specific package, such as a database name or a module name. For example, `TbUsers` indicates that the class corresponds to an existing database table, and `MdBook` indicates a class related to an existing module.
4. **Class methods** should use **camelCase** and should **not** start with `Lt`.  
   - Example: `getUser()`, `findId()`.  
   - A full example: `TbUsers->findId()`.