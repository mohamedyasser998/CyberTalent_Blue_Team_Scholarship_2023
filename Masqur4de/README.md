## Challenge Description
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/78305cde-8e07-4c68-adac-8a7a1a15dea2)

## Challenge Solution
### 1- The challenge provides us a memory dump file so we need to solve this challenge with volatility 3. We start with pstree plugin to check processes and parent process of each one.
```
python vol.py -f Masqur4qe.mem windows.pstree
```
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/6b6156da-b708-49b7-ae70-4efbeb228f8b)

### 2- There is a suspicious process hiding "masqurading" behind normal windows process "svchost.exe" this process must have a parent process "services.exe", But in the image it started from "explorer.exe". So we need to get this process file to check it using this command.
```
python vol.py -f Masqur4de.mem -o FilesOut windows.dumpfiles --pid 3588
```
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/1818da96-2e5a-4ac2-aacd-b0e5debd9714)

### 3- We check file on virustotal now and indeed the file is malicious. We go to relations tab to see domain names the malicious file is communicating with.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/a9768534-84a5-4561-9149-af08af9b986f)

![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/61ee0a94-6b9c-4285-89eb-f05d871ff740)

The final flag is &rarr; `FLAG{svchost_explorer_brb.3dtuts.by}`
