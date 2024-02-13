# Executive Summary
Cloud providers like Azure, Google, and AWS have changed the way organizations build out their infrastructure. By nature, the cloud tends to be more "open" due to the fact that it is operating on shared hardware owned by someone else (the cloud provider). This can present risks, though. One of the risks that has been widely publicized is that of overly permissive S3 buckets in AWS. There are plenty of news stories about data being leaked via an S3 bucket that was publicly shared unintentionally. These misconfigurations can lead to lawsuits, bad press, and other negative outcomes for businesses. There is a need for more detailed baselines for S3 buckets in order to minimize sensitive data leakage. 

The S3 Baseline Project aims to fix that problem of misconfigured S3 buckets leaking sensitive data by providing actionable baselines which security professionals and cloud administrators can use to secure their S3 buckets. The goals of this project are: 
- Provide actionable baseline for administrators to aid in securing S3 buckets
- Meet the needs of various verticals by providing tailored baselines for different needs
  - Banks may need more stringent configurations to ensure NO sensitive data is leaked
  - Retail organizations may need moderately stringent configurations to minimize sensitive data leakage but still allow sharing of information publicly as needed
  - Certain media outlets or other oganizations may need very little configuration due to the majority of data being published publicly anyway
- Test each level of baseline provided above against reasonable attack vectors against S3 buckets to provide some assurance that the framework provides value

Organizations of all sizes would be able to benefit from having detailed baselines like those proposed above, in order to assist them in securing S3 buckets. Smaller organizations with less in-house cloud expertise would likely benefit most from these baselines, though. Having a proven baseline to guide the setup and configuration of S3 buckets would make it easier for organizations of any size to safely utilize cloud resources like S3 buckets. 

# Project Risk Matrix
<to be completed by Mark>

# Resources Needed
|Resource  | Dr. Hale needed? | Investigating Team member | Description |
|-------------------|---------|---------------------------|-------------|
|Sample AWS Account|No|Matt|Need to spin up a test AWS account, complete with S3 buckets.|
|Pentesting Tool|No|Grace|A pentesting solution will be needed to detect vulnerabilities in publicly accessible S3 buckets.|
|IaC Scripting Knowledge|Maybe|Mark|Some Infrastructure as Code (IaC) knowledge will be needed to help create the AWS configs. This may be a book, tutorials, or other training resources to help sharpen the team's knowledge of IaC.|
|Baseline Storage/Repository|No|Matt|There needs to be a working directory for the team to store baseline drafts and collaborate. This will likely be GitHub, but could be Google Docs, etc.|
|DLP Tool|No|Grace|In order to identify sensitive data types shared publicly, a DLP (Data Loss Prevention) tool may help classify and detect data.|

# Methodology
## Literature Review:
In order to get a sense of what work had already been done in the S3 bucket space a thorough literature review was started and is in progress. The literature review as it pertains to this project is broken up into two pieces: 
1. Gather information on common security best practices, industry standards, and regulatory requirements related to securing S3 buckets
2. Analyze past security incidents and data breaches involving misconfigured S3 buckets to identify common attack vectors and vulnerabilities

A cross-section of research papers related to S3 bucket security are listed in the table below. 

| Article | Date Published | Description/Summary |
| -- | -- | -- |
| There's a Hole in that Bucket!: A Large-scale Analysis of Misconfigured S3 Buckets | (2018) | Introduction:
Cloud storage services, such as Amazon S3 (Simple Storage Service), offer cost-effectiveness and ease of use, appealing to hobbyists and businesses alike. The proliferation of cloud storage, accessed through user-friendly APIs, is reducing barriers for developers by eliminating the need for complex in-house storage setups. Amazon S3 provides a reliable and scalable infrastructure, accessible via web console or programmatically, facilitating seamless integration into applications. Custom domain referencing is enabled by setting up CNAME resource records.

Methods:
This study investigates the prevalence and impact of misconfigurations in Amazon S3 buckets. We automatically identify and validate publicly listable buckets, employing various discovery methods. Candidate bucket names are filtered and verified for public readability or writability. Additionally, we examine publicly accessible websites referencing writable buckets to assess the potential for resource infection attacks.

Results:
Our tool, implemented in Python, effectively analyzes buckets in parallel. Using a sample set size of k = 30, we determine bucket readability. While the exposure of ACL permissions to anonymous users is identified, we emphasize that this is not inherently a security breach. Analysis reveals 3,415 buckets with writable ACLs for anonymous users and 3,446 buckets with writable ACLs for authenticated users.

Discussion:
Our study prompts ethical considerations regarding large-scale scans and underscores the necessity of precautions to mitigate potential risks. We emphasize that our experiments focused solely on identifying misconfigurations without accessing user data. Our methodology relies on HTTP requests and file extension analysis to assess sensitive exposure.

