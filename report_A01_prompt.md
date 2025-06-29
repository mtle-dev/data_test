---
title: report_a01_aws_data_platform_genai_strategic_prompts
---

# GenAI Strategic Prompts for AWS Data Platform Foundation - Technical Architecture & Leadership

---

## AWS Infrastructure Architecture Design Prompts

---

### AWS Data Platform Foundation Architecture

<details>
<summary>AI-Assisted AWS-Specific Infrastructure Design and Implementation Planning</summary>

---

#### AWS Data Platform Architecture Optimization Prompt

```
ROLE: Senior AWS Solutions Architect and Data Platform Lead

CONTEXT: Design a complete AWS Data Platform Foundation for a data engineering team with the following specific requirements:
- Foundation for future data processing workloads (Spark, Airflow, ML pipelines)
- User Linux systems on EC2 with specific sizing requirements
- NFS shared storage using Amazon EFS for collaborative work
- FreeIPA integration for centralized authentication and user management
- Complete Infrastructure as Code approach (Terraform + Ansible, no manual console work)
- 8-week implementation timeline with 3-4 engineer team

SPECIFIC AWS COMPONENTS TO DESIGN:
- EC2 Architecture: Master node (m5.large), Worker nodes (m5.xlarge), Dev instances (t3.medium)
- VPC Design: Multi-AZ, public/private subnets, security groups, NACLs
- EFS Configuration: Performance mode, throughput optimization, mount targets
- IAM Architecture: Roles, policies, instance profiles, cross-account access
- RDS Setup: PostgreSQL for metadata, backup strategy, security
- S3 Structure: Data lake buckets, lifecycle policies, encryption

INFRASTRUCTURE AS CODE REQUIREMENTS:
- Terraform modules: VPC, compute, storage, IAM, monitoring
- Ansible playbooks: Configuration management, application deployment
- State management: Remote backend, locking, environment separation
- Automation: No manual AWS console operations

TEAM COORDINATION NEEDS:
- Lead DevOps Engineer: Overall architecture and Terraform
- Systems Engineer: EC2, FreeIPA, networking
- Automation Engineer: Ansible, CI/CD, monitoring
- Platform Engineer: Data processing setup, user training

Provide a comprehensive AWS architecture design with specific instance types, storage configurations, networking setup, and detailed team coordination strategy for 8-week implementation.
```

#### EC2 and Compute Infrastructure Design Prompt

```
ROLE: AWS Infrastructure Architect and Compute Specialist

SCENARIO: Design the complete EC2 compute architecture for an AWS Data Platform Foundation serving 20-30 data engineers and data scientists.

EC2 ARCHITECTURE REQUIREMENTS:
- Master Node: m5.large (orchestration, job scheduling, metadata management)
- Worker Nodes: m5.xlarge with auto-scaling (2-6 instances based on workload)
- Development Environment: t3.medium for individual developer work
- Bastion Host: t3.micro for secure administrative access
- FreeIPA Server: t3.medium for authentication and directory services

STORAGE AND PERFORMANCE:
- EBS Configuration: gp3 volumes with encryption, sizing for each instance type
- EFS Integration: NFS mounts for shared storage, performance optimization
- Instance Store: Temporary storage strategy for high-performance workloads
- Backup Strategy: EBS snapshots, AMI creation, cross-region replication

AUTO SCALING AND AVAILABILITY:
- Auto Scaling Groups: Launch templates, scaling policies, health checks
- Multi-AZ Deployment: Instance distribution across availability zones
- Load Balancing: Application Load Balancer for web interfaces
- Spot Instances: Cost optimization strategy for non-critical workloads

SECURITY AND ACCESS:
- Security Groups: Layered security with specific port access controls
- IAM Instance Profiles: Least privilege access for AWS services
- SSH Key Management: Centralized through FreeIPA integration
- Network Access: Bastion host strategy, VPN considerations

TEAM IMPLEMENTATION COORDINATION:
- Week 1-2: VPC and networking setup (Systems Engineer lead)
- Week 3-4: EC2 instances and auto-scaling (All engineers)
- Week 5-6: Application configuration and integration testing
- Week 7-8: Performance tuning and production readiness

Design a complete EC2 architecture with specific configurations, automation strategies, and detailed team coordination for implementation over 8 weeks.
```

---

</details>

### Network Architecture and Security Design

<details>
<summary>AWS VPC Design and Security Architecture Strategic Planning</summary>

---

#### VPC and Network Architecture Design Prompt

```
ROLE: AWS Network Architect and Security Specialist

PROJECT: Design secure, scalable VPC architecture for AWS Data Platform Foundation supporting data engineering workloads.

VPC DESIGN REQUIREMENTS:
- CIDR Planning: 10.0.0.0/16 with room for growth and multi-region expansion
- Subnet Strategy: Public (NAT, Bastion), Private (Compute), Database (RDS, isolated)
- Multi-AZ Design: 3 availability zones for high availability and fault tolerance
- Routing: Internet Gateway, NAT Gateway, custom route tables
- DNS: Route 53 private hosted zones for internal service discovery

SECURITY GROUP ARCHITECTURE:
- Management SG: Bastion host, FreeIPA server, administrative access
- Compute SG: EC2 instances, internal communication, application ports
- Database SG: RDS access, restricted to compute and management tiers
- Load Balancer SG: External access points, SSL termination
- Monitoring SG: CloudWatch agents, log collection, metrics

NETWORK ACCESS CONTROL:
- NACLs: Subnet-level security controls as defense in depth
- VPC Flow Logs: Network traffic monitoring and security analysis
- AWS WAF: Web application firewall for public-facing endpoints
- Shield Standard: DDoS protection for internet-facing resources

CONNECTIVITY PATTERNS:
- Internet Access: Outbound through NAT Gateway in public subnets
- Internal Communication: Private IP addressing, service discovery via DNS
- Cross-AZ Traffic: Optimized routing, minimal latency between compute nodes
- External Integration: VPC Peering or Transit Gateway for future expansion

IMPLEMENTATION COORDINATION:
- Lead DevOps Engineer: Overall network design and Terraform modules
- Systems Engineer: Security groups, NACLs, routing tables
- Automation Engineer: Network monitoring, flow logs automation
- Platform Engineer: Application-specific networking requirements

Create a comprehensive VPC design with security groups, routing architecture, and team implementation strategy for 8-week deployment timeline.
```

