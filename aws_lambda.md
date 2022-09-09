# AWS Lambda
This summary was written in 09/09/2022. Depending on when you are reading this, you should only use this summary as a reference, not an absolute guide. AWS products change quite quickly and some features may not be able or new features may arise. Chances are the concepts will still remain the same but for more detailed technical tips, look at the official AWS documentations when working.

## General info
Computing service to run code in any supported languages without manually provisioning or managing servers. Think of it as a hosting service for web applications' backend services. Examples of Lambda in action:

- Data-processing triggers for AWS S3 and AWS DynamoDB
- Process streaming data stored in AWS Kinesis

You pay only for the compute time of the function, no charge when the code is not running.

Because Lambda manages all the computing resources and configurations, you cannot log in to compute instances or customize the operating system on provided runtimes. To manage your own compute resources, checkout Amazon EC2 or AWS Elastic Beanstalk.

## Concepts

### Function
A Lambda function is a resource that you can invoke to run your code. A function has code to process the events that you pass into the function or that other AWS services send to the function. When a request is made, the function is invoked and AWS Lambda creates an instance of the function to process the request. Many instances of the function can be invoked and run in parallel. 

### Trigger
Resource or configuration that invokes the Lambda function. This can be done via the Lambda API or other AWS services like AWS SQS.

### Event source mapping
Resource in Lambda that reads items from a stream or queue and invokes the Lambda function. 

### Event
JSON-formatted document that contains data for the Lambda function to process. At runtime, AWS Lambda converts the event to an object that can be passed to the Lambda function. Depending on which entity that invokes the function, the structure of the event is different.

When the user invokes a function, the user can decide on the event's structure.

When an AWS service like SQS invokes a functino, the service decides on the event's structure. Checkout documentation regarding AWS Lambda with other services for more specific details.

### Execution environment
Provides an isolated environment for the Lambda function to run in. The execution environment manages the process and resources of the Lambda function. 

### Runtime
Provides a language-specific environment that runs within an execution environment. The runtime relays invocation events, context information, and responses between Lambda and the function. You can use runtimes that Lambda provides or build your own. 

### Instruction set architecture
Determines the type of computer processor Lambda should use for the function. 

### Deployment package
Lambda functions are deployed via a deployment package. Two types of deployment packages:
- .zip file archieve. Configure your function to use a runtime that matches your programming language. 
- container image compatiable with the Open Container Initiative (OCI) specfication. The OS and Lambda runtime must also be included

### Layer
.zip file archieve that can contain additional code or other content. Main purpose is to reduce the uploaded deployment achieves sizes and speed up the code deployments. It makes the process of libraries packaging and other dependencies for the Lambda functions easier. A layer can contain libraries, custom runtime, data, or configuration files. Each Lambda function can have max five layers and count towards the standard Lambda deployment size quotas. 

Layers are .zip file achrieve specific and not part of container images. For the latter, you package your preferred runtime, libraries, and other dependencies into the container image when you build the image.

When a layer is included in the Lambda function, the contents are extracted to the */opt* directory of the execution environment. 

Layers are by default private to the user's AWS account. It can be shared across other accounts or public. If a  function uses a layer that a different account published, that layer version in that function persists after it has been deleted from the other account, or after its permission to access the layer is revoked. However, new functions or updated functions can't use the deleted layer.

### Extension
Augments a function by allowing integration of the function into preferred monitoring and governance tools. There are already existing internal AWS Lambda partners or create your own external Lambda extension.

Internal extensions run in the runtime process and shares the same lifecycle as the runtime. External extensions run in a separate process in the execution environment. External extensions are initialized before the function is invoked. It runs in parallel with the function's runtime and continues even after the function invocation has finished. 

### Concurrency
Number of requests the function is processing at any given time. As mentioned before, multiple instances of the function can run asynchronously. Concurrency is subject to quotas at the AWS Region level. Each individual functions can be configured to limit or enable a specific rate of concurrency.

### Version
A version is an immutable snapshot of a function's code and configuration, with a numeric value. For example, *my-function:1*. 

### Alias
An alias is a pointer to a version. Alias can be updated to map to a different version, or split traffic between two versions. For example, *my-function:BLUE*.

### Qualifer
When a function is invoked or viewed, a qualifier can be included to specify the version or alias. 

### Destination
AWS resource where the AWS Lambda can send events from an asynchronous invocation. You can set destinations for events when the process is a success or a failure. 

## Lambda features

- Concurrency and scaling controls
- Functions defined as container images
- Code signing - enabling this makes Lambda check that the package is signed by AWS Signer before deployment
- Use Lambda extensions for easier integration of Lambda function with other monitoring tools
- Function blueprints - provides sample code and function configurations for Node.js and Python runtimes with other AWS services or third party applications. 
- Database proxy that manages pool of database connections and relays queries from a function
- Can mount Amazon Elastic File System (EFS) to a local directory to access and modify shared resources

## Related services

- API Gateway for web APIs that route HTTP requests to Lambda functions
- Services that generate a queue or data stream, Lambda can poll from them and invoke the function to process the received data
- AWS S3 Events that invoke a Lambda function to process S3 objects
- Process AWS SQS messages or AWS SNS notifications
- AWS Step Functions to connect multiple Lambda functions together into serverless workflows. Known as State Machines

## Lambda can be accessed via

- AWS Management Console
- AWS Command Line Interface
- AWS SDKs
- AWS CloudFormation
- AWS Serverless Application Model 

