# Session and State Management

[Previous](authentication-methods.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](role-management.md)

**1.     check().**

```
LtAuth::check();
```

Returns:

-  true if user_id exists in session
-  false otherwise

**2.     user()**

	Retrieves authenticated session snapshot.

```
LtAuth::user();
```

Returns JSON containing:

- ltId
- surname
-  firstname
-  othername
- email
- phone
- role
- username
- hash
- salt

**3.     logout()**

```
LtAuth::logout();
```

**Actions:**

- Removes user_id
- Destroys session

**Returns:**

- true if session existed
- false otherwise

Source: https://www.lifetech.host/hubs/Docs#session-and-state-management

[Previous](authentication-methods.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](role-management.md)
