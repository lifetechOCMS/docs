# Previewing a Theme

[Previous topic](19-edit-theme-package.md) · [Contents](README.md) · [Next topic](21-publishing-a-theme.md)

## On this page

- [Open Preview](#open-preview)
- [Check the first working result](#check-the-first-working-result)
- [Test pages and browser behaviour](#test-pages-and-browser-behaviour)

## Open Preview

1. Open the Themes Development list.
1. Locate ThemeStarter.
1. Select **Preview**.
1. Inspect the page and refresh it after saving code changes.

Preview is useful while developing; access and session rules still apply to the pages you open.

## Check the first working result

Use the theme's Preview action or open the configured page through LifeTechOCMS. Publish the theme and assign it to the required pages when ready; select it as the site's default theme if you want it to be the site's main design.

Confirm these results:

1. Home displays the shared header, Home card and footer.
1. Clicking the welcome button displays the message.
1. About uses the same design but displays its own text.
1. The navigation links open their configured routes.
1. The page remains readable on a narrow screen.

**You have completed a basic theme.** Sections [Understand the Default Layout and Custom Layouts](15-understand-the-default-layout-and-custom-layouts.md#understand-the-default-layout-and-custom-layouts) and [Connect Theme Views to Backend APIs](18-connect-theme-views-to-backend-apis.md#connect-theme-views-to-backend-apis) extend it with an alternative layout and backend data.

## Test pages and browser behaviour

Use Preview while developing. Check Home, About and any separate layout. Test links, the welcome button, narrow screens and API loading. In browser developer tools, Console shows JavaScript errors and Network shows request statuses.

Check that only one document wrapper and one dynamic insertion point appear in the chosen composition. For API views, test successful data, an empty response and a failed request.

**Expected result:** you have verified the design before using the publishing actions.

[Previous topic](19-edit-theme-package.md) · [Contents](README.md) · [Next topic](21-publishing-a-theme.md)
