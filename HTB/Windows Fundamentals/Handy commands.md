### tree utility like bash  
The tree command can provide us with a large amount of information. The following command can be used to walk through all the files in the C drive, one screen at a time. This command can be modified to be run against any directory.

```
``` cmd-session
tree c:\ /f | more
``````

It is also possible to query and manage services via the command line using `sc.exe` using [PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7) cmdlets such as `Get-Service`.
`Get-Service` 


### Examine service permissions using PowerShell

```powershell-session
Get-ACL -Path HKLM:\System\CurrentControlSet\Services\wuauserv | Format-List
```


- lists information about the operating system.
```cmd-session
C:\htb> wmic os list brief

BuildNumber  Organization  RegisteredUser  SerialNumber             SystemDirectory      Version
19041                      Owner           00123-00123-00123-AAOEM  C:\Windows\system32  10.0.19041
```


Here is an example of the `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run` showing applications running under the current user while logged in to a system.

```powershell-session
reg query HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
```


We can use the PowerShell cmdlet `Get-MpComputerStatus` to check which protection settings are enabled.

```powershell-session
PS C:\htb> Get-MpComputerStatus | findstr "True"
```