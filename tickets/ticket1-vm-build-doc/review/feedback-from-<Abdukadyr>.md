# Feedback on <Aimaral Baiduisen>'s BUILD.md
Reviewer: <Akhazik Abdukadyr>
Commit reviewed: <https://github.com/Aknazik07/osarch-abdukadirova/tree/c570d33de87ecf000423d9d5109bac39e7a60d4f/tickets>
Hypervisor I used: VMware Workstation 

## First step where I got stuck
Step number:Step 1
What the step says:"Open VMware Workstation and click 'Create a New Virtual Machine'."
What I did:I clicked the button and the "New Virtual Machine Wizard" popped up.
What happened / what I had to guess:The document jumps straight from clicking the button to the disk settings in Step 2. It doesn't tell me whether to choose "Typical" or "Custom", nor does it tell me which OS to select Linux/Ubuntu. As a beginner, I had to guess that I should pick "Typical" and find Ubuntu in the list.


## Other places I hesitated
Step 2: The document says "Set the virtual disk size to 40GB". It doesn't mention what to do with the "Store virtual disk as a single file" vs "Split virtual disk into multiple files" options. I had to guess and just left it on the default.

Step 4: It says "I checked the system details", but it doesn't actually provide the command like e.g., uname -a in the text. If I didn't know Linux, I wouldn't know how to check the system details.

## Settings I would not have chosen without the document
- I would not have known to choose NAT for the network adapter in Step 3. The document gave a great explanation of why NAT is better than Bridged for the university network. Without this document, I would have probably just left it on Bridged.

## One thing that worked well
The screenshots are very clear and perfectly match the text. I could easily see exactly where to click for the disk size and the NAT settings.
