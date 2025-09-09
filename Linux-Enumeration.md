
<pre>
Hostname

# Find kernel version
  cat /etc/issue
# Find linux version
  cat /proc/version
# Check home bash history for passwords.
# Check openvpn etc
# Display running process
  ps
  ps aux
  ps -A 

# Check permision
  ls -la

# Displaying list of program user can run as sudo 
  sudo -l

# Displaying user privilege level and group membership
  id

# Discovering other users on the system
  cat /etc/passwd

# Displaying listening ports and established connection
  netstat -a

# Discovering sensitive files
#Files that are readable writeable and executable
 find / -type f -perm 0777

# Finding executables
  find / -perm a=x

# Enumerating user owned files
  find /home -user frank

# Configs that often hold data
find / -type d -name config

# Find any directories the user can write to
find / -writable -type d 2>/dev/null

#find / -perm -222 -type d 2>/dev/null

# Find programs with suid bit set
find / -perm -04000 -type f ls 2>/dev/null


</pre>
