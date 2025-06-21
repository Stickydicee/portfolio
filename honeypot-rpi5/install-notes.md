Installing Cowrie on Raspberry Pi 5 (Kali Linux)
#################################################

This guide describes how to install Cowrie in `shell` mode on a Raspberry Pi 5 running Kali Linux. It includes all steps from the official INSTALL.rst, with custom additions for proper SSH port handling, configuration usage, and authbind setup.

Step 1: Install system dependencies
***********************************

Install required system-wide packages:

.. code-block:: shell

    sudo apt update && sudo apt install -y \
      git python3 python3-venv python3-pip libssl-dev libffi-dev \
      build-essential libpython3-dev libevent-dev authbind

Step 2: Create a new user for Cowrie (recommended)
**************************************************

.. code-block:: shell

    sudo adduser --disabled-password cowrie
    su - cowrie

Step 3: Clone the Cowrie repository
***********************************

.. code-block:: shell

    git clone https://github.com/cowrie/cowrie.git
    cd cowrie

Step 4: Setup Python virtual environment
****************************************

.. code-block:: shell

    python3 -m venv cowrie-env
    source cowrie-env/bin/activate
    pip install --upgrade pip
    pip install -r requirements.txt

Step 5: Install configuration file
**********************************

Copy the default configuration to make it editable:

.. code-block:: shell

    cp etc/cowrie.cfg.dist etc/cowrie.cfg

⚠️ **Important:** Always edit `etc/cowrie.cfg`, **not** the `.dist` file.

Step 6: Change system SSH port from 22 to 2201
**********************************************

To free up port 22 for Cowrie, move your system SSH daemon to port 2201:

.. code-block:: shell

    sudo nano /etc/ssh/sshd_config

Find and change:

::

    Port 22

To:

::

    Port 2201

Then restart SSH:

.. code-block:: shell

    sudo systemctl restart ssh

Step 7: Enable listening on port 22 via authbind
************************************************

Authbind allows non-root users to bind to low ports like 22.

.. code-block:: shell

    sudo touch /etc/authbind/byport/22
    sudo chown cowrie:cowrie /etc/authbind/byport/22
    sudo chmod 500 /etc/authbind/byport/22

Then update the Cowrie config (`etc/cowrie.cfg`):

::

    [ssh]
    listen_endpoints = tcp:22:interface=0.0.0.0

Also ensure the following is set:

::

    authbind_enabled = true

Step 8: Start Cowrie
********************

Make sure your environment is activated:

.. code-block:: shell

    source cowrie-env/bin/activate

Then start Cowrie:

.. code-block:: shell

    bin/cowrie stop
    bin/cowrie start

You can check the logs in `var/log/cowrie/` or run `bin/cowrie status`.

