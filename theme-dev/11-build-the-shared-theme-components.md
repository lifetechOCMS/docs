# Build the Shared Theme Components

[Previous topic](10-edit-or-update-existing-theme-content.md) · [Contents](README.md) · [Next topic](12-add-the-compulsory-dynamic-content-loader.md)

## On this page

- [Add the stylesheet](#add-the-stylesheet)
- [Create the document opening component](#create-the-document-opening-component)
- [Understand ltSiteName](#understand-ltsitename)
- [Understand ltImport](#understand-ltimport)
- [Create the visible header and navigation](#create-the-visible-header-and-navigation)
- [Add JavaScript and the footer](#add-javascript-and-the-footer)
- [Know whether your asset already contains tags](#know-whether-your-asset-already-contains-tags)

## Add the stylesheet

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

## Create the document opening component

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

## Understand ltSiteName

ltSiteName() returns the configured site name. It allows a visitor-facing title to follow the site's settings instead of a name hardcoded into the theme.

**<?= ... ?>** is PHP's short echo syntax: it outputs the expression's value into the HTML. htmlspecialchars() is a PHP function that safely displays text in HTML; it is not a LifeTechOCMS-specific function.

## Understand ltImport

```php
<?php ltImport('ThemeStarter', 'Style.css'); ?>
```

ltImport() loads registered content. In the supplied themes, it accepts a package name and a content filename. Here, ThemeStarter identifies the package and Style.css identifies the asset.

Notice that the call uses Style.css, not **Assets/css/Style.css**. The content registration records its resource type and additional path. Use exact spelling and capitalization, and choose distinct filenames within a package.

## Create the visible header and navigation

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

ltSiteUrl() supplies the base used for links in the provided themes. rtrim(..., '/') removes an ending slash before adding the route. Check the automatically generated Home and About routes in section [Create Views Pages and Menus](13-create-views-pages-and-menus.md#create-views-pages-and-menus) before using them in your links.

An href is the destination of a link**.** It should refer to the configured page route, not the view's filesystem path. Do not link visitors directly to **Views/Home.html**.

## Add JavaScript and the footer

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

## Know whether your asset already contains tags

Our Script.js contains JavaScript only, so Footer supplies [[script]] tags. ThemeBlog's supplied Script.js already contains [[script]] tags and PHP helper calls, so that asset is imported directly instead:

```php
<?php ltImport('ThemeBlog', 'Script.js'); ?>
```

Do not wrap an asset that already contains [[script]] tags inside another [[script]] element. Similarly, our stylesheet contains CSS only, so TopHeader provides [[style]] tags.

When an asset contains PHP, load it through LifeTechOCMS's registered content processing. A direct request for an ordinary .js file does not normally execute PHP embedded in it.

[Previous topic](10-edit-or-update-existing-theme-content.md) · [Contents](README.md) · [Next topic](12-add-the-compulsory-dynamic-content-loader.md)
