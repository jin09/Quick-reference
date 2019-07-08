# AWS

### Deploy Single Function AWSLambda

```console
serverless deploy  --verbose  function --f function_name --envornment_variables="value" 
```

## Invoke lambda from lambda

Before you attempt this, make sure that your lambda has access to control other lambdas.  
Give permissions to lambda through IAM.  

```python
import json
import os
from boto3 import client as boto3_client
from setting import log_exception


def dummy(event, context):
    print event
    return event


def handler(event, context):
    try:
        print event
        function_name = 'Attendance-Api-' + str(os.environ.get('stage')) + '-dummy'

        lambda_client = boto3_client('lambda', region_name="us-east-1")
        response = lambda_client.invoke(
            FunctionName=function_name,
            InvocationType='RequestResponse',
            Payload=json.dumps({'hello': 'test this func !!'})
        )

        string_response = response["Payload"].read().decode('utf-8')
        parsed_response = json.loads(string_response)

        print parsed_response
    except Exception as e:
        log_exception(e)
        return 'error occurred'

```
