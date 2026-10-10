# LifeTechOCMS Theme Development for Beginners

A practical guide to creating, coding and managing themes through the backend. This edition contains 29 numbered topics, including the confirmed naming conventions.

## Contents

1. Theme Development Overview
2. Accessing Themes Development
3. Add Theme Package
4. Theme Content and the Four Resource Types
5. Understand Theme Folders and Subfolders
6. Theme Development Conventions
7. Add New Theme Content
8. Sync Files
9. Editing Theme Content Code
10. Edit or Update Existing Theme Content
11. Build the Shared Theme Components
12. Add the Compulsory Dynamic Content Loader
13. Create Views Pages and Menus
14. Load Menus for the Current User's Roles
15. Understand the Default Layout and Custom Layouts
16. Import Content or Load Content
17. Use Site Information and Helper Functions
18. Connect Theme Views to Backend APIs
19. Edit Theme Package
20. Previewing a Theme
21. Publishing a Theme
22. Publish Theme to Page
23. Set Theme as Default
24. Export Theme
25. Installing a Theme
26. Delete Theme
27. Security and Management Permissions
28. Troubleshooting and Development Checklist
29. Example Themes and References

## 1 Theme Development Overview

This guide teaches you how to create and manage a LifeTechOCMS theme. We build ThemeStarter with Home and About views, shared components, CSS and JavaScript, then add an optional dashboard layout and a backend API example.

### 1.1 What a theme does

A theme supplies the presentation of a website: its document structure, visible navigation, styling and placement of assigned content. A module can supply application features and data while the theme provides the surrounding design. Content assigned from themes, modules or plugins appears through the dynamic loader.

### 1.2 Requirements and testing environment

You need a working LifeTechOCMS installation, access to its administration panel, and basic knowledge of HTML. CSS changes appearance; JavaScript adds browser behaviour; PHP runs on the server and lets a theme call LifeTechOCMS functions.

Write theme content in the LifeTechOCMS code editor, or edit the corresponding files in your local LifeTechOCMS installation. Open the theme through LifeTechOCMS when testing: opening an HTML file directly on your computer will not run its PHP helpers.

### 1.3 How to use this guide

Follow sections 2 to 13 to build your first theme. Section 14 adds role-based menus and section 15 explains custom layouts. Sections 16 to 18 cover imports, helpers and APIs; sections 19 to 27 cover management actions. Use a number such as 12.3 when recording an observation.

The snippets use ThemeStarter consistently. ThemeNova and ThemeStarter follow the same confirmed package and content naming conventions; this guide does not require ThemeNova to be installed. The CSS is a small teaching example, and the loader can work with your chosen styling framework.

### 1.4 Key terminology

| Keyword | Meaning | Small example |
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

**A view is not a page route.** `Home.html` is a content filename; `/ThemeStarter/Home` is the address visitors open. When you create content as a View resource, LifeTechOCMS creates its page and menu automatically.

**A layout is also content.** Components, views, layouts and assets are all managed as content items. Their resource types tell LifeTechOCMS what kind of content they are and where their files belong.

## 2 Accessing Themes Development

### 2.1 Open the theme management area

1. Sign in to the LifeTechOCMS backend with a role permitted to manage packages.
2. Open **Packages**.
3. Select **Themes Development**.

### 2.2 Understand the theme list and actions

The theme list is where you create, install and manage theme packages. Open a package to work on the individual content items inside it.

| Action | Purpose | Example |
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

**Expected result:** you can locate a theme package and distinguish package actions from actions on its content.

## 3 Add Theme Package

1. Sign in to the backend.
2. Open **Packages → Themes Development**.
3. Choose **Create Theme** or **Add Theme Package**.
4. Enter `ThemeStarter` as the package name. Use no spaces.
5. Enter a description such as `A beginner theme with Home and About pages`.
6. Enter a package version such as `v1.0.0` and submit the form.
7. Open ThemeStarter to manage its content.

Creating the theme from the panel generates its package metadata and necessary folders. Use these generated files as your starting point. The exact button labels may vary between installed versions.

**What you have now:** a theme package ready for content. A package without page content is not yet a complete website design.

### 3.1 Understand package metadata and dependencies

`package.json` describes the package. It is LifeTechOCMS package metadata; its name does not mean you must install Node.js or run npm to create a basic theme.

An example of the fields used in the supplied themes is:

```json
{
    "packageName": "ThemeStarter",
    "packageType": "theme",
    "version": "v1.0.0",
    "dependsOn": [],
    "description": "A beginner theme"
}
```

This is a shortened explanation, not a replacement for the generated manifest. Keep the other fields and identifiers created by LifeTechOCMS.

`packageName` identifies the package. `packageType` says that it is a theme. `version` identifies your theme release. `dependsOn` lists packages the theme needs. For example, ThemeBlog declares a dependency on `MdBlog` version `1.0` because its interface requests blog data from a backend module.

## 4 Theme Content and the Four Resource Types

In LifeTechOCMS, **content** is an individual item you create and register inside a package. A header, a Home interface, a dashboard wrapper and a stylesheet are all content. You select a **resource type** to describe the item's job and determine its folder.

### 4.1 Component content

A component is a reusable part of the design. For example, Header.html displays navigation and Footer.html displays the footer. The same component can appear on several pages, so one edit can update a shared part of the design.

Component files belong in Components/. A simple component might contain:

```html
<header>
    <p>Welcome to our website</p>
</header>
```

Components marked Is Theme Default form the theme's default page composition. ContentLoadBody is a component whose job is to load the content assigned to each page.

### 4.2 View content

A view is the interface displayed for a page, such as Home, About or a book catalogue. View files belong in Views/.

```html
<section>
    <h1>About us</h1>
    <p>Learn about our organisation.</p>
</section>
```

When you create content with the View resource type, LifeTechOCMS automatically creates its **content record, page and menu**, and assigns the view to its page and menu. The menu leads visitors to that page; the dynamic content loader displays the assigned view there. You do not need to create and connect these records manually for this workflow.

### 4.3 Layout content

A layout arranges reusable components around dynamic content. Layout files belong in Layouts/. For example, an administration layout can place a sidebar beside the current view:

```php
<div>
    <?php ltImport('ThemeStarter', 'MemberSidebar.html'); ?>
    <?php dddm::loadDynamicContent(); ?>
</div>
```

The wrapper and styling are your choice. A separate layout is optional when default components already provide the required design. Use another layout when views need a different arrangement.

### 4.4 Asset content

An asset supplies supporting styles, scripts or other design resources. Asset files belong in Assets/, often in subfolders such as css/ and js/.

