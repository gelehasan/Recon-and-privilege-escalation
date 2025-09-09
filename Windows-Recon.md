# Show file contents
<pre>Get-Content <file_path> </pre>

# User/ groups / system info
<pre>whoami
whoami /priv
whoami /groups

systeminfo 
# Viewing users
net user

# Displaying users belong to adminstrator
Net localgroup administrator

</pre>

# Product names
<pre>
Get-CimInstance -ClassName Win32_Product | Select-Object Name, Version Vendor
</pre>

# Discovering other systems connected to our LAN or interacted with our system
<pre>
  arp -a 
</pre>

# Network related 
<pre>
netstat -ano                # All connections with PID  
netstat -anob               # All PID 
</pre>

# Get process ids
<pre>
  Get-Process <id>
  Get-CimInstance Win32_Process
</pre>
