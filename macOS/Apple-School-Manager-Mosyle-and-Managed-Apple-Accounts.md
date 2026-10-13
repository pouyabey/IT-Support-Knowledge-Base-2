# Apple School Manager, Mosyle, and Managed Apple Accounts

## Overview

Implemented and prepared a centralized Apple device management environment using Apple School Manager (ASM), Mosyle MDM, and Google Workspace.

The main goals are to:

- Automate management of school-owned Macs
- Prevent personal Apple Accounts from being used on school Macs
- Reduce Activation Lock risks
- Allow staff to use school-managed Apple Accounts
- Keep Apple devices under organizational control

## Problem

School-owned Macs could previously be signed into personal Apple Accounts.

This can create an Activation Lock problem after a device is erased or reassigned. We currently have a 2020 Mac affected by this issue, which cannot be fully reused or sold until the lock is resolved.

Apple devices also were not automatically assigned to the school's MDM.

## Implementation

### 1. Apple School Manager and Mosyle Integration

- Created Mosyle as a Device Management Service in Apple School Manager
- Exchanged the required public key and server token
- Verified communication between ASM and Mosyle
- Set Mosyle as the default MDM assignment for new Macs

Existing Macs can also be manually assigned to Mosyle from Apple School Manager.

### 2. School Domain Verification

Verified the school's email domain in Apple School Manager.

This allows the organization to manage Apple Accounts associated with the school domain and prepare them for Google Workspace authentication.

### 3. Managed Apple Accounts

The planned account structure is:

Google Workspace
→ Managed Apple Account
→ Apple School Manager
→ Mosyle-managed Mac

Staff will be able to use their school credentials for Apple services through Managed Apple Accounts.

### 4. Block Personal Apple Accounts on School Macs

School-owned Macs will be restricted to Managed Apple Accounts only.

This prevents staff from signing into school Macs with personal Gmail, iCloud, or other personal Apple Accounts.

Benefits include:

- Reducing Activation Lock risk
- Preventing school devices from becoming tied to personal accounts
- Making devices easier to reset and reassign
- Avoiding problems when devices are sold or retired
- Keeping organizational devices under school control

## Existing Personal Accounts

Apple School Manager identified existing personal Apple Accounts using the school email domain.

Before Managed Apple Accounts are fully implemented, those users may need to either:

- Transfer the existing account to organizational management, or
- Change the email address of their personal Apple Account to a personal address

A personal account may still be kept for use on personal devices, but it will not be permitted on school-owned Macs.

## Domain Capture

Domain Capture will allow the organization to take control of the school email domain for Apple Account use.

Because this affects existing accounts and cannot simply be reversed, implementation will proceed after management approval.

## Current Status

Completed:
- Apple School Manager access
- Mosyle MDM integration
- MDM server token exchange
- Default Mac assignment to Mosyle
- School domain verification

Pending:
- Management approval
- Domain Capture
- Google Workspace federation
- Managed Apple Account rollout
- Restriction of school Macs to Managed Apple Accounts only
- Assignment of existing Macs to Mosyle

## Expected Result

School-owned Macs will be centrally managed through Apple School Manager and Mosyle, while staff use organization-managed Apple Accounts instead of personal Apple IDs.

This provides a cleaner deployment process and significantly reduces the risk of Activation Lock preventing devices from being reused, reassigned, or sold.
