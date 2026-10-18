# Installation Process

[Previous](downloading-and-running-lifetech-ocms.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](first-run-administration-and-next-steps.md)

## On this page

- [Method A - Three-step installation wizard (non-Docker)](#method-a---three-step-installation-wizard-non-docker)
- [Step 1 - PHP Configuration Setup](#step-1---php-configuration-setup)
- [Step 2 - Database Configuration](#step-2---database-configuration)
- [Step 3 - Finish](#step-3---finish)
- [Method B - Docker installation (no browser wizard)](#method-b---docker-installation-no-browser-wizard)

## Method A - Three-step installation wizard (non-Docker)

## Step 1 - PHP Configuration Setup

1. Open the application URL.
1. Review Upload Max Size, Post Max Size and Execution Time.
1. If a check fails, update the active PHP configuration and restart the relevant service.
1. When all checks show OK, select Verify & Continue.

## Step 2 - Database Configuration

1. Enter your proposed database name.
1. For a typical local setup, retain the displayed host, username, port and password only if they match your actual database server.
1. Use Create / Verify to create or verify the connection.

The form includes Database Name, Username, Database Port No., Database Host, Database Password and an Advanced Database Privilege option. Some macOS configurations may need 127.0.0.1 instead of localhost. Do not assume an empty password is safe outside local development.

## Step 3 - Finish

When installation succeeds, the wizard displays Installation Complete and automatically redirects to the homepage. Confirm that the site loads before signing in to /admin.

**Figure 1 - PHP configuration verification**

 ![Installation Process screenshot](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/1ced17745188f5a9235b3f8ab41472e3.png)

**Figure 2 - Database configuration**

 ![Installation Process screenshot](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/45316b16431c95710334c6e27426e81d.png)

**Figure 3 - Installation complete**

 ![Installation Process screenshot](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/6926facd0f93360323fdd73a53f7f237.png)

## Method B - Docker installation (no browser wizard)

For Docker installations, configure the .env file before building. The Compose configuration must provide the required application and database services and initialisation steps. The sample below is based on the supplied LifeTech OCMS environment file; change example credentials before deployment.

| **Setting** | **Example** | **Purpose** |
| --- | --- | --- |
| **APP_NAME** | lifetechocms_main | Application name |
| **APP_PORT** | 8080 | Host port for website |
| **PHPMYADMIN_PORT** | 8081 | Host port for phpMyAdmin |
| **MYSQL_PORT** | 3307 | Host database port |
| **MYSQL_DATABASE / LT_DB_NAME** | lifetech_demo | Must refer to same database |
| **MYSQL_USER / LT_DB_USER** | lifetech_user | Must refer to same user |
| **MYSQL_PASSWORD / LT_DB_PASS** | Choose strong matching values | Database user password |
| **MYSQL_ROOT_PASSWORD** | Choose a separate strong password | Database root password |
| **LT_DB_HOST** | db | Docker Compose database service hostname |

1. Open .env and update the application name, port and database name.
1. Keep matching database name, user and password pairs consistent between MYSQL_* and LT_DB_* settings.
1. From the project directory, build and start the containers.

```cmd
docker compose up -d --build
```

1. Open the homepage and then /admin.

[http://localhost:8080/](http://localhost:8080/)

[http://localhost:8080/admin](http://localhost:8080/admin)

If APP_PORT is different, replace 8080 in the URLs. Existing Docker database volumes may retain older settings; changing .env alone may not recreate an existing database or user. Avoid deleting volumes without a backup.

Source: https://www.lifetech.host/hubs/Docs#installation-process

[Previous](downloading-and-running-lifetech-ocms.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](first-run-administration-and-next-steps.md)
