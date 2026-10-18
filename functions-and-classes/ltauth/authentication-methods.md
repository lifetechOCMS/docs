# Authentication Methods

[Previous](initialization.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](session-and-state-management.md)

All login methods sanitize inputs against XSS (using htmlspecialchars) and verify passwords securely via LtDdm::verifyPassword. Successful logins automatically destroy expired tokens, check if the user account is enabled, verify active roles, and insert a new LW-Token

**1.     login($username, $password = "")**

- Accepts either username OR email
- If password is empty- performs user existence check
-  If password provided- full authentication process

```
LtAuth::login('john', 'secret123');
```

**Password empty behavior:**

```
LtAuth::login('john');
```

**Returns:**

-  ltId if found 
-   "Record Not Found" if not

**2.     loginWithEmail($email, $password = "")**

- Validates email format using FILTER_VALIDATE_EMAIL
- Performs email-only authentication
-  Rejects invalid email format with code 1003

```
LtAuth::loginWithEmail('user@example.com', 'secret123');
```

**3.     loginWithUsername($username, $password = "")**

- Strict username authentication
- Filters by isEnabled = 1

```
  LtAuth::loginWithUsername('john', 'secret123');
```

4.     **loginWithId($id, $password)** 

-  Direct ID-based authentication
- Skips string-based lookup
- Verifies password against fetched user

```
LtAuth::loginWithId('176496897646211', 'secret123');
```

Source: https://www.lifetech.host/hubs/Docs#authentication-methods

[Previous](initialization.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](session-and-state-management.md)
