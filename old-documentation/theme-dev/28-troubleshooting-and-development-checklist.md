# Troubleshooting and Development Checklist

[Previous topic](27-security-and-management-permissions.md) · [Contents](README.md) · [Next topic](29-example-themes-and-references.md)

## On this page

- [Solve common beginner problems](#solve-common-beginner-problems)
- [Final checklist](#final-checklist)

## Solve common beginner problems

| **Problem** | **Likely cause** | **What to check** |
| --- | --- | --- |
| PHP code appears as text | File opened outside LifeTechOCMS or loaded as a static asset | Open the configured LifeTechOCMS page and use registered imports |
| Header and footer appear but Home does not | Dynamic loader missing, or generated content settings changed | ContentLoadBody and the generated page content publication |
| Page has no styling | Style asset not imported or wrong registered name | TopHeader import and Style.css registration |
| Welcome button does nothing | Script not loaded or element names do not match | Footer import, ids and Console errors |
| About shows a JavaScript error | Script expects Home elements on every page | Keep the element existence checks |
| Navigation returns a missing page | Link and configured route differ | Match route spelling and capitalization |
| Dashboard wrapper appears twice | Shared components and layout both render it | Page default component publication and layout assignment |
| Import cannot find content | Wrong package, filename, resource type or additional path | Check the content record and exact capitalization |
| API returns an error | Backend dependency, token, permission or endpoint issue | Network response and application responseCategory |
| New local file is absent in the panel | File has no registered content record | Create/register content through the panel |

## Final checklist

1. Create the theme through the panel and preserve its generated metadata.
1. Register components, views and assets with the correct types and paths.
1. Load plain CSS inside style tags and plain JavaScript inside script tags.
1. Arrange document opening, header, dynamic loader and footer in order.
1. Check the page, menu and assignments automatically created for each View content item.
1. Build links with the site helper and that configured route.
1. Use layouts when a page needs a different composition.
1. Preview every page and install the modules required by API examples.
1. Export through LifeTechOCMS when preparing the theme for another installation.

[Previous topic](27-security-and-management-permissions.md) · [Contents](README.md) · [Next topic](29-example-themes-and-references.md)
