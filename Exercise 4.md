**Exercise: Compute & Networking**
- In this scenario, you will create the underlying network infrastructure in which the employee directory EC2 instance will live. 
- In this exercise, you will **set up a new VPC with four subnets** (two public and two private) and **two route tables** (one public and one private). 
- Then, you will **launch an EC2 instance inside the new VPC.** Finally, at the end of the lab, you will stop the instance to prevent future costs from incurring.

**Lab Steps**
**Stage 1 - Create VPC**
- Search for VPC in the search bar at the top. Choose VPC. 
- Choose Your VPCs in the left panel. Choose Create VPC
- Under Name tag paste in app-vpc.
- For the IPv4 CIDR block paste in 10.1.0.0/16. Choose Create VPC. 
- Choose Internet Gateways in the left panel. 
- Choose Create internet gateway. Under Name tag paste in app-igw. Choose Create internet gateway.
- Choose Actions and Attach to VPC. 
- Under Available VPCs choose the app-vpc. Choose Attach internet gateway. 

**Stage 2 - Create Subnets**
- Choose Subnets at the left. Choose Create subnet. Under VPC ID, select the app-vpc from the drop down list. 
- Under Subnet settings and Subnet name, paste in Public Subnet 1
- Under Availability Zone, choose the 1st AZ. Example: If you are in US West (Oregon) you would choose us-west-2a.
- For the IPv4 CIDR block paste in 10.1.1.0/24. 

- Choose Add new subnet. Under Subnet name, paste in Public Subnet 2. Under Availability Zone, choose the 2nd AZ. Example: If you are in US West (Oregon) you would choose us-west-2b.
- For the IPv4 CIDR block paste in 10.1.2.0/24. 

- Choose Add new subnet. Under Subnet name, paste in Private Subnet 1. 
- Under Availability Zone, choose the 1st AZ. Example: If you are in US West (Oregon) you would choose us-west-2a.
- For the IPv4 CIDR block paste in 10.1.3.0/24. 

- Choose Add new subnet. Under Subnet name, paste in Private Subnet 2. 
- Under Availability Zone, choose the 2nd AZ. Example: If you are in US West (Oregon) you would choose us-west-2b.
- For the IPv4 CIDR block paste in 10.1.4.0/24. 

- Finally choose Create subnet. 

- Select the checkbox next to Public Subnet 1 after the subnets have been created. Choose Actions and Modify auto-assign IP settings. Under Auto-assign IPv4, choose Enable auto-assign public IPv4 address. Choose Save. 

- De-select Public Subnet 1. Select the checkbox next to Public Subnet 2. Choose Actions and Modify auto-assign IP settings. Under Auto-assign IPv4, choose Enable auto-assign public IPv4 address. Choose Save. 

**Stage 3 - Create Route Tables**
- Choose Route Tables at the left. Choose Create route table. Under Name tag, paste in app-routetable-public
- Under VPC, choose the app-vpc. Choose Create. Choose Close. 
- Select the app-routetable-public from the list. Choose the Routes tab. Choose Edit routes. 
- Choose Add route. For Destination, paste in 0.0.0.0/0
- For Target choose Internet Gateway. Choose the app-igw you set up in the VPC section. Select Save routes. Choose Close. 
- Choose the Subnet Associations tab. Choose Edit subnet associations. Select the 2 Public subnets (Public Subnet 1 & Public Subnet 2) you created in the Subnet section. Choose Save.

- Choose Create route table.  Under Name tag paste in app-routetable-private. Under VPC chose the app-vpc. Choose Create. Choose Close. 
- Deselect the app-routetable-public. Select the app-routetable-private from the list. 
- Choose the Subnet Associations tab. Choose Edit subnet associations. Select the 2 Private subnets (Private Subnet 1 & Private Subnet 2) you created in the Subnet section. Choose Save.

**Stage 4 - Launch EC2 instances using role**
- Now that you've created a network, it's time to launch your EC2 instance using the VPC you created! 
- Search for EC2 in the search bar at the top. Choose EC2. 
- Under Launch instance choose the Launch instance button. 
- Choose Select next to the first AMI which should be Amazon Linux 2 AMI (HVM), SSD Volume Type.
- Choose the t2.micro (Free tier eligible) as the Type. Choose Next: Configure Instance Details. 
- Next to Network choose the app-vpc from the list. Next to Subnet choose Public Subnet 1 from the list. 
- Next to Auto-assign Public IP choose Enable. 
- Next to IAM role choose the S3DynamoDBFullAccessRole. 
- Scroll down to Advanced Details. Paste in the following into the User data box:
```
    #!/bin/bash -ex
    wget https://aws-tc-largeobjects.s3-us-west-2.amazonaws.com/DEV-AWS-MO-GCNv2/FlaskApp.zip
    unzip FlaskApp.zip
    cd FlaskApp/
    yum -y install python3 mysql
    pip3 install -r requirements.txt
    amazon-linux-extras install epel
    yum -y install stress
    export PHOTOS_BUCKET=${SUB_PHOTOS_BUCKET}
    export AWS_DEFAULT_REGION=us-east-1
    export DYNAMO_MODE=on
    FLASK_APP=application.py /usr/local/bin/flask run --host=0.0.0.0 --port=80
```
- Change the following line to match your region:
- Note: You can find this at the top right next to your user name.  
- export AWS_DEFAULT_REGION=<INSERT REGION HERE>
Example: 
Note: US West (Oregon) 
export AWS_DEFAULT_REGION=us-west-2
- Note: You still do not have to change the PHOTOS_BUCKET variable in the User Data script, you will do this in a later lab.
- Choose Next: Add Storage. Choose Next: Add Tags. 
- Choose Add Tag. Under Key paste in Name. Under Value paste in employee-directory-app. 
- Choose Next: Configure Security Group. For Security group name: paste in web-security-group. 
- For the Description paste in Enable HTTP access. 
- Choose Add Rule. For Type, choose HTTP. For Source, change to Anywhere. 
- Choose Add Rule. For Type, choose HTTPS. For Source, change to Anywhere. 
- Then, next to the SSH rule, choose the X at the right to remove it as you will not need SSH access to the instance. 
- Choose Review and Launch. Choose Launch. 
- Leave Choose an existing key pair selected. Under Select a key pair app-key-pair should be selected. Select the checkbox next to the acknowledgement. Choose Launch Instances. 
- Choose View Instances. The instance should now show up under Instances. Wait for the Instance state to change to Running and the Status check to change to 2/2 checks passed.
- Note: Often, the status checks update and the UI does not. Feel free to refresh the page after a few minutes to minimize waiting.  

- Next to Name, choose the checkbox to select the running employee-directory-app instance.  Under the Details tab, copy down the Public IPv4 address. 
- Note: do not click the link to open the IPv4 address. Simply just copy the address and paste it into a new tab. 
- Paste it into a new browser tab/window. You should see a Employee Directory placeholder. Right now, you will not be able to interact with it as it's not currently connected to a database. 

**Stage 5 - Stop instance**
- Congrats! You've launched an EC2 instance hosting your employee directory application into a customized VPC. To prevent future costs, you will now stop the instance. (Note: do not terminate it, as the next lab will use this instance.)
- Choose Instance state and Stop instance. Choose Stop. The Instance state will eventually go into the Stopped state. 
- Lab Complete: Congratulations! You have completed the lab.


 