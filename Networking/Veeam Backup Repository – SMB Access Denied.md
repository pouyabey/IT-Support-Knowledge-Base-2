# 🔧 Veeam Backup Repository – SMB Access Denied

**Category:** Backup Infrastructure | Network Storage | Permissions  
**Technologies:** Veeam, Synology NAS, SMB  
**Status:** ✅ Resolved

## 🔴 Problem
Veeam was unable to access a replacement NAS backup repository.

- Backup copy jobs could not access the destination.
- The Veeam console displayed a misleading server availability error.
- Diagnostic logs revealed the actual issue: **Access Denied**.

## 🔍 Root Cause
The service account had Read/Write permissions on the shared folder but was explicitly denied access to the SMB service.

The SMB restriction overrode the folder permissions, preventing Veeam from accessing the repository.

## 🛠️ Troubleshooting & Resolution
1. Verified NAS connectivity and shared folder accessibility.
2. Compared access using different authorized accounts.
3. Reviewed Veeam diagnostic logs and identified the permission error.
4. Examined shared folder and SMB application permissions.
5. Removed the unnecessary explicit SMB Deny, allowing access through existing group permissions.
6. Verified repository connectivity and successfully synchronized Veeam metadata.
7. Re-enabled the backup copy job.

## ✅ Outcome
- Repository connectivity restored.
- Backup copy sessions resumed.
- Initial backup data transfer initiated; completion pending verification.

## 💡 Key Takeaway
**Shared folder permissions and SMB application permissions are separate access controls.**

An explicit Deny can prevent access even when Read/Write permissions are granted.

Always investigate effective permissions and diagnostic logs before assuming a network or server failure.
