## Challenge Description
![image](https://github.com/mohamedyasser998/CyberTalent_Blue_Team_Scholarship_2023/assets/57010124/24e367eb-3174-41f6-9675-53d44a294634)


## Challenge Solution
### Opening the WAF's log file in the challenge, the whole log file is just many 'GET' requests from same IP in close times obvious directory bruteforcing using tool called 'wfuzz'
```
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /randomfile1 HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /frand2 HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.bash_history HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.bashrc HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.cache HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.config HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.cvs HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.cvsignore HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.forward HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.git/HEAD HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.history HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.hta HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.htaccess HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.htpasswd HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
172.17.0.1 - - [12/Jun/2022:11:04:05 +0000] "GET /.listing HTTP/1.1" 404 169 "-" "Wfuzz/2.2" "-"
```

### In the end of the log file we notice successful 'GET' request from the attacker to 'files' directory, moving back then to 'home' directory and requesting 'flag.txt' file.
```
172.17.0.1 - - [12/Jun/2022:11:04:31 +0000] "GET /files../ HTTP/1.1" 200 2482 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:95.0) Gecko/20100101 Firefox/95.0" "-"
172.17.0.1 - - [12/Jun/2022:11:04:38 +0000] "GET /files../home/ HTTP/1.1" 200 302 "http://localhost/files../" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:95.0) Gecko/20100101 Firefox/95.0" "-"
172.17.0.1 - - [12/Jun/2022:11:05:12 +0000] "GET /files../home/flag.txt HTTP/1.1" 200 49 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:95.0) Gecko/20100101 Firefox/95.0" "-"
172.17.0.1 - - [12/Jun/2022:11:05:12 +0000] "GET /favicon.ico HTTP/1.1" 404 169 "http://localhost/files../home/flag.txt" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:95.0) Gecko/20100101 Firefox/95.0" "-"
```

### Now we have everything needed to form the flag

The final flag is &rarr; `flag{172.17.0.1:wfuzz:49:12/06/2022:11:05:12}`
