# Theme Development Overview

Previous · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](accessing-themes-development.md)

## On this page

- [What a theme does](#what-a-theme-does)
- [Requirements and testing environment](#requirements-and-testing-environment)
- [How to use this guide](#how-to-use-this-guide)
- [Key terminology](#key-terminology)

This guide teaches you how to create and manage a LifeTechOCMS theme. We build ThemeStarter with Home and About views, shared components, CSS and JavaScript, then add an optional dashboard layout and a backend API example.

## What a theme does

A theme supplies the presentation of a website: its document structure, visible navigation, styling and placement of assigned content. A module can supply application features and data while the theme provides the surrounding design. Content assigned from themes, modules or plugins appears through the dynamic loader.

## Requirements and testing environment

You need a working LifeTechOCMS installation, access to its administration panel, and basic knowledge of HTML. CSS changes appearance; JavaScript adds browser behaviour; PHP runs on the server and lets a theme call LifeTechOCMS functions.

Write theme content in the LifeTechOCMS code editor, or edit the corresponding files in your local LifeTechOCMS installation. Open the theme through LifeTechOCMS when testing: opening an HTML file directly on your computer will not run its PHP helpers.

## How to use this guide

Follow sections [Accessing Themes Development](accessing-themes-development.md) to [Create Views Pages and Menus](create-views-pages-and-menus.md) to build your first theme.

Section [Load Menus for the Current Users Roles](load-menus-for-the-current-users-roles.md) adds role-based menus and section [Understand Default Components and Alternative Layouts](understand-the-default-layout-and-custom-layouts.md) explains alternative layouts. Sections [Import Content and Load Assets](import-content-and-load-content.md) to [Connect Theme Views to Backend APIs](connect-theme-views-to-backend-apis.md) cover imports, helpers and APIs; sections [Edit Theme Package](edit-theme-package.md) to [Security and Management Permissions](security-and-management-permissions.md) cover management actions. Use a section title such as 'How does it work' when recording an observation.

The snippets use ThemeStarter consistently. ThemeNova and ThemeStarter follow the same confirmed package and content naming conventions; this guide does not require ThemeNova to be installed. The CSS is a small teaching example, and the loader can work with your chosen styling framework.

## Key terminology

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

Source: https://www.lifetech.host/hubs/Docs#theme-development-overview

Previous · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](accessing-themes-development.md)
