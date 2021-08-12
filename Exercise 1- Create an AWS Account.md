**Exercise: Create an AWS Account**
The exercises are designed to be completed in your AWS account, and will have an associated cost. For this reason, in addition to the written instructions, this course includes video recordings of the exercises. If you intend to attempt the exercises, familiarize yourself with AWS pricing, specifically Amazon EC2 pricing, Amazon S3 pricing, and Amazon DynamoDB pricing and the AWS Free Tier.

In this scenario, imagine you work for a company that currently has no presence in the cloud. You have been tasked with creating the companies employee directory application in AWS. 

In this exercise, you will be creating and confirming a new AWS account. You will then log into that account and do basic management tasks, such as choosing a support plan. 

Lab Steps
**Stage 1** - Sign up for an account
Visit the Amazon Web Services home page.

Choose Create an AWS Account.
Note: If you signed in to AWS recently, choose Sign in to the Console. If Create a new AWS account isn't visible, first choose Sign in to a different account, and then choose Create a new AWS account.

Enter your account information, and then choose Continue. Be sure that you enter your account information correctly, especially your email address. If you enter your email address incorrectly, you can't access your account.

Choose Personal or Professional.

Note: These two account types are identical in functionality. You can choose a personal account for your personal projects or choose professional for use within your company, an educational institution, or an organization.

Enter your company or personal information.

Read the AWS Customer Agreement, and then check the box.

Click Create Account and Continue.

**Stage 2** - Add a payment method
On the Payment Information page, add a payment method by typing the requested information associated with your payment method.

Choose Verify and Add.

Important: You can't proceed with the sign-up process until you add a valid payment method.

**Stage 3** - Verify your identity
On the Identity Verification page. Choose your country or region code from the list.
Enter a phone number where you can be reached in the next few minutes.
Enter the code displayed in the CAPTCHA.
When you're ready to receive a call or text message (sms). Choose Contact me/Send SMS. In a few moments you should be contacted via the verification system. 
Enter the verification code you receive and choose Verify Code.
Choose Continue.
**Stage 4** - Choose an AWS Support plan
On the Select a Support Plan page, select the Basic Plan included in the free tier.
Click Sign in to Console to sign in to your console.
**Stage 5** - Set up free tier alert and custom billing alert
Search for Billing in the search bar and select it.
In the left hand navigation bar select Billing preferences
Under the Cost Management Preferences section, select the check boxes for Receive Free Tier Usage Alerts and Receive Billing Alerts.
Enter your email address into the text input box under Receive Free Tier Usage Alerts.
Select Save preferences.
In the services search bar, type in CloudWatch and select it. 
If necessary, change the Region in the upper right corner to US East (N. Virginia). Billing metric data is stored in this Region and represents worldwide charges.
In the navigation pane, choose Alarms, then click Create Alarm.
Choose Select metric. In the search bar under Metrics, type in Billing, then choose Billing >Total Estimated Charge. If you don't see Billing or the Total Estimated Charge metric, you may need to go back a few steps to enable billing alerts from the Billing preferences page.
Select the check box next to EstimatedCharges, and choose Select metric.
Under Conditions, choose Static.
For Whenever EstimatedCharges is, choose Greater.
For than, enter the monthly amount (this should be whatever number you are comfortable with. For example, 10) that must be exceeded to trigger the alarm. Choose Next.
In the Notification box, for Alarm State Trigger, select In alarm. Under Select an SNS Topic, choose create a new topic to be notified. 
 Amazon Simple Notification Service (Amazon SNS) is a service that publishes messages to a topic which delivers the message to all topic subscribers.

Enter a topic name. The name must be unique. Then, type in your email to receive the notification. 

NOTE: You will get an email in your inbox asking you to confirm your subscription to this topic. By confirming, you're ensuring that you will get notifications when your estimated billing charges rises above your threshold.

Click Create Topic. Then, select Next.

Enter in an alarm name and description. The name must contain only ASCII characters. 

Under Preview and create, confirm that the information and conditions are what you want, then choose Create alarm.

Lab Complete
	 Congratulations! You have completed the lab.

	For feedback, suggestions, or corrections, please contact us at:https://support.aws.amazon.com/#/contacts/aws-training

 