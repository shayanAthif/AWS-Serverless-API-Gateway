
## 🚨 Critical Cleanup Steps 🚨  
**To avoid unexpected AWS charges, delete all resources after testing:**  

1. **DynamoDB Table**  
   - Go to **DynamoDB Console** → Tables → Select `lambda-apigateway` → **Delete Table**  

2. **Lambda Function**  
   - Go to **Lambda Console** → Functions → Select `LambdaOverHttps` → **Delete**  

3. **API Gateway**  
   - Go to **API Gateway Console** → APIs → Select `DynamoDBOperations` → **Actions** → **Delete API**  

---

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
