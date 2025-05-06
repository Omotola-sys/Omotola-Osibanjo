# Omotola-Osibanjo
# Socra Tech, a rapidly expanding technology solutions provider, has identified an alarming increase in suspicious network activity. This concerning development has raised significant red flags about potential unauthorized access, malware infections, and insider threats within their systems.
# This report summarizes the findings of proposed security improvements and present recommendations and mitigation measures to Socra Tech. 
# Socra Tech
## Security Operations Center (SOC) analysis report
## Prepared by: Omotola Osibanjo
## Date: April 25,2025.
# TABLE OF CONTENTS
# •	EXECUTIVE SUMMARY
# •	TOOLS USED
# •	PHASE 1: Wireshark – Network Traffic Capture & Analysis 
# •	PHASE 1: FINDINGS AND IMPACT
# •	PHASE 2: pfSense – Firewall & Policy Enforcement
# •	PHASE 2: FINDINGS AND IMPACT
# •	PHASE 3: Wazuh – Security Event Monitoring & Response
# •	PHASE 3: FINDINGS AND IMPACT
# •	Recommendations and conclusions
EXECUTIVE SUMMARY: SOCRA TECH SECURITY
•	Socra Tech, a rapidly expanding technology solutions provider, has identified an alarming increase in suspicious network activity, raising concerns about potential unauthorized access, malware infections, and insider threats. To address these challenges effectively, an in-depth investigation has been conducted using cutting-edge tools including Wireshark, pfSense, and Wazuh.
•	The findings highlight vulnerabilities in network infrastructure, such as anomalies in traffic patterns suggesting unauthorized access attempts and potential malware presence. Additionally, monitoring tools flagged unusual user behavior, suggesting the possibility of insider threats. These risks, if left unaddressed, could compromise Socra Tech’s operational integrity, data confidentiality, and customer trust.
•	This report summarizes the findings of proposed security improvements and present recommendations and mitigation measures to Socra Tech. 
TOOLS USED:
•	WIRESHARK
•	PFSENSE
•	WAZUH
•	UBUNTU VIRTUAL MACHINE
•	KALI LINUX
PHASE 1: NETWORK TRAFFIC CAPTURE AND ANALYSIS USING WIRESHARK
•	This phase covers the traffic analysis of the most common network protocols, focusing on HTTP, DNS, and SSH traffic.
•	Suspicious HTTP and DNS requests were identified by analyzing logs for unusual patterns, such as spikes in traffic, frequent requests to unknown domains, or unusual query lengths. During these monitoring traffic exercises, the following were the focus of objective in Socra Tech’s network environment - unusual traffic patterns such as repeated connections to suspicious IP addresses, unusual protocols, or large amounts of data being transferred, long domain names or subdomains, and requests to newly registered or misspelled domains.
•	Analyzing DNS, HTTP & SSH Logs:
Socra Tech’s main sources (IP Addresses) and source ports are 172.17.0.17 & 172.17.0.99 and ports 53 ,80 & 443. In collecting data flowing through the selected interfaces, the first exercise was to start capturing in Wireshark to analyze the network traffic. Once the Wireshark capture started, the interface is divided into three main panes:
•	Packet List Pane (Top) - This displays a list of all the packets that Wireshark has captured.
•	Packet Details Pane (Middle) – This area shows detailed information about the selected packet in a hierarchical format.
•	Packet Bytes Pane (Bottom) – This pane shows the raw packet data in both hexadecimal and American Standard Code for Information Interchange (ASCII) formats.
DNS FILTERING FROM WIRESHARK
![image](https://github.com/user-attachments/assets/7f170ba2-77cd-453f-a9b8-c0deece62bcd)
IDENTIFIED SUSPISCIOUS DNS QUERIES FROM WIRESHARK
![image](https://github.com/user-attachments/assets/de52174b-7839-4869-9b21-326abab7ed3d)
HTTP FILTERING FROM WIRESHARK
![image](https://github.com/user-attachments/assets/75ddd7ba-b482-44e5-ba97-ceda9f6b88b1)
IDENTIFIED UNUSUAL HTTP PATTERNS FROM WIRESHARK
![image](https://github.com/user-attachments/assets/ac70b305-70c2-4861-8079-d42a4142c876)
SSH FILTERING FROM WIRESHARK
![image](https://github.com/user-attachments/assets/b6b8c6db-2857-46ef-b069-3c270f0234c7)
FINDINGS ON NETWORK TRAFFIC CAPTURE & ANALYSIS USING WIRESHARK.
•	Ports scanning activities detected
   - sources: 172.17.0.17 & 172.17.0.99
   - targeted ports: 80, 53,443
   - evidence: 
Domain Name System Response – Standard Query Response – No such name.
Port scanning activity (SYN-Synchronize packets without ACK-Acknowledgements)
Client/Server encrypted packets. Content unknown without the decryption key.
•	Noticed a lot of SYN packets with no lag time.
•	Monitored the flag values. Domain Name System Response – Standard Query Response – No such name.
•	Looked for HTTP requests with unusual URLs, parameters, or user-agents, which could indicate malicious activity. Example is POST /foots.php
•	Checked for HTTP requests to known malicious domains or IP addresses. Example is connecttest.txt
•	Monitored HTTP requests for large data transfers from 150 info length and above, especially to unfamiliar or suspicious destinations.
•	Looked for HTTP requests to known C2 server domains or IP addresses.
•	Identified pattern of systematic connection attempts
•	Monitored the SSH directory for unauthorized access to Socra Tech’s private keys and other credentials.
•	• Hunted for credential access attempts by analyzing logs and looking for suspicious patterns. Filtered alerts related to SSH attacks, including brute-force attempts.
PHASE 2: FIREWALL IMPLEMENTATION & POLICY ENFORCEMENT (PFSENSE)
•	This phase covers a robust solution to firewall implementation and policy enforcement due to the concerns about potential unauthorized access, malware infections, and insider threats in Socra Tech.
•	For this phase, pfSense was set up and used as a network security appliance to filter, block, and log malicious traffic. This allowed the cybersecurity analyst in Socra Tech to create, manage and enforce firewall rules. These rules allowed the right type of network traffic to pass through the system based on certain criteria such as IP address, ports, protocol and more.
•	Policy was enforced in Socra Tech’s security environment by regulating user access, block unauthorized traffic, prioritize bandwidth and ensure compliance and regulatory standards. The intrusion detection/prevention systems also enhanced policy enforcement.
•	Management and monitoring were simplified in SocraTech’s environment while using pfSense. This allowed real-time traffic monitoring and generating reports to allow policy effectiveness.
![image](https://github.com/user-attachments/assets/6a1976c5-9a19-4357-ae95-08878fc8e0c8)
![image](https://github.com/user-attachments/assets/1c35521a-535d-411a-bc32-35ceee86adae)
![image](https://github.com/user-attachments/assets/dec0a57e-8c44-4a32-80af-33e48d1692d5)
FINDINGS ON FIREWALL IMPLEMENTATION & POLICY ENFORCEMENT (PFSENSE).
•	Snort was installed in pfSense. This is an open-source network intrusion detection and prevention system (IDS/IPS) that monitors network traffic for suspicious activity
•	The WAN and the LAN interfaces were added to get the snort running.
•	Created an intrusion detection rule. Example: inbound/outbound rules, blocklists
•	The same rule was switched to create an intrusion prevention rule
•	Reported on blocked traffic, its sources, and targeted services
•	Generated alerts based on predefined rules to identify unusual network behavior
PHASE 3: WAZUH – SECURITY EVENT MONITORING & RESPONSE.
•	For phase 3, Wazuh, a Security Information and Event Management (SIEM) tool was deployed to help protect SocraTech’s IT assets and provide threat detection, incident response, and compliance monitoring.
•	A Wazuh agent was added, named TolaUbuntu and attached to endpoints to help monitor Socra Tech’s devices to see the traffic and help collect data and see threats.
Wazuh also has a dashboard to visualize Socra Tech’s security events.
IDENTIFIED MALICIOUS TRAFFIC NETWORK BEHAVIOR FROM WAZUH.
![image](https://github.com/user-attachments/assets/5b5341d9-1994-4196-8fbc-2f3dbe265916)
IDENTIFIED MALICIOUS TRAFFIC NETWORK BEHAVIOR FROM WAZUH.
![image](https://github.com/user-attachments/assets/ab5d503b-99a6-4953-bd57-a3f935fc28f9)
![image](https://github.com/user-attachments/assets/79d943a6-7a74-4eef-919c-4fe6c22badf0)
FINDINGS ON NETWORK TRAFFIC CAPTURE & ANALYSIS USING WAZUH.
•	Monitored the SSH directory for unauthorized access to Socra Tech's private keys and other credentials. 
•	Observed that there were five thousand, four hundred and five (5,405) hits from suspicious /brute force attacks.
•	Noticed the vulnerability severity levels of above seven (7) are considered high, a level above eight (8) is considered critical while a level close to ten (10) is considered bad. Socra Tech’s environment recorded a number of these.
•	Checked for credential access attempts by analyzing logs and observed that there were so many failed logs in attempts in a short time.
•	Filtered alerts related to SSH attacks, including brute-force attempts as there were multiple attempts to log in by using non-existent users. 
•	Visualized the alert data and traffic patterns associated with SSH attacks on the Wazuh dashboard as there were so many changes with the port statuses. 
•	Viewed and reported on the frequency and severity of SSH attacks in Socra Tech's environment.
RECOMMENDATION AND CONCLUSION.
•	Socra Tech is encouraged to be proactive with respect to the security environment. The IT department needs to always scan the system for vulnerabilities.
•	Socra Tech must have a business continuity plan in place 
•	Security measures and policies are to be put in place.
•	Socra Tech should strengthen proactive defenses.
•	The company must deploy a robust DDOS mitigation service.
•	Socra Tech must deploy real time detection for the vulnerabilities using the SIEM tools.
•	The company must leverage behavioral analysis to curb attackers from infiltrating into the security landscape.
•	Employees at Socra Tech are required to be trained on security measures and policies.
•	Segregation of duties at all levels of authorities should be activated as this may help curtail the vulnerability.
•	The security policies and procedures that are currently in place at Socra Tech need to be reviewed.
•	A policy, which shows a detailed responsibilities of each employee and management team should be emphasized in Socra Tech.
•	The management style, playbook and incident response plan should be reviewed
