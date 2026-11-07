
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
- Some other network devices operated normally at 100 Mbps due to their hardware specifications.

---

## 🧪 2. Troubleshooting & Test Results

| Test | Action | Result |
|------|--------|--------|
| Direct PC Connection | Bypassed the IP phone and connected the computer directly | ✅ 1000 Mbps |
| Through IP Phone | Connected the computer through the phone's Ethernet port | ⚠️ Phone uplink sometimes limited to 100 Mbps |
| Cable Reconnection | Reconnected Ethernet cables multiple times | ⚠️ Link sometimes negotiated at 100 Mbps and sometimes at 1000 Mbps |
| Auto-Negotiation | Enabled automatic link negotiation on the switch | ⚠️ Intermittent 100 Mbps / 1000 Mbps connections and occasional link drops |
| Manual Gigabit | Manually forced the switch port to 1 Gbps | ❌ Ethernet link disconnected |
| Direct Switch Test | Connected an IP phone directly to different switch ports, bypassing structured cabling | ⚠️ Sometimes 100 Mbps, sometimes 1000 Mbps |
| Original Connection Retest | Returned the phone to its original connection | ✅ Reached 1000 Mbps during retesting |

---

## 🔍 3. Key Findings

- The phone's uplink speed appeared to be the bottleneck for computers connected through it.
- The issue was intermittent rather than a permanent 100 Mbps limitation.
- Reconnecting Ethernet cables sometimes restored Gigabit connectivity.
- Direct switch connections also exhibited inconsistent link negotiation.
- Manually forcing the switch port to 1 Gbps caused the Ethernet link to disconnect.
- The issue could occur even when bypassing structured cabling.
- Multiple phones exhibited similar behavior, making isolated phone hardware failures less likely.
- Physical cabling and PoE-related issues have not been ruled out.

---

## ⚠️ 4. Possible Root Causes

| Potential Cause | Description |
|----------------|-------------|
| Auto-Negotiation | Possible instability during Ethernet speed and duplex negotiation |
| Cable Terminations | Intermittent RJ45 connectors, keystone jacks, or patch panel connections |
| Structured Cabling | Possible signal degradation or excessive cable resistance |
| PoE Delivery | Potential voltage drop or power delivery instability |
| Firmware | Possible phone or switch firmware-related negotiation behavior |

**Note:** These are hypotheses, not confirmed root causes.

The fact that the issue also occurs during direct switch testing suggests that structured cabling may not be the only contributing factor.

---

## 🛠️ 5. Temporary Workaround

Repeatedly disconnecting and reconnecting Ethernet cables sometimes restored **1000 Mbps** connectivity.

However, this is not a permanent solution because the underlying cause remains unidentified.

---

## 📋 6. Next Steps

### Planned Test: External Power Adapter

- [ ] Power an affected IP phone using a manufacturer-approved external power adapter.
- [ ] Disable PoE on the corresponding switch port.
- [ ] Keep the same Ethernet cable and network path.
- [ ] Test Auto-Negotiation across multiple reconnections.
- [ ] Monitor link speed, stability, and unexpected disconnections.
- [ ] Check switch port errors and link events.
- [ ] Compare results between direct switch connections and structured cabling.

### Expected Results

| Result | Interpretation |
|--------|----------------|
| Stable 1000 Mbps with external power | PoE delivery or power-related behavior becomes more suspect |
| Still alternating between 100/1000 Mbps | Auto-Negotiation, cable quality, or firmware remain possible |
| Stable Gigabit directly but unstable through structured cabling | Building cabling or terminations become more suspect |
| Intermittent link drops | Further investigation of physical connectivity and firmware required |

---

## 💡 7. Potential Workaround: Separate Phone and PC Connections

Computers achieved Gigabit speeds when connected directly to Ethernet, bypassing the IP phones.

A potential workaround is to connect computers and IP phones to separate network connections wherever suitable wall jacks and switch ports are available.

### Expected Benefits

- Computers could maintain Gigabit Ethernet connectivity without being limited by the phone's uplink speed.
- IP phones generally require far less bandwidth than 100 Mbps for voice communication.
- Existing network cabling could potentially be reused without installing additional cable runs.
- The workaround could reduce user impact while the underlying issue is investigated.

**Limitation:** This approach depends on the availability of working Ethernet connections and does not resolve the underlying phone negotiation issue.

---

## ✅ 8. Current Conclusion

The investigation identified an **intermittent Ethernet link negotiation issue** affecting multiple IP phones and indirectly reducing network performance for connected computers.

The issue was observed with both structured cabling and direct switch connections.

Additionally, manually forcing 1 Gbps on the switch resulted in link disconnection, suggesting that further investigation of link negotiation and physical connectivity is necessary.

### Areas for Further Investigation

1. Auto-Negotiation behavior between phones and switches.
2. PoE delivery and potential power instability.
3. Ethernet cable quality and terminations.
4. Phone and switch firmware.
5. Structured cabling and patch panel connections.

**Root Cause:** ❌ Not confirmed  
**Resolution Status:** 🔎 Under Investigation  
**Next Action:** Test using an external power adapter and compare connection stability.

---

**Documentation Note:** This case study has been anonymized for technical learning purposes. No confidential organizational details, network addresses, device identifiers, or internal infrastructure information are included.
