**Exercise 2: Following IAM Best Practices**

In this exercise, you will **log into the root account**, **delete the root user access keys**, and **set up multi-factor authentication (MFA)**. 

Instead of using the root user, you will create an IAM admin user. Then, you will will log in as the IAM admin user and create an IAM role that you will later assign to an EC2 instance hosting the employee directory application.

Lab Steps
**Stage 1 - Login to the Console**
- Visit https://aws.amazon.com/console/
- Choose Sign In to the Console.
- Choose Root user. Enter the Root user email address.
- Choose Next.
- Enter the Password for the root user. Choose Sign in.

**Stage 2 - Enable MFA (optional)**
- At the top right, choose your account name. Then choose My Security Credentials from the drop down menu. 

- Expand Multi-factor authentication (MFA). Choose Activate MFA. 

- On the Manage MFA device pop-up window. Choose Virtual MFA device and choose Continue. (microsoft authenticator)

- Note: You will need a virtual MFA application installed on your device or computer. You can see a list of applications on step 1 on the Set up virtual MFA device pop-up window. There is a hyperlink which shows a list of compatible applications. Before continuing to the next step make sure you have one of these applications installed on your mobile device or computer. 

- Choose Show QR code and scan the code using your device. 

- Note: If you are using a computer you can choose Show secret key and type the secret key into your MFA application.  

- Type the first MFA code into the MFA code 1 field. Then type the second generated number into  the MFA code 2 field. Choose Assign MFA. 

- You should see a pop-up indicating that you have successfully assigned a virtual MFA device. Choose Close. 

- Expand Access keys (access key ID and secret access key). 

- Note: There should be no access keys listed. If an access key exists (for your new account) choose Delete under Actions. Choose Deactivate. Enter in the access key ID in the confirmation field. Choose Delete. 

**Stage 3 - Create an IAM user**
- In the service search bar, type in Identity and Access Management (IAM) dashboard. On the left side panel, choose Users. 
- Choose Add user. Paste in Admin for the User name. Next to Access type, choose Programmatic access and AWS Management Console access. 
- Next to Console password, choose Custom password and type in a password of your choosing. 
- Uncheck Require password reset. 
- Choose Next: Permissions. 
- Choose Attach existing policies directly. Next to Filter policies, search for administrator. Under Policy name, choose AdministratorAccess. Choose Next: Tags. 
- Choose Next: Review. Choose Create user. 

- You can sign in with the new IAM user by clicking the hyperlink at the bottom of the Success window.

Note: It should look similar to the following: https://000000000000.signin.aws.amazon.com/console. Your account number will be different :) 

Log in using the Admin user and password that you created. 

**Stage 4 - Set up an IAM role for EC2 instance**
- Now that you are logged in as the Admin user, search for IAM again in the service search bar. 
- On the left side panel, choose Roles. Then, choose Create role. 
- Choose AWS service. Choose EC2. Choose Next: Permissions. 
- Next to Filter policies, search for amazons3full and choose AmazonS3FullAccess. 
- Next to Filter policies search for amazondynamodb and choose AmazonDynamoDBFullAccess. 
- Choose Next: Tags. Choose Next: Review. 
- For Role name paste in S3DynamoDBFullAccessRole. Choose Create role.
- Note: **Using full access policies are not something reccommended you should do in a production environment.** We are using these policies as a proof of concept to get your demo up and running quickly. Once your Amazon S3 bucket and Amazon DynamoDB table are created, you can come back and modify this IAM Role to have more specific and restrictive permissions. More on this later.

Lab Complete
	 Congratulations! You have completed the lab.

