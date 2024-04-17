## Enabling Server-Side Encryption (SSE) for AWS S3 buckets

 **Sign in to the AWS Management Console**: Go to the [AWS Management Console](https://console.aws.amazon.com/).

 **Navigate to Amazon S3**: From the list of AWS services, select "S3" to access the Amazon S3 dashboard.
 
 ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/ab5f2345-005f-44fd-aaff-00cd30f22616)


 **Select the S3 Bucket**: Click on the name of the S3 bucket for which you want to enable server-side encryption.

 **Configure Bucket Properties**: Once the bucket is selected , click on the "Properties" tab.
 

 **Enable Server-Side Encryption**: Scroll down to the "Default encryption" section and click on it to expand the options.

 ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/df084e85-f9f3-4759-b268-14b9f3f74112)


 **Choose Encryption Type**: Select the encryption type you want to use for server-side encryption. There are three options available:

    - Server-side encryption with Amazon S3 managed keys (SSE-S3): This is Amazon S3-managed encryption, where AWS automatically handles the encryption and decryption of your objects using Advanced Encryption Standard (AES) with 256-bit keys.
    
    - Server-side encryption with AWS Key Management Service keys (SSE-KMS): This option allows you to use AWS Key Management Service (KMS) to manage encryption keys. SSE-KMS provides additional control and auditing capabilities, allowing you to create and manage keys and define access policies.
    
    - Dual-layer server-side encryption with AWS Key Management Service keys (DSSE-KMS): Amazon S3 applies two individual layers of object-level encryption to satisfy compliance requirements for highly regulated customers.
    

![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/91e0c6c4-229f-45ed-8a4e-790d28b691d6)

    
 **Save Changes**: After selecting the desired encryption type, click "Save" to apply the encryption settings to the bucket.

 **Access Control List (ACL)**: Ensure that the bucket's ACL settings are configured to allow only authorized users and applications to access the bucket. This helps prevent unauthorized access to the encrypted data.

 **Upload Encrypted Data**: Upload objects to the S3 bucket as usual. Amazon S3 automatically encrypts these objects using the specified server-side encryption method.
 

 ## Configuring AWS Key Management Service (KMS) for S3 Bucket

**Sign in to the AWS Management Console:**
   Go to the [AWS Management Console](https://aws.amazon.com/console/) and sign in to your AWS account.

**Navigate to AWS KMS:**
   Navigate to the AWS Key Management Service (KMS) console. You can find it by typing "KMS" in the search bar at the top of the console.
  ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/0f64c527-0279-47d6-af6f-f109f597dd82)


**Create a Customer Master Key (CMK):**
   - Click on "Customer managed keys" in the left navigation panel.
   - Click on the "Create key" button.
     ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/7798481c-49f8-4d6f-a6f2-d9c93c0bba16)

   - Choose the key creation method (e.g., "Symmetric").
     ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/16442302-47f4-4ff8-b0bd-b51eb0b19e6c)

     ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/0f002b52-83bd-4d85-b398-8cca16dc80d3)


   - Define key details, usage permissions, and rotation settings.
     
     ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/ecb9c429-71c4-4f95-a8a4-02114560765d)

     ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/184fffd1-3ad5-4712-9392-7f23231e2d54)

     ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/4b5bf93b-b7c8-4d82-a499-36e1120da793)


   - Review and create the CMK.
     ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/218ab850-c1a9-4724-8d28-012f339706a3)


**Note the Key ARN:**
   After creating the CMK, note down the Amazon Resource Name (ARN) of the CMK.
   ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/ccf780de-255f-4536-806b-3b43a3bd7eed)

  ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/b94cb840-743c-4eaf-ac49-4c7da982f557)



**Navigate to AWS S3:**
   Go to the AWS S3 console by typing "S3" in the search bar or under the "Storage" section.

**Select the S3 Bucket:**
   Choose the bucket for which you want to enable encryption using AWS KMS.

**Enable Default Encryption:**
   - Click on the "Properties" tab of the selected bucket.
   - Click on "Edit" under the "Default encryption" section.

**Choose KMS Encryption:**
   Select "AWS-KMS" as the default encryption method.
   ![image](https://github.com/mestabrookuno/8950-aws-scanner/assets/129107955/5d2ae354-40ff-4d4d-a5c6-38f3d32ec13b)


**Select the KMS Key:**
   Choose the KMS master key (CMK) created earlier from the dropdown list.

**Save Changes:**
    Click on the "Save changes" button to enable encryption for the S3 bucket using AWS KMS.

