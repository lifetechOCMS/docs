# Connect Theme Views to Backend APIs

[Previous topic](17-use-site-information-and-helper-functions.md) · [Contents](README.md) · [Next topic](19-edit-theme-package.md)

## On this page

- [Understand the API terms](#understand-the-api-terms)
- [Create a Posts view](#create-a-posts-view)
- [Read what the code does](#read-what-the-code-does)
- [Send a token for a protected request](#send-a-token-for-a-protected-request)

The theme presents data; the backend module supplies it. A theme that includes a blog interface does not by itself create blog storage or API routes.

This example uses an endpoint demonstrated in ThemeBlog: **blogs/posts/widget?limit=6&type=popular**. Use it only where the corresponding blog backend is installed and configured. Otherwise substitute a working endpoint from your module.

## Understand the API terms

| **Term** | **Meaning** | **Example** |
| --- | --- | --- |
| Base URL | The common starting address for backend requests | Returned by backEndBaseUrl() |
| Endpoint | A particular backend path | blogs/posts/widget |
| Query parameter | An option added after a question mark | limit=6 |
| GET | Read data | Load popular posts |
| POST | Submit data or request an action | Create a comment, when the module supports it |
| JSON | A structured data format used by the API | An object with responseData |
| Token | A login credential used by protected API requests | A bearer token |
| HTTP status | The transport-level request result | 200 or 401 |
| responseCategory | LifeTechOCMS's application-level result category | 200 for success in these themes |
| responseData | The returned application data | A list of posts |
| responseResult | A response message | An explanation when a request fails |

## Create a Posts view

Create Posts.html as View content with additional path / and Is Theme Default set to No. Paste:

```html
<section class="card">
     <h1>Popular posts</h1>
     <p id="postsStatus" role="status">Loading posts...</p>
     <ul id="postsList"></ul>
 </section>
 
 <script>
 (async function loadPosts() {
     const apiBase = <?= json_encode(
         ApiTokenDetails::backEndBaseUrl(),
         JSON_HEX_TAG | JSON_HEX_AMP | JSON_HEX_APOS | JSON_HEX_QUOT
     ) ?>;
     const status = document.getElementById('postsStatus');
     const list = document.getElementById('postsList');
 
     try {
         const url = apiBase.replace(/\/+$/, '')
             + '/blogs/posts/widget?limit=6&type=popular';
         const response = await fetch(url, {
             method: 'GET',
             headers: { Accept: 'application/json' }
         });
         if (!response.ok) {
             throw new Error('Request failed with HTTP status ' + response.status);
         }
         const result = await response.json();
         if (Number(result.responseCategory) !== 200) {
             throw new Error(result.responseResult || 'Unable to load posts.');
         }
         const posts = Array.isArray(result.responseData) ? result.responseData : [];
         list.replaceChildren();
         for (const post of posts) {
             const item = document.createElement('li');
             item.textContent = post.title || 'Untitled post';
             list.appendChild(item);
         }
         status.textContent = posts.length ? '' : 'No posts available.';
     } catch (error) {
         status.textContent = error.message;
     }
 })();
 </script>
```

Creating this View content automatically creates its associated page and menu. Check the generated route, such as **/ThemeStarter/Posts**, and open it through its menu or Preview.

## Read what the code does

First, PHP supplies the backend base address. The browser then calls fetch() to request the endpoint. await waits for the response. response.ok checks HTTP success; responseCategory checks the application's result. Finally, the code creates a list item for each returned post.

The loading text gives feedback while the request runs. An empty result displays a useful message. A failed request displays its error. Using textContent renders post titles as text rather than executable HTML.

## Send a token for a protected request

ThemeBlog's administration views use the Authorization header. This example prepares those headers; it does not invent a protected endpoint:

```html
<script>
 const tokenName = <?= json_encode(
     ApiTokenDetails::tokenName(),
     JSON_HEX_TAG | JSON_HEX_AMP | JSON_HEX_APOS | JSON_HEX_QUOT
 ) ?>;
 
 function authenticatedHeaders() {
     const token = localStorage.getItem(tokenName);
     if (!token) throw new Error('Please sign in first.');
     return {
         Accept: 'application/json',
         Authorization: `Bearer ${token}`
     };
 }
 </script>
```

Use these headers only with the intended trusted backend and the module's documented request. Backend permissions must still decide what the caller can do. For a JSON submission, the module may require Content-Type: application/json and a body built with JSON.stringify(); follow its actual method and field names.

[Previous topic](17-use-site-information-and-helper-functions.md) · [Contents](README.md) · [Next topic](19-edit-theme-package.md)
