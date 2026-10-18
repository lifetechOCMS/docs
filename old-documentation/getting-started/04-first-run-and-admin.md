[← Previous: Installation Process](03-installation-process.md) | [Back to Get Started](README.md)

---

# First Run, Administration and Next Steps


## On this page

- [5.1 Open your website](#51-open-your-website)
- [5.2 Sign in to the admin panel](#52-sign-in-to-the-admin-panel)
- [5.3 Next steps](#53-next-steps)
- [5.4 Troubleshooting](#54-troubleshooting)

## 5.1 Open your website

Non-Docker installations redirect to the homepage when the wizard finishes. Docker users open the configured mapped URL after containers start and the application is ready.

## 5.2 Sign in to the admin panel

Append /admin to your site base URL. The documented initial development credentials are:

- Username: developer
- Password: 123456

Security: change the default password immediately after first login. Never expose a site with these default credentials to the public internet.

## 5.3 Next steps

1. Review the dashboard and application settings.
2. Configure user accounts, roles and permissions.
3. Install or create a theme and publish site content.
4. Explore modules and plugins.
5. Continue with the Theme Development and Module Development guides.

## 5.4 Troubleshooting

- PHP verification fails: inspect the active php.ini, restart the relevant service and try again.
- Database verification fails: check the database service, hostname, port, credentials and privileges.
- Docker site unavailable: check container status, logs, port mapping and database readiness.
- /admin unavailable: verify the installation, base path and routing configuration.

### Documentation references

- https://www.lifetech.host/hubs/Docs#get-started
- https://www.lifetech.host/hubs/Docs#installation-process
- https://github.com/lifetechOCMS/docs

---

[← Previous: Installation Process](03-installation-process.md) | [Back to Get Started](README.md)
