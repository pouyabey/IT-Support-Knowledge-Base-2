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

# Troubleshooting Workflow

I followed my standard troubleshooting process:

**Clarify the Issue → Determine the Scope → Check the Basics → Isolate the Cause → Apply the Fix → Verify the Resolution → Document the Issue**

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

`Settings → System → Activation`

I also verified that the issue was related to the device rather than simply assuming that a successful Windows login meant the computer was properly registered.

A user being able to sign in does **not** necessarily mean that the device is correctly joined to Microsoft Entra ID or Active Directory.

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

Useful commands included:

```powershell
ipconfig /all
