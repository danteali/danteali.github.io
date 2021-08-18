---
Created:  '2021-08-17 12:25:37 +01:00'
Modified: '2021-08-17 12:25:37 +01:00'
---

| Tags: #tools #ctf #pentesting #infosec #windows #linux |
| --------------------------------------- |

---
# Windows - [LOLBAS](https://lolbas-project.github.io/) - Living Off The Land Binaries and Scripts (and also Libraries)
Repository of information on official signed Microsoft utilities which can be used for 'unintended' purposes, e.g. to exfiltrate data, create reverse shells, run unsigned code, ...

> **A LOLBin/Lib/Script must:**
> 
> -   Be a Microsoft-signed file, either native to the OS or downloaded from Microsoft.
> -   Have extra "unexpected" functionality. It is not interesting to document intended use cases.
>     -   Exceptions are application whitelisting bypasses
> -   Have functionality that would be useful to an APT or red team
> 
> **Interesting functionality can include:**
> 
> -   Executing code
>     -   Arbitrary code execution
>     -   Pass-through execution of other programs (unsigned) or scripts (via a LOLBin)
> -   Compiling code
> -   File operations
>     -   Downloading
>     -   Upload
>     -   Copy
> -   Persistence
>     -   Pass-through persistence utilizing existing LOLBin
>     -   Persistence (e.g. hide data in ADS, execute at logon)
> -   UAC bypass
> -   Credential theft
> -   Dumping process memory
> -   Surveillance (e.g. keylogger, network trace)
> -   Log evasion/modification
> -   DLL side-loading/hijacking without being relocated elsewhere in the filesystem.


# Linux - [GTFOBins](https://gtfobins.github.io/)

> GTFOBins is a curated list of Unix binaries that can be used to bypass local security restrictions in misconfigured systems.
>
> The project collects legitimate [functions](https://gtfobins.github.io/functions/) of Unix binaries that can be abused to ~~get the f**k~~ break out restricted shells, escalate or maintain elevated privileges, transfer files, spawn bind and reverse shells, and facilitate the other post-exploitation tasks.