#### FreeIPA Integration and Authentication Architecture Prompt

```
ROLE: Identity and Access Management Architect and Linux Systems Specialist

CHALLENGE: Design complete FreeIPA integration for AWS Data Platform Foundation providing centralized authentication for 20-30 users across multiple EC2 instances.

FREEIPA ARCHITECTURE REQUIREMENTS:
- Server Configuration: t3.medium instance in private subnet with backup/replica
- Domain Design: dataplatform.internal with integrated Certificate Authority
- User Management: LDAP directory, group-based access controls, password policies
- Service Integration: SSH key management, sudo rules, host-based authentication
- High Availability: Master-replica configuration across availability zones

INTEGRATION WITH AWS SERVICES:
- EC2 Instances: Automated domain joining during launch via user data scripts
- EFS Mounting: User home directories on shared NFS storage
- Application Authentication: LDAP integration for web applications and services
- Service Accounts: Automated processes and data pipeline authentication
- SSL/TLS: Certificate management and distribution through FreeIPA CA

AUTHENTICATION FLOW DESIGN:
- User Login: SSH key authentication via centralized key management
- Multi-Factor: Integration with TOTP/token-based second factor
- Service Access: Kerberos tickets for service-to-service authentication
- Application SSO: Single sign-on capabilities for web-based tools
- Audit Logging: Comprehensive authentication and authorization logging

AUTOMATION AND CONFIGURATION:
- Ansible Integration: FreeIPA client configuration automation
- User Provisioning: Automated account creation and group membership
- Key Rotation: SSH key rotation policies and automated deployment
- Backup and Recovery: FreeIPA database backup and disaster recovery

TEAM COORDINATION STRATEGY:
- Systems Engineer: FreeIPA server setup and domain configuration (Week 3-4)
- Automation Engineer: Client automation and user provisioning (Week 4-5)
- Platform Engineer: Application integration and user training (Week 6-7)
- Lead DevOps: Overall integration testing and troubleshooting support

Design a complete FreeIPA architecture with AWS integration, automation strategies, and detailed implementation coordination for enterprise-grade authentication.
```

---

</details>

---

## Infrastructure as Code Implementation Prompts

---

### Terraform Automation Strategy

<details>
<summary>AWS-Specific Terraform Module Design and State Management</summary>

---

#### Terraform Module Architecture Design Prompt

```
ROLE: Infrastructure as Code Architect and Terraform Expert

OBJECTIVE: Design comprehensive Terraform architecture for AWS Data Platform Foundation with modular, reusable, and environment-agnostic infrastructure code.

TERRAFORM PROJECT STRUCTURE:
```
terraform/
├── environments/
│   ├── dev/
│   ├── staging/
│   └── production/
├── modules/
│   ├── vpc/                    # Network foundation
│   ├── compute/               # EC2, Auto Scaling
│   ├── storage/               # EFS, S3, RDS
│   ├── iam/                   # Roles, policies
│   ├── security/              # Security groups, NACLs
│   └── monitoring/            # CloudWatch, alarms
└── shared/
    ├── backend.tf             # Remote state configuration
    ├── providers.tf           # AWS provider configuration
    └── variables.tf           # Global variables
```

MODULE DESIGN REQUIREMENTS:
- VPC Module: Complete networking with subnets, gateways, routing
- Compute Module: EC2 instances, launch templates, auto-scaling groups
- Storage Module: EFS file systems, S3 buckets, RDS databases
- IAM Module: Roles, policies, instance profiles with least privilege
- Security Module: Security groups, NACLs with layered defense
- Monitoring Module: CloudWatch dashboards, alarms, SNS topics

STATE MANAGEMENT STRATEGY:
- Remote Backend: S3 bucket with versioning and encryption
- State Locking: DynamoDB table for concurrent access prevention
- Environment Separation: Separate state files for dev/staging/production
- Module Versioning: Git tags and semantic versioning for stability

IMPLEMENTATION BEST PRACTICES:
- Variable Validation: Input validation and type constraints
- Output Values: Structured outputs for module composition
- Resource Tagging: Consistent tagging strategy for cost allocation
- Provider Versions: Pinned provider versions for reproducibility

TEAM COORDINATION:
- Lead DevOps Engineer: Module architecture and state backend setup
- Systems Engineer: VPC and security module development
- Automation Engineer: Compute and storage module implementation
- Platform Engineer: Monitoring and application-specific resources

Create a complete Terraform architecture with modular design, state management strategy, and team implementation coordination for 8-week delivery timeline.
```

#### Ansible Configuration Management Strategy Prompt

```
ROLE: Configuration Management Lead and Ansible Automation Expert

PROJECT: Design comprehensive Ansible automation for AWS Data Platform Foundation configuration management and application deployment.

ANSIBLE PROJECT ARCHITECTURE:
```
ansible/
├── inventories/
│   ├── production/
│   │   ├── hosts.yml          # Static inventory
│   │   ├── aws_ec2.yml        # Dynamic inventory
│   │   └── group_vars/
│   └── development/
├── roles/
│   ├── common/                # Base system configuration
│   ├── freeipa_server/        # FreeIPA server setup
│   ├── freeipa_client/        # Domain joining automation
│   ├── nfs_client/            # EFS mounting and configuration
│   ├── data_processing/       # Spark, Docker, applications
│   ├── monitoring/            # CloudWatch agent, logging
│   └── security/              # Hardening, compliance
├── playbooks/
│   ├── site.yml               # Master playbook
│   ├── infrastructure.yml     # Infrastructure setup
│   ├── applications.yml       # Application deployment
│   └── maintenance.yml        # Ongoing maintenance
└── group_vars/
    ├── all.yml                # Global variables
    ├── master.yml             # Master node specific
    └── workers.yml            # Worker node specific