```css
.page-title {
    color: #155e75;
}
```

This stylesheet is asset content. An HTML element with class page-title can use its styling once the stylesheet is loaded. Assets can be imported as registered content or loaded through an appropriate direct file URL, as explained later.

### 4.5 How these types work together

| Item | Resource type | Its job |
| --- | --- | --- |
| Header.html | Component | Shared navigation |
| Home.html | View | Home page interface |
| MemberLayout.html | Layout | Alternative arrangement around a view |
| Style.css | Asset | Colours, spacing and other styles |

A resource type describes the content's purpose; it is different from its extension. Both a component and a view can be .html files. Choose the resource type according to the item's job.

## 5 Understand Theme Folders and Subfolders

Your local theme lives under `packages/themes/ThemeStarter/`. Both uploaded themes use the following folders, with these exact capital letters.

| Folder | What belongs here | Beginner example |
| --- | --- | --- |
| Components/ | Reusable page parts | Header.html, Footer.html |
| Views/ | Main page interfaces | Home.html, About.html |
| Layouts/ | Optional alternative page wrappers | MemberLayout.html |
| Assets/ | Supporting styles and scripts | css/Style.css, js/Script.js |
| ddm/ | System-managed DDM marker files | Home.View.lifetech |
| Export/ | Records included when exporting a theme | content.json, page.json, menu.json |

`README.md` explains your theme to other developers. `LICENSE` states its licence. The generated `index.php` files are not your Home view; preserve the system files rather than replacing them with your interface.

### 5.1 How subfolders work

A subfolder helps you organize related files. For example:

| Resource type | Content name | Additional path | File location |
| --- | --- | --- | --- |
| Component | Header.html | / | Components/Header.html |
| View | Home.html | / | Views/Home.html |
| Asset | Style.css | /css | Assets/css/Style.css |
| Asset | Script.js | /js | Assets/js/Script.js |
| Component | AdminHeader.html | /admin | Components/admin/AdminHeader.html |

The additional path belongs **inside the resource folder**. Do not enter the whole installation path in this field. `/admin` is an organizational folder; it does not automatically create an administration route or protect a page.

ThemeBlog uses lowercase `admin`; ThemeBrainDump uses folders such as `Admin` and `Auth`. Match the registered path exactly. Linux may treat `admin` and `Admin` as different folders.

### 5.2 What ddm and Export mean for a beginner

**DDM means Data Defacing Model.** The supplied themes have `.lifetech` marker files named after content and its type, such as `ContentLoadBody.Component.lifetech`. These markers are empty in the supplied exports. Your actual interface code belongs in the resource files, not in these markers.

`Export/content.json` contains content registrations. `Export/page.json` contains page and route records. `Export/menu.json` contains menu records. Both supplied themes also have `pageContent.json` and `table.json`, currently containing empty arrays. Let LifeTechOCMS manage these records through its panel and export process.

## 6 Theme Development Conventions

Conventions give developers a consistent way to name packages and content. The four rules below cover package names, content names, theme versions and release tags. We can extend this section as more conventions are agreed.

### 6.1 Theme package names use PascalCase

PascalCase joins words without spaces and capitalizes the first letter of every word. Use it for theme package names.

| Suitable name | Why it follows the convention |
| --- | --- |
| ThemeNova | Theme and Nova each start with a capital letter |
| ThemeStarter | Theme and Starter each start with a capital letter |
| ThemeBlog | Theme and Blog each start with a capital letter |

For our walkthrough, enter `ThemeStarter` as the package name. Refer to that exact name when importing its content:

```php
<?php ltImport('ThemeStarter', 'Header.html'); ?>
```

The names `themeStarter`, `theme_starter` and `Theme Starter` do not follow this convention. Consistent spelling also helps avoid path and import errors.

### 6.2 File names and content names use PascalCase

Use PascalCase for the filename before its extension. Keep the extension appropriate to the file: `.html`, `.css` or `.js` in these examples.

| Purpose | Content or filename |
| --- | --- |
| Document opening | TopHeader.html |
| Dynamic content insertion point | ContentLoadBody.html |
| Main page interface | Home.html |
| Alternative page wrapper | MemberLayout.html |
| Shared stylesheet | Style.css |
| Shared JavaScript | Script.js |

For example, register `ContentLoadBody.html` as Component content, then edit the matching file. An import must use the same registered name and capitalization.

This naming convention applies to developer-created theme content. Keep platform-generated filenames such as `package.json` and `index.php` as generated. Historical names in the supplied themes are shown as they exist; do not rename them without updating their registrations and references.

**Expected result:** you can choose a consistent package name and content filename before creating them.

### 6.3 Theme versions use v followed by three numeric parts

Use a version such as `v1.0.0` for your theme. Keep the leading v and all three numeric parts. This is the convention for new theme releases in this guide; historical versions in supplied packages are shown as recorded.

| Part | Meaning | Example |
| --- | --- | --- |
| v | Version prefix | v1.0.0 |
| First number | Major version | v2.0.0 for a major release |
| Second number | Minor version | v1.1.0 for a minor release |
| Third number | Patch version | v1.0.1 for a patch release |

For example, ThemeStarter begins at `v1.0.0`. Record the release version consistently in the theme package information and its package.json metadata using the supported platform workflow.

### 6.4 GitHub release tags use the same three-part version

Use GitHub tags such as `v1.0.0`, `v1.0.1` and `v1.1.0`. The release tag must match the theme version being released. A tag identifies a particular source revision so developers can download and discuss the same release.

For a theme whose package version is `v1.0.0`, the matching release tag is `v1.0.0`. Avoid shortened tags such as v1.0 for this convention. Update the package version before preparing its matching release tag.

## 7 Add New Theme Content

Open ThemeStarter and select **Add Content**. Create the following items one at a time.

| Content name | Resource type | Additional path | Is Theme Default |
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

### 7.1 Understand the content form

| Setting | What to enter or select | Why it matters |
| --- | --- | --- |
| Content Name | The filename, such as Home.html | Used when identifying or importing content |
| Description | A brief purpose, such as Main navigation | Helps you recognize the content later |
| Content Category | An optional organization label | Groups content in management; it is not its resource folder |
| Resource Type | Component, View, Layout or Asset | Determines the content's role and resource folder |
| Additional Path | /, /css, /js or another subfolder | Organizes files within that resource folder |
| Store Type | Folder for these examples | Stores code in the corresponding file |
| Is Theme Default | Yes for the shared components above | Identifies the default page composition |

