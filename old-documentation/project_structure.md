# Project Structure Page 
_A modern PHP backend framework for secure and modular applications wtih RBAC._

## 📖 Table of Contents  
1. [Go back](readme.md) 

This document outlines the standard folder structure of a LifetechOCMS application. It serves as a reference for developers who want to understand or contribute to the framework.

```
lifetechocms/
├── admin                # Core LifetechOCMS Administrator files
├── lifemodules/         # Custom application modules
│   └── mdPosProduct/    # Example module
│       ├── controllers/ # Controller files (PHP)
│       ├── services/    # Services files (PhP, Js, e.t.c)
│       ├── views/       # View files (HTML, Liferazor)
│       ├── models/      # Maplite ORM models (PhP)
│       └── screenshot/  # Keeping images of the module
│
├── lifethemes/          # Frontend UI themes
├── lifeplugins/         # Extendable functionality plugins
├── lifemedia/           # Keeping Media files
├── lifepage/            # Public root folder (entry: index.php)
├── lifezip/             # All Exported Zip Files
├── includes/            # Configuration files (e.g., database, tokens)
├── vendor/              # Composer-installed PHP dependencies
├── composer.json        # Composer package file
└── README.md            # Project description and overview
```

✅ Notes

All modules must be prefixed with md (e.g., mdPosBranch, mdBook).

Each module contains a complete MVC structure.
