🧰 Cowrie Honeypot Installation Guide (Raspberry Pi 5 + Kali Linux)
===================================================================

This guide walks you through installing Cowrie on a Raspberry Pi 5 running Kali Linux.
You’ll set up a dedicated user, create a virtual environment, adjust your SSH settings, and start the honeypot.

Step 1: Install system dependencies
***********************************

First, install all required base packages.
Python packages will be installed later.

On Debian-based systems::

    $ sudo apt-get install git python3-pip python3-venv libssl-dev libffi-dev build-essential libpython3-dev python3-minimal authbind

Step 2: Create a user account
*****************************

It’s recommended to run Cowrie under a non-root user::

    $ sudo adduser --disabled-password cowrie

Then switch to that user::

    $ sudo su - cowrie

Step 3: Clone the repository
****************************

Get the Cowrie code from GitHub::

    $ git clone http://github.com/cowrie/cowrie
    $ cd cowrie

Step 4: Set up the virtual environment
**************************************

Create the virtual environment and install Python packages::

    $ python3 -m venv cowrie-env
    $ source cowrie-env/bin/activate
    (cowrie-env) $ python -m pip install --upgrade pip
    (cowrie-env) $ python -m pip install --upgrade -r requirements.txt

Step 5: Set up the configuration
********************************

Cowrie uses two config files: `cowrie.cfg.dist` (defaults) and `cowrie.cfg` (your custom settings).

To create your editable config::

    $ cp etc/cowrie.cfg.dist etc/cowrie.cfg

**Only edit `cowrie.cfg`.**  
Do not make changes to `cowrie.cfg.dist` — it will be overwritten on updates.

You can enable individual services like telnet by adding this to `cowrie.cfg`::

    [telnet]
    enabled = true

Step 6: Start Cowrie and change system SSH port
***********************************************

Start Cowrie with::

    $ bin/cowrie start

If you want Cowrie to listen on port 22, first change the system SSH daemon to a different port.

Edit the SSH configuration::

    $ sudo nano /etc/ssh/sshd_config

Find this line::

    Port 22

Change it to::

    Port 2201

Then restart SSH::

    $ sudo systemctl restart ssh

Step 7: Listening on port 22 (OPTIONAL)
***************************************

There are three ways to make Cowrie listen on port 22: `iptables`, `authbind`, or `setcap`.

Iptables
========

Redirect incoming traffic on port 22 to Cowrie’s default port 2222::

    $ sudo iptables -t nat -A PREROUTING -p tcp --dport 22 -j REDIRECT --to-port 2222

For telnet::

    $ sudo iptables -t nat -A PREROUTING -p tcp --dport 23 -j REDIRECT --to-port 2223

Test these only from another machine — they don’t affect localhost.

MacOS::

    $ echo "rdr pass inet proto tcp from any to any port 22 -> 127.0.0.1 port 2222" | sudo pfctl -ef -

Authbind
========

To allow a non-root user to bind to port 22 using authbind::

    $ sudo apt-get install authbind
    $ sudo touch /etc/authbind/byport/22
    $ sudo chown cowrie:cowrie /etc/authbind/byport/22
    $ sudo chmod 770 /etc/authbind/byport/22

Also update `bin/cowrie` to enable authbind support (set `AUTHBIND_ENABLED` to `yes`).

Then in `cowrie.cfg` change the port::

    [ssh]
    listen_endpoints = tcp:22:interface=0.0.0.0

Step 8: Stopping and restarting Cowrie
**************************************

To restart Cowrie after making changes::

    $ bin/cowrie stop
    $ bin/cowrie start
