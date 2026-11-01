# Manage Authentication, Sessions and Permissions

[Previous](use-ltmodel-and-ltservice-for-database-operations.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](using-the-module-code-editor.md)

*Section: Working with Core Services (MdLt)*

LifeTech OCMS modules can use MdLt's `LtAuth`, `LtSession`, `LtLWToken`, and role-management services to identify users and protect operations. **Authentication** establishes who the user is; **session management** retains temporary state; **authorization** determines whether that user may perform a particular operation. These are separate checks.

## Import the MdLt libraries

```php
use Lt\Modules\MdLt\Services\LtAuth;
use Lt\Modules\MdLt\Services\LtSession;
use Lt\Modules\MdLt\Services\LtLWToken;
use Lt\Modules\MdLt\Services\LtResponse;
```

The imports above refer to actual MdLt classes. For an ordinary module, LifeTech's application bootstrap should already manage session initialization and the login lifecycle.

## Authentication with LtAuth

`LtAuth` offers static methods for logging in and checking the current login state:

| Method | Purpose |
| --- | --- |
| `LtAuth::login($username, $password)` | Authenticate using a username **or email address** and password. |
| `LtAuth::loginWithUsername($username, $password)` | Authenticate by username. |
| `LtAuth::loginWithEmail($email, $password)` | Authenticate by email. |
| `LtAuth::check()` | Check whether the session contains `user_id`. |
| `LtAuth::user()` | Return a LifeTech JSON response containing session-based user details, rather than a plain user object. |
| `LtAuth::logout()` | Clear the authentication session when `user_id` exists. |

For example, in an existing login endpoint:

```php
// Credentials must come from a validated, HTTPS-protected login request.
$result = LtAuth::login($username, $password);
// $result is a LifeTech JSON response string; do not wrap it in another JSON response.
return $result;
```

**Important:** Calling `LtAuth::login($username)` without a password follows a different branch in the current implementation: it looks up an account and returns an identifier. It is **not** a successful password-authenticated login. Supply the password for actual authentication.

## Protect a module endpoint

This example shows a simple authentication gate before calling a module service. It does not claim to enforce role-specific permission.

```php
<?php
namespace Lt\Modules\MdBlog\Controllers;

use Lt\Modules\MdLt\Services\LtAuth;
use Lt\Modules\MdLt\Services\LtResponse;
use Lt\Modules\MdBlog\Services\TbBlogCategoryService;

class ProtectedCategoryController
{
    public function index()
    {
        if (!LtAuth::check()) {
            return LtResponse::json(
                'Authentication required',
                '4000',
                '100'
            );
        }

        $service = new TbBlogCategoryService();
        return $service->index();
    }
}
```

*Illustrative controller:* adapt its name and route to your module. `4000` is an example from the mandatory **custom module response-code range `4000–5999`**; register a unique code in Response Management before use. Every application response code must have **exactly four digits**. Categories remain `200` (success) and `100` (failure).

## Work with LtSession

`LtSession` stores and retrieves values in PHP's `$_SESSION`. It is **not** a substitute for `LtAuth::check()` or permission verification.

```php
// Save a module-specific preference.
LtSession::set('mdBlogPageSize', 20);

// Read it later.
$pageSize = LtSession::has('mdBlogPageSize')
    ? LtSession::get('mdBlogPageSize')
    : 10;

// Remove it when no longer needed.
LtSession::forget('mdBlogPageSize');
```

Useful methods are `set($key, $value)`, `get($key)`, `has($key)`, `forget($key)`, and `all()`. In the current source, `get()` returns `false` if the key is absent. Avoid calling `start()`, `end()`, or `destroy()` inside routine module actions; session lifecycle and logout should remain coordinated with the framework.

### How MdBlog uses sessions

The actual `TbBlogCategoryService` constructor includes:

```php
$this->userId = LtSession::get('ltUid');
```

This demonstrates retrieving a user identifier from the session. **It does not establish that the request is authenticated or authorized.** Note that the inspected `LtAuth` implementation sets `user_id` during login, while this MdBlog example reads `ltUid`. Do not assume those keys are interchangeable: check your running application's identity/session configuration before relying on a particular key.

