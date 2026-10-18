# Client-Side Fetching (Vanilla JS)

[Previous](server-side-rendering-php.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · Next

If you are building a decoupled frontend or a Single Page Application (SPA), you can fetch the active role menus dynamically via the REST API.

The endpoint requires a secure LW_TOKEN to be passed in the Authorization header to verify the user's roles.

**JavaScript:**

```
const fetchDynamicMenu = async () => {
   try {
       const menu = await fetch(`${BASE_URL}/menu/active-roles`, {
           method: "GET",
           headers: {
               'Authorization': `Bearer ${LW_TOKEN}`,
               'Accept': 'application/json'
           }
       });
       
       // Extract the array of menu objects
       const { responseData } = await menu.json();
       
       // Append the fetched menus to your existing navigation array/logic
       navLinks = [...navLinks, ...responseData];
       
   } catch (error) {
       console.error("Failed to fetch navigation menu:", error);
   }
};
```

Source: https://www.lifetech.host/hubs/Docs#client-side-fetching-(vanilla-js)

[Previous](server-side-rendering-php.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · Next
