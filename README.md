# Lab : IAM User and Group Management

## Objective
To create IAM users and groups, attach policies, and validate access control using the Principle of Least Privilege.

---

## Steps

### Step 1: IAM Console Access
- Navigated to the IAM service via AWS Console.
  
![aws-iam-landing-page](https://github.com/user-attachments/assets/c34823c5-34da-40f0-98c6-29854c4a7f1d)


### Step 2: Created Group `S3Admins`
- Attached policy: `AmazonS3FullAccess`
  
![aws-iam-user-group-creation](https://github.com/user-attachments/assets/bbe9be45-717c-4eb6-870b-c3924bc551c6)



### Step 3: Created User `test_user_1`

![creating-iam-user-specifying-details](https://github.com/user-attachments/assets/f640cc3c-727e-459f-bbef-732c5477a316)

- Granted:
  - Programmatic access
  - AWS Console access
- Assigned to group `S3Admins`


![adding-user-to-group](https://github.com/user-attachments/assets/331be36b-83bf-4ee5-ac4b-e1431a85e01f)

![reviewing-user-details](https://github.com/user-attachments/assets/108f0cf4-1383-450d-952a-db4056cd61b9)



### Step 4: Verified Access
- Logged in as `test_user_1`

![logged-in-as-test_user_1](https://github.com/user-attachments/assets/f1f563e3-6213-440f-9a69-64ead93178c7)

  
- Access to S3: ✅ Successful

![s3-successfully-accessed](https://github.com/user-attachments/assets/291603da-9b8f-43ee-9ace-570de9ea9b84)

- Access to EC2: ❌ Denied
  
![verifying-permission-boundaries-for-test_user_1](https://github.com/user-attachments/assets/31adc82a-5e75-46ee-bcef-19e5bdb32550)


### Step 5: Created User `test_user_2` With No Permissions
- No group or policy assigned

![creating-another-with-no-permissions](https://github.com/user-attachments/assets/cc6b9aa7-7aae-42b7-92b1-361a1076e026)

- Access to all services: ❌ Denied
  
![access-denied-for-test_user_2-no-permissions](https://github.com/user-attachments/assets/3cea2a5a-9458-420d-9ded-5c4f8a553947)

---

## ✅ Expected vs Actual Behavior

| Test Case         | Expected Result          | Actual Result           |
|------------------|--------------------------|-------------------------|
| `test_user_1` S3 | Access allowed           | Access allowed ✅       |
| `test_user_1` EC2| Access denied            | Access denied ✅        |
| `test_user_2` S3 | Access denied everywhere | Access denied ✅        |

---

## 🔒 Reflection: Principle of Least Privilege

This lab illustrates how IAM allows fine-grained access control. By assigning only the necessary permissions to `test_user_1` (S3-only), and none to `test_user_2`, we ensured users only had the access they required and nothing more — a core principle of cloud security known as **Least Privilege**.

---
