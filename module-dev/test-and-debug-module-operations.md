# Test and Debug Module Operations

[Previous](connect-blog-views-to-api-responses.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](edit-module-package.md)

*Section: Practical MdBlog development*

Use a repeatable test sequence:

1. Confirm the module is installed and the expected database table exists.
2. Call `GET /blogs/categories` and inspect the response envelope.
3. Submit a valid category using `POST /blogs/categories`.
4. Submit missing or duplicate category values and verify failures.
5. Update and delete a test record, then confirm the resulting state.
6. Repeat database queries with the intended MySQL/MariaDB SQL mode.

Review [LtResponse](../../appcore/LtResponse.md) and the [response-code reference](../../appcore/LtResponse_Codes_and_Response_Groups.md). These are suggested tests; no execution is claimed here.

---

[Previous](connect-blog-views-to-api-responses.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](edit-module-package.md)
