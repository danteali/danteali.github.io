---
Created:  '2021-08-17 14:58:38 +01:00'
Modified: '2021-08-17 14:58:38 +01:00'
---

| Tags: #tools #ctf #pentesting #infosec #kali #cryptography #crypto |
| ----- |

---


# Common Cryptography

---


| Sources                                                           |
| ----------------------------------------------------------------- |
| https://book.hacktricks.xyz/crypto/crypto-ctfs-tricks#easy-crypto |
| https://www.boxentriq.com/code-breaking/cipher-identifier         |
| https://www.dcode.fr/cipher-identifier |

---

##### XOR
The basic idea behind XOR – encryption is, if you don’t know the XOR-encryption key before decrypting the encrypted data, it is impossible to decrypt the data.

[https://wiremask.eu/tools/xor-cracker/](https://wiremask.eu/tools/xor-cracker/)

---

##### Bifid

A keyword is needed
```text
fgaargaamnlunesuneoa
```


---


##### Fernet

2 base64 strings (token and key)

Token:
```text
gAAAAABWC9P7-9RsxTz_dwxh9-O2VUB7Ih8UCQL1_Zk4suxnkCvb26Ie4i8HSUJ4caHZuiNtjLl3qfmCv_fS3_VpjL7HxCz7_Q==
```
Key:
```text
-s6eI5hyNh8liH7Gq0urPC-vzPgNnxauKvRO4g03oYI=
```

- [https://asecuritysite.com/encryption/ferdecode](https://asecuritysite.com/encryption/ferdecode)
    
---


##### Samir Secret Sharing

A secret is split in X parts and to recover it you need Y parts (_Y <=X_).

```text
8019f8fa5879aa3e07858d08308dc1a8b45
80223035713295bddf0b0bd1b10a5340b89
803bc8cf294b3f83d88e86d9818792e80cd
```

* *[http://christian.gen.co/secrets/](http://christian.gen.co/secrets/)