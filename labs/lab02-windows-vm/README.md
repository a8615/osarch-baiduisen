Network: I used NAT. It allows VMs to reach each other and the internet. Bridged failed due to campus MAC filtering. Host-only has no internet.
· Firewall: Ping failed initially because Windows blocks ICMP by default. I added a rule to allow ICMPv4 from LocalSubnet and I did not turn off the firewall.
· Experiment: Host RAM is 15.7 GB. I assigned 16 GB (8+8) to VMs.
· Data: Available memory dropped from 10.3 GB to 1.7 GB.
· Conclusion: Overcommitting caused the host to use swap, making it very laggy.