```

ROLE DEVELOPMENT REQUIREMENTS:
- Common Role: Base packages, security hardening, CloudWatch agent
- FreeIPA Server: Domain controller setup, CA configuration, user management
- FreeIPA Client: Domain joining, SSH key management, home directories
- NFS Client: EFS mounting, performance tuning, shared storage setup
- Data Processing: Docker, Spark, Jupyter, development tools installation
- Monitoring: Log configuration, metrics collection, alerting setup

DYNAMIC INVENTORY INTEGRATION:
- AWS EC2 Plugin: Automatic instance discovery based on tags
- Grouping Strategy: Role-based groups (master, workers, development)
- Variable Assignment: Instance-specific variables from EC2 tags
- Cache Configuration: Inventory caching for performance optimization

DEPLOYMENT AUTOMATION:
- Rolling Updates: Zero-downtime application deployments
- Health Checks: Service validation after configuration changes
- Rollback Procedures: Automated rollback for failed deployments
- Testing Integration: Molecule testing for role validation

TEAM IMPLEMENTATION STRATEGY:
- Automation Engineer: Role development and playbook orchestration (Week 4-6)
- Systems Engineer: FreeIPA integration and security hardening (Week 3-5)
- Platform Engineer: Application deployment and user tools (Week 5-7)
- Lead DevOps: Integration testing and deployment pipeline (Week 6-8)

Design a comprehensive Ansible automation strategy with role-based architecture, dynamic inventory, and team coordination for infrastructure configuration management.
```

---

</details>

### Storage and Data Architecture

<details>
<summary>Amazon EFS and S3 Data Lake Architecture Design</summary>

---

#### Amazon EFS Architecture and Performance Optimization Prompt

```
ROLE: AWS Storage Architect and Performance Engineering Lead

CHALLENGE: Design high-performance Amazon EFS architecture for AWS Data Platform Foundation supporting collaborative data science work and shared storage needs.

EFS ARCHITECTURE REQUIREMENTS:
- File System Configuration: Regional EFS with General Purpose performance mode
- Throughput Mode: Provisioned throughput for consistent performance (1 GB/s baseline)
- Storage Classes: Standard for active files, Infrequent Access for archival
- Encryption: Encryption at rest using AWS KMS, encryption in transit via TLS
- Backup Strategy: AWS Backup integration with cross-region replication

MOUNT TARGET DESIGN:
- Multi-AZ Deployment: Mount targets in each private subnet for high availability
- Security Groups: NFS traffic (port 2049) from compute instances only
- DNS Configuration: EFS file system DNS names for automatic failover
- Performance Optimization: Connection optimization using EFS utilities

CAPACITY AND PERFORMANCE PLANNING:
- Initial Capacity: 10 TB with automatic scaling based on usage
- Performance Scaling: Throughput scales with storage size (50 MB/s per TB)
- Burst Credits: Understanding burst credit system for temporary high throughput
- Monitoring: CloudWatch metrics for throughput, IOPS, and client connections

INTEGRATION WITH COMPUTE:
- EC2 Mount Strategy: Automated mounting via Ansible during configuration
- User Home Directories: Individual user directories with quota management
- Shared Project Spaces: Team collaboration areas with appropriate permissions
- Application Data: Temporary processing data and shared datasets

CLIENT OPTIMIZATION:
- EFS Utils: Installation and configuration for optimized performance
- Mount Options: Performance-optimized mount options for different use cases
- Caching Strategy: Client-side caching for frequently accessed files
- Connection Pooling: Multiple connections for high-throughput applications

BACKUP AND DISASTER RECOVERY:
- Automatic Backups: Daily backups with configurable retention periods
- Point-in-Time Recovery: Restore capabilities for accidental deletion/corruption
- Cross-Region Backup: Disaster recovery backups in secondary region
- Testing Procedures: Regular backup restore testing and validation

TEAM IMPLEMENTATION COORDINATION:
- Systems Engineer: EFS setup and mount target configuration (Week 4)
- Automation Engineer: Client mounting automation and optimization (Week 5)
- Platform Engineer: User directory setup and application integration (Week 6)
- Lead DevOps: Performance monitoring and backup configuration (Week 7)

Design a comprehensive EFS architecture with performance optimization, backup strategy, and team implementation plan for shared storage foundation.
```

#### S3 Data Lake Architecture and Lifecycle Management Prompt

```
ROLE: Data Lake Architect and S3 Storage Specialist

MISSION: Design comprehensive S3 data lake architecture for AWS Data Platform Foundation supporting current and future data processing workflows.

S3 BUCKET ARCHITECTURE:
```
data-platform-foundation/
├── raw/                       # Landing zone for ingested data
│   ├── year=2025/month=06/    # Partitioned by date
│   └── source=system_name/    # Partitioned by source system
├── processed/                 # Cleaned and processed data
│   ├── year=2024/month=01/
│   └── dataset=customer_data/
├── curated/                   # Business-ready analytics data
│   ├── domain=finance/
│   └── domain=marketing/
├── archive/                   # Long-term archived data
│   └── year=2020-2022/
└── temp/                      # Temporary processing data
    └── job_id=12345/
