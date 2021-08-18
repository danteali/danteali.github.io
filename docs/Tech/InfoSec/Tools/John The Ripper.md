---
Created: '2021-08-15 20:45:20 +01:00'
Modified: '2021-08-15 22:49:53 +01:00'

---

| Tags: #tools #ctf #pentesting #infosec #kali #passwords #brute-force |
| -------------------------------------------- |

---

More brute-forcing info can be found at: https://book.hacktricks.xyz/brute-force

# John The Ripper

John can be used to crack passwords! It is similar to [hashcat](https://hashcat.net/wiki/doku.php?id=hashcat) but seems more user-friendly (maybe).
*Obviously running in a VM means it will be SLOW!*

It has a LOT of options so worth checking the [readme](https://www.openwall.com/john/doc/README.shtml) online for specific use cases. And the [examples](https://www.openwall.com/john/doc/EXAMPLES.shtml).

While quite old, there is a good cheat sheet here: https://countuponsecurity.files.wordpress.com/2016/09/jtr-cheat-sheet.pdf

###### Linux
It comes bundled with Kail, the binary is at: `/usr/sbin/john`
Additional tools are saved in `/usr/share/john`. These are mainly used to convert various output into a form usable for John. e.g. convert windows hash dumps into john's format.

###### Windows
For a Windows install, see https://kalitut.com/john-the-ripper/. Essentially we need to use cygwin and download a pre-compiled binary from [here](https://github.com/openwall/john-packages/releases/tag/jumbo-dev). 
Just download the binary and extract somewhere local, then access from MobaXterm or WSL. e.g. command from MobaXterm to run binary extracted in downloads folder:
```bash
/drives/c/Users/Ryan/Downloads/winX64_1_JtR/JtR/run/john --test
```

---

###### Usage

If you just run John against a file it will look for hashes and try to crack them:
`john <target_file>`

It will first try  "single crack" mode, then use a wordlist with rules, and finally go for "incremental" mode. See [modes](https://www.openwall.com/john/doc/MODES.shtml) for more details.
You can specify specific 'modes' to use with e.g. 
`john --single passwd_file`

You can obviously specify lots of options when using John e.g. specify a wordlist (John's default wordlist is at: `/usr/share/john/password.lst`) with below command.
*(The `--rules` options tells John to use mangling rules on the words in the list and try the mangled versions too.)*
`john --wordlist=password.lst --rules mypasswd`

You can actually generate the output of the `--rules` as applied to a wordlist (without attempting any cracking) with:
`john --wordlist=<wordlist file> --rules --stdout > rules_applied.txt`

You can also specify the algorithm to use with `--format` if you know what algorithm is needed for your hash. By specifying an algorithm you can make John use the GPU in some instances which will be faster than CPU based cracking. You can list all available formats with (the 'opencl' ones are GPU based):
`john --list=formats`

If you've cracked some passwords, they are stored in `~/.john/john.pot`. The `john.pot` file is not meant to be human-friendly. You should be using John itself to display the contents of its "pot file" in a convenient format:
`john --show mypasswd`

You can also start John in it's own background process with the `--session=<name>` option.
And check the status at any time with:
`john --status`

###### Status
John will occasionally report it's status, or status can be requested using above command. The output looks like:
```bash
0g 0:00:09:01 30.00% 1/3 (ETA: 22:54:26) 0g/s 20.71p/s 20.71c/s 20.71C/s
```

This means:

*   successful guess count ("g"),
*   session duration (in the D:HH:MM:SS format for days, hours, minutes, and seconds),
*   progress indicator (percent done and optionally pass number out of the total number of passes),
*   The four speed metrics are:
    *   g/s is successful guesses per second (so it'll stay at 0 until at least one password is cracked),
    *   p/s is candidate passwords tested per second,
    *   c/s is "crypts" (password hash or cipher computations) per second,
    *   C/s is combinations of candidate password and target hash per second.

###### Benchmarks
You can also run a benchmark/test command to see how well your system is expected to perform:
`john --test`
This also shows the sheer variety of hashes that john can attempt to crack!

---

**Examples:**

**A. Cracking passphrase for SSH keys**
For example if we had someone's private key but not the passphrase so still can't use it to access the target server.

For testing, I generated a new keypair with passphrase `test`. The keypair is just saved as default `id_rsa` filenames. These were copied to a working dir for playing with.

Run `ssh2john` on the `id_rsa`private key file:

```bash
/usr/share/john/ssh2john.py ~/working/john/ssh/id_rsa > id_rsa.john
```

Then run john itself against the output to see if we can get the password. Using john's default wordlist (see below example for custom wordlist):

```bash
john id_rsa.john
```

Once complete we can view results with:

```bash
john --show id_rsa.john
```

<br>

**B. Running against Linux password file**
In linux all hashed passwords are saved in `/etc/shadow` along with other details like date of last password change etc.

If you have access to both the `/etc/passwd` and `/etc/shadow` files, we can use `unshadow` to combine their info so that all user/password info is in one file. This will help john be more efficient as it can use some of the data in `/etc/passwd` to help inform some of it's password guesses.

John will work against `/etc/shadow` even without doing `unshadow` first. 

```bash
sudo unshadow /etc/passwd /etc/shadow > unshadowed
```

Then run John against it using the [Rock You Wordlist](Wordlists.md) wordlist:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt --rules unshadowed
```

And view any results with:

```bash
john --show unshadowed
```

<br>

**C. Cracking Windows Password Hashes**

Still to document.
See:

*   <https://null-byte.wonderhowto.com/how-to/use-john-ripper-metasploit-quickly-crack-windows-hashes-0200322/>
*   <https://www.securitynewspaper.com/2018/11/27/crack-windows-password-with-john-the-ripper/>

---

| Sources:                                                                           |
| ---------------------------------------------------------------------------------- |
| https://www.hackingarticles.in/beginner-guide-john-the-ripper-part-1/              |
| https://www.binarytides.com/cracking-linux-password-with-john-the-ripper-tutorial/ |
| https://miloserdov.org/?p=4961 |