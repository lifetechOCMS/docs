# Understand Module Folders and Subfolders

[Previous](add-module-package.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](module-content-and-resource-types.md)

*Section: Getting started*

The existing [MdBlog module](https://github.com/adedayoAdetunji/MdBlog) illustrates how LifeTechOCMS organizes module resources.

```text
MdBlog/
├── Controllers/
├── ddm/
├── Export/
├── Models/
├── Services/
│   └── MdBlogRoutes.php
├── Views/
├── LICENSE
├── package.json
└── README.md
```

| Resource | Responsibility |
|---|---|
| `Controllers/` | Request handlers, e.g. `TbBlogCategoryController.php` |
| `Models/` | Database-facing classes, e.g. `TbBlogCategory.php` |
| `Services/` | Business Services and automatically created module routes |
| `Views/` | Presentation templates |
| `ddm/` | Module data-definition resources |
| `Export/` | Export-related module resources |

The folder structure belongs in this lesson rather than in Module Development Conventions. Consult your installed version before assuming all optional resources are required.

---

[Previous](add-module-package.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](module-content-and-resource-types.md)
