---
Created:  '2021-08-17 14:31:46 +01:00'
Modified: '2021-08-17 14:31:46 +01:00'
---

| Tags: #tools #ctf #pentesting #infosec #kali #cypher #encoded #code #base #steganography |
| ----- |

---

> # Key Takeaways / Things to Remember
> See extensive lists at these links - below are common ones more likely to encounter:
https://book.hacktricks.xyz/crypto/crypto-ctfs-tricks#encoders
https://github.com/JohnHammond/ctf-katana#esoteric-languages
>
> Useful Tools:
> * Multiple decoding tools: https://cryptii.com
> * More decoding tools (including cypher identifier): www.dcode.fr
> * Check all bases with: https://github.com/mufeedvh/basecrack
> * Convert from multiple systems: https://gchq.github.io/CyberChef/
---

# Common Codes & Cyphers

[Featherbuster](https://github.com/nccgroup/featherduster) by NCC Group can be used to help determine and solve codes.

## Bases

Check all bases with: https://github.com/mufeedvh/basecrack
And the wiki shows some obscure binary to ascii conversions: https://www.wikiwand.com/en/Binary-to-text_encoding

##### Base 2 / Binary
[0-1]

##### Base 8 / Octal
[0-8]


##### Base16 / Hexidecimal
[0-9A-F]
Example:
```
Hey! This is an example of base16 encoding.
```
is:
```
48657921205468697320697320616E206578616D706C65206F662062617365313620656E636F64696E672E
```

Decode with: https://simplycalc.com/base16-encode.php


##### Base32
[_A-Z2-7=_]

Often ends with a multiple `=` to pad remaining text.

Example:
`NBXWYYLDMFZGCY3PNRQQ====`

Decode at: https://simplycalc.com/base32-encode.php

    
##### Base58
[_123456789ABCDEFGHJKLMNPQRSTUVWXYZabcdefghijkmnopqrstuvwxyz_]
    
Example:
`2yJiRg5BF9gmsU6AC`
      
    
##### Base62
[_0-9A-Za-z_]

Example:
`g2AextRZpBKRBzQ9`
        
    
##### Base64 
[_A-Za-z0-9+/=_]

Often ends with a multiple `=` to pad remaining text.

Example:
`aG9sYWNhcmFjb2xh`

**Linux**
```
base64 -w0 <file> #Encode file
base64 -d file #Decode file
```

**Windows**
```
certutil -encode payload.dll payload.b64
certutil -decode payload.b64 payload.dll
```


##### Base85 --> Like Ascii85

---

##### Morse Code

Example:
`.... --- .-.. -.-. .- .-. .- -.-. --- .-.. .-`

Decode at:
* https://morsecode.scphillips.com/translator.html
* https://gchq.github.io/CyberChef/

---

##### Phone Keypad
![https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQSySxHjMFv80XWp74LZpfrnAro6a1MLqeF1F3zpguA5PGSW9ov|150](https://camo.githubusercontent.com/0a09b3f773f371310cba6af9578b5f296a1864de4554760078d0044cb645ea0d/68747470733a2f2f656e637279707465642d74626e302e677374617469632e636f6d2f696d616765733f713d74626e3a414e643947635153795378486a4d4676383058577037344c5a7066726e41726f3661314d4c7165463146337a706775413550475357396f76)

---

##### DNA
When given a sequence with only A, C, G, T , there is an online mapping for these. Try this:
![img/dna_codes.png|400](https://github.com/JohnHammond/ctf-katana/raw/master/img/dna_codes.png)
![img/genome_coding.jpg|300](https://github.com/JohnHammond/ctf-katana/raw/master/img/genome-coding.jpg)

---

##### QR Codes

---


# Hashes

##### MD% / SHA1 / SHA256 / SHA512
Generate hashes here:
https://passwordsgenerator.net/sha512-hash-generator/

---

# Cyphers

##### Keyboard Shift

If you see any thing that has the shape of a sentence but it looks like nonsense letters, and notes some shift left or right, it may be a keyboard shift...

Decode at: https://www.dcode.fr/keyboard-shift-cipher

---

##### Bit Shift

Sometimes the letters may be shifted by a stated hint, like a binary bit shift ( x >> 1 ) or ( x << 1 ).

---

##### Reversed Text

Sometimes a "ciphertext" is just as easy as reversed text. Don't forgot to check under this rock! 

You can reverse a string in [Python](https://www.python.org/) like so:
```py
"UOYMORFEDIHOTGNIYRTEBTHGIMFTCA.TAHTTERCESASISIHT"[::-1]
```

---

##### Simple Substitution
This is simply substituting the letter for the corresponding number in the alphabet. It's a Ceasar Cypher with no shift key.

---

##### Ceasar 
The most classic shift cipher. Substitute the letter for the alphabet number and shift by X.

Here's a one liner to try all letter positions:
```bash
 cipher='jeoi{geiwev_gmtliv_ws_svmkmrep}' ; for i in {0..25}; do echo $cipher | caesar $i; done
```

Decode at: www.dcode.fr/caesar-cipher

---

##### ROT 13

This is a Ceasar Cypher with a shift/key of 13.

ROT-47 is common too apparently.

---

##### Vigenere

A keyword is needed
```text
wodsyoidrods
```

Decode at: 
- https://www.guballa.de/vigenere-solver
- https://www.dcode.fr/vigenere-cipher
- https://www.mygeocachingprofile.com/codebreaker.vigenerecipher.aspx

---

# Steganography
Lots of useful tools, some online.

See notes here:
https://github.com/JohnHammond/ctf-katana#steganography

Notable tools:
* [`steghide`](http://steghide.sourceforge.net/)
    A command-line tool typically used alongside a password or key, that could be uncovered some other way when solving a challenge.
- [StegSeek](https://github.com/RickdeJager/stegseek)
    This is similar to `stegcracker`, but _much_ faster. Can also extract metadata without a password list.
- [StegCracker](https://github.com/Paradoxis/StegCracker)
    Don't ever forget about [`steghide`](http://steghide.sourceforge.net/)! This tool can use a password list like `rockyou.txt` with steghide. SOME IMAGES CAN HAVE MULTIPLE FILED ENCODED WITH MULTIPLE PASSWORDS.
- [Steganography Online](http://stylesuxx.github.io/steganography/)
    A tool often used in CTFs for encoding messages into images.
- [`Stegsolve.jar`](http://www.caesum.com/handbook/stego.htm)
    A [Java](https://en.wikipedia.org/wiki/Java_(programming_language)) [`.JAR`](https://en.wikipedia.org/wiki/JAR_(file_format)) tool, that will open an image and let you as the user arrow through different renditions of the image (viewing color channels, inverted colors, and more). The tool is surprisingly useful.
- [`openstego`](https://www.openstego.com/)
    A [Java](https://en.wikipedia.org/wiki/Java_(programming_language)) [`.JAR`](https://en.wikipedia.org/wiki/JAR_(file_format)) tool, that can extract data from an image. A good tool to use on guessing challenges, when you don't have any other leads. We found this tool after the [Misc50](http://0xahmed.ninja/nullcon-hackim18-ctf-writeups/) challenge from [HackIM 2018](https://ctftime.org/event/566)
- [`zsteg`](https://github.com/zed-0xff/zsteg)
    Command-line tool for use against Least Significant Bit steganography... unfortunately only works against PNG and BMP images.
- [`jsteg`](https://github.com/lukechampine/jsteg)
    Another command-line tool to use against JPEG images. Handy for Hackerrank Codefest CTF 2018.
- [Jstego](https://sourceforge.net/projects/jstego/)
    A GUI tool for JPG steganography. [https://sourceforge.net/projects/jstego/](https://sourceforge.net/projects/jstego/) It is a [Java](https://en.wikipedia.org/wiki/Java_(programming_language)) [JAR](https://en.wikipedia.org/wiki/JAR_(file_format)) file similar to stegsolve.jar