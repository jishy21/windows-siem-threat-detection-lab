# Incident Report: Administrator Group Membership Change Detection

## Incident Summary

A local user account was added to the Administrators group on the Windows client and successfully detected in Splunk.

## Event ID

4732

## Affected Host

WIN-CLIENT01

## Severity

High

## Detection Method

Splunk Search Query:

```spl
EventCode=4732
