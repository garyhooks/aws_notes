# CloudFront

* Content Delivery Network
* Caching website at the edge locations and increases speed
* Users therefore get a better experience
* DDoS protection due to it being spread out. Shield and WAF also provides protection.

### Origins

* S3 Bucket
    * Security provided with **Origin Access Control** (OAC)
    * Can also be used as an ingress - to upload files to S3
 
* Custom Origin (HTTP)
    * ALB (must be public... and EC2s can be private)
    * EC2 instance (must be public)
    * S3 website (static S3 website)
    * any HTTP backend
 
# Restricting contents based on user

* CloudFront signed URLs - good for access to single files
* Signed cookies - good for accessing lots of different files and content, such as subscriber areas
* Require users access content via CloudFront URLs

# CloudFront vs S3 Cross Region Replication 

Cloudfront:
* Global Edge network
* Files are cached for a TTL
* Great for static content which must be available everywhere

S3 Cross Region Replication:
* Must be set up for every region you want replication in
* Files are updated in NEAR real-time (NO CACHING)
* Great for dynamic content which changes a lot
* S3 CRR can be set up to automatically sync contents between different regions using repication rules

# CloudFront Geo Restriction

* Restrict based on country
* Allowlist to whitelist
* Blocklist to deny
* The country is determined using a 3rd party geo-IP database
* You can turn this on within security->Cloudfront Geographic restrictions

# Cache Invalidation

* If you update the backend, CloudFront does not know about it until the cache TTL expires
* You can force an entire or patial refresh by using **CloudFront Invalidation**
* Invalidate ALL files using * wildcard or special paths, using /images/*

# AWS Global Accelerator
  
* Scenario:
    * Global application but the application is only deployed to India
    * However, users are based everywhere and so this reduces latency and increases hops

### Unicast IP vs Anycast
**Unicast**: One server has a specific IP address  
**AnyCast IP**: All servers hold the same IP address, and the client is sent to the nearest one  
* Users are routed through edge locations through the internal AWS network  
* Works with:   
    * Elastic IP
    * EC2 
    * ALB
    * NLB

### Benefits of Anycast
* Healthchecks
* Great for disaster recovery
* Security as only two external IP addresses need whitelisting
* DDoS protection thanks to AWS Shield
   

# AWS Global Accelerator vs CloudFront

* Both use the AWS global network and edge locations
* Both integrate with Shield for DDoS protection

* CloudFront:
    * Improves performance due to caching
    * Dynamic content
    * Content served at the edge

* Global Accelerator:
    * Packets are proxied at the endge to applications inside the AWS network
    * No caching available
    * Use cases:  
        * Gaming, IoT, Voip
        * Anything needing a static IP address