Depending on the panel, resource type may be labelled **Theme Resource Type**. The exports store it as `themeResourceType`, the subfolder as `additionalPath`, and the default flag as `isThemeDefault`.

After creating an item, use its **Code Editor** action to enter the code in sections 11 to 13. If you create files locally instead, use Sync Files to register them, as explained in section 8.

**What you have now:** eight registered items. Sections 11 to 13 give each item a specific job.

## 8 Sync Files

Sync Files registers new files created locally in the theme's resource folders as content in the database. It is useful when you write files in a local editor or when an AI tool generates new theme files for you.

### 8.1 Which folders are scanned

Place files inside the appropriate resource folder of the theme package. Sync Files applies to the Components, Views, Assets and Layouts folders.

| Folder | Example new file | Content resource type |
| --- | --- | --- |
| Components/ | Announcement.html | Component |
| Views/ | AboutUs.html | View |
| Assets/ | css/ExtraStyle.css | Asset |
| Layouts/ | LandingLayout.html | Layout |

Use the confirmed PascalCase naming conventions for developer-created content names. Choose the folder according to the content's job, not just its extension: both a view and a component can be HTML files.

### 8.2 Register a locally created view

For example, create this file in the installation you are developing:

```text
packages/themes/ThemeStarter/Views/AboutUs.html
```

Add a small interface:

```html
<section class="card">
    <h1>About our team</h1>
    <p>Learn about the people behind our website.</p>
</section>
```

Then:

1. Save AboutUs.html inside ThemeStarter's Views folder.
2. Open ThemeStarter's content management area in the backend.
3. Click **Sync Files**.
4. Find AboutUs.html in the content list and check that it is registered as View content.
5. Review its content settings and the related page and menu records, then preview it through LifeTechOCMS.

The confirmed purpose of Sync Files is file-to-database content registration. Check the page and menu results in your installed version rather than assuming every sync operation performs the same follow-up actions as Add Content.

**Expected result:** the locally created AboutUs.html is known to LifeTechOCMS and appears as a registered content item.

### 8.3 Use Sync Files with AI generated code

Ask the AI tool to generate files using your theme's package name, correct resource folders and PascalCase content names. Place the generated files into the target installation, review their code, and run Sync Files. Inspect the registered content and preview the relevant pages.

A file generated in another directory or on another computer must first be copied into the target theme's resource folders. Sync Files registers files present in those folders; it does not retrieve files from an AI conversation.

### 8.4 Understand syncing versus editing

| Action | When to use it |
| --- | --- |
| Add Content | Create and register content through the backend |
| Sync Files | Register new files placed locally in the resource folders |
| Code Editor or local editing | Change code in an existing registered file |
| Upload | Update an existing content item with an edited file |

Saving an existing registered file changes its code. Creating a new file adds a file to disk; Sync Files supplies its content registration. After syncing, review publication, access and default component settings separately.

## 9 Editing Theme Content Code

### 9.1 Use the built in code editor

1. Open ThemeStarter from the theme list.
2. Find the registered content item, such as Header.html.
3. Select its **Code Editor** action, usually shown with a code symbol.
4. Enter or update its code and save.
5. Refresh Preview to check the result.

Start with the content created in section 7. Sections 11 to 13 provide the starter code.

### 9.2 Work with a local code editor

For a local installation, open the corresponding registered file in VS Code, PHPStorm or another editor. In the updated structure, examples include:

```text
packages/themes/ThemeStarter/Components/Header.html
packages/themes/ThemeStarter/Views/Home.html
packages/themes/ThemeStarter/Assets/css/Style.css
```

Save the file and refresh the page through LifeTechOCMS. You are editing the file used by that local installation, so you do not need to upload the same edit back to it. Changes made to a separate computer or checkout must still be transferred to the target installation.

The previous online guide used a single contents folder. Use the resource folders in the updated structure. For a new local file, place it in the appropriate resource folder and run Sync Files from the backend to register it. Section 8 explains this workflow.

### 9.3 Check your saved changes

Change a paragraph in Home.html, save it and open the generated Home page. The new text should appear. If PHP appears as text, check that you opened the page through LifeTechOCMS rather than opening the file directly.

## 10 Edit or Update Existing Theme Content

### 10.1 Edit content settings

Use the content row's **Edit** action to change its description or other registered settings. Review the resource type and additional path before saving: these identify where the item belongs.

For example, correcting Header.html's description does not require creating a second Header content record.

### 10.2 Upload an updated content file

1. Open the theme's content list.
2. Locate the existing content item.
3. Select its **Upload** action.
4. Choose the updated file for that item and complete the upload.
5. Preview a page that uses the content.

Use Code Editor when writing code in the panel; use Upload when replacing it with an edited file. Edit changes the record's settings.

### 10.3 Check references after a change

If you change a content name or path, verify imports, direct asset links and relevant page assignments. A direct URL contains the folders and filename, so a moved asset requires an updated URL. Registered imports must still identify the correct content item.

**Expected result:** the existing registered item contains the update and pages that use it continue to work.

## 11 Build the Shared Theme Components

### 11.1 Add the stylesheet

Open `Style.css` and enter:

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

A **class** is a reusable CSS selector. An element with `class="card"` receives the `.card` styles. A **CSS variable**, such as `--brand`, gives you one place to change a shared design value.

This asset contains plain CSS, so its importer will be placed inside a `<style>` element in section 11. This matches the stylesheet loading pattern in ThemeBlog.

### 11.2 Create the document opening component

Open `TopHeader.html` and enter:

```php
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

This component opens the HTML document. `viewport` makes the page scale correctly on mobile devices. It deliberately leaves `body` and `html` open; Footer will close them after the view has been rendered.

### 11.3 Understand ltSiteName

`ltSiteName()` returns the configured site name. It allows a visitor-facing title to follow the site's settings instead of a name hardcoded into the theme.

`<?= ... ?>` is PHP's short echo syntax: it outputs the expression's value into the HTML. `htmlspecialchars()` is a PHP function that safely displays text in HTML; it is not a LifeTechOCMS-specific function.

### 11.4 Understand ltImport

```php
<?php ltImport('ThemeStarter', 'Style.css'); ?>
```

`ltImport()` loads registered content. In the supplied themes, it accepts a package name and a content filename. Here, `ThemeStarter` identifies the package and `Style.css` identifies the asset.

Notice that the call uses `Style.css`, not `Assets/css/Style.css`. The content registration records its resource type and additional path. Use exact spelling and capitalization, and choose distinct filenames within a package.

### 11.5 Create the visible header and navigation

Open `Header.html` and enter:

```php
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

