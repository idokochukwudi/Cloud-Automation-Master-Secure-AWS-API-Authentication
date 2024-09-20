# Cloud-Automation-Master-Secure-AWS-API-Authentication
## Set Up Secure Authentication to AWS API
In this mini project, the goal is to set up secure authentication for an AWS API. The authentication is essential for a script that will interact with AWS services like EC2 and S3. Below are the steps to securely set up IAM resources and programmatic access for automation tasks.

**STEP 1: Create an IAM Role**
- Navigate to the IAM Dashboard in the AWS Console.
- Click Roles → Create Role.
![](./img/1.%20Create%20an%20IAM%20Role/1.click-roles-create-role.png)
- Select AWS Service as the trusted entity type and choose EC2 or S3 for the use case (depending on your script’s target service).
![](./img/1.%20Create%20an%20IAM%20Role/2.trusted-entity-use-case.png)
- Click Next and assign relevant permissions (EC2, S3 access).
![](./img/1.%20Create%20an%20IAM%20Role/3.Click-Next.png)
![](./img/1.%20Create%20an%20IAM%20Role/4a.search-AmazonEC2FullAccess..png)
![](./img/1.%20Create%20an%20IAM%20Role/4b.search-AmazonS3FullAccess-and-click-next.png)
- Name the role (e.g., automation_role) and finalize by creating the role.
![](./img/1.%20Create%20an%20IAM%20Role/5.role-name.png)
- Click Create role
![](./img/1.%20Create%20an%20IAM%20Role/6.click-create-role.png)

**STEP 2: Create an IAM Policy**
- Go to Policies in the IAM Dashboard.
- Click Create Policy.
![](./img/2.%20Create%20an%20IAM%20Policy/1.policies-create-policy.png)
- Choose JSON and input a policy that provides full access to both EC2 and S3, such as:
![](./img/2.%20Create%20an%20IAM%20Policy/2.choose-json-provide-policy.png)
- Click Next
![](./img/2.%20Create%20an%20IAM%20Policy/3.click-Next.png)
- Review the policy and name it (e.g., AutomationFullAccessPolicy), then create the policy.
![](./img/2.%20Create%20an%20IAM%20Policy/4.policy-name-and-create-policy.png)

**STEP 3: Create an IAM User**
- From the IAM dashboard, click on Users → Create user.
![](./img/3.%20Create%20an%20IAM%20User/1.users-create-user.png)
- Enter a user name like automation_user.
![](./img/3.%20Create%20an%20IAM%20User/2.user-name-Next.png)
- Select Programmatic access to enable API/CLI access.
![](./img/3.%20Create%20an%20IAM%20User/3.user-name-programmatic-access-next.png)
- Attach permissions directly to the user (you'll link to the policy and role in later steps).
![](./img/3.%20Create%20an%20IAM%20User/4.attach-ec2-and-s3-permissions.png)
- Review and Click Create
![](./img/3.%20Create%20an%20IAM%20User/5.Review-and-click-create.png)
- Download and save your console sign in details
![](./img/3.%20Create%20an%20IAM%20User/6.download-csv-file.png)

**STEP 4: Assign the User to the IAM Role**
- Select the automation_user you just created.
- Go to the Permissions tab.
- Under Add Permissions, click Attach policies → Attach existing policies directly.
![](./img/4.%20Assign%20the%20User%20to%20the%20IAM%20Role/1.select-user-permissions-add-permissions.png)
- Select the AutomationFullAccessPolicy created earlier and attach it to the user.
![](./img/4.%20Assign%20the%20User%20to%20the%20IAM%20Role/2.add-AutomationFullAccessPolicy-Next.png)
![](./img/4.%20Assign%20the%20User%20to%20the%20IAM%20Role/3.click-add-permission.png)

**STEP 5: Generate Programmatic Access Credentials**
- In the Security Credentials tab for automation_user, click on Create Access Key.
![](./img/5.%20Generate%20Programmatic%20Access%20Credentials/1.security-group-create-access-key.png)
- Select Command Line Interface (CLI), Check to confirm and then Click Next
![](./img/5.%20Generate%20Programmatic%20Access%20Credentials/2.select-CLI-click-Next.png)
- Provide Description tag value and click Create access key
![](./img/5.%20Generate%20Programmatic%20Access%20Credentials/3.tag-value-create.png)
-  Download and save the access key in a secured location and click Done
![](./img/5.%20Generate%20Programmatic%20Access%20Credentials/4.download-click-done.png)

**Final Steps: Authenticating the Script**
- Use the generated credentials to configure AWS CLI on your local machine:
- Input the Access Key ID and Secret Access Key when prompted, along with the default region and output format.
![](./img/6.%20Authenticating%20the%20Script/1.configure-AWS-CLI-on-local-machine.png)
- EXAMPLE: Command to list all the available AWS regions that you can use with the EC2 service.
![](./img/6.%20Authenticating%20the%20Script/2.aws-regions.png)

## Conclusion from the Project: Cloud-Automation-Master-Secure-AWS-API-Authentication
This project successfully sets up a secure authentication mechanism for AWS APIs, enabling programmatic interaction with AWS services such as EC2 and S3. The primary goal is to establish secure access for automation tasks using IAM roles, policies, and users.

**Key Takeaways:**

Structured IAM Configuration:

The project demonstrates a step-by-step approach to configuring IAM roles, policies, and users. This structured configuration ensures that only the necessary permissions are granted, following the principle of least privilege.

**Separation of Roles and Policies:**
By creating distinct IAM roles and policies for different use cases (like EC2 and S3), the project enforces clear boundaries and responsibilities. This separation minimizes the risk of misuse or accidental changes to AWS resources.

**Programmatic Access Enablement:**
The project provides detailed instructions on setting up programmatic access credentials, such as Access Key ID and Secret Access Key, necessary for scripts to interact with AWS services securely. This is crucial for automating tasks and integrating AWS operations into CI/CD pipelines or other automation frameworks.

**Security Best Practices:**
The project follows best practices for securing AWS resources, such as using roles over users where possible, downloading and storing credentials securely, and not hardcoding sensitive information in scripts. It also recommends configuring the AWS CLI with the credentials for secure interaction.

**Step-by-Step Documentation:**
The detailed steps and screenshots make the project easy to follow, even for users with limited AWS experience. The visual aids help in verifying that each step is correctly completed, reducing the chances of misconfiguration.

**Practical Application:**
The project’s outcome provides a practical setup that can be immediately used for automating AWS interactions. The example script for listing AWS regions demonstrates how to use the configured authentication programmatically.


Overall, this project is a comprehensive guide for anyone looking to securely automate interactions with AWS services. It emphasizes secure practices, proper IAM configuration, and practical usage, making it a valuable resource for cloud automation tasks.