## Tokens and API authentication

MdLt also provides `LtLWToken` for lightweight access tokens:

- `LtLWToken::insertLwtToken($userId, $user_role, $expireTime)` issues a token.
- `LtLWToken::isValid($token, $expireTime)` validates a supplied token.
- `LtLWToken::destroy($token)` revokes a token.
- `LtLWToken::destroyExpiredToken()` cleans up expired tokens.

The normal login implementation already invokes token creation. Do not issue another token for every module request. For token-protected endpoints, obtain the token through the framework's configured request/authentication mechanism, validate it, and inspect the actual return structure before allowing the operation. **A valid token does not automatically grant every role permission.**

See [LtLWToken — Developer Guide](../../appcore/LtLWToken.md).

## Permissions and roles

LifeTech's `TbRoleService` includes `roleUserPermissionStatus($roles)`, which checks the `tb_role` table for enabled role IDs. The login implementation calls this check before activating the user's session. It returns a LifeTech JSON response, not a simple boolean.

This distinction matters:

1. **Authentication:** Has the user signed in? For session-based endpoints, use `LtAuth::check()`.
2. **Active role:** Is at least one assigned role enabled? The framework checks this through `TbRoleService::roleUserPermissionStatus()` during login.
3. **Operation permission:** Does the active role have access to **this particular route, content, or operation**? Enforce the configured permission for that resource on the server before calling the module service.

The inspected `TbRoleService::rolePermission()` updates role-related access columns across `tb_page`, `tb_menu`, and `tb_content`; it is an **administrative permission-changing operation**, not a generic read-only `can()` helper. Do not call it merely to check access. The reviewed MdLt files do not establish a single public `LtAuth::can($permission)` API, so this guide intentionally does not invent one. Consult the application's actual route/permission enforcement before adding a role-specific code example.

**Security rule:** Hiding a menu item or button is not authorization. Protect the backend endpoint itself. Do not trust a `roleId` or `userId` submitted by the browser as proof of permission.

## Practical MdBlog workflow

For a protected blog-category update, the intended order is:

1. Receive and validate HTTP input with `LtRequest` / `LtValidator`.
2. Verify authentication with `LtAuth` or the configured API-token authentication path.
3. Check the caller's permission for the category-management route/action using LifeTech's configured authorization layer.
4. Only then call the existing `TbBlogCategoryService::update($ltId)`.
5. Return the resulting LifeTech response without double-encoding it.

MdBlog currently reads `LtSession::get('ltUid')` in its category service, but that alone does not demonstrate steps 2 or 3. This guide therefore separates **observed MdBlog code** from the **recommended secure workflow**.

## Implementation notes

- The inspected `LtAuth::check()` specifically tests `LtSession::has('user_id')`; it does not verify a bearer token or a resource-specific permission.
- `LtAuth::user()` produces a JSON response and should not be treated as a raw user object. Its current implementation checks `ltId`, whereas `LtAuth::check()` checks `user_id`; verify your application's session setup before using it for identity retrieval.
- Avoid returning session contents, password hashes, salts, or tokens in module responses.
- Use HTTPS, validated credentials, and the framework's existing login/logout routes. Do not create a parallel authentication system inside a module.
- Reserve `4000–5999` for new module response codes; register each unique four-digit code in Response Management.

## Further reading

- [LtAuth — Developer Guide](../../appcore/LtAuth.md)
- [LtSession — Developer Guide](../../appcore/LtSession.md)
- [LtLWToken — Developer Guide](../../appcore/LtLWToken.md)
- [LtResponse — Developer Guide](../../appcore/LtResponse.md)
- [MdLt LtAuth source](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtAuth.php)
- [MdLt LtSession source](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/LtSession.php)
- [MdLt TbRoleService source](https://github.com/lifetechOCMS/MdLt/blob/v1.x/Services/TbRoleService.php)
- [MdBlog category service](https://github.com/adedayoAdetunji/MdBlog/blob/main/Services/TbBlogCategoryService.php)

---

[Previous](use-ltmodel-and-ltservice-for-database-operations.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](using-the-module-code-editor.md)
