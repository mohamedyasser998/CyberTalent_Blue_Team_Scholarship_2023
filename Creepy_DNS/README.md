## Challenge description
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/74294505-283e-4efc-94fb-62b4a8b0283b)

## Challenge Solution
### 1- Starting by filtering packets to show only dns traffic. When we scroll down we notice weird queries with domain name cybertalents.com and different subdomains.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/25b3b811-8589-4c42-8550-ced16f912eb6)

### Adding subdomains together seems to form a base64 encoded string which might be the answer. To apply this theory we need to use tshark to extract them. This is the query I used.
```
tshark -r Creepy_dns.pcapng -Y "dns.qry.name contains cybertalents.com && !(dns.resp.type==OPT) && !(dns.flags.response==1)" -T fields -e dns.qry.name | cut -d '.' -f 1 | tr -d '\n' | base64 -d
```
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/953702a7-3168-4688-a540-8a24c48dfff9)

The final flag is &rarr; `flag{tshArk_Is_Awes0me_Netw0rking_to0l}`
