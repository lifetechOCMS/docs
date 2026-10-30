# Connect Blog Views to API Responses

[Previous](register-and-test-blog-api-endpoints.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](test-and-debug-module-operations.md)

*Section: Practical MdBlog development*

Use MdBlog's [Category view](https://github.com/adedayoAdetunji/MdBlog/blob/main/Views/Category.html) as the visual reference and the `/blogs/categories` route as the data source.

The response is produced by `TbBlogCategoryController::index()` using `LtResponse::json()`. Read the returned `responseData` and handle error categories before rendering rows.

**Exercise:** Inspect the existing view and identify where it requests category data. Avoid assuming a particular JavaScript library without reading the view source.

---

[Previous](register-and-test-blog-api-endpoints.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](test-and-debug-module-operations.md)
