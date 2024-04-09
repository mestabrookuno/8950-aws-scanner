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
			    "AWS": "arn:aws:iam::975050068436:user/mattE"
			},
			"Effect": "Allow",
			"Action": [
				"s3:CreateBucket",
				"s3:CreateAccessPointForObjectLambda",
				"s3:CreateAccessPoint",
				"s3:CreateAccessGrantsLocation",
				"s3:CreateAccessGrantsInstance",
				"s3:CreateAccessGrant",
				"s3:AssociateAccessGrantsIdentityCenter",
				"s3:AbortMultipartUpload",
				"s3:CreateJob",
				"s3:CreateMultiRegionAccessPoint",
				"s3:CreateStorageLensGroup",
				"s3:DeleteAccessGrant",
				"s3:DeleteAccessGrantsInstance",
				"s3:DeleteAccessGrantsInstanceResourcePolicy",
				"s3:DeleteAccessGrantsLocation",
				"s3:DeleteAccessPoint",
				"s3:DeleteAccessPointForObjectLambda",
				"s3:BypassGovernanceRetention",
				"s3:DeleteAccessPointPolicy",
				"s3:DeleteAccessPointPolicyForObjectLambda",
				"s3:UpdateStorageLensGroup",
				"s3:UpdateJobStatus",
				"s3:UpdateJobPriority",
				"s3:UpdateAccessGrantsLocation",
				"s3:SubmitMultiRegionAccessPointRoutes",
				"s3:RestoreObject",
				"s3:ReplicateObject",
				"s3:ReplicateDelete",
				"s3:PutStorageLensConfiguration",
				"s3:PutReplicationConfiguration",
				"s3:PutObjectRetention",
				"s3:PutObjectLegalHold",
				"s3:PutObject",
				"s3:PutMetricsConfiguration",
				"s3:PutLifecycleConfiguration",
				"s3:PutInventoryConfiguration",
				"s3:PutIntelligentTieringConfiguration",
				"s3:PutEncryptionConfiguration",
				"s3:PutBucketWebsite",
				"s3:PutBucketVersioning",
				"s3:PutBucketRequestPayment",
				"s3:PutBucketOwnershipControls",
				"s3:PutBucketObjectLockConfiguration",
				"s3:PutBucketNotification",
				"s3:PutBucketLogging",
				"s3:PutBucketCORS",
				"s3:PutAnalyticsConfiguration",
				"s3:PutAccessPointConfigurationForObjectLambda",
				"s3:PutAccessGrantsInstanceResourcePolicy",
				"s3:PutAccelerateConfiguration",
				"s3:InitiateReplication",
				"s3:DissociateAccessGrantsIdentityCenter",
				"s3:DeleteStorageLensGroup",
				"s3:DeleteStorageLensConfiguration",
				"s3:DeleteObjectVersion",
				"s3:DeleteObject",
				"s3:DeleteMultiRegionAccessPoint",
				"s3:DeleteBucketWebsite",
				"s3:DeleteBucket"
			],
			"Resource": [
				"arn:aws:s3:::uno-8950-high-sec-baseline"
			]
		}
	]
}
```
