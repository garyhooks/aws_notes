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
    * ALB
    * EC2 instance
    * S3 website (static S3 website)
    * any HTTP backend

# CloudFront vs S3 Cross Region Replication 

Cloudfront:
* Global Edge network
* Files are cached for a TTL
* Great for static content which must be available everywhere

S3 Cross Region Replication

