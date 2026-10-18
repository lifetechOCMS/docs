[← Previous: Getting Started and System Requirements](01-system-requirements.md) | [Back to Get Started](README.md) | [Next: Installation Process →](03-installation-process.md)

---

# Downloading and Running LifeTech OCMS


## On this page

- [3.1 Download the framework](#31-download-the-framework)
- [3.2 Start the application](#32-start-the-application)
- [3.3 What happens next?](#33-what-happens-next)

## 3.1 Download the framework

### Method A — Composer

1. Open a terminal in the parent directory where you want your new project.
2. Run the command below; replace my-lifetech-site with your preferred new folder name.
3. Enter the created project folder.
```bash
composer create-project lifetechocms/lifetechocms my-lifetech-site
```

```bash
cd my-lifetech-site
```

Composer downloads the published framework package and its dependencies. Do not run create-project into a directory already containing unrelated project files.

### Method B — GitHub

Clone the appropriate branch or release, then install dependencies:

```bash
git clone https://github.com/lifetechOCMS/lifetechocms.git my-lifetech-site
```

```bash
cd my-lifetech-site
```

```bash
composer install
```

### Method C — Official website

1. Visit https://www.lifetech.host/hubs/download?release=software.
2. Choose the appropriate LifeTech OCMS software release.
3. Download and extract the package into your preferred project directory.

## 3.2 Start the application

### Method A — PHP built-in server

From the project directory, run:

```bash
php lt start
```

For a custom port, where supported by your release:

```bash
php lt start 8080
```

Open the local address displayed by the command.

### Method B — XAMPP / WAMP / Laragon

1. Place the extracted or downloaded project in the web directory or configure a virtual host.
2. Start the web server and MySQL/MariaDB services.
3. Open the corresponding local site URL in a browser.

### Method C — Docker

1. Confirm Docker and Compose are installed.
2. Edit the project .env file before the first build (see Section 4.2).
3. Run the build/start command in the folder containing the Compose configuration.
```bash
docker compose up -d --build
```

## 3.3 What happens next?

- PHP built-in server, XAMPP, WAMP and Laragon: open the site and complete the three-step browser wizard in Section 4.1.
- Docker: the supplied container setup uses .env configuration and does not require the three-step browser wizard; follow Section 4.2.

---

[← Previous: Getting Started and System Requirements](01-system-requirements.md) | [Back to Get Started](README.md) | [Next: Installation Process →](03-installation-process.md)
