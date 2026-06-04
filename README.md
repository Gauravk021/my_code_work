Validation completed for DCR-21793.

Debug analysis confirmed that when TLE returns error code 12048 (“ACCOUNT NOT ON PROFILE”), the error is mapped to NF (Not Found), which results in a TleAccountNotFoundException being thrown.

The exception flow was verified as follows:

* TLE returned error code 12048.
* Error code mapping resolved to NF (Not Found).
* TleAccountNotFoundException was thrown.
* Exception handling mapped the response to a Not Found response.
* The Vendor Maintenance exception path was not executed.

Swagger validation confirmed the following response:

HTTP Status: 404 Not Found

Response:
{
“message”: “Vendor Data not found”
}

Note:
“Vendor Data not found” is the existing application response for account-not-found scenarios in the vendor system. No changes were made to this mapping as part of this story.

The purpose of this fix was to ensure that account-not-found scenarios are no longer incorrectly returned as “Vendor Maintenance Window” errors when the request is outside the vendor maintenance window.

Result:
Account-not-found scenarios now correctly return a 404 Not Found response with the existing “Vendor Data not found” message instead of being incorrectly returned as Vendor Maintenance Window errors.