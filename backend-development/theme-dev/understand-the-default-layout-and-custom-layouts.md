# Understand the Default Layout and Custom Layouts

[Previous](load-menus-for-the-current-users-roles.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](import-content-and-load-content.md)

## On this page

- [Understand how the layout is selected](#understand-how-the-layout-is-selected)
- [Create the automatic default layout](#create-the-automatic-default-layout)
- [Understand the fallback default components](#understand-the-fallback-default-components)
- [Create a custom layout for selected pages](#create-a-custom-layout-for-selected-pages)
- [Add your own styling](#add-your-own-styling)
- [Assign a custom layout through the backend](#assign-a-custom-layout-through-the-backend)
- [Prepare automatic custom layout assignments](#prepare-automatic-custom-layout-assignments)
- [Compare the layout approaches](#compare-the-layout-approaches)
- [Check the result](#check-the-result)

A layout controls the structure around the content assigned to a page. In the updated LifeTechOCMS workflow, Layouts/Default.html is selected automatically as the theme's default layout. Selected pages can use a different registered Layout content item, such as **MemberLayout.html.**

## Understand how the layout is selected

| **Page configuration** | **Layout used** |
| --- | --- |
| A page has a custom layout assignment | The assigned custom layout |
| No custom layout is assigned and the theme has Layouts/Default.html | Default.html automatically |
| No custom layout is assigned and the theme has no Default.html | Components marked Is Theme Default provide the fallback composition |

The filename **Default.html** has a specific purpose. Preserve its spelling and capitalization. Create and register it as Layout content in the theme's Layouts/ folder.

You do not need to assign **Default.html** separately to every page. It does not belong in **PendingLayouts.json**: that file is for custom layout assignments.

## Create the automatic default layout

In ThemeStarter, create this content item:

| **Content name** | **Resource type** | **Additional path** | **File location** |
| --- | --- | --- | --- |
| Default.html | Layout | / | Layouts/Default.html |

Use the existing registered components **TopHeader.html**, **Header.html** and **Footer.html**:

```html
<?php ltImport('ThemeStarter','TopHeader.html');?>
<?php ltImport('ThemeStarter','Header.html');?>

<main class="container" id="main-content">
     <?php dddm::loadDynamicContent();?>
</main>

<?php ltImport('ThemeStarter','Footer.html');?>
```

**TopHeader.html** opens the document and loads the shared styles. **Header.html** supplies the visible navigation. The dynamic loader displays the content assigned to the current page. **Footer.html** supplies the footer, shared scripts and document closing tags.

The main element, container class and main-content ID are design examples. The required dynamic loading instruction is:

```php
<?php dddm::loadDynamicContent();?>
```

This layout already calls the dynamic loader, so it does not also import **ContentLoadBody.html**. Keep one dynamic insertion point in the resulting composition.

When Home and About have no custom layout assignment, both automatically use this layout. Their assigned views supply the different page content.

## Understand the fallback default components

The component field Is Theme Default remains useful when there is no **Default.html**. Components marked Yes provide the fallback page composition, in the intended order:

| **Order** | **Component** | **Purpose** |
| --- | --- | --- |
| 1 | TopHeader.html | Open the document and load styles |
| 2 | Header.html | Display navigation |
| 3 | ContentLoadBody.html | Call the dynamic content loader |
| 4 | Footer.html | Display the footer and close the document |

In this fallback approach, default components are independent content assignments on each page. An owner can unpublish a component on one page without unpublishing it on another page. Preserve a complete document and a dynamic loader in the resulting composition.

With **Default.html**, components are imported by the layout's code. Unpublishing a separate page assignment does not remove an explicit ltImport() call. Edit the layout's imports to change its shared structure, or assign a custom layout to pages needing another design.

For the ThemeStarter example using **Default.html**, keep the imported components' Is Theme Default flags set to No. This makes the example use the layout explicitly rather than relying on fallback component assignments. The panel may label the component field Is Theme Default; exports use isThemeDefault.

## Create a custom layout for selected pages

A custom layout is also registered content. For example, a member dashboard needs a sidebar and member header while public pages use **Default.html.**

Create these items:

| **Content name** | **Resource type** | **Additional path** |
| --- | --- | --- |
| MemberLayout.html | Layout | / |
| MemberSidebar.html | Component | / |
| MemberHeader.html | Component | / |
| MemberDashboard.html | View | / |

Set the member components' Is Theme Default flags to No: they are imported only where needed.

In MemberSidebar.html, add:

```html
<h2>Member area</h2>
<navaria-label="Member navigation">
     <ahref="<?= htmlspecialchars(
         rtrim(ltSiteUrl(), '/') . '/ThemeStarter/MemberDashboard',
         ENT_QUOTES, 'UTF-8'
     ) ?>">Dashboard</a>
</nav>
```

Use the actual generated page route in your installation. The [role-based menu loader](load-menus-for-the-current-users-roles.md) can replace this static navigation example.

In MemberHeader.html, add:

```html
<h1>Member dashboard</h1>
In MemberDashboard.html, add:
<section class="card">
     <h2>Your overview</h2>
     <p>This content appears inside the member layout.</p>
</section>
```

In MemberLayout.html, add:

```html
<?php ltImport('ThemeStarter', 'TopHeader.html'); ?>

<div class="member-layout">
     <aside class="member-sidebar">
         <?php ltImport('ThemeStarter','MemberSidebar.html');?>
     </aside>

     <div class="member-content">
         <headerclass="member-header">
             <?php ltImport('ThemeStarter','MemberHeader.html');?>
         </header>

         <main class="member-body">
             <?php dddm::loadDynamicContent();?>
         </main>
     </div>
</div>

<?php ltImport('ThemeStarter','Footer.html');?>
```

This layout imports its own components and provides its own dynamic insertion point. It does not import **Default.html** or **ContentLoadBody.html**. Several pages can share MemberLayout while the loader displays each page's assigned content.

## Add your own styling

Add this optional CSS to the shared Style.css content:

```css
.member-layout { display: flex;min-height: 70vh; }
.member-sidebar { width: 220px;padding: 24px;background: #e2e8f0; }
.member-content { flex: 1;min-width: 0; }
.member-header,.member-body { padding: 24px; }

@media (max-width: 640px) {
     .member-layout { display: block; }
     .member-sidebar { width: auto; }
}
```

The class names and CSS are examples. Use your own styles or framework while keeping the imports and dynamic loader in the correct positions.

## Assign a custom layout through the backend

1. Create or sync the layout and its components so they are registered content.
1. Open the layout assignment controls in the theme development backend.
1. Assign MemberDashboard to **MemberLayout.html.**
1. Review the page's content publication and access roles.
1. Preview the page and confirm that the member layout and assigned content appear once.

Home, About and other pages without custom assignments continue using **Default.html** automatically. Selecting a layout controls presentation; it does not grant access to the page or its backend APIs.

## Prepare automatic custom layout assignments

The updated workflow uses two application storage files:

| **File** | **Purpose** |
| --- | --- |
| /Storage/Layouts/PendingLayouts.json | Holds custom layout mappings waiting to be applied |
| /Storage/Layouts/AppliedLayouts.json | Records mappings processed by the platform |

These paths refer to the application's storage area. Theme layout source files still belong in the theme's Layouts/ folder.

A pending mapping identifies a custom layout, the target content and the package containing the layout:

```json
[
     {
         "layoutName":"MemberLayout.html",
         "contentName":"MemberDashboard.html",
         "layoutPackageName":"ThemeStarter"
     },
     {
         "layoutName":"DynamicMenuLayout.html",
         "contentName":"DynamicMenuDemo.html",
         "layoutPackageName":"ThemeStarter"
     }
]
```

| **Key** | **Meaning** | **Example** |
| --- | --- | --- |
| layoutName | Registered custom Layout content filename | MemberLayout.html |
| contentName | Target content filename, including its extension | MemberDashboard.html |
| layoutPackageName | Package containing the layout | ThemeStarter |

The second mapping is optional and assumes **DynamicMenuLayout.html** and **DynamicMenuDemo.html** have also been created and registered. Remove it when using only the member example.

Use exact registered names. **MemberDashboard.html** is a content filename; it is not the page route **/ThemeStarter/MemberDashboard**.

After the required content has been registered, the platform's pending layout processing applies the custom assignments and records processed mappings in **AppliedLayouts.json**. This supports automatic assignment without repeating the backend assignment clicks for each prepared mapping. Use the pending processing supported by your installed core version; do not add an invented function call or endpoint to the theme.

Do not add Home or About mappings to **Default.html**. Default selection already handles pages without a custom assignment. Do not manually mark mappings as applied to bypass processing; inspect the resulting assignments and preview the pages instead.

When preparing JSON, keep a valid array with double-quoted strings and no comments or trailing commas. Preserve unrelated mappings already present in the storage files.

## Compare the layout approaches

| **Approach** | **When it is used** | **How components are controlled** |
| --- | --- | --- |
| Default.html | Automatically for pages without a custom layout assignment | Imports in Default.html |
| Custom layout | For pages assigned to that layout, through the backend or pending mappings | Imports in the custom layout |
| Default components | Fallback when Default.html is absent and no custom layout is assigned | Independent component publication on each page |

## Check the result

| **Page** | **Custom mapping** | **Expected layout** |
| --- | --- | --- |
| Home | None | Default.html automatically |
| About | None | Default.html automatically |
| MemberDashboard | MemberLayout.html | MemberLayout.html |
| DynamicMenuDemo, when included | DynamicMenuLayout.html | DynamicMenuLayout.html |

1. Confirm layouts, components and views are registered with the correct names and resource types.
1. Open Home and About and check that the default layout appears automatically.
1. Open each custom-layout page and check its assigned layout.
1. If a mapping has not taken effect, inspect pending processing and the registered filenames; check page access and content publication separately.
1. Confirm one document wrapper, one header/footer arrangement and one dynamic loader in the resulting page.
1. Check styles, scripts, navigation and narrow-screen display.

**Expected result:** ordinary pages automatically use Default.html, selected pages use their custom layouts, and default components remain the fallback when **Default.html** is absent.

Source: https://www.lifetech.host/hubs/Docs#understand-the-default-layout-and-custom-layouts

[Previous](load-menus-for-the-current-users-roles.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](import-content-and-load-content.md)
