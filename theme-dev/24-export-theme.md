# Export Theme

[Previous topic](23-set-theme-as-default.md) · [Contents](README.md) · [Next topic](25-installing-a-theme.md)

## On this page

- [Prepare the theme](#prepare-the-theme)
- [Export through the panel](#export-through-the-panel)
- [Understand what an export contains](#understand-what-an-export-contains)
- [Name the exported package](#name-the-exported-package)

## Prepare the theme

Preview its pages, save all changes and update the README and version. Check that required packages are documented and that content imports use correct names.

## Export through the panel

1. Open the theme's content area.
1. Choose **Export Theme**.
1. Download the resulting package and retain it as the version you intend to distribute.

Use **Export Theme** in the panel. A proper LifeTechOCMS export includes source files and registration records. This is how the supplied ThemeBlog and ThemeBrainDump packages combine presentation files with Export/ metadata.

Add a useful README explaining installation, required modules, pages and theme configuration. The supplied READMEs are empty, so they do not yet provide installation guidance.

## Understand what an export contains

The supplied exports combine source files with registration records such as content.json, page.json and menu.json. These records let the platform recognize the package's content and destinations. A ZIP containing only copied HTML files is not equivalent to a platform export.

## Name the exported package

Use a filename beginning with Theme, such as ThemeStarter.zip, as required by the previous installation documentation. Share installation guidance and dependency information with the ZIP.

**Expected result:** you have a platform-exported theme package ready for backup or installation.

[Previous topic](23-set-theme-as-default.md) · [Contents](README.md) · [Next topic](25-installing-a-theme.md)
