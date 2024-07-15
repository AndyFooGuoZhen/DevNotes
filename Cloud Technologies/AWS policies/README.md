Resource: https://www.youtube.com/watch?v=ExjW3HCFG1U&t=792s

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
- (Left), shows a resource based policy that ties to the IAM user of iamuser 1, restricting access to the specified s3 bucket
- (right), identity based policy attached to SmallerUser on the actions it can perform on s3 buckets it has access to

### Example usage of a resource based policy
- Goal: we want to restrict SmallerAndy to have access to other s3 buckets, except for the one specified in the resource based policy
- We head to the admin account, head to the s3 bucket we want to restrict access for SmallerAndy, head to permissions for buckets and paste our resource based json there and hit save
- <img width="432" alt="image" src="https://github.com/user-attachments/assets/ada9ad8f-5cd1-4070-8d76-4538cdbfe67a">
- On SmallerAndy's account, we have no access to the bucket specified in the Resource policy
- <img width="964" alt="image" src="https://github.com/user-attachments/assets/f6878ebd-6e17-49d8-83bc-d180f7f56991">

### Roles
- Access to resources is granted based on the user's role, rather than their individual identity
- head to IAM, roles, give the role a name, a service use case (EX: EC2) and the sets of permissions tied to this role
- More function centric than user groups

### User groups
- Collections of users that share common characteristics or requirements within an organization's access control system
- Head to IAM, user groups, Create group, add users, and attach policies. If you want to be specific you can also add inline policies here (something like resource based policy)
- EX: if you attach a read only access to s3 policy but you also want to allow users in this group to have write access to an s3 bucket called bucketA, you can add an inline policy for write access to bucket A

### Principles of least privilege
Resource: https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html
- Sometimes a user group policy may allow access to a particular resource but resource policy denies access for some users, how can we determine if the user has access to the resource?
- AWS applies the principles of least privilege, ensuring that each element only has the permissions necessary to function correctly
- Permissions and policy evaluation is evaluated with a hierachical order
- <img width="745" alt="image" src="https://github.com/user-attachments/assets/21fe2c2d-6a0e-4839-b6e8-73a715ca4814">

### Usage of roles
- Once a role is created, you can attach the role to a specific resource
- EX: using an EC2 example, you can attach the role simply by heading to EC2 instance, Actions > security > modify IAM role and attach the role you have created



