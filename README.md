# Data Engineering Leadership Portfolio

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![AWS](https://img.shields.io/badge/cloud-AWS-orange.svg)](https://aws.amazon.com/)
[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://python.org/)
[![Scala](https://img.shields.io/badge/scala-2.13+-red.svg)](https://scala-lang.org/)

> **Exploring data engineering leadership challenges**  
> *A back-end engineer's perspective on scaling data systems and teams*

**Note**: This repository demonstrates my thinking about data engineering leadership roles as I transition from back-end engineering. The projects represent learning exercises and architectural explorations based on my production experience with distributed systems.

## What's in here?

This is my exploration of data engineering leadership challenges as I transition from back-end engineering to data engineering roles. Each project represents how I'd approach common technical and organizational problems based on my experience with distributed systems and data pipelines.

These are learning exercises and thought experiments, building on my background in Python, Scala, Apache Flink, and Kafka. The goal is to demonstrate how I think about scaling both technology and teams.

### What I focus on:
- **Building things that work**: I prefer solutions that actually run in production over perfect architectures
- **Working with teams**: Coordinating engineers, dealing with the usual project challenges
- **Business communication**: Explaining technical stuff to non-technical people (still working on this)
- **Maintainable code**: Writing infrastructure code that the next person can understand
- **Realistic planning**: Accounting for the fact that things will break and timelines will slip

## The Projects

### **A01: Building an AWS Data Platform from Scratch**
*How I'd approach the classic "we need a data platform" project*

This is my take on building a foundational AWS data platform, drawing from my experience with distributed systems and infrastructure deployment at Parcel Perform.

**The scenario**: 8 weeks, small team, mixed AWS experience, and stakeholders wanting regular updates.

**My approach**:
- AWS infrastructure design (VPC, EC2, EFS, RDS, S3) based on patterns I've used
- Terraform for infrastructure as code (similar to my CI/CD experience)
- Authentication system design (always comes up in real projects)
- Implementation timeline with realistic milestones
- Team coordination strategies from my mentoring experience

**Note**: This is a learning exercise exploring how I'd scale beyond the microservices and pipeline work I've done to a full platform architecture.

📁 **Files**: [`report_A01.md`](report_A01.md) • [`report_A01_prompt.md`](report_A01_prompt.md) • [`a_01/`](a_01/)

### **A02: Dask Distributed Computing Platform**
*When pandas runs out of memory but Spark feels like overkill*

Common scenario: data science team is outgrowing pandas but doesn't want to learn Spark. Dask seemed like a good middle ground, so I worked through how to actually deploy and manage it.

**The situation**: Small data science team needed to handle larger datasets without a complete rewrite of their existing pandas code.

**What I learned**: Dask works well when configured properly, but the deployment and cluster management pieces aren't trivial. Took some experimenting to get auto-scaling working reliably.

**The challenge**: Getting the team comfortable with distributed computing concepts while keeping their familiar pandas workflow.

📁 **Files**: [`report_A02.md`](report_A02.md) • [`report_A02_prompt.md`](report_A02_prompt.md) • [`a_02/`](a_02/)

### **A03: Metaflow ML Pipeline Platform**
*Trying to make MLOps work without making everyone miserable*

Most MLOps tools seem designed for people who love Kubernetes. Our data scientists just wanted to get their models into production without becoming infrastructure experts.

**The challenge**: Small ML team that knows Python and statistics, but every deployment was a manual process. Models would work fine in notebooks but break when moving to production.

**Why I chose Metaflow**: Netflix built it for data scientists, not platform engineers. The Python-first approach meant less context switching for the team.

**What happened**: Deployment got more predictable and the team spent less time debugging infrastructure issues. Not perfect, but much better than our previous manual process.

📁 **Files**: [`report_A03.md`](report_A03.md) • [`report_A03_prompt.md`](report_A03_prompt.md) • [`a_03/`](a_03/)



---

## Leadership & Team Development

### **B01: Vector Database Team Training**
*Explaining vector databases to a team that's never used them*

Vector databases started coming up in conversations, but our team hadn't worked with them before. I put together some training materials to get everyone up to speed.

**The situation**: Team familiar with SQL and some NoSQL, but vector databases and embeddings were new concepts. Needed to understand if/when we should actually use them.

**My approach**: Started with concrete use cases rather than the technical details. Built some simple examples that people could actually run and understand.

**What I learned**: The technical concepts weren't the hard part - it was figuring out when vector databases actually solve problems we have versus when they're just interesting technology.

📁 **Files**: [`report_B01.md`](report_B01.md) • [`report_B01_prompt.md`](report_B01_prompt.md) • [`b_01/`](b_01/)

### **B05: PMO Framework for Data Operations**
*Trying to make project management work for data projects*

Data projects don't fit neatly into standard project management frameworks. I've worked on adapting some PMO processes to work better with the exploratory nature of data work.

**The problem**: Standard project management expects predictable timelines, but data projects involve a lot of discovery. You don't know what you'll find in the data until you start looking at it.

**What I tried**: More structured discovery phases upfront, milestone-based planning instead of fixed timelines, and better communication about uncertainty and risk.

**What helped**: Being more explicit about the exploratory phases and setting expectations with stakeholders about what we can and can't predict in data projects.

📁 **Files**: [`report_B05.md`](report_B05.md) • [`report_B05_prompt.md`](report_B05_prompt.md) • [`b_05/`](b_05/)

---

## Tech Stack

**My current experience**:
- **Python & Scala** - my primary languages for web services and data processing
- **Apache Flink** - real-time stream processing (production experience)
- **Apache Kafka** - message streaming and event processing
- **PostgreSQL** - primary database, including query optimization and indexing
- **Django & FastAPI** - web framework experience
- **Docker & Kubernetes** - containerization and orchestration on AWS
- **AWS** - EC2, S3, Lambda, and other core services
- **GitLab CI/CD** - deployment pipelines and infrastructure automation

**Exploring for data engineering leadership**:
- **Terraform** - infrastructure as code beyond basic deployments
- **Airflow/Metaflow** - workflow orchestration at scale
- **Data warehouse architectures** - beyond operational databases
- **Team coordination tools** - scaling beyond individual contributor work

**Things I've learned from building production systems**:
- Simple solutions are usually better, even when complex ones are more interesting to build
- Good documentation and monitoring save more time than perfect code
- Many performance problems are actually database query problems
- The best architecture is the one your team can debug at 2 AM
- Over-engineering is tempting but rarely worth the complexity

**From mentoring and team collaboration**:
- People work better when they understand the business context
- Most production issues trace back to communication gaps
- Code reviews are opportunities for knowledge sharing
- Technical decisions should consider both engineering and business constraints
- Sometimes the hardest part is saying no to technically interesting but unnecessary features

## Repository Structure

This repository is organized as a portfolio demonstrating my approach to data engineering challenges:

**For employers/reviewers**: Each project shows how I think about technical architecture, team coordination, and project management. The reports include both implementation details and leadership considerations.

**Technical exploration**: If you want to examine the technical approaches, each folder contains detailed architecture documents and implementation notes.

## How it's organized

```
data_test/
├── a_01/    # AWS platform from scratch
├── a_02/    # Dask for distributed computing
├── a_03/    # MLOps with Metaflow
├── b_01/    # Teaching vector databases
└── b_05/    # PMO for data teams
```

Each project has:
- The main report (all the technical details)
- GenAI prompts (how I'd use AI to help with implementation)
- Project structure docs (because organization matters)

## About me

I'm **Minh T. Le**, a back-end engineer at Parcel Perform in Ho Chi Minh City, Vietnam. I've been working with distributed systems, building web services that handle 150M+ daily requests, and developing real-time data pipelines using Apache Flink and Kafka.

My background is in Python and Scala, with experience in PostgreSQL, Docker, Kubernetes, and AWS. I've also mentored junior developers and worked on system architecture decisions. Now I'm interested in transitioning to data engineering leadership roles.

This repository represents my exploration of data engineering challenges beyond just the technical implementation - thinking about team coordination, project management, and architectural decisions at scale.

**Contact**: letuanminh94@gmail.com | [LinkedIn](https://linkedin.com/in/your-profile) | Ho Chi Minh City, Vietnam

---

This project is MIT licensed - use whatever's helpful.