# Validate Input with LtValidator

[Previous](handle-http-requests-with-ltrequest.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](return-api-responses-with-ltresponse.md)

*Section: Working with Core Services (MdLt)*

Use the documented [LtValidator service](../../appcore/LtValidator.md) for supported validation operations. Check the method signatures in that reference before integrating them into a controller or service.

MdBlog's category service currently checks that a trimmed category name is nonempty and rejects duplicate category names. Those checks are useful requirements, but they are **manual checks in MdBlog**, not evidence that MdBlog calls `LtValidator`.

## Practice

Define the required fields, formats, and duplicate checks for a blog category before attempting to insert it.

---

[Previous](handle-http-requests-with-ltrequest.md) · [Main documentation](../../README.md) · [Guide contents](README.md) · [Next](return-api-responses-with-ltresponse.md)
