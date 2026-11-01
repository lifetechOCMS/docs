# Create Module Views

[Previous](define-module-routes-and-endpoints.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](connect-views-to-module-apis.md)

*Section: Creating module content*

## What is a Module View?

A **View** is module content that presents an interface to users. In the Model–View–Controller (MVC) architecture, the Model handles data access, the Service implements operations and business rules, the Controller coordinates requests, and the View displays information or allows users to interact with a feature.

LifeTechOCMS themes normally provide the main website design, including shared headers, navigation, footers, and page layouts. **Modules can also provide their own Views** for screens directly related to their functionality. A module View can be a simple HTML page or a more complete interface, such as a blog management dashboard.

A module View is **optional**. An API-only module can expose Controllers and Services without providing a visual interface.

## When should you create a Module View?

Use a module View when a feature needs a screen that belongs naturally to the module, such as:

- A form for creating or editing records.
- A management dashboard for a module.
- A list or table of records.
- A sign-in or account-related interface for a module-specific workflow.
- A simple report or preview page.

Use a **theme View** when building the wider public-facing website experience, especially pages that should share the theme's layout and design conventions. A theme can consume a module's API endpoints without using that module's Views.

| Concern | Module View | Theme View |
| --- | --- | --- |
| Main purpose | Present a feature's own interface | Present the website's overall experience |
| Typical examples | Management form, dashboard, report | Home page, public blog layout, landing page |
| Data source | Module APIs or appropriate framework integrations | Module APIs or theme data sources |
| Required? | No; API-only modules may omit Views | Depends on the site's theme design |

## Create View content in LifeTechOCMS

1. Open **Modules** in the LifeTechOCMS backend.
2. Select the module you are developing, such as `MdStudent`.
3. Open the module's **Content** section and choose **Add Content**.
4. Enter a descriptive filename, such as `Student-list.html`.
5. Select **View** as the MVC content type.
6. Complete the other content settings required by your installation, then create the content.
7. Open the content editor and write your HTML, CSS, and JavaScript as needed.
8. Save the View and configure how it will be accessed according to your installation's page, menu, or dispatch settings.

If you create a View file directly inside the module's `Views/` folder, use **Sync Module Files** to register newly discovered files in the LifeTechOCMS content system when necessary.

> **Note:** Creating a View file and making it reachable at a public URL are separate concerns. The exact dispatch, page-assignment, and layout behaviour depends on your installed LifeTechOCMS version and configuration. Do not assume that a module View automatically creates a route or public page.

## View naming and structure

For a sample student module:

```text
MdStudent/
├── Controllers/
│   └── TbStudentController.php
├── Models/
│   └── TbStudent.php
├── Services/
│   ├── TbStudentService.php
│   └── MdStudentRoutes.php
└── Views/
    ├── Student-list.html
    └── Student-form.html
```

Use descriptive filenames and keep related Views together in the module's `Views/` folder. Unlike Controllers, Services, and Models, an HTML View does not require a PHP namespace or class declaration.

## Simple example: student list View

Create `Views/Student-list.html` with a small interface:

```html
<section class="student-page">
    <h1>Students</h1>
    <p>Manage student records from this module.</p>

    <button type="button" id="loadStudents">Load students</button>
    <ul id="studentList"></ul>
    <p id="studentMessage" role="status"></p>
</section>

<script>
    const button = document.getElementById('loadStudents');
    const list = document.getElementById('studentList');
    const message = document.getElementById('studentMessage');

    button.addEventListener('click', async () => {
        message.textContent = 'Loading students...';
        list.replaceChildren();

        try {
            // Replace with the registered MdStudent endpoint in your installation.
            const response = await fetch('/api/v1/v2/students');
            if (!response.ok) throw new Error('Request failed');

            const result = await response.json();
            const students = Array.isArray(result.responseData)
                ? result.responseData
                : [];

            for (const student of students) {
                const item = document.createElement('li');
                item.textContent = student.studentName ?? 'Unnamed student';
                list.appendChild(item);
            }

            message.textContent = `${students.length} student(s) loaded.`;
        } catch (error) {
            message.textContent = 'Unable to load students. Please try again.';
        }
    });
</script>
```

This is an **illustrative example**, not a confirmed endpoint from the MdStudent module. It assumes a registered `GET /students` API route and a response containing `responseData`. Adapt the API prefix, authentication, field names, and error handling to your installation. Using `textContent` prevents API values from being inserted as executable HTML.

## How Views relate to Controllers and Services

When a View needs dynamic information, a common pattern is:

```text
User opens a Module View
          ↓
View sends an HTTP request to a module API
          ↓
Module Route → Controller → Service → Model
          ↓
Controller returns an API response
          ↓
View displays the result
```

For example, a student list View can call a route handled by `TbStudentController::index()`. The Controller delegates to `TbStudentService::index()`, which retrieves student records through `TbStudent`. The View then displays those records.

**Keep business rules in Services**, not embedded in HTML or JavaScript. Protect sensitive API operations using server-side authentication and authorisation; hiding buttons in a View is not a security control.

## Practical MdBlog example

MdBlog provides real module Views in its [`Views/` directory](https://github.com/adedayoAdetunji/MdBlog/tree/main/Views), including:

| View file | Intended interface |
| --- | --- |
| [`Admin-dashboard.html`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Views/Admin-dashboard.html) | Blog administration dashboard |
| [`Category.html`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Views/Category.html) | Blog category interface |
| [`Manage-post.html`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Views/Manage-post.html) | Post management interface |
| [`Sign-in.html`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Views/Sign-in.html) | Sign-in interface |
| [`Blog.html`](https://github.com/adedayoAdetunji/MdBlog/blob/main/Views/Blog.html) | Blog interface |

These files demonstrate that a module can ship its own user interface rather than relying exclusively on a theme. The existence of these files does not, by itself, establish their public URLs or how they are dispatched; verify that separately in the running installation.

## Module Views and theme integration

There are two useful approaches:

**Module-owned interface:** The module provides its own View, such as an administration screen or a simple data-entry form. This is convenient when the interface is closely tied to the module's functionality.

**Theme-owned interface:** The theme provides the public-facing design and requests data from the module's API. This is usually preferable when the page must follow the site's overall appearance or when multiple themes should present the same module data differently.

A module may support **both** approaches. For example, MdBlog can include its own management Views while a separately developed blog theme uses MdBlog's API endpoints to present posts and categories.

## Before moving on

- Confirm that the View belongs to the module and has a descriptive filename.
- Save it under `Views/` or create it as **View** content through the backend.
- Register newly added local files through file synchronisation if required.
- Verify how the View is assigned, dispatched, and accessed in your installation.
- Keep data operations in Controllers, Services, and Models.
- Use module API endpoints for dynamic data when appropriate.
- Handle loading, empty, error, and authentication states in the interface.

Next, learn how to [Connect Views to Module APIs](connect-views-to-module-apis.md).

---

[Previous](define-module-routes-and-endpoints.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](connect-views-to-module-apis.md)
