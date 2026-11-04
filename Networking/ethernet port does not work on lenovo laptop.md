Issue: Realtek PCIe GbE Ethernet Adapter Not Detected (Windows)

Problem:
A Lenovo computer was unable to connect via Ethernet. The Realtek PCIe GbE Family Controller was missing from active network adapters and appeared grayed out in Device Manager with Error Code 45 (hardware not connected/detected). The user was relying on slow Wi-Fi.

Troubleshooting:
1. Verified the Ethernet cable and wall jack using another computer.
2. Checked Device Manager and confirmed Error Code 45.
3. Attempted to enable the Ethernet adapter through Device Manager and BIOS without success.
4. Updated Windows and network drivers using Lenovo Vantage, but the issue persisted.
5. Updated the system BIOS, which restored detection of the Realtek Ethernet controller.

Resolution:
The BIOS update successfully resolved the issue. The Ethernet adapter became operational, and the computer established a stable wired connection. Speed tests confirmed significantly improved network performance.

Root Cause:
Likely a BIOS/firmware-related hardware detection issue. The exact underlying cause was not independently confirmed.
