# Connect Views to Module APIs

[Previous](create-module-views.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](handle-http-requests-with-ltrequest.md)

*Section: Creating module components*

The route `GET /blogs/categories` is defined by MdBlog and handled by its category controller. A view can request that endpoint and render the returned categories.

```js
// Illustration: adapt the API base path and authentication to your installation.
const response = await fetch('/api/v1/v2/blogs/categories');
const result = await response.json();
console.log(result.responseData);
```

The API prefix above is an integration example, not a claim about every installation. Confirm the configured endpoint prefix and authentication requirements before using it.

---

[Previous](create-module-views.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](handle-http-requests-with-ltrequest.md)
