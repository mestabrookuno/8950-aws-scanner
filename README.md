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
| There's a Hole in that Bucket!: A Large-scale Analysis of Misconfigured S3 Buckets |2018| **Introduction**: Cloud storage services, such as Amazon S3 (Simple Storage Service), offer cost-effectiveness and ease of use, appealing to hobbyists and businesses alike. The proliferation of cloud storage, accessed through user-friendly APIs, is reducing barriers for developers by eliminating the need for complex in-house storage setups. Amazon S3 provides a reliable and scalable infrastructure, accessible via web console or programmatically, facilitating seamless integration into applications. Custom domain referencing is enabled by setting up CNAME resource records. **Methods**: This study investigates the prevalence and impact of misconfigurations in Amazon S3 buckets. We automatically identify and validate publicly listable buckets, employing various discovery methods. Candidate bucket names are filtered and verified for public readability or writability. They also examine publicly accessible websites referencing writable buckets to assess the potential for resource infection attacks. **Results**: The tool, implemented in Python, effectively analyzes buckets in parallel. Using a sample set size of k = 30, they determine bucket readability. While the exposure of ACL permissions to anonymous users is identified, they emphasize that this is not inherently a security breach. Analysis reveals 3,415 buckets with writable ACLs for anonymous users and 3,446 buckets with writable ACLs for authenticated users. **Discussion**: The study prompts ethical considerations regarding large-scale scans and underscores the necessity of precautions to mitigate potential risks. The study emphasizes that the experiments focused solely on identifying misconfigurations without accessing user data. The methodology relies on HTTP requests and file extension analysis to assess sensitive exposure. **Conclusion**: This research highlights security implications associated with Amazon S3 usage, aiming to raise awareness and caution users about real-world security risks. The automated tool facilitates the discovery and verification of public S3 buckets, revealing significant proportions vulnerable to unauthorized access. Over 200 readable buckets were found to leak sensitive data.|
| Swinhoe, D. What are Amazon Zelkova and Tiros? AWS looks to reduce S3 configuration errors | 2018 |**Introduction:** According to Skyhigh Networks, a notable percentage of Amazon S3 buckets have unrestricted public access, while a significant portion remains unencrypted. To address AWS S3 configuration errors, Amazon is developing two new tools – Zelkova and Tiros – aimed at enhancing visibility into data and resource access. Despite previous security initiatives by AWS, organizations such as Verizon, Booz Allen Hamilton, and others have experienced data exposure due to configuration errors. **Methods:** Amazon's efforts to improve AWS security include the launch of Macie, a machine learning tool for sensitive data discovery, and features like default encryption and permission checks for S3. Nevertheless, challenges persist due to a lack of user education, complex deployments, and the rapid expansion of cloud services, often deployed without the oversight of security teams. **Results:** AWS's new tools aim to mitigate human error and minimize the risk of data leaks by providing enhanced security verification capabilities before infrastructure changes are implemented. However, while these tools offer benefits, there are also potential downsides, as highlighted by some experts. **Discussion:** The introduction of Zelkova and Tiros reflects AWS's commitment to bolstering security measures. However, the effectiveness of these tools may depend on user education, the complexity of deployments, and the evolving nature of cloud environments. Balancing the benefits and potential drawbacks of these tools is crucial for organizations aiming to enhance their AWS security posture. **Conclusion:** As AWS continues to innovate in cloud security, the introduction of Zelkova and Tiros signifies a proactive approach to addressing configuration errors and minimizing data leakage risks. While these tools offer promising solutions, their successful implementation will require careful consideration of various factors, including user education and the dynamic nature of cloud environments.|
| Cloud based automated encryption approach to prevent S3 bucket leakage using AWS Lambda | 2022 | **Introduction**: The cloud, composed of hardware, software, databases, and associated operations, offers scalable and cost-effective computing services. Utilized widely in remote workplaces, distributed storage services leverage APIs to streamline interactions between system administrators and developers. AWS cloud services, along with other major providers like Google Cloud and Microsoft Azure, offer various benefits, including data compliance, scalability, and cost-effectiveness. **Objectives**: This report aims to explore methods for enhancing data privacy in cloud platforms, particularly focusing on protecting data within AWS S3 buckets through automated encryption. **Methods**: The report discusses the challenges of data leakage in private S3 buckets, highlighting the vulnerability of bucket names in revealing sensitive information. A methodology for restricting the flow of sensitive data from AWS S3 buckets is presented, utilizing tools like S3Scanner and AWS CloudFormation for secure bucket configuration. **Results**: Implementation and evaluation of the proposed methodology demonstrate the effectiveness of automated encryption for S3 buckets. A template designed for CloudFormation streamlines resource provisioning and administration, embedding AWS Lambda encryption functions and IAM roles for enhanced security. **Conclusion**: Automated encryption techniques, such as those demonstrated in this report, offer a robust solution for protecting data stored in AWS S3 buckets. Leveraging AWS CloudFormation and Lambda can significantly enhance cloud security and privacy, ensuring timely action against potential threats. As security and privacy are intertwined, adopting such automated approaches is crucial for safeguarding sensitive information in cloud environments.|
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


