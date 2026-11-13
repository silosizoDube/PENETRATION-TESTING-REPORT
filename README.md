# PENETRATION-TESTING-REPORT

# PENETRATION TESTING REPORT
## FOOTPRINTING & NETWORK SCANNING PHASES

**W2-PM-FINAL | CYBERSECURITY | NETWORKWALKS**

---

## Student Information

| Field | Details |
|---|---|
| Pentester Name | Silosizo L B Dube |
| Program/Batch | B084 – Networkwalks |
| Report Date | 13 November 2026 |
| Modules Completed | W2-PM1 and W2-PM5 |
| Client/Target | networkwalks.com and my own local LAN |
| Permission Secured | Yes |

### Phases Covered

- Phase 1: Reconnaissance and Footprinting – Completed
- Phase 2: Scanning and Network Discovery – Completed
- Phases 3–5: Not covered in this report

---

## 1. Liability Disclaimer

I performed these activities only on systems and networks for which I had authorization or which I personally own. The activities were conducted for educational and research purposes as part of my cybersecurity training.

The information in this report must not be used to access, damage, or interfere with systems without permission. Unauthorized access may have legal consequences. All testing was limited to the authorized educational scope.

## 2. Introduction

This report documents practical cybersecurity activities completed during Week 2 of my Cybersecurity and Ethical Hacking internship at Networkwalks.

The report covers two modules:

- **W2-PM1:** Footprinting and reconnaissance of networkwalks.com using multiple Kali Linux tools.
- **W2-PM5:** Network scanning and host discovery on my own local network using Zenmap.

The footprinting exercise involved collecting publicly available domain, DNS, website technology, and HTTP information. The network scanning exercise involved identifying my local IP address and subnet, discovering live hosts, recording IP and MAC addresses, and generating a network topology.

These activities helped me understand how reconnaissance and network discovery contribute to the early stages of a penetration test.

## 3. Tools Used

| Tool | Purpose |
|---|---|
| Kali Linux | Operating system used for footprinting activities |
| WHOIS | Retrieves publicly available domain registration information |
| WhatWeb | Identifies website technologies |
| Nslookup | Resolves domain names through DNS |
| Curl | Retrieves HTTP response headers |
| Wafw00f | Checks for web application firewall identification |
| DNSRecon | Collects DNS record information |
| Zenmap (Nmap GUI) | Discovers live hosts on a network |
| Windows Command Prompt | Identifies local IP and MAC addresses |

## 4. Activities Performed

### 4.1 Footprinting and Reconnaissance – W2-PM1

I performed reconnaissance against the authorized educational target, networkwalks.com, using six Kali Linux tools.

### 4.1.1 WHOIS

I used WHOIS to retrieve publicly available domain registration information, including domain-related registration and name server details.

**Command used:**

```bash
whois networkwalks.com > whois-results.txt
```

The output was saved for documentation and later review.

**Evidence:** WHOIS screenshot to be added.

### 4.1.2 WhatWeb

I used WhatWeb to identify technologies exposed by the target website.

**Command used:**

```bash
whatweb networkwalks.com > whatweb-results.txt
```

The results identified WordPress 7.0.4 and WP Download Manager 3.3.58, along with other website technology information.

This showed how technology fingerprinting can help a security professional understand the software environment exposed by a website.

**Evidence:** WhatWeb screenshot to be added.

### 4.1.3 Nslookup

I used Nslookup to resolve the domain name and identify its IP address.

**Command used:**

```bash
nslookup networkwalks.com > nslookup-results.txt
```

The result identified the IP address:

**192.232.216.135**

This demonstrated how DNS lookup can reveal the IP address associated with a domain.

**Evidence:** Nslookup screenshot to be added.

### 4.1.4 Curl

I used Curl with the `-I` option to inspect the HTTP response headers.

**Command used:**

```bash
curl -I https://networkwalks.com > curl-results.txt
```

The response provided HTTP header information and exposed the WordPress REST API endpoint `/wp-json/`.

This helped demonstrate how HTTP response information can reveal details about a web application.

**Evidence:** Curl screenshot to be added.

### 4.1.5 Wafw00f

I used Wafw00f to check whether a Web Application Firewall could be identified on the target website.

**Command used:**

```bash
wafw00f https://networkwalks.com > wafw00f-results.txt
```

The result identified ModSecurity (SpiderLabs).

This demonstrated how a security professional can identify information about a website's web application firewall.

**Evidence:** Wafw00f screenshot to be added.

### 4.1.6 DNSRecon

I used DNSRecon to collect DNS-related information about the target domain.

**Command used:**

```bash
dnsrecon -d networkwalks.com > dnsrecon-results.txt
```

The results were saved for review and documentation. DNS reconnaissance helps identify publicly available DNS information, such as name servers and mail-related records.

**Evidence:** DNSRecon screenshot to be added.

### 4.2 Network Scanning with Zenmap – W2-PM5

For this practical, I used Zenmap on my Windows 11 computer to discover active devices on my own local network.

### 4.2.1 Installation

I downloaded and installed Zenmap on my Windows PC.

### 4.2.2 Identifying My Local IP Address and Subnet

I used the Windows command:

```cmd
ipconfig
```

The results showed:

| Network Detail | Actual Result |
|---|---|
| Local IPv4 address | 192.168.1.xxx |
| Subnet mask | 255.255.255.0 |
| LAN subnet | 192.168.1.0/24 |

### 4.2.3 Discovering Live Hosts

I entered my LAN subnet into Zenmap and performed a Ping Scan to identify active hosts.

The scan identified three live hosts.

**Total live hosts discovered: 3**

For this public report, the private network addresses are masked.

**Evidence:** Zenmap scan screenshot to be added.

### 4.2.4 Identifying MAC Addresses

