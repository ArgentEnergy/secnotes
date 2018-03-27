# dirb

## Enumeration
```shell
# Find hidden web objects using dirb common.txt wordlist
dirb http://192.168.1.19/test -R

# Find hidden web objects using dirb big.txt wordlist
dirb http://192.168.1.19/test /usr/share/dirb/wordlists/big.txt -R

# Find web objects ignoring 403 status codes
dirb http://192.168.1.19/cgi-bin/ -N 403
```