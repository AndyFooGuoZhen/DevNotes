### IAM
- Identitiy Access Management

### Principals
- Person or service requesting access (EX: user, application, roles)

### Policies
- Idnetity based (Principals, roles)
- Resource based (S3, dynamodb)
- All policies are in the form of an json object

### Creating a user / New User view
- Head to IAM in AWS console > Users > Create new user
- (Example credentials for SmallerAndy - pwd : TestUser123
- Sign in link for this user : https://149312211348.signin.aws.amazon.com/console
- You can then log in to the AWS console via a IAM user with the SmallerAndy username

### Granting permissions / Attaching policies
- Once logged in with SmallerAndy
- Notice that access to EC2 is limited and there are no S3 buckets found (when the admin user has 1)
- We are going to grant SmallerAndy read only access to S3 buckets
- To do so, we head back to the admin acc, head to IAM > Users > Add Permissions > Attach policies directly
- Select S3 read only access polcies (Clicking on the + icon shows the polciy in a json format)

### Identity vs Resource based policy
- Almost looks the same in structure
- Resource-based policy focuses on controlling and managing access to specific resources, such as files, databases, or applications.
- Identity-based policy focuses on managing and controlling access based on the user's identity and associated attributes.
- <img width="1018" alt="image" src="https://github.com/user-attachments/assets/1603eeef-aa19-4a8d-99df-759cf4d31f33">
- (Left), shows a resource based policy that ties to the IAM user of iamuser 1, restricting access to only the specified s3 bucket
- (right), identity based policy attached to SmallerUser on the actions it can perform on s3 buckets it has access to