I used the scan information and Windows network configuration details to document the MAC addresses associated with the discovered hosts.

I used the following command to obtain my computer's adapter information:

```cmd
ipconfig /all
```

Private MAC addresses have been masked in this public report.

| Device | MAC Address |
|---|---|
| Discovered host 1 | XX:XX:XX:XX:XX:XX |
| Discovered host 2 | XX:XX:XX:XX:XX:XX |
| My Windows computer | XX:XX:XX:XX:XX:XX |

**Evidence:** Relevant MAC address screenshot to be added, with private details redacted.

### 4.2.5 Network Topology

After completing the scan, I opened the Topology section in Zenmap, enabled the legend, and saved the network topology as a PDF.

The topology provided a visual representation of the discovered network hosts.

**Evidence:** Zenmap topology image to be added.

## 5. Risk Analysis and Impact

The following table summarizes potential security observations from the exercises.

| No. | Finding | Evidence / Observation | Potential Impact | Risk |
|---|---|---|---|---|
| 1 | Website technology information exposed | WhatWeb identified WordPress and WP Download Manager | May help attackers identify software versions for further security research | Medium |
| 2 | Website IP address identifiable | Nslookup returned 192.232.216.135 | Helps identify the IP address associated with the domain | Low |
| 3 | HTTP technical information exposed | Curl returned response headers and the /wp-json/ endpoint | May assist technology fingerprinting | Low |
| 4 | WAF technology identifiable | Wafw00f identified ModSecurity (SpiderLabs) | Reveals information about the website's security architecture | Low |
| 5 | DNS information available | DNSRecon collected DNS-related records | Helps build an understanding of the domain's infrastructure | Medium |
| 6 | Multiple live devices discovered | Zenmap identified three live hosts on my LAN | Unexpected devices may require investigation | Medium |

**Risk assessment note:** These are potential risks based on information gathered during reconnaissance and network discovery. They are not confirmed vulnerabilities. No exploitation or vulnerability validation was performed during these exercises.

## 6. Recommendations

Based on the observations, I recommend the following security practices:

1. **Review exposed website technologies:** Regularly review information publicly exposed about website platforms, plugins, and versions.
2. **Keep software updated:** Maintain current versions of content management systems, plugins, and other software.
3. **Review HTTP response headers:** Check whether unnecessary technical information is being disclosed.
4. **Review DNS records:** Periodically verify that DNS records are accurate and that only required services are exposed.
5. **Maintain WAF protection:** Keep web application firewall protections properly configured, updated, and monitored.
6. **Perform regular network discovery:** Scan owned or authorized networks to maintain an accurate inventory of active devices.
7. **Investigate unknown devices:** Verify unexpected devices discovered during network scans.
8. **Maintain network documentation:** Keep network addresses, device records, and topology information updated.
9. **Test only with authorization:** Ensure all reconnaissance and scanning activities remain within an approved scope.

## 7. Conclusion

During Week 2 of my Cybersecurity and Ethical Hacking internship at Networkwalks, I completed practical activities covering footprinting, reconnaissance, and network scanning.

In W2-PM1, I used six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon. These tools helped me understand how publicly available domain information, DNS records, website technologies, HTTP headers, and web application firewall information can be collected.

In W2-PM5, I used Zenmap to scan my own local network. I identified my local IP address and subnet, discovered three live hosts, recorded their IP and MAC addresses, and generated a network topology PDF.

These practical exercises improved my understanding of the information-gathering and network-discovery stages of penetration testing. I also learned the importance of documenting findings, assessing potential risks carefully, and following authorization requirements throughout security testing.

## 8. Evidence Collected

The following evidence will be uploaded to this repository.

| Figure | Evidence Description |
|---|---|
| 1 | WHOIS results |
| 2 | WhatWeb results |
| 3 | Nslookup results |
| 4 | Curl HTTP response results |
| 5 | Wafw00f results |
| 6 | DNSRecon results |
| 7 | Windows ipconfig output |
| 8 | Zenmap scan showing three live hosts |
| 9 | MAC address evidence |
| 10 | Zenmap network topology |

Screenshots will be added to the repository and linked in this section.

---<img width="1366" height="643" alt="image" src="https://github.com/user-attachments/assets/c3e39cb3-019b-4c54-8e78-b0135c58ec76" />

<img width="1366" height="643" alt="image" src="https://github.com/user-attachments/assets/293d0995-b600-4d37-bbb4-71907e615398" />
<img width="1366" height="643" alt="image" src="https://github.com/user-attachments/assets/3b9b7b41-c3e0-46a9-a4d3-2d7dea1a5c77" />
<img width="1366" height="643" alt="image" src="https://github.com/user-attachments/assets/a0630064-1092-43b9-bde6-728403f99e15" />
<img width="1366" height="643" alt="image" src="https://github.com/user-attachments/assets/fef472b7-93b4-44cc-b9c3-2602075fd73b" />
<img width="1366" height="643" alt="image" src="https://github.com/user-attachments/assets/ffc2890e-0e70-48a0-aba1-9deae8d137f2" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/4132dcea-c685-44d1-8254-b8811af86b6c" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/0d30a0ac-b4cf-471d-8a39-26784f4cf966" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/00308a11-2331-44e5-b3fd-ea41b7de4e71" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/3329d329-2ed6-4395-a784-f1f4cd2344d3" />

## Author

**Name:** Silosizo L B Dube

**Program/Batch:** B084 – Networkwalks

**LinkedIn:** [Silosizo Dube](https://www.linkedin.com/in/silosizo-dube-5523a9210/)

**Program:** Cybersecurity and Ethical Hacking Internship

**Project Information:** Networkwalks Cybersecurity Program | Week 02 | GitHub

---

**End of Report**