`ltSiteUrl()` supplies the base used for links in the provided themes. `rtrim(..., '/')` removes an ending slash before adding the route. Check the automatically generated Home and About routes in section 13 before using them in your links.

**An href is the destination of a link.** It should refer to the configured page route, not the view's filesystem path. Do not link visitors directly to `Views/Home.html`.

### 11.6 Add JavaScript and the footer

Open `Script.js` and enter this **plain JavaScript**:

```javascript
const welcomeButton = document.getElementById('welcomeButton');
const welcomeMessage = document.getElementById('welcomeMessage');

if (welcomeButton && welcomeMessage) {
    welcomeButton.addEventListener('click', () => {
        welcomeMessage.textContent = 'Your LifeTechOCMS theme is working!';
    });
}
```

The condition checks that both elements exist. This lets the same script run on About without failing because the Home button is absent. `textContent` displays plain text in an element.

Open `Footer.html` and enter:

```php
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

The script is imported after the dynamic view, so the Home elements already exist when JavaScript looks for them. `date('Y')` is a PHP function that supplies the current year.

### 11.7 Know whether your asset already contains tags

Our `Script.js` contains JavaScript only, so Footer supplies `<script>` tags. ThemeBlog's supplied `Script.js` already contains `<script>` tags and PHP helper calls, so that asset is imported directly instead:

```php
<?php ltImport('ThemeBlog', 'Script.js'); ?>
```

Do not wrap an asset that already contains `<script>` tags inside another `<script>` element. Similarly, our stylesheet contains CSS only, so TopHeader provides `<style>` tags.

When an asset contains PHP, load it through LifeTechOCMS's registered content processing. A direct request for an ordinary `.js` file does not normally execute PHP embedded in it.

## 12 Add the Compulsory Dynamic Content Loader

Your theme provides the page design, including its header, navigation and footer. Each page also needs a place to display the content assigned to it.

The **dynamic content loader** provides that place. It loads and displays any **theme, module or plugin content assigned to the current page**, including multiple assigned content items.

### 12.1 Add the loader to your theme

Create or open the `ContentLoadBody.html` component and add:

```php
<?php dddm::loadDynamicContent(); ?>
```

Set **Is Theme Default** to **Yes** so this component forms part of the theme's default page composition. Position it where assigned content should appear, usually between the header and footer.

The function call is the required instruction. No particular HTML wrapper, CSS class or styling framework is required. You can leave it on its own or wrap it in any HTML and classes that suit your design:

```php
<section class="my-page-content">
    <?php dddm::loadDynamicContent(); ?>
</section>
```

`my-page-content` is only an example chosen by the developer. The wrapper controls presentation; the function loads assigned content.

### 12.2 How does it work

| Page | Assigned content | What the loader displays |
| --- | --- | --- |
| Home | Home view from a theme | The Home interface |
| Book Catalogue | Book listing content from a module | The book listing interface |
| A page using plugin content | Displayable content assigned from a plugin | That plugin's assigned content |

You do not rewrite the loader for each page. **The page's assignments determine what appears; the loader's position determines where it appears.**

### 12.3 Why is it necessary

Assigning content to a page tells LifeTechOCMS what to display. The loader gives the theme an insertion point for that content. Without the loader in the resulting page composition, the shared header and footer may appear while the assigned page content is missing.

For our beginner theme, arrange TopHeader, Header, ContentLoadBody and Footer in that order. When Home is opened, the loader displays the assigned Home view. When a module page is opened, the same loader displays its assigned module content.

### 12.4 How is this different from ltImport

`ltImport()` loads a specific registered item that you name:

```php
<?php ltImport('ThemeStarter', 'Header.html'); ?>
```

`dddm::loadDynamicContent()` loads the content assigned to the current page:

```php
<?php dddm::loadDynamicContent(); ?>
```

Use an import for a specific reusable item. Keep the dynamic loader where page-assigned theme, module or plugin content should appear.

### 12.5 What if the page uses a separate layout

A separate layout also needs a dynamic insertion point. Place the same function call inside that layout where assigned content should appear. The default composition provides the loader through ContentLoadBody; a custom layout can provide it directly. Check that the resulting composition does not load the same dynamic content twice.

## 13 Create Views Pages and Menus

### 13.1 Write the Home and About views

Open `Home.html` and enter:

```html
<section class="card">
    <h1>Welcome to our website</h1>
    <p>This Home view is displayed inside the theme's dynamic content area.</p>
    <button id="welcomeButton" type="button">Show welcome message</button>
    <p id="welcomeMessage" role="status"></p>
</section>
```

Open `About.html` and enter:

```html
<section class="card">
    <h1>About us</h1>
    <p>We built this website with LifeTechOCMS.</p>
    <p>This view shares the same header, stylesheet and footer as Home.</p>
