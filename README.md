buyDetail.setBatchEntryCode(
        rollUpStringField(buyDetail.getBatchEntryCode(), deltaBuyDetail.getBatchEntryCode()));

if (buyDetail.getBatchEntryCode() == null && deltaBuyDetail.getBatchEntryCode() == null) {
    buyDetail.setBatchEntryCode(TaxLotDataConstants.LIT_SPACE);
}