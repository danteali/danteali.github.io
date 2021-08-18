---
Created:  '2021-08-17 15:44:11 +01:00'
Modified: '2021-08-17 15:44:11 +01:00'
---

| Tags: #tools #ctf #pentesting #infosec #kali #binwalk |
| ----- |

---
# Miscellaneous Tools

## binwalk
A command-line tool to carve files out of another file. Usage to extract is `binwalk -e [filename]` and it will create a _[filename]_extracted directory.

---

## strings
Tool to find text strings inside binary files. VERY useful in CTFs etc
```bash
strings <filename>
```

---

## ltrace
Program that runs and analyses specified command until it exits. It intercepts and records the dynamic library calls which are called by the executed process and the signals which are received by that process.
You can use it to see exactly what a program is doing and can often be used in CFTs etc to find passwordss etc being passed as part of a command running.
```bash
ltrace <command>
```
