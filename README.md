buyDetail.setInherited(
        rollUpBooleanField(buyDetail.isInherited(), deltaBuyDetail.isInherited()));

buyDetail.setGifted(
        rollUpBooleanField(buyDetail.isGifted(), deltaBuyDetail.isGifted()));

buyDetail.setWashSale30DayReplacement(
        rollUpBooleanField(buyDetail.isWashSale30DayReplacement(),
                deltaBuyDetail.isWashSale30DayReplacement()));

buyDetail.setWashSale90DayReplacement(
        rollUpBooleanField(buyDetail.isWashSale90DayReplacement(),
                deltaBuyDetail.isWashSale90DayReplacement()));

// Common rollup logic for boolean flags.
// Keeps the existing true value, or copies true from delta when current is false.
private boolean rollUpBooleanField(boolean currentValue, boolean deltaValue) {
    return currentValue || deltaValue;
}