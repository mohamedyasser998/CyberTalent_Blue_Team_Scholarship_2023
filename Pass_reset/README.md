## Challenge Description
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/98b2adc1-5b17-4fd5-936a-186d2a09ab6c)

## Challenge Solution
### 1- We have a zipped file in this challenge and it's password protected so the first step we need to crack the password to get the msg in it. We use john the ripper to do this step.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/ee276e33-77e9-4a10-ba2f-d93b3f814cd9)

### We got the zipped file password "infected" now we go to next step

### 2- We open the email message in any mail client here I am using "eM Client". First thing we need is the sender email address we just hover with mouse over "Password Request" and there it is.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/f9fed034-c44f-4fee-8419-7139fe6e3cd7)

### 3- Second thing we need to get is the date user received the email. Obvious on top right corner.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/3f8f5eac-7708-48f2-8775-89f240881542)

### 4- Thrid thing is the domain name associated url on mail body we just need to hover over the link on the body and the domain shows on bottom.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/f040caa4-ce49-41bb-9ec5-736f74936af4)

### 5- Last thing we decide if mail is suspicious or not which is clearly suspicious the domain on the mail body is not microsoft related which is enough for a clue.

The final flag is &rarr; `flag{roger@captech.com:25/02/2022:attemplate.com:S}`
