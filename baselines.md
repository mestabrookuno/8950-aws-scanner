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
**Control check for high-impact security baseline**:

| Control                                | Definition                                                                                                         | Applicability                                                                                                                                          | Implementation                                                                                                                                                                                              |
|----------------------------------------|--------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MP-1: Media Protection Policy And Procedures | Focuses on establishing and implementing policies and procedures to protect media containing sensitive information | Yes, in case sensitive data is stored in the S3 bucket. **ex**: Develop media protection policies in compliance with HIPAA regulations, outlining procedures for protecting electronic protected health information stored in S3 buckets. | - Who in the organization is going to develop, document, and disseminate <br> - Who is going to manage <br> - Who is going to review and update |
| MP-2: Media Access                         | **Threat addressed**: Tampering and information disclosure <br> - Focuses on <ins> controlling access </ins> to media containing sensitive information to ensure that only authorized individuals or systems are granted access based on established policies and procedures.                                                             | **ex**: Denying access to patient medical records in a community hospital unless the individuals seeking access to such records are authorized healthcare providers is an example of restricting access to non-digital media. | Clearly defining what type of media is restricted to who in the organization                                                                                                                                 |
| MP-3: Media Marking                        | Focus on <ins> establishing policies and procedures for marking media </ins> with appropriate labels to indicate the sensitivity, classification level, handling restrictions.       | **Importance**: scenarios where <ins> precise identification and classification </ins> of sensitive data stored in AWS S3 buckets are critical for maintaining confidentiality and compliance with regulatory requirements.             | Clearly define what <br> - data classification need to be adopted <br> - Marking and labels                                                                                                                           |
| MP-4: Media Storage                        | <ins> Secure storage </ins> of media to prevent unauthorized access, data corruption, and loss. **Threat addressed**: Tampering and information disclosure                                                                                                                                                              |                                         | Clearly define <br> - media that needs to be physically controlled and securely stored and where <br> - Who and what protects the media until destruction using approved methods 

- MP Media Protection
- SC System and Communications Protection
- SI System and Information Integrity
