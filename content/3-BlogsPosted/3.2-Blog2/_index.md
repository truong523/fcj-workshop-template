---
title: "Blog 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b>3.2.</b> "
---

# Amazon SQS – When Speed Isn't Everything

When I first started learning about Amazon Web Services (AWS), I believed that the best system was simply the one that could process requests as quickly as possible. An API receives a request, processes it immediately, and returns a response—that sounded like the perfect design.

However, while building a **Flash Sale Ticket Booking System** and simulating thousands of users attempting to purchase tickets at the same time, I realized that **speed is not the most important factor**. What truly matters is whether the system can process every request **reliably without losing data or becoming overloaded**.

That was the moment I truly understood the value of **Amazon Simple Queue Service (Amazon SQS)**.

Instead of forcing the backend to process every request instantly, Amazon SQS acts as a **message queue**. Each request is stored safely in the queue, and workers such as **AWS Lambda** retrieve and process messages one by one.

This approach allows the system to remain stable even when traffic increases dramatically.

## Benefits I Experienced with Amazon SQS

- Prevents the system from becoming overloaded during sudden traffic spikes.
- Messages remain safely stored in the queue if backend services temporarily fail.
- Workers or Lambda functions can be scaled independently without changing the client application.
- Reduces dependencies between system components, making the architecture more flexible and easier to maintain.

What impressed me the most about Amazon SQS is not how fast it processes requests, but **how effectively it keeps the system reliable under heavy workloads**.

In the past, I often asked myself:

> *"How can I process requests as quickly as possible?"*

After learning more about AWS Event-Driven Architecture, my perspective changed:

> *"What would happen if my application suddenly received 10,000 requests within a single minute?"*

This small shift in thinking completely changed the way I design cloud applications.

From my experience, Amazon SQS is not only suitable for enterprise-scale systems but also provides significant value for many real-world applications, including:

- Flash Sale Ticket Booking Systems
- E-commerce Platforms
- Asynchronous Email Processing
- Image and Video Processing
- Data Synchronization
- Event-Driven Microservices
- AI Workflows and Background Jobs

Immediate processing is not always the best solution.

Sometimes, the most effective way to build a scalable and reliable system is simply **to let requests wait their turn**.

That is one of the most valuable lessons I learned while exploring and building cloud solutions with **Amazon SQS** on AWS.

---

## Architecture Diagram

![Amazon SQS Architecture](/images/3-Blog/Blog2.jpg)

*Source: Amazon Web Services*

---

## References

- **Amazon SQS Turns 20: Two Decades of Reliable Messaging at Scale**  
  https://aws.amazon.com/blogs/aws/amazon-sqs-turns-20-two-decades-of-reliable-messaging-at-scale/

- **Amazon SQS Developer Guide**  
  https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html

- **Amazon SQS Official Product Page**  
  https://aws.amazon.com/sqs/