
# AWS Practical Assignments
============================

## 1. EC2 Instance Creation
============================
- Created an **IAM** user (admin) with EC2 full Access permission.
- created Group "admingroup" and assigned EC2 full access permissions.
- logged in with admin user and launched EC2 instance with default configuration.
- EBS storage leave "Delete on Termination" checked. (dont uncheck)
- explore EC2 instance details, configurations, permissions, Ip address, VPC, subnet information etc.
- Start/stop and terminate the instance and verify its associated EBS volume is also remove.

## 2. AMAZON RDS creation
 - Search RDS > **Create Database** (myrdsdb) 
 - Select "**Standard Create**"
 - Select mySQL/MariaDB DB engine and its version
 - Select Free Tier Template
 - name db "myrdsdb" with t2.micro and add username/password credentials 
 - create an instance and connect to this RDS.
 - connect to the db, create a table and insert data to the table.

## 3. AWS ORGANIZATIONs
 - Login as root user and **Add an AWS account**
 - Invite another AWS account holder with their email or Account ID using **"Invite AWS Account"** 
 - Create an organization and move the invited member to that Organization Unit
 - Create and attach a deny policy. (prerequisite, the member has to have that as a fULL access policy: ex. s3 full acess)
 - To verify, invited member can try to create S3 bucket and they should see an error "no enough permissions to create S3 bucket".


# AWS Notes:
============
## IAM - IDENTITY AND ACCESS MANAGEMENT
- IAM is Global region
- Login credentials or Login ID are created uniquely across global and same user ID cannot be created under any region as IAM falls under Global Region.
 
- 3 Important components of IAM:
	-- User 
		--- (Root user = Admin), 
		--- IAM user is assigned with restricted Roles 
		--- IAM user with all privileges will be equal to root user
	-- User Groups
	-- Roles

- User creation screen will contain optional "Tags" (can be used to sub-categorize users)
- Security Credentials:
	-- MFA - Multi factor Authentication can be enabled for free of cost on AWS
	-- Access Keys: 
		--- Public key
		--- Private key

* For a conflict permission like allow and deny permission assigned to same user, Deny takes the precedence.
* When a usergroup is created and various users are associated to that usergroup, upon deleting the usergroup, associated users will still exist but the usergroup will be removed. 


* ROLES: Roles are for temporary process/people which can revoked/reused  
* Roles are similar to visitor ID card, which is used to access instance on a temporary basis ex; Auditor
* Create a ROLE and select the AWS account

* Policy or permission required to switch role (Trainer to get back on it)
* Identity center in User creation screen (not covered)
* Access Advisor tab under Users screen ?

# Elastic Cloud Compute (EC2)
============================
## Amazon Machine Image: OS, AWS offers all the possible OS for selection during instance creation.

## Instance Type:
### T2.nono, t2.micro etc hardware varies

- Private key file format:
 -- .pem: OpenSSH
 ---.ppk : for use with puTTY

* Once the keypair of an instance is lost/forgot, we will never be able to login to the instance. 
* Key pair is specific to a Region.

* Security Group: acts like a fence to a house.
* Volume: Harddisk

* Public IP is assigned by default - it will change whenever instance is rebooted/restarted

- Actions menu:
 -- Modify volume


# Virtual Private cloud (VPC)
=============================
Works as on-prem VPN. Entire infrastructure/architecture of an application lies under VPC which is a security fence to the entire cloud stack.

- Subnets: private and public subnets 
- Internet gateway: used to route to public subnets
- Route Tables: switch to route the access to either Public or private subnet.
 -- Public route table --- add Internet Gateway
 -- Private route table --- route table without Internet Gateway
- Security Groups: to define inbound and outbound rules

# Elastic Load Balancer (ELB)
=============================
- ELB are client facing with public IP address.
- ELB shares the load coming from various equally to the configured nodes

- Types of Load Balancers:
 --Application : handles HTTP/HTTPS traffic of a web application, operating at the request level
 -- Network: High performance and static IP address of an application, operating at the connection level
 -- Classic: when application running on EC2 classic network (Previous Generation)
 -- Gateway: Newly launched, used for managing home appliances.
	
- These Load balancers are further categorized into:
 -- Internet facing : Nodes work on Public IP Address. Route requests from clients over internet
 -- Internal: Nodes work on the private IP Address. Route requests from clients with access to VPC
	
- Statefull sticky sessions vs Stateless sessions
- Sticky sessions stick onto a specific instance for any specific set of users. 

* Cross-zone load balancing allows equal load balancing among the nodes belong to different Azs. i.e. When Cross-zone LB is enabled, it distributes traffic evenly across all registered instances in all enabled Azs.

**Auto Scaling Group: ** 
- Collection of similar configured EC2 instances logically grouped for scaling automatically.
- Increase the instances when on demand and decrease the instances when low demand.
 -- Auto scaling group manages EC2 capacity automatically.
 -- Template instance is configured and the same will be launched/terminated based on configuration specified to meet the demand

- **Target Groups**: Load balancers routes requests to the targets in a target group and performs health checks on the targets

* Load Balacers >> Target Groups (Health checks)
* Auto Scaling >> Launch Configurations (Template instance) >> Auto Scaling Groups

# Simple Storage Service (S3):
============================
 - S3 - Regional service, stored data within multiple AZs within same region
 - S3 is charged for retrieval/transactions performed on the data but not on the storage.

* Can save upto 5 TB per file (object) and 
* can create 100 Buckets per AWS Account (can request for more if required), 
* 5 GB per PUT request.
* Files in S3 are encrypted by default
* Every file uploaded/stored in S3 are treated as Object

- S3 storage Classes:
 -- S3-Standard: 
 -- S3- Intelligent Archive (frequently unaccessed files will be archived), we can set the archive days (say 30 days etc).
 -- So all files that were not accessed in last 30 days will be stored in S3-IA (less pricing than S3-standard) which helps save cost.

- Server Access Logging: Auditing on all S3 files in a bucket.
?? S3 with blocked public access is not charged?