```

SECURITY AND ACCESS CONTROL:
- Bucket Policies: Environment-specific access controls with least privilege
- IAM Integration: Role-based access for different user types and applications
- Encryption Strategy: Server-side encryption with AWS KMS, bucket-level keys
- Access Logging: S3 access logs for security auditing and compliance
- Cross-Region Replication: Disaster recovery and data locality optimization

LIFECYCLE MANAGEMENT:
- Storage Classes: Standard → Standard-IA → Glacier → Deep Archive transition
- Lifecycle Policies: Automated transitions based on data age and access patterns
- Deletion Policies: Automatic cleanup of temporary processing data
- Cost Optimization: Storage class analysis and optimization recommendations

PERFORMANCE OPTIMIZATION:
- Request Patterns: Prefix distribution for high request rate performance
- Transfer Acceleration: CloudFront integration for global data access
- Multipart Upload: Large file upload optimization and resume capabilities
- Parallel Processing: S3 Select and parallel data processing patterns

DATA GOVERNANCE:
- Tagging Strategy: Cost allocation, data classification, retention policies
- Data Catalog: AWS Glue integration for metadata management
- Data Quality: Validation and quality checks during ingestion
- Compliance: Data retention, deletion, and audit trail requirements

INTEGRATION WITH PLATFORM:
- EC2 Access: S3 access from compute instances via IAM roles
- Data Processing: Spark integration for large-scale data processing
- ETL Pipelines: Future Airflow integration for workflow orchestration
- Analytics Tools: Query access via Athena and future BI tools

TEAM IMPLEMENTATION STRATEGY:
- Platform Engineer: Bucket structure and lifecycle policy setup (Week 2-3)
- Systems Engineer: Security configuration and IAM integration (Week 3-4)
- Automation Engineer: Terraform automation and monitoring setup (Week 4-5)
- Lead DevOps: Performance optimization and disaster recovery testing (Week 7-8)

Design a complete S3 data lake architecture with governance, performance optimization, and team coordination for scalable data storage foundation.
```

---

</details>

---

## Team Leadership and Project Management Prompts

---

### 8-Week Implementation Coordination

<details>
<summary>Project Timeline Management and Team Coordination Strategy</summary>

---

#### 8-Week Project Timeline and Milestone Management Prompt

```
ROLE: Technical Project Manager and Infrastructure Delivery Lead

PROJECT: Coordinate 3-4 engineers through 8-week AWS Data Platform Foundation implementation with specific milestones and deliverables.

TEAM COMPOSITION:
- Lead DevOps Engineer: Overall architecture, Terraform, AWS services coordination
- Systems Engineer: EC2, FreeIPA, networking, security configuration
- Automation Engineer: Ansible, CI/CD, monitoring, configuration management
- Platform Engineer: Data processing setup, user tools, documentation, training

8-WEEK DELIVERY TIMELINE:

WEEK 1-2: FOUNDATION SETUP
Milestones:
- AWS account configuration and billing setup
- Terraform backend infrastructure (S3, DynamoDB)
- VPC creation with subnets, gateways, routing
- Security groups and NACLs baseline configuration
- Initial team training on AWS services and architecture

Team Assignments:
- Lead DevOps: Terraform backend, VPC module development
- Systems Engineer: Security group design, network architecture validation
- Automation Engineer: Ansible project structure, inventory setup
- Platform Engineer: Requirements gathering, user needs analysis

Daily Coordination:
- Morning standup: Progress, blockers, dependencies
- Technical deep-dive sessions: Architecture decisions
- End-of-day: Risk assessment, next-day planning

WEEK 3-4: CORE INFRASTRUCTURE
Milestones:
- EC2 instances deployed with auto-scaling
- FreeIPA server setup and domain configuration
- EFS file system creation and mount targets
- RDS database setup for metadata storage
- Basic monitoring and alerting configuration

Team Assignments:
- Lead DevOps: EC2 Terraform modules, overall integration
- Systems Engineer: FreeIPA server deployment and configuration
- Automation Engineer: EC2 configuration automation, basic monitoring
- Platform Engineer: EFS setup, storage architecture validation

Coordination Focus:
- Cross-team dependencies: FreeIPA integration with EC2 instances
- Integration testing: Component interaction validation
- Risk mitigation: Backup plans for complex integrations

WEEK 5-6: INTEGRATION AND AUTOMATION
Milestones:
- FreeIPA client configuration on all EC2 instances
- NFS mounting and shared storage operational
- Application deployment automation functional
- User account provisioning and access controls
- Comprehensive monitoring and logging

Team Assignments:
- Lead DevOps: End-to-end integration testing, troubleshooting
- Systems Engineer: User management, SSH key automation
- Automation Engineer: Complete Ansible playbook development
- Platform Engineer: Data processing tools installation, user setup

Quality Assurance:
- Integration testing protocols
- Security validation and penetration testing
- Performance benchmarking and optimization
- Documentation review and updates

WEEK 7-8: PRODUCTION READINESS
Milestones:
- Full system testing and validation
- Performance optimization and tuning
- Disaster recovery testing and procedures
- User training and documentation completion
- Production deployment and go-live

Team Assignments:
- Lead DevOps: Production deployment, final integration validation
- Systems Engineer: Security hardening, compliance validation
- Automation Engineer: Operational procedures, monitoring refinement
- Platform Engineer: User training, documentation, support procedures

Success Validation:
- End-to-end functionality testing
- Performance meets requirements
- Security and compliance validation
- User acceptance and training completion
- Operational procedures documented and tested

Create a detailed 8-week project plan with daily coordination frameworks, milestone tracking, and team assignment strategies for successful platform foundation delivery.
```

#### Technical Risk Management and Team Development Prompt

