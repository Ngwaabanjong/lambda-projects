# lambda-cloudwatch-sns
This code pulls error, info, and critical logs from CloudWatch using Lambda trigger and send an email to end users using SNS

# STEPS
## Create an SNS topic
Create a topic and subscribe 

# Create an IAM role for Lambda 
On IAM
- Select Lambda
- Attach: CloudWatchFullAccess, AmazonSNSFullAccess

## Create a Lambda Function with for sample errors that will be monitored, for test porpose. 
On Lambda
- create a funtion with python runtime.
- use the sampleError.py file
- click on deploy
- click on test, then test
- go to CloudWatch and view logs

## (2nd) Create a Lambda Function that will trigger the error logs from CloudWatch and send to email.
On Lambda
- create a funtion with python runtime.
- use the errorHandler.py file
- Add trigger
- Select CloudWatch
- Select the Log group you want to monitor, an exaple is the CloudWatch log group of the sampleError Lambda.
- File name: choose a name for your file
- Filter pattern: ?ERROR ?INFO ?CRITICAL

## Add environment variables (2nd)
On Lambda
- Click on environment variables
- Go to SNS and open the topic details and copy the arn
- Key: SNS_TOPIC_ARN
- Value: arn:aws:sns:us-east-1:XXX748XXXXX:MyTopic