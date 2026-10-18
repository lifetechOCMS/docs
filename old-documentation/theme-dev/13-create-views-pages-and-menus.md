# Create Views Pages and Menus

[Previous topic](12-add-the-compulsory-dynamic-content-loader.md) · [Contents](README.md) · [Next topic](14-load-menus-for-the-current-users-roles.md)

## On this page

- [Write the Home and About views](#write-the-home-and-about-views)
- [What happens when you create a view](#what-happens-when-you-create-a-view)
- [Check the generated route before writing links](#check-the-generated-route-before-writing-links)
- [Preview the generated pages](#preview-the-generated-pages)
- [Review publication and access settings](#review-publication-and-access-settings)

## Write the Home and About views

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

## What happens when you create a view

For the Home.html view created earlier:

1. LifeTechOCMS registers Home.html as View content.
1. It creates the page for that content.
1. It creates the associated menu entry.
1. It assigns the content to its page and menu.
1. The menu provides navigation to the page.
1. When the page opens, ContentLoadBody's dynamic loader displays the content assigned to that page.

The same process applies when you create About.html as View content.

## Check the generated route before writing links

Open the generated page or menu settings and check its route. The beginner examples use **/ThemeStarter/Home** and **/ThemeStarter/About**. Use the actual generated route in your installation, including its capitalization, when writing navigation links.

For example, if Home's route is **/ThemeStarter/Home**, the Home link in Header should use that route. You can use the generated menu navigation or build your own navigation using the generated page addresses.

## Preview the generated pages

Open each generated page through its menu or the available Preview action. Check its theme settings, intended access permissions and publication status. Confirm that the shared components are in the right order and the view appears at the dynamic loader's position.

Automatic creation establishes the page, content and menu relationships. You can still review and adjust their settings through the backend when your design needs it.

## Review publication and access settings

Automatic creation connects the records. Review who can visit the page and whether its content is published for those visitors. A published theme does not by itself give an anonymous visitor access to a restricted page.

**Expected result:** Home and About each have their own page and menu, and the loader displays the appropriate assigned view.

[Previous topic](12-add-the-compulsory-dynamic-content-loader.md) · [Contents](README.md) · [Next topic](14-load-menus-for-the-current-users-roles.md)
