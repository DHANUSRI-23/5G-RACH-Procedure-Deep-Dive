# NGAP and NAS Signalling Analysis

## InitialUEMessage

The first observable NGAP message for each UE is an
InitialUEMessage.

The message contains:

- RAN-UE-NGAP-ID
- NAS-PDU
- User Location Information
- RRC Establishment Cause
- UE Context Request

The NAS-PDU contains a 5GS Registration Request.

## RRC Establishment Cause

The captured InitialUEMessage contains:

```text
RRCEstablishmentCause: mo-Signalling
