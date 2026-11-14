# Builds and Reasoning

## The Director's Assumption
The director assumes that buying four identical machines is the right approach. This is wrong. 
The four roles (Accountant, Sales, Developer, Designer) have completely different workloads. Buying identical machines would mean overpaying for components some people don't need, and under-powering the people who actually need them (like the Designer). By customizing, we stay under the 3,000,000 KZT budget while solving the specific bottlenecks of each role.

---

### Build 1 – Accountant
Load: Heavy Excel spreadsheets with complex formulas, accounting software, and general office applications. Running mostly single-threaded tasks.
Bottleneck: Single-core CPU speed. When calculating large Excel files, the program will freeze or take a long time to recalculate if the CPU single-core speed is low. 16GB RAM is sufficient here.
Trade-off: We did not include a dedicated GPU. The accountant does not need one. We took a mid-range Intel i5 CPU and spent the budget on a reliable 1TB SSD and a standard 24" monitor.

### Build 2 – Sales Manager
Load: CRM in a browser, 30-40 tabs, Excel, and four hours of video calls a day, sometimes all at once.
Bottleneck: Memory, not CPU. Chrome with forty tabs plus a video call is around 11-12 GB. On 8 GB the machine starts swapping in the middle of a customer call, causing massive lag.
Trade-off: Took a Ryzen 5 instead of a Ryzen 7 and spent the saved ~60,000 KZT on 32 GB instead of 16 GB. The CPU idles in this role; the memory does not. No dedicated GPU needed.

### Build 3 – Web Developer
Load: Code editor (VS Code), running local servers, Docker containers, multiple browsers for testing, and compiling code.
Bottleneck: Multi-core CPU performance for faster build times, and RAM for running containers smoothly.
Trade-off: We allocated more budget to an AMD Ryzen 7 CPU and 32GB of RAM. To save money, we skipped the dedicated GPU (integrated graphics are enough for web dev) and kept a standard 24" monitor.

### Build 4 – Designer
Load: Adobe Creative Cloud (Photoshop, Illustrator, Figma), large high-resolution image files, and multi-tasking.
Bottleneck: GPU and Monitor color accuracy. The designer needs a dedicated graphics card to render effects smoothly and a high-resolution, color-accurate monitor to ensure their work looks correct.
Trade-off: This is the most expensive build. We took a mid-range Intel i5 CPU to save money, but spent heavily on an RTX 3060 GPU and a 27" 2K IPS Color-accurate monitor. We kept RAM at 16GB to balance the budget, but left room for upgrade later.

---
 ## Three Report Questions

1. Which of the four machines will you upgrade first, eighteen months from now, and why?
The Web Developer machine. As the project grows, they will run more Docker containers, larger codebases, and heavier test environments. The first thing to fail will be the 32GB of RAM (they will run out). I would upgrade their RAM to 64GB. 
*(Alternative acceptable answer: Upgrade the Designer's RAM to 32GB, as their design files will get larger and Photoshop will start swapping).*

2. Price the same four as pre-built machines from a vendor. What does the company gain and what does it lose by not building them?
*Gain:* Pre-built machines offer a single point of contact for warranty (one phone call fixes everything), corporate support, and immediate delivery.
*Lose:* Pre-built machines (like Dell or HP office PCs) charge a premium. To stay within the 3,000,000 KZT budget for four machines + monitors, we would have to downgrade crucial parts. They often lock down motherboards, making future upgrades difficult. Custom builds give us exactly what each role needs without paying for features we don't use.

3. One of these four people will complain about performance within a month. Which one, and about what?
The Designer will complain. While we bought a great GPU and monitor, 16GB of RAM is the minimum for professional design. When they open multiple large Photoshop files or use After Effects, they will experience lag and the system will start swapping to the disk. We made a deliberate trade-off to fit the budget, but it's the most likely failure point.
*(Alternative acceptable answer: The Developer complaining that 32GB isn't enough if they run heavy virtual machines).*
