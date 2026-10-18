# Server-Side Rendering (PHP)

[Previous](loading-dynamic-menus.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](client-side-fetching-vanilla-js.md)

To turn that raw data into a visible menu on your website, the system uses a PHP script. While the code might look complex, it essentially performs a repetitive reading task (called a "loop") to stack the menus properly.

'''

use Lt\Modules\MdLt\Controllers\TbMenuController;

$menuInstance = new TbMenuController();

$menusNavigation = json_decode($menuInstance->isNavigation())->responseData;

foreach ($menusNavigation as $dataLayer1) {

  // Level 1: Loading.

  echo "Menu Name: ".$dataLayer1->menuName . ": level". $dataLayer1->menuLevel."";

  // Determine whether layer1 menu contains any child menus.

  $hasChildrenFromLayer1 = $dataLayer1->children;

  if (!empty($hasChildrenFromLayer1)) {

    foreach ($hasChildrenFromLayer1 as $dataLayer2) {

      // Level 2: Loading.

      echo "... Menu Name: ".$dataLayer2->menuName . ": level". $dataLayer2->menuLevel."";

      // Check whether this Level 2 menu has a child.

      $hasChildrenFromLayer2 = $dataLayer2->children;

      if (!empty($hasChildrenFromLayer2)) {

        // Level 3: Loading.

        foreach ($hasChildrenFromLayer2 as $dataLayer3) {

          // Level 3: Final navigation item (leaf node).

          echo "... ... Menu Name: ".$dataLayer3->menuName . ": level". $dataLayer3->menuLevel."";

        }

      }

    }

  }

}

'''

Source: https://www.lifetech.host/hubs/Docs#server-side-rendering-(php)

[Previous](loading-dynamic-menus.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](client-side-fetching-vanilla-js.md)
