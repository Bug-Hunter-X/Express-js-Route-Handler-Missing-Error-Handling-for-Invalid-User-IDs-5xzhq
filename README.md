# Express.js Route Handler Missing Error Handling for Invalid User IDs

This repository demonstrates a common error in Express.js route handlers:  lack of error handling for invalid input.  Specifically, the provided code attempts to parse a user ID from a route parameter as an integer without validating the input. This can lead to unexpected behavior or crashes if the ID is not a valid number.

## Bug Description

The `/users/:id` route attempts to find a user based on the provided ID. However, it doesn't handle the case where `req.params.id` is not a valid integer.  Trying to parse a non-numeric string as an integer will result in `NaN`, leading to a `user` value of `undefined` and the failure to find a user, even if one exists with a valid numeric ID.  A more robust solution is required to gracefully handle these errors.

## Solution

The solution involves adding input validation to ensure that `req.params.id` is a valid integer before attempting to parse it.  Error handling is implemented to return a suitable HTTP status code (e.g., 400 Bad Request) and a descriptive error message when an invalid ID is provided.