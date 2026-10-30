# Register and Test Blog API Endpoints

[Previous](build-a-blog-category-model-service-and-controller.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](connect-blog-views-to-api-responses.md)

*Section: Practical MdBlog development*

The verified MdBlog route file defines these category endpoints:

| Method | Route | Controller method |
| --- | --- | --- |
| GET | `/blogs/categories` | `index` |
| POST | `/blogs/categories` | `store` |
| PATCH | `/blogs/categories/{ltId}` | `update` |
| PATCH | `/blogs/categories/{ltId}/toggle-active` | `toggleActive` |
| DELETE | `/blogs/categories/{ltId}` | `destroy` |

Test with an authenticated API client when required. Confirm the API base prefix in your environment; the route definitions themselves do not include it.

[View the actual routes](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/MdBlogRoutes.php).

---

[Previous](build-a-blog-category-model-service-and-controller.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](connect-blog-views-to-api-responses.md)
