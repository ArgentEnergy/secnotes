# hping3

## Ping Sweep
```shell
# Send 3 ICMP packets
hping3 --icmp -c 3 172.17.19.62

# Send ICMP packets every 10 seconds
hping3 --icmp -i 10 172.17.19.62
```

## Scanning Techniques
```shell
# TCP SYN scan port
hping3 -S -p 80 -c 1 -V 172.17.19.62

# TCP SYN scan port range
hping3 -S --scan 1-3000 172.17.19.62

# UDP scan SNMP port
hping3 --udp --data 16 -p 161 172.17.19.62
```

## Flooding
```shell
# TCP flood a host
hping3 --flood 172.17.19.62

# ICMP flood a host
hping3 --icmp --flood 172.17.19.62

# Perform an amplification attack
hping3 --icmp --flood 172.17.255.255
```

## Firewall/IDS Evasion and Spoofing
```shell
# Send 64 byte ICMP fragmented packets
hping3 --icmp -f --mtu 64 --data 500 172.17.19.62

# Send ICMP packets using random IPs
hping3 --icmp -c 3 --rand-source 172.17.19.62

# Send TCP SYN packets using a spoofed IP
hping3 -a 172.17.19.61 -S -c 3 172.17.19.62
```

## Other
```shell
# Send "Communication administratively filtered" packets (ICMP disabled on firewall) 
hping3 --icmptype 3 --icmpcode 13 172.17.19.62
```