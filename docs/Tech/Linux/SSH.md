---
Created: '2021-08-14 23:19:27 +01:00'
Modified: '2021-08-15 00:40:41 +01:00'

---

| Tags: #linux #ssh |
| ----------------- |

---

# SSH

*include this with other SSH notes when we migrate to Obsidian*

## ssh-pass

Password automation i.e. can pass a password to SSH. The `sshpass` utility is designed to run SSH using the *keyboard-interactive* password authentication mode, but in a non-interactive way.

**Examples:**

**A. Pass plain text on command line **

Use the `-p` (this is considered the least secure choice and shouldn't be used):

```shell
sshpass -p !4u2tryhack ssh username@host.example.com
```

Or can use `-p` with a password saved in a file but `-f` is better for that (see below):

```shell
sshpass -p $(cat pass_file) ssh username@host.example.com
```

The `-p` option looks like this when used in a shell script:

```shell
$ sshpass -p !4u2tryhack ssh -o StrictHostKeyChecking=no username@host.example.com
```

**B. Read password from a file**

Use the `-f` option (the password should be the first line of the filename):

```shell
echo '!4u2tryhack' >pass_file
chmod 0400 pass_file
sshpass -f pass_file ssh username@host.example.com
```

Here is the `-f` option when used in shell script:

```shell
$ sshpass -f pass_file ssh -o StrictHostKeyChecking=no username@host.example.com
```

C. Use the `-e` option to pull password from environment variable `SSHPASS`:

```shell
$ SSHPASS='!4u2tryhack' sshpass -e ssh username@host.example.com
```

The `-e` option when used in shell script looks like this:

```shell
$ SSHPASS='!4u2tryhack' sshpass -e ssh -o StrictHostKeyChecking=no username@host.example.com
```

| Sources:                                                 |
| -------------------------------------------------------- |
| <https://www.redhat.com/sysadmin/ssh-automation-sshpass> |
