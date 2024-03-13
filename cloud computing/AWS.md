# AWS

EC2: Elastic Compute Cloud

#### 1. Write the code snippet to extract the public IP address and the instanceID once you submit the request to create a VM and you get the result. Your code should address the asynchronous aspect of the request you might have submitted to request a VM instance.
```
import boto3
import time

# Initialize AWS client
ec2 = boto3.client('ec2')

# Submit request to create VM
response = ec2.run_instances(
    ImageId='ami-123456',  # Specify your AMI ID
    InstanceType='t2.micro',
    MinCount=1,
    MaxCount=1
)

# Extract instance ID
instance_id = response['Instances'][0]['InstanceId']

# Function to get instance public IP and status
def get_instance_info(instance_id):
    response = ec2.describe_instances(InstanceIds=[instance_id])
    instance = response['Reservations'][0]['Instances'][0]
    public_ip = instance.get('PublicIpAddress', 'Not assigned yet')
    state = instance['State']['Name']
    return public_ip, state

# Polling loop to wait for the instance to be running
while True:
    public_ip, state = get_instance_info(instance_id)
    if state == 'running':
        break
    else:
        print("Instance is still in state:", state)
        time.sleep(10)  # Wait for 10 seconds before polling again

print("Instance is now running with Public IP:", public_ip)
print("Instance ID:", instance_id)
```

#### 2. You want to create a backup service using AWS cloud to backup files from your local drive. Describe how you would design this and the key steps required for this. Add any code fragments (i.e., command line etc from CLI) to illustrate it.

Designing a backup service using AWS cloud to backup files from a local drive involves several key steps:

Choose AWS Services: Decide which AWS services to use for storage and backup. Commonly used services include Amazon S3 for storage and AWS Backup for managing backups.

Set up AWS Credentials: Ensure you have AWS credentials configured on your local machine to interact with AWS services programmatically.

Create an S3 Bucket: Create an S3 bucket where you will store your backup files. You can do this via the AWS Management Console or AWS CLI:

```
aws s3 mb s3://your-bucket-name
```
Write Backup Script: Write a script that will backup files from your local drive to the S3 bucket.
```
aws s3 sync /path/to/local/files s3://your-bucket-name
```