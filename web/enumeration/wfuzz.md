# wfuzz

## Directory Traversal Fuzzing
```shell
wfuzz -c -w /usr/share/wfuzz/wordlist/vulns/dirTraversal-nix.txt http://192.168.1.8/?page=FUZZ
```

## Directory Index Fuzzing
```shell
wfuzz -c --hl 14 --follow -z range,1-300 -z range,1-100 https://192.168.1.10:15020/vault/DoorFUZZ/VaultFUZ2Z
```

## Enumeration
```shell
# PHP script enumeration
wfuzz -c --sc=200 -w /usr/share/dirb/wordlists/common.txt http://192.168.1.19/test/FUZZ.php

# Image enumeration
wfuzz -c --sc=200 -w /usr/share/dirb/wordlists/common.txt http://192.168.1.19/test/FUZZ.jpg
```