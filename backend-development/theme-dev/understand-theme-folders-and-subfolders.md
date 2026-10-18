# Understand Theme Folders and Subfolders

[Previous](theme-content-and-the-four-resource-types.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](add-new-theme-content.md)

## On this page

- [How subfolders work](#how-subfolders-work)
- [What ddm and Export mean for a beginner](#what-ddm-and-export-mean-for-a-beginner)

Your local theme lives under packages/themes/ThemeStarter/. Both uploaded themes use the following folders, with these exact capital letters.

| **Folder** | **What belongs here** | **Beginner example** |
| --- | --- | --- |
| Components/ | Reusable page parts | Header.html, Footer.html |
| Views/ | Main page interfaces | Home.html, About.html |
| Layouts/ | Optional alternative page wrappers | DashboardLayout.html |
| Assets/ | Supporting styles and scripts | css/Style.css, js/Script.js |
| ddm/ | System-managed DDM marker files | Home.View.lifetech |
| Export/ | Records included when exporting a theme | content.json, page.json, menu.json |

README.md explains your theme to other developers. LICENSE states its licence. The generated index.php files are not your Home view; preserve the system files rather than replacing them with your interface.

## How subfolders work

A subfolder helps you organize related files. For example:

| **Resource type** | **Content name** | **Additional path** | **File location** |
| --- | --- | --- | --- |
| Component | Header.html | / | Components/Header.html |
| View | Home.html | / | Views/Home.html |
| Asset | Style.css | /css | Assets/css/Style.css |
| Asset | Script.js | /js | Assets/js/Script.js |
| Component | AdminHeader.html | /admin | Components/admin/AdminHeader.html |

The additional path belongs **inside the resource folder**. Do not enter the whole installation path in this field. /admin is an organizational folder; it does not automatically create an administration route or protect a page.

ThemeBlog uses lowercase admin; ThemeBrainDump uses folders such as Admin and Auth. Match the registered path exactly. Linux may treat admin and Admin as different folders.

## What ddm and Export mean for a beginner

**DDM means Data Defacing Model.** The supplied themes have .lifetech marker files named after content and its type, such as ContentLoadBody.Component.lifetech. These markers are empty in the supplied exports. Your actual interface code belongs in the resource files, not in these markers.

Export/content.json contains content registrations. Export/page.json contains page and route records. Export/menu.json contains menu records. Both supplied themes also have pageContent.json and table.json, currently containing empty arrays. Let LifeTechOCMS manage these records through its panel and export process.

Source: https://www.lifetech.host/hubs/Docs#understand-theme-folders-and-subfolders

[Previous](theme-content-and-the-four-resource-types.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](add-new-theme-content.md)
