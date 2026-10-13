# Deploying Managed Wi-Fi to Chromebooks with Google Admin Console

## Purpose

This guide explains how to centrally deploy a Wi-Fi configuration to managed Chromebooks using Google Admin Console.

The configuration is applied at the device level so Chromebooks can connect to the managed network without requiring users to manually enter Wi-Fi credentials.

No organization-specific SSIDs, passwords, domains, IP addresses, or other sensitive infrastructure information should be stored in this documentation.

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

Enable:

[x] Chromebooks (by device)

Leave other platforms disabled unless they are specifically required.

For a Chromebook-only deployment:

[ ] Android
[ ] Chromebooks (by user)
[x] Chromebooks (by device)
[ ] Google Meet hardware
[ ] iOS

Using "Chromebooks (by device)" applies the network configuration directly to managed ChromeOS devices.

This also allows the network to be available before a user signs in.

---

## Network Name

### Name

The Name field is an administrative label used inside Google Admin Console.

Example:

Student Wi-Fi - Managed Chromebooks

This value does not need to match the actual SSID.

### SSID

Enter the exact SSID broadcast by the wireless infrastructure.

Example:

Student-WiFi

The SSID entered in Google Admin must exactly match the network name configured on the wireless controller.

Do not document production SSIDs in a public repository.

---

## Automatic Connection

Enable:

[x] Automatically connect

This allows managed Chromebooks to automatically connect when the configured network is available.

---

## Security

Configure the same wireless security method used by the wireless infrastructure.

For a WPA/WPA2/WPA3 Personal network, enter the network passphrase in the Google Admin configuration.

Important:

Never store the actual Wi-Fi passphrase in documentation, source control, screenshots, tickets, or public repositories.

Example documentation should use:

<WI-FI-PASSPHRASE>

instead of an actual credential.

---

## IP Settings

For a standard DHCP-based network, leave:

[ ] Allow IP address to be configured on the device

The Chromebook will receive its IP configuration from DHCP.

Static addresses should only be configured when specifically required.

---

## Proxy Settings

For networks that do not use an explicit proxy, configure:

Proxy Type:
Direct Internet connection

If an organization uses an HTTP/HTTPS proxy, configure it according to the organization's network requirements.

Do not publish internal proxy addresses in public documentation.

---

## DNS Settings

For a standard DHCP configuration:

[ ] Allow users to modify these values

Select:

(x) Automatic name servers

Leave static DNS server fields empty unless custom DNS servers are required.

Do not publish internal DNS server IP addresses in public documentation.

---

## Custom Search Domains

Leave the search domain field empty unless an internal DNS search domain is required.

When left empty, ChromeOS can use values supplied through DHCP.

Internal DNS domains should not be included in public documentation.

---

## Captive Portal Settings

For a normal internal password-protected Wi-Fi network that does not require browser-based authentication:

(x) Captive Portal Detection Off

Leave:

[ ] HTTP web probes only

If the network requires users to interact with a captive portal or sign-in page, enable captive portal detection instead.

---

## Safe Wi-Fi Migration Procedure

When migrating Chromebooks from an existing Wi-Fi network to a new managed Wi-Fi configuration, avoid removing the existing network before devices receive the new policy.

Recommended process:

1. Keep the existing network available.

2. Configure the new Wi-Fi network in Google Admin Console.

3. Enable:

   Chromebooks (by device)

4. Enable:

   Automatically connect

5. Save the configuration.

6. Allow managed Chromebooks to receive the updated device policy while they still have Internet access.

7. Test the new network on a small number of Chromebooks.

8. Verify:

   - Successful Wi-Fi association
   - DHCP address assignment
   - DNS resolution
   - Internet connectivity
   - Automatic reconnection after restart

9. Confirm that the broader Chromebook fleet has received the policy.

10. Retire the previous network only after successful validation.

---

## Why Device-Level Configuration Is Preferred

Using:

Chromebooks (by device)

makes the Wi-Fi configuration part of the managed Chromebook policy rather than relying on individual users to configure the network.

Benefits include:

- Wi-Fi availability before user login
- Centralized credential management
- Consistent configuration across devices
- Reduced manual setup
- Easier network migration
- Less exposure of Wi-Fi credentials to users

---

## Security Considerations

Do not include the following in public documentation:

- Wi-Fi passwords
- Production SSIDs
- Internal domains
- Organizational Unit names
- Device serial numbers
- MAC addresses
- Internal IP addresses
- VLAN IDs
- Firewall rules
- Internal DNS servers
- Administrative usernames
- Google Admin screenshots containing organization-specific information

Use placeholders such as:

<SSID>
<WI-FI-PASSPHRASE>
<ORGANIZATION-DOMAIN>
<DEVICE-OU>
<DNS-SERVER>

when examples are necessary.

---

## Configuration Summary

Platform:
Chromebooks (by device)

Connection:
Automatically connect

IP configuration:
DHCP

Proxy:
Direct Internet connection

DNS:
Automatic

Captive Portal Detection:
Off for networks without captive portal authentication

Deployment:
Google Admin device policy

Result:
Managed Chromebooks automatically receive the centrally configured Wi-Fi profile without requiring users to manually enter network credentials.
