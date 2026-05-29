Hi Abhishek, update on DCR-21186:

I addressed the SonarQube cyclomatic complexity issue for rollUpBuyDetail in TaxLotDataVendorToEjResponseMapper.

Previously, rollUpBuyDetail had repeated if/else blocks for rolling up fields such as activity desc, batch entry code, lot id, transaction id, process date, settlement date, trade date, gifted date, wash sale adjustment date, cost basis method, and boolean flags like inherited/gifted/wash sale replacement.

I refactored the repeated roll-up logic into small helper methods:

* rollUpStringField(...)
* rollUpCostBasisMethod(...)
* rollUpBooleanField(...)

These helpers preserve the same existing behavior:

* copy delta value when current value is missing
* mark as LIT_VARIOUS / VARIOUS when current and delta values are both present but different
* keep existing current value when no change is required
* preserve boolean roll-up behavior using logical OR

There is no intended business logic change. This is a refactoring-only change to reduce method complexity and remove duplicated conditional logic.

Validation completed:

* Local Gradle build successful
* Application startup successful
* Jenkins/Sonar analysis completed
* rollUpBuyDetail is no longer showing as an open Sonar issue
* Quality Gate is passing

Remaining Sonar issues are separate existing methods and can be handled separately:

* rollUpSellDetail
* updateSecurityTypeOnSecurity
* getBuyDetail