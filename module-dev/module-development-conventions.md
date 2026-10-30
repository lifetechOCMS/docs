# Module Development Conventions

[Previous](accessing-modules-development.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](add-module-package.md)

*Section: Getting started*

Follow the package and namespace patterns of the actual module rather than inventing new conventions. In MdBlog, the package is named `MdBlog` and its PHP classes use `Lt\Modules\MdBlog` namespaces.

- Controllers live under `Lt\Modules\MdBlog\Controllers`.
- Models live under `Lt\Modules\MdBlog\Models`.
- Services live under `Lt\Modules\MdBlog\Services`.
- Views are stored in `Views/`.
- Route definitions are in `Services/MdBlogRoutes.php`.

**Note:** MdBlog is a reference implementation; confirm naming and required metadata against the package tools in your installed LifeTech version.

---

[Previous](accessing-modules-development.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](add-module-package.md)
