# Downloading and Running LifeTech OCMS

[Previous](getting-started-and-system-requirements.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](installation-process.md)

## On this page

- [1. Download the framework](#1-download-the-framework)
- [Method A - Composer](#method-a---composer)
- [Method B - GitHub](#method-b---github)
- [Method C - Official website](#method-c---official-website)
- [2. Start the application](#2-start-the-application)
- [Method A - PHP built-in server](#method-a---php-built-in-server)
- [Method B - XAMPP / WAMP / Laragon](#method-b---xampp--wamp--laragon)
- [Method C - Docker](#method-c---docker)
- [3. What happens next?](#3-what-happens-next)

## 1. Download the framework

## Method A - Composer

1. Open a terminal in the parent directory where you want your new project.
1. Run the command below; replace my-lifetech-site with your preferred new folder name.
1. Enter the created project folder.

```cmd
composer create-project lifetechocms/lifetechocms
cd lifetechocms
```

OR

```cmd
composer create-project lifetechocms/lifetechocms your-project-name
cd your-project-name
```

Composer downloads the published framework package and its dependencies. Do not run create-project into a directory already containing unrelated project files.

## Method B - GitHub

Clone the appropriate branch or release, then install dependencies:

```cmd
git clone https://github.com/lifetechOCMS/lifetechocms.git
```

## Method C - Official website

1. Visit [https://www.lifetech.host/hubs/download?release=software.](https://www.lifetech.host/hubs/download?release=software.)
1. Choose the appropriate LifeTech OCMS software release.
1. Download and extract the package into your preferred project directory.

## 2. Start the application

## Method A - PHP built-in server

From the project directory, run:

php lt start

For a custom port, where supported by your release:

php lt start 8080

Open the local address displayed by the command.

## Method B - XAMPP / WAMP / Laragon

1. Place the extracted or downloaded project in the web directory or configure a virtual host.
1. Start the web server and MySQL/MariaDB services.
1. Open the corresponding local site URL in a browser.

## Method C - Docker

1. Confirm Docker and Compose are installed.
1. Edit the project .env file before the first build [Installation Process](installation-process.md) Step 2.
1. Run the build/start command in the folder containing the Compose configuration.

```cmd
    docker compose up -d --build
```

## 3. What happens next?

1. PHP built-in server, XAMPP, WAMP and Laragon: open the site and complete the three-step browser wizard in Section [Installation Process](installation-process.md) Step 1.
1. Docker: the supplied container setup uses .env configuration and does not require the three-step browser wizard; follow [Installation Process](installation-process.md) Step 2.

Source: https://www.lifetech.host/hubs/Docs#downloading-and-running-lifetech-ocms

[Previous](getting-started-and-system-requirements.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](installation-process.md)
