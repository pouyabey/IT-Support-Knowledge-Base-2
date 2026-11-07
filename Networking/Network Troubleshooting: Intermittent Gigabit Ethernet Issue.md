
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
| Cable Reconnection | Reconnected Ethernet cables multiple times | ⚠️ Some phones alternated between 100 and 1000 Mbps |
| Auto-Negotiation | Enabled automatic link negotiation | ⚠️ Intermittent 100 Mbps / link drops |
| Manual Gigabit | Selected 1 Gbps on the switch | ✅ Gigabit link indicated |
| Direct Switch Test | Connected an IP phone directly to the switch, bypassing structured cabling | ⚠️ Sometimes 100 Mbps, sometimes 1000 Mbps |
| Original Connection Retest | Returned the phone to its original connection | ✅ Reached 1000 Mbps during retesting |

---

## 🔍 3. Key Findings

- The phone uplink appeared to be the bottleneck for computers connected through it.
- The issue was intermittent rather than a permanent 100 Mbps limitation.
- Reconnecting Ethernet cables sometimes restored Gigabit connectivity.
- Direct switch connections also exhibited inconsistent link negotiation.
- The issue could occur even when bypassing structured cabling.
- Multiple phones exhibited similar behavior, making isolated phone hardware failures less likely.
- Physical cabling and PoE-related problems have not been ruled out.

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
- [ ] Compare direct switch connections with connections through structured cabling.

### Expected Results

| Result | Interpretation |
|--------|----------------|
| Stable 1000 Mbps with external power | PoE delivery or power-related behavior becomes more suspect |
| Still alternating between 100/1000 Mbps | Auto-Negotiation, cable quality, or firmware remain possible |
| Stable Gigabit directly but unstable through structured cabling | Building cabling or terminations become more suspect |
| Intermittent link drops | Further investigation of physical connectivity and firmware required |

---

## ✅ 7. Current Conclusion

The investigation identified an **intermittent Ethernet link negotiation issue** affecting multiple IP phones.

Because inconsistent link speeds were also observed during direct switch testing, the issue cannot currently be attributed solely to structured cabling.

The most relevant areas for further investigation are:

1. Auto-Negotiation behavior between phones and switches.
2. PoE delivery, voltage drop, or cable resistance.
3. Physical cabling and connector quality.
4. Phone or switch firmware.

**Root Cause:** ❌ Not confirmed  
**Resolution Status:** 🔎 Under Investigation  
**Next Action:** Test with an external power adapter.

---

**Documentation Note:** This case study has been anonymized for technical learning purposes.
