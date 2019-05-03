<img src="https://github.com/geoportti/Logos/blob/master/geoportti_logo_300px.png">

# Use of cPouta

This article gives the general overview of how to use the CSC's cPouta cloud. For more detailed information visit [CSC's Pouta user guide](https://research.csc.fi/pouta-user-guide).

## Introduction

cPouta is a cloud environment, where users set up their own virtual machines (VM). The computational resources of the VMs can be configures for different purposes, from web servers to numerical analysis.

The user first logs to [cPouta web UI](https://pouta.csc.fi) with the credentials from CSC, and sets up a virtual machine. After the VM is running, the user connects to it using SSH and installs the required software like on any desktop machine.

## Getting credentials

First thing you need is to have credentials to the cPouta and have an active computing project from CSC. Information on obtaining those can be found at [here](https://research.csc.fi/csc-guide-projects-and-resource-allocation).

## Creating a virtual machine

Log in to [cPouta web UI](https://pouta.csc.fi). In the **Instances** tab you can launch new VMs by clicking the **Launch Instance** button, which opens a new window. Select appropriate flavor and parameters for the VM. More detailed information about the different VM flavors [here](https://research.csc.fi/pouta-flavours). **Important**:
- Remember to select Key Pair in the **Access & Security** tab.
- Remember to select **ssh** from the **Security Groups**.

If you forget either one, you will not be able to log in to the VM. Info on how to generate SSH keys [here](https://research.csc.fi/pouta-getting-started#Runningyourfirstrealmachine-Settingupkeys).

Once you have selected proper values for the parameters, click **Launch** and wait until the machine appear on the instances list with the **Power State** "running".

All that is left to do in the web UI is to add a public IP address to the VM. This can be done by clicking the small downwards arrow next to the **Create Snapshot** button in the instances list, and clicking on **Associate Floating IP**. Once the IP address is set, you are ready to connect to your new virtual machine.

For more detailed information about creating VMs [here](https://research.csc.fi/pouta-getting-started).

## Connecting to VM

Connecting to the VM happens via SSH. On Windows the de facto program is [PuTTY](https://www.putty.org). On Unix-like systems any terminal will do, simple give the command
```
ssh username@<public_IP_address> -i keyfile.pem
```
The username is defined in the VM image that you used to create the VM. For example, in Ubuntu 14 and 16 the username is **cloud-user**, whereas in Ubuntu 18 it is set to **ubuntu**.  More information on connecting to VMs [here](https://research.csc.fi/pouta-connecting-a-virtual-machine).

## Setting up VM

Once you have managed to connect to your VM, there are no general instructions on how to proceed. You have a root access to the VM, and you can install any software you need. It is recommended to use the package managers, for example **apt** if you created the VM from Ubuntu image. Additional ports can be opened from the web UI for different servers.

## Billing

Remember that a running VM will use your billing units all the time, whether it is actually doing something or just sitting idle. If you know that you will not need the VM for a long time, it is beneficial to **shelve** the instance. This means that the machine is shutdown and stored elsewhere. You can then **unshelve** it when you need it running again. However, especially for larger VMs unshelving may take some time, depending on the usage of the cPouta. More info [here](https://research.csc.fi/pouta-vm-lifecycle).

## More information

You can find more detailed information on using Taito from [CSC's Pouta user guide](https://research.csc.fi/pouta-user-guide).

## Usage and Citing

When used, the following citing should be mentioned: "We made use of geospatial
data/instructions/computing resources provided by the Open Geospatial
Information Infrastructure for Research (oGIIR,
urn:nbn:fi:research-infras-2016072513) funded by the Academy of Finland."
