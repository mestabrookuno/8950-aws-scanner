Below are instructions for implementing controls surrounding identification and authentication in AWS/S3.

## Implementing Identification and Authentication in AWS
NIST 800-53 control IA-2 reads: 
> Uniquely identify and authenticate organizational users and associate that unique identification with processes acting on behalf of those users.

When looking at an S3 bucket, the primary means of enforcing authentication is to utilize the built-in AWS authentication mechanisms. User management is done through the IAM (Identity and Access Management) console from within the AWS Console. After logging in to the AWS console, you can select "IAM" from the list of AWS services. 

![AWS Services Menu - Selecting IAM](https://github.com/mestabrookuno/8950-aws-scanner/blob/196741dae2aee77b545f17e894776b2403c368e5/images/IA-1_IAMSelection.png)

## Implementing Multi-factor Authentication on AWS Accounts
NIST 800-53 IA-2(1) reads: 
> Implement multi-factor authentication for access to privileged accounts.

And IA-2(2) reads: 
> Implement multi-factor authentication for access to privileged accounts.

To enable multi-factor authentication on an account in AWS, you first need to navigate to the IAM menu. Once you're there, click on "Users" on the left side in the menu. 

[![AWS Services Menu - Users in IAM](https://github.com/mestabrookuno/8950-aws-scanner/blob/32eaaad5f9fc6849583c24fcfb0ca97e562ab08a/images/IA-2_Step1.png)

Next, click on the name of the user you wish to implement MFA for. Click on the "Security credentials" tab. 

![AWS Users Security Credentials Menu](images/IA-2_Step2.png)

Click on "Assign MFA device" and follow the prompts to set up either a virtual authenticator app (such as Google Authenticate) or a physical FIDO device (such as a Yubikey). 

![AWS Users Set up MFA](images/IA-2_Step3.png)

Once that has been completed, MFA is enabled for that user. 

## Testing Multi-factor Authentication
