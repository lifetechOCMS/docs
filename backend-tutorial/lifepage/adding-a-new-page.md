# Adding a New Page

[Previous](life-page-interface.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](publish-to-content.md)

**Steps:**

1. Click **Add Page**. 
1. The **Add New Page** window will appear.
1. Fill in the required page information.
                    ![Adding a New Page screenshot](https://www.lifetech.host/hubs/packages/modules/MdDocs/Media/acc435498a311d4e71939de712cd856a.png)
               

***General Form Fields:***

- **Page Name:** Enter the name of the page. Spaces are not allowed in the page name.
- **Route Path:** Define the URL path (e.g., /api/example/path).
- **Description:** Enter a brief description of the page's purpose.
- **Module Name:** An optional dropdown to link the page to a specific module.
- **Page Type:** Select the classification of the page. Available types include Theme, Report, Router, and Api.
- **Status Toggles:** Use the checkboxes to mark the page as **Published** or **Protected**.

***Page Type Configurations***

 Depending on the selected Page Type, specific settings may apply:

- **Router Type Configuration:** If **Router** is selected as the Page Type, the following specific fields will be available:
- **Route Method:** Select the HTTP method (e.g., GET).
- **Route File Name:** Enter the file name (e.g., filename.html).
- **Route Handler:** Define the handler using the format PackageName@ControllerName@MethodName.
- **Route Content:** Enter the HTML or necessary content.
- **Route Payload (JSON):** Enter any required JSON payload (e.g., {"key": "value"}).
- **API Type Configuration:** If **Api** is selected as the Page Type, this acts as an API to allow routers.

Source: https://www.lifetech.host/hubs/Docs#adding-a-new-page

[Previous](life-page-interface.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](publish-to-content.md)
