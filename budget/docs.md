# aws-budget-alarms

A CloudFormation template for sending budget alarms to slack using AWS Chatbot

## Preview

![Slack Notification](./assets/slack_preview.png)

## Prerequisites

- [Configure a chat client in AWS Chatbot](https://docs.aws.amazon.com/chatbot/latest/adminguide/setting-up.html)
- Invite the AWS Chatbot to your Slack channel: `/invite @aws`

- Slack channel ID: right-clicking the channel you want to use > Additional Options > Copy Link

![Slack Channel ID](./assets/slack_id.png)

`https://mycompany.slack.com/archives/SlackChannelId`

(Only provide the string after `/archives/`)


## Installation

The installation is automated with Infrastructure as Code using Cloudformation.


The stack includes:
 
- IAM Chatbot role
- SNS  Topic
- SNS Topic Policy
- AWS Budget
- AWS Chatbot Configuration for Slack

### AWS CLI

Deploy as Cloudformation stack:
```
aws cloudformation deploy \
    --template-file BudgetNotification-Chatbot.yaml \
    --stack-name CF-BudgetNotification-Chatbot \
    --capabilities CAPABILITY_IAM \
    --parameter-overrides \
    BudgetLimit=<limit-in-USD> \
    CostNotification=<ACTUAL | FORECASTED> \
    SlackChannel=<your-slack-channel-id> \
    SlackWorkspaceId=<your-aws-chatbot-workspace-id-for-slack> \
    --region <your-region-1>
```

Using email instead of Slack:
```
aws cloudformation deploy \
    --template-file BudgetNotification.yaml \
    --stack-name CF-BudgetNotification \
    --capabilities CAPABILITY_IAM \
    --parameter-overrides \
    BudgetLimit=<limit-in-USD> \
    CostNotification=<ACTUAL | FORECASTED> \
    NotificationEmail=<your-email> \
    --region <your-region-1>
```