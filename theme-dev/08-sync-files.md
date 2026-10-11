# Sync Files

[Previous topic](07-add-new-theme-content.md) · [Contents](README.md) · [Next topic](09-editing-theme-content-code.md)

## On this page

- [Which folders are scanned](#which-folders-are-scanned)
- [Register a locally created view](#register-a-locally-created-view)
- [Use Sync Files with AI generated code](#use-sync-files-with-ai-generated-code)
- [Understand syncing versus editing](#understand-syncing-versus-editing)

Sync Files registers new files created locally in the theme's resource folders as content in the database. It is useful when you write files in a local editor or when an AI tool generates new theme files for you.

## Which folders are scanned

Place files inside the appropriate resource folder of the theme package. Sync Files applies to the Components, Views, Assets and Layouts folders.

| **Folder** | **Example new file** | **Content resource type** |
| --- | --- | --- |
| Components/ | Announcement.html | Component |
| Views/ | AboutUs.html | View |
| Assets/ | css/ExtraStyle.css | Asset |
| Layouts/ | LandingLayout.html | Layout |

Use the confirmed PascalCase naming conventions for developer-created content names. Choose the folder according to the content's job, not just its extension: both a view and a component can be HTML files.

## Register a locally created view

For example, create this file in the installation you are developing:

**packages/themes/ThemeStarter/Views/AboutUs.html**

Add a small interface:

```html
<section class="card">
    <h1>About our team</h1>
    <p>Learn about the people behind our website.</p>
</section>
```

Then:

1. Save AboutUs.html inside ThemeStarter's Views folder.
1. Open ThemeStarter's content management area in the backend.
1. Click **Sync Files**.
1. Find AboutUs.html in the content list and check that it is registered as View content.
1. Review its content settings and the related page and menu records, then preview it through LifeTechOCMS.

The confirmed purpose of Sync Files is file-to-database content registration. Check the page and menu results in your installed version rather than assuming every sync operation performs the same follow-up actions as Add Content.

**Expected result:** the locally created AboutUs.html is known to LifeTechOCMS and appears as a registered content item.

## Use Sync Files with AI generated code

Ask the AI tool to generate files using your theme's package name, correct resource folders and PascalCase content names. Place the generated files into the target installation, review their code, and run Sync Files. Inspect the registered content and preview the relevant pages.

A file generated in another directory or on another computer must first be copied into the target theme's resource folders. Sync Files registers files present in those folders; it does not retrieve files from an AI conversation.

## Understand syncing versus editing

| **Action** | **When to use it** |
| --- | --- |
| Add Content | Create and register content through the backend |
| Sync Files | Register new files placed locally in the resource folders |
| Code Editor or local editing | Change code in an existing registered file |
| Upload | Update an existing content item with an edited file |

Saving an existing registered file changes its code. Creating a new file adds a file to disk; Sync Files supplies its content registration. After syncing, review publication, access and default component settings separately.

[Previous topic](07-add-new-theme-content.md) · [Contents](README.md) · [Next topic](09-editing-theme-content-code.md)
