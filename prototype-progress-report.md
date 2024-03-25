# Progress Report (insert date here)
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

## Outcomes
(brief overview of outcomes - what did you achieve?)

also list them out like this:
* outcome 1
* outcome 2

## Hinderances
(insert brief discussion of challenges encountered)

## Ongoing Risks
(address your project risks identified from Milestone 1 and update them based on your current progress, this should be a table)

