# Understand the MVC Architecture

[Previous](sync-module-files.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-database-table-and-model.md)

*Section: Creating module content*

## What is MVC?

**MVC** stands for **Model–View–Controller**. It is a way to organize application code so that handling requests, working with data, and displaying information are not mixed into one file.

LifeTechOCMS module development uses **Model**, **Controller**, and **View** content, and also uses **Service** content to keep business operations separate from request handling. A module's routes connect incoming requests to the appropriate controller.

## Understand each content type

| Content | Main responsibility | Example in `MdBlog` |
| --- | --- | --- |
| **Model** | Represents and works with stored data, such as records in a database table. | `Models/TbBlogCategory.php` |
| **View** | Presents information to a visitor or administrator. It can request data from an API. | A blog category page in `Views/` |
| **Controller** | Receives a routed request, coordinates the operation, and returns a response. | `Controllers/TbBlogCategoryController.php` |
| **Service** | Holds the business operations used by controllers, keeping them reusable and easier to test. | `Services/TbBlogCategoryService.php` |
| **Routes** | Connects a URL and HTTP method to the correct controller action. | `Services/MdBlogRoutes.php` |

**Note:** A service is not one of the three letters in MVC. LifeTechOCMS uses it alongside MVC to organize business logic more clearly.

## How module content works together

For a request that retrieves blog categories, the typical backend flow is:

```text
HTTP request
     |
     v
Module routes (MdBlogRoutes.php)
     |
     v
Controller (TbBlogCategoryController)
     |
     v
Service (TbBlogCategoryService)
     |
     v
Model (TbBlogCategory)
     |
     v
Database
```

The result then travels back through the application as an API response. A **View** can call that API and display the categories on a page.

This diagram is a simplified explanation of responsibilities, not a claim that every request must pass through every layer. For example, some operations do not require a database query.

## Practical example: Blog categories

Imagine that a developer wants to show all blog categories on a page:

1. The **View** needs a list of categories to display.
2. It sends a request to the appropriate **module API endpoint**.
3. The **route** directs that request to the category **Controller**.
4. The **Controller** delegates the category operation to the **Service**.
5. The **Service** uses the **Model** to retrieve the relevant database records.
6. The Controller returns the result through the API, and the **View** displays it.

Separating these responsibilities makes it easier to update a page's design without changing database logic, or change a business rule without rewriting the interface.

## Where Auto Create fits in

The [Auto-Create Model, Controller and Service](auto-create-model-controller-service.md) feature can generate starting content from an existing database table. Developers can then review and extend the generated Model, Controller, and Service content as needed.

A **View** is a separate content type that developers can create using [Add New Module Content](add-new-module-content.md). The module route and any API integration must also be configured appropriately; generating content alone does not guarantee a complete working feature.

## Explore MdBlog

Review these source examples to see how the responsibilities are separated:

- [Category Controller](https://github.com/adedayoAdetunji/MdBlog/blob/main/Controllers/TbBlogCategoryController.php)
- [Category Service](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php)
- [Category Model](https://github.com/adedayoAdetunji/MdBlog/blob/main/Models/TbBlogCategory.php)

**Learning task:** Find the category controller, service, and model in `MdBlog`. Identify which content handles the request, which contains the operation, and which interacts with the data. Then explain how a View could display the returned categories.

## Next step

Continue to [Create a Database Table and Model](create-database-table-and-model.md) to begin applying this structure to your own module.

---

[Previous](sync-module-files.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](create-database-table-and-model.md)
