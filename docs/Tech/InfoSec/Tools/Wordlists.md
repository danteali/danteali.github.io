---
Created:  '2021-08-15 20:48:50 +01:00'
Modified: '2021-08-15 20:48:50 +01:00'
---

| Tags: #ctf #pentesting #infosec #wordlist |
| ----- |

---

> # Key Takeaways / Things to Remember
> * Kali's built-in wordlists are at: `/etc/share/wordlists`
>   * including the RockYou wordlist 

---

Note that there is a whole repo full of wordlists at:
https://github.com/danielmiessler/SecLists
They are organised for various uses. Worth downloading in advance of any challenges.

---

# Custom lists with [Crunch](https://manpages.ubuntu.com/manpages/bionic/man1/crunch.1.html)
We can generate our own wordlists with #crunch. Lots of good crunch examples at [man crunch](https://manpages.ubuntu.com/manpages/bionic/man1/crunch.1.html)

**Examples**

**A. Defcon29 Badge Challenge**
e.g. Defcon29 badge challenge we knew that the URL was a combination of the badge names but didn't know the order or if the words were capitalised. We can generate wordlists to test with (we need to generate twice to include all lower-case and capitalised letters): ^644cab
```bash
crunch 1 1 -o DC29_badge.txt -p Artist Human Goon Press Vendor Speaker Creator
crunch 1 1 -p artist human goon press vendor speaker creator >> DC29_badge.txt
```
* `-p` supplies a list of characters or words to permute. The min/max lengths are not used but must still be passed so can be anything. `-p` **must** be the last option supplied!

We can then pass this wordlist into [Gobuster & Dirbuster](Gobuster%20&%20Dirbuster.md) to enumerate the defcon.org URL.

<br>

**B. Create list of all numeric only password between 4-6 characters long**
```bash
crunch 4 6 0123456789 > numeric_min4_max6.txt

tail -3 numeric_min4_max6.txt
	999997
	999998
	999999

head -n 3 numeric_min4_max6.txt
	0000
	0001
	0002
```

<br>

**C. Specify a pattern using `-t`**
`-t` allows you to specify a pattern:
-   @ will insert lower case characters
-   , will insert upper case characters
-   % will insert numbers
-   ^ will insert symbols

Let's generate a 10 character password of lower-case letters ending 0316 (e.g. birthday) - output will be c. 10GB!
```bash
crunch 10 10 -t @@@@@@0316 -o /root/birth_datlist.txt
```

<br>

**D. Use a pre-defined character set from `/usr/share/rainbowcrack/charset.txt`**
`/usr/share/rainbowcrack/charset.txt` contains definitions of lots of different character sets. We can specify the use of one of these in crunch command:
```bash
crunch 8 8 -f /usr/share/rainbowcrack/charset.txt mixalpha -o /root/alphawordlist.lst
```


---

# Kali wordlists
Kali's wordlists are located at `/usr/share/wordlists`

---

# Rock You Wordlist
The **rockyou wordlist** is a password dictionary used to help to perform different types of password cracking attacks. It is a collection of the most used and potential passwords.
Rock You is an old company that went bust ages ago.

It can be used in multiple tools e.g. [John The Ripper](John%20The%20Ripper.md)

It can be downloaded from:
https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt

It also comes 'pre-installed' as a zipped file in Kali. But is owned by root. We want to change ownership of all the pre-installed wordlists to our user and unzip the rockyou file before we can use it:
```bash
ll /usr/share/wordlists/
sudo chown -R ryan:ryan /usr/share/wordlists/
gzip -d /usr/share/wordlists/rockyou.txt.gz
ll /usr/share/wordlists/rockyou.txt
```
