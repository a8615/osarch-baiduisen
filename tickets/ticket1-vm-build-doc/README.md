# Ticket 1 — VM build document

## 1. What was asked

> From: Aigerim T. (Office Manager)
> Subject: test machine for new dev
>
> Hi, we have someone starting on Monday and he needs a test computer set up. Nothing special, just so he can try things without breaking anything. Can you write down how to do it so I can do the next one myself? Thanks

## 2. What was actually needed
The request leaves out several critical details. I had to make the following assumptions:
*   *What is a "test computer"?* Aigerim didn't specify. Because she said "without breaking anything," I assumed a *Virtual Machine (VM)* is required, rather than a physical machine that could be broken.
*   *What OS?* The request doesn't say. Since the new developer needs to test things, I assumed we need both a *Linux (Ubuntu)* and a *Windows* guest.
*   *What are the resources?* The request doesn't specify RAM or disk space. Based on my host machine's real specs (16GB RAM, 512GB SSD), I decided to allocate 4GB RAM and 40GB disk to the Linux VM, and 4GB RAM and 50GB disk to the Windows VM so as not to overload the host.
*   *Network?* I assumed the VMs need internet access. I used a NAT network.

## 3. What I did
I created two virtual machines in VMware Workstation. 
(Here I will summarize the build process. The detailed steps are in BUILD.md)

*   Created VM 1 (Ubuntu Server/GUI)
*   Created VM 2 (Windows 11)
*   Set up NAT networking for both.
## 4. Evidence
*   [evidence/01-new-vm-wizard.png](evidence/01-new-vm-wizard.png) — Shows the initial VM creation wizard.
*   [evidence/02-disk-settings.png](evidence/02-disk-settings.png) — Shows the disk allocation (e.g., 40GB).
*   [evidence/03-network-adapter.png](evidence/03-network-adapter.png) — Shows the network adapter set to NAT.
*   [evidence/05-ping-between-guests.txt](evidence/05-ping-between-guests.txt) — Shows the successful ping test between the Linux VM and the Windows VM.
## 5. What I would do differently
If I did this again, I would create a "linked clone" or use a template instead of a full installation, which would save a massive amount of time and disk space. Also, I would ask Aigerim if the new developer actually needs a GUI on the Ubuntu machine, because a headless server would use far fewer resources.

