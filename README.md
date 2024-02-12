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

# Resources Needed
|Resource  | Dr. Hale needed? | Investigating Team member | Description |
|-------------------|---------|---------------------------|-------------|
|Sample AWS Account|No|Estabrook|Need to spin up a test AWS account, complete with S3 buckets|


<b style="font-weight:normal;" id="docs-internal-guid-5bde2d32-7fff-948b-291b-7ece568072f6"><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Milstone 1:</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:700;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Methodology:</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Lit review:</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">1. Research:</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- Gather information on common security best practices, industry standards, and regulatory requirements related to securing S3 buckets.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- Analyze past security incidents and data breaches involving misconfigured S3 buckets to identify common attack vectors and vulnerabilities.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:8pt;"><br /></p><div dir="ltr" style="margin-left:0pt;" align="left">
Artilce | Date published | Methodology/Description
-- | -- | --
There's a Hole in that Bucket!: A Large-scale Analysis of Misconfigured S3 Buckets | (2018) | The study aims to assess the prevalence and impact of misconfigurations in publicly accessible Amazon S3 buckets. Their methodology involves three steps:1. Candidate Generation: They use various methods to generate potential S3 bucket names since there is no public directory of valid bucket names. This includes creating acronyms and mutating dictionary words, leveraging web crawling to find linked buckets, and passive DNS data to find S3 domains.2. Scanner: Using the generated bucket names, they attempt to access the buckets via HTTPS requests to the S3 API. They check if the buckets exist and if they are publicly listable. They do not access personal files for privacy reasons.3. Inspector: For existing and publicly accessible buckets, they analyze their permission settings. They verify if files are readable and/or writable without accessing private files. They also check access control lists to study access control policies.Additionally, they inspect websites to identify those loading resources from S3 buckets and determine if those buckets are writable. If so, they conclude the website is vulnerable to resource infection attacks. These attacks could involve tampering with or delivering malicious content through the loaded resources.
Swinhoe, D. What are Amazon Zelkova and Tiros? AWS looks to reduce S3 configuration errors | 2018 | According to Skyhigh Networks, a significant percentage of Amazon S3 buckets have security vulnerabilities, with 7 percent having unrestricted public access and 35 percent being left unencrypted. To address these issues, Amazon is developing two new tools, Zelkova and Tiros, aimed at providing clearer insights into data access and usage permissions. Despite previous efforts by AWS to enhance security, organizations such as Verizon, Booz Allen Hamilton, and others have exposed sensitive information due to configuration errors.Last year, AWS introduced Macie, a machine learning tool to identify and safeguard sensitive data within AWS, along with additional security features for S3. However, challenges persist, including a lack of education, the complexity of cloud deployments, and the proliferation of AWS services. AWS aims to mitigate these risks with new tools to reduce human error and prevent data leaks.While these tools offer benefits, some caution about potential drawbacks and emphasize the importance of thorough security verification before making changes to AWS infrastructure.
Cloud based automated encryption approach to prevent S3 bucket leakage using AWS Lambda | 2022 | Making the AWS S3 bucket private, will it be breach proof? And is it possible to automate S3 bucket encryption while creating S3 bucket to ensure data privacy?outlines the process of creating S3 buckets and the susceptibility of bucket names to reveal sensitive information due to widely accepted naming conventions. The report proposes using security tools like "S3Scanner" to secure S3 buckets and prevent information leakage. Additionally, it suggests leveraging AWS CloudFormation for automated encryption, as it allows for third-party installations if needed.
Security best practices for Amazon S3 |   | Technical
AWS security cookbook : practical solutions for managing security policies, monitoring, auditing, and compliance with AWS | 2020 | Technical step by step help with baseline configuration
de Oliveira, A. Securing Weak Points in Serverless Architectures. |   |  

