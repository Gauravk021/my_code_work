public void updateSecurityTypeOnSecurity(Security security, String vendorSecurityType) {
    if (vendorSecurityType != null) {
        SecurityTypeMapping mapping = SECURITY_TYPE_MAPPING.get(vendorSecurityType);

        if (mapping != null) {
            security.setSecurityType(mapping.securityType);
            security.setSecurityTypeCategory(mapping.securityTypeCategory);
        } else {
            security.setSecurityType(SecurityType.OTH_Other);
            security.setSecurityTypeCategory(SecurityTypeCategory.OTHER);
        }
    }
}