# mediawiki
Automate the Deployment of MediaWiki Webserver on AWS Instance


Description: Ansible Playbook to Automate the Installation of Security Group, Application Load Balancer, Target Group, Auto-Scaling Group. The playbook is tested on Ansible version 2.9

## Role Variables ##
Include the variables to roles/ec2_provisioning/vars/main.yml file

**Variable** | **Default**              | **Description**
------------   ------------                --------------
aws_region       Required                  Add the AWS REGION Parameter
aws_access_key   Required                  Create IAM User with AWS_ACCESS & AWS_SECRET KEY
aws_secret_key   Required                  Create IAM User with AWS_ACCESS & AWS_SECRET KEY 
image_id         ami-0e8834a21d50f1979     AMI for WebServer Created and made Public available for use
vpc_id           --                        If not specify default VPC ID will be used
subnet1          Required                  Subnet1 Required
subnet2          Required                  Subnet2 Required
aws_az1          Required                  AZ1 require 
aws_az2          Required                  AZ2 require
key_name         Required                  Create the Keypair and Save the pem file on local system. Specify name of keypair

The AMI is pre-configured with Apache Server and Maria DB server along with HTTPD configuration and make public available for use. 

Requirements:
   1. Create IAM User with Administrator access and download ACCESS_KEY AND SECRET KEY.
   2. Create KEYPAIR and down the pemfile require to SSH to instance

Variables: roles/ec2_provisioning/vars/main.yml
           aws_region: ********
           aws_access_key: ********
           aws_secret_key: ********
           image_id: ami-0e8834a21d50f1979
           vpc_id: ********
           subnet1: ********
           subnet2: ********
           aws_az1: ********
           aws_az2: ********
           key_name: ********

RUN the playbook using below command: (Require Ansible engine version 2.9)
 # ansible-playbook playbook.yml 


*******IMP NOTICE*******
Once the Instance is provisioned Don't forget to add to TargetGroup "TEST-TG" for Load Balancing. 
