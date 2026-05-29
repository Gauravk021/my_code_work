if (vendorDetailLot.getIndicators() != null
        && StringUtils.equals(vendorDetailLot.getIndicators().getViolationInd(),
        TaxLotDataVendorConstants.NOT_COSTED_INDICATOR_N)) {
    deltaSubtotal.setCostBasisComplete(false);
    return false;
}

boolean costed;