![API Gateway Architecture](https://github.com/user-attachments/assets/c89f4bc5-9103-4447-8dbd-c9356a6b4dfe)  
    


## ❓ What is API Gateway?  
Amazon API Gateway is a **fully managed service** that:  
- 🚀 Creates, publishes, and secures APIs at scale  
- 🔄 Acts as an entry point for backend services  
- ⚡ Enables RESTful API development and deployment  

---

## ❓ Why is API Gateway Important?  
- **Serverless Integration**: Seamlessly connects to AWS Lambda and DynamoDB  
- **Traffic Management**: Handles throttling, caching, and authorization  
- **Monitoring**: Provides detailed metrics via CloudWatch  
- **Version Control**: Supports multiple API stages (e.g., dev, prod)  

---

## ❓ Where is API Gateway Used in This Project?  
- **HTTP Endpoint**: Provides public URL for API access  
- **Request Routing**: Directs POST requests to Lambda function  
- **Security Layer**: First line of defense for API operations  


---

## API Gateway Setup

### Step 1: Create REST API
1. Navigate to **API Gateway Service**  
2. Under **REST API**, click **Build**  
![Create REST API](https://github.com/user-attachments/assets/b83bb1b6-f209-4189-8507-cb120af36a0f)  

---

### Step 2: Configure API Settings
- **API Name**: `DynamoDBOperations`  
- Keep all other settings as default  
- Click **Create API**  

---

### Step 3: Create Resource
1. In left navigation pane, select **Resources**  
2. Click **Create Resource**  
![Create Resource Interface](https://github.com/user-attachments/assets/4c071b5e-43b3-4e0d-adc4-197cfac0ebfd)  

---

### Step 4: Name Resource
- **Resource Name**: `DynamoDBManager`  
- Click **Create Resource**  
![Resource Naming](https://github.com/user-attachments/assets/1de31bc4-1417-45f4-b974-8bf917d2cf7b)  

---

### Step 5: Create POST Method
1. Under **Resources** > **DynamoDBManager**  
2. Click **Create Method**  
![Method Creation](https://github.com/user-attachments/assets/4a228991-8fea-4aa6-b1de-353963996e32)  

---

### Step 6: Configure Method Integration
- **Method Type**: `POST`  
- **Integration Type**: Lambda Function  
- **Lambda Function**: `LambdaOverHttps`  
- Enable **Use Lambda Proxy Integration**  
![Method Configuration](https://github.com/user-attachments/assets/3cf4c5e8-9dec-45c9-8f5a-aa32084b5d44)  

---

### Step 7: Deploy API
1. In top-right corner, click **Deploy API**  
2. Select **[New Stage]** for Deployment Stage  
![Deploy API](https://github.com/user-attachments/assets/24fd3595-a08e-4789-a9ac-1ae3be22675f)  

---

### Step 8: Configure Deployment Stage
- **Stage Name**: `Prod`  
- Click **Deploy**  

---
### Step 9: Access API Endpoint
1. Navigate to **Stages** > **Prod**  
2. Locate **Invoke URL** for API testing  
![Invoke URL](https://github.com/user-attachments/assets/2d7779b4-0c02-4e47-8a7e-5803363d088d)  

---

## 🚨 Critical Cleanup Steps 🚨  
**To avoid unexpected AWS charges, delete all resources after testing:**  

1. **DynamoDB Table**  
   - Go to **DynamoDB Console** → Tables → Select `lambda-apigateway` → **Delete Table**  

2. **Lambda Function**  
   - Go to **Lambda Console** → Functions → Select `LambdaOverHttps` → **Delete**  

3. **API Gateway**  
   - Go to **API Gateway Console** → APIs → Select `DynamoDBOperations` → **Actions** → **Delete API**  

![image](https://github.com/user-attachments/assets/61eced3e-4f4e-4157-9a94-6dfc76dba73a)

*Do not let this happen to you!*  

---

## 🎉 Serverless API Deployment Complete  
You've successfully created and tested a production-ready serverless architecture:  

- **Frontend**: `API Gateway` endpoint  
- **Logic Layer**: `Lambda` function (Python)  
- **Database**: `DynamoDB` NoSQL table  

---

➡️ **[Return to Project Overview](/README.md)**  
*(Click to revisit documentation or restart the process)*
