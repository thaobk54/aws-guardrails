# GuardDuty

## Getting Started

Deploy as Cloudformation stack:

```
aws cloudformation create-stack \
--stack-name guardduty-cf-stack \
--capabilities CAPABILITY_NAMED_IAM \
--template-body file://template.yaml
```