# SQS

## Short Polling

* Is the Default
* Request checks the servers/shards that store the messages
* Immediately returns a result even if there are no messages

## Long Polling

* Can wait up to 20 seconds before returning with the messages 
* Attempts to retrieve all messages from servers in the queue
* Reduces the chance of missing messages and can return more per request. This can therefore make it more efficient when handling the messages.
  


#### Distributed Messaging System

There are 3 parts:
1) EC2 instances
2) SQS Queues
3) Messages in the Queue
