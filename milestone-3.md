# Progress Report 5/16/2024
## Overview
The last third of this semester was focused on pulling together the settings we'd collected to satisfy the NIST 800-53 controls throughout the semester. By this point we had already decided on which NIST controls were applicable to S3, and had done some work on figuring out what S3 settings (or AWS settings) would be needed to satisfy the list of NIST controls we had put together. Another pass was made at the list of controls to finalize what settings would be needed. 

Once the sum of the S3 settings and associated information was put together, we needed to produce a deliverable that relayed that information. We decided that the target audience should be that of non-AWS experts. Administrators who were responsible for securing S3 buckets but did not have much formal training in that specialty would benefit most from an easy-to-read guide detailing how to solve some of the most common security issues with S3. For that reason, we ended up taking a threat-centric approach in our document. Common S3 threats and configuration issues were spelled out, and detailed steps were provided for someone to follow to help remediate that issue or threat. All of this information was put into a GitHub Pages site that would be publicly accessible so that the information would be available via the Internet, and could be updated easily. 

Site: https://securing-s3-buckets.github.io/s3-security/

## Outcomes
We were able to create a mapping of NIST SP800-53 controls to AWS S3 controls. This mapping helped us lay out the most impactful security controls that an administrator can "tweak" in the S3 console. We then took this list of settings and mapped those to the most popular threats facing S3 buckets. Then, that was used to create a guide for non-AWS experts to administer their S3 buckets. There were sections provided that had detailed instructions laying out what settings to change to address various popular S3 threats. Then, we were able to recruit a non-AWS expert to go through the instruction set and try and apply the suggested settings. We were able to get some valuable feedback from this tester and that helped us make revisions to, and simplify, the instruction document we ended up delivering at the end of the semester. 

In summary: 
* Created a list of NIST SP800-53 controls applicable to S3
* Mapped NIST 800-53 controls to AWS settings
* Tied those S3 settings to the most popular threats against S3 buckets
* Authored a document for S3 admins with little experience to follow to secure their S3 buckets against common threats
* Delivered a page mapping NIST 800-53 controls to specific AWS settings
* A non-technical user was used as a tester to validate our instructions, and adjustments were made based upon their experience and feedback

## Hinderances
