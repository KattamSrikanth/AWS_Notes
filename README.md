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

