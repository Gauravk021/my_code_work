Review the PR comment and my current implementation before making any changes.

Reviewer concern:
"RestTemplateCustomizer applies to every RestTemplate created via RestTemplateBuilder in the application context, not just the CRT client. cprCacheHttpFactory has its own interceptor/pool sizing/timeouts for unrelated HTTP clients and may cause unexpected socket exhaustion/pool connection refused errors in production under load. Is it okay to use cprCacheHttpFactory?"

Current implementation:
I added a RestTemplateCustomizer that sets cprCacheHttpFactory as the request factory.

I confirmed that CRT AuthorizationClientImpl receives Spring RestTemplateBuilder and internally creates its RestTemplate using:

this.restTemplate = restTemplateBuilder.build();

Requirement:
The connection/request factory configuration is needed for the CRT AuthorizationClient only. It must NOT modify unrelated RestTemplates such as cache-manager or other application HTTP clients.

Please:
1. Inspect the complete project and CRT authorization-client configuration/dependency.
2. Find how CRTAuthorizationClient / AuthorizationClientImpl is created and whether the CRT library provides an official configuration mechanism, dedicated RestTemplateBuilder, request factory, timeout properties, or extension point.
3. Determine whether my current RestTemplateCustomizer is global and could affect unrelated RestTemplates.
4. If yes, replace it with the smallest safe implementation that applies the required HTTP/request-factory configuration ONLY to CRT.
5. Do not change CRT library source code.
6. Do not change existing unrelated RestTemplate configuration.
7. Do not change business logic in RealizedDataService or UnrealizedDataService.
8. Keep the existing CRT authorization behavior unchanged.
9. Before editing files, explain exactly which files and lines you intend to change and why.
10. Do NOT make any code changes until I approve the proposed solution.