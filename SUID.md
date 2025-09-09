# Overview SUID – Shared Object Injection
When a SUID binary loads a shared object (e.g. .so file) from a user-controlled path, you can inject malicious code and get root execution.

<pre>find / -perm -4000 -type f 2>/dev/null
</pre>

Look for SUID binaries not owned by you. Then check if they dynamically load shared objects:
<pre>ldd /path/to/suid-binary
</pre>

#SUID – Symlinks
A SUID binary or root-owned script writes to a file/folder you control (e.g. /tmp/tmpfile), and you can symlink that path to something sensitive (like /etc/shadow or a cron script), tricking the binary into overwriting it.
<pre>find / -perm -4000 -type f 2>/dev/null

strace /path/to/suid-binary 2>&1 | grep -i open
Check for:
*Writes to predictable locations like /tmp/filename
*Weak permission files created as root

# Explotation
  Wait for binary to write to /tmp/output.log
  *ln -s /etc/shadow /tmp/output.log
</pre>
