# Shares

## Samba
```shell
# Enumerate Samba information
enum4linux 192.168.1.5 | less

# Mount Samba share
mount -t cifs //192.168.1.5/tmp -o username=guest /media/samba

# Connect to Samba share
smbclient //192.168.1.5/tmp -U guest
```

## NFS
```shell
# Show NFS mounts
showmount -e 192.168.1.18

# Mount NFS share
mount -t nfs 192.168.1.18:/backup /media/nfs
```