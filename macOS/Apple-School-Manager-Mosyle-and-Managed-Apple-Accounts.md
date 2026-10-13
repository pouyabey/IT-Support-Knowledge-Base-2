# Apple School Manager + Mosyle Integration

## Overview

Implemented centralized Apple device and account management by integrating Apple School Manager (ASM), Mosyle MDM, and Google Workspace.

The goal was to improve control of school-owned Macs, simplify enrollment, and prevent devices from becoming tied to personal Apple IDs.

## Problem

Some school Macs had been signed into personal Apple IDs.

This creates a risk of Activation Lock remaining on a device after it is reset. In one case, a 2020 Mac became locked to a previous user's Apple ID, preventing the device from being fully reused or sold.

Apple devices were also not automatically assigned to the school's MDM.

## Implementation

### 1. Connected Apple School Manager to Mosyle

- Created a Device Management Service for Mosyle in Apple School Manager.
- Exchanged the required public key and server token.
- Verified communication between ASM and Mosyle.
- Configured Mosyle as the default MDM assignment for new Macs.

### 2. Device Assignment

Existing Apple devices can now be manually assigned to Mosyle through Apple School Manager.

New Macs added to the organization can automatically be assigned to Mosyle for enrollment.

### 3. Verified the School Domain

Verified the organization's email domain in Apple School Manager.

This allows the school to manage Apple Accounts that use the school email domain.

### 4. Prepared Managed Apple Accounts

Planned integration with Google Workspace so staff can use their existing school Google credentials with Managed Apple Accounts.

Benefits include:

- Preventing new personal Apple IDs from using school email addresses
- Reducing Activation Lock risks
- Keeping school devices under organizational control
- Simplifying Apple Account management
- Providing consistent device management through Mosyle

## Domain Capture

Apple School Manager identified existing personal Apple Accounts using the school domain.

Domain Capture can be used to transition these accounts.

Existing users will be asked to either:

- Transfer the account to the organization, or
- Change the Apple Account to a personal email address

Because Domain Capture affects existing user accounts and is not easily reversible, management approval is required before implementation.

## Result

The Apple management environment is now prepared for:

- Automated Device Enrollment
- Centralized Mac management through Mosyle
- Managed Apple Accounts
- Google Workspace authentication
- Reduced risk of personal Apple IDs locking school-owned devices

## Next Steps

- Assign existing Macs to Mosyle
- Enable Google Workspace federation
- Implement Domain Capture after approval
- Restrict school-owned Macs to Managed Apple Accounts
