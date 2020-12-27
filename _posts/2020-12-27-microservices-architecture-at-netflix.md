---
layout: post
title: "Microservices Architecture at Netflix!"
categories: development
tags: architecture best-practices
---

1. Client sends a Play request to Backend running on AWS. The request is handled by AWS Load balancer (ELB)

2. AWS ELB will forward that request to API Gateway Service running on AWS EC2 instances. That component, named Zuul, is built by the Netflix team to allow dynamic routing, traffic monitoring & security, etc

3. Application API component is the core business logic, in this scenario, the forwarded request from API Gateway Service is handled by Play API.

4. Play API will call a microservice or a sequence of microservices to fulfill the request.

5. Microservices are mostly stateless small programs, to control its cascading failure & enable resilience, each microservice is isolated from the caller processes by Hystrix.

6. Microservices can save to or get data from a data store during its process.

7. Microservices can send events for tracking user activities or other data to the Stream Processing Pipeline for either real-time processing of personalized recommendation.

8. The data coming out of the Stream Processing Pipeline can be persistent to other data stores such as AWS S3, Hadoop HDFS, Cassandra, etc.

Source: https://www.linkedin.com/posts/stevenouri_che-out-the-microservices-architecture-at-activity-6747796908284215296-RdGz
