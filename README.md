// Common rollup logic for String fields.
// Copies the delta value when current value is empty.
// Marks the field as VARIOUS when current and delta values are both present but different.
private String rollUpStringField(String currentValue, String deltaValue) {
    if (StringUtils.isEmpty(currentValue) && StringUtils.isNotEmpty(deltaValue)) {
        return deltaValue;
    }

    if (StringUtils.isNotEmpty(currentValue)
            && StringUtils.isNotEmpty(deltaValue)
            && !currentValue.equals(deltaValue)) {
        return TaxLotDataConstants.LIT_VARIOUS;
    }

    return currentValue;
}

buyDetail.setActivityDesc(
        rollUpStringField(buyDetail.getActivityDesc(), deltaBuyDetail.getActivityDesc()));