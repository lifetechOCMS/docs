# Understand Module Folders and Subfolders

[Previous](add-module-package.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](module-content-and-resource-types.md)

*Section: Getting started*

MdBlog provides this verified folder layout:

```text
MdBlog/
├── Controllers/
├── Models/
├── Services/
│   └── MdBlogRoutes.php
├── Views/
├── Export/
├── ddm/
├── package.json
└── README.md
```

`Controllers/` receives dispatched requests, `Models/` defines database-facing classes, `Services/` holds business operations and route definitions, and `Views/` holds page templates. `Export/` contains exported module resources; `ddm/` contains data definition files.

Inspect [MdBlog's repository](https://github.com/adedayoAdetunji/MdBlog) for concrete examples.

---

[Previous](add-module-package.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](module-content-and-resource-types.md)
