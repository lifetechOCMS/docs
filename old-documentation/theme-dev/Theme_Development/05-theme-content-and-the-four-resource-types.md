# Theme Content and the Four Resource Types

[Previous topic](04-add-theme-package.md) · [Contents](README.md) · [Next topic](06-understand-theme-folders-and-subfolders.md)

## On this page

- [Component content](#component-content)
- [View content](#view-content)
- [Layout content](#layout-content)
- [Asset content](#asset-content)
- [How these types work together](#how-these-types-work-together)

In LifeTechOCMS, **content** is an individual item you create and register inside a package. A header, a Home interface, a dashboard wrapper and a stylesheet are all content. You select a **resource type** to describe the item's job and determine its folder.

## Component content

A component is a reusable part of the design. For example, Header.html displays navigation and Footer.html displays the footer. The same component can appear on several pages, so one edit can update a shared part of the design.

Component files belong in Components/. A simple component might contain:

```html
<header>
	<p>Welcome to our website</p>
</header>
```

Components marked Is Theme Default form the theme's default page composition. ContentLoadBody is a component whose job is to load the content assigned to each page.

## View content

A view is the interface displayed for a page, such as Home, About or a book catalogue. View files belong in Views/.

```html
<section>
	<h1>About us</h1>
	<p>Learn about our organisation.</p>
</section>
```

When you create content with the View resource type, LifeTechOCMS automatically creates its **content record, page and menu**, and assigns the view to its page and menu. The menu leads visitors to that page; the dynamic content loader displays the assigned view there. You do not need to create and connect these records manually for this workflow.

## Layout content

A layout arranges reusable components around dynamic content. Layout files belong in Layouts/. For example, an administration layout can place a sidebar beside the current view:

```html
<div>
	<?php ltImport('ThemeStarter', 'DashboardSidebar.html'); ?>
	<?php dddm::loadDynamicContent(); ?>
</div>
```

The wrapper and styling are your choice. A separate layout is optional when default components already provide the required design. Use another layout when views need a different arrangement.

## Asset content

An asset supplies supporting styles, scripts or other design resources. Asset files belong in Assets/, often in subfolders such as css/ and js/.

```css
.page-title {
		color: #155e75;
}
```

This stylesheet is asset content. An HTML element with class page-title can use its styling once the stylesheet is loaded. Assets can be imported as registered content or loaded through an appropriate direct file URL, as explained later.

## How these types work together

| **Item** | **Resource type** | **Its job** |
| --- | --- | --- |
| Header.html | Component | Shared navigation |
| Home.html | View | Home page interface |
| DashboardLayout.html | Layout | Alternative arrangement around a view |
| Style.css | Asset | Colours, spacing and other styles |

A resource type describes the content's purpose; it is different from its extension. Both a component and a view can be .html files. Choose the resource type according to the item's job.

![image](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/92c1d75ea0ee501dbb9f24387ff8353b.png)

[Previous topic](04-add-theme-package.md) · [Contents](README.md) · [Next topic](06-understand-theme-folders-and-subfolders.md)
