## AWS S3 bucket Denial of Service Protection (Implementing AWS Shield)

**Sign in to the AWS Management Console**: Go to the [AWS Management Console](https://console.aws.amazon.com/). 

**Navigate to AWS Shield**: In the AWS Management Console, use the search bar or navigate to the "Security, Identity, & Compliance" section and click on "Shield" under "Security."

![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/aa35d44a-b388-4f24-b168-82087af78c64)


**Choose AWS Shield Advanced (optional)**: AWS shield offers two shield services standard and advanced. If an organization require additional protection and features beyond the basic protection offered by AWS Shield Standard, they can subscribe to AWS Shield Advanced. This includes advanced DDoS protection and 24/7 access to the AWS DDoS Response Team (DRT). Something to note is that AWS Shield Standard is automatically enabled for all AWS customers at no extra cost. 

![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/62deebba-5e63-4111-b30e-4f21782305e7)

![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/8fb9507e-05b2-4892-9788-a696a5cdbb6e)

![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/f8f289d1-f30e-449f-9398-786f04c2fb16)




**Enable AWS Shield on Amazon S3**: If using AWS Shield Advanced, follow the instructions provided in the AWS Shield console to enable the service for your Amazon S3 buckets.

![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/11d93541-6ccf-47b9-84d0-6cd3e50e4ebc)


To specifically enable the shield for a specific S3 bucket press on add resources to protect and select your bucket and configure the desired protection settings. You can then see what services AWS shield advanced are serving.

![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/ced2f866-3b19-4393-a3b0-05803379f5ea)  ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/ce7ee4a0-651c-4b97-bf67-6db66e583d04)



**Review Protection Settings**: Once AWS Shield is enabled for the S3 buckets, review and configure the protection settings as needed like setting up mitigation preferences, configuring advanced protection features, and defining notification preferences for DDoS events. [AWS Shield advanced update](https://aws.amazon.com/blogs/aws/aws-shield-advanced-update-automatic-application-layer-ddos-mitigation/).


**Monitor DDoS Events**: AWS Shield provides visibility into DDoS events and alerts through the AWS Management Console, CloudWatch alarms, and Amazon S3 access logs. It is good practice to monitor these channels regularly to stay informed about any DDoS activity targeting the S3 buckets and take appropriate action as necessary.[AWS Shield advanced update](https://aws.amazon.com/blogs/aws/aws-shield-advanced-update-automatic-application-layer-ddos-mitigation/).

