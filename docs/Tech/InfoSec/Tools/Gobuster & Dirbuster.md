---
Created:  '2021-08-15 23:57:51 +01:00'
Modified: '2021-08-15 23:57:51 +01:00'
---

| Tags: #tools #ctf #pentesting #infosec #kali #enumeration |
| -------------------------------------------- |

---

###### URL Response Codes
Just a quick reminder before we get into the meat of this:
- **100 Continue** - Codes in the 100 range indicate that, for some reason, the client request has not been completed and the client should continue.
- **200 Successful** - Codes in the 200 range generally mean the request was successful.
- **300 Multiple Choices** - Codes in the 300 range can mean many things, but generally they mean that the request was not completed.
- **400 Bad Request** - The codes in the 400 range generally signal a bad request. The most common is the 404 (not found) and 403 (forbidden).

---

# Gobuster & Dirbuster
Tools for enumerating URLs and directory trees. Handy in CTFs and pentesting to find valid targets.

## [Dirbuster](https://github.com/KajanM/DirBuster)
Comes bundled with Kali and has a GUI :)

GUI is pretty self-explainatory. 

*Note that when testing the Defcon29 badge challenge URL enumeration (see wordlist generation at [DC29 wordlist](Wordlists.md#^644cab)), defcon.org detected and blocked attempts. Suspect my test rate was too high so start LOW.*

**Wordlists**
* See note: [Wordlists](Wordlists.md)
* The app comes along with some wordlists for checking, these are detailed in the GUI. 
* Kali also has some specific wordlists for directories at `/usr/share/wordlists/dirb/` and `/usr/share/wordlists/dirbuster/`


| Sources:                                                                                                  |
| --------------------------------------------------------------------------------------------------------- |
| https://cryptokait.com/2020/03/04/a-beginners-guide-to-scanning-with-dirbuster-for-the-ncl-games/         |
| https://null-byte.wonderhowto.com/how-to/hack-like-pro-find-directories-websites-using-dirbuster-0157593/ |

---

## [Gobuster](https://github.com/OJ/gobuster)

Command line only.

Couple of mode options:
-   dir - the classic directory brute-forcing mode
-   dns - DNS subdomain brute-forcing mode

**Examples**

**A. General use to find directories of websites **
```bash
gobuster dir -f -u https://defcon.org/signal/YourJourneyBegins/AlphabetShift/SandsSaharaAladdin/MC56F8006VLC/ -w DC29_badge.txt -o gobuster.txt [--delay 1000ms]
```
- `-u` target URL
- `-w` wordlist
- `-o` output to file
- `-f` (optional) append `/` to each URL
- `--delay 1000ms` (optional) if target is limiting or refusing connections, add/increase delay 

<br>

**B. Find specific file types **
```bash
gobuster dir -v -e -u http://192.168.1.105/dvwa -w /usr/share/wordlists/dirb/common.txt -x .php
```
- `-e` print full path of the files
- `-u` target URL
- `-w` wordlist
- `-v` verbose output
- `-x` specify file type

<br>

**C. Specify username & password to access resource **
```bash
gobuster dir -v -e -u http://192.168.1.105/dvwa -w /usr/share/wordlists/dirb/common.txt -U test -P test
```
- `-e` print full path of the files
- `-u` target URL
- `-w` wordlist
- `-v` verbose output
- `-U` username
- `-P` password

<br>

**D. Specify specific codes **
```bash
gobuster dir -v -e -u http://192.168.1.105/dvwa -w /usr/share/wordlists/dirb/common.txt -s 301,200
```
- `-e` print full path of the files
- `-u` target URL
- `-w` wordlist
- `-v` verbose output
- `-U` username
- `-P` password

| Sources:                                                                                                        |
| --------------------------------------------------------------------------------------------------------------- |
| https://null-byte.wonderhowto.com/how-to/scan-websites-for-interesting-directories-files-with-gobuster-0197226/ |
| https://www.securitynewspaper.com/2019/11/04/bruteforce-any-website-with-gobuster-step-by-step-guide/ |




