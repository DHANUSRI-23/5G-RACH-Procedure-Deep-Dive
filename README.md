# 5G RACH Procedure Deep-Dive

## Contention-Based Random Access Capture and Msg1–Msg4 Timing Analysis

## Overview

This project investigates the 5G Standalone (5G SA) UE registration
procedure using UERANSIM and Open5GS.

Wireshark is used to capture and analyse the signalling traffic,
including NGAP, NAS and UERANSIM Radio Link Simulation (RLS) traffic.

The project focuses on understanding the relationship between the
contention-based Random Access procedure and the subsequent UE
registration signalling.

---

## Objectives

- Trigger UE registration using UERANSIM and Open5GS
- Capture NGAP and NAS signalling using Wireshark
- Observe UERANSIM Radio Link Simulation traffic
- Analyse the InitialUEMessage and Registration Request
- Analyse signalling timing
- Configure and test multiple UEs
- Study multi-UE registration behaviour
- Document the limitations of observing physical RACH parameters
  through a simulated software stack

---

## Technology Stack

| Component | Version / Description |
|---|---|
| UERANSIM | v3.3.0 |
| Open5GS | 5G SA Core |
| Wireshark | 3.6.2 |
| Operating System | Ubuntu |
| Radio Link | UERANSIM RLS |
| Protocols | NGAP, NAS, SCTP, RLS |

---

## Network Configuration

### gNB

```text
MCC: 999
MNC: 70
TAC: 1
gNB IP: 127.0.0.1
AMF IP: 127.0.0.5
AMF Port: 38412


### UE Configuration

Three UEs were configured for the experiment:

| UE | SUPI |
|---|---|
| UE1 | imsi-999700000000001 |
| UE2 | imsi-999700000000002 |
| UE3 | imsi-999700000000003 |

All UEs use MCC `999`, MNC `70`, and the same test subscription credentials configured in Open5GS.

---

## Setup

### 1. Start Open5GS

Verify that the required Open5GS services are running:

```bash
sudo systemctl --type=service | grep open5gs
