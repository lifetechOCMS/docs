# Import Content and Load Content

[Previous](understand-the-default-layout-and-custom-layouts.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](use-site-information-and-helper-functions.md)

## On this page

- [Method 1 Import registered content with ltImport](#method-1-import-registered-content-with-ltimport)
- [Method 2 Load content through direct or CDN links](#method-2-load-content-through-direct-or-cdn-links)
- [Which method should you use](#which-method-should-you-use)

Importing means reusing an existing content item inside another content item. For example, a layout can include a sidebar component, and a header can load a stylesheet.

There are two approaches: **import registered content with ltImport**, or **load a browser-ready asset through its direct URL**.

## Method 1 Import registered content with ltImport

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

## Method 2 Load content through direct or CDN links

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

## Which method should you use

| **Requirement** | **Approach** |
| --- | --- |
| Include a registered component, view or layout | ltImport |
| Include registered CSS or JavaScript in the page output | ltImport with the appropriate tags |
| Load browser-ready CSS, JavaScript or an image by address | Direct URL |
| Reference a package regardless of the default theme | Name the package explicitly in either approach |

**With ltImport, supply the package name and registered filename. With direct linking, supply the package name and full remaining path to the file.**

Source: https://www.lifetech.host/hubs/Docs#import-content-and-load-content

[Previous](understand-the-default-layout-and-custom-layouts.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](use-site-information-and-helper-functions.md)