## Prerequisites

- AWS account
- AWS CLI
- AWS SAM
- AWS SAM CLI
- Tools for container images
- Code authoring tools

## Supported languages and tools
As of 2022-09-07, these are the supported langauges in Lambda. To see the tools that can author each language, checkout the AWS Lambda documentation.

- Node.js    
- Java       
- C#        
- Python     
- Ruby       
- Go         
- PowerShell

## Lambda with AWS SQS
Amazon SQS allows offloading tasks from your system by sending it to a queue and processing them *asynchronously*. 

A lambda function can be used to process the messages in this queue. Lamda's Event Source Mappings support standard queues and FIFO queues. 

Lambda polls the queue and invokes the Lambda function *synchronously* with an event that contains multiple queue messages. Lambda reads messages in batches and invokes your function once for each batch (batch request). When your function successfully processes a batch, Lambda deletes its messages from the queue. 

Each message is a JSON string, with a batch being an array and containing multiple messages. "Records" is the key for the batch value.

Below is an example of SQS message event from a *standard queue*

{
    "Records": [
        {
            "messageId": "059f36b4-87a3-44ab-83d2-661975830a7d",
            "receiptHandle": "AQEBwJnKyrHigUMZj6rYigCgxlaS3SLy0a...",
            "body": "Test message.",
            "attributes": {
                "ApproximateReceiveCount": "1",
                "SentTimestamp": "1545082649183",
                "SenderId": "AIDAIENQZJOLO23YVJ4VO",
                "ApproximateFirstReceiveTimestamp": "1545082649185"
            },
            "messageAttributes": {},
            "md5OfBody": "e4e68fb7bd0e697a0ae8f1bb342846b3",
            "eventSource": "aws:sqs",
            "eventSourceARN": "arn:aws:sqs:us-east-2:123456789012:my-queue",
            "awsRegion": "us-east-2"
        },
        {
            "messageId": "2e1424d4-f796-459a-8184-9c92662be6da",
            "receiptHandle": "AQEBzWwaftRI0KuVm4tP+/7q1rGgNqicHq...",
            "body": "Test message.",
            "attributes": {
                "ApproximateReceiveCount": "1",
                "SentTimestamp": "1545082650636",
                "SenderId": "AIDAIENQZJOLO23YVJ4VO",
                "ApproximateFirstReceiveTimestamp": "1545082650649"
            },
            "messageAttributes": {},
            "md5OfBody": "e4e68fb7bd0e697a0ae8f1bb342846b3",
            "eventSource": "aws:sqs",
            "eventSourceARN": "arn:aws:sqs:us-east-2:123456789012:my-queue",
            "awsRegion": "us-east-2"
        }
    ]
}

By default, Lambda polls up to 10 messages in your queue at once and sends that batch to your function. To avoid invoking the function with a small number of records, you can tell the event source to buffer records for up to 5 minutes by configuring a batch window. Before invoking the function, Lambda continues to poll messages from the SQS standard queue one of hte following occurs:

- batch window expires
- the invocation payload size quota is reached
- the configured maximum batch size is reached

For FIFO queues, records contain additional attributes that are related to deduplication and sequencing.

Example Amazon SQS message event (FIFO queue):

{
    "Records": [
        {
            "messageId": "11d6ee51-4cc7-4302-9e22-7cd8afdaadf5",
            "receiptHandle": "AQEBBX8nesZEXmkhsmZeyIE8iQAMig7qw...",
            "body": "Test message.",
            "attributes": {
                "ApproximateReceiveCount": "1",
                "SentTimestamp": "1573251510774",
                "SequenceNumber": "18849496460467696128",
                "MessageGroupId": "1",
                "SenderId": "AIDAIO23YVJENQZJOL4VO",
                "MessageDeduplicationId": "1",
                "ApproximateFirstReceiveTimestamp": "1573251510774"
            },
            "messageAttributes": {},
            "md5OfBody": "e4e68fb7bd0e697a0ae8f1bb342846b3",
            "eventSource": "aws:sqs",
            "eventSourceARN": "arn:aws:sqs:us-east-2:123456789012:fifo.fifo",
            "awsRegion": "us-east-2"
        }
    ]
}

When Lambda reads a batch, the messages stay in the queue but are hidden for the length of the queue's visibility timeout. If your function successfully processes the batch, Lambda deletes the messages from the queue. By default, if your function encounters an error while processing a batch, all messages in that batch become visible in the queue again. For this reason, your function code must be able to process the same message multiple times without unintended side effects. You can modify this reprocessing behavior by including batch item failures in your function response.


## SQS Standard queue vs FIFO queue
By definition both are queues but there are some differences.

Standard queues:

- *best-effort ordering*: ensures that messages are generally delivered in the same order as they are sent.
- more than one copy of a message might be delivered out of order
- guarantee that a message is delivered at least once and duplicates can be introduced into the queue.
- allow nearly-unlimited number of transactions per second
- available in all the regions.
- supported by all AWS services.

FIFO queues: 
- first-in-first-out delivery: the order in which messages are sent and received is strictly preserved
- exactly-once processing
- message is delivered exactly once and remains available until a consumer processes and deletes it
- duplicates are not introduced into the queue.
- FIFO queues aren’t currently compatible with the SQS Buffered Asynchronous Client, where messages are buffered at client side and send as a single request to the SQS queue to reduce cost.
- available in limited regions only
- not supported by all AWS services