# Security and Management Permissions

[Previous](delete-theme.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](troubleshooting-and-development-checklist.md)

## On this page

- [Backend management roles](#backend-management-roles)
- [Page access and API permissions](#page-access-and-api-permissions)
- [Site wide changes](#site-wide-changes)
- [Safe output and external assets](#safe-output-and-external-assets)

## Backend management roles

Installing and deleting theme packages require privileged roles according to the existing documentation. Use a permitted backend account to manage packages. A visitor's permission to open a page is separate from a developer's permission to edit its theme.

## Page access and API permissions

Review the intended visitor roles on each page. For protected API calls, send the required token and let the backend enforce permissions. Hiding a button in the theme does not authorize or block the corresponding backend action.

## Site wide changes

Changing the default theme affects the main frontend design. Preview and test representative pages before applying it. Export the current theme if you need a restorable copy of its source and registrations.

## Safe output and external assets

Use htmlspecialchars when displaying text in HTML, json_encode when supplying PHP values to JavaScript, and textContent for plain text returned by APIs. Choose asset URLs intentionally and confirm their availability in the browser's Network panel.

**Expected result:** package management, page access and backend authorization are understood as separate responsibilities.

Source: https://www.lifetech.host/hubs/Docs#security-and-management-permissions

[Previous](delete-theme.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](troubleshooting-and-development-checklist.md)
