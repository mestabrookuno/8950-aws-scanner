# Project Purpose
Cloud providers like Azure, Google, and AWS have changed the way organizations build out their infrastructure. By nature, the cloud tends to be more "open" due to the fact that it is operating on shared hardware owned by someone else (the cloud provider). This can present risks, though. One of the risks that has been widely publicized is that of overly permissive S3 buckets in AWS. There are plenty of news stories about data being leaked via an S3 bucket that was publicly shared unintentionally. These misconfigurations can lead to lawsuits, bad press, and other negative outcomes for businesses. There is a need for more detailed baselines for S3 buckets in order to minimize sensitive data leakage.

The S3 Baseline Project aims to fix that problem of misconfigured S3 buckets leaking sensitive data by providing actionable baselines which security professionals and cloud administrators can use to secure their S3 buckets. The goals of this project are: 
- Provide actionable baseline for administrators to aid in securing S3 buckets
- Meet the needs of various verticals by providing tailored baselines for different needs
  - Banks may need more stringent configurations to ensure NO sensitive data is leaked
  - Retail organizations may need moderately stringent configurations to minimize sensitive data leakage but still allow sharing of information publicly as needed
  - Certain media outlets or other oganizations may need very little configuration due to the majority of data being published publicly anyway
- Test each level of baseline provided above against reasonable attack vectors against S3 buckets to provide some assurance that the framework provides value

Organizations of all sizes would be able to benefit from having detailed baselines like those proposed above, in order to assist them in securing S3 buckets. Smaller organizations with less in-house cloud expertise would likely benefit most from these baselines, though. Having a proven baseline to guide the setup and configuration of S3 buckets would make it easier for organizations of any size to safely utilize cloud resources like S3 buckets.

# Framework Alignment and Control Family Applicability
The NIST 800-53 framework provides a list of 20 control families. The contributors to this project selected 10 control families that are applicable to S3 buckets. The list of applicable control families is below. 
- AC Access Control
- AT Awareness and Training
- AU Audit and Accountability
- CA Assessment, Authorization, and Monitoring
- CM Configuration Management
- CP Contingency Planning
- IA Identification and Authentication
- MP Media Protection
- SC System and Communications Protection
- SI System and Information Integrity

Not every individual control within each of the above control families is applicable. In fact, most are, by nature of AWS and S3, not applicable. The below sections (organized by control family) provide a list of the applicable controls within that family, and link to documentation on how to implement settings within S3 that satisfy each control. 

# AC Access Control

# AT Awareness and Training

# AU Audit and Accountability

# CA Assessment, Authorization, and Monitoring

# CM Configuration Management
The CM family controls deals with managing the configuration of information systems. For S3 buckets, the below control is applicable: 
- CM-5

### Restricting Administrator Permissions in S3
NIST 800-53 control CM-5 reads: 
> Define, document, approve, and enforce physical and logical access restrictions associated with changes to the system.

This control deals with the limiting of administrators and privileged users who have the ability to make changes to physical or logical access. In this case, only logical access is at play since the resources are in the cloud.

## Setting up a Bucket Policy to Limit Administrator Permissions
Bucket policies are a feature of S3 buckets in AWS that allow you to grant or restrict access to S3 buckets, and they can even apply down to the object level within buckets.

In order to restrict access to administrative-level actions on an S3 bucket, you would want to restrict the ability to modify or remove bucket policies and ACLs. There are AWS "Actions" that correspond to those three administrative actions. We can write a bucket policy which has an "Allow" effect for specified principals (AWS users).

In order to more easily write up a bucket policy to block access to the bucket policy for certain administrators, we can use the AWS policy generator tool. The tool can be found here: https://awspolicygen.s3.amazonaws.com/policygen.html

Once on the policy generator page, we select "S3" as the policy type. 

![AWS Policy Generator](/assets/CM-5_Step1.png)

Next, select "Deny" as the intended effect of this policy statement. You will need to fill in the Principal (the administrator account ARN(s) that you would like to deny access to), and select the below three options from the "Actions" dropdown:

