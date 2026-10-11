# Understand the Default Layout and Custom Layouts

[Previous topic](14-load-menus-for-the-current-users-roles.md) · [Contents](README.md) · [Next topic](16-import-content-and-load-content.md)

## On this page

- [Default components form the default layout](#default-components-form-the-default-layout)
- [15.2 Unpublish individual components on a page](#152-unpublish-individual-components-on-a-page)
- [Create custom Layout content](#create-custom-layout-content)
- [Add your own layout styling](#add-your-own-layout-styling)
- [Assign pages to the custom layout](#assign-pages-to-the-custom-layout)
- [Compare the two approaches](#compare-the-two-approaches)

LifeTechOCMS offers two ways to arrange a page's design: default components that together form the theme's default layout, and a separate custom Layout content item assigned to selected pages.

## Default components form the default layout

Component content has an optional is_theme_default field with Yes or No. All components set to Yes automatically form the theme's default layout for new pages. You do not need to write a separate Layout content file for this default composition.

| **Component** | **is_theme_default** | **Purpose** |
| --- | --- | --- |
| TopHeader.html | Yes | Open the document and load shared styles |
| Header.html | Yes | Display the header and navigation |
| ContentLoadBody.html | Yes | Load the content assigned to the page |
| Footer.html | Yes | Display the footer and close the document |
| Announcement.html | No | Use only on pages that need it |

Arrange the default components in the intended display order: document opening, header, content loader, then footer. The panel may label the field Is Theme Default; exported content records use isThemeDefault.

## 15.2 Unpublish individual components on a page

Default components are published as independent content assignments on each new page. They are not statically combined inside one layout file. The owner can later unpublish a particular component on a particular page without changing its publication on other pages.

For example, a campaign landing page may unpublish Header.html while Home and About keep it. This changes the landing page's composition without editing a shared layout file.

Keep the dynamic content loader available wherever assigned page content should appear. Also preserve the required document opening and closing, and any files that supply the page's styles or scripts.

## Create custom Layout content

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

Use the actual generated route for MemberDashboard. You can replace this teaching link with the role-based menu renderer in section [Load menu data without HTML or CSS](14-load-menus-for-the-current-users-roles.md#load-menu-data-without-html-or-css).

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

## Add your own layout styling

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

## Assign pages to the custom layout

1. Create and register MemberLayout.html as Layout content.
1. Open the layout assignment controls in the theme development backend.
1. Assign MemberDashboard and the other intended member pages to MemberLayout.html.
1. Review each page's content publication and access roles.
1. Preview the pages and confirm the document, header, sidebar and assigned content appear once.

Public pages can continue using the theme's default components. For pages assigned to the custom layout, inspect the resulting composition so imported TopHeader and Footer are not duplicated by separate page assignments, and the content loader runs once.

Components imported inside a custom layout are controlled by its code. Unpublishing a separate page assignment does not remove an explicit ltImport() call from that layout. To change those imported components, edit the layout's imports or the imported content.

## Compare the two approaches

| **Default layout from components** | **Custom Layout content** |
| --- | --- |
| Components marked is_theme_default = Yes form the composition | A Layout content file defines the composition |
| Automatically included for new pages | Assigned to the pages that need it |
| Individual component assignments can be unpublished per page | Imported components are controlled by the layout code |
| Useful for a shared design with per-page adjustments | Useful for a different arrangement, such as a member dashboard |

A separate Layout content item is optional because default components already provide the theme's default layout.

**Expected result:** you understand both layout approaches and can assign the member layout to its intended pages.

[Previous topic](14-load-menus-for-the-current-users-roles.md) · [Contents](README.md) · [Next topic](16-import-content-and-load-content.md)
