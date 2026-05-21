
---

### `successful-login-investigation.md`

```markdown id="c8m88f"
# Incident Report: Successful Login Detection

## Incident Summary

Successful user authentication activity was generated on the Windows client and detected in Splunk using Windows Security logs.

## Event ID

4624

## Affected Host

WIN-CLIENT01

## Severity

Informational

## Detection Method

Splunk Search Query:

```spl
EventCode=4624
