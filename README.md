# Enforcing-Policies
Enforcing Organizational Policies in the Cloud

## 🎥 Video Demo
[Watch the video demo](#) *(Replace with actual link)*

# MapleTech Policy Lab

## ✅ Summary
As a new Cloud Security Engineer at MapleTech Solutions, I implemented governance using Azure Policy. The objective was to enforce deployment standards for security and compliance.

## 🎯 Objectives
- Restrict deployments to Canada Central region.
- Enforce tagging with `ProjectName` tag.
- Block creation of Public IP addresses.
- Validate policy enforcement with real-world test cases.

## 📜 Policies Implemented
1. **Only-CanadaCentral**: Denies resources outside Canada Central.
2. **Require-ProjectName-Tag**: Denies resources without a `ProjectName` tag.
3. **Deny-Public-IP**: Blocks creation of public IP addresses.

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

