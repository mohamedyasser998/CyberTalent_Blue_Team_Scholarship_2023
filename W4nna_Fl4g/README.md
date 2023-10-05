## Challenge Description
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/bbb6bf69-baf0-4d2d-99c5-f83f51840128)

## Challenge Solution
### 1- First thing we need to do is listing the process tree to see all processes and their parent process.

```
python vol.py -f "W4nna Flag.mem"  windows.pstree
```
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/fba6ccc1-2804-4898-a392-0240475e1923)

### We notice a strange process "yw4qxckT.exe" starting from "explorer.exe" and starting "@WanaDecryptor" obviously this needs to be looked at

### 2- We dump this suspicious executable file to check on virus total using this command

```
python vol.py -f "W4nna Flag.mem" -o ./output windows.dumpfiles --pid 4168
```
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/cdbb16e8-a357-43d4-bf03-9ec81ed70aac)

### 3- We check this file on virustotal it's flagged as malicious by 66 vendor

![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/90a65d6c-eacb-4f37-b609-f3b674ea38f9)


### now we need to get the name of the malware according to drweb as challenge specified
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/3c06a993-ab5d-44ca-97b8-f5589c7ef6bd)

### 4- Last part we need host based IOC (Mutex). We run this command and try different IOCs

```
python vol.py -f "W4nna Flag.mem"  windows.mutantscan
```

![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/d10c4a2f-a552-4651-bdfd-a0511f9ea994)

### The third one turns to be the right one


The final flag is &rarr; `Flag{yw4qxckT.exe_Trojan.Encoder.11432_MsWinZonesCacheCounterMutexA}`
