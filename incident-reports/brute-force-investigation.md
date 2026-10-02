# Brute-Force Authentication Investigation

## 1. Incident Summary

A high number of failed authentication attempts were detected in the Splunk SOC monitoring lab.

The investigation identified **300 failed login attempts** from the source IP address **203.0.113.50**.

This activity was investigated as a potential brute-force authentication attempt.

## 2. Detection Method

Authentication logs were ingested into Splunk and analyzed for repeated failed login attempts.

### Splunk Detection Query

```spl
index=main sourcetype=syslog
| search ("Failed password" OR "authentication failure" OR "Failed login")
| rex "from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
| stats count as failed_attempts min(_time) as first_seen max(_time) as last_seen by src_ip
| where failed_attempts >= 5
| convert ctime(first_seen) ctime(last_seen)
| sort -failed_attempts
```

## 3. Investigation Findings

| Field               | Finding                              |
| ------------------- | ------------------------------------ |
| Source IP           | 203.0.113.50                         |
| Failed Attempts     | 300                                  |
| Log Source          | auth.log                             |
| Detection Type      | Potential brute-force authentication |
| Detection Threshold | 5 or more failed attempts            |

## 4. Investigation Process

1. Authentication logs were ingested into Splunk.
2. Failed authentication events were searched.
3. Source IP addresses were extracted from the events.
4. Failed attempts were counted for each source IP.
5. A threshold of 5 or more failed attempts was used for detection.
6. The source IP 203.0.113.50 was identified with 300 failed attempts.
7. The activity was flagged for further investigation.

## 5. Recommended SOC Response

* Review the authentication timeline.
* Check whether a successful login occurred after the failed attempts.
* Investigate the targeted account if account information is available.
* Review other logs for activity from the same source IP.
* Apply appropriate security controls according to the organization's procedures.
* Document the investigation and evidence.

## 6. Evidence

Splunk investigation screenshot:

`24-bruteforce-final-investigation.png`

The screenshot shows the source IP and the number of failed authentication attempts identified during the investigation.

## 7. Conclusion

The Splunk investigation identified **300 failed authentication attempts** from **203.0.113.50**.

The activity meets the lab's defined threshold for potential brute-force activity. Further investigation would be required to determine whether the activity resulted in a successful compromise.
