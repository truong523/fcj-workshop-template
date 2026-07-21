---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# ES, AN INTERN: WHEN THE "USER" OF THE DATABASE IS AN AI AGENT, NOT A FELLOW HUMAN BEING.

Lately, I've been researching GenAI and AI Agents, and today I stumbled upon a really compelling article on the AWS Partner Network Blog. After reading it, I gained a lot of new insights into infrastructure design, so I'd like to share my perspective as an intern and I'd greatly appreciate any guidance from experienced professionals!

Before, when working on major projects at school, I always thought that a database only needed to handle user requests (type a command ➡️ click Submit ➡️ wait for the result). Human speed is limited, so traffic was relatively manageable. But this blog post revealed a completely different reality as we move into the era of autonomous AI Agents.

In this era, "Users" are no longer humans but machines running continuous iterative processes (planning ➡️ executing ➡️ evaluating ➡️ revising). I casually issued a command like "Optimize the supply chain for me," and the AI ​​agent below automatically generated thousands of SQL statements, creating and deleting temporary schemas continuously every few seconds for testing.

The authors (all top SAs from AWS and PingCAP) pointed out three fatal headaches for traditional databases when faced with this situation:

Metadata Junk: Agents create/delete temporary tables indiscriminately, causing the system to easily run out of steam.

Unpredictable Traffic Fluctuations: Just after resting (idling), it jumps back to running in highly parallel mode as agents simultaneously aggregate data.

Economic Problem: Configuring fixed capacity to cover peak agent traffic means that when agents are idle, cloud costs continue to increase, which is very painful for businesses.

To solve this, they presented a Blueprint combining Amazon Bedrock (acting as the brain for the reasoning) and TiDB Cloud (the scalable database layer). I found their design for solving these problems incredibly clever:

Storage in one place, computation in another (Separate Compute & Storage): The original data remains securely stored on Amazon S3, while the compute nodes automatically scale up when the Agent is under heavy load and automatically scale down to the lowest level when the Agent is idle. It's a pay-as-you-use model, incredibly cost-effective!

The database can also be "Git Branched": Similar to how we use git branches to code new features, the AI ​​Agent can use TiDB Cloud's Serverless Branching feature to create its own independent database branch, allowing for schema testing or data experimentation without crashing the Production server. Once the branch is finished, it's done – extremely efficient.

All-in-One DB: Instead of an intern like me having to painstakingly build a database for transactions (OLTP), then build another one for analysis (OLAP), and then painstakingly configure a separate Vector DB for RAG... TiDB Cloud handles all three tasks in a single system. This reduces infrastructure fragmentation and minimizes latency for AI.

The article also mentions some impressive real-world use cases, such as a game that smoothly handles millions of players without manual database sharding, or Atlassian's Forge platform scaling over 3 million GB in a single cluster.

I'm still learning and gaining experience. I wonder if anyone here has actually implemented an AI Agent system or RAG model using Amazon Bedrock combined with TiDB Cloud (or similar architectures)? Could those of you who have experience please give me some reviews or advice?

Thank you very much!



(Reference article...)

https://aws.amazon.com/vi/blogs/apn/generative-ai-using-tidb-and-amazon-bedrock/

![Ảnh của bạn](/images/3-Blog/Blog1.jpg)