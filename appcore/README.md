# LifeTech OCMS — MdLt Services Developer Guides

> **LifeTech OCMS core services** · `MdLt` · `v1.x`

These guides follow the teaching structure of the supplied `LtSession` document, with the requested introductory section omitted: Overview, Import the class, Quick start, Method reference, Practical module example, Common mistakes, Summary, and Source and navigation.

**Module scenarios:** Each implemented service now includes a controller-oriented scenario. Placeholder or incomplete files have an explicit non-implementation example. The LtSession page retains the supplied full controller example.

**Documentation accuracy:** The LtSession page retains its practical example and method reference, with the requested editorial updates. Other pages expand the previously inspected method inventories but do not claim unverified method contracts. Source-dependent operations should be checked against GitHub before publication.

## Table of contents

1. [CaseConverter](CaseConverter.md)
2. [LtAuth](LtAuth.md)
3. [LtComponentMgt](LtComponentMgt.md)
4. [LtDate](LtDate.md)
5. [LtFile](LtFile.md)
6. [LtLWToken](LtLWToken.md)
7. [LtMail](LtMail.md)
8. [LtModel](LtModel.md)
9. [LtNavigate](LtNavigate.md)
10. [LtRequest](LtRequest.md)
11. [LtResponse](LtResponse.md)
12. [LtRoute](LtRoute.md)
13. [LtService](LtService.md)
14. [LtSession](LtSession.md)
15. [LtSiteInfo](LtSiteInfo.md)
16. [LtValidator](LtValidator.md)
17. [TbContentService](TbContentService.md)
18. [TbLoginAuditService](TbLoginAuditService.md)
19. [TbMenuService](TbMenuService.md)
20. [TbModuleService](TbModuleService.md)
21. [TbPackageService](TbPackageService.md)
22. [TbPageContentService](TbPageContentService.md)
23. [TbPageSerice](TbPageSerice.md)
24. [TbPageService](TbPageService.md)
25. [TbResponseService](TbResponseService.md)
26. [TbRoleService](TbRoleService.md)
27. [TbThemeService](TbThemeService.md)
28. [TbUserService](TbUserService.md)
29. [displayError](displayError.md)
30. [tableManagementService](tableManagementService.md)

## Notes

- `LtMail.php` and `LtModel.php` were empty in the inspected branch.
- `LtDate.php` was incomplete.
- `TbPageSerice.php` and `TbPageService.php` are separate files.
- Methods requiring database models or authentication are not presented as standalone executable calls unless verified.
