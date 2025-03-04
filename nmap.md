# Nmap


* `-p-` Scan all ports
* `-sn` Ping. Scan for live hosts. ICMP echo requests that only checks if the host is up. 
* `-sV` Detect version numbers of services, such as Apache.
* `-sS` Stealthy SYN scan. It doesn't complete TCP handshake. Making detection harder.
* `-O` OS detection

* `-T0` Scan very slowly to evade IDS detection
* `-T1` Scan slowly to avoid detection
* `-T2` Scan slower to reduce network congestion
* `-T3` Default speed
* `-T4` Aggressive scan. Faster and may cause detection. 
* `-T5` Scan very fast but may unrealible and could cause network disruptions


Find the open TCP ports
```
nmap -p- --open -T4 -n 10.10.10.10
```

Aggressive and fast scan and detect OS
```
nmap -T4 -O -F 10.10.10.10
```