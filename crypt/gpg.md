# GPG

## Symmetric Ciphers
```shell
# Encrypt directory using a passphrase (default cipher is CAST-128)
gpg-zip -c test/ > test.tar.gz.gpg

# Decrypt file containing directory
gpg-zip --decrypt test.tar.gz.gpg

# Encrypt file using a passphrase (default cipher is AES-128)
gpg -c test.txt

# Decrypt file
gpg test.txt.gpg
```

## Asymmetric Keys
```shell
# Create a public/private key pair
gpg --gen-key

# Export David's public key (David's system)
gpg --export -a "David" > david.key

# Import David's public key (Colin's system)
gpg --import david.key

# Encrypt the text file using David's public key (Colin's system)
gpg -e -r "David" test.txt

# Decrypt the text file using David's private key (David's system)
gpg -d test.txt.gpg

# View keys on system
gpg --list-keys
```