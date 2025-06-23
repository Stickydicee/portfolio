🧰 Cowrie Honeypot Installation Guide (Raspberry Pi 5 + Kali Linux)
===================================================================

This guide walks you through installing Cowrie on a Raspberry Pi 5 running Kali Linux.
You’ll set up a dedicated user, create a virtual environment, adjust your SSH settings, and start the honeypot.

Step 1: Install system dependencies
***********************************

First, install all required base packages.
Python packages will be installed later.

On Debian-based systems:

.. code-block:: bash

    sudo apt-get install git python3-pip python3-venv libssl-dev libffi-dev build-essential libpython3-dev python3-minimal authbind

Step 2: Create a user account
*****************************

It’s recommended to run Cowrie under a non-root user:

.. code-block:: bash

    sudo adduser --disabled-password cowrie

Then switch to that user:

.. code-block:: bash

    sudo su - cowrie

Step 3: Clone the repository
****************************

Get the Cowrie code from GitHub:

.. code-block:: bash

    git clone http://github.com/cowrie/cowrie
    cd cowrie

Step 4: Set up the virtual environment
**************************************

Create the virtual environment and install Python packages:

.. code-block:: bash

    python3 -m venv cowrie-env
    source cowrie-env/bin/activate
    python -m pip install --upgrade pip
    python -m pip install --upgrade -r requirements.txt

Step 5: Set up the configuration
********************************

Cowrie uses two config files: `cowrie.cfg.dist` (defaults) and `cowrie.cfg` (your custom settings).

To create your editable config:

.. code-block:: bash

    cp etc/cowrie.cfg.dist etc/cowrie.cfg

**Only edit `cowrie.cfg`.**  
Do not make changes to `cowrie.cfg.dist` — it will be overwritten on updates.

You can enable individual services like telnet by adding this to `cowrie.cfg`::

    [telnet]
    enabled = true

Step 6: Start Cowrie and change system SSH port
***********************************************

Start Cowrie with:

.. code-block:: bash

    bin/cowrie start

If you want Cowrie to listen on port 22, first change the system SSH daemon to a different port.

Edit the SSH configuration:

.. code-block:: bash

    sudo nano /etc/ssh/sshd_config

Find this line::

    Port 22

Change it to::

    Port 2201

Then restart SSH:

.. code-block:: bash

    sudo systemctl restart ssh

Step 7: Listening on port 22 with Authbind
***************************************

To allow a non-root user to bind to port 22 using authbind:

.. code-block:: bash

    sudo apt-get install authbind
    sudo touch /etc/authbind/byport/22
    sudo chown cowrie:cowrie /etc/authbind/byport/22
    sudo chmod 770 /etc/authbind/byport/22

Also update `bin/cowrie` to enable authbind support (set `AUTHBIND_ENABLED` to `yes`).

Then in `cowrie.cfg` change the port::

    [ssh]
    listen_endpoints = tcp:22:interface=0.0.0.0

Step 8: Stopping and restarting Cowrie
**************************************

To restart Cowrie after making changes:

.. code-block:: bash

    $ bin/cowrie stop
    $ bin/cowrie start
