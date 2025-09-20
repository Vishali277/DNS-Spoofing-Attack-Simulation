# Task 6: DNS Spoofing Attack Simulation
This project demonstrates a classic Man-in-the-Middle (MITM) attack to perform DNS spoofing in a controlled and isolated virtual lab environment. The objective is to understand the mechanics of DNS-based attacks and the importance of network security controls.
---
## 🧪 Lab Setup Instructions (Deliverable 1)
The entire experiment was conducted within a sandboxed network to ensure safety and prevent any impact on live networks.
1.  **Virtual Environment**: Oracle VM VirtualBox was used.
2.  **Virtual Machines**:
    * **Attacker**: A Kali Linux VM with IP `10.0.0.1`.
    * **Victim**: A second Kali Linux VM with IP `10.0.0.2`.
3.  **Isolated Network**: Both VMs were configured to use VirtualBox's **"Internal Network"** feature (`dns-lab`), completely isolating them from the host machine and the internet.
4.  **IP Configuration**: IP addresses were set manually on both VMs as there is no DHCP server on an internal network.
5.  **Fake Web Server**: A simple Python web server was launched on the Attacker VM on port 80 to serve a fake webpage.
---
## ⚔️ Attack Execution
The attack was performed using the graphical interface of **Ettercap**.
1.  **MITM Attack**: An **ARP poisoning** attack was launched against the Victim (`10.0.0.2`), tricking it into sending all its network traffic to the Attacker machine.
2.  **DNS Spoofing Plugin**: Ettercap's `dns_spoof` plugin was enabled and configured to intercept any DNS query for `example.com`.
3.  **Redirection**: The plugin was set to respond to these queries with a fake DNS "A" record pointing `example.com` to the Attacker's IP (`10.0.0.1`).
4.  **Result**: When the Victim's browser tried to visit `example.com`, it was successfully redirected to the fake webpage hosted by the Attacker.
---
## 🛡️ Defense Strategies
Several measures can be taken to defend against DNS spoofing attacks:
* **DNSSEC (DNS Security Extensions)**: This is the most direct defense. DNSSEC uses digital signatures to provide cryptographic authentication for DNS responses, allowing a client to verify that a response is legitimate and has not been tampered with.
* **Encrypted DNS**: Using protocols like **DNS over HTTPS (DoH)** or **DNS over TLS (DoT)** encrypts DNS queries, making them much harder for a man-in-the-middle to read or modify.
* **Network Intrusion Detection Systems (NIDS)**: Tools like Snort or Suricata can be configured to detect signs of ARP poisoning on a network.
* **Use of VPNs**: A Virtual Private Network (VPN) encrypts all traffic from a user's machine, preventing local attackers from intercepting or modifying it.
---
## 📁 Files in Repository
* `victim-spoofed-browser.png`: Screenshot of the Victim's browser showing the fake webpage.
* `attacker-ettercap-log.png`: Screenshot of the Attacker's Ettercap window showing the successful DNS spoof.
* `README.md`: This report detailing the lab setup, attack process, and defense mechanisms. . Cann you find me or get me the screenshots from somehwere
