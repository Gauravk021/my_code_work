private static final class SecurityTypeMapping {
    private final SecurityType securityType;
    private final SecurityTypeCategory securityTypeCategory;

    private SecurityTypeMapping(SecurityType securityType, SecurityTypeCategory securityTypeCategory) {
        this.securityType = securityType;
        this.securityTypeCategory = securityTypeCategory;
    }
}