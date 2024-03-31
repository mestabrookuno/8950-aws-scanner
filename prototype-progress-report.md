# Progress Report March 31st 2024
## Overview
### Progress on Baselines
After much discussion around how to form the initial baselines, we decided to use the NIST 800-53 control families as a starting point. The NIST 800-53 document has an extensive list of control families, as well as individual controls. We also found that the document provides example baselines for low, medium, and high security applications (generalized) and advises which controls are applicable to each baseline. This was exactly the sort of framework and guidance we were looking for. 

Armed with the 800-53 baselines documentation, we went through the list of control families and eliminated the families that we deemed not applicable to our project. Because S3 buckets are hosted on AWS, certain control families like physical access controls are just not applicable. Listed below are the control families we decided were applicable. 

Applicable: 
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

Within these families we were also able to determine which individual controls would apply to the AWS atmosphere. For example in AT a control like role based training would not apply to how buckets are secured, while a control like event logging would be very important. Using this we were able to heavily trim down what we truly needed in a baseline.

### Progress on Infrastructure
One of the main hurdles in this project was getting access to AWS resources so the entire team had enough access in order to spin up the required resources, and carry out testing. The University has a corporate AWS account that we were able to utilize in this regard. The IT team was able to provision a separate account for us to use. We are currently spending time determining if there are any further permissions needed for us to carry out the necessary testing. For now we have gained full access to S3 and EC2 in order to spin up buckets and a Kali box. Further requests for permissions will go through Dr.Hale as necessary. We currently have three S3 buckets that we will implement the low medium and high baselines to. 

### Research Progress
The research question we developed is as follows, "What are the most effective methods for detecting and responding to security threats (e.g., unauthorized access attempts, data breaches) targeting S3 buckets?". Using the AWS infrastructure and baselines we will create a comprehensive answer to this question. We have also begun looking at outside answers to this question in order to test them and compare our results against them. 

## Outcomes

### Baseline Outcomes
The largest progress throughout this milestone was in developing the high security baseline. We were able to create a baseline using the NIST 800-53 families and individual controls that we can now adapt into AWS. Using this high security baseline we are able to filter it down into medium and low security baselines to further test against. 

### Infrastructure Outcomes
The majority of our results were on the infrastructure side. We were able to gain access and permissions for the AWS account through Dr. Hale and the school's IT team. This is what allowed us to make further progression by spinning up the three different S3 buckets. After they were spun up, test data was filled into the bucket and removed later in order to test permissions and gain further familiarity with the test bed. The next step was spinning up the Kali box for further use. We will use this to test and further develop our three baselines.

### Listed Outcomes
* Developed High Security Baseline
* Gained Access to AWS Account
* Received Proper Permissions in AWS
* Spun up Three S3 Buckets
* Began Spinning up Kali Box
* Developed a Research Question for Final Project

## Hindrances

### Baseline Hindrances
Within developing the baseline not too many hindrances were encountered. The one small hindrance was determining which baseline we would model ours after. We ultimately decided on NIST 8000-53 as it is the most widely used and fully encompassed our needs in the project. 

### Infrastructure Hindrances
We saw the most challenges within building the infrastructure. Gaining access to the AWS account took about one week while waiting for a response from the school IT team. Once we received access there was a small amount of confusion on how access was granted which was delayed for another few days. Once access was gained we spent the next few days determining the correct permissions needed for us to carry out our testing. Overall we had some time delays, but all problems were fairly easy to solve. 


## Ongoing Risks
|Risk name (value)  | Impact     | Likelihood | Description |
|-------------------|------------|------------|-------------|
|Limitations of Pen Testing (63) | 9 | 7 | As we have moved towards a heavy penetration testing based research question the risk has greatly increased. Without sufficient time or knowledge we will not be able to comprehensively answer the research question. |
|Legality of Scanning S3 Buckets (36) | 9 | 4 | The risk has decreased as we landed on using EC2 from within the AWS account. We are also using the school AWS account so we are not scanning public buckets. |
|Scripting Limitations in AWS (25) | 6 | 4 | We have not yet worked on the scripting within AWS so the risk has not changed.|
|Data Acquisition (18) | 9 | 2 | We have not yet worked on the data acquisition for the S3 buckets so the risk has not changed. |
|Creating Realistic AWS Infrastructure (10) | 5 | 2 | Fairly realistic infrastructure has already been created. It is not likely we will have issues with further developing it. |
