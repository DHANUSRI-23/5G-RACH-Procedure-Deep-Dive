# Multi-UE Contention Analysis

## Objective

The purpose of this experiment is to observe the behaviour of
multiple UEs attempting registration within the same simulated
5G network.

## UEs Used

| UE | SUPI |
|---|---|
| UE1 | imsi-999700000000001 |
| UE2 | imsi-999700000000002 |
| UE3 | imsi-999700000000003 |

## Observations

Three UEs were configured using separate UERANSIM configuration
files and registered with the Open5GS 5G Core.

The following RAN-UE-NGAP-ID values were observed:

| UE | RAN-UE-NGAP-ID |
|---|---:|
| UE1 | 7 |
| UE2 | 8 |
| UE3 | 9 |

Each UE generated an InitialUEMessage containing a Registration
Request.

All three UEs successfully completed the registration procedure
and established their PDU sessions.

## Contention Result

No failed registration or unresolved contention was observed during
the captured experiment.

The experiment demonstrates successful multi-UE registration in the
UERANSIM/Open5GS environment.

Physical PRACH collision parameters such as preamble collision and
RA-RNTI values were not directly available in the captured NGAP
traffic and therefore were not inferred.
