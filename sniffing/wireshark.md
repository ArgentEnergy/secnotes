# Wireshark

## DHCP Display Filters

```text
# Displays DHCPv6 traffic
dhcpv6

# Displays DHCP traffic
udp.port eq 67
```

## NetBIOS Display Filters

```text
# Displays NetBIOS Name Service
nbns
```

## HTTP Display Filters

```text
# Displays HTTP traffic
http

# Displays HTTP requests
http.request

# Displays HTTP POST requests
http.request.method==POST

# Displays HTTP traffic that contains txtPassword
http contains txtPassword

# Displays HTTP traffic that has cookies
http.cookie
```

## ICMP Display Filters

```text
# Displays ICMP requests with an assigned source IP
icmp and ip.src==172.17.19.67

# Displays ICMP replies with an assigned destination IP
icmp and ip.dst==172.17.19.67
```

## TCP Display Filters

```text
# Displays TCP resets
tcp.flags.reset==1

# Displays TCP retransmissions
tcp.analysis.retransmission

# Displays traffic for a host
ip.addr==172.17.19.67 and tcp
```

## Wireless Display Filters

```text
# Displays Wireless handshake traffic
eapol
```

## Other

```text
# Mask out ARP and DHCPv6 traffic (display filter)
!(arp or dhcpv6)

# View ARP request storms
Edit > Preferences… > Protocols > ARP/RARP > Detect ARP request storms
Analyze > Expert Info

# Export Audio file from packet(s)
- Click on the packet that has the audio file response data
- Click File > Export Objects > HTTP > Save
```