# DNS Log Analysis & Investigation Using Splunk

## 🎯 Project Overview

This project focuses on analyzing DNS logs using Splunk Enterprise to understand DNS traffic patterns, identify frequently queried domains, and investigate hosts generating DNS requests.

Using JSON-formatted Zeek DNS logs and Splunk Search Processing Language (SPL), this project demonstrates basic DNS monitoring and log investigation techniques used in Security Operations Center (SOC) environments.

## 🎯 Objectives

- Ingest and analyze DNS logs in Splunk.
- Identify the most frequently queried domain names.
- Find source IP addresses generating the highest DNS traffic.
- Analyze DNS query types, including A, AAAA, CNAME, and PTR.
- Practice SPL queries for DNS monitoring and investigation.

## 🖥️ Tools & Technologies

- **SIEM:** Splunk Enterprise
- **Log Format:** JSON
- **Log Source:** Zeek-style DNS logs
- **Query Language:** Splunk Search Processing Language (SPL)

## 📥 Dataset

[Download Sample DNS Logs](https://raw.githubusercontent.com/0xrajneesh/30-Days-SOC-Challenge-Beginner/refs/heads/main/dns_logs.json)

## ⚙️ Lab Setup

1. Open Splunk Web.
2. Navigate to **Settings → Add Data → Upload**.
3. Upload the downloaded DNS JSON log file.
4. Set the source type to `_json`.
5. Select or create the `dns_lab` index.
6. Finish the upload and verify that the events are searchable.

## 🔍 Investigation Tasks

### Task 1: Identify the Most Frequently Queried Domains

**Objective:** Find the domain names generating the highest number of DNS queries.

```spl
index=dns_lab sourcetype="_json"
| stats count by query
| sort -count
```

**Investigation:** Identify frequently queried domains and determine whether any require further investigation.

### Task 2: Identify the Most Active Source IP Addresses

**Objective:** Find the source IP addresses generating the highest DNS traffic.

```spl
index=dns_lab sourcetype="_json"
| stats count by id.orig_h
| sort -count
```

**Investigation:** Review the most active source IPs and investigate unusual DNS request volumes.

### Task 3: Analyze DNS Query Types

**Objective:** Understand the distribution of DNS query types.

```spl
index=dns_lab sourcetype="_json"
| stats count by qtype
| sort -count
```

**Investigation:** Compare A, AAAA, CNAME, and PTR queries to understand DNS activity patterns.

## 🛡️ Skills Demonstrated

- DNS log analysis
- Splunk and SPL queries
- DNS traffic monitoring
- Source IP investigation
- Event aggregation and analysis
- Basic SOC investigation techniques

## 🚀 Future Improvements

- Investigate unusually long or suspicious domain names.
- Analyze spikes in DNS query volume over time.
- Identify potential DNS tunneling indicators.
- Build a Splunk dashboard for DNS monitoring.
- Develop detection alerts for suspicious DNS activity.

## ✅ Conclusion

This project demonstrates how Splunk can be used to analyze DNS logs, understand query patterns, and identify hosts generating high volumes of DNS traffic. It provides hands-on experience with SIEM-based monitoring and foundational SOC investigation workflows.

**Disclaimer:** High DNS query volumes or unusual domain names are investigation leads, not proof of malicious activity. Additional evidence is required to validate suspicious behavior.
