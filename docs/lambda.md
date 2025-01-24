![AWS Lambda Flow](https://github.com/user-attachments/assets/46333ed7-288f-493a-bfe9-ab99a920848e)  


### ❓ **What is AWS Lambda?**  
AWS Lambda is a **serverless computing service** that:  
- 🚀 Runs code without requiring you to provision or manage servers.  
- ⏱️ Executes functions in response to events (e.g., HTTP requests, database updates).  
- 💰 Charges only for the compute time consumed (pay-per-execution model).  

---

### ❓ **Why is Lambda Important?**  
- **No Server Management**: Focus on code, not infrastructure.  
- **Automatic Scaling**: Handles thousands of requests concurrently.  
- **Cost Efficiency**: No charges when code isn’t running.  
- **Integration**: Works seamlessly with AWS services (API Gateway, DynamoDB, S3).  

---

### ❓ **Where is Lambda Used in This Project?**  
In your serverless API architecture:  
1. **Request Handling**:  
   - Lambda processes HTTP requests from API Gateway (e.g., GET, POST).  
2. **Business Logic**:  
   - Executes CRUD operations (Create, Read, Update, Delete) on DynamoDB.  
3. **Scalability**:  
   - Automatically scales to handle user traffic spikes.  


---
# AWS Lambda Function Setup Guide

## Step 1: Create Lambda Function
1. Navigate to **AWS Lambda Service**
2. Click **Create Function**  
![Lambda Create Function](https://github.com/user-attachments/assets/f8a3c0c3-8781-4446-95fa-a5b3e5e68d4f)

---

## Step 2: Configure Basic Settings
- **Author from scratch**
- **Function name**: `LambdaOverHttps`
- **Runtime**: Python 3.9  
![Function Configuration](https://github.com/user-attachments/assets/75c90ca1-4adb-4145-a8f7-5164f6df9785)

---

## Step 3: Set Up Permissions
- Under **Permissions** > **Execution role**:
  - Select **Use an existing role**
  - Choose `lambda-API-gateway-role`  
![Role Selection](https://github.com/user-attachments/assets/d4963941-4311-4f97-8a4f-787a047d746b)

---

## Step 4: Implement Function Code
1. In the **Code** tab, replace default code with:
```python
from __future__ import print_function
import boto3
import json

print('Loading function')

def lambda_handler(event, context):
    operation = event['operation']
    
    if 'tableName' in event:
        dynamo = boto3.resource('dynamodb').Table(event['tableName'])
    
    operations = {
        'create': lambda x: dynamo.put_item(**x),
        'read': lambda x: dynamo.get_item(**x),
        'update': lambda x: dynamo.update_item(**x),
        'delete': lambda x: dynamo.delete_item(**x),
        'list': lambda x: dynamo.scan(**x),
        'echo': lambda x: x,
        'ping': lambda x: 'pong'
    }
    
    return operations[operation](event.get('payload')) if operation in operations \
        else ValueError(f'Unrecognized operation "{operation}"')
![image](https://github.com/user-attachments/assets/c6961876-737c-434b-986a-d1b6755a5c17)  

5 - Next to the Code tab, select the Test tab. We will be testing out our lambda function. 
    Now, Under Test, Click Create a New test event. Choose the event template as hello-world and the event name as echotest, paste the below JSON file and click save.  
```json
{
    "operation": "echo",
    "payload": {
        "somekey1": "somevalue1",
        "somekey2": "somevalue2"
    }
}
```
---

### 6. Select Test Event
1. Navigate back to the **Code** tab.  
2. In the bottom-left corner of the code editor, locate the **Test events** dropdown.  
3. Select the `echotest` event you created.  

![Test Event Selection](https://github.com/user-attachments/assets/a061ff0a-ada8-40af-8700-55cf09af9a2a)  

---

### 7. Deploy and Execute Test
1. Click **Deploy** to save your code changes.  
2. Click **Test** to run the Lambda function with your test event.  
3. Verify successful execution in the results panel:  

![image](https://github.com/user-attachments/assets/68d41ce6-baa0-4e0c-acb4-b420ac73ba27)

---

## Next Step: Database Setup  
With the Lambda function successfully tested, proceed to configure the DynamoDB database.  

➡️ **[Create DynamoDB Table](dynamodb-setup.md)**  
*(Click to configure the database for your serverless API)*  
