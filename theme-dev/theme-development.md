# LifeTechOCMS Theme Development

Source: https://www.lifetech.host/hubs/Docs#theme-development-overview

Website edition retrieved 10 October 2026.

## Contents

Select a topic or subtopic to navigate within this document.
- [Go back](../readme.md) 
- [Theme Development Overview](#theme-development-overview)
  - [What a theme does](#what-a-theme-does)
  - [Requirements and testing environment](#requirements-and-testing-environment)
  - [How to use this guide](#how-to-use-this-guide)
  - [Key terminology](#key-terminology)
- [Accessing Themes Development](#accessing-themes-development)
  - [Open the theme management area](#open-the-theme-management-area)
  - [Understand the theme list and actions](#understand-the-theme-list-and-actions)
- [Theme Development Conventions](#theme-development-conventions)
  - [1. Theme package names use PascalCase](#1-theme-package-names-use-pascalcase)
  - [2. File names and content names use PascalCase](#2-file-names-and-content-names-use-pascalcase)
  - [3. Theme versions use v followed by three numeric parts](#3-theme-versions-use-v-followed-by-three-numeric-parts)
  - [4. GitHub release tags use the same three part version](#4-github-release-tags-use-the-same-three-part-version)
- [Add Theme Package](#add-theme-package)
  - [Understand package metadata and dependencies](#understand-package-metadata-and-dependencies)
- [Theme Content and the Four Resource Types](#theme-content-and-the-four-resource-types)
  - [Component content](#component-content)
  - [View content](#view-content)
  - [Layout content](#layout-content)
  - [Asset content](#asset-content)
  - [How these types work together](#how-these-types-work-together)
- [Understand Theme Folders and Subfolders](#understand-theme-folders-and-subfolders)
  - [How subfolders work](#how-subfolders-work)
  - [What ddm and Export mean for a beginner](#what-ddm-and-export-mean-for-a-beginner)
- [Add New Theme Content](#add-new-theme-content)
  - [Understand the content form](#understand-the-content-form)
- [Sync Files](#sync-files)
  - [Which folders are scanned](#which-folders-are-scanned)
  - [Register a locally created view](#register-a-locally-created-view)
  - [Use Sync Files with AI generated code](#use-sync-files-with-ai-generated-code)
  - [Understand syncing versus editing](#understand-syncing-versus-editing)
- [Editing Theme Content Code](#editing-theme-content-code)
  - [Use the built in code editor](#use-the-built-in-code-editor)
  - [Work with a local code editor](#work-with-a-local-code-editor)
  - [Check your saved changes](#check-your-saved-changes)
- [Edit or Update Existing Theme Content](#edit-or-update-existing-theme-content)
  - [Edit content settings](#edit-content-settings)
  - [Upload an updated content file](#upload-an-updated-content-file)
  - [Check references after a change](#check-references-after-a-change)
- [Build the Shared Theme Components](#build-the-shared-theme-components)
  - [Add the stylesheet](#add-the-stylesheet)
  - [Create the document opening component](#create-the-document-opening-component)
  - [Understand ltSiteName](#understand-ltsitename)
  - [Understand ltImport](#understand-ltimport)
  - [Create the visible header and navigation](#create-the-visible-header-and-navigation)
  - [Add JavaScript and the footer](#add-javascript-and-the-footer)
  - [Know whether your asset already contains tags](#know-whether-your-asset-already-contains-tags)
- [Add the Compulsory Dynamic Content Loader](#add-the-compulsory-dynamic-content-loader)
  - [Add the loader to your theme](#add-the-loader-to-your-theme)
  - [How does it work](#how-does-it-work)
  - [Why is it necessary](#why-is-it-necessary)
  - [How is this different from ltImport](#how-is-this-different-from-ltimport)
  - [What if the page uses a separate layout](#what-if-the-page-uses-a-separate-layout)
- [Create Views Pages and Menus](#create-views-pages-and-menus)
  - [Write the Home and About views](#write-the-home-and-about-views)
  - [What happens when you create a view](#what-happens-when-you-create-a-view)
  - [Check the generated route before writing links](#check-the-generated-route-before-writing-links)
  - [Preview the generated pages](#preview-the-generated-pages)
  - [Review publication and access settings](#review-publication-and-access-settings)
- [Load Menus for the Current Users Roles](#load-menus-for-the-current-users-roles)
  - [Understand token and session identification](#understand-token-and-session-identification)
  - [Prepare the API and site addresses](#prepare-the-api-and-site-addresses)
  - [Load menu data without HTML or CSS](#load-menu-data-without-html-or-css)
  - [Inspect data before rendering](#inspect-data-before-rendering)
  - [Understand the response fields](#understand-the-response-fields)
  - [Display menus with plain HTML](#display-menus-with-plain-html)
  - [Connect loading and rendering](#connect-loading-and-rendering)
  - [Optional PHP rendering](#optional-php-rendering)
  - [Test roles and distinguish the two loaders](#test-roles-and-distinguish-the-two-loaders)
- [Understand the Default Layout and Custom Layouts](#understand-the-default-layout-and-custom-layouts)
  - [Default components form the default layout](#default-components-form-the-default-layout)
  - [15.2 Unpublish individual components on a page](#152-unpublish-individual-components-on-a-page)
  - [Create custom Layout content](#create-custom-layout-content)
  - [Add your own layout styling](#add-your-own-layout-styling)
  - [Assign pages to the custom layout](#assign-pages-to-the-custom-layout)
  - [Compare the two approaches](#compare-the-two-approaches)
- [Import Content and Load Content](#import-content-and-load-content)
  - [Method 1 Import registered content with ltImport](#method-1-import-registered-content-with-ltimport)
  - [Method 2 Load content through direct or CDN links](#method-2-load-content-through-direct-or-cdn-links)
  - [Which method should you use](#which-method-should-you-use)
- [Use Site Information and Helper Functions](#use-site-information-and-helper-functions)
  - [Other helpers used in your theme](#other-helpers-used-in-your-theme)
  - [Use more site configuration helpers](#use-more-site-configuration-helpers)
  - [Understand the URL and environment helpers](#understand-the-url-and-environment-helpers)
- [Connect Theme Views to Backend APIs](#connect-theme-views-to-backend-apis)
  - [Understand the API terms](#understand-the-api-terms)
  - [Create a Posts view](#create-a-posts-view)
  - [Read what the code does](#read-what-the-code-does)
  - [Send a token for a protected request](#send-a-token-for-a-protected-request)
- [Edit Theme Package](#edit-theme-package)
  - [Update package information](#update-package-information)
  - [Maintain the version and dependencies](#maintain-the-version-and-dependencies)
  - [Write a useful README](#write-a-useful-readme)
- [Previewing a Theme](#previewing-a-theme)
  - [Open Preview](#open-preview)
  - [Check the first working result](#check-the-first-working-result)
  - [Test pages and browser behaviour](#test-pages-and-browser-behaviour)
- [Publishing a Theme](#publishing-a-theme)
  - [Understand publishing](#understand-publishing)
  - [Publish through the panel](#publish-through-the-panel)
  - [Check content publication separately](#check-content-publication-separately)
- [Publish Theme to Page](#publish-theme-to-page)
  - [When to use a page specific theme](#when-to-use-a-page-specific-theme)
  - [Apply a theme to selected pages](#apply-a-theme-to-selected-pages)
  - [Distinguish theme selection from View creation](#distinguish-theme-selection-from-view-creation)
- [Set Theme as Default](#set-theme-as-default)
  - [What default means](#what-default-means)
  - [Select the default theme](#select-the-default-theme)
  - [What happens to the previous default](#what-happens-to-the-previous-default)
- [Export Theme](#export-theme)
  - [Prepare the theme](#prepare-the-theme)
  - [Export through the panel](#export-through-the-panel)
  - [Understand what an export contains](#understand-what-an-export-contains)
  - [Name the exported package](#name-the-exported-package)
- [Installing a Theme](#installing-a-theme)
  - [Method 1 Download and upload the theme](#method-1-download-and-upload-the-theme)
  - [Method 2 Browse Online from the backend](#method-2-browse-online-from-the-backend)
  - [Verify and choose how to use the theme](#verify-and-choose-how-to-use-the-theme)
- [Delete Theme](#delete-theme)
  - [Check before deleting](#check-before-deleting)
  - [Delete through the panel](#delete-through-the-panel)
  - [Check the result](#check-the-result)
- [Security and Management Permissions](#security-and-management-permissions)
  - [Backend management roles](#backend-management-roles)
  - [Page access and API permissions](#page-access-and-api-permissions)
  - [Site wide changes](#site-wide-changes)
  - [Safe output and external assets](#safe-output-and-external-assets)
- [Troubleshooting and Development Checklist](#troubleshooting-and-development-checklist)
  - [Solve common beginner problems](#solve-common-beginner-problems)
  - [Final checklist](#final-checklist)
- [Example Themes and References](#example-themes-and-references)
  - [Inspect the supplied themes](#inspect-the-supplied-themes)
  - [Documentation references](#documentation-references)

## Theme Development Overview

This guide teaches you how to create and manage a LifeTechOCMS theme. We build ThemeStarter with Home and About views, shared components, CSS and JavaScript, then add an optional dashboard layout and a backend API example.

### What a theme does

A theme supplies the presentation of a website: its document structure, visible navigation, styling and placement of assigned content. A module can supply application features and data while the theme provides the surrounding design. Content assigned from themes, modules or plugins appears through the dynamic loader.

### Requirements and testing environment

You need a working LifeTechOCMS installation, access to its administration panel, and basic knowledge of HTML. CSS changes appearance; JavaScript adds browser behaviour; PHP runs on the server and lets a theme call LifeTechOCMS functions.

Write theme content in the LifeTechOCMS code editor, or edit the corresponding files in your local LifeTechOCMS installation. Open the theme through LifeTechOCMS when testing: opening an HTML file directly on your computer will not run its PHP helpers.

### How to use this guide

Follow sections [Accessing Themes Development](#accessing-themes-development) to [Create Views Pages and Menus](#create-views-pages-and-menus) to build your first theme.

Section [Load Menus for the Current Users Roles](#load-menus-for-the-current-users-roles) adds role-based menus and section [Understand the Default Layout and Custom Layouts](#understand-the-default-layout-and-custom-layouts) explains alternative layouts. Sections [Import Content and Load Content](#import-content-and-load-content) to [Connect Theme Views to Backend APIs](#connect-theme-views-to-backend-apis) cover imports, helpers and APIs; sections [Edit Theme Package](#edit-theme-package) to [Security and Management Permissions](#security-and-management-permissions) cover management actions. Use a section title such as 'How does it work' when recording an observation.

The snippets use ThemeStarter consistently. ThemeNova and ThemeStarter follow the same confirmed package and content naming conventions; this guide does not require ThemeNova to be installed. The CSS is a small teaching example, and the loader can work with your chosen styling framework.

### Key terminology

| **Keyword** | **Meaning** | **Small example** |
| --- | --- | --- |
| Theme | A package that defines the appearance and presentation of pages | ThemeStarter |
| Package | A named collection of files and settings managed by LifeTechOCMS | A theme package or a module package |
| Content | An individual registered item inside a package | Header.html or Style.css |
| Resource type | The kind of theme content you are creating | Component, View, Layout or Asset |
| Component | A reusable part of a page | A header used on Home and About |
| View | The main interface displayed inside a page | The text and buttons on Home |
| Layout | A wrapper that arranges components around a view | A dashboard with a sidebar |
| Asset | Supporting code or resources for the design | A stylesheet or JavaScript file |
| Page | A configured destination that visitors can open | The Home page |
| Route | The public path used to reach a page or API | /ThemeStarter/Home |
| Additional path | A subfolder inside the selected resource folder | /css places an asset under Assets/css |
| Import | Load another registered content item into the current content | ltImport('ThemeStarter', 'Style.css') |
| Theme default component | A component selected for the theme's default page composition | A shared header with Is Theme Default set to Yes |
| Default theme | The theme selected as the site's main theme | ThemeStarter selected as the site default |
| Publish | Make a theme or assigned content available for use | Make a theme available to visitors |
| API | A backend address that the browser can request for data or actions | An endpoint returning blog posts |
| Module | A package supplying application features and backend logic | MdBlog supplies blog functionality |

**A view is not a page route.** Home.html is a content filename; /ThemeStarter/Home is the address visitors open. When you create content as a View resource, LifeTechOCMS creates its page and menu automatically.

**A layout is also content.** Components, views, layouts and assets are all managed as content items. Their resource types tell LifeTechOCMS what kind of content they are and where their files belong.

[Back to contents](#contents)

## Accessing Themes Development

### Open the theme management area

1. Sign in to the LifeTechOCMS backend with a role permitted to manage packages.
1. Open **Packages**.
1. Select **Themes Development**.

### Understand the theme list and actions

The theme list is where you create, install and manage theme packages. Open a package to work on the individual content items inside it.

| **Action** | **Purpose** | **Example** |
| --- | --- | --- |
| Add Theme Package | Start a new theme | Create ThemeStarter |
| Install Theme | Import an exported theme ZIP | Install ThemeStarter.zip |
| Edit Theme Package | Change package information | Update the description or version |
| Preview | Inspect the design | Check Home before publishing |
| Publish | Make the theme available for frontend use | Publish the completed theme |
| Publish Theme to Page | Apply the design to selected pages | Give a landing page a different theme |
| Set Theme as Default | Select the site's main theme | Use ThemeStarter as the main design |
| Export Theme | Download a portable package | Move the theme to another installation |
| Delete Theme | Remove a package | Remove an unused theme after checks |

Button labels and icon placement can vary by installed version. Use the matching action in your panel.      



![image](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/6f8b73070fc43c63ca1ec01cabb6e80e.png)

**Expected result:** you can locate a theme package and distinguish package actions from actions on its content.

[Back to contents](#contents)

## Theme Development Conventions

Conventions give developers a consistent way to name packages and content. The four rules below cover package names, content names, theme versions and release tags. We can extend this section as more conventions are agreed.

### 1. Theme package names use PascalCase

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

### 2. File names and content names use PascalCase

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

### 3. Theme versions use v followed by three numeric parts

Use a version such as v1.0.0 for your theme. Keep the leading v and all three numeric parts. This is the convention for new theme releases in this guide; historical versions in supplied packages are shown as recorded.

| **Part** | **Meaning** | **Example** |
| --- | --- | --- |
| v | Version prefix | v1.0.0 |
| First number | Major version | v2.0.0 for a major release |
| Second number | Minor version | v1.1.0 for a minor release |
| Third number | Patch version | v1.0.1 for a patch release |

For example, ThemeStarter begins at v1.0.0. Record the release version consistently in the theme package information and its package.json metadata using the supported platform workflow.

### 4. GitHub release tags use the same three part version

Use GitHub tags such as v1.0.0, v1.0.1 and v1.1.0. The release tag must match the theme version being released. A tag identifies a particular source revision so developers can download and discuss the same release.

For a theme whose package version is v1.0.0, the matching release tag is v1.0.0. Avoid shortened tags such as v1.0 for this convention. Update the package version before preparing its matching release tag.

[Back to contents](#contents)

## Add Theme Package

1. Sign in to the backend.
1. Open **Packages > Themes Development**.
1. Choose **Create Theme** or **Add Theme Package**.
1. Enter ThemeStarter as the package name. Use no spaces.
1. Enter a description such as A beginner theme with Home and About pages.
1. Enter a package version such as 1.0.0 and submit the form.
1. Open ThemeStarter to manage its content.

Creating the theme from the panel generates its package metadata and necessary folders. Use these generated files as your starting point. The exact button labels may vary between installed versions.

**What you have now:** a theme package ready for content. A package without page content is not yet a complete website design.

### Understand package metadata and dependencies

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

[Back to contents](#contents)

## Theme Content and the Four Resource Types

In LifeTechOCMS, **content** is an individual item you create and register inside a package. A header, a Home interface, a dashboard wrapper and a stylesheet are all content. You select a **resource type** to describe the item's job and determine its folder.

### Component content

A component is a reusable part of the design. For example, Header.html displays navigation and Footer.html displays the footer. The same component can appear on several pages, so one edit can update a shared part of the design.

Component files belong in Components/. A simple component might contain:

```html
<header>
	<p>Welcome to our website</p>
</header>
```

Components marked Is Theme Default form the theme's default page composition. ContentLoadBody is a component whose job is to load the content assigned to each page.

### View content

A view is the interface displayed for a page, such as Home, About or a book catalogue. View files belong in Views/.

```html
<section>
	<h1>About us</h1>
	<p>Learn about our organisation.</p>
</section>
```

When you create content with the View resource type, LifeTechOCMS automatically creates its **content record, page and menu**, and assigns the view to its page and menu. The menu leads visitors to that page; the dynamic content loader displays the assigned view there. You do not need to create and connect these records manually for this workflow.

### Layout content

A layout arranges reusable components around dynamic content. Layout files belong in Layouts/. For example, an administration layout can place a sidebar beside the current view:

```html
<div>
	<?php ltImport('ThemeStarter', 'DashboardSidebar.html'); ?>
	<?php dddm::loadDynamicContent(); ?>
</div>
```

The wrapper and styling are your choice. A separate layout is optional when default components already provide the required design. Use another layout when views need a different arrangement.

### Asset content

An asset supplies supporting styles, scripts or other design resources. Asset files belong in Assets/, often in subfolders such as css/ and js/.

```css
.page-title {
		color: #155e75;
}
```

This stylesheet is asset content. An HTML element with class page-title can use its styling once the stylesheet is loaded. Assets can be imported as registered content or loaded through an appropriate direct file URL, as explained later.

### How these types work together

| **Item** | **Resource type** | **Its job** |
| --- | --- | --- |
| Header.html | Component | Shared navigation |
| Home.html | View | Home page interface |
| DashboardLayout.html | Layout | Alternative arrangement around a view |
| Style.css | Asset | Colours, spacing and other styles |

A resource type describes the content's purpose; it is different from its extension. Both a component and a view can be .html files. Choose the resource type according to the item's job.

![image](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/92c1d75ea0ee501dbb9f24387ff8353b.png)

[Back to contents](#contents)

## Understand Theme Folders and Subfolders

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

### How subfolders work

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

### What ddm and Export mean for a beginner

**DDM means Data Defacing Model.** The supplied themes have .lifetech marker files named after content and its type, such as ContentLoadBody.Component.lifetech. These markers are empty in the supplied exports. Your actual interface code belongs in the resource files, not in these markers.

Export/content.json contains content registrations. Export/page.json contains page and route records. Export/menu.json contains menu records. Both supplied themes also have pageContent.json and table.json, currently containing empty arrays. Let LifeTechOCMS manage these records through its panel and export process.

[Back to contents](#contents)

## Add New Theme Content

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

### Understand the content form

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

After creating an item, use its **Code Editor** action to enter the code in sections [Build the Shared Theme Components](#build-the-shared-theme-components) to [Create Views Pages and Menus](#create-views-pages-and-menus). If you create files locally instead, use Sync Files to register them, as explained in section [Sync Files](#sync-files).

**What you have now:** eight registered items. Sections '**Build the Shared Theme Components**' to '**Create Views Pages and Menus**' give each item a specific job.  

![image](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/c144949b1140ee0331f7c310c1030806.png)

[Back to contents](#contents)

## Sync Files

Sync Files registers new files created locally in the theme's resource folders as content in the database. It is useful when you write files in a local editor or when an AI tool generates new theme files for you.

### Which folders are scanned

Place files inside the appropriate resource folder of the theme package. Sync Files applies to the Components, Views, Assets and Layouts folders.

| **Folder** | **Example new file** | **Content resource type** |
| --- | --- | --- |
| Components/ | Announcement.html | Component |
| Views/ | AboutUs.html | View |
| Assets/ | css/ExtraStyle.css | Asset |
| Layouts/ | LandingLayout.html | Layout |

Use the confirmed PascalCase naming conventions for developer-created content names. Choose the folder according to the content's job, not just its extension: both a view and a component can be HTML files.

### Register a locally created view

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

### Use Sync Files with AI generated code

Ask the AI tool to generate files using your theme's package name, correct resource folders and PascalCase content names. Place the generated files into the target installation, review their code, and run Sync Files. Inspect the registered content and preview the relevant pages.

A file generated in another directory or on another computer must first be copied into the target theme's resource folders. Sync Files registers files present in those folders; it does not retrieve files from an AI conversation.

### Understand syncing versus editing

| **Action** | **When to use it** |
| --- | --- |
| Add Content | Create and register content through the backend |
| Sync Files | Register new files placed locally in the resource folders |
| Code Editor or local editing | Change code in an existing registered file |
| Upload | Update an existing content item with an edited file |

Saving an existing registered file changes its code. Creating a new file adds a file to disk; Sync Files supplies its content registration. After syncing, review publication, access and default component settings separately.

[Back to contents](#contents)

## Editing Theme Content Code

### Use the built in code editor

1. Open ThemeStarter from the theme list.
1. Find the registered content item, such as Header.html.
1. Select its **Code Editor** action, usually shown with a code symbol.
1. Enter or update its code and save.
1. Refresh Preview to check the result.

Start with the content created in section [Add New Theme Content](#add-new-theme-content). Sections [Build the Shared Theme Components](#build-the-shared-theme-components) to  [Create Views Pages and Menus](#create-views-pages-and-menus) provide the starter code.

### Work with a local code editor

For a local installation, open the corresponding registered file in VS Code, PHPStorm or another editor. In the updated structure, examples include:

packages/themes/ThemeStarter/Components/Header.html

packages/themes/ThemeStarter/Views/Home.html

packages/themes/ThemeStarter/Assets/css/Style.css

Save the file and refresh the page through LifeTechOCMS. You are editing the file used by that local installation, so you do not need to upload the same edit back to it. Changes made to a separate computer or checkout must still be transferred to the target installation.

The previous online guide used a single contents folder. Use the resource folders in the updated structure. Create/register a content item through the panel before expecting a new local file to appear in content management.

### Check your saved changes

Change a paragraph in Home.html, save it and open the generated Home page. The new text should appear. If PHP appears as text, check that you opened the page through LifeTechOCMS rather than opening the file directly.

[Back to contents](#contents)

## Edit or Update Existing Theme Content

### Edit content settings

Use the content row's **Edit** action to change its description or other registered settings. Review the resource type and additional path before saving: these identify where the item belongs.

For example, correcting Header.html's description does not require creating a second Header content record.

### Upload an updated content file

1. Open the theme's content list.
1. Locate the existing content item.
1. Select its **Upload** action.
1. Choose the updated file for that item and complete the upload.
1. Preview a page that uses the content.

Use Code Editor when writing code in the panel; use Upload when replacing it with an edited file. Edit changes the record's settings.

### Check references after a change

If you change a content name or path, verify imports, direct asset links and relevant page assignments. A direct URL contains the folders and filename, so a moved asset requires an updated URL. Registered imports must still identify the correct content item.

**Expected result:** the existing registered item contains the update and pages that use it continue to work.

[Back to contents](#contents)

## Build the Shared Theme Components

### Add the stylesheet

Open Style.css and enter:

```css
:root {
     --brand: #155e75;
     --background: #f5f7fa;
     --text: #17212b;
 }
 
 * { box-sizing: border-box; }
 body {
     margin: 0;
     font-family: Arial, sans-serif;
     color: var(--text);
     background: var(--background);
 }
 .container {
     max-width: 960px;
     margin: 0 auto;
     padding: 24px;
 }
 .site-header, .site-footer {
     background: white;
     padding: 16px 24px;
 }
 .site-header a {
     color: var(--brand);
     margin-right: 16px;
 }
 .card {
     padding: 24px;
     background: white;
     border-radius: 12px;
 }
 button {
     padding: 10px 16px;
     background: var(--brand);
     color: white;
     border: 0;
     border-radius: 6px;
     cursor: pointer;
 }
 .dashboard {
     display: flex;
     min-height: 70vh;
 }
 .dashboard aside {
     width: 220px;
     padding: 24px;
     background: #e2e8f0;
 }
 .dashboard main { flex: 1; min-width: 0; }
 @media (max-width: 640px) {
     .dashboard { display: block; }
     .dashboard aside { width: auto; }
 }
```

A **class** is a reusable CSS selector. An element with class="card" receives the .card styles. A **CSS variable**, such as --brand, gives you one place to change a shared design value.

This asset contains plain CSS, so its importer will be placed inside a [[style]] element in this section. This matches the stylesheet loading pattern in ThemeBlog.

### Create the document opening component

Open TopHeader.html and enter:

```html
<!DOCTYPE html>
 <html lang="en">
 <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title><?= htmlspecialchars(ltSiteName(), ENT_QUOTES, 'UTF-8') ?></title>
     <style>
         <?php ltImport('ThemeStarter', 'Style.css'); ?>
     </style>
 </head>
 <body>
```

This component opens the HTML document. viewport makes the page scale correctly on mobile devices. It deliberately leaves body and html open; Footer will close them after the view has been rendered.

### Understand ltSiteName

ltSiteName() returns the configured site name. It allows a visitor-facing title to follow the site's settings instead of a name hardcoded into the theme.

**<?= ... ?>** is PHP's short echo syntax: it outputs the expression's value into the HTML. htmlspecialchars() is a PHP function that safely displays text in HTML; it is not a LifeTechOCMS-specific function.

### Understand ltImport

```php
<?php ltImport('ThemeStarter', 'Style.css'); ?>
```

ltImport() loads registered content. In the supplied themes, it accepts a package name and a content filename. Here, ThemeStarter identifies the package and Style.css identifies the asset.

Notice that the call uses Style.css, not **Assets/css/Style.css**. The content registration records its resource type and additional path. Use exact spelling and capitalization, and choose distinct filenames within a package.

### Create the visible header and navigation

Open Header.html and enter:

```html
<header class="site-header">
     <strong><?= htmlspecialchars(ltSiteName(), ENT_QUOTES, 'UTF-8') ?></strong>
     <nav aria-label="Main navigation">
         <a href="<?= htmlspecialchars(
             rtrim(ltSiteUrl(), '/') . '/ThemeStarter/Home',
             ENT_QUOTES, 'UTF-8'
         ) ?>">Home</a>
         <a href="<?= htmlspecialchars(
             rtrim(ltSiteUrl(), '/') . '/ThemeStarter/About',
             ENT_QUOTES, 'UTF-8'
         ) ?>">About</a>
     </nav>
 </header>
```

TopHeader provides document metadata. Header provides what visitors see at the top of the page. Giving these two components separate jobs makes them easier to reuse.

ltSiteUrl() supplies the base used for links in the provided themes. rtrim(..., '/') removes an ending slash before adding the route. Check the automatically generated Home and About routes in section [Create Views Pages and Menus](#create-views-pages-and-menus) before using them in your links.

An href is the destination of a link**.** It should refer to the configured page route, not the view's filesystem path. Do not link visitors directly to **Views/Home.html**.

### Add JavaScript and the footer

Open Script.js and enter this plain JavaScript:

```js
const welcomeButton = document.getElementById('welcomeButton');
 const welcomeMessage = document.getElementById('welcomeMessage');
 
 if (welcomeButton && welcomeMessage) {
     welcomeButton.addEventListener('click', () => {
         welcomeMessage.textContent = 'Your LifeTechOCMS theme is working!';
     });
 }
```

The condition checks that both elements exist. This lets the same script run on About without failing because the Home button is absent. textContent displays plain text in an element.

Open Footer.html and enter:

```html
<footer class="site-footer">
     <small>
         &copy; <?= date('Y') ?>
         <?= htmlspecialchars(ltSiteName(), ENT_QUOTES, 'UTF-8') ?>
     </small>
 </footer>
 <script>
     <?php ltImport('ThemeStarter', 'Script.js'); ?>
 </script>
 </body>
 </html>
```

The script is imported after the dynamic view, so the Home elements already exist when JavaScript looks for them. date('Y') is a PHP function that supplies the current year.

### Know whether your asset already contains tags

Our Script.js contains JavaScript only, so Footer supplies [[script]] tags. ThemeBlog's supplied Script.js already contains [[script]] tags and PHP helper calls, so that asset is imported directly instead:

```php
<?php ltImport('ThemeBlog', 'Script.js'); ?>
```

Do not wrap an asset that already contains [[script]] tags inside another [[script]] element. Similarly, our stylesheet contains CSS only, so TopHeader provides [[style]] tags.

When an asset contains PHP, load it through LifeTechOCMS's registered content processing. A direct request for an ordinary .js file does not normally execute PHP embedded in it.

[Back to contents](#contents)

## Add the Compulsory Dynamic Content Loader

Your theme provides the page design, including its header, navigation and footer. Each page also needs a place to display the content assigned to it.

The **dynamic content loader** provides that place. It loads and displays any **theme, module or plugin content assigned to the current page**, including multiple assigned content items.

### Add the loader to your theme

Create or open the ContentLoadBody.html component and add:

```php
<?php dddm::loadDynamicContent(); ?>
```

Set **Is Theme Default** to **Yes** so this component forms part of the theme's default page composition. Position it where assigned content should appear, usually between the header and footer.

The function call is the required instruction. No particular HTML wrapper, CSS class or styling framework is required. You can leave it on its own or wrap it in any HTML and classes that suit your design:

```html
<section class="my-page-content">
	<?php dddm::loadDynamicContent(); ?>
</section>
```

my-page-content is only an example chosen by the developer. The wrapper controls presentation; the function loads assigned content.

### How does it work

| **Page** | **Assigned content** | **What the loader displays** |
| --- | --- | --- |
| Home | Home view from a theme | The Home interface |
| Book Catalogue | Book listing content from a module | The book listing interface |
| A page using plugin content | Displayable content assigned from a plugin | That plugin's assigned content |

You do not rewrite the loader for each page. **The page's assignments determine what appears; the loader's position determines where it appears.**

### Why is it necessary

Assigning content to a page tells LifeTechOCMS what to display. The loader gives the theme an insertion point for that content. Without the loader in the resulting page composition, the shared header and footer may appear while the assigned page content is missing.

For our beginner theme, arrange TopHeader, Header, ContentLoadBody and Footer in that order. When Home is opened, the loader displays the assigned Home view. When a module page is opened, the same loader displays its assigned module content.

### How is this different from ltImport

ltImport() loads a specific registered item that you name:

```php
<?php ltImport('ThemeStarter', 'Header.html'); ?>
```

dddm::loadDynamicContent() loads the content assigned to the current page:

```php
<?php dddm::loadDynamicContent(); ?>
```

Use an import for a specific reusable item. Keep the dynamic loader where page-assigned theme, module or plugin content should appear.

### What if the page uses a separate layout

A separate layout also needs a dynamic insertion point. Place the same function call inside that layout where assigned content should appear. The default composition provides the loader through ContentLoadBody; an alternative layout can provide it directly. Check that the resulting composition does not load the same dynamic content twice.

[Back to contents](#contents)

## Create Views Pages and Menus

### Write the Home and About views

Open Home.html and enter:

```html
<section class="card">
     <h1>Welcome to our website</h1>
     <p>This Home view is displayed inside the theme's dynamic content area.</p>
     <button id="welcomeButton" type="button">Show welcome message</button>
     <p id="welcomeMessage" role="status"></p>
 </section>
```

Open About.html and enter:

```html
<section class="card">
     <h1>About us</h1>
     <p>We built this website with LifeTechOCMS.</p>
     <p>This view shares the same header, stylesheet and footer as Home.</p>
 </section>
```

A view normally contains the interface for the dynamic area. Do not add another complete html, head and body document to these views, because the shared components already provide that wrapper.

An **id** identifies an individual HTML element. JavaScript will use welcomeButton and welcomeMessage to find the Home page elements. About does not need these elements.

When you create content with the **View** resource type, LifeTechOCMS automatically creates the content record, a page and a menu for that view. It also assigns the view to the page and menu.

You do not need to manually create a Home page and then attach Home.html to it as separate steps in this workflow.

### What happens when you create a view

For the Home.html view created earlier:

1. LifeTechOCMS registers Home.html as View content.
1. It creates the page for that content.
1. It creates the associated menu entry.
1. It assigns the content to its page and menu.
1. The menu provides navigation to the page.
1. When the page opens, ContentLoadBody's dynamic loader displays the content assigned to that page.

The same process applies when you create About.html as View content.

### Check the generated route before writing links

Open the generated page or menu settings and check its route. The beginner examples use **/ThemeStarter/Home** and **/ThemeStarter/About**. Use the actual generated route in your installation, including its capitalization, when writing navigation links.

For example, if Home's route is **/ThemeStarter/Home**, the Home link in Header should use that route. You can use the generated menu navigation or build your own navigation using the generated page addresses.

### Preview the generated pages

Open each generated page through its menu or the available Preview action. Check its theme settings, intended access permissions and publication status. Confirm that the shared components are in the right order and the view appears at the dynamic loader's position.

Automatic creation establishes the page, content and menu relationships. You can still review and adjust their settings through the backend when your design needs it.

### Review publication and access settings

Automatic creation connects the records. Review who can visit the page and whether its content is published for those visitors. A published theme does not by itself give an anonymous visitor access to a restricted page.

**Expected result:** Home and About each have their own page and menu, and the loader displays the appropriate assigned view.

[Back to contents](#contents)

## Load Menus for the Current Users Roles

LifeTechOCMS stores navigation menus in the database. Theme developers can request the menus permitted for the current user, then display them with their own navigation design. Use the general endpoint for menus across packages, or add packageName to filter by a named package:

**GET /menus/is-navigation**

**GET /menus/is-navigation?packageName=ThemeStarter**

### Understand token and session identification

The request can carry a Bearer token or use an existing login session. AppCore processes the available authentication before the menu method runs. The method reads role IDs from LtSession::get('ltUrid'). If no role value is available, it uses the Anonymous role. Multiple role IDs are separated and trimmed before the role filtering is applied.

A request without a Bearer token is not automatically an Anonymous request. A logged-in user may already have a session. The backend determines role permissions. Do not send role IDs. Omit packageName to obtain all permitted navigation menus, or supply it to restrict the result to that package; the role checks still apply.

### Prepare the API and site addresses

Place these declarations inside a theme content file processed as PHP, before the menu functions:

```js
<script>
 const BASE_URL = <?= json_encode(ApiTokenDetails::backEndBaseUrl()); ?>;
 const siteHostAddress = <?= json_encode(ltSiteHostAddress()); ?>;
 </script>
```

| **Variable** | **Purpose** |
| --- | --- |
| BASE_URL | Backend API base address used to request menus |
| siteHostAddress | Site address used to build internal navigation links |
| LW_TOKEN | Current user's token, when already supplied by your authentication code |

json_encode() converts PHP values into JavaScript string values safely. The examples below are JavaScript: put them inside a script element after these declarations, or in your loaded JavaScript content. Declare shared constants only once.

### Load menu data without HTML or CSS

The loader requests the data and returns the menu array. It does not produce markup or apply styling.

```js
async function loadNavigationMenus(token = '', packageName = '') {
     const headers = { Accept: 'application/json' };

     if (token) {
         headers.Authorization = `Bearer ${token}`;
     }

     const url = new URL(
         `${BASE_URL.replace(/\/+$/, '')}/menus/is-navigation`
     );
     if (packageName) {
         url.searchParams.set('packageName', packageName);
     }

     const response = await fetch(url.href, { method: 'GET', headers });

     if (!response.ok) {
         throw new Error(`Menu request failed: ${response.status}`);
     }

     const result = await response.json();

     if (result.responseCategory !== 200) {
         throw new Error(
             result.responseResult || 'Unable to load navigation menus.'
         );
     }

     if (!Array.isArray(result.responseData)) {
         throw new Error('Invalid menu response.');
     }

     return result.responseData;
}
```

| **Syntax** | **Explanation** |
| --- | --- |
| async / await | Wait for the HTTP request and JSON parsing |
| token = '' | Make the Bearer token optional |
| packageName = '' | Make the package filter optional |
| url.searchParams.set() | Add and encode the packageName query parameter |
| Authorization | Carry the token in the format Bearer followed by the token |
| fetch() | Send the HTTP request |
| response.ok | Check HTTP success |
| responseCategory | Check application success; 200 indicates success |
| responseData | Return the menu records, including nested children |

No explicit credentials option is used. For a same-origin request, fetch sends eligible session cookies by default. An API on another origin needs a suitable authentication arrangement; the loader does not assume that its session cookies will accompany the request.

### Inspect data before rendering

Start with a console example using the existing session:

```js
async function inspectMenus() {
     try {
         const menus = await loadNavigationMenus();
         console.log(menus);
     } catch (error) {
         console.error('Menu Load Error:', error.message);
     }
}

inspectMenus();
```

If your authentication code already provides LW_TOKEN, change the call inside the function to:

```js
const menus = await loadNavigationMenus(LW_TOKEN);
```

To filter menus by package, use one of these calls inside your async function:

```js
// Existing session, restricted to ThemeStarter menus.
const menus = await loadNavigationMenus('', 'ThemeStarter');

// Bearer token, restricted to ThemeStarter menus.
const menus = await loadNavigationMenus(LW_TOKEN, 'ThemeStarter');
```

Both requests retain role-based filtering. Without the second argument, the loader uses /menus/is-navigation and requests permitted navigation menus across packages.

An invalid or expired token can cause an authentication error. Do not silently retry as a different user or as Anonymous.

### Understand the response fields

The supplied response includes this parent menu and its child:

```json
{
   "responseResult": "Data Fetched",
   "responseCode": 2009,
   "responseCategory": 200,
   "responseData": [
     {
       "ltId": "178791436425882",
       "menuName": "ThemeBlog",
       "slug": null,
       "routePath": "#",
       "target": "self",
       "isExternal": 0,
       "parentMenuId": null,
       "menuLevel": 1,
       "icon": null,
       "children": [
         {
           "ltId": "178791826124184",
           "menuName": "Blog.html",
           "slug": null,
           "routePath": "/ThemeBlog/Blog",
           "target": "_blank",
           "isExternal": 0,
           "parentMenuId": "178791436425882",
           "menuLevel": 2,
           "icon": ""
         }
       ]
     }
   ]
}
```

| **Field** | **Meaning** |
| --- | --- |
| ltId | Unique menu identifier |
| menuName | Label displayed in the navigation |
| routePath | Destination; # can act as a parent placeholder |
| target | Link target; map self to _self, while _blank opens a new tab |
| isExternal | Whether the destination is external |
| parentMenuId | Parent identifier; null indicates a top-level item |
| menuLevel | Depth of the menu in its hierarchy |
| children | Nested records, when present |
| icon | Optional icon information for a styled renderer |
| slug | Additional API field; null in this example |

The loader returns responseData, not the entire response envelope. The renderer uses the nested children directly rather than rebuilding the hierarchy from parentMenuId.

### Display menus with plain HTML

Add this container to the theme's navigation component:

```html
<nav id="mainNav" aria-label="Main navigation"></nav>
```

Use a separate renderer to create links and nested lists. This example needs no CSS framework or icon library.

```js
function getMenuUrl(item) {
     const route = item.routePath ?? '#';
     if (route === '#') return '#';

     let url;
     if (Number(item.isExternal) === 1) {
         url = new URL(route);
     } else {
         const base = `${siteHostAddress.replace(/\/+$/, '')}/`;
         url = new URL(route.replace(/^\/+/, ''), base);
     }

     if (!['http:', 'https:'].includes(url.protocol)) {
         throw new Error('Unsupported menu URL.');
     }
     return url.href;
}

function buildMenuList(items) {
     const list = document.createElement('ul');

     for (const item of items) {
         const listItem = document.createElement('li');
         const link = document.createElement('a');
         link.textContent = item.menuName || '';
         link.href = getMenuUrl(item);

         const target = item.target || 'self';
         link.target = target === 'self' ? '_self' : target;
         if (link.target === '_blank') {
             link.rel = 'noopener noreferrer';
         }

         listItem.append(link);
         if (Array.isArray(item.children) && item.children.length) {
             listItem.append(buildMenuList(item.children));
         }
         list.append(listItem);
     }
     return list;
}

function renderNavigation(menus) {
     const nav = document.getElementById('mainNav');
     if (nav) nav.replaceChildren(buildMenuList(menus));
}
```

textContent displays menu labels as text. Internal routes are appended to the site address, preserving a site installation subfolder. External entries use their complete HTTP or HTTPS URL. This beginner example limits destinations to those protocols.

buildMenuList() calls itself for each set of children. This is recursion: the same function renders the parent list, child lists and deeper levels. All lists are visible; add dropdown interaction separately if your design needs it.

### Connect loading and rendering

Place this after the navigation container and the functions above:

```js
async function initialiseNavigation(token = '', packageName = '') {
     try {
         const menus = await loadNavigationMenus(token, packageName);
         renderNavigation(menus);
     } catch (error) {
         console.error('Menu Load Error:', error.message);
     }
}

// Use the existing session; Anonymous roles apply if none are available.
initialiseNavigation();
```

When LW_TOKEN is already available, use initialiseNavigation(LW_TOKEN) instead of the final call. To filter the displayed navigation, use initialiseNavigation('', 'ThemeStarter') with an existing session, or initialiseNavigation(LW_TOKEN, 'ThemeStarter') with a token. Choose one initialization call. With the supplied data, ThemeBlog appears as the parent and Blog.html appears beneath it. Blog opens the configured page in a new tab.

Optional developer-defined links can be added before rendering:

```js
const navLinks = [
     { menuName: 'Home', routePath: '', target: 'self', isExternal: 0 },
     ...menus,
     { menuName: 'Documentation', routePath: '/Docs', isExternal: 0 }
];
renderNavigation(navLinks);
```

Use this inside initialiseNavigation after obtaining menus, and replace its existing render call. Only add routes that exist on your site. An empty Home route resolves to the site base. A missing route remains # because getMenuUrl uses the nullish coalescing operator (??).

### Optional PHP rendering

PHP can render menus with foreach if the role-filtered data is obtained on the server before the page is rendered. PHP cannot loop over data fetched later by browser JavaScript. A server-side API request must carry the appropriate user identity; it does not automatically inherit the browser's session.

The following rendering-only example assumes $menuResponse already holds the decoded response as a PHP array. The server-side loading call must use your platform's supported helper or service.

```html
<?php
$menus = $menuResponse['responseData'] ?? [];

$renderMenuLabels = function (array $items) use (&$renderMenuLabels): void {
     echo '<ul>';
     foreach ($items as $item) {
         echo '<li><span>';
         echo htmlspecialchars(
             $item['menuName'] ?? '', ENT_QUOTES, 'UTF-8'
         );
         echo '</span>';

         if (!empty($item['children']) && is_array($item['children'])) {
             $renderMenuLabels($item['children']);
         }
         echo '</li>';
     }
     echo '</ul>';
};
?>

<nav aria-label="Main navigation">
     <?php $renderMenuLabels($menus); ?>
</nav>
```

This example demonstrates escaped labels and recursive PHP loops. It does not implement navigation links or a menu-fetching helper. Use the complete JavaScript example for navigation until your server-side integration is available.

### Test roles and distinguish the two loaders

Test a visitor with no login, a user with an existing session, and a user sending a valid Bearer token. Check nested links, targets and the page destinations. Menu visibility does not replace page or API authorization.

| **Loader** | **Responsibility** |
| --- | --- |
| /menus/is-navigation | Return navigation menus permitted for the current user's roles across packages |
| /menus/is-navigation?packageName=ThemeStarter | Return permitted navigation menus filtered to ThemeStarter |
| dddm::loadDynamicContent() | Display theme, module or plugin content assigned to the current page |

A menu directs the visitor to a page. The dynamic content loader displays that page's assigned content. Developers can add their own classes, icons and navigation interactions without changing the data loader.

**Expected result:** the theme loads role-filtered menu data and displays it using a separate renderer.

[Back to contents](#contents)

## Understand the Default Layout and Custom Layouts

LifeTechOCMS offers two ways to arrange a page's design: default components that together form the theme's default layout, and a separate custom Layout content item assigned to selected pages.

### Default components form the default layout

Component content has an optional is_theme_default field with Yes or No. All components set to Yes automatically form the theme's default layout for new pages. You do not need to write a separate Layout content file for this default composition.

| **Component** | **is_theme_default** | **Purpose** |
| --- | --- | --- |
| TopHeader.html | Yes | Open the document and load shared styles |
| Header.html | Yes | Display the header and navigation |
| ContentLoadBody.html | Yes | Load the content assigned to the page |
| Footer.html | Yes | Display the footer and close the document |
| Announcement.html | No | Use only on pages that need it |

Arrange the default components in the intended display order: document opening, header, content loader, then footer. The panel may label the field Is Theme Default; exported content records use isThemeDefault.

### 15.2 Unpublish individual components on a page

Default components are published as independent content assignments on each new page. They are not statically combined inside one layout file. The owner can later unpublish a particular component on a particular page without changing its publication on other pages.

For example, a campaign landing page may unpublish Header.html while Home and About keep it. This changes the landing page's composition without editing a shared layout file.

Keep the dynamic content loader available wherever assigned page content should appear. Also preserve the required document opening and closing, and any files that supply the page's styles or scripts.

### Create custom Layout content

A custom layout is a content item created with the Layout resource type. The developer writes its structure and imports the components it needs with ltImport(). Use it when selected pages need a different arrangement, such as a member dashboard with a sidebar.

Create these additional content items in ThemeStarter:

| **Content name** | **Resource type** | **Additional path** | **Is Theme Default** |
| --- | --- | --- | --- |
| MemberLayout.html | Layout | / | No |
| MemberSidebar.html | Component | / | No |
| MemberHeader.html | Component | / | No |
| MemberDashboard.html | View | / | No |

MemberSidebar.html supplies the navigation content inside the layout's aside element:

```html
<h2>Member area</h2>
<nav aria-label="Member navigation">
     <a href="<?= htmlspecialchars(
         rtrim(ltSiteUrl(), '/') . '/ThemeStarter/MemberDashboard',
         ENT_QUOTES, 'UTF-8'
     ) ?>">Dashboard</a>
</nav>
```

Use the actual generated route for MemberDashboard. You can replace this teaching link with the role-based menu renderer in section [Load menu data without HTML or CSS](#load-menu-data-without-html-or-css).

MemberHeader.html supplies the dashboard heading inside the layout's header element:

```html
<h1>Member dashboard</h1>
```

MemberDashboard.html supplies the page's view content:

```html
<section class="card">
     <h2>Your overview</h2>
     <p>This content appears inside the member layout.</p>
</section>
```

Open MemberLayout.html and enter:

```html
<?php ltImport('ThemeStarter', 'TopHeader.html'); ?>

<div class="member-layout">
     <aside class="member-sidebar">
         <?php ltImport('ThemeStarter', 'MemberSidebar.html'); ?>
     </aside>

     <div class="member-content">
         <header class="member-header">
             <?php ltImport('ThemeStarter', 'MemberHeader.html'); ?>
         </header>

         <main class="member-body">
             <?php dddm::loadDynamicContent(); ?>
         </main>
     </div>
</div>

<?php ltImport('ThemeStarter', 'Footer.html'); ?>
```

TopHeader.html and Footer.html are the registered components created earlier in this guide. The custom layout imports them explicitly. MemberSidebar.html and MemberHeader.html supply its member-specific navigation and heading.

The dynamic loader displays whichever content is assigned to the current page. The same layout can serve several member pages. It does not import ContentLoadBody.html, because the layout already calls the dynamic loader directly.

### Add your own layout styling

The HTML class names above are examples, not required framework classes. Add CSS to the registered Style.css content if you want a sidebar arrangement:

```css
.member-layout { display: flex; min-height: 70vh; }
.member-sidebar { width: 220px; padding: 24px; background: #e2e8f0; }
.member-content { flex: 1; min-width: 0; }
.member-header, .member-body { padding: 24px; }

@media (max-width: 640px) {
     .member-layout { display: block; }
     .member-sidebar { width: auto; }
}
```

Developers can use their own CSS or styling framework while keeping the imports and dynamic loader in the appropriate positions.

### Assign pages to the custom layout

1. Create and register MemberLayout.html as Layout content.
1. Open the layout assignment controls in the theme development backend.
1. Assign MemberDashboard and the other intended member pages to MemberLayout.html.
1. Review each page's content publication and access roles.
1. Preview the pages and confirm the document, header, sidebar and assigned content appear once.

Public pages can continue using the theme's default components. For pages assigned to the custom layout, inspect the resulting composition so imported TopHeader and Footer are not duplicated by separate page assignments, and the content loader runs once.

Components imported inside a custom layout are controlled by its code. Unpublishing a separate page assignment does not remove an explicit ltImport() call from that layout. To change those imported components, edit the layout's imports or the imported content.

### Compare the two approaches

| **Default layout from components** | **Custom Layout content** |
| --- | --- |
| Components marked is_theme_default = Yes form the composition | A Layout content file defines the composition |
| Automatically included for new pages | Assigned to the pages that need it |
| Individual component assignments can be unpublished per page | Imported components are controlled by the layout code |
| Useful for a shared design with per-page adjustments | Useful for a different arrangement, such as a member dashboard |

A separate Layout content item is optional because default components already provide the theme's default layout.

**Expected result:** you understand both layout approaches and can assign the member layout to its intended pages.

[Back to contents](#contents)

## Import Content and Load Content

Importing means reusing an existing content item inside another content item. For example, a layout can include a sidebar component, and a header can load a stylesheet.

There are two approaches: **import registered content with ltImport**, or **load a browser-ready asset through its direct URL**.

### Method 1 Import registered content with ltImport

Provide the package name and registered content filename:

```php
<?php ltImport('ThemeStarter', 'Header.html'); ?>
```

ThemeStarter identifies the package. Header.html identifies the registered content. LifeTechOCMS uses the registration to locate its resource folder and additional path, so you do not include those folders in this call.

The package is explicitly named. It does not have to be the default theme. This makes it possible to reuse content from a named package in another package's interface.

| **Resource type** | **Example use** |
| --- | --- |
| Component | Include a reusable header, footer or sidebar |
| View | Include a particular registered interface |
| Layout | Include a registered wrapper where appropriate |
| Asset | Include registered CSS or JavaScript |

Import a component:

```php
<?php ltImport('ThemeStarter', 'DashboardSidebar.html'); ?>
```

Import plain CSS inside style tags:

```css
<style>
     <?php ltImport('ThemeStarter', 'Style.css'); ?>
</style>
```

Import plain JavaScript inside script tags:

```js
<script>
     <?php ltImport('ThemeStarter', 'Script.js'); ?>
</script>
```

If the content already contains its own style or script tags, import it directly without adding another pair. Avoid importing a complete document layout inside another complete document, since that can duplicate the HTML wrapper.

### Method 2 Load content through direct or CDN links

Content can come from any resource folder. Choose the loading method according to how the file should be used, rather than assuming all loaded files are assets.

Direct linking tells the browser to request a file at its address. Use a link element for CSS, a script element with src for JavaScript, and an img element for an image.

The package path helper stops at the **parent folder containing the packages**. The developer explicitly adds the package folder name, subfolders and filename. It does not automatically choose the default theme.

This makes the address independent of which theme is currently the default. Another theme, module or plugin can reference an asset from the named package..

The address has these parts:

Parent folder URL + package folder name + subfolders + filename

The following working pattern uses the plugins parent path helper:

```js
<script src="<?= ltPluginPath() ?>/PlgMyTailwind/Services/tailwind_4_cdn.js"></script>
```

| **Part** | **Purpose** |
| --- | --- |
| ltPluginPath() | Supplies the URL up to the plugins parent folder |
| PlgMyTailwind | Explicitly selects the package folder |
| Services | Selects a subfolder in that package |
| tailwind_4_cdn.js | Selects the JavaScript file |

For theme files, apply the same principle using the themes parent path helper, then append **/ThemeStarter/Assets/css/Style.css** or **/ThemeStarter/Assets/js/Script.js**.

Use ltThemePath() to obtain the themes parent URL, then explicitly add your package name and the path to the asset:

```html
<link rel="stylesheet"
       href="<?= ltThemePath() ?>/ThemeStarter/Assets/css/Style.css">
<script src="<?= ltThemePath() ?>/ThemeStarter/Assets/js/Script.js"></script>
```

ltThemePath() stops at the themes directory. It does not add ThemeStarter or choose the default theme. Explicitly naming ThemeStarter allows another package to reference its assets even when ThemeStarter is not the default theme.

Similarly, ltModulePath() supplies the modules parent URL and ltPluginPath() supplies the plugins parent URL. Add the intended package name and remaining file path yourself.

Direct linking is suitable for browser-ready files. It does not render PHP components, views or layouts into the current page. Assets containing PHP instructions need the appropriate LifeTechOCMS content processing.

A CDN link follows the same browser-loading principle but points to a CDN-hosted file. Inline CSS or JavaScript means code written inside style or script tags; it is different from linking an external file.

### Which method should you use

| **Requirement** | **Approach** |
| --- | --- |
| Include a registered component, view or layout | ltImport |
| Include registered CSS or JavaScript in the page output | ltImport with the appropriate tags |
| Load browser-ready CSS, JavaScript or an image by address | Direct URL |
| Reference a package regardless of the default theme | Name the package explicitly in either approach |

**With ltImport, supply the package name and registered filename. With direct linking, supply the package name and full remaining path to the file.**

[Back to contents](#contents)

## Use Site Information and Helper Functions

### Other helpers used in your theme

| **Function or method** | **Purpose** |
| --- | --- |
| ltSiteName() | Display the configured site name |
| ltSiteUrl() | Build site page links |
| ltSiteHostAddress() | Build navigation or redirect addresses |
| dddm::loadDynamicContent() | Display content assigned to the current page |
| ApiTokenDetails::backEndBaseUrl() | Find the configured backend API address |
| ApiTokenDetails::tokenName() | Find the application's token storage key |
| ltPluginPath() | Find the plugins parent URL for explicit file links |

When placing a PHP string into JavaScript, use json_encode so special characters are represented correctly:

```js
<script>
const siteAddress = <?= json_encode(
     ltSiteHostAddress(),
     JSON_HEX_TAG | JSON_HEX_AMP | JSON_HEX_APOS | JSON_HEX_QUOT
) ?>;

function goHome() {
     window.location.href = siteAddress.replace(/\/+$/, '') + '/ThemeStarter/Home';
}
</script>
```

json_encode is a PHP function; window.location.href is a browser property. The LifeTechOCMS helper supplies the site address. Test links against your configured routes, particularly when your installation uses a subfolder.

### Use more site configuration helpers

Site configuration helpers let you use saved website information without hardcoding it into each content file. Update the site settings, and your theme can display the configured values through these helpers.

| **Helper** | **Returned information** |
| --- | --- |
| ltSiteName() | Main website name |
| ltSiteTitle() | Site subtitle |
| ltSiteAlias() | Site alias or short name |
| ltSiteCopyright() | Configured copyright text |
| ltSiteLogo(), ltSiteFavicon() | Configured logo and favicon path or filename |
| ltSiteEmail(), ltSiteEmail2() | Primary and secondary email addresses |
| ltSitePhone(), ltSitePhone2() | Primary and secondary phone numbers |
| ltSiteAddress(), ltSiteAddress2() | Primary and secondary addresses |
| ltSiteOpenHour(), ltSiteClosedHour() | Opening and closing hours |
| ltSiteLinkedln(), ltSiteInstagram(), ltSiteFacebook() | Configured social links |
| ltSiteTwitter(), ltSiteYoutube() | Additional social links |

Use the exact function names. In the linked documentation, the LinkedIn helper is spelled ltSiteLinkedln(), with a lowercase l after Linked.

Display the site subtitle:

```html
<p><?= htmlspecialchars(ltSiteTitle(), ENT_QUOTES, 'UTF-8') ?></p>
```

Display contact information in a footer:

```html
<p>Email: <?= htmlspecialchars(ltSiteEmail(), ENT_QUOTES, 'UTF-8') ?></p>
<p>Phone: <?= htmlspecialchars(ltSitePhone(), ENT_QUOTES, 'UTF-8') ?></p>
<p><?= htmlspecialchars(ltSiteCopyright(), ENT_QUOTES, 'UTF-8') ?></p>
```

For a logo stored as a filename in the installation's uploads folder, the documentation demonstrates this pattern:

```html
<img src="<?= htmlspecialchars(
     rtrim(ltSiteUrl(), '/') . '/uploads/' . ltSiteLogo(),
     ENT_QUOTES, 'UTF-8'
) ?>" alt="Website logo">
```

Check how your logo setting is stored before adding a directory: a stored full URL or path should not have another uploads prefix added to it.

### Understand the URL and environment helpers

| **Helper** | **Purpose** |
| --- | --- |
| isHttps() | Returns whether the request is using HTTPS |
| ltDomain() | Returns the domain name |
| ltBaseUrl() | Returns the domain with its protocol |
| ltSiteUrl() | Returns the root URL of the LifeTechOCMS installation |
| ltThemePath() | Returns the themes parent URL |
| ltModulePath() | Returns the modules parent URL |
| ltPluginPath() | Returns the plugins parent URL |

Use **ltSiteUrl()** for installation-relative page links. Use a package parent helper for direct asset links and explicitly add the package folder name. These functions provide addresses; they do not replace content registration or page assignment.

Full helper reference: [LtSiteInfo and Site Helper Functions](https://www.lifetech.host/hubs/Docs#ltsiteinfo-and-site-helper-functions)

[Back to contents](#contents)

## Connect Theme Views to Backend APIs

The theme presents data; the backend module supplies it. A theme that includes a blog interface does not by itself create blog storage or API routes.

This example uses an endpoint demonstrated in ThemeBlog: **blogs/posts/widget?limit=6&type=popular**. Use it only where the corresponding blog backend is installed and configured. Otherwise substitute a working endpoint from your module.

### Understand the API terms

| **Term** | **Meaning** | **Example** |
| --- | --- | --- |
| Base URL | The common starting address for backend requests | Returned by backEndBaseUrl() |
| Endpoint | A particular backend path | blogs/posts/widget |
| Query parameter | An option added after a question mark | limit=6 |
| GET | Read data | Load popular posts |
| POST | Submit data or request an action | Create a comment, when the module supports it |
| JSON | A structured data format used by the API | An object with responseData |
| Token | A login credential used by protected API requests | A bearer token |
| HTTP status | The transport-level request result | 200 or 401 |
| responseCategory | LifeTechOCMS's application-level result category | 200 for success in these themes |
| responseData | The returned application data | A list of posts |
| responseResult | A response message | An explanation when a request fails |

### Create a Posts view

Create Posts.html as View content with additional path / and Is Theme Default set to No. Paste:

```html
<section class="card">
     <h1>Popular posts</h1>
     <p id="postsStatus" role="status">Loading posts...</p>
     <ul id="postsList"></ul>
 </section>
 
 <script>
 (async function loadPosts() {
     const apiBase = <?= json_encode(
         ApiTokenDetails::backEndBaseUrl(),
         JSON_HEX_TAG | JSON_HEX_AMP | JSON_HEX_APOS | JSON_HEX_QUOT
     ) ?>;
     const status = document.getElementById('postsStatus');
     const list = document.getElementById('postsList');
 
     try {
         const url = apiBase.replace(/\/+$/, '')
             + '/blogs/posts/widget?limit=6&type=popular';
         const response = await fetch(url, {
             method: 'GET',
             headers: { Accept: 'application/json' }
         });
         if (!response.ok) {
             throw new Error('Request failed with HTTP status ' + response.status);
         }
         const result = await response.json();
         if (Number(result.responseCategory) !== 200) {
             throw new Error(result.responseResult || 'Unable to load posts.');
         }
         const posts = Array.isArray(result.responseData) ? result.responseData : [];
         list.replaceChildren();
         for (const post of posts) {
             const item = document.createElement('li');
             item.textContent = post.title || 'Untitled post';
             list.appendChild(item);
         }
         status.textContent = posts.length ? '' : 'No posts available.';
     } catch (error) {
         status.textContent = error.message;
     }
 })();
 </script>
```

Creating this View content automatically creates its associated page and menu. Check the generated route, such as **/ThemeStarter/Posts**, and open it through its menu or Preview.

### Read what the code does

First, PHP supplies the backend base address. The browser then calls fetch() to request the endpoint. await waits for the response. response.ok checks HTTP success; responseCategory checks the application's result. Finally, the code creates a list item for each returned post.

The loading text gives feedback while the request runs. An empty result displays a useful message. A failed request displays its error. Using textContent renders post titles as text rather than executable HTML.

### Send a token for a protected request

ThemeBlog's administration views use the Authorization header. This example prepares those headers; it does not invent a protected endpoint:

```html
<script>
 const tokenName = <?= json_encode(
     ApiTokenDetails::tokenName(),
     JSON_HEX_TAG | JSON_HEX_AMP | JSON_HEX_APOS | JSON_HEX_QUOT
 ) ?>;
 
 function authenticatedHeaders() {
     const token = localStorage.getItem(tokenName);
     if (!token) throw new Error('Please sign in first.');
     return {
         Accept: 'application/json',
         Authorization: `Bearer ${token}`
     };
 }
 </script>
```

Use these headers only with the intended trusted backend and the module's documented request. Backend permissions must still decide what the caller can do. For a JSON submission, the module may require Content-Type: application/json and a body built with JSON.stringify(); follow its actual method and field names.

[Back to contents](#contents)

## Edit Theme Package

### Update package information

1. Return to the Themes Development list.
1. Find ThemeStarter and choose **Edit Theme Package**.
1. Update the description or version using the available fields.
1. Save and confirm the details in the list.

This edits the package information. To change Header.html's code, use its content editor instead.

### Maintain the version and dependencies

For example, after a reviewed update you might change the theme version from 1.0.0 to 1.0.1. Follow the package version policy used by your project. Keep the generated manifest and panel information consistent using the supported editing and export workflow.

Record required packages accurately. A blog view that calls a module endpoint needs that module installed; the theme does not create the endpoint by itself.

### Write a useful README

Include the theme's purpose, installation instructions, required packages, intended core compatibility, available pages and configuration steps. Explain any logo, contact or API settings the next developer needs.

**Expected result:** another developer can identify the release and understand what it requires  

![image](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/3e0992590310e5957b493008178f4918.png)

[Back to contents](#contents)

## Previewing a Theme

### Open Preview

1. Open the Themes Development list.
1. Locate ThemeStarter.
1. Select **Preview**.
1. Inspect the page and refresh it after saving code changes.

Preview is useful while developing; access and session rules still apply to the pages you open.

### Check the first working result

Use the theme's Preview action or open the configured page through LifeTechOCMS. Publish the theme and assign it to the required pages when ready; select it as the site's default theme if you want it to be the site's main design.

Confirm these results:

1. Home displays the shared header, Home card and footer.
1. Clicking the welcome button displays the message.
1. About uses the same design but displays its own text.
1. The navigation links open their configured routes.
1. The page remains readable on a narrow screen.

**You have completed a basic theme.** Sections [Understand the Default Layout and Custom Layouts](#understand-the-default-layout-and-custom-layouts) and [Connect Theme Views to Backend APIs](#connect-theme-views-to-backend-apis) extend it with an alternative layout and backend data.

### Test pages and browser behaviour

Use Preview while developing. Check Home, About and any separate layout. Test links, the welcome button, narrow screens and API loading. In browser developer tools, Console shows JavaScript errors and Network shows request statuses.

Check that only one document wrapper and one dynamic insertion point appear in the chosen composition. For API views, test successful data, an empty response and a failed request.

**Expected result:** you have verified the design before using the publishing actions.

[Back to contents](#contents)

## Publishing a Theme

### Understand publishing

Publishing makes a theme available for frontend use. Installing or creating a theme does not replace the site's design automatically.

### Publish through the panel

1. Locate the completed theme in Themes Development.
1. Use its **Publish** control.
1. Confirm the panel shows it as published.
1. Choose whether to apply it to selected pages or set it as default, as explained in sections [Publish Theme to Page](#publish-theme-to-page) and [Set Theme as Default](#set-theme-as-default).

### Check content publication separately

Theme publication, page content publication and page access are different settings. Confirm all three when reviewing a page. If the header appears but the view does not, inspect ContentLoadBody and the assigned conten's publication rather than repeatedly publishing the theme.

**Expected result:** the theme is available to apply, and its intended content can be displayed for the intended visitors.

[Back to contents](#contents)

## Publish Theme to Page

### When to use a page specific theme

Use this action when one or more pages need a different theme from the site's main design. For example, a campaign landing page may use ThemeStarter while the rest of the site uses another default theme.

### Apply a theme to selected pages

1. Locate the published theme in Themes Development.
1. Open **Publish Theme to Page**, or the matching page assignment action.
1. Choose the intended existing page or pages using your panel's controls.
1. Save and open those pages to confirm their appearance.

The online documentation identifies the action but does not specify every current field. Use the page-selection controls in your installed panel.

### Distinguish theme selection from View creation

Creating View content automatically creates its page and menu and connects the content. Publish Theme to Page selects the surrounding theme for a page; it is not a requirement to manually recreate those records.          




![image](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/f3f54b69c7d1fb12946c06609acb4d55.png)

 
**Expected result:** the selected pages use the chosen design while the site retains its configured default theme.

[Back to contents](#contents)

## Set Theme as Default

### What default means

The default theme is the site's main frontend design. Only one theme can hold default status at a time. This differs from Is Theme Default on an individual component: that component flag controls the theme's default page composition.

### Select the default theme

1. Preview and publish the intended theme.
1. Find it in Themes Development.
1. Choose **Set Default** or **Set Theme as Default**.
1. Confirm that it is now identified as the default theme.
1. Open representative frontend pages and check their content, navigation and styling.

### What happens to the previous default

The selected theme becomes the main design, and the previous theme loses default status. This does not mean the previous theme package has been deleted. Review pages with explicit theme selections separately.

| **Setting** | **What it controls** |
| --- | --- |
| Publish theme | Availability for frontend use |
| Set theme as default | Main site design |
| Publish theme to page | Design selected for particular pages |
| Is Theme Default on a component | Component membership in the default composition |

**Expected result:** one theme is identified as the default, and the site's ordinary frontend pages use the intended design.

[Back to contents](#contents)

## Export Theme

### Prepare the theme

Preview its pages, save all changes and update the README and version. Check that required packages are documented and that content imports use correct names.

### Export through the panel

1. Open the theme's content area.
1. Choose **Export Theme**.
1. Download the resulting package and retain it as the version you intend to distribute.

Use **Export Theme** in the panel. A proper LifeTechOCMS export includes source files and registration records. This is how the supplied ThemeBlog and ThemeBrainDump packages combine presentation files with Export/ metadata.

Add a useful README explaining installation, required modules, pages and theme configuration. The supplied READMEs are empty, so they do not yet provide installation guidance.

### Understand what an export contains

The supplied exports combine source files with registration records such as content.json, page.json and menu.json. These records let the platform recognize the package's content and destinations. A ZIP containing only copied HTML files is not equivalent to a platform export.

### Name the exported package

Use a filename beginning with Theme, such as ThemeStarter.zip, as required by the previous installation documentation. Share installation guidance and dependency information with the ZIP.

**Expected result:** you have a platform-exported theme package ready for backup or installation.

[Back to contents](#contents)

## Installing a Theme

LifeTechOCMS provides two ways to install an existing theme: download an installation ZIP and upload it, or browse online from the backend and install the selected package.

### Method 1 Download and upload the theme

1. Visit the LifeTechOCMS Marketplace, find the theme and download its installation ZIP. You can also use a theme ZIP exported from another LifeTechOCMS installation.
1. Sign in to the backend of the target installation.
1. Open **Packages > Themes Development**.
1. Select **Install Theme**.
1. Choose the downloaded or exported theme ZIP and complete installation.
1. Open the installed theme and preview its pages.

Use a clear package filename such as ThemeStarter.zip and a proper installation package. A ZIP of copied HTML files alone does not contain the content registrations and page records included in a LifeTechOCMS export.

### Method 2 Browse Online from the backend

1. Sign in to your LifeTechOCMS backend.
1. Open **Packages > Themes Development**.
1. Select **Browse Online**.
1. Search for the existing theme you want.
1. Use its download/install option. LifeTechOCMS downloads and installs the package.
1. Open the installed theme and preview its pages.

This approach lets you discover and install the theme from inside the backend. The first approach is useful when you already have its installation ZIP or an export from another site.

### Verify and choose how to use the theme

After either method, confirm that the theme's content items, pages and menu relationships are available. Install any required dependencies, check the actual routes on the target site, and preview the imported pages.

When ready, publish the theme. Then either set it as the site's default theme or apply it to selected pages. Installation makes a theme available; publishing and selecting its use are separate steps.

Check the theme's supported core versions before installing. Preserve its declared dependencies and release information when moving it between sites.

**Expected result:** the existing theme is installed, previewed and ready to publish and use.  

![image](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/e27a7fb04cfcdcaa430cb45bb045ccb9.png)

[Back to contents](#contents)

## Delete Theme

### Check before deleting

Deleting removes the theme package permanently according to the online documentation. Export it first if you may need its code again. Review pages that use the theme and arrange an appropriate replacement.

If it is the current default, first publish and select another working default theme. The site must retain a default theme.

### Delete through the panel

1. Open Themes Development.
1. Identify the exact theme package to remove.
1. Use its **Delete** action and review any confirmation shown by the panel.
1. Complete deletion only after checking the package name and replacement design.
1. Confirm the package is gone from the list and affected pages still work.

### Check the result

Test the default frontend design and any pages previously using the deleted theme. The online guide does not describe every related-record cleanup rule; inspect remaining page and menu settings in your installation.

**Expected result:** the unwanted theme is removed and the site still has a working default design.

[Back to contents](#contents)

## Security and Management Permissions

### Backend management roles

Installing and deleting theme packages require privileged roles according to the existing documentation. Use a permitted backend account to manage packages. A visitor's permission to open a page is separate from a developer's permission to edit its theme.

### Page access and API permissions

Review the intended visitor roles on each page. For protected API calls, send the required token and let the backend enforce permissions. Hiding a button in the theme does not authorize or block the corresponding backend action.

### Site wide changes

Changing the default theme affects the main frontend design. Preview and test representative pages before applying it. Export the current theme if you need a restorable copy of its source and registrations.

### Safe output and external assets

Use htmlspecialchars when displaying text in HTML, json_encode when supplying PHP values to JavaScript, and textContent for plain text returned by APIs. Choose asset URLs intentionally and confirm their availability in the browser's Network panel.

**Expected result:** package management, page access and backend authorization are understood as separate responsibilities.

[Back to contents](#contents)

## Troubleshooting and Development Checklist

### Solve common beginner problems

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

### Final checklist

1. Create the theme through the panel and preserve its generated metadata.
1. Register components, views and assets with the correct types and paths.
1. Load plain CSS inside style tags and plain JavaScript inside script tags.
1. Arrange document opening, header, dynamic loader and footer in order.
1. Check the page, menu and assignments automatically created for each View content item.
1. Build links with the site helper and that configured route.
1. Use layouts when a page needs a different composition.
1. Preview every page and install the modules required by API examples.
1. Export through LifeTechOCMS when preparing the theme for another installation.

[Back to contents](#contents)

## Example Themes and References

### Inspect the supplied themes

Once ThemeStarter works, use the larger themes to see how the same ideas scale.

| **What you want to learn** | **Example to inspect** |
| --- | --- |
| Document opening and stylesheet import | ThemeBlog/Components/Top-header.html |
| Dynamic view loading | Either theme's Components/ContentLoadBody.html |
| Administration layout with imported components | ThemeBlog/Layouts/Admin-layout.html |
| Separate authentication design | ThemeBrainDump/Layouts/Auth/AuthLayout.html |
| Shared API address and token helpers | ThemeBlog/Assets/js/Script.js |
| A view that loads blog data | ThemeBlog/Views/Blog.html |
| Registered content types and subfolders | Either theme's Export/content.json |
| The distinction between filename and route | Either theme's Export/page.json |

### Documentation references

Previous learning documentation: [Theme Development](https://www.lifetech.host/hubs/Docs#theme-development)

The updated folder names, resource types, registration fields and function calls are grounded in the supplied ThemeBlog and ThemeBrainDump packages. The beginner theme is a new teaching example built from those patterns. The view creation workflow and DDM terminology include the platform author's corrections. Exact layout controls should be checked in the installed platform.

Site helper reference: [Site Info](https://www.lifetech.host/hubs/Docs#ltsiteinfo-and-site-helper-functions)

[Back to contents](#contents)
