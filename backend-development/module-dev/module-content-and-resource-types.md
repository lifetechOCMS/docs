# Module Content/Component and Resource Types

[Previous](understand-module-folders-and-subfolders.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](add-new-module-content.md)

*Section: Getting started*

## Overview

A LifeTechOCMS module groups the resources required to implement a particular feature. For example, a blog module may need controllers to handle requests, models to access blog records, services to implement business rules, and views to display content.

This lesson introduces **what module resources do**. For the directory layout itself, see [Understand Module Folders and Subfolders](understand-module-folders-and-subfolders.md). Instructions for creating resources are covered in [Add New Module Content](add-new-module-content.md).

## Main module resource types

| Resource | Typical location | Responsibility |
| --- | --- | --- |
| Controller | `Controllers/` | Receives a routed request, coordinates application actions, and returns a response. |
| Model | `Models/` | Represents or accesses application data, commonly associated with a database table. |
| Service | `Services/` | Encapsulates reusable business logic and coordinates operations involving models or other services. |
| View | `Views/` | Contains presentation content that a module may render or make available to the application. |
| Supporting resources | `Media/`, `Storage/`, `ddm/`, `Export/` | Hold resources needed by a module for media, stored data, and other module-specific operations. Their precise use depends on the module. |

A module does not need to place every operation into every resource type. Choose the appropriate responsibility for each piece of functionality.

## Controllers

Controllers are the entry points for application actions reached through routes. A controller can receive request data, invoke a service, and return the result using LifeTechOCMS response conventions.

For a model named `TbBlogCategory`, the corresponding controller follows the naming convention `TbBlogCategoryController.php`.

Keep controllers focused on request handling. Reusable business rules belong in services rather than being duplicated across controllers.

## Models

Models provide the data-access layer. New LifeTechOCMS database tables use the `tb_` prefix and snake_case names. Their corresponding model classes use PascalCase:

| Database table | Model class | Model filename |
| --- | --- | --- |
| `tb_blog_category` | `TbBlogCategory` | `TbBlogCategory.php` |
| `tb_student` | `TbStudent` | `TbStudent.php` |

LifeTechOCMS models commonly extend the framework's `\LtModel` base class. Keep database access and data-related responsibilities in the model layer rather than embedding SQL directly in views.

## Services

Services implement reusable application behaviour, such as validating business conditions, coordinating records, or processing a workflow. A model-associated service uses the model name followed by `Service`.

For example, `TbBlogCategoryService.php` is the service associated with the `TbBlogCategory` model.

The automatically generated module route file, such as `MdBlogRoutes.php`, also lives in `Services/`. **It is a routing file, not a business service**, so it does not follow the `Service.php` filename suffix. Route configuration is explained in the dedicated routing lesson.

## Views

Views hold module presentation content. They are concerned with how information is displayed, not with implementing database operations or complex business rules.

LifeTechOCMS also supports theme development as a separate concern. A module's views and a theme's layouts or visual components should not be treated as interchangeable merely because both contribute to the final page. The way a particular view is rendered or integrated with a theme depends on the application's configuration and is addressed in later lessons.

## Supporting resources

A module may also contain resources outside the four primary code-oriented directories. For example, the standard module structure includes `Media/`, `Storage/`, `ddm/`, and `Export/`. These are **supporting directories**, not additional controller/model/service layers.

The MdBlog reference also demonstrates that supporting JavaScript and CSS may exist within `Services/`. Do not assume that every resource in that directory is a PHP service class; inspect its actual role.

## Optional developer-defined components

In addition to the main module resources, developers **may create optional components** when their module needs clearer separation of responsibilities. These are examples of custom PHP organization, not mandatory built-in LifeTechOCMS resource types.

| Optional component | Example | Purpose |
| --- | --- | --- |
| Traits | `Traits/HasSubscriptionStatus.php` | Share reusable methods among compatible classes. |
| Contracts / Interfaces | `Contracts/NewsletterSenderInterface.php` | Define a contract that multiple implementations can follow. |
| DTOs | `DTOs/SubscriberData.php` | Carry structured data between layers. |
| Exceptions | `Exceptions/SubscriptionException.php` | Represent module-specific errors. |
| Utilities | `Utilities/EmailNormalizer.php` | Group small, reusable helper logic. |
| Events / Listeners | `Events/SubscriberRegistered.php`, `Listeners/NotifySubscriber.php` | Organize event-related logic where supported by the application's event system. |

Use **PascalCase** for directory and PHP class/interface/trait names, and use PHP namespaces consistent with the module. For example:

```php
<?php
namespace Lt\Modules\MdNewsletter\Contracts;

interface NewsletterSenderInterface {
    public function send(string $email, string $subject, string $message): bool;
}
```

A service can reference the contract using `use Lt\Modules\MdNewsletter\Contracts\NewsletterSenderInterface;` and receive an implementation through its constructor. This is standard PHP composition; it does not require a special LifeTechOCMS component generator. Ensure new classes are discoverable by the project's autoloading setup.

Only create these directories when needed. They do not replace the module's required routing conventions or the core Controller, Model, Service, and View responsibilities.

## How resources work together

A typical request can be understood as the following sequence:

1. A route directs a request to a controller.
2. The controller invokes a service for the required application behaviour.
3. The service interacts with one or more models when data access is necessary.
4. The controller returns an API response or arranges presentation through a view, depending on the route's purpose.

This is a **conceptual example**, not a requirement that every LifeTechOCMS request must pass through all four resource types.

## Practical example: MdBlog

Use **MdBlog** as the reference module when exploring these responsibilities. For instance, the `TbBlogCategory` naming family illustrates how a database-backed feature can be divided between a model, controller, and service.

When reviewing the repository, check the actual public methods and route definitions before copying implementation details into a new module. Naming conventions alone do not establish a method's signature or behaviour.

## Learning task

Open the `Controllers/`, `Models/`, `Services/`, and `Views/` directories in MdBlog.

1. Identify one resource in each directory, where present.
2. Explain whether it handles requests, accesses data, applies business rules, or displays content.
3. Locate the module's `MdBlogRoutes.php` file and explain why it is different from a business service.
4. Consider which resource you would modify to add a new business rule without changing the page design.

## Continue learning

Next, see [Add New Module Content](add-new-module-content.md) for the resource-creation workflow.

---

[Previous](understand-module-folders-and-subfolders.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](add-new-module-content.md)
