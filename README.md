import org.springframework.http.client.ClientHttpRequestInterceptor;
    @Bean
    public org.springframework.boot.web.client.RestTemplateBuilderClientHttpRequestInterceptorCustomizer securityInterceptorCustomizer(
            @org.springframework.beans.factory.annotation.Autowired(required = false) ClientHttpRequestInterceptor securityInterceptor) {
        return builder -> {
            if (securityInterceptor != null) {
                builder.additionalInterceptors(securityInterceptor);
            }
        };
    }
