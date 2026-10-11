# Entra ID and Intune Re-enrollment After Motherboard Replacement

## Issue Summary

A Windows laptop was sent for warranty repair and the motherboard was replaced.

After the device was returned, several problems appeared:

- Windows activation was failing.
- The device was not being recognized correctly in Microsoft Entra ID.
- Intune management and device synchronization were not functioning as expected.
- The device had previously been managed successfully before the motherboard replacement.

Because replacing a motherboard can affect the hardware identity of a Windows device, I suspected that the existing device registration and management records might no longer match the repaired computer.

---

## Troubleshooting Workflow

I followed my standard troubleshooting process:

Clarify the Issue → Determine the Scope → Check the Basics → Isolate the Cause → Apply the Fix → Verify the Resolution → Document the Issue

---

## 1. Clarify the Issue

I first confirmed exactly what was failing.

The computer was able to:

- Boot into Windows.
- Connect to the network.
- Allow the user to access Windows.

However:

- Windows activation was failing.
- The device was not behaving as expected in Entra ID.
- Intune management was not functioning correctly.

I checked Windows activation under:

Settings → System → Activation

I also verified that the issue was related to the device rather than simply assuming that a successful Windows login meant the computer was properly registered.

A user being able to sign in does not necessarily mean that the device is correctly joined to Microsoft Entra ID or Active Directory.

For example, the user may be signing in with:

- A local account.
- Cached domain credentials.
- An existing Windows profile.
- A Microsoft account.

Device registration must be verified separately.

---

## 2. Determine the Scope

I checked whether other managed computers were experiencing similar issues.

Other devices were operating normally.

The affected computer was the only device experiencing the problem, and it had recently undergone a motherboard replacement.

This strongly suggested a device-specific issue rather than:

- A company-wide Entra ID outage.
- An Intune service issue.
- A general network problem.
- A widespread authentication problem.

The motherboard replacement became an important troubleshooting clue.

---

## 3. Check the Basics

Before making major changes to the device, I started with the least disruptive checks.

### Verify Network Connectivity

I confirmed that the computer had normal network access.

I checked:

- Wi-Fi or Ethernet connectivity.
- IP configuration.
- DNS resolution.
- General internet access.

Useful command:

ipconfig /all

This allows me to inspect:

- IP address
- Subnet mask
- Default gateway
- DHCP configuration
- DNS servers

---

### Verify Connectivity to Microsoft Authentication Services

I tested outbound HTTPS connectivity to Microsoft's authentication infrastructure:

Test-NetConnection login.microsoftonline.com -Port 443

A successful result should include:

TcpTestSucceeded : True

This confirms that the computer can:

1. Resolve the Microsoft hostname.
2. Reach the destination.
3. Establish a TCP connection over HTTPS port 443.

This helped rule out a basic network or firewall connectivity problem before focusing on Entra ID and Intune.

It is important to note that this test does not prove that every Microsoft Intune or Entra service is functioning correctly.

It only confirms basic connectivity to that specific Microsoft authentication endpoint over TCP 443.

---

## 4. Check the Device Registration State

I used:

dsregcmd /status

This command provides information about the Windows device's identity and registration state.

Important fields I reviewed included:

AzureAdJoined
DomainJoined
WorkplaceJoined
DeviceId
TenantId

For an Entra-joined device, I would expect the appropriate registration fields to reflect the organization's configuration.

For example:

AzureAdJoined : YES

If the device unexpectedly showed:

AzureAdJoined : NO

that would indicate that the device was not currently joined to Microsoft Entra ID.

I also reviewed the DeviceId and TenantId to determine whether the device registration matched the organization's environment.

---

## 5. Check the Work or School Account

I reviewed:

Settings → Accounts → Access work or school

I checked whether the organization's account was:

- Connected.
- Properly registered.
- Showing management information.
- Able to synchronize.

If the device was enrolled in MDM, I also checked:

Access work or school → Organization Account → Info

and attempted:

Sync

This allowed me to determine whether the device could still communicate with the organization's device-management environment.

---

## 6. Check Intune and Entra ID

I reviewed the administrative portals to determine how the device appeared on the server side.

I checked for:

- The device in Microsoft Entra ID.
- The device in Microsoft Intune.
- Duplicate device objects.
- Old or stale device records.
- Device ID mismatches.
- Last check-in time.
- Enrollment status.
- Management status.

