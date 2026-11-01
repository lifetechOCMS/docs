# Configure Module Dependencies

[Previous](sync-module-files.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](publishing-and-unpublishing-a-module.md)

*Section: Managing module content*

MdBlog's documented `package.json` declares a dependency on `MdLt` using a `dependsOn` array.

```json
{
  "packageName": "MdBlog",
  "packageType": "module",
  "dependsOn": [{"packageName": "MdLt", "version": "1.3.0"}]
}
```

This is a shortened example from MdBlog's README, not a complete package manifest. Match the dependency version to the framework version you actually support and verify installation behavior before publishing.

---

[Previous](sync-module-files.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](publishing-and-unpublishing-a-module.md)
