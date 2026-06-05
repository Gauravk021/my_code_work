Hi [Lead Name],

I reviewed Dwayne’s test result and compared it with our testing.

Our original test was done with account 28611427 using our tested parameter set, and we got 404 - Vendor Data not found, which confirmed that AccountNotFound is no longer getting converted to Vendor Maintenance Window.

Dwayne tested the same account with a different parameter combination (sysId=COS, positionType=LONG, etc.) and got From Cache: AccountNotFound. I also tried the same parameter combination locally and got the same result.

He also tested another account 18818437 with the same parameter combination and got a successful 200 response with actual data.

So currently, the difference seems to be due to the input parameter combination and/or account data availability, not necessarily the DCR fix itself.

Can you please confirm which exact parameter set should be considered valid for DCR-21793 validation? Once confirmed, I can retest both account scenarios with the same inputs and update Jira/client accordingly.