</section>
```

A view normally contains the interface for the dynamic area. Do not add another complete `html`, `head` and `body` document to these views, because the shared components already provide that wrapper.

An **id** identifies an individual HTML element. JavaScript will use `welcomeButton` and `welcomeMessage` to find the Home page elements. About does not need these elements.

When you create content with the **View** resource type, LifeTechOCMS automatically creates the content record, a page and a menu for that view. It also assigns the view to the page and menu.

You do not need to manually create a Home page and then attach Home.html to it as separate steps in this workflow.

### 13.2 What happens when you create a view

For the Home.html view created earlier:

1. LifeTechOCMS registers Home.html as View content.
2. It creates the page for that content.
3. It creates the associated menu entry.
4. It assigns the content to its page and menu.
5. The menu provides navigation to the page.
6. When the page opens, ContentLoadBody's dynamic loader displays the content assigned to that page.

The same process applies when you create About.html as View content.

### 13.3 Check the generated route before writing links

Open the generated page or menu settings and check its route. The beginner examples use /ThemeStarter/Home and /ThemeStarter/About. Use the actual generated route in your installation, including its capitalization, when writing navigation links.

For example, if Home's route is /ThemeStarter/Home, the Home link in Header should use that route. You can use the generated menu navigation or build your own navigation using the generated page addresses. Section 14 explains loading database-managed menus according to the current role.

### 13.4 Preview the generated pages

Open each generated page through its menu or the available Preview action. Check its theme settings, intended access permissions and publication status. Confirm that the shared components are in the right order and the view appears at the dynamic loader's position.

Automatic creation establishes the page, content and menu relationships. You can still review and adjust their settings through the backend when your design needs it.

### 13.5 Review publication and access settings

Automatic creation connects the records. Review who can visit the page and whether its content is published for those visitors. A published theme does not by itself give an anonymous visitor access to a restricted page.

**Expected result:** Home and About each have their own page and menu, and the loader displays the appropriate assigned view.

## 14 Load Menus for the Current User's Roles

LifeTechOCMS stores navigation menus in the database. Theme developers can request the menus permitted for the current user, then display them with their own navigation design. Use the general endpoint for menus across packages, or add packageName to filter by a named package:

```text
GET /menus/is-navigation
GET /menus/is-navigation?packageName=ThemeStarter
```

### 14.1 Understand token and session identification

The request can carry a Bearer token or use an existing login session. AppCore processes the available authentication before the menu method runs. The method reads role IDs from `LtSession::get('ltUrid')`. If no role value is available, it uses the Anonymous role. Multiple role IDs are separated and trimmed before the role filtering is applied.

A request without a Bearer token is not automatically an Anonymous request. A logged-in user may already have a session. The backend determines role permissions. Do not send role IDs. Omit packageName to obtain all permitted navigation menus, or supply it to restrict the result to that package; the role checks still apply.

### 14.2 Prepare the API and site addresses

Place these declarations inside a theme content file processed as PHP, before the menu functions:

```php
<script>
const BASE_URL = <?= json_encode(ApiTokenDetails::backEndBaseUrl()); ?>;
const siteHostAddress = <?= json_encode(ltSiteHostAddress()); ?>;
</script>
```

| Variable | Purpose |
| --- | --- |
| BASE_URL | Backend API base address used to request menus |
| siteHostAddress | Site address used to build internal navigation links |
| LW_TOKEN | Current user's token, when already supplied by your authentication code |

`json_encode()` converts PHP values into JavaScript string values safely. The examples below are JavaScript: put them inside a script element after these declarations, or in your loaded JavaScript content. Declare shared constants only once.

### 14.3 Load menu data without HTML or CSS

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

| Syntax | Explanation |
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

### 14.4 Inspect data before rendering

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

### 14.5 Understand the response fields

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

| Field | Meaning |
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

### 14.6 Display menus with plain HTML

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

`textContent` displays menu labels as text. Internal routes are appended to the site address, preserving a site installation subfolder. External entries use their complete HTTP or HTTPS URL. This beginner example limits destinations to those protocols.

`buildMenuList()` calls itself for each set of children. This is recursion: the same function renders the parent list, child lists and deeper levels. All lists are visible; add dropdown interaction separately if your design needs it.

### 14.7 Connect loading and rendering

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

When LW_TOKEN is already available, use `initialiseNavigation(LW_TOKEN)` instead of the final call. To filter the displayed navigation, use `initialiseNavigation('', 'ThemeStarter')` with an existing session, or `initialiseNavigation(LW_TOKEN, 'ThemeStarter')` with a token. Choose one initialization call. With the supplied data, ThemeBlog appears as the parent and Blog.html appears beneath it. Blog opens the configured page in a new tab.

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

### 14.8 Optional PHP rendering

PHP can render menus with foreach if the role-filtered data is obtained on the server before the page is rendered. PHP cannot loop over data fetched later by browser JavaScript. A server-side API request must carry the appropriate user identity; it does not automatically inherit the browser's session.

The following rendering-only example assumes `$menuResponse` already holds the decoded response as a PHP array. The server-side loading call must use your platform's supported helper or service.

```php
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

### 14.9 Test roles and distinguish the two loaders

Test a visitor with no login, a user with an existing session, and a user sending a valid Bearer token. Check nested links, targets and the page destinations. Menu visibility does not replace page or API authorization.

| Loader | Responsibility |
| --- | --- |
| /menus/is-navigation | Return navigation menus permitted for the current user's roles across packages |
| /menus/is-navigation?packageName=ThemeStarter | Return permitted navigation menus filtered to ThemeStarter |
| dddm::loadDynamicContent() | Display theme, module or plugin content assigned to the current page |

A menu directs the visitor to a page. The dynamic content loader displays that page's assigned content. Developers can add their own classes, icons and navigation interactions without changing the data loader.

**Expected result:** the theme loads role-filtered menu data and displays it using a separate renderer.

## 15 Understand the Default Layout and Custom Layouts

LifeTechOCMS offers two ways to arrange a page's design: default components that together form the theme's default layout, and a separate custom Layout content item assigned to selected pages.

### 15.1 Default components form the default layout

Component content has an optional `is_theme_default` field with Yes or No. All components set to Yes automatically form the theme's default layout for new pages. You do not need to write a separate Layout content file for this default composition.

| Component | is_theme_default | Purpose |
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

### 15.3 Create custom Layout content

A custom layout is a content item created with the Layout resource type. The developer writes its structure and imports the components it needs with ltImport(). Use it when selected pages need a different arrangement, such as a member dashboard with a sidebar.

Create these additional content items in ThemeStarter:

| Content name | Resource type | Additional path | Is Theme Default |
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

Use the actual generated route for MemberDashboard. You can replace this teaching link with the role-based menu renderer in section 14.

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

```php
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

### 15.4 Add your own layout styling

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

### 15.5 Assign pages to the custom layout

1. Create and register MemberLayout.html as Layout content.
2. Open the layout assignment controls in the theme development backend.
3. Assign MemberDashboard and the other intended member pages to MemberLayout.html.
4. Review each page's content publication and access roles.
5. Preview the pages and confirm the document, header, sidebar and assigned content appear once.

Public pages can continue using the theme's default components. For pages assigned to the custom layout, inspect the resulting composition so imported TopHeader and Footer are not duplicated by separate page assignments, and the content loader runs once.

Components imported inside a custom layout are controlled by its code. Unpublishing a separate page assignment does not remove an explicit ltImport() call from that layout. To change those imported components, edit the layout's imports or the imported content.

### 15.6 Compare the two approaches

| Default layout from components | Custom Layout content |
| --- | --- |
| Components marked is_theme_default = Yes form the composition | A Layout content file defines the composition |
| Automatically included for new pages | Assigned to the pages that need it |
| Individual component assignments can be unpublished per page | Imported components are controlled by the layout code |
| Useful for a shared design with per-page adjustments | Useful for a different arrangement, such as a member dashboard |

A separate Layout content item is optional because default components already provide the theme's default layout.

**Expected result:** you understand both layout approaches and can assign the member layout to its intended pages.

## 16 Import Content or Load Content

Importing means reusing an existing content item inside another content item. For example, a layout can include a sidebar component, and a header can load a stylesheet.

There are two approaches: **import registered content with ltImport**, or **load content files through direct or CDN links**.

### 16.1 Method 1 Import registered content with ltImport

Provide the package name and registered content filename:

```php
<?php ltImport('ThemeStarter', 'Header.html'); ?>
```

`ThemeStarter` identifies the package. `Header.html` identifies the registered content. LifeTechOCMS uses the registration to locate its resource folder and additional path, so you do not include those folders in this call.

The package is explicitly named. It does not have to be the default theme. This makes it possible to reuse content from a named package in another package's interface.

| Resource type | Example use |
| --- | --- |
| Component | Include a reusable header, footer or sidebar |
| View | Include a particular registered interface |
| Layout | Include a registered wrapper where appropriate |
| Asset | Include registered CSS or JavaScript |

Import a component:

```php
<?php ltImport('ThemeStarter', 'MemberSidebar.html'); ?>
```

Import plain CSS inside style tags:

```php
<style>
    <?php ltImport('ThemeStarter', 'Style.css'); ?>
