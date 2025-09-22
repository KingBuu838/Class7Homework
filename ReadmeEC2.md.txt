9/9/2025

Class 7 EC2 - Basics

task - building an Amazon Linux EC2 with custom script

- template ==> https://github.com/BashiM1/bmc5/blob/main/ec2scrpit ---> copy ec2script (COPY RAW TEXT)	

steps
1. create New Secutity Group, Do Not Use Default
	- Go to Security Group
	- click on create Security Group
	- Name Security Group and give an description, leave VPC as is
	- Configure Inbound Rules
		- Type = HTTP
		- Protocol = TCP
		- Port Range = 80
		- Source = Anywhere-IPv4, 0.0.0.0/0
		- Description = Whatever you want
	- Outbound Rules: DO NOT TOUCH
	- Tags 
		- Key = name
		- Value = whatever
	- Click on the orange Create Security Group button at bottom
	
2. create EC2
	- Go to EC2, click on Instances
	- click on orange Launch Instance button
	- Name and tags 
		-name the Instance
	- Application and OS Images 
		- Amazon Linux (AMI)
	- Instance Type
		- t3.micro(free tier eligible) 
	- Key pair (login)
		- Proceed without a key pair(can create new key pair)
	- Network settings
		- Firewall
			- Select existing security group (never use default)
	- Configure storage 
		- leave as is 
	- Advanced details
		- skip down all the way to User data
			-Go to Github and copy file from repo
				- Paste into User data
	- Click on orange button that says Launch Instances
	- It should be a success green bar at the top

3. copy public DNS, make it into a useable link and paste the link to the chat
	- click on the instance in the green bar or go back to Instances
	- It will show you instance summary find where it says Public DNS and click on the copy button(looks like 2 paper pages)
	- Open another tab in the url bar:type in http:// paste in the Public DNS that was copied 
	- Should see a running web page
	- if not troubleshoot(check Security group, inbound rules, etc.) 




EC2 Teardown instrutions:
- Delete any ASGs 
- Delete Load Balancer listeners 
- Delete Target groups
- Make sure all instances are terminated
- Check dashboard for running resources
-[Extra step] make sure nothing is showing in EBS > volumes
