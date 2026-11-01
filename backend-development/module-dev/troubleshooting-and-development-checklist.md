# Troubleshooting and Development Checklist

[Previous](security-and-management-permissions.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](example-modules-and-references.md)

*Section: Deployment and maintenance*

Before publishing or distributing a module, check:

- [ ] Package metadata and dependencies are correct.
- [ ] PHP namespaces match package paths.
- [ ] Models map to the expected tables.
- [ ] Controllers call the intended services.
- [ ] Routes use correct HTTP methods and paths.
- [ ] Validation and permissions cover writes.
- [ ] API responses use the required four-digit application codes.
- [ ] Views handle success and failure responses.
- [ ] Database operations pass under the intended SQL mode.
- [ ] Installation, export, and update have been tested.

For framework-specific errors, consult the relevant [Core Services guide](../../appcore/README.md).

---

[Previous](security-and-management-permissions.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](example-modules-and-references.md)
