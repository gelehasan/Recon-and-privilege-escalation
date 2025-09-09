# Overview
A weak service file permission which can be modified by anyone can easily be replaced with a malicious content.
This will give you a list of services, look for the unknown or non standard services, then proceed with checking permision
<pre>Get-CimInstance -ClassName Win32_Service -Property Name, DisplayName, PathName, StartMode |
    Where-Object { $_.PathName -notlike 'C:\Windows*' } |
    Select-Object Name, DisplayName, StartMode, PathName
</pre>


# Checking folder permission for the target service that has been found

<pre> Get-Acl <File_path> | Format-List *</pre>
