### 1- Multiple RSYNC packets are sent from the local machine 192.168.1.80 to 34.140.248.32 (Malicious) According to VirusTotal.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/966cb39b-52f5-439a-9203-6486729876bc)![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/86961f24-0702-429f-b741-a74aa4d0d976)
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/d2a2890e-dd8f-45a3-8631-c412f2a54037)

![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/f15ae817-c2ad-477c-acd8-5ae5a1c708c4)

#### RSYNC is commonly used for file synchronization and transfer over network can be used for legitimate purpose such as backing up files or sharing data. But in this case data are being sent to a malicious IP which could indicate sensitive or confidential data is being exfiltrated from local machine to remote attacker system.

### 2- Multiple mDNS packets sent from the local machine 192.168.1.53 to 224.0.0.251 (Malicious) According to VirusTotal relations page.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/4d2b4ff6-46bc-4683-ad7f-65be7bdb5573)


#### mDNS is used for resolving hostnames to IP addresses in small networks without a dedicated DNS. it operates using multicast packets that are sent to specific IP address range and port number. In this case a malware is using mDNS to communicate wit a C2 server. A follow-up packet with source and destination IPv6 and same info may suggest malware is trying to establish channel with C2 server using IPv6 to bypass network security controls hat aren't configured to monitor IPv6 traffic.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/13fa0c50-9786-4860-87df-2f5cbc25ffb0)


### 3- The first infected IP 34.140.248.32 which has the mac address of Arcadyan_cb:56:d7 is sending ARP request broadcast packets trying to get requesting multiple machines and got response from one machine with IP of 192.168.1.80. 
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/49a792c9-349e-4b30-b7f2-de317f6803d7)

![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/35c2ab32-96c9-4dda-81e8-369632a70fab)

### 4- the infected machine with IP 192.168.1.58 sends SYN packet to 192.168.1.80 on port 6200 (may indicated malware attempting to scan open ports) gets RST,ACK response meaning closed port. tries again to send SYN packet to port 21 completes threeway handshake with the system running vsftpd v2.3.4 which allowed attackers to execute arbitrary code or gain unauthorized access to an affected system by exploiting a flaw in the FTP server's source code (CVE-2011-2523). Attempting a login with a smiley face after random username and random password triggers a backdoor which which results in a shell listening on TCP port 6200.

![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/8e44b941-2c2c-4a05-a1f3-ea346e009bb9)

The final flag is &rarr; `flag{Internal:192.168.1.58:CVE-2011-2523:08:00:27:66:e3:8b}`
