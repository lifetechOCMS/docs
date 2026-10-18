# Load Menus for the Current Users Roles

[Previous](create-views-pages-and-menus.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](understand-the-default-layout-and-custom-layouts.md)

## On this page

- [Understand token and session identification](#understand-token-and-session-identification)
- [Prepare the API and site addresses](#prepare-the-api-and-site-addresses)
- [Load menu data without HTML or CSS](#load-menu-data-without-html-or-css)
- [Inspect data before rendering](#inspect-data-before-rendering)
- [Understand the response fields](#understand-the-response-fields)
- [Display menus with plain HTML](#display-menus-with-plain-html)
- [Connect loading and rendering](#connect-loading-and-rendering)
- [Optional PHP rendering](#optional-php-rendering)
- [Test roles and distinguish the two loaders](#test-roles-and-distinguish-the-two-loaders)

LifeTechOCMS stores navigation menus in the database. Theme developers can request the menus permitted for the current user, then display them with their own navigation design. Use the general endpoint for menus across packages, or add packageName to filter by a named package:

**GET /menus/is-navigation**

 **GET /menus/is-navigation?packageName=ThemeStarter**

## Understand token and session identification

The request can carry a Bearer token or use an existing login session. AppCore processes the available authentication before the menu method runs. The method reads role IDs from LtSession::get('ltUrid'). If no role value is available, it uses the Anonymous role. Multiple role IDs are separated and trimmed before the role filtering is applied.

A request without a Bearer token is not automatically an Anonymous request. A logged-in user may already have a session. The backend determines role permissions. Do not send role IDs. Omit packageName to obtain all permitted navigation menus, or supply it to restrict the result to that package; the role checks still apply.

## Prepare the API and site addresses

Place these declarations inside a theme content file processed as PHP, before the menu functions:

```js
<script>
 const BASE_URL = <?= json_encode(ApiTokenDetails::backEndBaseUrl()); ?>;
 const siteHostAddress = <?= json_encode(ltSiteHostAddress()); ?>;
 </script>
```

| **Variable** | **Purpose** |
| --- | --- |
| BASE_URL | Backend API base address used to request menus |
| siteHostAddress | Site address used to build internal navigation links |
| LW_TOKEN | Current user's token, when already supplied by your authentication code |

json_encode() converts PHP values into JavaScript string values safely. The examples below are JavaScript: put them inside a script element after these declarations, or in your loaded JavaScript content. Declare shared constants only once.

## Load menu data without HTML or CSS

The loader requests the data and returns the menu array. It does not produce markup or apply styling.

```js
async function loadNavigationMenus(token = '', packageName = '') {
     const headers = { Accept: 'application/json' };

     if (token) {
         headers.Authorization = `Bearer ${token}`;
     }

     const url = new URL(
         `${BASE_URL.replace(/\/+$/, '')}/menus/is-navigation`
     );
     if (packageName) {
         url.searchParams.set('packageName', packageName);
     }

     const response = await fetch(url.href, { method: 'GET', headers });

     if (!response.ok) {
         throw new Error(`Menu request failed: ${response.status}`);
     }

     const result = await response.json();

     if (result.responseCategory !== 200) {
         throw new Error(
             result.responseResult || 'Unable to load navigation menus.'
         );
     }

     if (!Array.isArray(result.responseData)) {
         throw new Error('Invalid menu response.');
     }

     return result.responseData;
}
```

| **Syntax** | **Explanation** |
| --- | --- |
| async / await | Wait for the HTTP request and JSON parsing |
| token = '' | Make the Bearer token optional |
| packageName = '' | Make the package filter optional |
| url.searchParams.set() | Add and encode the packageName query parameter |
| Authorization | Carry the token in the format Bearer followed by the token |
| fetch() | Send the HTTP request |
| response.ok | Check HTTP success |
| responseCategory | Check application success; 200 indicates success |
| responseData | Return the menu records, including nested children |

No explicit credentials option is used. For a same-origin request, fetch sends eligible session cookies by default. An API on another origin needs a suitable authentication arrangement; the loader does not assume that its session cookies will accompany the request.

## Inspect data before rendering

Start with a console example using the existing session:

```js
async function inspectMenus() {
     try {
         const menus = await loadNavigationMenus();
         console.log(menus);
     } catch (error) {
         console.error('Menu Load Error:', error.message);
     }
}

inspectMenus();
```

If your authentication code already provides LW_TOKEN, change the call inside the function to:

```js
const menus = await loadNavigationMenus(LW_TOKEN);
```

To filter menus by package, use one of these calls inside your async function:

```js
// Existing session, restricted to ThemeStarter menus.
const menus = await loadNavigationMenus('', 'ThemeStarter');

// Bearer token, restricted to ThemeStarter menus.
const menus = await loadNavigationMenus(LW_TOKEN, 'ThemeStarter');
```

Both requests retain role-based filtering. Without the second argument, the loader uses /menus/is-navigation and requests permitted navigation menus across packages.

An invalid or expired token can cause an authentication error. Do not silently retry as a different user or as Anonymous.

## Understand the response fields

The supplied response includes this parent menu and its child:

```json
{
   "responseResult": "Data Fetched",
   "responseCode": 2009,
   "responseCategory": 200,
   "responseData": [
     {
       "ltId": "178791436425882",
       "menuName": "ThemeBlog",
       "slug": null,
       "routePath": "#",
       "target": "self",
       "isExternal": 0,
       "parentMenuId": null,
       "menuLevel": 1,
       "icon": null,
       "children": [
         {
           "ltId": "178791826124184",
           "menuName": "Blog.html",
           "slug": null,
           "routePath": "/ThemeBlog/Blog",
           "target": "_blank",
           "isExternal": 0,
           "parentMenuId": "178791436425882",
           "menuLevel": 2,
           "icon": ""
         }
       ]
     }
   ]
}
```

| **Field** | **Meaning** |
| --- | --- |
| ltId | Unique menu identifier |
| menuName | Label displayed in the navigation |
| routePath | Destination; # can act as a parent placeholder |
| target | Link target; map self to _self, while _blank opens a new tab |
| isExternal | Whether the destination is external |
| parentMenuId | Parent identifier; null indicates a top-level item |
| menuLevel | Depth of the menu in its hierarchy |
| children | Nested records, when present |
| icon | Optional icon information for a styled renderer |
| slug | Additional API field; null in this example |

The loader returns responseData, not the entire response envelope. The renderer uses the nested children directly rather than rebuilding the hierarchy from parentMenuId.

## Display menus with plain HTML

Add this container to the theme's navigation component:

```html
<nav id="mainNav" aria-label="Main navigation"></nav>
```

Use a separate renderer to create links and nested lists. This example needs no CSS framework or icon library.

```js
function getMenuUrl(item) {
     const route = item.routePath ?? '#';
     if (route === '#') return '#';

     let url;
     if (Number(item.isExternal) === 1) {
         url = new URL(route);
     } else {
         const base = `${siteHostAddress.replace(/\/+$/, '')}/`;
         url = new URL(route.replace(/^\/+/, ''), base);
     }

     if (!['http:', 'https:'].includes(url.protocol)) {
         throw new Error('Unsupported menu URL.');
     }
     return url.href;
}

function buildMenuList(items) {
     const list = document.createElement('ul');

     for (const item of items) {
         const listItem = document.createElement('li');
         const link = document.createElement('a');
         link.textContent = item.menuName || '';
         link.href = getMenuUrl(item);

         const target = item.target || 'self';
         link.target = target === 'self' ? '_self' : target;
         if (link.target === '_blank') {
             link.rel = 'noopener noreferrer';
         }

         listItem.append(link);
         if (Array.isArray(item.children) && item.children.length) {
             listItem.append(buildMenuList(item.children));
         }
         list.append(listItem);
     }
     return list;
}

function renderNavigation(menus) {
     const nav = document.getElementById('mainNav');
     if (nav) nav.replaceChildren(buildMenuList(menus));
}
```

textContent displays menu labels as text. Internal routes are appended to the site address, preserving a site installation subfolder. External entries use their complete HTTP or HTTPS URL. This beginner example limits destinations to those protocols.

buildMenuList() calls itself for each set of children. This is recursion: the same function renders the parent list, child lists and deeper levels. All lists are visible; add dropdown interaction separately if your design needs it.

## Connect loading and rendering

Place this after the navigation container and the functions above:

```js
async function initialiseNavigation(token = '', packageName = '') {
     try {
         const menus = await loadNavigationMenus(token, packageName);
         renderNavigation(menus);
     } catch (error) {
         console.error('Menu Load Error:', error.message);
     }
}

// Use the existing session; Anonymous roles apply if none are available.
initialiseNavigation();
```

When LW_TOKEN is already available, use initialiseNavigation(LW_TOKEN) instead of the final call. To filter the displayed navigation, use initialiseNavigation('', 'ThemeStarter') with an existing session, or initialiseNavigation(LW_TOKEN, 'ThemeStarter') with a token. Choose one initialization call. With the supplied data, ThemeBlog appears as the parent and Blog.html appears beneath it. Blog opens the configured page in a new tab.

Optional developer-defined links can be added before rendering:

```js
const navLinks = [
     { menuName: 'Home', routePath: '', target: 'self', isExternal: 0 },
     ...menus,
     { menuName: 'Documentation', routePath: '/Docs', isExternal: 0 }
];
renderNavigation(navLinks);
```

Use this inside initialiseNavigation after obtaining menus, and replace its existing render call. Only add routes that exist on your site. An empty Home route resolves to the site base. A missing route remains # because getMenuUrl uses the nullish coalescing operator (??).

## Optional PHP rendering

PHP can render menus with foreach if the role-filtered data is obtained on the server before the page is rendered. PHP cannot loop over data fetched later by browser JavaScript. A server-side API request must carry the appropriate user identity; it does not automatically inherit the browser's session.

The following rendering-only example assumes $menuResponse already holds the decoded response as a PHP array. The server-side loading call must use your platform's supported helper or service.

```html
<?php
$menus = $menuResponse['responseData'] ?? [];

$renderMenuLabels = function (array $items) use (&$renderMenuLabels): void {
     echo '<ul>';
     foreach ($items as $item) {
         echo '<li><span>';
         echo htmlspecialchars(
             $item['menuName'] ?? '', ENT_QUOTES, 'UTF-8'
         );
         echo '</span>';

         if (!empty($item['children']) && is_array($item['children'])) {
             $renderMenuLabels($item['children']);
         }
         echo '</li>';
     }
     echo '</ul>';
};
?>

<nav aria-label="Main navigation">
     <?php $renderMenuLabels($menus); ?>
</nav>
```

This example demonstrates escaped labels and recursive PHP loops. It does not implement navigation links or a menu-fetching helper. Use the complete JavaScript example for navigation until your server-side integration is available.

## Test roles and distinguish the two loaders

Test a visitor with no login, a user with an existing session, and a user sending a valid Bearer token. Check nested links, targets and the page destinations. Menu visibility does not replace page or API authorization.

| **Loader** | **Responsibility** |
| --- | --- |
| /menus/is-navigation | Return navigation menus permitted for the current user's roles across packages |
| /menus/is-navigation?packageName=ThemeStarter | Return permitted navigation menus filtered to ThemeStarter |
| dddm::loadDynamicContent() | Display theme, module or plugin content assigned to the current page |

A menu directs the visitor to a page. The dynamic content loader displays that page's assigned content. Developers can add their own classes, icons and navigation interactions without changing the data loader.

**Expected result:** the theme loads role-filtered menu data and displays it using a separate renderer.

Source: https://www.lifetech.host/hubs/Docs#load-menus-for-the-current-users-roles

[Previous](create-views-pages-and-menus.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](understand-the-default-layout-and-custom-layouts.md)
