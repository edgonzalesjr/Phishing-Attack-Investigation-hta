## Objective

Analyze a phishing email with a malicious .hta (HTML application) attachment, investigate its impact, and track its progression, including bypassing User Account Control (UAC), credential harvesting, and lateral movement to the Domain Controller.

### Skills Learned

- Email Analysis
  - Inspecting and analyzing phishing emails and attachments for malicious behavior.
  - Identifying potential Tactics, Techniques, and Procedures (TTPs) used in spear-phishing attacks. 
- Artifact Analysis
  - Understanding .hta files and their potential to execute malicious scripts.
  - Investigating payloads (.dat files) retrieved via Command and Control (C2) channels.  
- Advanced Threat Hunting
  - Tracking lateral movement within a network.
  - Identifying credential harvesting activities and their impact on enterprise security.  
- Log Analysis and Visualization
  - Using Elastic Search and Kibana for searching, correlating, and visualizing security events.
  - Extracting and interpreting critical artifacts from security logs.

### Tools Used

- Email Analysis
  - Email client for inspecting headers, attachments, and metadata.
- Artifact Analysis
  - Manual inspection of .hta files and .dat payloads.
  - Basic scripting and reverse engineering tools (if needed).
- Log Analysis and Visualization
  - Elastic Search: Searchable repository for security logs.
  - Kibana: Visualization tool for analyzing and visualizing log data.

## Perform Analysis

<p align="center">
<img src="https://imgur.com/jPetkxh.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>Login to the SIEM.</b>
<br/>

<p align="center">
<img src="https://imgur.com/Y6ETQ2Z.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>Set the timeline to match the time of incident.</b>
<br/>

<p align="center">
<img src="https://imgur.com/UuCnNj7.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>The process that executed the initial stage 1 payload. It used the Windows-native binary designed to execute Microsoft HTML Application (HTA) files.</b>
<br/>

<p align="center">
<img src="https://imgur.com/pPfS0TL.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>The implanted file was eventually used and executed by the stage 1 payload. It used the xcopy.exe to deliver another file review.dat.</b>
<br/>

<p align="center">
<img src="https://imgur.com/XI6LNoG.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>The Stage 1 payload established a persistence mechanism by using PowerShell to create a scheduled task.</b>
<br/>

<p align="center">
<img src="https://imgur.com/c22PC5M.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>The implanted file has initiated a potential C2 connection to an external IP address.</b>
<br/>

<p align="center">
<img src="https://imgur.com/Ep7vo2R.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>The process used by the attacker to execute a UAC bypass.</b>
<br/>

<p align="center">
<img src="https://imgur.com/qHX0Kh4.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>The attacker attempted to download a tool for credential dumping and dump the credentials on the machine.</b>
<br/>

<p align="center">
<img src="https://imgur.com/JxH5bto.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>The attacker successfully dumped the credentials and used the credentials to gain access to another machine.</b>
<br/>

<p align="center">
<img src="https://imgur.com/CRBjCEB.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<img src="https://imgur.com/975jErp.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<img src="https://imgur.com/nXBARKL.png" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>The attacker attempted to enumerate and access the file share.</b>
<br/>

<p align="center">
<img src="https://imgur.com/" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>.</b>
<br/>

<p align="center">
<img src="https://imgur.com/" height="40%" width="40%" alt="Device Specification"/>
<br/>
<b>.</b>
<br/>

## Outcome

- Email Analysis
  - Successfully identified the .hta attachment as the initial vector of compromise.  
- Artifact Analysis
  - Decoded the .dat payload and revealed its capabilities to bypass UAC, perform credential harvesting, and facilitate lateral movement.  
- Log Analysis and Threat Hunting
  - Used Elastic Search and Kibana to trace lateral movement from the initial access point to the Domain Controller.
  - Identified compromised credentials and critical data access events.
- Incident Assessment
  - Delivered a detailed assessment of the attack’s progression and impact.
  - Recommended measures to strengthen defenses against similar attacks in the future.

## Acknowledgements
- Adapted from [TryHackMe - Boogeyman 3](https://tryhackme.com/r/room/boogeyman3)
- [Kibana](https://www.elastic.co/kibana)

## Disclaimer

The projects and activities within this portfolio are for educational and ethical cybersecurity research purposes only. All work was performed in controlled environments, including isolated, personally owned laboratories, subscription-based cloud environments, and through engagement with online cybersecurity learning platforms. Any cloud-based activities and participation in online learning platforms were conducted in full compliance with their respective terms of service and acceptable use policies. These projects should not be used for any illegal or unethical activities. Unauthorized access to any computer system or network is strictly prohibited. The author(s) are not responsible for any misuse of the information or code provided.
