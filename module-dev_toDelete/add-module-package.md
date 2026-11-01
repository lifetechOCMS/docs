# Add a Module Package

[Previous](module-development-conventions.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](understand-module-folders-and-subfolders.md)

*Section: Getting started*

In the LifeTechOCMS module-development interface, choose **Add Module Package**, enter the required metadata, and submit the package.

## Naming checklist

- Package identifier: `MdStudent` (PascalCase with mandatory `Md` prefix).
- Namespace root: `Lt\Modules\MdStudent`.
- Package metadata: `package.json`; documentation: `README.md`.
- Generated route file: `Services/MdStudentRoutes.php`.

MdBlog's [`package.json`](https://github.com/adedayoAdetunji/MdBlog/blob/main/package.json) provides an existing reference with `packageName`, `packageType`, `version` and `dependsOn`. Do not assume example metadata values are valid for every release.

---

[Previous](module-development-conventions.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](understand-module-folders-and-subfolders.md)
