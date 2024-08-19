Note: Load Balancers allow distribution of traffic amongst **availability zones only** not across different regions

# ALB

* Layer7 only which is HTTP
* Can balance to multiple applications on the same machine - such as containers
* Supports HTTP2 and Websocket
* Supports routing by URL, for example mysite.com/orders and mysite.com/products or by subdomain internal.mysite.com
* Includes port mapping which can help to direct to different ECS

## Use Case
Where there are users searching, you can send traffic to one set of EC2s  
When orders are placed, these can be sent to different EC2s

ALBs can route and balance gRPC traffic. gRPC was created by Google and is an open source frameowrk allowing remote procedural calls.


# Gateway Load Balancer

Used to manage a fleet or 3rd party appliances which support the *GENEVE* protocol
GLB uses the 3rd layer of the OSI model (Network)
GENEVE:
- Stands for Generic Network Virtualization Encapsulation
- flexible tunneling protocol and encapsulates network traffic between endpoints
- Allows seamless integration between network devices (such as firewalls) and enhances scalability and flexibility
