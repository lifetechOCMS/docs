# Add Theme Package

[Previous topic](03-theme-development-conventions.md) · [Contents](README.md) · [Next topic](05-theme-content-and-the-four-resource-types.md)

## On this page

- [Understand package metadata and dependencies](#understand-package-metadata-and-dependencies)

1. Sign in to the backend.
1. Open **Packages > Themes Development**.
1. Choose **Create Theme** or **Add Theme Package**.
1. Enter ThemeStarter as the package name. Use no spaces.
1. Enter a description such as A beginner theme with Home and About pages.
1. Enter a package version such as 1.0.0 and submit the form.
1. Open ThemeStarter to manage its content.

Creating the theme from the panel generates its package metadata and necessary folders. Use these generated files as your starting point. The exact button labels may vary between installed versions.

**What you have now:** a theme package ready for content. A package without page content is not yet a complete website design.

## Understand package metadata and dependencies

package.json describes the package. It is LifeTechOCMS package metadata; its name does not mean you must install Node.js or run npm to create a basic theme.

An example of the fields used in the supplied themes is:

```json
{
    "ltId": "178798888476666",
    "packageName": "ThemeBlog",
    "packageType": "theme",
    "version": "1",
    "dependsOn": [
        {
            "packageName": "MdBlog",
            "version": "1.0.0"
        }
    ],
    "isPublished": null,
    "readme": "",
    "languageUsed": "html, tailwind\/css, javascript",
    "description": "Theme Blog",
    "ltVersion": "2.7.4"
}
```

This is a shortened explanation, not a replacement for the generated manifest. Keep the other fields and identifiers created by LifeTechOCMS.

1. ltId uniquely identifies the package.
1. packageName identifies the package by name.
1. packageType specifies the package type, such as theme.
1. version identifies the theme's release version.
1. dependsOn lists required packages and their compatible versions. For example, ThemeBlog depends on MdBlog version 1.0.0 for blog functionality and data.
1. isPublished indicates the package's publication status,
1. readme contains introductory documentation and usage instructions.
1. languageUsed lists the technologies used to build the theme.
1. description provides a brief summary of the package's purpose.
1. ltVersion specifies the LifeTechOCMS version associated with the package.

![image](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/e29ced364add1115c56b86eabc51318f.png)

[Previous topic](03-theme-development-conventions.md) · [Contents](README.md) · [Next topic](05-theme-content-and-the-four-resource-types.md)
