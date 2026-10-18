# First Run, Administration and Next Steps

[Previous](installation-process.md) · [Main documentation](../README.md) · [Guide contents](README.md) · Next

## On this page

- [Open your website](#open-your-website)
- [Sign in to the admin panel](#sign-in-to-the-admin-panel)
- [Next steps](#next-steps)
- [Troubleshooting](#troubleshooting)
- [Documentation references](#documentation-references)

## Open your website

Non-Docker installations redirect to the homepage when the wizard finishes. Docker users open the configured mapped URL after containers start and the application is ready.

## Sign in to the admin panel

Append /admin to your site base URL. The documented initial development credentials are:

1. Username: developer
1. Password: 123456

Security: change the default password immediately after first login. Never expose a site with these default credentials to the public internet.

## Next steps

1. Review the dashboard and application settings.
1. Configure user accounts, roles and permissions.
1. Install or create a theme and publish site content.
1. Explore modules and plugins.
1. Continue with the Theme Development and Module Development guides.

## Troubleshooting

1. PHP verification fails: inspect the active php.ini, restart the relevant service and try again.
1. Database verification fails: check the database service, hostname, port, credentials and privileges.
1. Docker site unavailable: check container status, logs, port mapping and database readiness.
1. /admin unavailable: verify the installation, base path and routing configuration.

## Documentation references

1. https://www.lifetech.host/hubs/Docs#get-started
1. https://www.lifetech.host/hubs/Docs#installation-process
1. https://github.com/lifetechOCMS/docs

Source: https://www.lifetech.host/hubs/Docs#first-run,-administration-and-next-steps

[Previous](installation-process.md) · [Main documentation](../README.md) · [Guide contents](README.md) · Next
