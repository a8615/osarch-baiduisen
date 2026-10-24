Resources: I gave the VM 2 vCPUs and 4GB of RAM. My host has 8 threads and 16GB RAM, so this leaves enough power and memory for the Windows VM in Lab 2. I also used a 25GB dynamically allocated disk to save space. 
What I broke: I used Option A (deleted /etc/hostname). I confirmed it was broken because cat /etc/hostname returned "No such file". I then reverted to the clean-install snapshot. 
What didn't work: SSH kept timing out, so I transferred the file using VMware Shared Folders instead.
