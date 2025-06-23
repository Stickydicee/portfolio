🔔 Cowrie & Slack Alert Integration Guide
=========================================

This guide explains how to connect your Cowrie honeypot to Slack.  
You'll set up a Python script that sends instant notifications to a Slack channel when something happens in the honeypot.

Step 1: Requirements
********************

Before you begin, make sure:

- Cowrie is installed and working
- You have a Slack workspace (with permission to create an app)

Step 2: Write the Python Alert Script
*************************************

Go to the Cowrie directory:

.. code-block:: bash

     cd ~/cowrie
     nano slack_alerts.py

Paste the contents of the `slack_alerts.py <https://github.com/Stickydicee/portfolio/blob/main/honeypot-rpi5/slack_alerts.py>`_ found in this repo or create one using the same structure.

Update the following two values in the script:

- Set `WEBHOOK_URL` to your own Slack webhook URL
- Point `LOG_FILE` to your Cowrie log file path  
  (for example: `/home/cowrie/cowrie/var/log/cowrie/cowrie.log`)

Step 3: Configure the Slack Webhook
***********************************

1. Open: https://api.slack.com/apps  
2. Choose **Create New App > From Scratch**
3. Give the app a name and link it to your workspace
4. In features, select **Incoming Webhooks**
5. Enable Incoming Webhooks
6. Click **Add New Webhook to Workspace**
7. Pick the Slack channel where alerts should go
8. Copy the Webhook URL

Paste this URL into your Python script under `WEBHOOK_URL`.

Step 4: Save and Launch the Script
**********************************

Make the script executable (optional):

.. code-block:: bash

    chmod +x slack_alerts.py

Then run it:

.. code-block:: bash

    python3 slack_alerts.py

Leave this running in a terminal window, or run it in the background using tools like `screen` or `tmux`.

Step 5: Try It Out
******************

Use this command to simulate an interaction with Cowrie:

.. code-block:: bash

    ssh cowrie@localhost

Try logging in or running a few fake commands. You should see Slack alerts like:

- 🔐 Login Attempt
- 💻 Command Executed
- 📥 File Download Attempt
- 🔌 New Session Started
- 📴 Session Ended

Step 6: Run the script in the background (tmux)
***********************************************

You can keep the script running in the background using `tmux`.

Start a new tmux session:

.. code-block:: bash

    tmux new -s slackmonitor
    python3 slack_alerts.py

Leave the script running and detach from tmux by pressing:

**Ctrl + B**, then **D**

To return to the session later:

.. code-block:: bash

    tmux attach -t slackmonitor

Step 7: Run Slack Alerts Automatically on Boot
===============================================

To ensure the Slack alert script runs automatically after reboot, we configure it as a systemd service. Additionally, Cowrie itself should also start automatically.

Step 7.1: Create a systemd service for Cowrie
******************

Create a new service file:

.. code-block:: bash

    sudo nano /etc/systemd/system/cowrie.service

Paste the contents of the `cowrie.service <https://github.com/Stickydicee/portfolio/blob/main/honeypot-rpi5/cowrie.service>`_ to configure it as a systemd service.

Save and enable the service:

.. code-block:: bash

    sudo systemctl daemon-reload
    sudo systemctl enable cowrie
    sudo systemctl start cowrie

Step 7.2: Create a systemd service for Slack Alerts
******************

Now create a service for the Slack alert script:

.. code-block:: bash

    sudo nano /etc/systemd/system/slackalerts.service

Paste the contents of the `slackalerts.service <https://github.com/Stickydicee/portfolio/blob/main/honeypot-rpi5/slackalerts.service>`_ to configure it as a systemd service.

Enable and start the service:

.. code-block:: bash

    sudo systemctl daemon-reload
    sudo systemctl enable slackalerts
    sudo systemctl start slackalerts

Step 7.3: Verify both services
******************

After rebooting your Raspberry Pi, verify both services:

.. code-block:: bash

    systemctl status cowrie
    systemctl status slackalerts

You should see both listed as ``active (running)``.  
Slack alerts will now be sent automatically every time Cowrie detects interaction.
