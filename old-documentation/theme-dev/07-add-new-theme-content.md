# Add New Theme Content

[Previous topic](06-understand-theme-folders-and-subfolders.md) · [Contents](README.md) · [Next topic](08-sync-files.md)

## On this page

- [Understand the content form](#understand-the-content-form)

Open ThemeStarter and select **Add Content**. Create the following items one at a time.

| **Content name** | **Resource type** | **Additional path** | **Is Theme Default** |
| --- | --- | --- | --- |
| TopHeader.html | Component | / | Yes |
| Header.html | Component | / | Yes |
| ContentLoadBody.html | Component | / | Yes |
| Footer.html | Component | / | Yes |
| Home.html | View | / | No |
| About.html | View | / | No |
| Style.css | Asset | /css | No |
| Script.js | Asset | /js | No |

For this tutorial, choose **Folder** as the storage type and write a short description for each item. Keep content names free of spaces and include their extensions.

## Understand the content form

| **Setting** | **What to enter or select** | **Why it matters** |
| --- | --- | --- |
| Content Name | The filename, such as Home.html | Used when identifying or importing content |
| Description | A brief purpose, such as Main navigation | Helps you recognize the content later |
| Content Category | An optional organization label | Groups content in management; it is not its resource folder |
| Resource Type | Component, View, Layout or Asset | Determines the content's role and resource folder |
| Additional Path | /, /css, /js or another subfolder | Organizes files within that resource folder |
| Store Type | Folder for these examples | Stores code in the corresponding file |
| Is Theme Default | Yes for the shared components above | Identifies the default page composition |

Depending on the panel, resource type may be labelled **Theme Resource Type**. The exports store it as themeResourceType, the subfolder as additionalPath, and the default flag as isThemeDefault.

After creating an item, use its **Code Editor** action to enter the code in sections [Build the Shared Theme Components](11-build-the-shared-theme-components.md#build-the-shared-theme-components) to [Create Views Pages and Menus](13-create-views-pages-and-menus.md#create-views-pages-and-menus). If you create files locally instead, use Sync Files to register them, as explained in section [Sync Files](08-sync-files.md#sync-files).

**What you have now:** eight registered items. Sections '**Build the Shared Theme Components**' to '**Create Views Pages and Menus**' give each item a specific job.  

![image](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/c144949b1140ee0331f7c310c1030806.png)

[Previous topic](06-understand-theme-folders-and-subfolders.md) · [Contents](README.md) · [Next topic](08-sync-files.md)
