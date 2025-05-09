# Lifetech OCMS Documentation  
_A modern PHP backend framework for secure and modular applications._

## 📖 Table of Contents  
1. [Introduction](#-introduction)  
2. [Core Features](#-core-features)  
3. [Getting Started](getting-started.md)  
4. [Installation](#-installation--running)  
5. [Publish Your First Content](#-publish-your-first-content)  
6. [Project Structure](project_structure.md)  
7. [Working with Modules](#-working-with-modules)  
8. [Importing Contents](#-importing)  
9. [Menu, Routing & Navigation](navigation.md)  
10. [Auth & Classes](#-auth--classes)  
11. [Security Features](#security-features)  
12. [Development Conventions](#development-conventions)  
13. [Contributing Guides](contributing.md)  
---

## 🛠 Introduction  
Lifetech OCMS is a PHP framework designed with security, modularity, and performance in mind. It includes:  
- **DDM Encryption**: Secure deployment by encrypting source code.  
- **LW-Token System**: Secure authentication.  
- **Modular Structure**: Separate themes, modules, and plugins.  

---

## 🔹 Core Features  
- **Model-View-Controller (MVC) Architecture**  
- **Data Defacing Model (DDM) for Security**  
- **LW-Token System for Authentication**  
- **Maplite Query Builder for Database Operations**  
- **Custom Jlon Data Format**  
- **Frontend Flexibility (React, Vue, Angular, etc.)**  

---

## ⚡ Installation & Running 
1. **Download via GitHub**  
   ```sh
   git clone https://github.com/lifetechOCMS/lifetechocms.git
2. **Installing via Composer**  
   ```sh 
   composer create-project lifetechocms/lifetechocms "your-project-name"
## Running the application locally
1. locate your folder terminal
   ```sh
   php lt start
if you want specific port number then 
    ```sh
      php lt start "your-port-number"
## 📦 Importing in LifetechOCMS

LifetechOCMS uses a custom import function called ltImport() to load files such as models, helpers, or other PHP resources from a module. This keeps modules self-contained and promotes a clean architecture.

🧠 Syntax
```
ltImport('ModuleName', 'FileName.php');
```

🔍 Example
```
ltImport('mdPosProduct', 'TbProduct.php');
```

This will load the TbProduct.php file from the models/ directory of the mdPosProduct module.

📁 Import Target Order

The import system checks the following folders within a module:

models/

based/

controllers/

views/ (for helper PHP files, not templates)

If the file exists in any of these, it will be included.

💡 Best Practice

Always ensure your filenames match exactly, including case.

Avoid using the same filename in multiple folders of a module.


## ⚡ contributing  
1. **Download via GitHub**  
   ```sh
   git clone https://github.com/lifetechOCMS/lifetechocms.git