</style>
```

Import plain JavaScript inside script tags:

```php
<script>
    <?php ltImport('ThemeStarter', 'Script.js'); ?>
</script>
```

If the content already contains its own style or script tags, import it directly without adding another pair. Avoid importing a complete document layout inside another complete document, since that can duplicate the HTML wrapper.

### 16.2 Method 2 Load content through direct or CDN links

Content can come from any resource folder. Choose the loading method according to how the file should be used, rather than assuming all loaded files are assets.

Direct linking tells the browser to request a file at its address. Use a link element for CSS, a script element with src for JavaScript, and an img element for an image.

The package path helper stops at the **parent folder containing the packages**. The developer explicitly adds the package folder name, subfolders and filename. It does not automatically choose the default theme.

This makes the address independent of which theme is currently the default. Another theme, module or plugin can reference an asset from the named package.

The address has these parts:

```text
Parent folder URL + package folder name + subfolders + filename
```

The following working pattern uses the plugins parent path helper:

```php
<script src="<?= ltPluginPath() ?>/PlgMyTailwind/Services/tailwind_4_cdn.js"></script>
```

| Part | Purpose |
| --- | --- |
| ltPluginPath() | Supplies the URL up to the plugins parent folder |
| PlgMyTailwind | Explicitly selects the package folder |
| Services | Selects a subfolder in that package |
| tailwind_4_cdn.js | Selects the JavaScript file |

For theme files, apply the same principle using the themes parent path helper, then append `/ThemeStarter/Assets/css/Style.css` or `/ThemeStarter/Assets/js/Script.js`.

Use ltThemePath() to obtain the themes parent URL, then explicitly add your package name and the path to the asset:

```php
<link rel="stylesheet"
      href="<?= ltThemePath() ?>/ThemeStarter/Assets/css/Style.css">
<script src="<?= ltThemePath() ?>/ThemeStarter/Assets/js/Script.js"></script>
```

ltThemePath() stops at the themes directory. It does not add ThemeStarter or choose the default theme. Explicitly naming ThemeStarter allows another package to reference its assets even when ThemeStarter is not the default theme.

Similarly, ltModulePath() supplies the modules parent URL and ltPluginPath() supplies the plugins parent URL. Add the intended package name and remaining file path yourself.

Direct linking is suitable for browser-ready files. It does not render PHP components, views or layouts into the current page. Assets containing PHP instructions need the appropriate LifeTechOCMS content processing.

A CDN link follows the same browser-loading principle but points to a CDN-hosted file. Inline CSS or JavaScript means code written inside style or script tags; it is different from linking an external file.

### 16.3 Which method should you use

| Requirement | Approach |
| --- | --- |
| Include a registered component, view or layout | ltImport |
| Include registered CSS or JavaScript in the page output | ltImport with the appropriate tags |
| Load browser-ready CSS, JavaScript or an image by address | Direct URL |
| Reference a package regardless of the default theme | Name the package explicitly in either approach |

**With ltImport, supply the package name and registered filename. With direct linking, supply the package name and full remaining path to the file.**

## 17 Use Site Information and Helper Functions

### 17.1 Other helpers used in your theme

| Function or method | Purpose |
| --- | --- |
| ltSiteName() | Display the configured site name |
| ltSiteUrl() | Build site page links |
| ltSiteHostAddress() | Build navigation or redirect addresses |
| dddm::loadDynamicContent() | Display content assigned to the current page |
| ApiTokenDetails::backEndBaseUrl() | Find the configured backend API address |
| ApiTokenDetails::tokenName() | Find the application's token storage key |
| ltPluginPath() | Find the plugins parent URL for explicit file links |

When placing a PHP string into JavaScript, use json_encode so special characters are represented correctly:

```php
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

### 17.2 Use more site configuration helpers

Site configuration helpers let you use saved website information without hardcoding it into each content file. Update the site settings, and your theme can display the configured values through these helpers.

| Helper | Returned information |
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

```php
<p><?= htmlspecialchars(ltSiteTitle(), ENT_QUOTES, 'UTF-8') ?></p>
```

Display contact information in a footer:

```php
<p>Email: <?= htmlspecialchars(ltSiteEmail(), ENT_QUOTES, 'UTF-8') ?></p>
<p>Phone: <?= htmlspecialchars(ltSitePhone(), ENT_QUOTES, 'UTF-8') ?></p>
<p><?= htmlspecialchars(ltSiteCopyright(), ENT_QUOTES, 'UTF-8') ?></p>
```

For a logo stored as a filename in the installation's uploads folder, the documentation demonstrates this pattern:

```php
<img src="<?= htmlspecialchars(
    rtrim(ltSiteUrl(), '/') . '/uploads/' . ltSiteLogo(),
    ENT_QUOTES, 'UTF-8'
) ?>" alt="Website logo">
```

Check how your logo setting is stored before adding a directory: a stored full URL or path should not have another uploads prefix added to it.

### 17.3 Understand the URL and environment helpers

| Helper | Purpose |
| --- | --- |
| isHttps() | Returns whether the request is using HTTPS |
| ltDomain() | Returns the domain name |
| ltBaseUrl() | Returns the domain with its protocol |
| ltSiteUrl() | Returns the root URL of the LifeTechOCMS installation |
| ltThemePath() | Returns the themes parent URL |
| ltModulePath() | Returns the modules parent URL |
| ltPluginPath() | Returns the plugins parent URL |

Use ltSiteUrl() for installation-relative page links. Use a package parent helper for direct asset links and explicitly add the package folder name. These functions provide addresses; they do not replace content registration or page assignment.

