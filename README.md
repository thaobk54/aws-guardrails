# Secure AWS account

- Enabled Guardduty to monitor AWS accounts and workloads for malicious activity and delivers detailed security findings for visibility and remediation.
- Budget alerts to notify when AWS spend exceeds a threshold. The current threshold is $2000 per month.
- The workflow deletes the exposed IAM Access Key, summarizes the recent API activity for the exposed key, and sends the summary message to an Amazon SNS Topic to notify the subscribers. Using Trusted Advisor.
- Enabled AWS Config to record and evaluate configuration changes to AWS resources in account.
- Added a config rule that checks whether your EC2 instances are of the specified instance types. Current rule does not allow the instance type which has more than 8 vcpus and 16 GB of memory.
- Setup an automated response to an access denied event that occurs within a CloudTrail event, a Failed authentication attempt to the AWS console, or a Client.UnauthorizedOperation (user try using operations which is not allowed) event occurs