# Creating LXC Containers in Proxmox VE

After the post-installation process and reboot, you are ready to start creating LXC containers and virtual machines.

To simplify the setup process, I primarily use helper scripts, which are also referenced in the [post-install.md](post-install.md) documentation.  
Specifically, I use the advanced installation method with helper scripts to apply my own configuration.  
The same configuration steps performed by those scripts are reflected throughout this documentation.

---

## Creating an LXC Container

To create an LXC container, right-click on the node and select **Create CT**.

![Right-click node](../images/lxc-vm/lxcvm-rightclicknode.png)

---

### General Configuration

Set the basic options:
- Node: `server-a`
- CT ID: `102`
- Hostname: `lxc-example`
- Password: set a strong password

![General Tab](../images/lxc-vm/lxcvm-createlxc.png)

---

### Template

Select your desired template. In this example, we are using Debian 12.

![Template Tab](../images/lxc-vm/lxcvm-templatelxc.png)

---

### Disks

Choose the storage and disk size for the root filesystem.

![Disks Tab](../images/lxc-vm/lxcvm-diskslxc.png)

---

### CPU

Assign the number of cores for the container.

![CPU Tab](../images/lxc-vm/lxcvm-cpulxc.png)

---

### Memory

Configure the memory and swap allocation.

![Memory Tab](../images/lxc-vm/lxcvm-memorylxc.png)

---

### Network

Set the container to use static IP with firewall enabled.

Example configuration:
- IPv4: `196.120.54.99/24`
- Gateway: `196.120.54.1`
- Bridge: `vmbr0`

![Network Tab](../images/lxc-vm/lxcvm-networklxc.png)

---

### DNS

Leave default or modify if needed.

![DNS Tab](../images/lxc-vm/lxcvm-dnslxc.png)

---

### Confirm Settings

Review and confirm all configuration values before creating the container.

![Confirm Tab](../images/lxc-vm/lxcvm-confirmlxc.png)

---

### Creation Process

Once confirmed, the container will be created and you will see the status in the task viewer.

![Creating Container](../images/lxc-vm/lxcvm-creatinglxc.png)

---

### Start and Shell Access

Right-click on the created container (CT 102) and click **Start**, then open **Console**.

![Start Container](../images/lxc-vm/lxcvm-startlxc.png)

Login with your root credentials to begin configuring the container.

![Console Access](../images/lxc-vm/lxcvm-shelllxc.png)

---

## Container Summary

Once started, you can view real-time stats and health of your container.

![Summary View](../images/lxc-vm/lxcvm-gotoshelllxc.png)

---

➡️ Proceed to next step: [Creating VM](vm.md)
