# ALB

* Layer7 only which is HTTP
* Can balance to multiple applications on the same machine - such as containers
* Supports HTTP2 and Websocket
* Supports routing by URL, for example mysite.com/orders and mysite.com/products or by subdomain internal.mysite.com
* Includes port mapping which can help to direct to different ECS

** Use Case **
Where there are users searching, you can send traffic to one set of EC2s
When orders are placed, these can be sent to different EC2s


  
