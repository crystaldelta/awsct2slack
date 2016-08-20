# CloudTrail to Slack (via Cloudwatch Logs)

Handles sending CloudTrail events that you are interested in to Slack. This reads from CloudWatch Logs (vs SNS+S3).

Similar to
https://github.com/auth0/cloudtrail-slack

### Installation

1. Modify config.js with the settings you would like
2. Deploy to lambda
  * Node 4.3
```
# Or Via CLI
# Create lambda example
aws lambda create-function --function-name Cloudtrail2Slack --runtime nodejs4.3 --role xxxx --handler Cloudtrail2Slack.handler --zip-file file://cloudtrail2slack.zip --profile xxxx --timeout 30 --memory-size 256
```
3. Associate the CloudWatch Logs group containing CloudTrail events

### Testing Locally
```
node runLocal.js
```

### Deploying to AWS

```
# Prepare code zip file
rm cloudtrail2slack.zip
zip -rq cloudtrail2slack.zip .

# update it
aws lambda update-function-code  --function-name Cloudtrail2Slack --zip-file fileb://cloudtrail2slack.zip
```