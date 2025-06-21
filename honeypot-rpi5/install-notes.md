# 🛠️ Installing Cowrie on Raspberry Pi 5 (Kali Linux)

This guide describes how to install Cowrie in `shell` mode on a Raspberry Pi 5 running Kali Linux. It includes all steps from the official INSTALL.rst, with custom additions for proper SSH port handling, configuration usage, and authbind setup.

---

## Step 1: Install system dependencies

Install required system-wide packages:

```bash
sudo apt update && sudo apt install -y \
  git python3 python3-venv python3-pip libssl-dev libffi-dev \
  build-essential libpython3-dev libevent-dev authbind

Step 2: Create a new user for Cowrie (recommended)

sudo adduser --disabled-password cowrie
su - cowrie

Step 3: Clone the Cowrie repository

git clone https://github.com/cowrie/cowrie.git
cd cowrie

Step 4: Setup Python virtual environment

python3 -m venv cowrie-env
source cowrie-env/bin/activate
pip install --upgrade pip
pip install -r requirements.txt

Step 5: Install configuration file

Copy the default config to make it editable:

cp etc/cowrie.cfg.dist etc/cowrie.cfg

⚠️ Important: Always edit etc/cowrie.cfg.
Do not edit cowrie.cfg.dist — that file is overwritten on updates.
Step 6: Change system SSH port from 22 to 2201

To allow Cowrie to use port 22, move your system SSH to another port:

sudo nano /etc/ssh/sshd_config

Find:

Port 22

Change to:

Port 2201

Then apply the change:

sudo systemctl restart ssh

Step 7: Enable listening on port 22 via authbind

Give the Cowrie user permission to bind to port 22:

sudo touch /etc/authbind/byport/22
sudo chown cowrie:cowrie /etc/authbind/byport/22
sudo chmod 500 /etc/authbind/byport/22

Then in etc/cowrie.cfg, set:

[ssh]
listen_endpoints = tcp:22:interface=0.0.0.0

Also ensure:

authbind_enabled = true

Step 8: Start and stop Cowrie

Make sure your virtual environment is active:

source cowrie-env/bin/activate

Start and stop Cowrie:

bin/cowrie stop
bin/cowrie start

Check the logs in:

var/log/cowrie/cowrie.log

✅ Done

Cowrie is now running on port 22 and logging SSH activity.

Test with:

ssh root@<your-pi-ip> -p 22
