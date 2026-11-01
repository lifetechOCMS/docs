
# Auto-Create Model, Controller and Service

[Previous](add-new-module-content.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](sync-module-files.md)

*Section: Creating module components*

## What is Auto Create?

**Auto Create** is a LifeTechOCMS module-development feature that helps developers generate a **Model**, **Controller**, and/or **Service** from an existing database table.

Rather than creating each component manually, select a database table and choose the components you need.

The generated files provide a starting point; developers should review and extend them to implement the intended behaviour.

## Open Auto Create

1. Open the **Modules** area in LifeTechOCMS.
2. Select the module you want to develop, such as `MdStudent`.
3. On its **Module Content** page, click **Auto Create**.
4. The **Auto Create Model–Controller–Service** form opens.

![Auto Create Model, Controller and Service form](../images/auto-create-module-components.png)

## Complete the form

| Field or option | What to do |
| --- | --- |
| **Database Tables** | Choose an existing database table. This field is required. |
| **Create with: Model** | Generate the model component. |
| **Create with: Controller** | Generate the controller component. |
| **Create with: Service** | Generate the service component. |
| **Create Content** | Submit the selected components for creation. |
| **Close** | Close the form without submitting. |

You can select **one, two, or all three** component types according to your needs.

## Example: Generate components for a student table

Suppose you already have a database table named `tb_student` and a module named `MdStudent`.

1. Open `MdStudent` and click **Auto Create**.
2. Choose `tb_student` under **Database Tables**.
3. Check **Model**, **Controller**, and **Service**.
4. Click **Create Content**.
5. Review the generated resources in the module content list.

Following LifeTechOCMS naming conventions, the expected component names are:

```text
MdStudent/
├── Models/
│   └── TbStudent.php
├── Controllers/
│   └── TbStudentController.php
└── Services/
    └── TbStudentService.php
```

These names illustrate the project's naming conventions. Check the generated files in your installation to confirm their actual structure.

## What does each component do?

- **Model (`TbStudent.php`)** — represents and works with the data associated with the `tb_student` table.
- **Controller (`TbStudentController.php`)** — handles incoming requests and coordinates module operations.
- **Service (`TbStudentService.php`)** — contains business operations that the controller can call.

**Auto Create provides a starting structure, not a finished feature.** Review generated classes, methods, table mappings, validation, permissions, and error handling before production use.

## After creating the files

Inspect the generated content. If you have added or modified files directly in module folders, continue to [Sync Module Files](sync-module-files.md).

For component responsibilities, see [Understand the MVC Architecture](understand-the-mvc-architecture.md).

---

[Previous](add-new-module-content.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](sync-module-files.md)
  