# **🔎 PhantomCheck**

**Platform:** HackTheBox Sherlock / DFIR  
**Category:** Incident Investigation / SOC / Blue Team  
**Date:** 2025-04-09  
**MITRE ATT&CK:** 

---

## **🎯 Objective**

Brief explanation of what you aimed to determine:

> Identify the root cause of the incident, analyze the attacker’s activity, build a complete timeline, extract indicators, and provide actionable mitigation recommendations.

---

## **📘 Executive Summary**

A high-level summary for recruiters/managers:

> During this investigation, I analyzed multiple evidence sources including Windows Event Logs, network data, and system artifacts. The attacker gained access through **[initial vector]**, executed **[malicious activity]**, and attempted **[objective]**.
> 
> Using tools such as Sigma, Zeek, Volatility, and artifact triage, I reconstructed the attack flow and identified key MITRE ATT&CK techniques.

---

## **🛠 Tools & Techniques**

List only the ones used:

- **Zeek** – Network traffic analysis
    
- **Sigma / Hayabusa** – Windows log analytics
    
- **Volatility 2/3** – Memory forensics
    
- **YARA** – Malware/IOC scanning
    
- **CyberChef** – Decoding/analysis
    
- **ripgrep / fzf** – Fast log searching
    
- **jq** – JSON processing
    

---

## **🔬 Methodology**

Describe your investigation flow:

1. Evidence collection
    
2. Initial triage
    
3. IOC extraction
    
4. Log correlation & enrichment
    
5. MITRE ATT&CK mapping
    
6. Timeline construction
    
7. Root cause analysis
    
8. Mitigation recommendations
    

---

## **📅 Attack Timeline**

Use a simple table:

|Time|Event|Evidence|
|---|---|---|
|06:31:39|Failed login attempts|Event ID 4625|
|06:31:40|Successful login|Event ID 4624|
|06:32:10|Suspicious PowerShell executed|Event ID 4104|
|06:33:45|User account created|Event ID 4720|

---

## **🧠 Technical Analysis**

Describe the deep dive. Example structure:

### **1. Initial Access**

- Evidence: Event ID XXX, network logs, etc.
    
- MITRE: **TXXXX – Technique Name**
    
- Explanation of what it means.
    

### **2. Execution**

- PowerShell commands, scripts, payloads
    
- MITRE mapping
    

### **3. Persistence**

- Registry keys, scheduled tasks, new users
    

### **4. Lateral Movement / Priv Esc**

- RDP, SMB, stolen credentials…
    

### **5. Impact**

- Data exfil, backdoor, configuration changes
    

---

## **📁 Evidence**

Provide:

- Screenshots (`/screenshots/`)
    
- Important log excerpts
    
- IOC lists
    
- Decoded/deobfuscated content
    

Add small labeled sections, like:

`Event ID 4624 (User Login) Account Name: Administrator Source IP: 65.2.161.68`

---

## **🧩 MITRE ATT&CK Mapping**

|Phase|Technique ID|Technique Name|Evidence|
|---|---|---|---|
|Execution|T1059.001|PowerShell|Event ID 4104|
|Credential Access|T1110|Brute Force|Event ID 4625|
|Persistence|T1547|Registry Run Keys|HKCU\Software\…|

---

## **📌 Indicators of Compromise (IOCs)**

### **IPs**

- `65.2.161.68`
    

### **Domains**

- `malicious-domain[.]xyz`
    

### **Hashes**

- SHA256: `xxxxxxxx...`
    

---

## **🛡 Recommendations**

### **Detection**

- Create Sigma rule for EventID 4104 with download-string patterns
    
- Monitor abnormal login spikes
    
- Alert on new user creation (EventID 4720)
    

### **Hardening**

- Enforce MFA
    
- Restrict PowerShell script execution
    
- Apply least privilege policies
    
- Block malicious IOCs in firewall/EDR
    

---

## **📄 Report**

Include your final PDF:

➡️ **`Final_Report.pdf`**