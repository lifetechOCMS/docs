# Add the Compulsory Dynamic Content Loader

[Previous](build-the-shared-theme-components.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-views-pages-and-menus.md)

## On this page

- [Add the loader to your theme](#add-the-loader-to-your-theme)
- [How does it work](#how-does-it-work)
- [Why is it necessary](#why-is-it-necessary)
- [How is this different from ltImport](#how-is-this-different-from-ltimport)
- [What if the page uses a separate layout](#what-if-the-page-uses-a-separate-layout)

Your theme provides the page design, including its header, navigation and footer. Each page also needs a place to display the content assigned to it.

The **dynamic content loader** provides that place. It loads and displays any **theme, module or plugin content assigned to the current page**, including multiple assigned content items.

## Add the loader to your theme

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

## How does it work

| **Page** | **Assigned content** | **What the loader displays** |
| --- | --- | --- |
| Home | Home view from a theme | The Home interface |
| Book Catalogue | Book listing content from a module | The book listing interface |
| A page using plugin content | Displayable content assigned from a plugin | That plugin's assigned content |

You do not rewrite the loader for each page. **The page's assignments determine what appears; the loader's position determines where it appears.**

## Why is it necessary

Assigning content to a page tells LifeTechOCMS what to display. The loader gives the theme an insertion point for that content. Without the loader in the resulting page composition, the shared header and footer may appear while the assigned page content is missing.

For our beginner theme, arrange TopHeader, Header, ContentLoadBody and Footer in that order. When Home is opened, the loader displays the assigned Home view. When a module page is opened, the same loader displays its assigned module content.

## How is this different from ltImport

ltImport() loads a specific registered item that you name:

```php
<?php ltImport('ThemeStarter', 'Header.html'); ?>
```

dddm::loadDynamicContent() loads the content assigned to the current page:

```php
<?php dddm::loadDynamicContent(); ?>
```

Use an import for a specific reusable item. Keep the dynamic loader where page-assigned theme, module or plugin content should appear.

## What if the page uses a separate layout

A separate layout also needs a dynamic insertion point. Place the same function call inside that layout where assigned content should appear. The default composition provides the loader through ContentLoadBody; an alternative layout can provide it directly. Check that the resulting composition does not load the same dynamic content twice.

Source: https://www.lifetech.host/hubs/Docs#add-the-compulsory-dynamic-content-loader

[Previous](build-the-shared-theme-components.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-views-pages-and-menus.md)
