# Ticket 1 — VM build document

## 1. What was asked

From: Aigerim T. (Office Manager)
Subject: test machine for new dev

Hi, we have someone starting on Monday and he needs a test computer set up. Nothing special, just so he can try things without breaking anything. Can you write down how to do it so I can do the next one myself? Thanks

## 2. What was actually needed
The request leaves out several critical details. I had to make the following assumptions:
*   *What is a "test computer"?* Aigerim didn't specify. Because she said "without breaking anything," I assumed a *Virtual Machine (VM)* is required, rather than a physical machine that could be broken.
*   *What OS?* The request doesn't say. Since the new developer needs to test things, I assumed we need both a *Linux (Ubuntu)* and a *Windows* guest.
*   *What are the resources?* The request doesn't specify RAM or disk space. Based on my host machine's real specs (16GB RAM, 512GB SSD), I decided to allocate 4GB RAM and 40GB disk to the Linux VM, and 4GB RAM and 50GB disk to the Windows VM so as not to overload the host.
*   *Network?* I assumed the VMs need internet access. I used a NAT network.

## 3. What I did
1. Opened VMware and created the Ubuntu VM.
2. Created the Windows 11 VM.
3. Set both to use NAT networking.
4. Checked the system info in Ubuntu.
5. Ran a ping test between the two machines.
6. Took a snapshot of the clean install.

## 4. Evidence

*   [evidence/01-new-vm-wizard.png](evidence/01-new-vm-wizard.png) — Starting the VM wizard.
*   [evidence/02-disk-settings.png](evidence/02-disk-settings.png) — Setting the disk to 40GB.
*   [evidence/03-network-adapter.png](evidence/03-network-adapter.png) — Choosing NAT mode.
*   [evidence/04-guest-uname.txt](evidence/04-guest-uname.txt) — Ubuntu system info.
*   [evidence/05-ping-between-guests.txt](evidence/05-ping-between-guests.txt) — Ping test (0% loss).
*   [evidence/06-snapshot-list.png](evidence/06-snapshot-list.png) — The snapshot list.

## 5. What I would do differently
Next time, I would allocate 8GB of RAM to the Windows 11 VM instead of 4GB. When I turned it on, it was lagging a lot, and since my host has 16GB, it would run much smoother. I would also give my snapshot a better name than just "clean-install".

