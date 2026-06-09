Update after cache-disabled local validation:

I disabled cache locally at code level and re-tested account 18818437 using the same request parameters. After cache was bypassed, the request went through the vendor path and executed getUnrealizedDataFromVendor(). The response showed numOfCallsToVendor = 1 and securities data was returned, so the HTTP 200 response is coming directly from vendor/TLE, not from cache.

My understanding from the code/debugging is:

* Vendor/TLE first returns either data or an error response.
* If vendor returns valid data, the normal success path continues and API returns 200.
* If vendor returns an Account Not Found/NF error, cbcommon maps it to TleAccountNotFoundException, which becomes 404 "Vendor Data not found".
* isTLEOutageWindow() does not force every successful vendor response to become Vendor Maintenance. It is only used in the error-handling path when vendor returns an error that is not already handled as NF/AccountNotFound.
* Therefore, forcing isTLEOutageWindow() to true helps reproduce maintenance behavior only for vendor error scenarios, not for successful data responses.

Current validation:

* Invalid account 28611427 → vendor returned NF/account-not-found path → 404 "Vendor Data not found".
* Valid account 18818437 with cache disabled → direct vendor call → vendor returned valid data → 200 response.