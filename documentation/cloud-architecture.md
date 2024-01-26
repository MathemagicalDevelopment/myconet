# Cloud Architecture

## Users/Authentication
AWS Cognito user pool

## Frontend
AWS Amplify hosted frontend with a CI/CD pipeline handled by AWS CodePipeline

## Assets
Device -> Route53 <-> CloudFront <-> S3

## API Calls
Device -> Route53 <-> CloudFront <-> API Gateway <-> Lambda
Lambda <-> Cognito user pools
Lambda <-> RDS Proxy <-> RDS
Lambda <-> S3
Lambda -> Cloudwatch logs