// Common rollup logic for CostBasisMethod.
// Copies delta value when current value is missing.
// Marks as VARIOUS when both values exist but are different.
private CostBasisMethod rollUpCostBasisMethod(CostBasisMethod currentValue,
                                              CostBasisMethod deltaValue) {
    if (currentValue == null && deltaValue != null) {
        return deltaValue;
    }

    if (currentValue != null
            && deltaValue != null
            && currentValue != deltaValue) {
        return CostBasisMethod.VARIOUS;
    }

    return currentValue;
}

buyDetail.setCostBasisMethod(
        rollUpCostBasisMethod(buyDetail.getCostBasisMethod(),
                deltaBuyDetail.getCostBasisMethod()));