Because the motherboard had been replaced, I considered the possibility that the repaired computer's current hardware identity no longer aligned correctly with its previous cloud device record.

---

## 7. Check MDM Enrollment Logs

For additional information about Intune enrollment or synchronization failures, I checked Windows Event Viewer.

Path:

Event Viewer → Applications and Services Logs → Microsoft → Windows → DeviceManagement-Enterprise-Diagnostics-Provider → Admin

This log can provide information about:

- MDM enrollment.
- Device synchronization.
- Policy processing.
- Enrollment failures.
- Management communication errors.

This is particularly useful when the Intune portal only shows that the device is not checking in but does not clearly explain why.

---

## Isolate the Cause

At this point, several things were known:

- Other managed computers were working normally.
- The affected computer had recently received a replacement motherboard.
- General network connectivity was functioning.
- Microsoft authentication services were reachable over HTTPS.
- The issue was isolated to one repaired computer.
- The device registration and management relationship was not functioning as expected.

Based on these findings, I focused on the device identity and management state rather than continuing to troubleshoot the network.

The motherboard replacement was likely related to the change in hardware identity, while existing Entra ID and Intune records could still represent the computer's previous state.

This could result in stale or mismatched device records and interfere with normal enrollment or management.

---

## Apply the Fix

I first attempted the least disruptive recovery steps.

These included:

- Verifying network connectivity.
- Confirming Microsoft HTTPS connectivity.
- Checking the Entra join state.
- Checking the Work or School account.
- Attempting an Intune synchronization.
- Reviewing Entra ID and Intune device records.

When those steps did not restore normal management, I moved to a clean device-registration approach.

The stale or incorrect device records were removed from the appropriate management systems.

The device was then prepared for a clean enrollment so that a new relationship could be established between:

- Windows
- Microsoft Entra ID
- Microsoft Intune
- The organization's management environment

Because the existing device state could no longer be trusted after the hardware change, the computer was ultimately wiped and re-enrolled.

After the clean enrollment, the device established a new and correct identity within the organization's environment.

---

## Windows Activation

Windows activation was also checked during the troubleshooting process.

Activation status can be reviewed through:

Settings → System → Activation

Additional commands that can help investigate activation include:

slmgr /xpr

This displays whether Windows is permanently activated.

Another useful command is:

slmgr /dlv

This displays detailed Windows licensing information.

One important troubleshooting distinction is that Windows activation and Intune enrollment are separate systems.

Intune does not directly provide a Windows activation code.

A motherboard replacement may affect Windows digital licensing because the motherboard is a major component of the device's hardware identity.

At the same time, the motherboard replacement may also affect how the device is represented in Entra ID, Intune, or Windows Autopilot.

These issues can occur together after hardware replacement, but they should still be investigated as separate components of the overall problem.

---

## Verify the Resolution

After the repair and re-enrollment process, I verified the device from both the endpoint and administrative sides.

### On the Windows Computer

I checked:

dsregcmd /status

and confirmed that the expected device registration information was present.

I also verified:

- The organizational account was connected.
- The device could authenticate successfully.
- The device could access organizational resources.
- Intune synchronization completed successfully.
- Windows activation was successful.

---

### In Microsoft Entra ID

I verified that:

- The device appeared correctly.
- The correct device identity was present.
- There were no conflicting stale records.
- The device was associated with the correct tenant.

---

### In Microsoft Intune

I verified that:

- The device appeared as managed.
- The device successfully checked in.
- Management synchronization worked.
- Policies could be applied.
- The device reported its status correctly.

---

## Final Resolution

The issue was resolved by rebuilding the device's management relationship after the motherboard replacement.

The troubleshooting process showed that basic network connectivity was functioning correctly, which allowed me to focus on the device's identity and enrollment state.

After removing stale device records and performing a clean re-enrollment, the computer was successfully recognized by Entra ID and Intune again.

Windows activation was also restored and verified separately.

---

## Troubleshooting Decision Flow

Motherboard Replaced
        |
        v
Windows boots successfully?
        |
        v
Check Windows Activation
        |
        v
Verify Network / DNS / Internet
        |
        v
Test Microsoft HTTPS Connectivity
Test-NetConnection login.microsoftonline.com -Port 443
        |
        v
