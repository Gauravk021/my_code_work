if (vendorSecurityType != null) {
    determineVendorDataType(vendorSecurityType);
    security.setSecurityType(determineSecurityType(vendorSecurityType));
    security.setSecurityTypeCategory(determineSecurityTypeCategory(vendorSecurityType));
}