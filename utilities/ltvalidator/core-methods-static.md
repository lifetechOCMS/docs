# Core Methods (Static)

[Previous](supported-validation-rules.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · Next

- **validate(array $data, array $rules)** The primary method used to validate data against your rule set.
- **Behavior on Failure:** If any rule fails, it populates the internal errors array, automatically echoes an LtResponse::json() payload containing the errors, and exits the script.
- **Behavior on Success:** If all rules pass, it simply returns true, allowing your controller to continue its execution.

PHP

```
$data = [
   'username' => 'admin',
   'email' => 'invalid-email',
   'age' => 'twenty'
];
 
$rules = [
   'username' => 'required|min:4|max:15',
   'email' => 'required|email',
   'age' => 'numeric'
];
 
// Executes validation. If it fails, the script stops here automatically.
LtValidator::validate((array)$data, $rules);
```

- **errors()** Returns an associative array of all validation errors encountered during the validation process. The array keys correspond to the failed field names.

*%% Because validate() automatically exits on failure, you typically only use this method if you are modifying the core class or executing partial checks. %%*

PHP

```
$errorList = LtValidator::errors();
```

- **passed()** Returns a boolean indicating whether the validation passed without any errors (true if empty, false if errors exist).

PHP

```
if (LtValidator::passed()) {
   // Safe to proceed
}
```

**Usage Example in a Controller** Because LtValidator::validate() handles the failure response internally, your controller logic remains incredibly clean:

PHP

```
public function registerUser(LtRequest $request) {
   // 1. Define Rules
   $rules = [
       'firstName' => 'required|min:2',
       'emailAddress' => 'required|email',
       'phoneNumber' => 'required|numeric'
   ];
   
   // 2. Validate (Stops execution and returns JSON if invalid)
   LtValidator::validate((array) $request, $rules);
   
   // 3. If execution reaches this line, the data is 100% valid.
   // Proceed with database insertion...
}
```

Source: https://www.lifetech.host/hubs/Docs#core-methods-(static)

[Previous](supported-validation-rules.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · Next
