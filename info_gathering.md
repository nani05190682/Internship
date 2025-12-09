Here is a **reformatted, clean, and real-time–example–based** version of your content.

---

# **Information Gathering – With Real-Time Examples**

## **Objectives**

After completing this reading, you will be able to:

* Identify and describe information gathering, forensic, and vulnerability analysis tools provided in Kali Linux
* Understand how these tools are used in **real-world pentesting scenarios**

---

# **Introduction**

Kali Linux provides a rich set of tools widely used by security professionals, penetration testers, and ethical hackers.
This chapter focuses on tools used for:

* Internet reconnaissance (OSINT)
* Social engineering
* Network scanning

Each tool includes a **real-time example** to help you understand how it works in practical scenarios.

---

# **1. Internet Information Gathering**

| Tool Name        | Interface    | Description                                                                                     | Real-Time Example                                                                                                        |
| ---------------- | ------------ | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **theHarvester** | Command line | Collects emails, subdomains, and hostnames from public sources like Google, Bing, and LinkedIn. | Use it to find exposed emails of a target company during reconnaissance: `theharvester -d example.com -b google`         |
| **Maltego**      | GUI          | Visual tool to map relationships between domains, IPs, people, emails, etc.                     | Investigate a phishing domain by visually identifying related social media accounts, DNS records, and hosting providers. |
| **Recon-ng**     | Command line | A modular framework to collect OSINT data automatically.                                        | Automatically pull data from APIs (Shodan, GitHub, social networks) to build a complete report about a target company.   |
| **Whois**        | Command line | Retrieves domain registration details such as owner name, registrar, and contact information.   | Check who registered `example.com` to analyze whether it's a suspicious domain used in phishing.                         |
| **Dig**          | Command line | Retrieves DNS records like A, MX, TXT, and CNAME.                                               | `dig example.com MX` to identify mail servers for a domain—useful in email spoofing analysis.                            |

---

# **2. Social Engineering Attacks**

| Tool Name                                 | Interface    | Description                                                                       | Real-Time Example                                                                                                      |
| ----------------------------------------- | ------------ | --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Social Engineering Toolkit (SET)**      | Command line | Framework for phishing, fake login pages, credential harvesting, and USB attacks. | Create a fake “Office365 login page” to test how many employees fall for credential harvesting (authorized test only). |
| **BeEF (Browser Exploitation Framework)** | GUI          | Exploits browser weaknesses to control victims' browsers.                         | Hook a vulnerable browser and force it to display warnings, take screenshots, or detect internal network IPs.          |

---

# **3. Network Host Scanning Tools**

| Tool Name       | Interface    | Description                                                          | Real-Time Example                                                                                        |
| --------------- | ------------ | -------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Nmap**        | Command line | Discovers hosts, open ports, OS fingerprinting, service enumeration. | `nmap -sV 192.168.1.10` to find open ports and services running on a server during penetration testing.  |
| **Netdiscover** | Command line | Identifies live hosts on a local network using ARP requests.         | Useful when joining a new network to list all active devices without sending noisy scans.                |
| **Masscan**     | Command line | Extremely fast port scanner.                                         | Scan the entire corporate subnet in seconds to identify exposed services: `masscan 10.0.0.0/8 -p80,443`. |
| **Wireshark**   | GUI          | Captures and analyzes packets in real time.                          | Capture packets to identify clear-text passwords, DNS queries, or malicious traffic patterns.            |
| **Ping**        | Command line | Tests connectivity with ICMP packets.                                | `ping 8.8.8.8` to verify if internet connectivity is available.                                          |
| **ARP-scan**    | Command line | Sends ARP broadcasts to map IP–MAC addresses.                        | Detect unknown devices connected inside the office LAN that may indicate unauthorized access.            |
| **Zenmap**      | GUI          | Graphical version of Nmap for easy scanning and visualization.       | Quickly map a network and generate graphical topology diagrams for reporting.                            |

---

# **Disclaimer**

Always perform information gathering or scanning activities **only with proper authorization** from the network owner.
Unauthorized scanning is illegal and unethical.

---

# **Summary**

In this chapter, you learned:

* Key information-gathering tools in Kali Linux and how they work
* Social engineering tools used for phishing and browser exploitation
* Network scanning tools for identifying hosts, services, and vulnerabilities
* Real-time examples showing how cybersecurity professionals use these tools during assessments


---

