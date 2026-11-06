
# 🔧 Network Troubleshooting: Intermittent Gigabit Ethernet Issue

**Equipment:** Gigabit Network Switches & IP Phones  
**Status:** 🔎 Under Investigation

---

## 📌 1. Problem Overview

Several computers experienced slow network connectivity when connected through IP phones.

The phones intermittently negotiated at **100 Mbps (Fast Ethernet)** instead of **1000 Mbps (Gigabit Ethernet)**.

### Initial Observations
- Some phones established 100 Mbps connections, while others negotiated at 1000 Mbps.
- Computers connected through affected phones experienced reduced network speeds.
- Direct Ethernet connections to computers worked normally at Gigabit speed.
- Some other network devices operated at 100 Mbps as expected due to their hardware limitations.

---

## 🧪 2. Troubleshooting & Test Results

| Test | Action | Result |
|------|--------|--------|
| Direct PC Connection | Bypassed the IP phone | ✅ 1000 Mbps |
| Through IP Phone | Connected PC through the phone | ⚠️ Phone uplink sometimes limited to 100 Mbps |
| Cable Reconnection | Reconnected Ethernet cables multiple times | ✅ Some phones reached 1000 Mbps |
| Auto-Negotiation | Enabled automatic link negotiation | ⚠️ Intermittent 100 Mbps / link drops |
| Manual Gigabit | Selected 1 Gbps on the switch | ✅ Gigabit link indicated |
| Direct Switch Test | Connected a phone that had reached 1 Gbps directly to multiple switch ports | ✅ Consistent 1000 Mbps |
| Original Connection Retest | Returned the phone to its original network connection | ✅ Remained at 1000 Mbps |

---

## 🔍 3. Key Findings

- The IP phone uplink appeared to be the bottleneck for computers connected through it.
- The issue was intermittent rather than a permanent 100 Mbps limitation.
- Reconnecting Ethernet cables sometimes restored Gigabit connectivity.
- A phone that successfully negotiated at 1000 Mbps maintained that speed during direct switch testing.
- The issue could not be consistently reproduced when bypassing the structured cabling.
- Physical cabling and PoE-related problems have not been ruled out.

---

## ⚠️ 4. Possible Root Causes

| Potential Cause | Description |
|----------------|-------------|
| Auto-Negotiation | Possible instability during Ethernet link negotiation |
| Cable Terminations | Intermittent RJ45 or keystone connections |
| Structured Cabling | Possible signal degradation or excessive resistance |
| PoE Delivery | Potential voltage drop or unstable power delivery |
| Firmware | Possible IP phone or switch firmware behavior |
| Hardware | Possible IP phone Ethernet port issue |

**Note:** These are hypotheses, not confirmed root causes.

---

## 🛠️ 5. Temporary Workaround

Repeatedly disconnecting and reconnecting Ethernet cables restored **1000 Mbps** on some affected phones.

This workaround does not guarantee long-term stability.

---

## 📋 6. Next Steps

### Planned Test: External Power Adapter

- [ ] Power an affected IP phone using a manufacturer-approved external adapter.
- [ ] Disable PoE on the corresponding switch port.
- [ ] Keep the same Ethernet cable and network path.
- [ ] Test Auto-Negotiation across multiple reconnections.
- [ ] Monitor link speed, stability, and disconnections.
- [ ] Review switch port errors and link events.

### Expected Results

| Result | Interpretation |
|--------|----------------|
| Stable 1000 Mbps with external power | PoE delivery or power-related behavior becomes more suspect |
| Still negotiating at 100 Mbps | Signal quality, cable terminations, or negotiation issues remain possible |
| Intermittent link drops | Further investigation of cabling, ports, and firmware required |

---

## ✅ 7. Current Conclusion

The investigation identified an **intermittent Ethernet link negotiation issue** affecting computers connected through IP phones.

The available evidence suggests several possible contributing factors:

1. Unstable physical connections or cable terminations.
2. PoE delivery or cable resistance issues.
3. Auto-Negotiation instability.
4. IP phone firmware or hardware behavior.

**Root Cause:** ❌ Not confirmed  
**Resolution Status:** 🔎 Under Investigation  
**Next Action:** Test with an external power adapter.

---

**Documentation Note:** This case study has been anonymized for technical learning and troubleshooting purposes.
