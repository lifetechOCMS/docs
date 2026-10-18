# Basic Usage

[Previous](standard-response-structure.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · Next

Calling the method empty will return the default failure response:

PHP

'''

return LtResponse::json();

'''

**Example Success Response**

PHP

'''

return LtResponse::json(

   'success',    // responseResult

   200,          // responseCode

   200,          // responseCategory

   ['user' => $user] // responseData

);

'''

**Example Failure Response**

PHP

'''

return LtResponse::json(

   'fail',       // responseResult

   102,          // responseCode

   100,          // responseCategory

   null          // responseData

);

'''

**%%**The default values of LtResponse::json() intentionally reflect a failure state unless they are explicitly overridden by the developer. This ensures secure fail-closed behavior across the application.%%

Source: https://www.lifetech.host/hubs/Docs#basic-usage

[Previous](standard-response-structure.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · Next