```
ROLE: Technical Risk Manager and Engineering Leadership Development Specialist

CHALLENGE: Manage technical risks and develop team capabilities during AWS Data Platform Foundation implementation while maintaining 8-week delivery timeline.

RISK ASSESSMENT AND MITIGATION:

HIGH-IMPACT TECHNICAL RISKS:
1. FreeIPA Integration Complexity
   - Risk: Authentication integration more complex than expected
   - Probability: Medium | Impact: High
   - Mitigation: Dedicated test environment, backup authentication method
   - Owner: Systems Engineer with DevOps support

2. EFS Performance Limitations
   - Risk: NFS performance doesn't meet user expectations
   - Probability: Low | Impact: Medium
   - Mitigation: Performance testing, provisioned throughput option
   - Owner: Platform Engineer with architecture review

3. Terraform Module Dependencies
   - Risk: Complex dependencies cause deployment failures
   - Probability: High | Impact: Medium
   - Mitigation: Modular testing, isolated deployment validation
   - Owner: Lead DevOps Engineer

TEAM SKILL DEVELOPMENT INTEGRATION:

WEEK 1-2: AWS FUNDAMENTALS
- Daily Learning: 30-minute AWS service deep-dives
- Hands-on Labs: Account setup, basic service interaction
- Team Sharing: Best practices and lessons learned
- Skill Assessment: Practical exercises and knowledge validation

WEEK 3-4: INFRASTRUCTURE AS CODE MASTERY
- Terraform Training: Module development, state management
- Ansible Workshops: Role creation, playbook orchestration
- Code Reviews: Peer learning and quality improvement
- Documentation: Architecture decision records and runbooks

WEEK 5-6: INTEGRATION AND SECURITY
- Security Best Practices: AWS security model, compliance
- Troubleshooting Skills: Debugging complex integrations
- Performance Optimization: Monitoring, tuning, optimization
- Team Collaboration: Cross-functional problem solving

WEEK 7-8: OPERATIONAL EXCELLENCE
- Monitoring and Alerting: Observability best practices
- Incident Response: Problem resolution and communication
- Knowledge Transfer: Documentation and training others
- Continuous Improvement: Post-implementation optimization

CONTINGENCY PLANNING:

FALLBACK STRATEGIES:
- Manual AWS Console: Emergency procedures for Terraform failures
- Alternative Authentication: Backup methods if FreeIPA issues
- Performance Alternatives: Backup storage solutions for EFS problems
- Timeline Buffers: 15% buffer time for complex integrations

TEAM COORDINATION DURING RISKS:
- Daily Risk Reviews: Morning standup risk assessment
- Escalation Procedures: When to involve external experts
- Communication Protocols: Stakeholder updates during issues
- Learning Integration: Turn problems into learning opportunities

SUCCESS METRICS:
- Technical Delivery: Platform functional within 8-week timeline
- Team Development: Skill advancement measurable through assessments
- Risk Management: Proactive identification and resolution
- Knowledge Transfer: Documentation quality and team knowledge retention

Design a comprehensive risk management strategy with integrated team development, contingency planning, and coordination frameworks for successful platform delivery and capability building.
```

---

</details>

### Stakeholder Communication and Business Alignment

<details>
<summary>Executive Communication and Business Value Translation</summary>

---

#### Executive Stakeholder Communication Strategy Prompt

```
ROLE: Technical Executive Communicator and Business Value Translator

OBJECTIVE: Develop comprehensive communication strategy for explaining AWS Data Platform Foundation progress to business leaders throughout 8-week implementation.

EXECUTIVE COMMUNICATION FRAMEWORK:

WEEKLY EXECUTIVE SUMMARY TEMPLATE:
```
AWS Data Platform Foundation - Week X Implementation Progress

🎯 OVERALL STATUS: X% Complete | Status: On Track/At Risk/Behind Schedule

✅ COMPLETED THIS WEEK:
• [Technical Achievement] → [Business Value Translation]
• VPC and networking setup → Secure foundation for data processing with enterprise-grade isolation
• FreeIPA authentication deployed → Centralized user management with audit capabilities and security compliance

🚧 IN PROGRESS:
• Current technical focus areas and expected business impact
• Timeline expectations and milestone dependencies

⚠️ RISKS AND MITIGATION:
• Technical challenges with clear resolution plans
• Resource or timeline concerns with mitigation strategies

💰 BUDGET AND RESOURCE STATUS:
• Current spend: $X of $Y budgeted (X% utilization)
• Resource allocation efficiency and optimization opportunities

📊 KEY METRICS:
• Infrastructure Availability: X% (Target: 99.9%)
• Security Compliance: X% complete
• Team Productivity: On track for 8-week delivery

🎯 NEXT WEEK PRIORITIES:
• Technical milestones with business impact
• Key decisions required from stakeholders
```

BUSINESS VALUE TRANSLATION MATRIX:

TECHNICAL ACHIEVEMENT → BUSINESS VALUE:
• "EC2 compute infrastructure deployed" → "Scalable processing capacity that grows with business needs while optimizing costs through auto-scaling"
• "EFS shared storage operational" → "Collaborative workspace enabling data science teams to work efficiently on shared datasets and projects"
• "IAM security controls implemented" → "Enterprise-grade access controls ensuring data security and regulatory compliance with full audit trails"
• "Monitoring and alerting configured" → "Proactive system health management preventing downtime and ensuring business continuity"

STAKEHOLDER-SPECIFIC COMMUNICATION:

C-LEVEL EXECUTIVES:
- Focus: Strategic value, competitive advantage, risk mitigation
- Frequency: Weekly written updates, monthly presentation
- Content: ROI metrics, business capability enablement, risk status
- Format: Executive dashboard, high-level summaries

FINANCE LEADERSHIP:
- Focus: Budget tracking, cost optimization, resource efficiency
- Frequency: Bi-weekly budget reviews
- Content: Cost per milestone, optimization opportunities, ROI projection
- Format: Financial dashboard, cost breakdowns

IT LEADERSHIP:
- Focus: Technical integration, operational impact, security compliance
- Frequency: Weekly technical briefings
- Content: Architecture decisions, integration status, security posture
- Format: Technical presentations, architecture reviews

BUSINESS UNIT LEADERS:
- Focus: Timeline impact, capability delivery, user readiness
- Frequency: Bi-weekly capability updates
- Content: Feature availability, user training timeline, business impact
- Format: Capability roadmap, user readiness assessments

COMMUNICATION PROTOCOLS:

ESCALATION PROCEDURES:
- Green Status: Weekly written updates, scheduled reviews
- Yellow Status: Increased frequency, stakeholder notifications
- Red Status: Daily updates, executive decision meetings, mitigation planning

CHANGE COMMUNICATION:
- Scope Changes: Impact assessment, approval process, timeline adjustment
- Technical Challenges: Risk assessment, mitigation options, resource needs
- Timeline Adjustments: Business impact analysis, stakeholder buy-in

SUCCESS COMMUNICATION:
- Milestone Achievements: Business value realization, capability demonstration
- Early Wins: Quick value delivery, momentum building
- Final Delivery: Comprehensive business value summary, next phase planning

Create a comprehensive stakeholder communication strategy with business value translation, tailored messaging for different audiences, and escalation procedures for successful platform implementation.
```