Conclusion:
This research highlights security implications associated with Amazon S3 usage, aiming to raise awareness and caution users about real-world security risks. Our automated tool facilitates the discovery and verification of public S3 buckets, revealing significant proportions vulnerable to unauthorized access. Notably, over 200 readable buckets were found to leak sensitive data.|
| Swinhoe, D. What are Amazon Zelkova and Tiros? AWS looks to reduce S3 configuration errors | 2018 | According to Skyhigh Networks, a significant percentage of Amazon S3 buckets have security vulnerabilities, with 7 percent having unrestricted public access and 35 percent being left unencrypted. To address these issues, Amazon is developing two new tools, Zelkova and Tiros, aimed at providing clearer insights into data access and usage permissions. Despite previous efforts by AWS to enhance security, organizations such as Verizon, Booz Allen Hamilton, and others have exposed sensitive information due to configuration errors.Last year, AWS introduced Macie, a machine learning tool to identify and safeguard sensitive data within AWS, along with additional security features for S3. However, challenges persist, including a lack of education, the complexity of cloud deployments, and the proliferation of AWS services. AWS aims to mitigate these risks with new tools to reduce human error and prevent data leaks.While these tools offer benefits, some caution about potential drawbacks and emphasize the importance of thorough security verification before making changes to AWS infrastructure.|
| Cloud based automated encryption approach to prevent S3 bucket leakage using AWS Lambda | 2022 | Making the AWS S3 bucket private, will it be breach proof? And is it possible to automate S3 bucket encryption while creating S3 bucket to ensure data privacy?outlines the process of creating S3 buckets and the susceptibility of bucket names to reveal sensitive information due to widely accepted naming conventions. The report proposes using security tools like "S3Scanner" to secure S3 buckets and prevent information leakage. Additionally, it suggests leveraging AWS CloudFormation for automated encryption, as it allows for third-party installations if needed.
| Security best practices for Amazon S3 | NA  | Technical |
| AWS security cookbook : practical solutions for managing security policies, monitoring, auditing, and compliance with AWS | 2020 | Technical step by step help with baseline configuration
de Oliveira, A. Securing Weak Points in Serverless Architectures. |   |  

## Technical Plan
This project aims to bolster S3 bucket security. In order to do that, the project has been split into four key sections, each complete with subtasks needed to accomplish the overall goal, all listed below. 
### Step 1 - Develop the Baseline
- Define a set of baseline configurations and security controls for securing S3 buckets based on the collected data and analysis.
- Tailor the baselines to meet the specific security requirements and compliance needs of different industries or verticals (ex: banking, retail, media…).
  - Example of security requirement; Health system HIPAA
- Define Baseline Configuration: Based on the identified security requirements and AWS best practices, we should define a baseline configuration for S3 buckets. settings related to access control, encryption, logging, and versioning.
  - Access Control: Determine the access control policies buckets, including permissions for IAM users, roles, and groups. Implement the principle of least privilege to ensure that only authorized users have access to the buckets and their contents.
  - Encryption: Decide on encryption requirements for data stored in S3 buckets. include enabling server-side encryption (SSE) with AWS-managed keys (SSE-S3) or customer-provided keys (SSE-C), or AWS Lambda encryption.
  - Logging and Monitoring: Configure S3 bucket logging to track access requests and activities performed on the buckets. Enable AWS CloudTrail integration to capture API calls related to S3 bucket management and data access.
### Step 2 - Build a Sandbox Environment
- Set up a test environment that mirrors the production AWS environment, create the S3 buckets in the test environment. creating buckets with similar names, settings, and permissions to replicate the data storage and access patterns observed in real life settings.
- Set up IAM roles and policies in the test environment to mirror the permissions and access controls defined in the real life industry. Users and services in the test environment have similar levels of access to resources as in production.
- Network configuration settings, including VPC (Virtual Private Cloud) configurations, subnets, security groups, and routing tables, to match those in the production environment to make sure that the test environment operates within a similar network and security boundaries as real life
- Use AWS Config, AWS CloudTrail, and AWS Security Hub to monitor and assess compliance with the baseline configurations.
### Step 3 - Test the Baseline
- We could use automated tools, manual testing, and simulation techniques to test how well the baseline configurations work against common attacks.
- Thinking develop scripts ???
- Manual penetration testing to validate the security controls implemented by the baseline configurations and identify any weaknesses or vulnerabilities.
### Step 4 - Review and Display Results:
- Analyze the results of any test we will simultate to identify vulnerabilities.
- How can the baseline be improved?

## Currently Available Tools: 
- AWS Config helps ensure that S3 buckets adhere to the defined baseline configurations by continuously evaluating their settings and notifying administrators of any deviations.
- CloudTrail provides visibility into changes made to S3 buckets and helps organizations track user activity and API usage for security monitoring and auditing purposes.
- Security Hub aggregates and analyzes security findings from multiple AWS services, including AWS Config and CloudTrail, to identify security risks and compliance issues related to S3 buckets and other AWS resources.


