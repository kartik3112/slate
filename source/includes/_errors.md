# Errors

The Associate API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your Access Token is wrong or not provided.
403 | Forbidden -- For administrators only.
404 | Not Found -- The specified associate could not be found.
405 | Method Not Allowed -- You tried to access a API with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The associate requested has been removed from our servers.
418 | I'm a teapot.
422 | Unprocessable Entity -- Validation has been failed.
429 | Too Many Requests -- Requesting too many data! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
