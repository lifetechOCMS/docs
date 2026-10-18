# Use Site Information and Helper Functions

[Previous](import-content-and-load-content.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](connect-theme-views-to-backend-apis.md)

## On this page

- [Other helpers used in your theme](#other-helpers-used-in-your-theme)
- [Use more site configuration helpers](#use-more-site-configuration-helpers)
- [Understand the URL and environment helpers](#understand-the-url-and-environment-helpers)

## Other helpers used in your theme

| **Function or method** | **Purpose** |
| --- | --- |
| ltSiteName() | Display the configured site name |
| ltSiteUrl() | Build site page links |
| ltSiteHostAddress() | Build navigation or redirect addresses |
| dddm::loadDynamicContent() | Display content assigned to the current page |
| ApiTokenDetails::backEndBaseUrl() | Find the configured backend API address |
| ApiTokenDetails::tokenName() | Find the application's token storage key |
| ltPluginPath() | Find the plugins parent URL for explicit file links |

When placing a PHP string into JavaScript, use json_encode so special characters are represented correctly:

```js
<script>
const siteAddress = <?= json_encode(
     ltSiteHostAddress(),
     JSON_HEX_TAG | JSON_HEX_AMP | JSON_HEX_APOS | JSON_HEX_QUOT
) ?>;

function goHome() {
     window.location.href = siteAddress.replace(/\/+$/, '') + '/ThemeStarter/Home';
}
</script>
```

json_encode is a PHP function; window.location.href is a browser property. The LifeTechOCMS helper supplies the site address. Test links against your configured routes, particularly when your installation uses a subfolder.

## Use more site configuration helpers

Site configuration helpers let you use saved website information without hardcoding it into each content file. Update the site settings, and your theme can display the configured values through these helpers.

| **Helper** | **Returned information** |
| --- | --- |
| ltSiteName() | Main website name |
| ltSiteTitle() | Site subtitle |
| ltSiteAlias() | Site alias or short name |
| ltSiteCopyright() | Configured copyright text |
| ltSiteLogo(), ltSiteFavicon() | Configured logo and favicon path or filename |
| ltSiteEmail(), ltSiteEmail2() | Primary and secondary email addresses |
| ltSitePhone(), ltSitePhone2() | Primary and secondary phone numbers |
| ltSiteAddress(), ltSiteAddress2() | Primary and secondary addresses |
| ltSiteOpenHour(), ltSiteClosedHour() | Opening and closing hours |
| ltSiteLinkedln(), ltSiteInstagram(), ltSiteFacebook() | Configured social links |
| ltSiteTwitter(), ltSiteYoutube() | Additional social links |

Use the exact function names. In the linked documentation, the LinkedIn helper is spelled ltSiteLinkedln(), with a lowercase l after Linked.

Display the site subtitle:

```html
<p><?= htmlspecialchars(ltSiteTitle(), ENT_QUOTES, 'UTF-8') ?></p>
```

Display contact information in a footer:

```html
<p>Email: <?= htmlspecialchars(ltSiteEmail(), ENT_QUOTES, 'UTF-8') ?></p>
<p>Phone: <?= htmlspecialchars(ltSitePhone(), ENT_QUOTES, 'UTF-8') ?></p>
<p><?= htmlspecialchars(ltSiteCopyright(), ENT_QUOTES, 'UTF-8') ?></p>
```

For a logo stored as a filename in the installation's uploads folder, the documentation demonstrates this pattern:

```html
<img src="<?= htmlspecialchars(
     rtrim(ltSiteUrl(), '/') . '/uploads/' . ltSiteLogo(),
     ENT_QUOTES, 'UTF-8'
) ?>" alt="Website logo">
```

Check how your logo setting is stored before adding a directory: a stored full URL or path should not have another uploads prefix added to it.

## Understand the URL and environment helpers

| **Helper** | **Purpose** |
| --- | --- |
| isHttps() | Returns whether the request is using HTTPS |
| ltDomain() | Returns the domain name |
| ltBaseUrl() | Returns the domain with its protocol |
| ltSiteUrl() | Returns the root URL of the LifeTechOCMS installation |
| ltThemePath() | Returns the themes parent URL |
| ltModulePath() | Returns the modules parent URL |
| ltPluginPath() | Returns the plugins parent URL |

Use **ltSiteUrl()** for installation-relative page links. Use a package parent helper for direct asset links and explicitly add the package folder name. These functions provide addresses; they do not replace content registration or page assignment.

Full helper reference: [LtSiteInfo and Site Helper Functions](../../functions-and-classes/ltsiteinfo-and-site-helper-functions/ltsiteinfo-and-site-helper-functions.md)

Source: https://www.lifetech.host/hubs/Docs#use-site-information-and-helper-functions

[Previous](import-content-and-load-content.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](connect-theme-views-to-backend-apis.md)
