# Editing Theme Content Code

[Previous topic](08-sync-files.md) · [Contents](README.md) · [Next topic](10-edit-or-update-existing-theme-content.md)

## On this page

- [Use the built in code editor](#use-the-built-in-code-editor)
- [Work with a local code editor](#work-with-a-local-code-editor)
- [Check your saved changes](#check-your-saved-changes)

## Use the built in code editor

1. Open ThemeStarter from the theme list.
1. Find the registered content item, such as Header.html.
1. Select its **Code Editor** action, usually shown with a code symbol.
1. Enter or update its code and save.
1. Refresh Preview to check the result.

Start with the content created in section [Add New Theme Content](07-add-new-theme-content.md#add-new-theme-content). Sections [Build the Shared Theme Components](11-build-the-shared-theme-components.md#build-the-shared-theme-components) to  [Create Views Pages and Menus](13-create-views-pages-and-menus.md#create-views-pages-and-menus) provide the starter code.

## Work with a local code editor

For a local installation, open the corresponding registered file in VS Code, PHPStorm or another editor. In the updated structure, examples include:

packages/themes/ThemeStarter/Components/Header.html

packages/themes/ThemeStarter/Views/Home.html

packages/themes/ThemeStarter/Assets/css/Style.css

Save the file and refresh the page through LifeTechOCMS. You are editing the file used by that local installation, so you do not need to upload the same edit back to it. Changes made to a separate computer or checkout must still be transferred to the target installation.

The previous online guide used a single contents folder. Use the resource folders in the updated structure. Create/register a content item through the panel before expecting a new local file to appear in content management.

## Check your saved changes

Change a paragraph in Home.html, save it and open the generated Home page. The new text should appear. If PHP appears as text, check that you opened the page through LifeTechOCMS rather than opening the file directly.

[Previous topic](08-sync-files.md) · [Contents](README.md) · [Next topic](10-edit-or-update-existing-theme-content.md)
