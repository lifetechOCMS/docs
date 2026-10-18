# LtImport

Previous · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](import-target-order.md)

## On this page

- [Overview](#overview)

## Overview

Lifetech OCMS uses a custom import function called ltImport () to securely load files such as models, controllers, helpers, or other PHP resources from a specific module. This design promotes modularity, security, and a clean architecture by keeping each module strictly self-contained

**Syntax Example**

```
ltImport('ModuleName', 'FileName.ext');
ltImport('ModuleName', 'FileName.ext');
```

*This example loads the TbProduct.php file from the appropriate directory within the mdPosProduct module, depending on how it is registered in the database.*

Source: https://www.lifetech.host/hubs/Docs#ltimport

Previous · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](import-target-order.md)
