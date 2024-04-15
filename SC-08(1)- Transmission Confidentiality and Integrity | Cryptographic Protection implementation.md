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
