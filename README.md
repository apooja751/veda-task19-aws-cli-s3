# Task 19: Upload and Download Files Using AWS CLI

## Overview
This project demonstrates how to use the AWS Command Line Interface (AWS CLI) in AWS CloudShell to manage objects in Amazon S3.

## Objectives
- Verify AWS CLI installation and identity.
- List S3 buckets and inspect bucket contents.
- Create a local test file in CloudShell.
- Upload a file to Amazon S3.
- List and verify the uploaded object.
- Download the object and verify its contents.
- Delete the test object and confirm the bucket remains intact.

## Tools and Services
- Amazon Web Services (AWS)
- AWS CloudShell
- AWS CLI v2
- Amazon Simple Storage Service (Amazon S3)
- GitHub

## Environment
- AWS Region: Asia Pacific (Mumbai) — `ap-south-1`
- CLI Environment: AWS CloudShell
- Existing test bucket: `veda-task16-cloud-storage-pooja-2026`

## Practical Steps

### 1. Verify AWS CLI
```bash
aws --version
```

### 2. Verify AWS Identity
```bash
aws sts get-caller-identity
```

### 3. List S3 Buckets
```bash
aws s3 ls
```

### 4. Inspect the Existing Bucket
```bash
aws s3 ls s3://veda-task16-cloud-storage-pooja-2026/
```

### 5. Create a Test File
```bash
printf 'VEDA INTERNSHIP - TASK 19\nAWS CLI S3 Upload and Download Test\nDate: 19 October 2026\n' > task19-test.txt
cat task19-test.txt
```

### 6. Upload the File
```bash
aws s3 cp task19-test.txt s3://veda-task16-cloud-storage-pooja-2026/task19-test.txt
```

### 7. List the Uploaded Object
```bash
aws s3 ls s3://veda-task16-cloud-storage-pooja-2026/task19-test.txt
```

### 8. Download the File
```bash
aws s3 cp s3://veda-task16-cloud-storage-pooja-2026/task19-test.txt task19-downloaded.txt
```

### 9. Verify the Download
```bash
cat task19-downloaded.txt
```

The downloaded file contained the same text as the original test file.

### 10. Delete the Test Object
```bash
aws s3 rm s3://veda-task16-cloud-storage-pooja-2026/task19-test.txt
```

### 11. Verify Deletion and Bucket Contents
```bash
aws s3 ls s3://veda-task16-cloud-storage-pooja-2026/task19-test.txt
aws s3 ls s3://veda-task16-cloud-storage-pooja-2026/
```

The specific-object listing returned no file, and the final bucket listing showed that the original folders remained present.

## Screenshots
Screenshots documenting the CLI installation, identity verification, bucket listing, file creation, upload, download, verification, deletion, and final bucket check will be added to this repository.

## Security Best Practices
- Avoid using the AWS root identity for routine work.
- Prefer IAM roles or appropriately scoped IAM identities.
- Never commit access keys, secret keys, session tokens, or passwords.
- Grant only the permissions needed for the task.
- Verify the target bucket and object name before deleting data.

## Result
Successfully used AWS CLI in CloudShell to upload, list, download, verify, and delete a test object in Amazon S3.

## Conclusion
This practical demonstrated basic cloud storage management using command-line operations. It also reinforced the importance of verifying operations and protecting AWS credentials.
