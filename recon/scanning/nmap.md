# Nmap

## Ping Sweep
```shell
# Ping sweep a subnet
nmap -sn 172.17.19.*

# Ping sweep a range of IPs
nmap -sn 172.17.19.60-70
```

## Scanning Techniques
```shell
# TCP connect scan with service/version info
nmap -sT -sV 172.17.19.62

# TCP stealth scan a port
nmap -sS -p 80 172.17.19.62

# TCP Xmas scan Unix host with service/version info
nmap -sX -sV 172.17.19.62

# TCP FIN scan Unix host
nmap -sF 172.17.19.62

# TCP NULL scan Unix host
nmap -sN 172.17.19.62

# TCP IDLE scan
nmap -Pn -sI 172.17.19.68 172.17.19.62

# TCP ACK scan to discover firewall
nmap -sA 172.17.19.62

# UDP intense scan on SNMP
nmap -sU -T4 -p 161 172.17.19.62

# IP protocol scan showing reason of status
nmap -sO --reason 172.17.19.62
```

## Script Scanning
```shell
# Perform a firewalk on port 80
nmap --traceroute --script=firewalk -p 80 172.17.19.62

# Verify if host is vulnerable to Heartbleed
nmap -p 443 --script ssl-heartbleed 172.17.19.65
```

## Firewall/IDS Evasion and Spoofing
```shell
# Scan sending 64 byte fragmented packets
nmap -sS -f --mtu 64 --data-length 500 172.17.19.62

# IP spoofing
nmap -sS -S 172.17.19.61 -e eth0 -Pn -p 80 172.17.19.62

# Cloak scan with random decoy IPs
nmap -D RND:10 172.17.19.62

# Cloak scan with selected IPs
nmap -D 172.17.19.43,172.17.19.44 172.17.19.62
```

## Output
```shell
# Scan showing packet trace
nmap --packet-trace 172.17.19.62

# Save scan as XML and convert to HTML
nmap 172.17.19.65 -oX scan.xml; xsltproc scan.xml -o scan.html
```