#### Business Value Realization and ROI Communication Prompt

```
ROLE: Business Value Analyst and ROI Communication Specialist

CHALLENGE: Quantify and communicate business value and return on investment for AWS Data Platform Foundation throughout implementation and post-deployment.

ROI ANALYSIS FRAMEWORK:

INVESTMENT BREAKDOWN:
• Infrastructure Costs: EC2, EFS, RDS, S3, data transfer (8-week + 1-year projection)
• Team Resources: 3-4 engineers × 8 weeks + ongoing support
• Training and Development: AWS certifications, skill development
• Tools and Licensing: Terraform, monitoring tools, backup solutions

DIRECT BUSINESS VALUE:

OPERATIONAL EFFICIENCY GAINS:
• Manual Infrastructure Reduction: 80% reduction in manual server provisioning
  - Previous: 2 weeks manual setup per environment
  - New: 2 hours automated deployment per environment
  - Annual Savings: $120K in engineering time

• Collaborative Productivity: Shared storage and centralized authentication
  - Previous: Individual development environments, file sharing issues
  - New: Collaborative workspace, instant access to shared datasets
  - Productivity Gain: 25% improvement in data science team efficiency

• Security and Compliance Automation:
  - Previous: Manual access management, compliance reporting
  - New: Automated access controls, audit trails, compliance dashboards
  - Risk Reduction: 60% reduction in security incidents, compliance cost savings

SCALABILITY AND GROWTH ENABLEMENT:

PLATFORM FOUNDATION VALUE:
• Future Data Processing Capabilities: Ready for Spark, Airflow, ML workflows
• Elastic Scaling: Auto-scaling infrastructure supports business growth
• Multi-Environment Support: Development, staging, production separation
• Integration Readiness: APIs and services ready for business application integration

COST OPTIMIZATION:

INFRASTRUCTURE EFFICIENCY:
• Auto-Scaling Cost Optimization: 30% reduction in compute costs through right-sizing
• Storage Lifecycle Management: 40% reduction in storage costs through intelligent tiering
• Reserved Instance Strategy: 25% reduction in EC2 costs through capacity planning

VALUE COMMUNICATION BY TIMELINE:

WEEK 2: Foundation Value
"Secure network foundation established, enabling controlled and auditable access to data processing resources"

WEEK 4: Authentication Value
"Centralized user management operational, reducing administrative overhead by 60% and improving security posture"

WEEK 6: Platform Value
"Collaborative data processing environment ready, enabling data science team productivity improvements"

WEEK 8: Full Platform Value
"Complete AWS Data Platform Foundation operational, providing scalable, secure, and cost-optimized infrastructure for current and future data initiatives"

POST-DEPLOYMENT VALUE TRACKING:

BUSINESS METRICS:
• Time to Deploy New Data Projects: Baseline vs. improved metrics
• Data Science Team Productivity: Project completion time improvements
• Infrastructure Utilization: Cost per project, resource efficiency
• Security Incident Reduction: Compliance metrics, audit findings

ROI CALCULATION:
• 3-Month ROI: Break-even through operational efficiency gains
• 12-Month ROI: 200% return through productivity and cost optimization
• 24-Month ROI: 400% return through platform capability enablement

EXECUTIVE PRESENTATION FRAMEWORK:
• Investment Summary: Clear cost breakdown and resource allocation
• Value Realization Timeline: When benefits will be realized
• Risk Mitigation Value: Security, compliance, and operational risk reduction
• Future Capability Enablement: Platform readiness for advanced data initiatives

Design a comprehensive business value and ROI communication strategy with quantified benefits, timeline-based value realization, and executive presentation materials for AWS Data Platform Foundation investment justification.
```

---

</details>

---

## Operational Excellence and Continuous Improvement Prompts

---

### Monitoring and Maintenance Strategy

<details>
<summary>CloudWatch Monitoring and Operational Procedures</summary>

---

#### AWS CloudWatch Monitoring and Alerting Strategy Prompt

