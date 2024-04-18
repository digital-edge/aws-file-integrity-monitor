# AWS File Integrity Monitoring Solution

This CloudFormation template deploys a File Integrity Monitoring (FIM) solution using AWS Lambda, DynamoDB, and SNS. It is designed to monitor the integrity of files across specified EC2 instances and alert via email if any changes are detected.

## Description

The template sets up the necessary AWS resources to monitor file integrity on EC2 instances. When a file change is detected, an alert is sent to the specified email addresses using Amazon Simple Notification Service (SNS).

## Resources Created

- **AWS Lambda Functions:** Executes the file integrity checks and logs results.
- **DynamoDB Tabls:** Store the file integrity data.
- **SNS Topic:** Sends notifications to email recipients when changes are detected.

## Parameters

- **EmailRecipients**
  - **Type:** String
  - **Default:** `test@domain.com`
  - **Description:** Comma separated list of email recipients for notifications.

- **FilesJson**
  - **Type:** String
  - **Default:** `'{}'`
  - **Description:** JSON string with a list of instances and files to monitor. Please refer to the documentation for format details.
  - **Format example:** 

```
{
     'i-0123456789abcdefg': {'os': 'Windows', 'files': ['D:\Sites\MySite1\web.config', 'D:\Sites\MySite2\Web.config']},
     'i-9876543210gfedcba': {'os': 'Linux', 'files': ['/local/sites/mysite/settings.php']}
}
```


## Prerequisites

- AWS Account with permissions to create Lambda, DynamoDB, and SNS resources.
- Configured AWS CLI or AWS SDK setup.

## Deployment

1. Clone this repository to your local machine.
2. Open the AWS Management Console.
3. Navigate to the CloudFormation service.
4. Choose 'Create Stack' and upload the provided CloudFormation template.
5. Fill in the parameter values as required.
6. Click on 'Create Stack' to deploy the resources.

## Configuration

- Modify the `FilesJson` parameter to include the instances and files you wish to monitor. The format should follow the JSON schema outlined in the documentation.

## Usage

Once deployed, the system will automatically monitor the specified files for any changes based on the provided `FilesJson` configuration. Notifications will be sent to the `EmailRecipients` if any discrepancies are detected.

## License

This project is licensed under the MIT License - see the LICENSE file for details.





