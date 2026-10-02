# Splunk SOC Threat Detection & Security Monitoring

## 📌 Project Overview

This project demonstrates a Security Operations Center (SOC) monitoring and threat detection workflow using **Splunk**.

The project focuses on ingesting security logs, analyzing suspicious activity using **SPL (Search Processing Language)**, performing security investigations, and building a SOC monitoring dashboard.

## 🎯 Objectives

* Ingest and analyze security event logs in Splunk
* Detect repeated failed login attempts
* Identify potential brute-force authentication activity
* Monitor successful and failed authentication events
* Analyze PowerShell activity
* Investigate PowerShell parent processes
* Analyze DNS activity
* Analyze firewall traffic
* Analyze Sysmon events
* Build a SOC security monitoring dashboard
* Document a security investigation using an incident report

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
 Threat Detection
        ↓
Security Investigation
        ↓
   SOC Dashboard
        ↓
 Incident Documentation
```

## 📂 Log Sources

The project uses multiple security datasets for analysis:

* Windows Security Logs
* Linux Authentication Logs
* PowerShell Logs
* DNS Logs
* Firewall Logs
* Sysmon Events
* VPN Logs
* Proxy Logs
* Email Logs
* File Access Logs
* USB Activity Logs
* User Account Logs
* System Logs
* Cron Logs

## 🔎 Security Detections & Analysis

### 1. Brute-Force Authentication Detection

Repeated failed authentication attempts were analyzed using Splunk.

The investigation identified:

* **Source IP:** `203.0.113.50`
* **Failed attempts:** `300`
* **Detection threshold:** 5 or more failed attempts

The activity was documented as a potential brute-force authentication event for further investigation.

### 2. PowerShell Activity Analysis

PowerShell process activity was analyzed to identify:

* Users running PowerShell
* Computers associated with the activity
* Source IP information where available
* Parent processes launching PowerShell

Parent-process analysis included processes such as:

* `svchost`
* `cmd`
* `explorer`
* `powershell`

This provides additional context for SOC investigation.

### 3. DNS Activity Analysis

DNS logs were analyzed to identify:

* Frequently requested domains
* High-volume DNS queries
* Source IP addresses associated with DNS activity

High-volume DNS activity was treated as an investigation signal rather than automatically classified as malicious.

### 4. Firewall Traffic Analysis

Firewall logs were analyzed to identify:

* Source IP addresses
* Destination IP addresses
* Destination ports
* Protocols
* Connection volume

High-volume connection activity was investigated as a potential security signal.

### 5. Sysmon Event Analysis

Sysmon events were analyzed by Event ID.

The dataset contained several Event IDs, including:

* Event ID 1 — Process Creation
* Event ID 3 — Network Connection
* Event ID 7 — Image Loaded
* Event ID 10 — Process Access
* Event ID 11 — File Creation

The available extracted fields were used for event-level analysis.

## 📊 SOC Security Monitoring Dashboard

A SOC monitoring dashboard was created in Splunk containing:

1. **Total Security Events**
2. **Failed Login Events**
3. **Successful Login Events**
4. **Top Source IPs**
5. **Top Users**
6. **Events Over Time**
7. **PowerShell Parent Processes**

The dashboard provides a centralized view of security activity for SOC monitoring and investigation.

## 🚨 Incident Investigation

A brute-force authentication investigation was performed using Splunk.

The investigation identified **300 failed authentication attempts** from the source IP:

```text
203.0.113.50
```

The investigation included:

* Searching authentication logs
* Extracting source IP information
* Counting failed authentication attempts
* Applying a detection threshold
* Reviewing the investigation results
* Documenting the findings

The complete investigation is available in:

```text
incident-reports/brute-force-investigation.md
```

## 📸 Project Evidence

Screenshots from the lab are stored in:

```text
screenshots/
```

Important evidence includes:

* Splunk Home
* Windows Security Log ingestion
* Authentication events
* Brute-force investigation
* PowerShell analysis
* DNS analysis
* Firewall analysis
* Sysmon analysis
* SOC dashboard

## 🧰 Tools & Technologies

* **Splunk Enterprise**
* **SPL**
* **Linux**
* **Windows**
* **Sysmon**
* **Security Event Logs**
* **Git & GitHub**

## 📁 Repository Structure

```text
splunk-soc-threat-detection/
│
├── data/
│   ├── auth.log
│   ├── cron.log
│   ├── dns_logs.csv
│   ├── email_logs.csv
│   ├── file_access_logs.csv
│   ├── firewall_logs.csv
│   ├── powershell_logs.csv
│   ├── proxy_logs.csv
│   ├── syslog.log
│   ├── sysmon_events.csv
│   ├── usb_activity_logs.csv
│   ├── user_accounts.csv
│   ├── vpn_logs.csv
│   └── windows_security_logs.csv
│
├── spl/
│   └── detections/
│
├── dashboard/
│
├── screenshots/
│
├── incident-reports/
│   └── brute-force-investigation.md
│
└── README.md
```

## 📚 What I Learned

Through this project, I practiced:

* Security log ingestion
* SPL searching and filtering
* Field extraction
* Event aggregation
* Authentication monitoring
* Brute-force detection
* PowerShell investigation
* DNS analysis
* Firewall traffic analysis
* Sysmon event analysis
* SOC dashboard creation
* Security incident documentation

## ⚠️ Disclaimer

This project was created as a **cybersecurity learning and portfolio lab** using sample security datasets.

The IP addresses and security events shown in the dataset are used for lab and analysis purposes and should not be interpreted as evidence of real-world malicious activity.

## 👩‍💻 Author

**Pranathi**

BTech Student | Aspiring SOC Analyst

GitHub: `https://github.com/Pranathi150306`
