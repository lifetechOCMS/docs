# Token Management

[Previous](user-activation.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](last-access-tracking.md)

**On Every Successful Login:**

-  LtLWToken::destroyExpiredToken()
-  ApiTokenDetails::apiTokenExpiredTimeOut()
- LtLWToken::insertLwtToken()

Token name retrieved dynamically via:

```
ApiTokenDetails::tokenName();
```

Token stored in session as: ''' lwToken '''

Source: https://www.lifetech.host/hubs/Docs#token-management

[Previous](user-activation.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](last-access-tracking.md)
