# AWS Lambda

AWS Lambda is a compute service provided by Amazon Web Services (AWS) that allows you to run code without the need to provision or manage servers. With AWS Lambda, you can execute code for various types of applications or backend services without any administrative overhead.

## Key Features of AWS Lambda:

1. Serverless Administration: AWS Lambda handles the provisioning and capacity of compute fleets, ensuring a balance of memory, CPU, network, and other resources.

2. Server and OS Maintenance: Lambda takes care of server and operating system maintenance.

3. High Availability and Automatic Scaling: The service ensures high availability and automatically scales based on the number of requests per second.

4. Monitoring and Security: AWS Lambda manages monitoring and security, including applying security measures to the functions.

5. Code Deployment: You can deploy your code as one or more Lambda functions in languages such as Node.js, Java, PowerShell, C#, Ruby, Python, and Go.

6. Cost-Effective: AWS Lambda charges you only for the compute time you consume, with no charges when your code is not running.

7. No Server Management: You don't need to log into compute instances or customize the operating system or language runtime.

## How Lambda Works:

1. You upload your code as one or more Lambda functions to AWS Lambda.
2. AWS Lambda executes the code on your behalf.
3. Once invoked, Lambda automatically manages the required servers for execution.

## Differences Between AWS Lambda and AWS EC2:

### AWS Lambda:

-   Platform as a Service (PaaS) offering.
-   Supports limited languages: Node.js, Python, Java, C#, Ruby, Go, and PowerShell.
-   Code is pushed to AWS Lambda.
-   No direct access to compute instances or customization of OS and language platform.

### AWS EC2:

-   Infrastructure as a Service (IaaS) offering.
-   No language restrictions; supports running any code or language.
-   Requires choosing the OS, installing necessary software, and deploying code to EC2 instances.
-   Offers various options for customizing OS instance types, network, security patches, RAM, CPU, etc.

## Important Terms Used in Lambda:

1. Function: A resource that can be invoked to run code in AWS Lambda. It contains code to process events and a runtime that passes requests and responses.

2. Runtime: Allows functions in different languages to run in the same base executing environment.

3. Event: A JSON-formatted document containing data for a function to process.

4. Event Source/Trigger: An AWS service (e.g., AWS SNS) or a custom service that triggers your function and executes its logic.

5. Downstream Resources: AWS services (e.g., DynamoDB tables or S3 buckets) that your Lambda function calls once it is triggered.

6. Concurrency: The number of requests your function serves at any given time.

## Lambda Triggers:

AWS Lambda can be used to run your code in response to various events, such as changes to data in an Amazon S3 bucket or an Amazon DynamoDB table. It can also respond to HTTP requests using Amazon API Gateway, enabling you to build data processing triggers for AWS services like S3, DynamoDB, or handle streaming data stored in Kinesis.

## Example of S3 Trigger:

-   A user creates an object in an S3 bucket.
-   Amazon S3 detects the object-created event.
-   Amazon S3 invokes your Lambda function using the permissions provided by an execution role.
-   AWS S3 knows which Lambda function to invoke based on the event source mapping stored in the bucket notification configuration.

## AWS Lambda Function Configuration:

A Lambda function consists of code and associated dependencies, along with configuration information. You specify the configuration when creating a Lambda function, and you can update some of the config data later using the Lambda API.

## Key Elements of Lambda Function Configuration:

-   Compute resources that you need: you only specify the amount of money you want to allocate from your lambda function.
-   aws lamda allocates CPU power propotional to the money by using the same ration as a general purpose amazon EC2 instance type, such as an M3 Type.
-   you can update the config and request additional memory in 64 MB increments from 128MB ti 3008MB.
-   function larger than 1536MB are allocated multiple CPU threads.

## Maximum Execution Timeout

-   you pay for the AWS Resources that are used to run your lamda function.
-   to prevent your lamda functionfrom running indefinetly, you specify a timeout.
-   When the specified timeout is reached aws lamda teamates your lamda function.
-   default is 3 seconds and maximum is 900 seconds(15 min).

## IAM Roles:

AWS Lambda assumes an IAM role when executing functions on your behalf.

## AWS Lambda Function Service Access:

Lambda functions can access AWS services or non-AWS services, AWS services running in an AWS VPC, non-AWS services running on EC2 instances within an AWS VPC. You can enable Lambda functions to access resources inside your private VPC by providing VPC-specific config information, including VPC subnet IDs and Security Group IDs.

## Different Ways to Invoke Lambda Function:

1. Synchronous Invoke (Push):

-   Functions execute immediately when invoking the Lambda API call, and you wait for the function to process the event and return a response.

-   Here are the list of a serice that invoke lamda func sync.
    -   Elastic load Balancer.
    -   Amazon Cognito.
    -   Cloudfront
    -   API Gateway
    -   Amazon Gateway
    -   Kinesis Data firebase

2. Asynchronous Invoke (Event):

-   Lambda places the event in a queue and returns a success response without additional information. Lambda can send an invocation record to other services like SQS, SNS, Lambda, or EventBridge.

-   Here are list of service that incoke lamda func async:-
    -   Amazon S3
    -   Amazon SNS
    -   Amazon SES
    -   Cloudformation
    -   cloudwatch logs
    -   cloudwatch events
    -   Aws CodeCommit
    -   AWS config

3. Poll-based Invoke (Pull-based): Lambda polls AWS Stream and queue-based services on your behalf, retrieves records, and invokes your function.

-   The following are supported service
    -   Amazon Kinesis
    -   Amazon SQS
    -   Amazon DynamoDB Streams

## Related Topics:

1. AWS Elastic Beanstalk
2. AWS EC2
3. AWS S3
4. AWS Amplify
5. AWS RDS
6. AWS DynamoDB
7. AWS ELK Stack
8. AWS SNS
9. Jenkins
10. SonarQube

> Note: Some services might have undergone updates or changes beyond the knowledge cutoff date.
