## Challenge Description
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/ff355ba5-7099-4c39-ab97-496ba0d3597d)

## Challenge Solution
### 1- After downloading the zip file in the challenge it contains an exe file called "worm.exe" we run it in an isolated windows machine and run wireshark to track it. After a while when the exe file is done running take a look the "statistics -> conversations" tab we notice the following
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/d130bfce-11d8-4254-9059-3fe76aa4f7b7)

### We have the range of the worm is spreading which is "192.168.1.0/24"

### 2- Using Tshark to filter source IP, destination IP and destination port with this command
```
tshark -r WormSeen.pcapng -Y "ip.src=192.168.229.4 && ip.dst=192.168.1.0/24" -T fields -e ip.src -e ip.dst -e tcp.dstport | uniq
```
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/61ffaa84-b4fb-400d-939b-2ed5f26279c4)


### 3- Last thing we need to get is how many hosts affected. We can get that just by adding "wc -l" to the end of last command to count number of lines.
```
tshark -r WormSeen.pcapng -Y "ip.src=192.168.229.4 && ip.dst=192.168.1.0/24" -T fields -e ip.src -e ip.dst -e tcp.dstport | uniq | wc -l
```
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/4b3bd8d3-d840-4e3c-9957-1b97daece45e)

The final flag is &rarr; `flag{192.168.1.0/24:22:85} `
