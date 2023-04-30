#aws #cloud #DevOps #iaac 

Treat Infrastructure as code.
We can define AWS resources in a structured text format, either YAML or JSON, called a **CloudFormation Template**.
Then We can create a **Cloudformation Stack** in AWS, which contains resources created via Cloudformation template.
CloudFormation tracks what changes need to be performed and makes all the changes while keeping your resources in a consistent state. CloudFormation can also create **Change Sets** for approval before making the changes, if you choose.
![[Pasted image 20230415010957.png]]
# Basic Concepts
**Resources**: Resources that we can create in AWS.
**Templates**: Text-based JSON or YAML descriptions of CloudFormation stacks.
**Stack**: A collection of AWS resources that you can manage as single unit.
**StackSet**: A named set of stacks that use the same template, but applied across different accounts and regions.

## Sample Cloudformation Template
```yaml
---
AWSTemplateFormatVersion: "2010-09-09"
Description: "Simple budget example"
Parameters:
  Email:
    Type: String
    Default: email@example.com
    Description: Please enter the email address to which budget notifications should be addressed.
Resources:
  BudgetExample:
    Type: "AWS::Budgets::Budget"
    Properties:
      Budget:
        BudgetLimit:
          Amount: 10
          Unit: USD
        TimeUnit: MONTHLY
        BudgetType: COST
      NotificationsWithSubscribers:
        - Notification:
            NotificationType: ACTUAL
            ComparisonOperator: GREATER_THAN
            Threshold: 99
          Subscribers:
            - SubscriptionType: EMAIL
              Address: !Ref Email
        - Notification:
            NotificationType: ACTUAL
            ComparisonOperator: GREATER_THAN
            Threshold: 80
          Subscribers:
          - SubscriptionType: EMAIL
            Address: !Ref Email
Outputs:
  BudgetId:
    Value: !Ref BudgetExample
```
Ref: BudgetWithParams.yml

## Running from Command Line
```bash
aws cloudformation create-stack --stack-name SimpleBudget --template-body file://BudgetWithParams.yaml
```
Ref: Cmd for BudgetWithParams.yml

### Note
To pass parameter values from the CLI.
https://stackoverflow.com/questions/45749424/passing-multiple-parameters-from-external-file-to-cloudformation-template-and-us
