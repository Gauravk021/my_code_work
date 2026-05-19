    public static void main(String[] args) {
        // This will print out the value directly to your console before the crash happens
        System.out.println("--- DIAGNOSTIC CHECK ---");
        System.out.println("BASE_URL: " + System.getProperty("crt.authorization.base_url"));
        System.out.println("CACHE_SIZE: " + System.getProperty("crt.authorization.cache.request.maximum_size"));
        System.out.println("------------------------");

        SpringApplication.run(TaxlotdataRestApplication.class, args);
    }