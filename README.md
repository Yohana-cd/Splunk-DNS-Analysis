# 🧠 Splunk DNS Log Analysis

## 🔹 Overview
This project demonstrates how to analyze **DNS logs** using **Splunk Enterprise** to detect anomalies and identify potential security threats in network activity.  
It was completed in **Kali Linux (VMware environment)** as part of my cybersecurity learning and lab practice.

---

## ⚙️ Tools & Environment
- **Operating System:** Kali Linux 2025.1 (VMware Workstation)
- **Software:** Splunk Enterprise 10.0.1 (Linux version)
- **Data Source:** DNS log file (`dns.log.gz`)
- **Goal:** Detect anomalies in DNS traffic using Splunk dashboards and searches.

---

## 🧩 Steps Performed
1. Installed **Splunk Enterprise** on Kali Linux.  
2. Started the Splunk service and created an admin account.  
3. Uploaded the DNS log file `dns.log.gz` as the data source.  
4. Configured the source type and indexed data as `dns_lab`.  
5. Used **search queries** to analyze DNS activity and detect unusual behavior.  
6. Created **field extractions** for `timestamp`, `src_ip`, and `domain`.  
7. Built a **dashboard** to visualize DNS query traffic and detect potential anomalies.

---

## 🔍 Example Search Queries

**Basic query to view DNS events:**
```spl
index="dns_lab" | head 5
```

---

## Query to analyze DNS query volume by IP and domain:
```spl
index="dns_lab" | stats count by src_ip, domain
```

---

## Query to detect failed DNS lookups (NXDOMAIN responses):
```spl
index="dns_lab" "NXDOMAIN" | stats count by domain | sort -count
```

---

## 📊 Dashboard: DNS Threat Analysis

**Objective:**  
Visualize DNS query traffic to identify source IPs generating excessive or suspicious DNS requests.

**Query Used:**
```spl
index=dns_lab | stats count by src_ip, domain
```

**Result:**  
The dashboard highlights spikes in query activity by specific hosts, allowing quick detection of potential C2 communications, data exfiltration, or DNS tunneling attempts.

📸 **Screenshot:**  
![Dashboard](screenshots/dns_threat_analysis.png)

---

## 🧠 Key Findings
- Identified abnormal spikes in DNS queries from specific source IPs.  
- Detected NXDOMAIN errors that could indicate communication with malicious or unreachable domains.  
- Built a Splunk dashboard to continuously monitor DNS behavior for threat hunting.  

---

## 📸 Additional Screenshots
| Splunk Dashboard | Query Results |
|------------------|----------------|
| ![Dashboard] | ![Query](screenshots/query_results.png) |

---

## 🗂️ Folder Structure
```
Splunk-DNS-Analysis/
│
├── README.md
├── screenshots/
│   ├── splunk_dashboard.png
│   ├── query_results.png
│   └── dns_threat_analysis.png
└── dns.log.gz
```

---

## 🧾 Summary
This project showcases the use of Splunk Enterprise for network traffic monitoring and threat detection.  
By analyzing DNS logs, I was able to visualize patterns, detect anomalies, and strengthen my understanding of SIEM analysis and threat hunting techniques in a real-world environment.

---

👩‍💻 **Created by:** [Yohana Contreras](https://linkedin.com/in/Yohana-Contreras-g)  
📧 **Email:** yohana.cgp29@gmail.com  
💼 **GitHub:** [Yohana-cd](https://github.com/Yohana-cd)

