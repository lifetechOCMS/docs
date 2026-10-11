# Theme Development Conventions

[Previous topic](02-accessing-themes-development.md) · [Contents](README.md) · [Next topic](04-add-theme-package.md)

## On this page

- [1. Theme package names use PascalCase](#1-theme-package-names-use-pascalcase)
- [2. File names and content names use PascalCase](#2-file-names-and-content-names-use-pascalcase)
- [3. Theme versions use v followed by three numeric parts](#3-theme-versions-use-v-followed-by-three-numeric-parts)
- [4. GitHub release tags use the same three part version](#4-github-release-tags-use-the-same-three-part-version)

Conventions give developers a consistent way to name packages and content. The four rules below cover package names, content names, theme versions and release tags. We can extend this section as more conventions are agreed.

## 1. Theme package names use PascalCase

PascalCase joins words without spaces and capitalizes the first letter of every word. Use it for theme package names.

| **Suitable name** | **Why it follows the convention** |
| --- | --- |
| ThemeNova | Theme and Nova each start with a capital letter |
| ThemeStarter | Theme and Starter each start with a capital letter |
| ThemeBlog | Theme and Blog each start with a capital letter |

For our walkthrough, enter ThemeStarter as the package name. Refer to that exact name when importing its content:

```php
<?php ltImport('ThemeStarter', 'Header.html'); ?>
```

The names themeStarter, theme_starter and Theme Starter do not follow this convention. Consistent spelling also helps avoid path and import errors.

## 2. File names and content names use PascalCase

Use PascalCase for the filename before its extension. Keep the extension appropriate to the file: .html, .css or .js in these examples.

| **Purpose** | **Content or filename** |
| --- | --- |
| Document opening | TopHeader.html |
| Dynamic content insertion point | ContentLoadBody.html |
| Main page interface | Home.html |
| Alternative page wrapper | DashboardLayout.html |
| Shared stylesheet | Style.css |
| Shared JavaScript | Script.js |

For example, register ContentLoadBody.html as Component content, then edit the matching file. An import must use the same registered name and capitalization.

This naming convention applies to developer-created theme content. Keep platform-generated filenames such as package.json and index.php as generated. Historical names in the supplied themes are shown as they exist; do not rename them without updating their registrations and references.

**Expected result:** you can choose a consistent package name and content filename before creating them.

## 3. Theme versions use v followed by three numeric parts

Use a version such as v1.0.0 for your theme. Keep the leading v and all three numeric parts. This is the convention for new theme releases in this guide; historical versions in supplied packages are shown as recorded.

| **Part** | **Meaning** | **Example** |
| --- | --- | --- |
| v | Version prefix | v1.0.0 |
| First number | Major version | v2.0.0 for a major release |
| Second number | Minor version | v1.1.0 for a minor release |
| Third number | Patch version | v1.0.1 for a patch release |

For example, ThemeStarter begins at v1.0.0. Record the release version consistently in the theme package information and its package.json metadata using the supported platform workflow.

## 4. GitHub release tags use the same three part version

Use GitHub tags such as v1.0.0, v1.0.1 and v1.1.0. The release tag must match the theme version being released. A tag identifies a particular source revision so developers can download and discuss the same release.

For a theme whose package version is v1.0.0, the matching release tag is v1.0.0. Avoid shortened tags such as v1.0 for this convention. Update the package version before preparing its matching release tag.

[Previous topic](02-accessing-themes-development.md) · [Contents](README.md) · [Next topic](04-add-theme-package.md)
