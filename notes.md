# Set Up Notes

### S3 Resource Steps

Manually created a xilution-myvoteapp-staging S3 bucket.

Manually zipped up the lambdas.

`rm -rf receive-vote.zip ; zip -r receive-vote.zip app.js node_modules/* package.json`

`rm -rf aggregate-votes.zip ; zip -r aggregate-votes.zip app.js`

Copied receive-vote.zip and aggregate-votes.zip into xilution-myvoteapp-staging.

### Cloud Formation

`aws cloudformation create-stack --stack-name lambda-refarch-webapp --template-body file:///Users/tbrunia/Documents/git/lambda-refarch-webapp/lambda_webapp.template --capabilities CAPABILITY_IAM`

`aws cloudformation delete-stack --stack-name lambda-refarch-webapp`

### API Gateway

According to the instructions in (README.md)[README.mb], manually Set up a /vote resource and POST method.
Paste (this)[mappingtemplate-integrationrequest.txt] into the integration request.
Paste (this)[mappingtemplate-integrationresponse.txt] into the integration response.
Change the Method Response content type to application/xml.

### Cognito

Updated the unauthorized policy with the contents of the policy.json file.
Updated the refresh.js file with the new Identity Pool ID.

### More S3 Resource Steps

Manually copied error.html, index.html, narrow.css, refresh.js and vote.css in to the xilution-myvoteapp-web bucket.

###

Through the AWS DynamoDB Console, configure the Vote DynamoDB table to trigger the Aggregate Lambda function.

### TODO

1. Automate - zip and send of lambda code to S3
2. Automate the upload of the web resources.
