# LifeTechOCMS Documentation

LifeTechOCMS is a PHP-based content management system and application framework for building websites, portals, APIs and business applications.

It brings content management and application development into one platform. Administrators manage pages, menus, users and access permissions through the backend, while developers extend the application through themes, modules and plugins.

## On this page

- [How the platform fits together](#how-the-platform-fits-together)
- [Choose your starting point](#choose-your-starting-point)
- [Development and deployment](#development-and-deployment)
- [Documentation areas](#documentation-areas)
- [Complete guide](#complete-guide)
- [Using this documentation](#using-this-documentation)

## How the platform fits together

| Part | Responsibility | Example |
| --- | --- | --- |
| Theme | Page presentation, reusable components and layouts | A public website design or member dashboard |
| Module | Application features and backend logic | Blog posts and their backend APIs |
| Plugin | Extensions and integrations | A supporting editor or frontend library |
| Page and content | Destinations and the registered content assigned to them | A page displaying an assigned theme view |
| Roles and permissions | Control access to the relevant pages and operations | Different access for visitors and signed-in users |

For example, a blog module can provide posts and backend APIs while a theme presents those posts to visitors. The same installation can support additional features, each with its own content and access requirements.

A theme's dynamic content loader displays the content assigned to the current page. This lets developers build a shared page design while using different theme, module or plugin content on individual pages.

## Choose your starting point

- **New to LifeTechOCMS?** Begin with [Getting Started](get-started/README.md) for requirements, installation and first-run guidance.
- **Managing a website?** Explore the [Backend Tutorial](backend-tutorial/README.md) for administration tasks.
- **Building an interface?** Follow [Theme Development](backend-development/theme-dev/README.md).
- **Building application features?** Follow [Module Development](backend-development/module-dev/README.md).
- **Looking up a helper or class?** Open [Functions and Classes](functions-and-classes/README.md).
- **Working with backend requests and responses?** Read [Request and Response Management](request-and-respond-management/README.md).

## Development and deployment

Start by checking the [installation and system requirements](get-started/README.md) for the LifeTechOCMS release you intend to use. Follow the documented setup before creating or installing packages.

Developers can work with the backend code editor or edit files in a local installation. Test pages through LifeTechOCMS so PHP helpers and the platform's content processing can run. A theme's source HTML file opened directly is not equivalent to its rendered application page.

Before moving a package to another installation, check its dependencies and supported core version. Use the documented export and installation workflows so source files and registration records travel together.

## Documentation areas

### GET STARTED

[Open contents](get-started/README.md)

### BACKEND TUTORIAL

[Open contents](backend-tutorial/README.md)

- [Site Information](backend-tutorial/site-information/README.md)
- [Life User Role](backend-tutorial/life-user-role/README.md)
- [Life Content](backend-tutorial/life-content/README.md)
- [Menu](backend-tutorial/menu/README.md)
- [Lifepage](backend-tutorial/lifepage/README.md)
- [User](backend-tutorial/user/README.md)
- [File Manager](backend-tutorial/file-manager/README.md)

### BACKEND DEVELOPMENT

[Open contents](backend-development/README.md)

- [Module Development](backend-development/module-dev/README.md)
- [Theme Development Overview](backend-development/theme-dev/README.md)

### FUNCTIONS AND CLASSES

[Open contents](functions-and-classes/README.md)

- [LtImport](functions-and-classes/ltimport/README.md)
- [LtAuth](functions-and-classes/ltauth/README.md)
- [Loading Dynamic Menus](functions-and-classes/loading-dynamic-menus/README.md)
- [CaseConverter](functions-and-classes/caseconverter/README.md)
- [LtValidator](functions-and-classes/ltvalidator/README.md)
- [LtSiteInfo and Site Helper Functions](functions-and-classes/ltsiteinfo-and-site-helper-functions/README.md)
- [LtSession](functions-and-classes/ltsession/README.md)

### REQUEST AND RESPOND MANAGEMENT

[Open contents](request-and-respond-management/README.md)

- [RESPONSE](request-and-respond-management/response/README.md)

## Complete guide

[Read the complete documentation](all-documentation.md)

## Using this documentation

Each guide has a README contents page and individual lesson files. Follow the listed learning order, or open a reference topic directly when you need a particular function or feature.

Lessons include four navigation positions at the top and bottom: **Previous · Main documentation · Guide contents · Next**. Longer lessons also include an **On this page** list. An unavailable Previous or Next position appears as plain text.

Filenames describe their topic without sequence numbers, allowing new lessons to be inserted without renaming the rest of the guide. Contributors should follow the [documentation conventions](documentation-conventions.md) and update affected links when adding or moving content.

The [LifeTechOCMS online documentation](https://www.lifetech.host/hubs/Docs) provides the published website edition. Check the relevant version and prerequisites when following examples.
