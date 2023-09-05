## Challenge Description
```
My computer was compromised and my files were stolen and then deleted from my computer, I've captured some of the traffic, can you analyse the PCAP and try to restore any of my files?
```

## Challenge Solution
### 1- First thing noticed is 3 fragmented packets with length of 1516 byte reassembled in an ICMP echo ping request packet. This pattern is repeated 4 times so first hypothesis comes to mind is ICMP data exfiltration.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/c8ccbc5f-a53b-4d8d-848c-c00f50d0a274)

### 2- To check if this theory was right or not we try to check the destination IP address on VirusTotal. We find the IP is indeed malicious (check relations page too). This indicates that someone is attempting to send data to Akami connected cloud infrastructure.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/cb11e63b-6dfd-4df5-b57f-a07bbd761afb)

### 3- First we get data from all ICMP packets in a text file using this (tshark command). 
```
tshark -r eXodus.pcapng -Y icmp -T fields -e data.data > output.txt
```

### 4- Data in the ICMP packets looks like xor encoded data so we need to transfer them to their binary form then applying xor on them.
```
Sample of data:
06113216111610161215001b12170b333b651727023c021c3b3e0c1312120f181215001d121500131e0018611e1010251d1014281e0774253139272604661731387b79053b2e0735001d22113c6020133c1a083b1b020f35141e121f182d263a1c132a17091a1315073c1317043f0664090d003b3c01283c38330c6000263120371b0f3d64263b61307f113e350c6e7d366309026a2034376b2e387d647f2f281c2d271f06126a1a6b050d6612331414113111361c6531151516130712152e19003f3203170c2d14603e163439600811023a070a6561202a397f19641113733e2b1a737d3f373b03101a6e3e1618201e296613031a3b31343c15083d25630b2705620d3e373327022b3315380a3c7631653a731316031307263f76793f0224173e16310335652e38260c2e222907371c356211196b7f262830323514230670226b242420236c2f03236006603c67700a1a2e3238181714633b7f047d602e053337183836061
```
 ### 5- Before decoding data there is a file downloaded using http protocol which name is a hint to decode this data.
 ![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/477cd0ed-37f4-410d-bd2f-50015d582aa1)

### 6- Now we decode this data using cyberchef (problem occurs when trying to decode data all at once so we divide them). 
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/128d0e00-16c6-4af7-95e4-6b6531eeffca)

### 7- Combined data seems like a base64 encoded string when decoded we get below output. The PK in the beginning of the output indicates zip file signature. using Unzip with the base64 decode we get an image containing the flag.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/0006aaba-82f1-4162-89d6-6293a9703000)

![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/bf411887-138b-4220-bc30-0da2bb29bd02)

The final flag is &rarr; `FLAG{M1gratingOutOfYourNetXwoXrk}`