Full helper reference: https://www.lifetech.host/hubs/Docs#ltsiteinfo-and-site-helper-functions

## 18 Connect Theme Views to Backend APIs

The theme presents data; the backend module supplies it. A theme that includes a blog interface does not by itself create blog storage or API routes.

This example uses an endpoint demonstrated in ThemeBlog: `blogs/posts/widget?limit=6&type=popular`. Use it only where the corresponding blog backend is installed and configured. Otherwise substitute a working endpoint from your module.

### 18.1 Understand the API terms

| Term | Meaning | Example |
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

### 18.2 Create a Posts view

Create `Posts.html` as View content with additional path `/` and Is Theme Default set to No. Paste:

```php
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

Creating this View content automatically creates its associated page and menu. Check the generated route, such as `/ThemeStarter/Posts`, and open it through its menu or Preview.

### 18.3 Read what the code does

First, PHP supplies the backend base address. The browser then calls `fetch()` to request the endpoint. `await` waits for the response. `response.ok` checks HTTP success; `responseCategory` checks the application's result. Finally, the code creates a list item for each returned post.

The loading text gives feedback while the request runs. An empty result displays a useful message. A failed request displays its error. Using `textContent` renders post titles as text rather than executable HTML.

### 18.4 Send a token for a protected request

ThemeBlog's administration views use the Authorization header. This example prepares those headers; it does not invent a protected endpoint:

```php
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

Use these headers only with the intended trusted backend and the module's documented request. Backend permissions must still decide what the caller can do. For a JSON submission, the module may require `Content-Type: application/json` and a body built with `JSON.stringify()`; follow its actual method and field names.

## 19 Edit Theme Package

### 19.1 Update package information

1. Return to the Themes Development list.
2. Find ThemeStarter and choose **Edit Theme Package**.
3. Update the description or version using the available fields.
4. Save and confirm the details in the list.

This edits the package information. To change Header.html's code, use its content editor instead.

### 19.2 Maintain the version and dependencies

For example, after a reviewed update you might change the theme version from `v1.0.0` to `v1.0.1`. Use three numeric parts with a leading v, and use the same version for the GitHub release tag. Keep the generated manifest and panel information consistent using the supported editing and export workflow.

Record required packages accurately. A blog view that calls a module endpoint needs that module installed; the theme does not create the endpoint by itself.

### 19.3 Write a useful README

Include the theme's purpose, installation instructions, required packages, intended core compatibility, available pages and configuration steps. Explain any logo, contact or API settings the next developer needs.

**Expected result:** another developer can identify the release and understand what it requires.

## 20 Previewing a Theme

### 20.1 Open Preview

1. Open the Themes Development list.
2. Locate ThemeStarter.
3. Select **Preview**.
4. Inspect the page and refresh it after saving code changes.

Preview is useful while developing; access and session rules still apply to the pages you open.

### 20.2 Check the first working result

Use the theme's Preview action or open the configured page through LifeTechOCMS. Publish the theme and assign it to the required pages when ready; select it as the site's default theme if you want it to be the site's main design.

Confirm these results:

- Home displays the shared header, Home card and footer.
- Clicking the welcome button displays the message.
- About uses the same design but displays its own text.
- The navigation links open their configured routes.
- The page remains readable on a narrow screen.

**You have completed a basic theme.** Sections 15 and 18 extend it with a custom layout and backend data.

### 20.3 Test pages and browser behaviour

Use Preview while developing. Check Home, About and any separate layout. Test links, the welcome button, narrow screens and API loading. In browser developer tools, Console shows JavaScript errors and Network shows request statuses.

Check that only one document wrapper and one dynamic insertion point appear in the chosen composition. For API views, test successful data, an empty response and a failed request.

**Expected result:** you have verified the design before using the publishing actions.

## 21 Publishing a Theme

### 21.1 Understand publishing

Publishing makes a theme available for frontend use. Installing or creating a theme does not replace the site's design automatically.

### 21.2 Publish through the panel

1. Locate the completed theme in Themes Development.
2. Use its **Publish** control.
3. Confirm the panel shows it as published.
4. Choose whether to apply it to selected pages or set it as default, as explained in sections 22 and 23.

### 21.3 Check content publication separately

Theme publication, page content publication and page access are different settings. Confirm all three when reviewing a page. If the header appears but the view does not, inspect ContentLoadBody and the assigned content's publication rather than repeatedly publishing the theme.

**Expected result:** the theme is available to apply, and its intended content can be displayed for the intended visitors.

## 22 Publish Theme to Page

### 22.1 When to use a page specific theme

Use this action when one or more pages need a different theme from the site's main design. For example, a campaign landing page may use ThemeStarter while the rest of the site uses another default theme.

### 22.2 Apply a theme to selected pages

1. Locate the published theme in Themes Development.
2. Open **Publish Theme to Page**, or the matching page assignment action.
3. Choose the intended existing page or pages using your panel's controls.
4. Save and open those pages to confirm their appearance.

The online documentation identifies the action but does not specify every current field. Use the page-selection controls in your installed panel.

### 22.3 Distinguish theme selection from View creation

Creating View content automatically creates its page and menu and connects the content. Publish Theme to Page selects the surrounding theme for a page; it is not a requirement to manually recreate those records.

**Expected result:** the selected pages use the chosen design while the site retains its configured default theme.

## 23 Set Theme as Default

### 23.1 What default means

The default theme is the site's main frontend design. Only one theme can hold default status at a time. This differs from Is Theme Default on an individual component: that component flag controls the theme's default page composition.

### 23.2 Select the default theme

1. Preview and publish the intended theme.
2. Find it in Themes Development.
3. Choose **Set Default** or **Set Theme as Default**.
4. Confirm that it is now identified as the default theme.
5. Open representative frontend pages and check their content, navigation and styling.

### 23.3 What happens to the previous default

The selected theme becomes the main design, and the previous theme loses default status. This does not mean the previous theme package has been deleted. Review pages with explicit theme selections separately.

| Setting | What it controls |
| --- | --- |
| Publish theme | Availability for frontend use |
| Set theme as default | Main site design |
| Publish theme to page | Design selected for particular pages |
| Is Theme Default on a component | Component membership in the default composition |

**Expected result:** one theme is identified as the default, and the site's ordinary frontend pages use the intended design.

## 24 Export Theme

### 24.1 Prepare the theme

Preview its pages, save all changes and update the README and version. Check that required packages are documented and that content imports use correct names.

### 24.2 Export through the panel

1. Open the theme's content area.
2. Choose **Export Theme**.
3. Download the resulting package and retain it as the version you intend to distribute.

