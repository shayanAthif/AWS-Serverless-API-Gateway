![DynamoDB Architecture](https://github.com/user-attachments/assets/d7554f6b-553b-4b65-aaf1-b1acdd879f4b)    
## ❓ What is DynamoDB?  
Amazon DynamoDB is a **fully managed NoSQL database service** that:  
- 🚀 Delivers single-digit millisecond performance at any scale  
- 🔄 Automatically scales throughput capacity  
- 🔒 Provides built-in security and backup features  

---

## ❓ Why is DynamoDB Important?  
- **Serverless Architecture**: No server management required  
- **High Availability**: Automatic multi-AZ replication  
- **Cost Effective**: Pay-per-request pricing model  
- **AWS Integration**: Native compatibility with Lambda and API Gateway  

---

## ❓ Where is DynamoDB Used in This Project?  
- **Data Storage**: Persistent storage for API records  
- **CRUD Operations**: Supports Create/Read/Update/Delete actions from Lambda  
- **Scalability**: Automatically scales with API traffic  


---

## DynamoDB Table Setup

### Step 1: Create New Table
1. Navigate to **DynamoDB Service**  
2. Select **Tables** in left navigation pane  
3. Click **Create Table**  

![Create Table Interface](https://github.com/user-attachments/assets/eb05880f-7863-4ce8-a537-b7a185f62c70)  

---

### Step 2: Configure Table Settings
- **Table Name**: `lambda-apigateway`  
- **Partition Key**:  
  - **Name**: `id`  
  - **Type**: `String`  
- Keep all other settings as default  

![Table Configuration](https://github.com/user-attachments/assets/7c1e3a36-4716-4fde-93a0-432d9ccfe572)  

---

### ❓ What is NoSQL?  
NoSQL ("Not Only SQL") databases:  
- 🗄️ **Store flexible data formats** (key-value, document, etc.) instead of rigid tables  
- ⚡ **Optimize for scalability/speed** over complex queries  
- 🚫 **No fixed schema** – adapt to changing data needs  

---

### ❓ Why Use NoSQL (DynamoDB) Here?  
1. **Serverless Scalability**  
   - Automatically scales with API traffic (matches Lambda/API Gateway behavior).  
2. **Low Latency**
   - Single-digit millisecond response times for CRUD operations.

---

## Next Step: API Gateway Configuration  
With the database table ready, proceed to set up the API interface.  

➡️ **[Create API Gateway](api-gateway-setup.md)**  
*(Click to configure the API endpoints)*  
