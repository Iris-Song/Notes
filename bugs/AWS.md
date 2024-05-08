# AWS
## Lambda
+ CORS
    
    In API Gateway, enable CORS

    at the end of Lambda return, add headers
  ```
  def lambda_handler(event, context):
    // ...
    return {
        'statusCode': 200,
        "headers": { 
            "Content-Type": "application/json",
            'Access-Control-Allow-Origin': '*'
        },
        'body': json.dumps(json_object)
    }
  ```

## EKS
  + nodegroup Architecture
    
    be the same with your server!
  + [tutorial](
    https://docs.aws.amazon.com/eks/latest/userguide/getting-started-console.html#eks-launch-workers)