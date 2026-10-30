# Security and Management Permissions

[Previous](delete-a-module.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](troubleshooting-and-development-checklist.md)

*Section: Deployment and maintenance*

Module endpoints must enforce server-side authorization. Apply validation before writes, use parameterized database operations through supported framework methods, and avoid exposing internal error details in production.

Consult [LtAuth](../../appcore/LtAuth.md), [LtValidator](../../appcore/LtValidator.md), [LtSession](../../appcore/LtSession.md), and [LtResponse](../../appcore/LtResponse.md).

**Review task:** Identify which MdBlog endpoints modify data and verify their actual access controls in the deployment configuration. The presence of a session read does not establish authorization.

---

[Previous](delete-a-module.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](troubleshooting-and-development-checklist.md)
