## Build Document: How to set up a test VM

This document explains how to set up the Ubuntu and Windows test VMs from scratch using VMware Workstation.

## Step 1: Creating the Virtual Machine

Open VMware Workstation and click "Create a New Virtual Machine".

*Why this option?* We use the standard installation wizard so we can set specific hardware limits manually, rather than letting VMware guess.

![New VM Wizard](evidence/01-new-vm-wizard.png)

## Step 2: Disk Settings

Set the virtual disk size to 40GB for the Linux VM.

*Why 40GB?* My host machine has a 512GB SSD. Allocating 40GB for the Linux VM and 50GB for the Windows VM leaves enough space on the host for my actual operating system. 
