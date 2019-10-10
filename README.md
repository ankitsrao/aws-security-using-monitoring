# Implementing securtiy in AWS accounts using monitoring and alarming tools
Creates metrices and alarms for various security events for the AWS account

# SYNOPSIS
     Script to create metrices and alarms for various events in the AWS Account.
# .DESCRIPTION
     This script will create a CloudTrail, Cloudwatchlog group, S3 bucket, Event Metrices, SNS Topic and subscription and alarms to remediate the below list of policies.
     1) Ensure a log metric filter and alarm exist for unauthorized API calls
     2) Ensure a log metric filter and alarm exist for Management Console sign-in without MFA
     3) Ensure a log metric filter and alarm exist for usage of 'root' account
     4) Ensure a log metric filter and alarm exist for IAM policy changes
     5) Ensure a log metric filter and alarm exist for CloudTrail configuration changes
     6) Ensure a log metric filter and alarm exist for AWS Management Console authentication failures
     7) Ensure a log metric filter and alarm exist for disabling or scheduled deletion of customer created CMKs
     8) Ensure a log metric filter and alarm exist for S3 bucket policy changes
     9) Ensure a log metric filter and alarm exist for AWS Config configuration changes
     10) Ensure a log metric filter and alarm exist for security group changes
     11) Ensure a log metric filter and alarm exist for changes to Network Access Control Lists (NACL)
     12) Ensure a log metric filter and alarm exist for changes to network gateways
     13) Ensure a log metric filter and alarm exist for route table changes
     14) Ensure a log metric filter and alarm exist for VPC changes
# .NOTES
     Version: 1.0

# PREREQUISITE
       - Install aws cli
         Link : https://docs.aws.amazon.com/cli/latest/userguide/install-linux-al2017.html
       - Configure your aws account using the below command:
         aws configure
         Enter the required inputs: (configure using details of the AWS account where you want to remediate the policies)
             AWS Access Key ID: Access key of any admin user of the account in consideration.
             AWS Secret Access Key: Secret Access Key of any admin user of the account in consideration
             Default region name: Programmatic region name where you want to deploy the resources (eg: us-east-1)
             Default output format: json  

# .EXAMPLE
     Command to execute : aws cloudformation deploy --template-file create-metric-alarms.yml --stack-name <stack-name> --parameter-overrides env=<environment-prefix> region=<region-name> awsaccountid=<12-digit AWS account Id> emailid=<email-id where you wish to receive notifications> --capabilities CAPABILITY_NAMED_IAM

# .INPUTS
     stack-name: Name of the stack that will be created
     env: Environment prefix
     region: Programmatic region name where you want to deploy the resources (eg: us-east-1)
     awsaccountid: 12-digit AWS Account Id of the account where you need to set up the alarms
     emailid: valid email id where one wishes to receive he notifications
# .OUTPUTS
     None

# .NOTE: 
Once the script successfully creates all the resources and alarms, you need to subscribe to the SNS using the link you will receive in the entered email, to start receiving notificatins of the alarms.

