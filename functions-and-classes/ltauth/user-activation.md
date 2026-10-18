# User Activation

[Previous](role-management.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](token-management.md)

**1.     activateUser($lifetech_general_id)**

**Used for:**

-  Admin forced login
- Post-verification login        
- System-level authentication

**Process:**

1. Fetch user
1.  Set session
1. Destroy expired tokens
1. Generate fresh LW token

```
LtAuth::activateUser($ltId);
```

Source: https://www.lifetech.host/hubs/Docs#user-activation

[Previous](role-management.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](token-management.md)