Use **Export Theme** in the panel. A proper LifeTechOCMS export includes source files and registration records. This is how the supplied ThemeBlog and ThemeBrainDump packages combine presentation files with `Export/` metadata.

Add a useful README explaining installation, required modules, pages and theme configuration. The supplied READMEs are empty, so they do not yet provide installation guidance.

### 24.3 Understand what an export contains

The supplied exports combine source files with registration records such as content.json, page.json and menu.json. These records let the platform recognize the package's content and destinations. A ZIP containing only copied HTML files is not equivalent to a platform export.

### 24.4 Name the exported package

Use a filename beginning with Theme, such as `ThemeStarter.zip`, as required by the previous installation documentation. Share installation guidance and dependency information with the ZIP.

**Expected result:** you have a platform-exported theme package ready for backup or installation.

## 25 Installing a Theme

LifeTechOCMS provides two ways to install an existing theme: download an installation ZIP and upload it, or browse online from the backend and install the selected package.

### 25.1 Method 1 Download and upload the theme

1. Visit the LifeTechOCMS Marketplace, find the theme and download its installation ZIP. You can also use a theme ZIP exported from another LifeTechOCMS installation.
2. Sign in to the backend of the target installation.
3. Open **Packages → Themes Development**.
4. Select **Install Theme**.
5. Choose the downloaded or exported theme ZIP and complete installation.
6. Open the installed theme and preview its pages.

Use a clear package filename such as ThemeStarter.zip and a proper installation package. A ZIP of copied HTML files alone does not contain the content registrations and page records included in a LifeTechOCMS export.

### 25.2 Method 2 Browse Online from the backend

1. Sign in to your LifeTechOCMS backend.
2. Open **Packages → Themes Development**.
3. Select **Browse Online**.
4. Search for the existing theme you want.
5. Use its download/install option. LifeTechOCMS downloads and installs the package.
6. Open the installed theme and preview its pages.

This approach lets you discover and install the theme from inside the backend. The first approach is useful when you already have its installation ZIP or an export from another site.

### 25.3 Verify and choose how to use the theme

After either method, confirm that the theme's content items, pages and menu relationships are available. Install any required dependencies, check the actual routes on the target site, and preview the imported pages.

When ready, publish the theme. Then either set it as the site's default theme or apply it to selected pages. Installation makes a theme available; publishing and selecting its use are separate steps.

Check the theme's supported core versions before installing. Preserve its declared dependencies and release information when moving it between sites.

**Expected result:** the existing theme is installed, previewed and ready to publish and use.

## 26 Delete Theme

### 26.1 Check before deleting

Deleting removes the theme package permanently according to the online documentation. Export it first if you may need its code again. Review pages that use the theme and arrange an appropriate replacement.

If it is the current default, first publish and select another working default theme. The site must retain a default theme.

### 26.2 Delete through the panel

1. Open Themes Development.
2. Identify the exact theme package to remove.
3. Use its **Delete** action and review any confirmation shown by the panel.
4. Complete deletion only after checking the package name and replacement design.
5. Confirm the package is gone from the list and affected pages still work.

### 26.3 Check the result

Test the default frontend design and any pages previously using the deleted theme. The online guide does not describe every related-record cleanup rule; inspect remaining page and menu settings in your installation.

**Expected result:** the unwanted theme is removed and the site still has a working default design.

## 27 Security and Management Permissions

### 27.1 Backend management roles

Installing and deleting theme packages require privileged roles according to the existing documentation. Use a permitted backend account to manage packages. A visitor's permission to open a page is separate from a developer's permission to edit its theme.

### 27.2 Page access and API permissions

Review the intended visitor roles on each page. For protected API calls, send the required token and let the backend enforce permissions. Hiding a button in the theme does not authorize or block the corresponding backend action.

### 27.3 Site wide changes

Changing the default theme affects the main frontend design. Preview and test representative pages before applying it. Export the current theme if you need a restorable copy of its source and registrations.

### 27.4 Safe output and external assets

Use htmlspecialchars when displaying text in HTML, json_encode when supplying PHP values to JavaScript, and textContent for plain text returned by APIs. Choose asset URLs intentionally and confirm their availability in the browser's Network panel.

**Expected result:** package management, page access and backend authorization are understood as separate responsibilities.

## 28 Troubleshooting and Development Checklist

### 28.1 Solve common beginner problems

| Problem | Likely cause | What to check |
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
| New local file is absent in the panel | File has not been synced into the content records | Check its resource folder, then run Sync Files and inspect the registered item |

### 28.2 Final checklist

- Create the theme through the panel and preserve its generated metadata.
- Register content through Add Content, or create local files in the resource folders and run Sync Files.
- Check database-managed navigation using the menu loader or API for the intended visitor roles.
- Load plain CSS inside style tags and plain JavaScript inside script tags.
- Arrange document opening, header, dynamic loader and footer in order.
- Check the page, menu and assignments automatically created for each View content item.
- Build links with the site helper and that configured route.
- Use layouts when a page needs a different composition.
- Preview every page and install the modules required by API examples.
- Export through LifeTechOCMS when preparing the theme for another installation.

## 29 Example Themes and References

### 29.1 Inspect the supplied themes

Once ThemeStarter works, use the larger themes to see how the same ideas scale.

| What you want to learn | Example to inspect |
| --- | --- |
| Document opening and stylesheet import | ThemeBlog/Components/Top-header.html |
| Dynamic view loading | Either theme's Components/ContentLoadBody.html |
| Administration layout with imported components | ThemeBlog/Layouts/Admin-layout.html |
| Separate authentication design | ThemeBrainDump/Layouts/Auth/AuthLayout.html |
| Shared API address and token helpers | ThemeBlog/Assets/js/Script.js |
| A view that loads blog data | ThemeBlog/Views/Blog.html |
| Registered content types and subfolders | Either theme's Export/content.json |
| The distinction between filename and route | Either theme's Export/page.json |

### 29.2 Documentation references

Previous learning documentation: https://www.lifetech.host/hubs/Docs#theme-development

The updated folder names, resource types, registration fields and function calls are grounded in the supplied ThemeBlog and ThemeBrainDump packages. The beginner theme is a teaching example built from those patterns. Package-filtered menu loading, the four conventions, both installation methods and the default/custom layout explanation include the platform author's updated guidance. The view creation workflow and DDM terminology include the platform author’s corrections. Exact layout controls should be checked in the installed platform.

Site helper reference: https://www.lifetech.host/hubs/Docs#ltsiteinfo-and-site-helper-functions


