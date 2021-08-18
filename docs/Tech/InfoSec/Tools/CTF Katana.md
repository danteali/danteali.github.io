---
Created:  '2021-08-17 11:30:31 +01:00'
Modified: '2021-08-17 11:30:31 +01:00'
---

| Tags: #tools #ctf #pentesting #infosec #kali |
| ----- |

---

> # Key Takeaways / Things to Remember
> **Couldn't get working!**
> 
> The CTF Katana notes repo is an excellent resource: 
> https://github.com/JohnHammond/ctf-katana
>
> And reading the code/info in the tool site can give insight on how to use the various tools.

---
# [Katana](https://github.com/JohnHammond/katana)
[Docs](https://ctf-katana.readthedocs.io/en/latest/installation.html)

Also see this repo which John used to document lots of notes related to CTFs: 
[CTF Katana](https://github.com/JohnHammond/ctf-katana)

Attempts to offer code and material to automate "running through the check-list" or hitting the "low-hanging fruit" in a Capture the Flag challenge.

May be slightly outdated now but still useful.

Clone the repo to a useful location and run setup:
```bash
cd ~/working/tools
git clone https://github.com/JohnHammond/katana
```

Install dependencies - including a bunch of tools useful in CTFs:
```bash
sudo apt update
sudo apt-get install -y python3-venv python-tk tk-dev libffi-dev libssl-dev pandoc \
	libgmp3-dev libzbar-dev tesseract-ocr xsel libpoppler-cpp-dev libmpc-dev \
	libdbus-glib-1-dev ruby apktool nodejs groff binwalk \
	foremost tcpflow poppler-utils exiftool steghide stegsnow bison ffmpeg \
	libgd-dev less
```

Setup (may need to change python command to reflect the python3 version installed - should be >3.7):
```bash
python3.9 -m venv env
source env/bin/activate
python setup.py install
```
Above commands do:
- Create a python virtual environment in `cd ~/working/tools/katana`  - new `env` folder now exists in directory.
	If setup fails we can simply remove the virtual environment and start again by deleting `env`
- Activate the environment - deactivate with `deactivate`
- Run setup script

### COULDN'T GET WORKING LOCALLY IN KALI - KEPT GETTING ERRORS DURING SETUP

---

## Docker

1. **Build Image**
	A docker build is also available which is probably easier. Build the image using the dockerfile inside the `docker` directory.
	```bash
	docker build -t katana .
	```

	### Note that build fails due to missing package: `libenchant-dev`

> Docker doesn't come bundled with Kali. 
> To install docker:
>```bash
>sudo apt-get install docker
>```
> Then create a `docker` group (it likely already exists after install - check with `less /etc/groups`) and add user to the group to allow running docker commands without sudo:
>```bash
> sudo groupadd docker
> sudo usermod -aG docker $USER
>```
> Logout and login again, or run this command to process group change without relogging: `newgrp docker`

2. **Configuration**
	Add a `katana.ini` file to the docker data directory, containing:
	```
	[manager]
	flag-format=FLAG{.*?}
	# Output directory
	outdir=./results
	```
	*See full details about config file [here](https://ctf-katana.readthedocs.io/en/latest/getting-started.html#configuration)*
	The config file can be updated to reflect the current flag format being used in any given challenge. 

3. **Run docker container**
	```bash
	docker run -v "~/working/tools/katana/docker_data:/data" -it katana
	```

4. **Process files**
	Target files can be placed in the `targets` directory and Katana will automatically detect the target type and attempt to solve common CTF challenges e.g. finding data inside an image, pull data from a PCAP file, ...