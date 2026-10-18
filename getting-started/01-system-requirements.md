[← Previous: Get Started](README.md) | [Back to Get Started](README.md) | [Next: Downloading and Running LifeTech OCMS →](02-download-and-run.md)

---

# Getting Started and System Requirements


## On this page

- [2.1 Choose your runtime first](#21-choose-your-runtime-first)
- [2.2 Before downloading](#22-before-downloading)
- [2.3 PHP configuration checks (non-Docker installer)](#23-php-configuration-checks-non-docker-installer)

## 2.1 Choose your runtime first

You do not need to install every tool listed below. Select one runtime and follow only its requirements. Docker provides PHP, the web server and database as containers when those services are defined in the supplied Compose setup.

| Runtime | Install on your computer | Separate PHP/MySQL installation? |
| --- | --- | --- |
| Docker | Docker Desktop, or Docker Engine with Compose | No, if included in Compose |
| XAMPP | XAMPP bundle | No, when bundled |
| WAMP | WAMP bundle | No, when bundled |
| Laragon | Laragon with PHP and database services | No, when bundled |
| PHP built-in server | PHP CLI and MySQL/MariaDB service | Yes, unless already installed |

## 2.2 Before downloading

- Docker users: install Docker and confirm Docker Compose is available. You do not need to install PHP, Apache or MySQL on the host separately when the provided containers supply them.
- XAMPP/WAMP/Laragon users: install one local server bundle with a compatible PHP version and database service.
- PHP built-in server users: install a compatible PHP CLI and a running MySQL/MariaDB database service.
- Composer download: Composer must be available in the environment where you run create-project.
- GitHub download: Git is needed to clone the repository; Composer is needed to install PHP dependencies if they are not included.
- Official website download: a browser and archive-extraction tool are sufficient to obtain the release; runtime requirements still depend on your chosen environment.

## 2.3 PHP configuration checks (non-Docker installer)

The browser installation wizard checks Upload Max Size, Post Max Size and Execution Time. If any requirement fails, update the active php.ini used by the web server, restart that service and verify again. The exact required values are defined by the installer for the selected release.

---

[← Previous: Get Started](README.md) | [Back to Get Started](README.md) | [Next: Downloading and Running LifeTech OCMS →](02-download-and-run.md)
