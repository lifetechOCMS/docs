# Practical Usage Examples

[Previous](last-access-tracking.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · Next

**Example 1: Standard Login (Username or Email)**

```
$_POST['username'];
$password = $_POST['password'];
$response = LtAuth::login($username, $password);
return $response;
```

**Example 2: Email Login with Validation**

```
$response = LtAuth::loginWithEmail('admin@site.com', 'Admin@123');
if ($response->responseCode === "1002") {
   // Login success
}
If email invalid Ã¢â â returns 1003
```

**Example 3: User Existence Check (Without Password)**

```
$response = LtAuth::login('john_doe');
```

**Example 4: Retrieve Logged-In User Data**

```
$user = LtAuth::user();
```

Source: https://www.lifetech.host/hubs/Docs#practical-usage-examples

[Previous](last-access-tracking.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · Next
