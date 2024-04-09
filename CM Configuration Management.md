Below are instructions for implementing controls in S3 found within the "CM Configuration Management" category of NIST 800-53.

# CM-5 - Access Restrictions for Change
CM-5, Access Restrictions for Change reads: 
> Define, document, approve, and enforce physical and logical access restrictions associated with changes to the system.

This control deals with the limiting of administrators and privileged users who have the ability to make changes to physical or logical access. In this case, only logical access is at play since the resources are in the cloud.

## Implementing CM-5
Bucket policies are a feature of S3 buckets in AWS that allow you to grant or restrict access to S3 buckets, and they can even apply down to the object level within buckets. 

In order to restrict access to administrative-level actions on an S3 bucket, you would want to restrict the ability to modify or remove bucket policies and ACLs. There are AWS "Actions" that correspond to those three administrative actions. We can write a bucket policy which has an "Allow" effect for specified principals (AWS users). 

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
			"Effect": "Allow",
			"Action": [
				"s3:DeleteBucketPolicy",
				"s3:PutBucketPolicy",
				"s3:PutBucketAcl"
			],
			"Resource": [
				"arn:aws:s3:::uno-8950-high-sec-baseline"
			]
		}
	]
}
```
