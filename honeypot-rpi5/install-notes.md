🛠️ Cowrie Installation Notes (Raspberry Pi 5 – Kali Linux)

This document covers the installation steps for running the Cowrie SSH honeypot on a Raspberry Pi 5 running Kali Linux.

🧾 System Info

Device: Raspberry Pi 5

OS: Kali Linux ARM (64-bit)

Python version: 3.11+

Cowrie version: latest from GitHub

✅ Step-by-step Installation

1. Update the system

sudo apt update && sudo apt upgrade -y

2. Move default SSH to port 2201 (so port 22 is free for Cowrie)

Edit the SSH server configuration file:

sudo nano /etc/ssh/sshd_config

Find the line:

#Port 22

Change it to:

Port 2201

Then restart the SSH server:

sudo systemctl restart ssh

Make sure to test your connection with:

ssh -p 2201 user@ip_address

3. Install required dependencies

sudo apt install -y authbind python3-venv git

4. Clone Cowrie from GitHub

git clone https://github.com/cowrie/cowrie.git
cd cowrie

5. Set up the Python virtual environment

python3 -m venv cowrie-env
source cowrie-env/bin/activate

6. Install Cowrie Python dependencies

pip install --upgrade pip
pip install -r requirements.txt

7. Create the Cowrie user

sudo adduser --disabled-password cowrie

Press ENTER for all user info prompts.

8. Install Cowrie configuration

Run:

cp etc/cowrie.cfg.dist etc/cowrie.cfg

Important: Make all Cowrie configuration changes in etc/cowrie.cfg – not in cowrie.cfg.dist.

9. Listening on port 22 with Authbind

Cowrie cannot bind to privileged ports (<1024) without root, so we use authbind:

Grant access:

sudo touch /etc/authbind/byport/22
sudo chown cowrie /etc/authbind/byport/22
sudo chmod 770 /etc/authbind/byport/22

Edit the config file:

nano etc/cowrie.cfg

Set:

listen_endpoints = tcp:22:interface=0.0.0.0

Then make sure Cowrie uses authbind:

bin/cowrie stop
AUTHBIND=yes bin/cowrie start

Cowrie should now be running and accepting SSH connections on port 22 while your real SSH server is on port 2201.

✅ Done!

