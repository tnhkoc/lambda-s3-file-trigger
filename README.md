# AWS Lambda – S3 Trigger Integration

This project demonstrates how to set up an AWS Lambda function that is automatically triggered whenever a new file is uploaded to a specific S3 bucket. The Lambda function extracts the uploaded file's name from the event and logs it to CloudWatch.

---

## 📌 Purpose

- Understand how AWS Lambda integrates with S3 events  
- Learn event-driven architecture basics using AWS native services  
- Practice IAM permissions and logging with CloudWatch  

---

## 🧰 Services Used

- **Amazon S3** – Object storage for file uploads  
- **AWS Lambda** – Event-driven compute service  
- **IAM** – Permissions for Lambda to access S3 and CloudWatch  
- **CloudWatch** – Logs to monitor Lambda execution  

---

## 📈 Architecture Overview

1. A file is uploaded to an S3 bucket  
2. This event triggers the Lambda function  
3. The function reads the filename from the event object  
4. The filename is logged to CloudWatch Logs  

---

## ⚙️ Setup Instructions

### 1. Create an S3 Bucket

- Go to the **S3 Console**
- Click **"Create Bucket"**
- Choose a name like `lambda-s3-trigger-demo`
- Keep **"Block all public access"** enabled

---

### 2. Create a Lambda Function

- Runtime: **Python 3.10**
- Permissions: Create a new role with **basic Lambda permissions**

Paste the following code into the Lambda function:

```python
import json

def lambda_handler(event, context):
    file_name = event['Records'][0]['s3']['object']['key']
    print(f"New file uploaded: {file_name}")
    return {
        'statusCode': 200,
        'body': json.dumps(f"Processed file: {file_name}")
    }
```

---

### 3. Add S3 as Trigger

- In the Lambda configuration, click **"Add trigger"**
- Select **Amazon S3**
- Choose the created bucket
- Event type: **PUT**
- Save the configuration

---

### 4. Test the Setup

- Upload a file to the S3 bucket (e.g. `test-file.txt`)
- Go to **CloudWatch Logs** via Lambda Monitoring tab
- You should see output like:

```
New file uploaded: test-file.txt
```

---

## 🖼️ Screenshots

All screenshots related to setup and test results are located in the `/screenshots` folder.

---

## 👤 Author

**Tunahan Koç**  
GitHub: [tnhkoc](https://github.com/tnhkoc)
