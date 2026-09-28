# Thaura Task 01 – Postman API Testing

## Overview

This repository contains the Postman collection and environment template for Thaura Task 01 API testing.

The collection contains **63 test cases** organized by functional module.

## Project Structure

```text
Thaura_Task01_Postman/
│
├── postman/
│   ├── Thaura_Task01_API_Testing.postman_collection.json
│   └── Thaura_Task01_Environment.template.json
│
├── test-data/
│
└── README.md
```

## Requirements

* Postman
* Valid Thaura test account
* Test email access for OTP verification
* Valid API key where required

## Setup

### 1. Clone the Repository

```bash
git clone <REPOSITORY_URL>
cd Thaura_Task01_Postman
```

### 2. Import Postman Files

Open Postman and import:

```text
postman/Thaura_Task01_API_Testing.postman_collection.json
postman/Thaura_Task01_Environment.template.json
```

Postman supports importing exported collections and environments directly.

### 3. Configure Environment

Select:

```text
Thaura Task 01 Environment
```

Set the required variables:

| Variable           | Value                           |
| ------------------ | ------------------------------- |
| `base_url`         | `https://backend.thaura.ai`     |
| `email`            | Your test account email         |
| `otp`              | OTP received by email           |
| `api_key`          | Your valid API key              |
| `thaura_token`     | Generated during authentication |
| `old_thaura_token` | Used for logout validation      |

Do not commit real API keys, tokens, passwords, or OTP values to Git.

Environment variables can be updated by Postman scripts and reused by subsequent requests during a collection run.

## Authentication Flow

Run these requests in order:

```text
Q1_auth_request_otp
        ↓
Q2_auth_verify_otp
        ↓
Q3_auth_validate_session_before_logout
        ↓
Q4_auth_logout
        ↓
Q5_auth_validate_old_token_after_logout
```

For OTP verification:

1. Run `Q1_auth_request_otp`.
2. Check the test email inbox.
3. Copy the OTP.
4. Set the `otp` environment variable.
5. Run `Q2_auth_verify_otp`.

## Collection Structure

```text
01_Auth_Session
02_Chat_Completions_Validation
03_Boundary_Parameters_Authentication
04_Response_Usage_Chat_Edge_Cases
05_User_Profile_Account
06_Free_Tier_Quota
07_File_Upload_Data_Integrity
```

## Run Tests

In Postman:

```text
Collection
   ↓
Run
   ↓
Select Environment
   ↓
Run Collection / Required Folder
```

The Collection Runner can execute collection or folder requests in sequence with a selected environment.

## Test Result

After execution, review:

* Passed tests
* Failed tests
* HTTP status codes
* Response validation
* Error messages
* Required evidence/screenshots

## Security

Never commit:

```text
API keys
Authentication tokens
Passwords
OTP values
Private credentials
```

Use the environment template and keep real credentials only in your local Postman environment. Postman notes that shared/public environment values can expose sensitive information, so sensitive values should not be published.
