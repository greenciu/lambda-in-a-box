# Running AWS Lambda locally

A sample project & instructions for running an AWS Lambda implementation locally.

## Prerequisites

## Build

````
mvn clean install -Pdocker
````

## Run

````
docker-compose up
Creating network "lambda-in-a-box_default" with the default driver
Creating lambda-in-a-box_function_1 ... done
Attaching to lambda-in-a-box_function_1
function_1  | 26 Apr 2022 15:39:39,519 [INFO] (rapid) exec '/var/runtime/bootstrap' (cwd=/var/task, handler=)
function_1  | 26 Apr 2022 15:39:42,866 [INFO] (rapid) extensionsDisabledByLayer(/opt/disable-extensions-jwigqn8j) -> stat /opt/disable-extensions-jwigqn8j: no such file or directory
function_1  | 26 Apr 2022 15:39:42,866 [WARNING] (rapid) Cannot list external agents error=open /opt/extensions: no such file or directory
function_1  | START RequestId: e59973d2-73e9-41d3-a9d3-fb46f437c39d Version: $LATEST
function_1  | context: {
function_1  |   "memoryLimit": 3008,
function_1  |   "awsRequestId": "e59973d2-73e9-41d3-a9d3-fb46f437c39d",
function_1  |   "logGroupName": "/aws/lambda/Functions",
function_1  |   "logStreamName": "$LATEST",
function_1  |   "functionName": "test_function",
function_1  |   "functionVersion": "$LATEST",
function_1  |   "invokedFunctionArn": "arn:aws:lambda:us-east-1:012345678912:function:test_function",
function_1  |   "deadlineTimeInMs": 1650987883042,
function_1  |   "logger": {}
function_1  | }END RequestId: e59973d2-73e9-41d3-a9d3-fb46f437c39d
function_1  | REPORT RequestId: e59973d2-73e9-41d3-a9d3-fb46f437c39d	Init Duration: 0.37 ms	Duration: 185.53 ms	Billed Duration: 186 ms	Memory Size: 3008 MB	Max Memory Used: 3008 MB
````

## Test

````
curl -iS -X POST \
    "http://localhost:8080/2015-03-31/functions/function/invocations" \
    -d'{"payload":"hello"}'
    
HTTP/1.1 200 OK
Date: Tue, 26 Apr 2022 15:39:43 GMT
Content-Length: 8
Content-Type: text/plain; charset=utf-8

"200 OK"
````

> Note the date in the path `/2015-03-31/` is the AWS Lambda API version, see [answer](https://stackoverflow.com/questions/68375675/aws-lambda-container-images-invocation).
