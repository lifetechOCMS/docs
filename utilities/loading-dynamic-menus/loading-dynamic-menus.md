# Loading Dynamic Menus

Previous · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](server-side-rendering-php.md)

Lifetech OCMS allows developers to render navigation menus dynamically based on the active user's roles and permissions. Instead of manually writing out every link, the system fetches the allowed links from a database and stacks them on the screen. This ensures that users only see the routes and pages they are authorized to access. You can achieve this using either server-side rendering (PHP) or client-side fetching (Vanilla JS).

**1. Menu Structure and Data Details**

When the system asks the database for a menu item, it receives a digital "object" packed with information. Each piece of information (called a "key") tells the system exactly how to display and link that specific menu item.

Here is what each key in the menu object does:

 
                 
                 
                 
                 ![Loading Dynamic Menus screenshot](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/05d2ba5087de61584d516eb9e4be773a.png)
            
            
            

- **ltId**: The unique system identification number for the specific menu item.
- **menuName**: The actual text that visitors will see on the screen (for example, "MdCardDesign").
- **slug**: A web-friendly version of the name used for background routing.
- **routePath**: The actual destination URL the menu item points to when clicked.
- **target**: Tells the browser how to open the link (for instance, opening in the same tab or a new one).
- **isExternal**: A simple switch (0 for no, 1 for yes) that indicates if the link points to a completely different website.
- **parentMenuId**: If this menu is hidden inside a dropdown, this tells the system which main menu it belongs to.
- **menuLevel**: Indicates the hierarchy. "1" is a main menu bar item, while higher numbers mean it is a sub-menu.
- **icon**: The specific graphic or symbol displayed next to the menu text.
- **children**: A list (or array) that holds any sub-menus that belong directly underneath this item.

**2. The Fetched Menu Data (Hierarchy)**

Because menus often have dropdowns, the system organizes the fetched data into levels. It groups items as primary links, secondary links, and even tertiary links.

When the backend fetches this data, it outputs a clean hierarchy. For example, the system will load a primary "Level 1" item, and then load all the "Level 2" items that belong inside it before moving on to the next primary item.

 
                 
                 
                 ![Loading Dynamic Menus screenshot](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/05c7b5d43d089f85aa9d9d3974e42ff4.png)
            
                        

- **Example from the system:** A main menu item named "MdCardDesign" (Level 1) acts as a parent, holding specific sub-menus inside it, such as "Create Section" (Level 2), "Card Profile" (Level 2), and "Card Layout" (Level 2).

**3. Menu Rendering Logic (Dynamic vs. Static Preview)**

When building or editing themes in Lifetech OCMS, the system needs a way to separate what your live visitors see from what you see while designing. To handle this, the theme utilizes a simple conditional "switch" in the code.

This switch checks the web address (URL) for a specific signal to determine which version of the navigation menu to load.

**How the Logic Works:**

- **DYNAMIC MENU LOGIC (Live Website)** 

if (!isset($_GET['preview_theme'])) 

This line checks if the URL *does not* contain the "preview_theme" signal. This is the default state for your actual website. When normal visitors browse your site, this condition is met, and the system securely connects to the database to fetch and render the live, role-based dynamic menus.

- **STATIC FALLBACK / PREVIEW LOGIC (Theme Editing)** 

 } else { 

If the "preview_theme" signal *is* detected in the URL (which happens automatically when you click the Preview button in the Theme Management dashboard), the system skips the database entirely. Instead, it loads the hard-coded, static HTML menu.

Why is this important? This dual-logic system ensures that you can safely preview, design, and style complex dropdown menus in your theme using the static HTML structure without needing to create fake pages or disrupt the live database structure of your actual website.

Source: https://www.lifetech.host/hubs/Docs#loading-dynamic-menus

Previous · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](server-side-rendering-php.md)
