# © 2021 Amazon Web Services, Inc. or its affiliates. All Rights Reserved.
# This AWS Content is provided subject to the terms of the AWS Customer Agreement
# available at http://aws.amazon.com/agreement or other written agreement between
# Customer and either Amazon Web Services, Inc. or Amazon Web Services EMEA SARL or both.

#Prerequisites
    # An active AWS account
    # The CMK key should already exist to encrypt RDS Instances and Clusters
    # Plesae ensure you have access to update KMS CMK Resource policy
    # An unencrypted Amazon RDS DB instance or Clusters
    # Access to AWS services, including:
    #     AWS Config
    #     AWS RDS
    #     AWS System Manager Automation Document
    #     AWS CloudFormation (Option #1)
    #     AWS CDK (Option #2)
    #     AWS Key Management Service (KMS) 
    #     AWS Identity and Access Management (IAM)
    #     You must have AWS Config enabled in your AWS account. For more information, see Getting Started with AWS Config.

# You can enable encryption for an Amazon RDS DB instance only when you create it, not after the DB instance is created.
# You can't have an encrypted read replica of an unencrypted DB instance or an unencrypted read replica of an encrypted DB instance.
# You can't restore an unencrypted backup or snapshot to an encrypted DB instance.
# Amazon RDS encryption is available for most DB instance classes. The following table lists DB instance classes that do not support Amazon RDS encryption: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.Encryption.html
# To copy an encrypted snapshot from one AWS Region to another, you must specify the CMK in the destination AWS Region. This is because CMKs are specific to the AWS Region that they are created in.
# The source snapshot remains encrypted throughout the copy process. Amazon RDS uses envelope encryption to protect data during the copy process. For more information about envelope encryption, see Envelope encryption in the AWS Key Management Service Developer Guide.
# You can't unencrypt an encrypted DB instance. However, you can export data from an encrypted DB instance and import the data into an unencrypted DB instance.
# You should delete a CMK only when you are sure that you don't need to use it anymore. If you are not sure, consider disabling the CMK instead of deleting it. You can reenable a disabled CMK if you need to use it again later, but you cannot recover a deleted CMK. 
# If you don't choose to retain automated backups, your automated backups in the same AWS Region as the DB instance are deleted. They can't be recovered after you delete the DB instance. 
# Your automated backups are retained for the retention period that is set on the DB instance at the time when you delete it. This set retention period occurs whether or not you choose to create a final DB snapshot. 