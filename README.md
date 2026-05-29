Implemented fix for Coverity CID 76205 in setCostBasisOnLot().

The previous costed=false assignment was being overwritten by later cost basis calculation logic before use. Updated the logic to return false immediately when the vendor marks the lot as not costed.

Validation completed:
- Local Gradle build passed
- Jenkins/CloudBees pipeline passed
- SonarQube Quality Gate passed
- Latest build console search shows no occurrence of CID 76205 / UNUSED_VALUE