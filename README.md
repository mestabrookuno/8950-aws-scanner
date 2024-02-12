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
|Sample AWS Account|No|Matt|Need to spin up a test AWS account, complete with S3 buckets.|
|Pentesting Tool|No|Grace|A pentesting solution will be needed to detect vulnerabilities in publicly accessible S3 buckets.|
|IaC Scripting Knowledge|Maybe|Mark|Some Infrastructure as Code (IaC) knowledge will be needed to help create the AWS configs. This may be a book, tutorials, or other training resources to help sharpen the team's knowledge of IaC.|
|Baseline Storage/Repository|No|Matt|There needs to be a working directory for the team to store baseline drafts and collaborate. This will likely be GitHub, but could be Google Docs, etc.|
|DLP Tool|No|Grace|In order to identify sensitive data types shared publicly, a DLP (Data Loss Prevention) tool may help classify and detect data.|