- DeleteBucketPolicy
- GetBucketPolicy
- PutBucketPolicy

Click "Add Statement" at the bottom in order to add that policy statement.

![AWS Policy Generator](/assets/CM-5_Step2.png)

In this case, we only need to add one statement. So, we are able to click "Generate Policy" at the bottom. This will generate the policy for us, and you can copy that policy right out of the generator and keep it handy for the next steps.

Below is an example of a policy that applies to a single AWS IAM user and allows that user to modify the bucket policies (and therefore the settings of the bucket itself).

```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "Statement1",
			"Principal": {
			    "AWS":"arn:aws:iam::975050068436:user/mattE"
			},
			"Effect": "Deny",
			"Action": [
				"s3:DeleteBucketPolicy",
				"s3:PutBucketPolicy",
				"s3:GetBucketPolicy"
			],
			"Resource": [
				"arn:aws:s3:::uno-8950-high-sec-baseline"
			]
		}
	]
}
```

Now, open up the bucket you intend to apply this policy to. Click on the "Permissions" tab to bring up the permissions page, where the bucket policy is located. 

![AWS S3 Buckets Screenshot](/assets/CM-5_Step3.png)

Find the Bucket policy section, and click the "Edit" button. 

![AWS S3 Bucket Policy Section](/assets/CM-5_Step4.png)

Copy and paste the policy into the Policy section of the page, and click "Save changes" at the bottom.

![AWS S3 Bucket Policy Photo](/assets/CM-5_Step5.png)

You have successfully denied access to the selected administrators to edit or remove the bucket policy.

## Testing Administrator Permissions Restrictions
In order to test this control, we need to attempt to make changes to the bucket policy as one of the users (principals) listed in the principal list in the above policy, and as a user not listed in the principal list. We would expect that the user in the principal list could edit the policy, while the user not in the principal list could not edit the policy.

If, as a principal of an administrator who was denied access to edit the bucket policy (as seen above) we try and access the bucket policy page, we should see the below error message if the access is correctly blocked.

![AWS Bucket Policy Access Error](/assets/CM-5_AccessDenied.png)

If we are able to see the bucket policy (and no error message is shown like the one above), the control is not in place.

# CP Contingency Planning

# IA Identification and Authentication
## IA-2 Identification and Authentication (organizational Users)
Identifying individual users and authenticating those users so that you can restrict access and assign permissions appropriately is crucial. For S3 buckets, the below controls are applicable: 
- IA-2
- IA-2(1)
- IA-2(2)

NIST 800-53 control IA-2 reads: 
> Uniquely identify and authenticate organizational users and associate that unique identification with processes acting on behalf of those users.

When looking at an S3 bucket, the primary means of enforcing authentication is to utilize the built-in AWS authentication mechanisms. User management is done through the IAM (Identity and Access Management) console from within the AWS Console. After logging in to the AWS console, you can select "IAM" from the list of AWS services. 

![AWS Services Menu - Selecting IAM](/assets/IA-1_IAMSelection.png)

## Implementing Multi-factor Authentication on AWS Accounts
NIST 800-53 IA-2(1) reads: 
> Implement multi-factor authentication for access to privileged accounts.

And IA-2(2) reads: 
> Implement multi-factor authentication for access to privileged accounts.

To enable multi-factor authentication on an account in AWS, you first need to navigate to the IAM menu. Once you're there, click on "Users" on the left side in the menu. 

![AWS Services Menu - Users in IAM](/assets/IA-2_Step1.png)

Next, click on the name of the user you wish to implement MFA for. Click on the "Security credentials" tab. 

![AWS Users Security Credentials Menu](assets/IA-2_Step2.png)

Click on "Assign MFA device" and follow the prompts to set up either a virtual authenticator app (such as Google Authenticate) or a physical FIDO device (such as a Yubikey). 

![AWS Users Set up MFA](assets/IA-2_Step3.png)

Once that has been completed, MFA is enabled for that user. 

## Testing Multi-factor Authentication


## MP Media Protection

## SC System and Communications Protection

## SI System and Information Integrity
