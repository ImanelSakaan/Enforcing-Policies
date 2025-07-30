# Enforcing-Policies
Enforcing Organizational Policies in the Cloud

## 🎥 Video Demo
[Watch the video demo](#) *(https://youtu.be/EBBPP0rfjlM)*

# MapleTech Policy Lab

## ✅ Azure Policy Lab – Cloud Security Engineer Tools
This lab provides **Azure Policy** tools that are essential for any cloud security engineer role.
> **Azure Policy** is a service in Microsoft Azure that helps manage and control what users can and cannot do in your Azure environment.


## 🎯 Objectives
- Restrict deployments to the Canada Central region.
- Enforce tagging with `ProjectName` tag.
- Block creation of Public IP addresses.
- Validate policy enforcement with real-world test cases.

## 📜 Policies Implemented
1. **Only-CanadaCentral**: Denies resources outside Canada Central.
2. **Require-ProjectName-Tag**: Denies resources without a `ProjectName` tag.
3. **Deny-Public-IP**: Blocks creation of public IP addresses.

## 🛡️ Part 1: Define the Guardrails (Create Custom Policies)

### 🔒 Policy 1: Region Lockdown
- **Name**: `Only-CanadaCentral`
- **Location**: Canada Central region only
- **Category**: Create new → `"MapleTech Governance"`

### 🏷️ Policy 2: Mandatory Tagging
- **Name**: `Require-ProjectName-Tag`

### 🌐 Policy 3: Block Public IPs
- **Name**: `Deny-Public-IP`

---

## 📦 Part 2: Group Policies into an Initiative

### 1. Create Policy Initiative
- **Name**: `MapleTech Secure Foundation`

### 2. Add Policies to Initiative
- Include:
  - `Only-CanadaCentral`
  - `Require-ProjectName-Tag`
  - `Deny-Public-IP`

---

## 🔗 Part 3: Assign the Initiative

### 1. Create a Test Resource Group
- **Name**: `rg-mapletech-test`
- **Region**: `Canada Central`
- **Tag**: `ProjectName: PolicyLabTest`

### 2. Assign the Initiative
- Navigate to: **Policy → Assignments**
- Click: **"Assign initiative"**
- **Scope**: Select your test resource group
- **Initiative Definition**: `MapleTech Secure Foundation`
- **Assignment Name**: `MapleTech-Compliance-Assignment`
- **Enforcement Mode**: `Default (Enabled)` – This ensures deny effects work
- Click **"Review + Create"** → **"Create"**

---

## 🧪 Part 4: Simulate Developer Activity (Test Cases)

### 🔴 Test Case 1: Deploy VM in East US (Should Fail)
- **Expected Result**: ❌ Deployment should fail due to **disallowed region**

### 🔴 Test Case 2: Deploy Storage Account without `ProjectName` tag (Should Fail)
- **Expected Result**: ❌ Deployment should fail due to **missing tag**

### 🔴 Test Case 3: Create Public IP (Should Fail)
- **Expected Result**: ❌ Creation should be **blocked by public IP policy**

### ✅ Test Case 4: Deploy VM in Canada Central with tag (Should Succeed)
- **Expected Result**: ✅ Deployment should **succeed**

---

## 🚀 Test Cases and Results

| Test Case | Description | Expected | Result |
|-----------|-------------|----------|--------|
| VM in East US | Region not allowed | ❌ Denied | ![EastUS](screenshots/test-eastus.png) |
| Storage without tag | Missing `ProjectName` tag | ❌ Denied | ![NoTag](screenshots/test-notag.png) |
| Create Public IP | Should be blocked | ❌ Denied | ![PublicIP](screenshots/test-publicip.png) |
| VM in Canada Central with tag | Valid deployment | ✅ Allowed | ![CanadaCentral](screenshots/test-canada.png) |


## 🧠 Lessons Learned
- Azure Policy is a powerful governance tool.
- Initiatives simplify management of multiple policies.
- Testing with real cases validates enforcement effectively.




