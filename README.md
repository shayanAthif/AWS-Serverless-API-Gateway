# Serverless API Gateway

## Overview  
We are creating a serverless API for managing database records using **AWS Lambda**, **API Gateway**, and **DynamoDB**. This cloud-based system allows users to perform:  
- **Create** new database entries  
- **Read** existing records  
- **Update** data  
- **List** all entries  

---

## Key Features  
- **Serverless architecture** with automatic scaling  
- No server management required  
- Minimal Python code leveraging cloud services  
- Transforms complex infrastructure into user-friendly workflows  

---

## Project Architecture  
![Project Architecture Diagram](https://github.com/user-attachments/assets/fea17bdb-98b1-4bd5-9358-336231e158a0)  

---

## Key Technologies Used  
- **AWS Lambda**: Smart functions for API logic.  
- **DynamoDB**: NoSQL database for storage.  
- **API Gateway**: Web interface for API access.  
- **Python**: Programming language for Lambda functions.  

---

## Implementation Roadmap  
### Key Components  
1. **Security Permissions (IAM Role)**  
   - Define roles/policies for secure AWS access.  
2. **Lambda Functions**  
   - Develop CRUD operations.  
3. **DynamoDB Tables**  
   - Configure schemas and scaling.  
4. **API Gateway Endpoints**  
   - Create RESTful API interfaces.  

---

## References  
This project was developed with reference to [saha-rajdeep/serverless-lab](https://github.com/saha-rajdeep/serverless-lab.git), which demonstrates AWS serverless architecture patterns.  

---

## Next Step  
➡️ [Setup IAM Roles](iam-roles-setup.md)  
*(Click to proceed to security configuration)*  
