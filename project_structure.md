# Project Structure Page 
_A modern PHP backend framework for secure and modular applications._

## 📖 Table of Contents  
1. [Go back](readme.md) 

This document outlines the standard folder structure of a LifetechOCMS application. It serves as a reference for developers who want to understand or contribute to the framework.


```text
lifetechocms/
├── modules/             # Custom application modules
│   └── mdPosProduct/    # Example module
│       ├── controllers/ # Controller files (PHP)
│       ├── views/       # View files (HTML, Liferazor)
│       ├── models/      # Maplite ORM models
│       └── based/       # Base logic classes or helpers
│
├── themes/              # Frontend UI themes
├── plugins/             # Extendable functionality plugins
├── public/              # Public root folder (entry: index.php)
├── system/              # Core LifetechOCMS framework files
├── config/              # Configuration files (e.g., database, tokens)
├── storage/             # Cache, logs, session data
├── routes/              # Routing definitions per module
├── resources/           # Static assets and language files
├── vendor/              # Composer-installed PHP dependencies
├── .env                 # Environment configuration file
├── composer.json        # Composer package file
└── README.md            # Project description and overview
```


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
├── resources/           # Static assets and language files
├── vendor/              # Composer-installed PHP dependencies
├── composer.json        # Composer package file
└── README.md            # Project description and overview
```

✅ Notes

All modules must be prefixed with md (e.g., mdPosBranch, mdBook).

Each module contains a complete MVC structure.

The public/ folder should be the web root in deployment.

The system/ folder is not meant to be modified directly unless updating the core.