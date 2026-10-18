# Getting Started and System Requirements

[Previous](get-started.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](downloading-and-running-lifetech-ocms.md)

## On this page

- [Choose your runtime first](#choose-your-runtime-first)
- [Before downloading](#before-downloading)
- [PHP configuration checks (non-Docker installer)](#php-configuration-checks-non-docker-installer)

## Choose your runtime first

You do not need to install every tool listed below. Select one runtime and follow only its requirements. Docker provides PHP, the web server and database as containers when those services are defined in the supplied Compose setup.

| **Runtime** | **Install on your computer** | **Separate PHP/MySQL installation?** |
| --- | --- | --- |
| **Docker** | Docker Desktop, or Docker Engine with Compose | No, if included in Compose |
| **XAMPP** | XAMPP bundle | No, when bundled |
| **WAMP** | WAMP bundle | No, when bundled |
| **Laragon** | Laragon with PHP and database services | No, when bundled |
| **PHP built-in server** | PHP CLI and MySQL/MariaDB service | Yes, unless already installed |

## Before downloading

1. Docker users: install Docker and confirm Docker Compose is available. You do not need to install PHP, Apache or MySQL on the host separately when the provided containers supply them.
1. XAMPP/WAMP/Laragon users: install one local server bundle with a compatible PHP version and database service.
1. PHP built-in server users: install a compatible PHP CLI and a running MySQL/MariaDB database service.
1. Composer download: Composer must be available in the environment where you run create-project.
1. GitHub download: Git is needed to clone the repository; Composer is needed to install PHP dependencies if they are not included.
1. Official website download: a browser and archive-extraction tool are sufficient to obtain the release; runtime requirements still depend on your chosen environment.

## PHP configuration checks (non-Docker installer)

The browser installation wizard checks Upload Max Size, Post Max Size and Execution Time. If any requirement fails, update the active php.ini used by the web server, restart that service and verify again. The exact required values are defined by the installer for the selected release.

Source: https://www.lifetech.host/hubs/Docs#getting-started-and-system-requirements

[Previous](get-started.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](downloading-and-running-lifetech-ocms.md)
