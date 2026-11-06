
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
- Other network devices operating at 100 Mbps appeared normal due to their hardware specifications.

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
| Original Connection Retest | Returned the phone to its original connection | ✅ Remained at 1000 Mbps |

---

## 🔍 3. Key Findings

- The phone uplink appeared to be the bottleneck for computers connected through it.
- The issue was intermittent rather than a permanent 100 Mbps limitation.
- Reconnecting Ethernet cables sometimes restored Gigabit connectivity.
- A phone that reached 1000 Mbps maintained that speed during direct switch testing.
- The problem could not be consistently reproduced when bypassing structured cabling.
- Physical cabling and PoE-related issues have not been ruled out.
- Multiple phones exhibited similar behavior, making isolated phone hardware failures less likely.

---

## ⚠️ 4. Possible Root Causes

| Potential Cause | Description |
|----------------|-------------|
| Auto-Negotiation | Possible instability during Ethernet link negotiation |
| Cable Terminations | Intermittent RJ45, keystone, or patch panel connections |
| Structured Cabling | Possible signal degradation or excessive resistance |
| PoE Delivery | Potential voltage drop or power delivery instability |
| Firmware | Possible phone or switch firmware behavior |

**Note:** These are hypotheses, not confirmed root causes.

---

## 🛠️ 5. Temporary Workaround

Repeatedly disconnecting and reconnecting Ethernet cables restored **1000 Mbps** on some affected phones.

This is not considered a permanent solution.

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
| Still negotiating at 100 Mbps | Signal quality, cable terminations, or Auto-Negotiation remain possible |
| Intermittent link drops | Further investigation of cabling and firmware required |

---

## ✅ 7. Current Conclusion

The investigation identified an **intermittent Ethernet link negotiation issue** affecting multiple IP phones.

The most relevant areas for further investigation are:

1. Physical cabling and cable terminations.
2. PoE voltage drop or cable resistance.
3. Auto-Negotiation behavior.
4. Phone or switch firmware.

**Root Cause:** ❌ Not confirmed  
**Resolution Status:** 🔎 Under Investigation  
**Next Action:** Test with an external power adapter.

---

**Documentation Note:** This case study has been anonymized for technical learning purposes.
