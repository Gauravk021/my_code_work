    public static void main(String[] args) {
        // --- ADD THESE LINES RIGHT HERE ---
        System.setProperty("crt.authorization.base_url", "https://crt-authorization-rest.apps2.devjones.com/");
        System.setProperty("crt.authorization.cache.principal.initial_size", "128");
        System.setProperty("crt.authorization.cache.principal.maximum_size", "4096");
        System.setProperty("crt.authorization.cache.request.enabled", "true");
        System.setProperty("crt.authorization.cache.request.time-to-live", "5m");
        System.setProperty("crt.authorization.cache.request.maximum_size", "4096");
        // ----------------------------------

        // Your existing run command stays exactly the same:
        SpringApplication.run(TaxlotdataRestApplication.class, args);
    }