DCR-21793 Status:

Issue reproduced and analyzed. Root cause was traced to cos-cbcommon-tle. Verified that the updated cos-cbcommon-tle 1.3.3-SNAPSHOT containing the fix is being consumed by cos-taxlotdata-rest. Removed temporary debugging changes, fixed failing unit tests, and completed successful build validation. PR has been raised and is ready for review/verification.