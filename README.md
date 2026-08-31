# 5G RACH Procedure Deep-Dive

## Contention-Based Random Access Capture and Msg1–Msg4 Timing Analysis

> A practical 5G Standalone (5G SA) signalling analysis project using **UERANSIM, Open5GS and Wireshark** to investigate UE registration, Random Access-related activity, NGAP/NAS signalling, timing behaviour and multi-UE registration.

---

## 📌 Overview

The **Random Access Channel (RACH)** procedure is an important part of 5G NR because it allows a UE to establish uplink synchronisation and gain access to the network.

This project performs a practical investigation of the **5G Standalone UE registration procedure** using a simulated 5G environment consisting of:

- **UERANSIM** – 5G UE and gNB simulator
- **Open5GS** – 5G Core Network
- **Wireshark** – packet capture and protocol analysis

The experiment focuses on studying the relationship between the simulated radio-link activity and the subsequent **NGAP and NAS signalling** involved in UE registration.

Multiple UEs were configured and tested to analyse their individual registration procedures and timing behaviour.

---

# 🎯 Objectives

The main objectives of this project are:

- Simulate UE registration using UERANSIM and Open5GS
- Capture signalling traffic using Wireshark
- Observe UERANSIM Radio Link Simulation (RLS) traffic
- Analyse NGAP and NAS signalling
- Identify the `InitialUEMessage`
- Analyse the NAS `Registration Request`
- Study Authentication signalling
- Study Security Mode procedures
- Analyse Initial Context Setup
- Analyse PDU Session Resource Setup
- Perform packet timing analysis
- Configure and test multiple UEs
- Analyse multi-UE registration behaviour
- Investigate the contention-based Random Access procedure
- Document the limitations of observing physical RACH parameters in a software-based simulation

---

# 🛠️ Technology Stack

| Component | Version / Description |
|---|---|
| UERANSIM | v3.3.0 |
| Open5GS | 5G SA Core Network |
| Wireshark | 3.6.2 |
| Operating System | Ubuntu Linux |
| Virtualization | VirtualBox |
| Radio Link | UERANSIM RLS |
| Signalling | NGAP, NAS, SCTP |
| Simulation Traffic | UDP / RLS |

---

# 🏗️ System Architecture

```text
                         ┌──────────────────────┐
                         │       Open5GS        │
                         │      5G Core         │
                         │                      │
                         │ AMF / SMF / UPF etc. │
                         └──────────┬───────────┘
                                    │
                                 NGAP/SCTP
                                    │
                         ┌──────────▼───────────┐
                         │       UERANSIM       │
                         │         gNB           │
                         └──────────┬───────────┘
                                    │
                              RLS / UDP
                                    │
                ┌───────────────────┼───────────────────┐
                │                   │                   │
          ┌─────▼─────┐       ┌─────▼─────┐       ┌─────▼─────┐
          │    UE1    │       │    UE2    │       │    UE3    │
          │            │       │            │       │            │
          │ IMSI ...001│       │ IMSI ...002│       │ IMSI ...003│
          └────────────┘       └────────────┘       └────────────┘

                                    │
                                    ▼
                              ┌────────────┐
                              │ Wireshark  │
                              │  Capture   │
                              └────────────┘



