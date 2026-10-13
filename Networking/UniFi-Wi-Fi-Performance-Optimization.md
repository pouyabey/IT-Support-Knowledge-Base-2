# UniFi Wi-Fi Performance Optimization

## Overview

This project focuses on improving wireless reliability and performance in a multi-access-point UniFi environment.

The primary areas of investigation are RF interference, airtime utilization, transmit retries, channel planning, and overall 2.4 GHz efficiency.

## Objective

Improve Wi-Fi reliability and performance by identifying and reducing:

- High TX retry rates
- RF interference
- Excessive airtime utilization
- Co-channel interference
- Unnecessary access point overlap
- Inefficient 2.4 GHz usage

The goal is to improve connection stability while making better use of the available wireless spectrum.

## Current Findings

Initial monitoring identified several access points with approximately **30–38% TX retries on the 2.4 GHz band**.

Additional observations include:

- High RF interference on multiple access points
- High airtime utilization
- Adequate overall AP density
- Significantly better performance on 5 GHz in several locations
- 2.4 GHz operating with 20 MHz channel widths
- Potential co-channel interference between nearby access points

These findings suggest that the primary issue is more likely related to RF congestion and configuration than insufficient AP coverage.

## Planned Work

### 1. Access Point Analysis

Review all UniFi access points and identify devices with:

- High TX retries
- High interference
- High airtime utilization
- Weak client signal levels
- Abnormal radio performance

### 2. 2.4 GHz Channel Planning

Review the existing 2.4 GHz channel plan and reduce co-channel interference between nearby access points.

Key areas include:

- Maintaining 20 MHz channel widths
- Using channels 1, 6, and 11 appropriately
- Reducing unnecessary channel reuse between nearby APs

### 3. Transmit Power Optimization

Review transmit power settings and determine whether reducing transmit power on selected APs can decrease excessive RF overlap.

Changes will be made gradually and validated against performance metrics.

### 4. SSID Review

Review wireless network configurations to identify unnecessary or duplicate SSID broadcasts.

Where appropriate, configurations may be consolidated to reduce management overhead and wireless airtime consumption.

### 5. RF and Airtime Analysis

Use UniFi RF tools, airtime scans, and Channel AI to evaluate:

- Channel congestion
- Neighboring wireless activity
- Interference levels
- Channel utilization
- Alternative channel assignments

### 6. 2.4 GHz AP Density Review

Evaluate whether the 2.4 GHz radio needs to remain enabled on every access point.

In higher-density environments, selected 2.4 GHz radios may be disabled if adequate coverage can be maintained by surrounding APs.

### 7. 5 GHz Optimization

Encourage compatible devices to use 5 GHz when appropriate.

This can reduce congestion on 2.4 GHz and improve overall wireless capacity.

### 8. Infrastructure Health

Review and resolve infrastructure warnings that may affect wireless performance, including:

- PoE availability
- Power delivery
- Switch port status
- AP uplink health

### 9. Performance Monitoring

Compare wireless performance before and after changes using metrics such as:

- TX retries
- RF interference
- Airtime utilization
- Signal strength
- Authentication success
- DHCP success
- DNS success
- Client connectivity

## Implementation Approach

Changes will be performed gradually rather than applied across the entire environment at once.

The process will follow this general workflow:

1. Establish baseline performance
2. Identify the highest-impact problem areas
3. Make targeted configuration changes
4. Monitor performance
5. Compare results against the baseline
6. Retain, adjust, or revert changes based on measured results

## Success Criteria

The project will be considered successful if it produces measurable improvements in:

- TX retry rates
- Airtime utilization
- Wireless interference
- Connection stability
- Client roaming
- Overall Wi-Fi reliability

## Expected Outcome

A cleaner and more efficient wireless environment with reduced retransmissions, improved spectrum utilization, and more reliable connectivity for users and devices.
