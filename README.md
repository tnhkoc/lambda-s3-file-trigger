# 📦 Lambda S3 File Trigger

This AWS Lambda function is triggered automatically whenever a file is uploaded to a specified S3 bucket. The function reads the event metadata and logs the filename using CloudWatch Logs.

## 🧰 Services Used

- AWS Lambda
- Amazon S3
- Amazon CloudWatch Logs
- IAM Role (for Lambda execution)

## 🚀 How It Works

1. An S3 bucket is created.
2. A Lambda function (`S3UploadLogger`) is created with a Python runtime.
3. A trigger is set up so the function is invoked on every file upload (`s3:ObjectCreated:*`).
4. The Lambda function reads the uploaded file's name from the event and logs it.

## 🔧 Setup Steps

- Create an S3 bucket
- Create a Lambda function with basic execution role
- Connect the S3 trigger to the function
- Upload any file to test

## 📷 Screenshots

Screenshots of configuration, trigger setup, and logs should be added here.

## ✅ Sample Output

