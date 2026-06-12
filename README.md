Fix Account Not Found handling to prevent Vendor Maintenance error from being returned incorrectly.

Testing:
- Reproduced issue locally
- Verified Account Not Found scenario
- Reverted temporary outage window reproduction code
- Build successful