## Challenge Descriptino
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/953df938-b36b-4453-9aa8-a6f9c571de7e)

## Challenge Solution
### When we first open the given url we see mr.bean's image. When we view page source the image is loaded from the current directory on server.
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/9a9599cb-89f5-4fb3-9548-3d981c0ac851)

### We try adding /etc to the url to see the response. We notice server is running nginx/1.23.2 which is vulnerable.
``` http://wlemj0wz0k1twzoer4gvmkxal3dm6dv926xoi4zl-web.cybertalentslabs.com/etc ```

![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/786950e9-43e6-4a6c-8d5d-a85c9742e3c9)

### Using Gobuster to brute-force: URIs (directories and files) in the web site
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/ab25b1ec-e098-4202-a232-b0ccf3f3912d)

### Open the url given in the results
``` http://wlemj0wz0k1twzoer4gvmkxal3dm6dv926xoi4zl-web.cybertalentslabs.com/files ```

![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/e101c516-8038-4819-a99b-bacd89f587bc)

### Go back to the parent directory adding ../ in the url
``` http://wlemj0wz0k1twzoer4gvmkxal3dm6dv926xoi4zl-web.cybertalentslabs.com/files../ ```

![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/2817ea28-41f9-4755-a928-e083ba7f2012)

### The hint given in the description was "Come back home". So we go to home directory and there is the flag.txt
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/ee0aeec1-38f8-4a5e-a975-98eecf423c66)

The final flag is &rarr; `FLAG{Nginx_nOt_aLWays_sEcUre_bY_The_waY}`
