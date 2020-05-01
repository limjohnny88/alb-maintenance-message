# Lambda Function to Start/Stop Maintenance Message on ALB

## Getting Started

This CloudFormation template will spin up the Lambda function to start and stop the maintenance message on the target ALB Listener.

### Prerequisites

Access to AWS Console with Administrative rights to spin up the CloudFormation Stack (IAM Role, Lambda and Access to ELB)

## Deployment - via AWS Console
1. Navigate to AWS CloudFormation in AWS Console.
2. Click on "Create stack" -> "With new resources (standard)".
3. Select "Upload a template file" and upload the template.yaml, and click on "Next".
4. Enter a Stack name.
5. Update TARGETALBLISTENERARN with your target ALB Listerner ARN. You can find it under the Listener tab on your ALB settings. *e.g. arn:aws:elasticloadbalancing:ap-southeast-1:[ACCOUNT_ID]:listener/app/[ALB_NAME]/[ALB_ID]/[ALB_LISTENER]*.
6. Update TARGETHOSTNAMELIST with your target target host name (seperated by ,) *e.g. example.com,www.example.com*.
7. Update TARGETMAINTENANCEMESSAGEHTML with your target maintenance message (HTML format).
8. Click on "Next".
9. Click on "Next" again.
10. Check the settings on the page and if everything is OK check on "I acknowledge that AWS CloudFormation might create IAM resources." and click "Create Stack".
11. The CloudFormation stack will start to spin up the resources. If everything is OK, you will see [Your Stack Name] as CREATE_COMPLETE.

## Triggering the Maintenance Page - via AWS Console
1. Navigate to AWS Lambda in AWS Console and go to the section "Functions".
2. Click on the "XXXX-StartMaintenancePageOnALB-YYYY" function that have been created by the CloudFormation Stack.
3. Click on "Test" on the top right corner, and if it is your first time triggering, then Create a new test event. You can give it any Event Name and keep the JSON message as default, and click "Create". Click on "Test" again.
4. You should see a green success message on the top if the Lambda function have been triggered successfully.
5. Navigate to your target hostname, and you should see the maintenance page up and running.

## Removing the Maintenance Page - via AWS Console
1. Same as Triggering. But now repeat the same using the "XXXX-StopMaintenancePageOnALB-YYYY" Lambda function.
