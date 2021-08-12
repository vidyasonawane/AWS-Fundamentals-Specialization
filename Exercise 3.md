**Exercise: Compute**
- The exercises are designed to be completed in your AWS account, and will have an associated cost. For this reason, in addition to the written instructions, this course includes video recordings of the exercises. If you intend to attempt the exercises, familiarize yourself with AWS pricing, specifically Amazon EC2 pricing, Amazon S3 pricing, and Amazon DynamoDB pricing and the AWS Free Tier.

- For this scenario, you will be creating the employee directory application using user data configured during the EC2 instance set up. Since this is a dry run, you will terminate the instance afterwards to prevent additional costs from occuring. 

- In this exercise, you will log into the console as the IAM admin user. 
- You will then launch an EC2 instance using the IAM role you created in the previous lab. 
- Finally, once you've created the employee directory application, you will stop and then terminate the instance. 

**Lab Steps**
**Stage 1 - Launch EC2 instance using role**
- Search for EC2 in the search bar at the top. Choose EC2. 
- Select Instances on the left side panel, and then choose the Launch instance button.
- Choose Select next to the first AMI, which should be Amazon Linux 2 AMI (HVM), SSD Volume Type.
- Choose the t2.micro (Free tier eligible) as the Type
- Choose Next: Configure Instance Details. 
- Leave the Network as the (default). 
- Next to Subnet, choose the first subnet in the drop down list.
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
    - Example: Note: US West (Oregon)
    export AWS_DEFAULT_REGION=us-west-2

- Note: You will modify this User Data script again to use your Amazon S3 bucket  in a later lab. For now, just leave the ${SUB_PHOTOS_BUCKET} in the script.

- Choose Next: Add Storage. Choose Next: Add Tags. 

- Choose Add Tag. Under Key paste in Name. Under Value paste in employee-directory-app. 

- Choose Next: Configure Security Group. For Security group name: paste in app-sg. 

- Choose Add Rule. For Type choose HTTP. For Source change to Anywhere. Then, next to the SSH rule, choose the X at the right to remove it as you will not need SSH access to the instance. 

- Note: You may get a warning that you will no longer be able to SSH into your instance. This is fine - as you won't need that functionality for this course.

- Choose Review and Launch. Choose Launch. Choose Create a new key pair. Under Key pair name paste in app-key-pair. Choose Download Key Pair. Finally choose Launch instances. 

- Scroll down, and choose View Instances. The instance should now show up under Instances. Wait for the Instance state to change to Running and the Status check to change to 2/2 checks passed.

- Note: Often, the status checks update and the UI does not. Feel free to refresh the page after a few minutes to minimize waiting.  

- Next to Name, choose the checkbox to select the instance.  Under the Details tab, copy down the Public IPv4 address. 

- Note: do not click the link to open the IPv4 address. Simply just copy the address and paste it into a new tab. 

- Paste it into a new browser tab/window. You should see a Employee Directory placeholder. Right now you will not be able to interact with it as it's not currently connected to our DynamoDB database. 

- Congrats! You've successfully created an EC2 instance hosting the employee directory application. After you've finished looking around, it's time to stop and terminate your instance, so that you don't incur future costs. 

- Back in the AWS Management Console, the employee-directory-app should still be selected. Now, choose Instance state at the top and choose Stop instance. Choose Stop. The Instance state will eventually go into the Stopped state. 

- Next, you will terminate the instance. Again, select the checkbox next to the instance Name. Choose Instance state and choose Terminate instance. Choose Terminate. 

- Lab Complete
	- Congratulations! You have completed the lab.