Check Device Registration
dsregcmd /status
        |
        v
Check Access Work or School
        |
        v
Attempt Intune Sync
        |
        v
Check Entra ID / Intune Records
        |
        v
Check MDM Event Logs
        |
        v
Stale / mismatched device identity?
        |
        v
Remove stale records
        |
        v
Clean re-enrollment / wipe if required
        |
        v
Verify Entra + Intune + Activation

---

## Commands Used

### View Network Configuration

ipconfig /all

Used to inspect:

- IP address
- DHCP
- Default gateway
- DNS servers

---

### Test Microsoft HTTPS Connectivity

Test-NetConnection login.microsoftonline.com -Port 443

Expected successful result:

TcpTestSucceeded : True

Purpose:

Rule out basic outbound HTTPS connectivity problems before focusing on Entra ID or Intune.

---

### Check Entra Device Registration

dsregcmd /status

Important fields:

AzureAdJoined
DomainJoined
WorkplaceJoined
DeviceId
TenantId

Purpose:

Determine the actual Windows device registration state.

---

### Check Windows Activation

slmgr /xpr

Purpose:

Check whether Windows is permanently activated.

---

### View Detailed Licensing Information

slmgr /dlv

Purpose:

Display detailed Windows activation and licensing information.

---

## Key Troubleshooting Lessons

### 1. User login does not prove device registration

A user may still be able to sign in even when the device is not properly joined to Entra ID.

Always verify the actual device state with:

dsregcmd /status

---

### 2. Use evidence to eliminate categories of problems

Once HTTPS connectivity to Microsoft services was confirmed, I did not continue treating the issue as a basic internet connectivity problem.

The troubleshooting focus moved toward device identity and enrollment.

---

### 3. Hardware replacement can affect multiple systems

Replacing a motherboard can affect:

- Windows activation.
- Device hardware identity.
- Entra ID registration.
- Intune enrollment.
- Autopilot registration.

However, these systems should not automatically be treated as the same problem.

---

### 4. Start with low-risk troubleshooting

Before wiping or re-enrolling a computer, first verify:

- Network connectivity.
- Device registration.
- Work or School account status.
- MDM synchronization.
- Administrative device records.
- Relevant event logs.

A wipe should normally be used only after lower-risk troubleshooting steps have failed or when a clean device state is required.

---

### 5. Always verify from both sides

Successful troubleshooting should be confirmed:

Locally:

- Windows registration
- Login
- Activation
- Organizational connection

Administratively:

- Entra ID
- Intune
- Device check-in
- Policy synchronization

---

## Interview Summary

If asked about this issue during a technical interview, I would summarize it like this:

One of the more complex issues I worked on involved a Windows computer that came back from warranty repair after a motherboard replacement. After the repair, Windows activation was failing and the device was no longer being recognized correctly in Entra ID and Intune.

I first determined the scope and confirmed that other devices were working normally, which isolated the problem to that computer. I verified network and DNS connectivity and then used Test-NetConnection to confirm outbound HTTPS connectivity to Microsoft's authentication services.

From there, I used dsregcmd /status to investigate the actual device-registration state, checked the Work or School account and Intune synchronization, and reviewed the device records in Entra ID and Intune.

Because connectivity was working and the problem started immediately after the motherboard replacement, I focused on the device identity. The existing cloud records appeared to be stale or mismatched with the repaired device.

After lower-risk troubleshooting did not resolve the issue, I removed the stale device records and performed a clean re-enrollment. I then verified that the device appeared correctly in Entra ID and Intune, could successfully synchronize, and that Windows activation was restored.

Finally, I documented the symptoms, troubleshooting steps, root cause, actions taken, and final resolution.

---

## Documentation Notes

For this incident, I would document:

- Device model and asset information.
- Warranty repair history.
- Motherboard replacement.
- Original symptoms.
- Windows activation status.
- Network troubleshooting results.
- Microsoft HTTPS connectivity test.
- dsregcmd /status findings.
- Work or School account status.
- Intune synchronization attempts.
- Relevant Event Viewer findings.
- Entra ID device records.
- Intune device records.
- Stale or duplicate records removed.
- Wipe or re-enrollment actions.
- Final Entra ID registration status.
- Final Intune management status.
- Final Windows activation status.
- User confirmation that the device was working normally.
