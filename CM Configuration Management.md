Below are instructions for implementing controls in S3 found within the "CM Configuration Management" category of NIST 800-53.

# CM-5 - Access Restrictions for Change
CM-5, Access Restrictions for Change reads: 
> Define, document, approve, and enforce physical and logical access restrictions associated with changes to the system.

This control deals with the limiting of administrators and privileged users who have the ability to make changes to physical or logical access. In this case, only logical access is at play since the resources are in the cloud.

## Implementing CM-5
Bucket policy: 
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
