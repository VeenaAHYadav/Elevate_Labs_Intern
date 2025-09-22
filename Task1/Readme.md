# Nmap Local Network Scan 

**Overview:**
This README describes a safe, repeatable workflow to scan your local network for live hosts and open TCP ports using Nmap, optionally analyze the traffic in Wireshark, and assess basic security risks.

### Step1: Install nmap

* Visit [https://nmap.org](https://nmap.org) and download the installer for your OS.
* Verify installation by running:

```bash
nmap --version
```

### Step2: Find your local IP range

```bash
ip a
# or
ifconfig
```
Identify your IPv4 address and subnet 

### Step3: Run the TCP SYN scan (basic)

This sends SYN packets to discover open TCP ports:

```bash
nmap -sS 192.168.1.0/24
```

### Step4: Results

Finding:Host is alive -->Target reachable(IP detected)
*Open ports:135(tcp),445(tcp),7070(tcp)

### 5) Analyzed packet capture with Wireshark

* Start Wireshark and begin capturing on the network interface used for the scan.

### 6) Common services found on these ports

* `135` — TCP
* `445` — TCP
* `7070` — TCP

### Step7: Identify potential security risks

* Exposed management interfaces (web admin on port 80/443)
* Unencrypted protocols (Telnet, FTP)
* Services with known CVEs (use `--script vuln` to let Nmap run vulnerability scripts)

### Step8: Save scan results

```bash
nmap -sS ip address -oN local-scan.txt
```




