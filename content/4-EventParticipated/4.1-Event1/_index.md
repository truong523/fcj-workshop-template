---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b>4.1.</b> "
---

# Workshop Report: "13-6 GenAI-powered App-DB Modernization"

## Workshop Objectives

The workshop was organized to introduce modern application design approaches and application modernization strategies on Amazon Web Services (AWS). The main topics focused on **Serverless Architecture**, **Event-Driven Architecture**, and AWS services that enable scalable, high-performance, and maintainable applications.

---

## Key Highlights

### Event-Driven Architecture

One of the main topics presented during the workshop was **Event-Driven Architecture (EDA)**.

This architecture allows system components to communicate through events rather than direct service calls, providing several advantages:

- Reduces dependencies between system components.
- Improves system scalability.
- Handles a large number of concurrent requests efficiently.
- Increases system resilience and fault tolerance.

The workshop also introduced several common communication patterns:

- Publish/Subscribe
- Point-to-Point Messaging
- Event Streaming

---

### AWS Serverless

The workshop explained the evolution of application deployment from traditional infrastructure to Serverless computing:

- Amazon EC2
- Amazon ECS
- AWS Fargate
- AWS Lambda

AWS Lambda was highlighted as an ideal solution for applications with dynamic workloads because it offers:

- No server management.
- Automatic scaling.
- Pay only for actual execution time.
- Seamless integration with other AWS services.

---

### Microservices Design

The workshop introduced the concept of **Domain-Driven Design (DDD)** for building Microservices architectures.

By separating applications into independent business domains, developers can:

- Simplify application development.
- Improve maintainability.
- Increase scalability.
- Minimize the impact of updates on other system components.

---

## Knowledge Gained

After attending the workshop, I learned:

- How to design systems using Event-Driven Architecture.
- The advantages of AWS Lambda in a Serverless environment.
- How message queues support asynchronous processing.
- The fundamentals of Microservices and Domain-Driven Design.
- Best practices for selecting appropriate AWS services for different business requirements.

---

## Application to My Project

The knowledge gained from this workshop was directly applied to my project, **Limited Event Ticket Booking System on AWS Serverless**.

Specifically:

- **Amazon API Gateway** receives ticket booking requests.
- **Amazon SQS** acts as a message queue to process requests asynchronously using an Event-Driven architecture.
- **AWS Lambda** executes the ticket booking business logic.
- **Amazon RDS PostgreSQL** stores ticket and user information while preventing overbooking by using database transactions and `SELECT ... FOR UPDATE`.
- **Amazon CloudWatch** monitors application logs and system performance.

Applying the Event-Driven architecture enables the system to handle thousands of concurrent ticket booking requests efficiently during Flash Sale events.

---

## Lessons Learned

This workshop helped me gain a deeper understanding of:

- Event-Driven Architecture on AWS.
- Serverless computing and automatic scaling.
- The importance of message queues in asynchronous processing.
- Modern application design for building scalable and highly available systems.

The knowledge acquired from this workshop provides a solid foundation for developing my AWS Serverless Flash Sale Ticket Booking System.
```