```
ROLE: AWS Monitoring Architect and Site Reliability Engineering Lead

MISSION: Design comprehensive CloudWatch monitoring and alerting strategy for AWS Data Platform Foundation ensuring operational excellence and proactive issue resolution.

MONITORING ARCHITECTURE:

INFRASTRUCTURE MONITORING:
• EC2 Metrics: CPU, memory, disk, network utilization across all instance types
• EFS Performance: Throughput, IOPS, client connections, burst credit balance
• RDS Monitoring: Database performance, connections, query execution time
• VPC Flow Logs: Network traffic analysis, security monitoring, cost optimization
• Auto Scaling: Scaling events, instance health, capacity utilization

APPLICATION MONITORING:
• Data Processing Jobs: Success/failure rates, execution time, resource utilization
• User Authentication: Login success/failure, FreeIPA performance metrics
• Storage Access: EFS mount performance, S3 access patterns, data transfer costs
• System Health: Service availability, response times, error rates

CUSTOM METRICS DEVELOPMENT:
• Business KPIs: Data processing throughput, user productivity metrics
• Cost Tracking: Resource utilization by team, project cost allocation
• Security Metrics: Authentication events, access pattern analysis
• Performance Indicators: System responsiveness, user experience metrics

DASHBOARD DESIGN:

EXECUTIVE DASHBOARD:
```json
{
  "widgets": [
    {
      "type": "metric",
      "properties": {
        "title": "Platform Availability",
        "metrics": [["AWS/EC2", "StatusCheckFailed", "InstanceId", "i-master"]],
        "period": 300,
        "stat": "Maximum",
        "region": "us-west-2"
      }
    },
    {
      "type": "metric", 
      "properties": {
        "title": "Cost Optimization",
        "metrics": [["AWS/Billing", "EstimatedCharges", "Currency", "USD"]],
        "period": 86400,
        "stat": "Maximum"
      }
    }
  ]
}
```

TECHNICAL TEAM DASHBOARD:
• System Performance: Real-time infrastructure metrics
• Application Health: Service status, error rates, response times
• Resource Utilization: Capacity planning, optimization opportunities
• Security Status: Authentication metrics, access patterns, compliance

ALERTING STRATEGY:

CRITICAL ALERTS (Immediate Response - 5 minutes):
• EC2 Instance Failures: Auto-scaling group health, master node availability
• Database Connectivity: RDS connection failures, performance degradation
• Security Incidents: Unauthorized access attempts, authentication failures
• Data Loss Risk: Backup failures, replication issues

WARNING ALERTS (Response within 1 hour):
• Resource Utilization: CPU >80%, Memory >85%, Disk >80%
• Performance Degradation: Response time increases, throughput reduction
• Cost Anomalies: Unexpected spend increases, resource waste
• Capacity Planning: Approaching resource limits, scaling thresholds

SNS INTEGRATION:
• Email Notifications: Technical team for immediate issues
• Slack Integration: Team collaboration channels for coordination
• PagerDuty: On-call rotation for critical infrastructure issues
• SMS Alerts: Emergency contact for business-critical failures

IMPLEMENTATION COORDINATION:
• Automation Engineer: CloudWatch agent deployment and configuration (Week 5)
• Systems Engineer: Custom metrics development and dashboard creation (Week 6)
• Platform Engineer: Application-specific monitoring and user experience metrics (Week 7)
• Lead DevOps: Alert tuning, escalation procedures, and runbook development (Week 8)

Design a comprehensive CloudWatch monitoring strategy with dashboards, alerting, and team coordination for operational excellence and proactive issue management.
```

#### Backup and Disaster Recovery Strategy Prompt

```
ROLE: Disaster Recovery Architect and Business Continuity Specialist

CHALLENGE: Design comprehensive backup and disaster recovery strategy for AWS Data Platform Foundation ensuring business continuity and data protection.

BACKUP ARCHITECTURE:

EC2 BACKUP STRATEGY:
• EBS Snapshots: Daily automated snapshots with 7-day retention
• AMI Creation: Weekly instance image backups for rapid deployment
• Configuration Backup: Infrastructure as Code in version control
• Data Backup: Critical application data to S3 with versioning

EFS BACKUP CONFIGURATION:
• AWS Backup Service: Daily backups with 35-day retention policy
• Cross-Region Replication: Secondary region backup for disaster recovery
• Point-in-Time Recovery: Granular file recovery capabilities
• Backup Validation: Monthly restore testing and integrity verification

RDS BACKUP APPROACH:
• Automated Backups: Daily backups with 7-day retention
• Manual Snapshots: Pre-maintenance and pre-deployment snapshots
• Cross-Region Snapshots: Disaster recovery database copies
• Transaction Log Backups: Point-in-time recovery capability (15-minute RPO)

S3 DATA PROTECTION:
• Versioning: Object versioning with lifecycle management
• Cross-Region Replication: Automatic replication to secondary region
• MFA Delete: Multi-factor authentication for deletion protection
• Glacier Deep Archive: Long-term archival for compliance retention

DISASTER RECOVERY PLANNING:

RECOVERY OBJECTIVES:
• Recovery Time Objective (RTO): 4 hours for critical services
• Recovery Point Objective (RPO): 15 minutes for database, 24 hours for files
• Business Continuity: Essential services operational within 2 hours
• Full Recovery: Complete platform restoration within 8 hours

DISASTER SCENARIOS:
• Single AZ Failure: Auto-scaling and multi-AZ deployment handling
• Region-Wide Outage: Cross-region failover procedures
• Data Corruption: Point-in-time recovery and backup restoration
• Security Breach: Isolation procedures and clean environment rebuild

RECOVERY PROCEDURES:

INFRASTRUCTURE RECOVERY:
```bash
# Disaster recovery automation script
#!/bin/bash
# 1. Assess disaster scope and impact
# 2. Activate disaster recovery team
# 3. Execute infrastructure recovery from Terraform
# 4. Restore data from latest backups
# 5. Validate system functionality
# 6. Update DNS and routing
# 7. Communicate with stakeholders
```

DATA RECOVERY WORKFLOW:
• Assessment: Determine data loss scope and recovery requirements
• Backup Selection: Identify appropriate backup point for recovery
• Recovery Execution: Automated restoration with validation checkpoints
• Validation Testing: Data integrity and application functionality verification
• User Communication: Status updates and service availability notifications

TESTING AND VALIDATION:

MONTHLY BACKUP TESTING:
• Automated restore testing in isolated environment
• Data integrity validation and corruption detection
• Recovery time measurement and optimization
• Documentation updates based on test results

QUARTERLY DR DRILLS:
• Full disaster recovery simulation with team coordination
• Cross-region failover testing and validation
• Communication protocol testing with stakeholders
• Process improvement identification and implementation

TEAM COORDINATION:
• Systems Engineer: Backup configuration and automation (Week 4-5)
• Automation Engineer: Recovery automation and testing procedures (Week 6-7)
• Platform Engineer: Application-specific backup and recovery (Week 7-8)
• Lead DevOps: DR planning, testing coordination, and documentation (Week 8)

Design a comprehensive backup and disaster recovery strategy with automated procedures, testing protocols, and team coordination ensuring business continuity and data protection.
```

