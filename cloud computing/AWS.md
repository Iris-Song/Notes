# AWS

EC2: Elastic Compute Cloud

Amazon Cognito: for user authentication

Amazon Personalize: generate personalized recommendation

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

#### What is the use of Secondary Indexes in DynamoDB tables? List and explain the different types of secondary indexes available in AWS DynamoDB.
**Global secondary index** — An index with a partition key and a sort key that can be different from those on the base table. A global secondary index is considered "global" because queries on the index can span all of the data in the base table, across all partitions. A global secondary index is stored in its own partition space away from the base table and scales separately from the base table.

**Local secondary index** — An index that has the same partition key as the base table, but a different sort key. A local secondary index is "local" in the sense that every partition of a local secondary index is scoped to a base table partition that has the same partition key value.

3. You will enhance the system and architecture of the Assignment 1 with these additional features using AWS. Following are the additional features you need to support:
    1. You need to support user authentication. Each user will have their own profile - you may assume whatever information you want to keep in the profile.
    2. When the user logs in, this should recommend a list of restaurants based on past usage and other factors such as what their friends are sharing about their restaurant choices.
    3. You need to have support for a Friends’ List - you could assume that a user will have a set of friends who are using this App. You need to support what the user’s friends are recommending with their reviews.

You need to state the details of the following to support these enhancements:
    1. Extended architecture on top of the architecture for Assignment 1.
    2. Additional data models you would need.
    3. List of APIs and Lambda functions to support the above.
    4. E2e interaction of components for illustrating how your proposed recommendation works.
    5. E2e interaction of components for illustrating how your friends’ recommendations surfaced on the user's app.
Your extended system should scale, handle failures, and should utilize appropriate data stores as needed.
### Answer
To enhance the system architecture for Assignment 1 with the additional features using AWS, we'll need to design an extended architecture that supports user authentication, user profiles, restaurant recommendations based on past usage and friends' recommendations. Here's a breakdown of the components and features required:

1. **Extended Architecture:**

   - **Authentication Service**: Utilize AWS Cognito for user authentication. Cognito will handle user sign-up, sign-in, and user management.
   
   - **User Profile Service**: Store user profiles in Amazon DynamoDB, allowing users to store information such as name, email, preferences, and social connections.
   
   - **Restaurant Recommendation Service**: Use Amazon Personalize to generate restaurant recommendations based on past user interactions and social factors such as friends' recommendations.
   
   - **Friends' List Service**: Store friends' lists in DynamoDB, enabling users to connect with friends and view their recommendations.
   
   - **API Gateway**: Expose APIs for user authentication, profile management, restaurant recommendations, and friends' recommendations.
   
   - **Lambda Functions**: Implement business logic for each service using AWS Lambda functions, ensuring scalability and fault tolerance.
   
   - **DynamoDB**: Use DynamoDB as the primary data store for user profiles, friends' lists, and other application data.
   
   - **S3**: Store static assets such as images and files related to user profiles and restaurant data.

2. **Additional Data Models:**

   - **User Profile**: Contains information such as user ID, name, email, preferences, and friends list.
   
   - **Friends List**: Stores the relationships between users and their friends.
   
   - **Restaurant Recommendations**: Stores past usage data and social interactions to generate personalized recommendations.

3. **List of APIs and Lambda Functions:**

   - **APIs**:
     - User authentication (Sign-up, Sign-in)
     - User profile management (Create, Update, Delete)
     - Restaurant recommendations
     - Friends' recommendations
     
   - **Lambda Functions**:
     - AuthenticateUser
     - CreateProfile
     - UpdateProfile
     - GenerateRecommendations
     - GetFriendsRecommendations

4. **E2E Interaction for Recommendation:**

   - The user logs in to the application, triggering the AuthenticateUser Lambda function.
   - Upon successful authentication, the user's profile is retrieved from DynamoDB using the GetProfile Lambda function.
   - The GenerateRecommendations Lambda function is invoked, which calls Amazon Personalize to generate personalized restaurant recommendations based on the user's past interactions and social factors.
   - The recommended restaurants are returned to the user through the API Gateway and displayed in the application.

5. **E2E Interaction for Friends' Recommendations:**

   - The user views their friends' list in the application, triggering the GetFriendsList Lambda function.
   - The Lambda function retrieves the user's friends' list from DynamoDB.
   - For each friend in the list, the GetFriendsRecommendations Lambda function is invoked.
   - This function retrieves the friend's recommendations from DynamoDB and returns them to the user.
   - The user sees their friends' recommendations alongside their own recommendations in the application.

By utilizing AWS services such as Cognito, DynamoDB, Personalize, API Gateway, and Lambda, we can build a scalable and fault-tolerant system that supports user authentication, user profiles, personalized recommendations, and friends' recommendations while ensuring efficient end-to-end interactions.