private ClosingCostBasisMethod rollUpClosingCostBasisMethod(
        ClosingCostBasisMethod currentValue,
        ClosingCostBasisMethod deltaValue) {

    if (currentValue == null && deltaValue != null) {
        return deltaValue;
    }

    if (currentValue != null
            && deltaValue != null
            && currentValue != deltaValue) {
        return ClosingCostBasisMethod.VARIOUS;
    }

    return currentValue;
}