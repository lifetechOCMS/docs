# Session Lifecycle Methods (Instance Methods)

[Previous](ltsession.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · Next

To completely start or terminate the session at the server level, you can use the non-static lifecycle methods by creating an instance of the class.

- **start()** Starts a new session or resumes an existing one.
- **Returns:** true if the session started successfully, otherwise false.

PHP

```
$session = new LtSession();
$session->start();
```

- **end()** Completely terminates the existing session. It destroys the session on the server, unsets all session variables, and deletes the session cookie from the user's browser.

PHP

```
$session->end();
```

**Static Session Operations** For day-to-day data storage and retrieval, LtSession utilizes static methods, meaning you do not need to instantiate the class to use them.

- **set($key, $value)** Sets a new item in the session.
- **Parameters:** Takes a $key (string) and a $value (mixed).

PHP

```
LtSession::set('user_role', 'Admin');
```

- **get($key)** Retrieves a specific item from the session.
- **Returns:** The stored value, or false if the key does not exist.

PHP

```
$role = LtSession::get('user_role');
```

- **has($key)** Checks if a specific session key is already set.
- **Returns:** true if the key exists, otherwise false.

PHP

```
if (LtSession::has('user_role')) {
   // Proceed with logic
}
```

- **all()** Retrieves the entire active session array.
- **Returns:** The complete $_SESSION global array.

PHP

```
$sessionData = LtSession::all();
```

- **forget($key)** Removes (unsets) a specific item from the session. If the key doesn't exist, it simply returns false.

PHP

```
LtSession::forget('user_role');
```

- **destroy()** Destroys all data registered to a session (wrapper for native session_destroy()).

*%%Unlike end(), this static method does not actively delete the browser cookie.%%*

PHP

```
LtSession::destroy();
```

**Quick Reference Usage Examples**

PHP

```
// Storing data
LtSession::set('status', 'loggedIn');
 
// Checking and retrieving data
if (LtSession::has('status')) {
   echo "Current status: " . LtSession::get('status');
}
 
// Removing specific data
LtSession::forget('status');
 
// Clearing the entire session globally
LtSession::destroy();
```

Source: https://www.lifetech.host/hubs/Docs#session-lifecycle-methods-(instance-methods)

[Previous](ltsession.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · Next
