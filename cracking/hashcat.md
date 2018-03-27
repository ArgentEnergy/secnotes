# hashcat

## Dictionary Attacks
```shell
# Crack salted hashes and set output format as plain 
hashcat -m 20 -a 0 hashes.txt /usr/share/wordlists/10_million_password_list_top_100000.txt --force --outfile-format=2 --show

# Crack Wordpress hashes
hashcat -m 400 -a 0 hashes.txt /usr/share/wordlists/10k_most_common.txt --force

# Crack TrueCrypt file
hashcat -a 0 -m 6211 container.tc /usr/share/wordlists/rockyou.txt --force
```
