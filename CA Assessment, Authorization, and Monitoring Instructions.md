Below are instructions for implementing controls in S3 found within the "CA Assessment, Authorization, and Monitoring" category of NIST 800-53. 

## CA-9 - Internal System Connections
The CA-9 control reads: 
> Authorize internal connections of [organization-defined system components or classes of components] to the system;

In order to restrict connections to the S3 bucket from only internal sources, we can turn on the "Block Public Access" setting from within the S3 settings page. 
![AWS S3 Setting for Block Public Access](CA-9_BlockPublicAccess.png)
