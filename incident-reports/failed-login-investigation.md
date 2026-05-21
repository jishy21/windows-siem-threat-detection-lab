# Incident Report: Failed Login Detection

## Incident Summary

Multiple failed login attempts were generated on the Windows client and successfully detected in Splunk using Windows Security Event logs.

## Event ID

4625

## Affected Host

WIN-CLIENT01

## Severity

Medium

## Detection Method

Splunk Search Query:

```spl
EventCode=4625
