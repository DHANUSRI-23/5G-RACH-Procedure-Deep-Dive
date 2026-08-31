# RACH and Registration Timing Analysis

## Objective

The objective of this experiment is to analyse the 5G SA UE
registration procedure using UERANSIM and Open5GS and to study the
associated signalling timing using Wireshark.

## Experimental Setup

- UERANSIM version: 3.3.0
- Open5GS: 5G Core Network
- Wireshark version: 3.6.2
- Radio Link: UERANSIM Radio Link Simulation (RLS)
- gNB address: 127.0.0.1
- AMF address: 127.0.0.5
- Number of UEs: 3

## UE Configuration

| UE | SUPI |
|---|---|
| UE1 | imsi-999700000000001 |
| UE2 | imsi-999700000000002 |
| UE3 | imsi-999700000000003 |

## Observed Initial UE Messages

| UE | Packet Number | Time (s) | RAN-UE-NGAP-ID |
|---|---:|---:|---:|
| UE1 | 429 | 32.135579695 | 7 |
| UE2 | 1112 | 43.203860449 | 8 |
| UE3 | 1697 | 53.624117052 | 9 |

## Observed NGAP/NAS Signalling

The following signalling messages were observed in the Wireshark
capture:

1. InitialUEMessage – Registration Request
2. DownlinkNASTransport – Authentication Request
3. UplinkNASTransport – Authentication Response
4. DownlinkNASTransport – Security Mode Command
5. UplinkNASTransport
6. InitialContextSetupRequest
7. InitialContextSetupResponse
8. UplinkNASTransport
9. DownlinkNASTransport
10. PDUSessionResourceSetupRequest
11. PDUSessionResourceSetupResponse

## Timing Observation

The Wireshark timestamps were used to determine the timing of the
observable NGAP/NAS signalling messages.

The packet capture operates on the simulated localhost interfaces,
therefore the measured times represent the simulated software-stack
signalling rather than over-the-air radio propagation delays.

## RACH Observation

The theoretical 4-step contention-based RACH procedure consists of:

- Msg1 – Random Access Preamble
- Msg2 – Random Access Response
- Msg3 – RRC message
- Msg4 – RRC Contention Resolution

The UERANSIM Radio Link Simulation traffic was captured separately
from the NGAP/NAS signalling.

The NGAP capture does not directly expose physical-layer PRACH
parameters such as the RA-RNTI and preamble index. Therefore, these
values were not inferred or fabricated from the NGAP packets.

## Conclusion

The experiment successfully captured the signalling associated with
three UE registration procedures and allowed the timing of the
observable NGAP/NAS messages to be analysed.
