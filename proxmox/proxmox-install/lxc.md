# Creating LXC Containers in Proxmox VE

After the post-installation process and reboot, you are ready to start creating LXC containers and virtual machines.

---

## Creating an LXC Container

To create an LXC container, right-click on the node and select **Create CT**.

![Right-click node](lxcvm-rightclicknode.png)

---

### General Configuration

Set the basic options:
- Node: `server-a`
- CT ID: `102`
- Hostname: `lxc-example`
- Password: set a strong password

![General Tab](lxcvm-createlxc.png)

---

### Template

Select your desired template. In this example, we are using Debian 12.

![Template Tab](lxcvm-templatelxc.png)

---

### Disks

Choose the storage and disk size for the root filesystem.

![Disks Tab](lxcvm-diskslxc.png)

---

### CPU

Assign the number of cores for the container.

![CPU Tab](lxcvm-cpulxc.png)

---

### Memory

Configure the memory and swap allocation.

![Memory Tab](lxcvm-memory.png)

---

### Network

Set the container to use static IP with firewall enabled.

Example configuration:
- IPv4: `196.120.54.99/24`
- Gateway: `196.120.54.1`
- Bridge: `vmbr0`

![Network Tab](lxcvm-network.png)

---

### DNS

Leave default or modify if needed.

![DNS Tab](lxcvm-dns.png)

---

### Confirm Settings

Review and confirm all configuration values before creating the container.

![Confirm Tab](lxcvm-confirmlxc.png)

---

### Creation Process

Once confirmed, the container will be created and you will see the status in the task viewer.

![Creating Container](lxcvm-creatinglxc.png)

---

### Start and Shell Access

Right-click on the created container (CT 102) and click **Start**, then open **Console**.

![Start Container](lxcvm-startlxc.png)
![Console Access](lxcvm-shelllxc.png)

Login with your root credentials to begin configuring the container.

---

## Container Summary

Once started, you can view real-time stats and health of your container.

![Summary View](lxcvm-gotoshell.png)

---

➡️ Proceed to next step: [Creating VM](vm.md)

# Save the markdown 
