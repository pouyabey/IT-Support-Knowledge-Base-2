# Deploying Managed Wi-Fi to Chromebooks with Google Admin Console

## Purpose

This guide explains how to centrally deploy a Wi-Fi configuration to managed Chromebooks using Google Admin Console.

The configuration is applied at the device level so managed Chromebooks can automatically receive and use the Wi-Fi profile without requiring users to manually enter network credentials.

This documentation intentionally uses generic placeholders and does not include production SSIDs, passwords, domains, IP addresses, or other organization-specific information.

---

## Admin Console Path

Navigate to:

Devices
> Networks
> Wi-Fi

Select the Organizational Unit containing the Chromebook devices that should receive the network configuration.

To deploy the configuration broadly, select the appropriate parent Organizational Unit.

Click:

CREATE WI-FI NETWORK

---

## Platform Access

For a Chromebook-only deployment, enable only:

[x] Chromebooks (by device)

Leave the other platforms disabled:

[ ] Android
[ ] Chromebooks (by user)
[x] Chromebooks (by device)
[ ] Google Meet hardware
[ ] iOS

Using "Chromebooks (by device)" applies the network configuration directly to managed ChromeOS devices rather than associating the configuration with an individual user account.

This allows the managed network to be available on the device even before a user signs in.

---

## Network Name

### Name

The Name field is an administrative label used only inside Google Admin Console.

It does not need to match the actual wireless network name.

Example:

Managed Student Wi-Fi

### SSID

Enter the exact SSID broadcast by the wireless infrastructure.

Example:

Student-WiFi

The SSID configured in Google Admin must exactly match the SSID configured on the wireless controller or access points.

Do not include production SSIDs in public documentation.

---

## Automatic Connection

Enable:

[x] Automatically connect

This allows managed Chromebooks to automatically connect to the network whenever it is available.

---

## Security Settings

Configure the same wireless security type used by the wireless infrastructure.

For a WPA/WPA2/WPA3 Personal network, enter the network passphrase in the Passphrase field.

The following values must match the wireless infrastructure:

- SSID
- Security type
- Passphrase

Never store real Wi-Fi credentials in documentation, source control, screenshots, tickets, or public repositories.

Use placeholders such as:

<SSID>
<WI-FI-PASSPHRASE>

---

## IP Settings

For a standard DHCP-based network, leave the following option disabled:

[ ] Allow IP address to be configured on the device

The Chromebook will receive its IP address, subnet information, gateway, and other network settings through DHCP.

Static IP configuration is not required for normal Chromebook deployments.

---

## Proxy Settings

For networks that do not use an explicit proxy, configure:

Proxy Type:
Direct Internet connection

Only configure proxy settings if the organization specifically requires an HTTP or HTTPS proxy.

Do not publish internal proxy addresses in public documentation.

---

## DNS Settings

For a standard DHCP-based configuration:

[ ] Allow users to modify these values

Select:

(x) Automatic name servers

Leave the Static DNS servers field empty.

This allows the Chromebook to use the DNS servers supplied by DHCP.

Do not publish internal DNS server addresses in public documentation.

---

## Custom Search Domains

Leave the Domain values field empty unless a specific DNS search domain is required.

When left empty, ChromeOS can use the search domain information supplied by DHCP.

Internal DNS domains should not be included in public documentation.

---

## Captive Portal Settings

For a normal password-protected internal Wi-Fi network that does not require browser-based authentication, select:

(x) Captive Portal Detection Off

Leave the following option disabled:

[ ] HTTP web probes only

If the wireless network requires users to interact with a captive portal, browser login page, or terms-of-service page, Captive Portal Detection should be enabled instead.

---

## Safe Wi-Fi Migration Procedure

When migrating managed Chromebooks from an existing Wi-Fi network to a new managed Wi-Fi configuration, do not remove the existing network before the devices receive the new policy.

A safe migration process is:

1. Keep the existing Wi-Fi network online.

2. Create the new Wi-Fi configuration in Google Admin Console.

3. Enable:

   Chromebooks (by device)

4. Enable:

   Automatically connect

5. Enter the new SSID, security type, and passphrase.

6. Save the configuration.

7. Allow the managed Chromebooks to receive the new device policy while they still have Internet access through the existing network.

8. Test the new network on a small number of Chromebook devices.

9. Verify:

   - Successful Wi-Fi association
   - DHCP address assignment
   - DNS resolution
   - Internet connectivity
   - Automatic reconnection
   - Connectivity after restart
   - Availability at the login screen

10. Confirm that the broader Chromebook fleet has received the policy.

11. Retire the old Wi-Fi network only after the new configuration has been successfully validated.

---

## Why Device-Level Configuration Is Preferred

Using:

Chromebooks (by device)

makes the Wi-Fi configuration part of the managed Chromebook policy instead of relying on individual users to configure the network.

Benefits include:

- Wi-Fi availability before user login
- Centralized Wi-Fi management
- Consistent configuration across devices
- Reduced manual configuration
- Easier Wi-Fi migrations
- Reduced exposure of Wi-Fi credentials to end users
- Improved control over managed Chromebook connectivity

---

## Security Considerations

Do not include the following information in a public repository:

- Wi-Fi passwords
- Production SSIDs
- Internal domains
- Organizational Unit names
- Usernames
- Device serial numbers
- MAC addresses
- Internal IP addresses
- Subnet information
- VLAN IDs
- Firewall rules
- Internal DNS server addresses
- Administrative account information
- Screenshots containing organization-specific information

Use generic placeholders when examples are necessary.

Examples:

<SSID>
<WI-FI-PASSPHRASE>
<ORGANIZATION-DOMAIN>
<DEVICE-OU>
<DNS-SERVER>
<INTERNAL-IP>

---

## Configuration Summary

Platform:
Chromebooks (by device)

Automatic connection:
Enabled

IP configuration:
DHCP

Proxy:
Direct Internet connection

DNS:
Automatic name servers

Static DNS:
None

Custom search domains:
None

Captive Portal Detection:
Off for networks without captive portal authentication

Deployment method:
Google Admin device policy

Result:
Managed Chromebooks automatically receive the centrally configured Wi-Fi profile without requiring users to manually enter network credentials.
