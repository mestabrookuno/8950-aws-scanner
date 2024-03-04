# Use Cases
## Use Case 1 - Low Security
An example of a use case which might implement the low security baseline would be a news site looking to host files and images for distribution to their readers. They would need to provide global read-only permissions to the entire Internet. Priorities would be data integrity and availability. 

## Use Case 2 - Medium Security
An example of a use case which might implement the medium security baseline would be a business storing customer information. This data is sensitive enough that it should be restricted to only need-to-know users and systems. The data should not be accessible publicly outside of the organization. A strong focus on logging and accountability would be needed. 

## Use Case 3 - High Security
An example of a use case which might implement the high security baseline would be a hospital storing patient health information or electronic health records (EHR). This type of information is regulated via laws like HIPAA and would be subject to audits to confirm certain controls were being met. There would be a strong focus on confidentiality, as well as logging and accountability, and integrity. In addition to the SP800-53 high security baseline controls, some HIPAA controls would need to be integrated into this baseline as well if using this as an example scenario. 

|Baseline Name|Encryption at Rest|Setting 2|Setting 3|
|-------------|-------------------|----------|------|
|Baseline Level 1|Yes|NA|NA|

# Work Breakdown
## Applicable Control Families
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

## Mark
- AC Access Control
- AT Awareness and Training
- AU Audit and Accountability

## Matt
- CA Assessment, Authorization, and Monitoring
- CM Configuration Management
- IA Identification and Authentication

## Grace
- MP Media Protection
- SC System and Communications Protection
- SI System and Information Integrity
