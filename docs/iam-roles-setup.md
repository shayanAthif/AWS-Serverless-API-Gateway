### ❓ **What is IAM?**  
IAM (**Identity and Access Management**) is an AWS service that controls **who or what** can access AWS resources (e.g., databases, APIs) and **what actions** they can perform.

---

### ❓ **What are IAM Roles?**  
IAM roles are **temporary permission sets** you assign to AWS services (like Lambda or EC2) instead of users. They:  
- 🔐 Have no passwords/keys.  
- ⏳ Grant time-limited access.  
- 🛡️ Follow the *principle of least privilege*.  

---

### ❓ **Why are they important?**  
- **Security**: Avoid hardcoding credentials in code.  
- **Scalability**: Simplify permissions for serverless architectures.  
- **Compliance**: Audit and restrict access easily.  

---

### ❓ **Where are we using IAM roles in this project?**  
In our serverless API setup:  
1. **Lambda to DynamoDB**:  
   - A role grants Lambda permissions to read/write to DynamoDB.  
2. **API Gateway to Lambda**:  
   - A role lets API Gateway invoke the Lambda function.  

## Implementation Example: Lambda-DynamoDB Access

```json
// Example Lambda-to-DynamoDB Role Policy
{
  "Action": ["dynamodb:GetItem", "dynamodb:PutItem"],
  "Resource": "arn:aws:dynamodb:ap-south-1:123456789012:table/MyTable"
}

```

---

### Before creating the IAM role, we’ll design a custom IAM policy to specify the exact permissions required for the role.

### ❓ **What is an IAM Policy?**  
An IAM policy is a **rulebook in JSON format** that defines:  
- ✅ **Allowed Actions**: What AWS services/APIs can be accessed (e.g., `dynamodb:PutItem`).  
- 🎯 **Resource Targeting**: Which specific resources these actions apply to (e.g., your DynamoDB table).  
- 🔒 **Security Boundaries**: Optional conditions like time restrictions or IP ranges.  

Policies are attached to IAM roles to grant permissions.

---

### ❓ **Why Create a Custom Policy?**  
While AWS provides pre-built policies (e.g., `AmazonDynamoDBFullAccess`), we create custom policies to:  
- 🛡️ **Enhance Security**: Follow the *least privilege principle* (only grant necessary permissions).  
- 🎯 **Precision Control**: Restrict access to **your specific DynamoDB table** instead of all tables.  

---
# AWS IAM Policy & Role Setup Guide

## Step 1: Create Custom IAM Policy

### 1. Access AWS Management Console
Navigate to the [AWS Management Console](https://aws.amazon.com/console/) and sign in.  
![AWS Console Dashboard](https://github.com/user-attachments/assets/aff40a16-741c-4e6b-8b19-e06f7cbd4daa)

---

### 2. Go to IAM > Policies
From the AWS services menu, select **IAM** > **Policies**.  
![IAM Policies Section](https://github.com/user-attachments/assets/5fae5c8d-4178-4b2e-9091-3086475adb18)

---

### 3. Create New Policy
Click **Create Policy** in the top-right corner.  
![Policy Creation Interface](https://github.com/user-attachments/assets/b13dd373-2c0b-42ad-9fcb-da3a32f71d3c)

---

### 4. Define Policy in JSON Editor
1. Select the **JSON** tab.  
2. Replace any existing content with:  
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DynamoDBAccess",
      "Effect": "Allow",
      "Action": [
        "dynamodb:DeleteItem",
        "dynamodb:GetItem",
        "dynamodb:PutItem",
        "dynamodb:Query",
        "dynamodb:Scan",
        "dynamodb:UpdateItem"
      ],
      "Resource": "*"
    },
    {
      "Sid": "CloudWatchAccess",
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:PutLogEvents"
      ],
      "Resource": "*"
    }
  ]
}
```

![image](https://github.com/user-attachments/assets/d4da2a7a-e48d-424a-a6c1-2e0837c3b008)  
---

### 5. Name and Create the Policy  
In **Step 2**, enter the following:  
- **Policy Name**: `lambda-API-gateway-policy`  
- Click **Create Policy**.  

![Policy Naming Screen](https://github.com/user-attachments/assets/d6e80b7c-37a8-43ca-b970-cade54d62914)  

---

### 6. Create a Custom IAM Role  
Navigate back to **IAM > Roles** and click **Create Role**.  
![Role Creation Interface](https://github.com/user-attachments/assets/76929b1a-800a-40f9-ba1d-1649f016eb75)  

---

### 7. Configure Trusted Entity (Step 1)  
- **Trusted Entity Type**: `AWS Service`  
- **Use Case**: `Lambda`  
- Click **Next**.  

![Trusted Entity Configuration](https://github.com/user-attachments/assets/868b15d4-ba89-4279-8cde-647db41704f9)  

---

### 8. Attach Permissions Policy (Step 2)  
- Under **Permissions Policies**, search for and select `lambda-apigateway-policy`.  
- Click **Next**.  

![Policy Attachment Interface](https://github.com/user-attachments/assets/5dbae540-a44d-46ea-a718-3da2e6a4c85e)  

---

### 9. Finalize Role Creation (Step 3)  
- **Role Name**: `lambda-API-gateway-role`  
- Click **Create Role**.  

![Role Naming Screen](https://github.com/user-attachments/assets/0e474d17-a769-4ac6-9154-a9455c4457c8)  

---

## Next Step  
➡️ **[Create Lambda Function](lambda.md)**  
*(Click here to proceed to Lambda setup)*  




