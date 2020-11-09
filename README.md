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
image_id         ami-0bca12658f76ae40c     AMI for WebServer Created and made Public available for use
vpc_id           --                        If not specify default VPC ID will be used
aws_az1          Required                  AZ1 require 
aws_az2          Required                  AZ2 require

The AMI is pre-configured with Apache Server and Maria DB server along with HTTPD configuration and make public available for use. 

Requirements:
   1. Create IAM User with Administrator access and download ACCESS_KEY AND SECRET KEY.

Variables: roles/ec2_provisioning/vars/main.yml
		aws_region: ap-south-1
		aws_access_key: *******************
		aws_secret_key: *******************
		image_id: ami-0bca12658f76ae40c
		cidr_block: 10.0.0.0/16
		aws_vars:
  		    - { name: 'subnet1', aws_az: 'ap-south-1a', cidr: '10.0.1.0/24' }
                    - { name: 'subnet2', aws_az: 'ap-south-1b', cidr: '10.0.2.0/24' }


RUN the playbook using below command: (Require Ansible engine version 2.9)
 # ansible-playbook playbook.yml

NOTE: Blue-Green Deployment URL's
      Before Upgrade: http://public-ipv4-dns/mediawiki-1.35
      After Upgrade: http://public-ipv4-dns/mediawiki/index.php?title=Main_Page 
