# Completed all practical assignments and i will get this notes updated here with all the assignments details and notes by 05/22.

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

