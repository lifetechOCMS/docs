# Role Management

[Previous](session-and-state-management.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](user-activation.md)

**1.     getActiveUserRole()**

```
static function getActivateUserRole($user);
```

**Uses TbRoleService**

	 **Returns:**

- Comma-separated role IDs if active
-  "100" if no active role

**2.     getFormRole($formName)**

'''

LtAuth::getFormRole("DashboardForm");

'''

**Behavior:**

1.     Searches form in TbFormRole

2.     If found Ã¢â â returns encrypted role

3.     If not found:

- Inserts new record
- Assigns default anonymous role:

```
c81e728d9d4c2f
Returns:
	{
		 "encryptRole": "value"
	}
```

Source: https://www.lifetech.host/hubs/Docs#role-management

[Previous](session-and-state-management.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](user-activation.md)
