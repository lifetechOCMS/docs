# Lifetech OCMS Documentation  
_A modern PHP backend framework for secure and modular applications._

## 📖 Table of Contents  
1. [Introduction](#-introduction)  
2. [Core Features](#-core-features)  
3. [Getting Started](getting-started.md)  
4. [Installation](#-installation--running)  
5. [Publish Your First Content](#-publish-your-first-content)  
6. [Project Structure](project_structure.md)  
7. [Request & Response](request_and_response.md)  
8. [Importing Contents](#-importing-contents)  
9. [Menu, Routing & Navigation](navigation.md)  
10. [Working with Modules](#-working-with-modules) 
11. [Auth & Classes](#-auth--classes)  
12. [Security Features](#security-features)  
13. [Development Conventions](#development-conventions)  
14. [Contributing Guides](contributing.md)  
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
   ```
2. **Installing via Composer**  
   ```sh 
   composer create-project lifetechocms/lifetechocms "your-project-name"
   ```
## Running the application locally
1. locate your folder terminal
   ```sh
   php lt start
   ```
if you want specific port number then 
   ```sh
      php lt start "your-port-number"
   ```
## 📦 Project Structure
The framework structure can be found on [Project struture](project_structure.md) 

## 📦 Request and Response
Learn more on [LtRequest and LtResponse](request_and_response.md)  

## 📦 Api resource, Routing, Page Navigation and menus
Learn more on [LtRouting and LtNavigation](navigation.md) 

## 📦 Importing Contents

LifetechOCMS uses a custom import function called ltImport() to load files such as models, controllers, helpers, or other PHP resources from a module. This design promotes modularity, security, and clean architecture by keeping each module self-contained.

🧠 Syntax
```
ltImport('ModuleName', 'FileName.ext');
```

🔍 Example
```
ltImport('mdPosProduct', 'TbProduct.php');
```


This loads the TbProduct.php file from the appropriate directory within the mdPosProduct module, depending on its registered type in the database.

📁 Import Target Order

The ltImport() function checks the database for the file's registration and determines its directory by the following MVC type:

MVC_TYPE : service / controller / Model / View

The search respects the module structure and includes the file accordingly. 

## 💡 Why Use ltImport() Over Namespaces?

While ltImport() functions similarly to a namespace-based loader, it provides additional features tailored to LifetechOCMS, such as:

✅ Acts like a namespace-based importer for organizing files across modules

🔐 Handles internal runtime code decryption using the Data Defacing Model (DDM)

🔎 Ensures secure inclusion based on database-registered module structure

🔄 Works uniformly across controllers, models, services, and view logic

In short, ltImport() combines the organizational benefits of namespaces with enhanced runtime security and modular loading control.


## ⚡ contributing  
1. **Download via GitHub**  
   ```sh
   git clone https://github.com/lifetechOCMS/lifetechocms.git