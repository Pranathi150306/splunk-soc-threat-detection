# Splunk SOC Threat Detection & Security Monitoring

## 📌 Project Overview

This project demonstrates a Security Operations Center (SOC) monitoring and threat detection workflow using Splunk.

The project focuses on ingesting security event logs, analyzing suspicious activity using SPL, creating detection queries, investigating security events, and building a SOC monitoring dashboard.

## 🎯 Objectives

- Ingest and analyze security event logs in Splunk
- Detect repeated failed login attempts
- Identify potential brute-force attacks
- Monitor successful and failed authentication activity
- Detect suspicious PowerShell activity
- Analyze DNS activity for unusual behavior
- Identify top source IP addresses and targeted users
- Build a security monitoring dashboard
- Perform basic alert investigation and incident analysis

## 🏗️ Project Architecture

```text
Security Event Logs
        ↓
   Splunk Ingestion
        ↓
   Data Parsing
        ↓
     SPL Queries
        ↓
Threat Detection Rules
        ↓
SOC Dashboard
        ↓
Security Investigation