</div><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><br /></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">2. Developing the baseline :</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- Define a set of baseline configurations and security controls for securing S3 buckets based on the collected data and analysis.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- Tailor the baselines to meet the specific security requirements and compliance needs of different industries or verticals (ex: banking, retail, media…).</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">example of security requirement; </span><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:#ff9900;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Health system HIPAA</span><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:8pt;"><br /></p><ol style="margin-top:0;margin-bottom:0;padding-inline-start:48px;"><li dir="ltr" style="list-style-type:decimal;font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;" aria-level="1"><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;" role="presentation"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Define Baseline Configuration: Based on the identified security requirements and AWS best practices, we should define a baseline configuration for S3 buckets. settings related to access control, encryption, logging, and versioning.</span></p></li></ol><ul style="margin-top:0;margin-bottom:0;padding-inline-start:48px;"><li dir="ltr" style="list-style-type:disc;font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;margin-left: 36pt;" aria-level="1"><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;" role="presentation"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:underline;-webkit-text-decoration-skip:none;text-decoration-skip-ink:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Access Control</span><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">: Determine the access control policies buckets, including permissions for IAM users, roles, and groups. Implement the principle of least privilege to ensure that only authorized users have access to the buckets and their contents.</span></p></li><li dir="ltr" style="list-style-type:disc;font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;margin-left: 36pt;" aria-level="1"><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;" role="presentation"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:underline;-webkit-text-decoration-skip:none;text-decoration-skip-ink:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Encryption</span><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">: Decide on encryption requirements for data stored in S3 buckets. include enabling server-side encryption (SSE) with AWS-managed keys (SSE-S3) or customer-provided keys (SSE-C), or AWS Lambda encryption.</span></p></li><li dir="ltr" style="list-style-type:disc;font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;margin-left: 36pt;" aria-level="1"><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:8pt;" role="presentation"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:underline;-webkit-text-decoration-skip:none;text-decoration-skip-ink:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Logging and Monitoring</span><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">: Configure S3 bucket logging to track access requests and activities performed on the buckets. Enable AWS CloudTrail integration to capture API calls related to S3 bucket management and data access.</span></p></li></ul><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">4. Test the baseline:</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- we could use automated tools, manual testing, and simulation techniques to test how well the baseline configurations work against common attacks.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- Thinking develop scripts ???</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- manual penetration testing to validate the security controls implemented by the baseline configurations and identify any weaknesses or vulnerabilities.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><br /></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">5. Sandbox environment:</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- Set up a test environment that mirrors the production AWS environment, create the S3 buckets in the test environment. creating buckets with similar names, settings, and permissions to replicate the data storage and access patterns observed in real life settings.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Set up IAM roles and policies in the test environment to mirror the permissions and access controls defined in the real life industry. users and services in the test environment have similar levels of access to resources as in production.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Network configuration settings, including VPC (Virtual Private Cloud) configurations, subnets, security groups, and routing tables, to match those in the production environment to make sure that the test environment operates within a similar network and security boundaries as &ldquo;real life&rdquo;.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- Use AWS Config, AWS CloudTrail, and AWS Security Hub to monitor and assess compliance with the baseline configurations.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:#00ff00;font-weight:700;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">AWS Config</span><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:#00ff00;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;"> helps ensure that S3 buckets adhere to the defined baseline configurations by continuously evaluating their settings and notifying administrators of any deviations.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:#00ff00;font-weight:700;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">CloudTrail</span><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:#00ff00;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;"> provides visibility into changes made to S3 buckets and helps organizations track user activity and API usage for security monitoring and auditing purposes.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:#00ff00;font-weight:700;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">Security Hub </span><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:#00ff00;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">aggregates and analyzes security findings from multiple AWS services, including AWS Config and CloudTrail, to identify security risks and compliance issues related to S3 buckets and other AWS resources.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><br /></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">6. Results:</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:0pt;padding:0pt 0pt 8pt 0pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- Analyze the results of any test we will simultate to identify vulnerabilities.</span></p><p dir="ltr" style="line-height:1.2;background-color:#ffffff;margin-top:0pt;margin-bottom:8pt;"><span style="font-size:12pt;font-family:Arial,sans-serif;color:#24292e;background-color:transparent;font-weight:400;font-style:normal;font-variant:normal;text-decoration:none;vertical-align:baseline;white-space:pre;white-space:pre-wrap;">&nbsp;&nbsp;&nbsp;- How can the baseline be improved?</span></p></b><br class="Apple-interchange-newline">