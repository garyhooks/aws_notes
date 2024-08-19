# AWS WAF

* Remember this is **Layer 7** so it would not work for network level filtering

* Monitor HTTP(S) requests which are forwarded to either:
    * Amazon API Gateway
    * Amazon CloudFront
    * ALB
    * AppSync GraphQL API
    * Cognito User Pool

* Can be configured based on conditions, such as:
    * IP Address
    * Country involved
    * Header values
    * Strings in the URL
    * Request length
    * SQL Code (including SQL Injection)
    * Script attacks
    * Rate-based rules which counts occurrences, useful for DDoS protections

## Behaviours

1) Allow all requests except the ones you specify
2) Block all requests except the ones you specify
3) Count requests that match certain properties 

