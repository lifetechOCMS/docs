# Auto-Create Model, Controller and Service

[Previous](add-new-module-content.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](understand-the-mvc-architecture.md)

*Section: Creating module components*

LifeTechOCMS provides **Auto Create** options to generate related files from a selected database table.

1. Open **Auto Create** in module development.
2. Select a table whose name begins with `tb_`, such as `tb_student`.
3. Select **Create with Model**, **Create with Controller**, and/or **Create with Service**.
4. Verify the generated filenames and class names.

| Generated resource | Expected name for `tb_student` |
|---|---|
| Model | `TbStudent.php` |
| Controller | `TbStudentController.php` |
| Service | `TbStudentService.php` |

The module's `MdStudentRoutes.php` is created when the module itself is created; it is not a Model-specific Controller or Service.

See the [original Auto Create guide](https://github.com/lifetechOCMS/docs/tree/master/backend-development/module-dev/auto-create-model-controller-service.md) for screenshots.

---

[Previous](add-new-module-content.md) · [Main documentation](../README.md) · [Guide contents](README.md) · [Next](understand-the-mvc-architecture.md)
