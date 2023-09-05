## Challenge Description
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/46b153a1-2b27-4879-99f7-b53e864468b7)

## Challenge Solution
### 1- First thing to do after openning the pcap file check statistics -> conversations. On the IPv4 tab we notice the brute force attempt mentioned in the description from IP "192.168.1.7" to the IP range of "192.126.117.0/24"
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/6e76f1a2-b48f-4e85-9fd5-349f4896e1f9)

### 2- We notice on the tcp payload of each packet a hex value so we use tshark to extract all of those payloads with this command
```
tshark -r Missey.pcap -e "tcp.payload" -T fields -Y "ip.src==192.168.1.7 and ip.dst==192.126.117.0/24"
```
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/d8df192a-4985-4bc2-84d6-ffac0255738b)

### 3- Now we need to convert these hex to binary using "xxd" the command becomes like this. xxd writes into its output file without truncating it. Use the combination -r -p to read plain hexadecimal dumps without line number information and without a particular column layout
```
tshark -r Missey.pcap -e "tcp.payload" -T fields -Y "ip.src==192.168.1.7 and ip.dst==192.126.117.0/24" | xxd -r -p
```

### 4- Last command got us hex value so we repeat the last part again and the final command becomes. Now we can see the flag hidden in the output
```
tshark -r Missey.pcap -e "tcp.payload" -T fields -Y "ip.src==192.168.1.7 and ip.dst==192.126.117.0/24" | xxd -r -p | xxd -r -p
```
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/37c79b23-27f3-4661-bc45-c7fc2dd0f279)

The final flag is &rarr; `FLAG{M15SED_INBY73$}`
