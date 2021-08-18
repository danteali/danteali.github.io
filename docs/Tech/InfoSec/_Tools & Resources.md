---
Created:  '2021-08-14 23:49:35 +01:00'
Modified: '2021-08-14 23:49:35 +01:00'
---

| Tags: #ctf #pentesting #tools #apps |
| ----------------------------------- |

---

> # Key Takeaways / Things to Remember
> 1. Check out John Hammond's [CTF Katana](https://github.com/JohnHammond/ctf-katana)

---
# Tools & Resources

Below are details of tools and resources picked up related to pen testing, cyphers, crypto, etc.

In particular aimed at solving CTFs, etc

# Kids Learning
Before I forget here are some sites which could be useful for James to learn crypto basics and coding/scripting:
* https://blockly.games/maze?lang=en&level=4&skin=1 
* https://www.codemonkey.com/
* http://www.crunchzilla.com/code-monster
* https://www.cryptoclub.org/#vAllTools
* https://www.makewonder.com/robots/dash/
* https://smile.amazon.co.uk/Wonder-Workshop-DA01-Dash-Robot/dp/B00SKURVKY/ref=sr_1_2?dchild=1&keywords=wonder+workshop&qid=1628803680&sr=8-2

# Reading
* ###### CTF Katana (John Hammond)
	* [CTF Katana](https://github.com/JohnHammond/ctf-katana)
	* And this Katana tool which automates a bunch of the simple stuff: 
		https://github.com/JohnHammond/katana 
		https://ctf-katana.readthedocs.io/en/latest/
	* And John's YouTube channel: https://youtu.be/xl2Xx5YOKcI

* ###### Hacktricks / PEASS (Carlos Polop)
	* https://book.hacktricks.xyz/
	* https://github.com/carlospolop/PEASS-ng
		And the DC29 Offensive Security talk: https://www.youtube.com/watch?v=9_fJv_weLU0

<br>

* https://github.com/swisskyrepo/PayloadsAllTheThings  - payload for basically every scenario
* Good methodology: https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Methodology%20and%20Resources
* https://cryptokait.com/workshops/national-cyber-league-coaching-guide-v-2-1/ncl-coaching-guide-resources-by-category/
	* https://cryptokait.com/2020/03/04/a-beginners-guide-to-scanning-with-dirbuster-for-the-ncl-games/
* https://capture.tf/files/CTF-Preparation-Guide.pdf
	LOADS of info on lost of common CFT puzzles incl cyphers
* https://resources.infosecinstitute.com/topic/tools-of-trade-and-resources-to-prepare-in-a-hacker-ctf-competition-or-challenge/#gref
* https://www.hacksplaining.com/
* https://null-byte.wonderhowto.com/


# To-do
##### URL Testing Script
#todo-low
This happened multiple times during the DC29 badge challenge - we had to check for various URL combinations. Write a script to create URL permutations and test for valid URL responses at those locations.

Requirements:
- should check curl response for non-404s
- should have timing capability e.g. how long last response took, avg response, % complete, expected completion
- need to be able to pull from file to try
- need to be able to generate own paths from permutations of strings.

This will do it for us already but can be detected by targets (defcon.org detected my post-conference testing)
* [Gobuster](Tools/Gobuster%20&%20Dirbuster.md) to enumerate URLs
* [crunch](https://www.hackers-arise.com/creating-a-custom-wordlist-with-cru) or 'Combinator' to generate wordlists based on permutations of strings.
* Maybe... [Screaming Frog](https://www.screamingfrog.co.uk/seo-spider/)

###### Script info/sources/help
**Generating Permutations**
* https://stackoverflow.com/questions/47905379/bash-permutation-with-list-of-words
* https://stackoverflow.com/questions/3846123/generating-permutations-using-bash
* Use the tool ‘crunch’ to generate permutations: https://pentestlab.blog/2012/07/12/creating-wordlists-with-crunch/
```bash
_./crunch 1 1 -p word1 word2 word3_
```

**Checking URLs**
* https://stackoverflow.com/questions/28099637/how-do-you-bulk-test-url-redirections
* https://stackoverflow.com/questions/35644789/bulk-url-checker-macro-excel
* https://stackoverflow.com/questions/6136022/script-to-get-the-http-status-code-of-a-list-of-urls
* *PHP*
	* https://stackoverflow.com/questions/36735364/bulk-link-checker-in-php
	* https://stackoverflow.com/questions/34173636/trying-to-get-this-php-code-to-work-for-bulk-action
* * Python*
	* https://stackoverflow.com/questions/53894401/bulk-http-status-requests
	* https://stackoverflow.com/questions/7152762/how-to-redirect-print-output-to-a-file
	* https://stackoverflow.com/questions/64724802/python-bulk-httpresponse-check
		* https://docs.aiohttp.org/en/stable/


# Software
###### Kali
* https://null-byte.wonderhowto.com/how-to/setup-practice-ctfs-from-vulnhub-kali-linux-0170228/
* [https://www.kali.org/docs/virtualization/install-virtualbox-guest-vm/](https://www.kali.org/docs/virtualization/install-virtualbox-guest-vm/)
* [https://www.offensive-security.com/metasploit-unleashed/](https://www.offensive-security.com/metasploit-unleashed/)

###### Ghidra
* [ghidra](https://github.com/NationalSecurityAgency/ghidra 
* https://www.shogunlab.com/blog/2019/04/12/here-be-dragons-ghidra-0.html 
* https://ghidra.re/courses/GhidraClass/Beginner/Introduction_to_Ghidra_Student_Guide_withNotes.html#Introduction_to_Ghidra_Student_Guide.html 
<br>
* Uf2 stuff
	* [uf2 plugin](https://github.com/wyattearp/ghidra_uf2loader)
	* https://github.com/kjcolley7/UF2-IDA-Loader
	* https://github.com/fkie-cad/FACT_core 
	* https://github.com/Microsoft/uf2#files-exposed-by-bootloaders


# Cyphers & Bases
Common examples in CTFs:
* hex
* ascii
* base-16
<br>
* rot 13
* rot 47
* Caesar Cipher
* Vigenère Cipher (including the autokey variant)
* Beaufort Cipher (including the autokey variant)
* Playfair Cipher
* Two-Square/Double Playfair Cipher

##### Cypher identifiers
* https://www.boxentriq.com/code-breaking/cipher-identifier
* https://www.dcode.fr/cipher-identifier

##### Decrypters
* www.dcode.fr/caesar-cipher
* www.dcode.fr/vigenere-cipher
* www.dcode.fr/ascii-code


# Misc Tools/Toolkits
* https://github.com/JohnHammond/ctf-katana
* https://github.com/eugenekolo/sec-tools
* https://github.com/zardus/ctf-tools
<br>
* Gobuster - URL tester
* Dirbuster 
* Enum4linux - enumerate services
* Hydra - password guesser
* LinPeas - Priv esc awesome script https://github.com/carlospolop/PEASS-ng
* John the ripper 
	Including how to turn common files into stuff that JTR can run against e.g. id_rsa SSH keys
* Rock you word lists