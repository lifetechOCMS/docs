# Connect Views to Module APIs

[Previous](create-module-views.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](handle-http-requests-with-ltrequest.md)

*Section: Creating module content*

## Purpose

A LifeTechOCMS **View** presents an interface, while a module **API endpoint** provides the data or performs the operation behind that interface. A module can include its own Views for dashboards, forms, and administration screens; a theme can also call the same module APIs to build a more complete website interface.

The usual request flow is:

```text
Module View or Theme View
       ↓ HTTP request (fetch)
Module API Route → Controller → Service → Model → Database
       ↓ JSON response
View updates the interface
```

Do not assume that opening a View automatically executes a Controller method. Connect the View to a registered module API endpoint when it needs dynamic records or actions.

## Find the module endpoint

MdBlog defines its API routes in [`Services/MdBlogRoutes.php`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/MdBlogRoutes.php). Its category routes include:

```php
LtRoute::get('/blogs/categories', 'MdBlog@TbBlogCategoryController@index')
    ->name('admin-blog-category.index');

LtRoute::post('/blogs/categories', 'MdBlog@TbBlogCategoryController@store')
    ->name('admin-blog-category.store');

LtRoute::patch('/blogs/categories/{ltId}', 'MdBlog@TbBlogCategoryController@update')
    ->name('admin-blog-category.update');

LtRoute::delete('/blogs/categories/{ltId}', 'MdBlog@TbBlogCategoryController@destroy')
    ->name('admin-blog-category.delete');
```

The first argument is the route path; the second is `ModuleName@ControllerName@MethodName`. The optional `name()` gives the route a stable identifier that can be documented in an API contract. The `ltId` segment identifies the record being updated or deleted.

| Action | HTTP method | MdBlog path | Controller method |
| --- | --- | --- | --- |
| List categories | GET | `/blogs/categories` | `index()` |
| Create category | POST | `/blogs/categories` | `store()` |
| Update category | PATCH | `/blogs/categories/{ltId}` | `update()` |
| Delete category | DELETE | `/blogs/categories/{ltId}` | `destroy()` |

The paths above are **registered module route paths**, not necessarily complete public URLs. In examples below, `/api/v1/v2` is an illustrative installation prefix. Confirm the prefix, base URL, authentication, and permissions in your own installation.

## Read API data in a View

For example, a simple module View can request categories and display their names:

```html
<section>
    <h2>Blog categories</h2>
    <p id="category-message" role="status">Loading categories...</p>
    <ul id="category-list"></ul>
</section>

<script>
    const apiBase = '/api/v1/v2'; // Adjust for your installation.

    async function loadCategories() {
        const message = document.getElementById('category-message');
        const list = document.getElementById('category-list');

        try {
            const response = await fetch(`${apiBase}/blogs/categories`, {
                headers: { 'Accept': 'application/json' },
                credentials: 'same-origin'
            });

            if (!response.ok) {
                throw new Error(`Request failed (${response.status})`);
            }

            const result = await response.json();

            // Check the LifeTechOCMS response envelope.
            if (String(result.responseCategory) !== '200') {
                throw new Error(result.responseResult || 'Could not load categories');
            }

            list.replaceChildren();
            const categories = Array.isArray(result.responseData)
                ? result.responseData
                : [];

            for (const category of categories) {
                const item = document.createElement('li');
                item.textContent = category.categoryName ?? category.category_name ?? 'Unnamed category';
                list.appendChild(item);
            }

            message.textContent = categories.length
                ? ''
                : 'No categories found.';
        } catch (error) {
            message.textContent = error.message;
        }
    }

    loadCategories();
</script>
```

**Notes:** This is a simplified teaching example, not copied from MdBlog. Confirm the actual JSON payload and field names in your running version. Using `textContent` avoids inserting untrusted API values as HTML. The `responseCategory` success value `200` follows LifeTechOCMS response conventions; `responseCode` is a separate, four-digit application response code for new implementations.

## Send data from a form

A View can also submit information to a module endpoint. This example shows the HTTP request pattern; the submitted fields must match the Service's expected input names.

```js
async function createCategory(categoryName) {
    const response = await fetch(`${apiBase}/blogs/categories`, {
        method: 'POST',
        headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
        },
        credentials: 'same-origin',
        body: JSON.stringify({ categoryName })
    });

    if (!response.ok) {
        throw new Error(`Request failed (${response.status})`);
    }

    const result = await response.json();
    if (String(result.responseCategory) !== '200') {
        throw new Error(result.responseResult || 'Unable to save category');
    }

    return result;
}
```

**Important:** The actual MdBlog Service uses `processRequest()` to read incoming values. Verify that your installed request handler accepts JSON before using this exact payload. If it expects form-encoded fields, send `FormData` or `URLSearchParams` instead. For state-changing requests, follow your application's CSRF and authentication requirements.

## Update or delete a record

The same principle applies to the remaining route methods:

```js
// Update a category (adapt the request body to the Service contract).
await fetch(`${apiBase}/blogs/categories/${encodeURIComponent(ltId)}`, {
    method: 'PATCH',
    headers: { 'Content-Type': 'application/json' },
    credentials: 'same-origin',
    body: JSON.stringify({ categoryName: 'Updated name' })
});

// Delete a category after user confirmation and authorisation.
await fetch(`${apiBase}/blogs/categories/${encodeURIComponent(ltId)}`, {
    method: 'DELETE',
    credentials: 'same-origin'
});
```

These snippets demonstrate request syntax only. In real Views, also check HTTP status, parse the LifeTech response, handle errors, and refresh the interface after success. Do not assume a successful HTTP status means the application operation succeeded.

## Practical reference: MdBlog Views

The [`Views/Category.html`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Views/Category.html) file contains a **Manage Category** interface, including an Add Category button, search field, table, filters, and pagination. Other module-owned interfaces include `Manage-post.html` and `Admin-dashboard.html`.

The API connection should remain clear: a View controls display and user interaction; a Controller receives the request; a Service implements the operation; a Model accesses stored records. The same API can serve a module View or a separate theme View.

## Authentication, errors, and deployment

- Use the actual site/API base address rather than assuming every deployment is at the domain root.
- Supply the authentication mechanism required by the endpoint. `credentials: 'same-origin'` only sends same-origin cookies; it does not replace bearer tokens or remote-site authentication.
- Check both the HTTP status and the LifeTechOCMS `responseCategory`, and show meaningful loading, empty, success, and error messages.
- If a token is missing or expired, inform the user and follow the application's login or Site Connect flow; do not silently leave the interface loading.
- Apply permissions and validation on the backend even when the View also checks user input.
- Avoid hardcoded records when the module already exposes an endpoint that supplies them.
- For cross-origin requests, configure CORS and credentials appropriately on the backend; never expose secret tokens in public source code.

## Before moving on

Confirm that the module route is registered, its Controller and Service methods exist, the View uses the correct endpoint and payload, and errors are visible to users. Test GET, POST, PATCH, and DELETE operations with the authentication and permissions required by your installation.

For more details, see [Define Module Routes and Endpoints](define-module-routes-and-endpoints.md), [LtRequest](../../appcore/LtRequest.md), and [LtResponse](../../appcore/LtResponse.md).

Next: [Handle HTTP Requests with LtRequest](handle-http-requests-with-ltrequest.md).

---

[Previous](create-module-views.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](handle-http-requests-with-ltrequest.md)
