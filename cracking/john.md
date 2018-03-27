# John the Ripper

## Cracking
```shell
# Crack Linux hashes
unshadow /etc/passwd /etc/shadow > hashes.txt
john --format=crypt hashes.txt
john --show hashes.txt

# Crack Windows SAM hashes
john --format=NT --rules -w=./Wordlists/Passwords.txt win-hashes.txt

# Crack SSH key passphrase
ssh2john id_rsa > tocrack
john tocrack --wordlist /usr/share/wordlists/10_million_password_list_top_100000.txt
john --show tocrack

# Crack RAR password
rar2john test.rar > hashes.txt
john hashes.txt --wordlist passwords.txt
```

## Generate Wordlists
```shell
# Generate a dictionary using a list of words
john -wordlist=words.txt -rules=All -stdout > passwords.txt

# Generate a dictionary from a website
cewl --depth 3 --write dict.pwd http://192.168.56.223/test
john --wordlist=dict.pwd --rules --stdout > dict2.pwd
```