---

</details>

---

## Success Validation and Continuous Improvement

---

### Implementation Success Criteria

<details>
<summary>DevOps Team Handover and Success Validation Framework</summary>

---

#### DevOps Team Implementation Readiness Assessment Prompt

```
ROLE: Technical Delivery Validation Specialist and DevOps Handover Coordinator

OBJECTIVE: Validate that AWS Data Platform Foundation deliverables enable successful step-by-step implementation by a DevOps team.

IMPLEMENTATION READINESS CHECKLIST:

TECHNICAL COMPLETENESS:
✅ Infrastructure as Code Validation:
• Terraform modules tested in development environment
• All AWS resources properly configured and integrated
• State management and backend configuration operational
• Variable validation and input sanitization implemented
• Module versioning and dependency management established

✅ Configuration Management Verification:
• Ansible playbooks successfully automate all configuration
• Dynamic inventory integration with AWS EC2 plugin
• Role-based configuration with proper error handling
• Idempotent operations and rollback capabilities
• Secret management and security hardening automation

✅ Step-by-Step Implementation Guide:
• Week-by-week implementation timeline with specific tasks
• Daily coordination framework and milestone checkpoints
• Prerequisites and dependency documentation
• Troubleshooting procedures for common integration issues
• Validation criteria for each implementation phase

TEAM COORDINATION VALIDATION:

LEADERSHIP FRAMEWORK ASSESSMENT:
✅ Team Structure and Responsibilities:
• Clear role definitions for 3-4 engineer team
• Task assignment matrix with skill-based allocation
• Communication protocols and coordination frameworks
• Escalation procedures and decision-making authority
• Cross-training and knowledge transfer plans

✅ Project Management Integration:
• 8-week timeline with realistic milestone planning
• Resource allocation and capacity management
• Risk assessment with proactive mitigation strategies
• Stakeholder communication and progress reporting
• Quality assurance and validation checkpoints

HANDOVER DOCUMENTATION:

TECHNICAL DOCUMENTATION PACKAGE:
• Architecture diagrams with component interaction details
• Network topology and security configuration specifications
• IAM roles, policies, and access control documentation
• Monitoring and alerting configuration guides
• Backup and disaster recovery procedures

OPERATIONAL PROCEDURES:
• Daily operational tasks and maintenance schedules
• Incident response and troubleshooting runbooks
• Change management processes and approval workflows
• User onboarding and access provisioning procedures
• Performance optimization and capacity planning guides

SUCCESS VALIDATION QUESTIONS:

"CAN A DEVOPS TEAM IMPLEMENT THIS STEP-BY-STEP?"
✅ YES - Complete validation:
• All Terraform configurations tested and validated
• Ansible playbooks automate entire configuration process
• Step-by-step timeline eliminates manual AWS console work
• Comprehensive troubleshooting and error resolution procedures
• Infrastructure as Code approach ensures reproducible deployments

"HOW WOULD YOU LEAD THEM THROUGH IT?"
✅ COMPREHENSIVE LEADERSHIP FRAMEWORK:
• Structured team coordination with daily standups and weekly reviews
• Technical skill development integrated with implementation tasks
• Risk management with proactive identification and mitigation
• Stakeholder communication translating technical progress to business value
• Quality assurance with validation checkpoints at each milestone

DELIVERY CONFIDENCE ASSESSMENT:
• Technical Implementation: 95% confidence in successful execution
• Team Coordination: Structured leadership approach with proven frameworks
• Timeline Achievability: Realistic 8-week schedule with appropriate buffers
• Risk Management: Comprehensive mitigation strategies for identified risks
• Business Value: Clear ROI and capability enablement for data platform foundation

Create a comprehensive implementation readiness assessment validating that deliverables enable successful DevOps team execution with effective leadership coordination.
```

---

</details>

---

## Conclusion

### AWS Data Platform Foundation GenAI Strategy Summary

<details>
<summary>Strategic AI-Assisted Implementation and Leadership Excellence</summary>

---

#### GenAI Utilization for Technical Excellence

This comprehensive prompt collection demonstrates advanced GenAI utilization for AWS Data Platform Foundation planning and implementation:

**Infrastructure Architecture Design**: AI-assisted optimization of AWS-specific components (EC2, EFS, FreeIPA, IAM) with detailed technical specifications and integration patterns.

**Team Leadership Coordination**: Strategic AI guidance for managing 3-4 engineers through 8-week implementation with role-based assignments, skill development, and coordination frameworks.

**Implementation Planning**: AI-enhanced project management with milestone-based timeline, risk assessment, and stakeholder communication strategies.

**Operational Excellence**: Comprehensive monitoring, backup, and maintenance strategies developed with AI assistance for long-term platform success.

#### Strategic Value Delivery

These prompts enable:
- **Technical Implementation Excellence**: Step-by-step guidance for reproducible AWS platform deployment
- **Leadership Development**: Framework for coordinating technical teams and developing engineering capabilities
- **Business Alignment**: Communication strategies for translating technical progress to business value
- **Operational Readiness**: Comprehensive procedures for production operation and continuous improvement

#### Success Enablement

The GenAI strategic prompts ensure:
- **DevOps Team Readiness**: Complete technical specifications enable step-by-step implementation
- **Leadership Coordination**: Structured approach for managing team delivery and stakeholder communication
- **Risk Mitigation**: Proactive identification and resolution of technical and project risks
- **Value Realization**: Clear ROI and business capability enablement through platform foundation

---

</details> 