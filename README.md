    @Bean
    public org.springframework.boot.web.client.RestTemplateCustomizer securityInterceptorCustomizer(
            @org.springframework.beans.factory.annotation.Autowired(required = false) ClientHttpRequestInterceptor securityInterceptor) {
        return restTemplate -> {
            if (securityInterceptor != null) {
                restTemplate.getInterceptors().add(securityInterceptor);
            }
        };
    }
