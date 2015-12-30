# PowerShell Async IPScanner

Powerful Asynchronous IP-Scanner which returns a custom PowerShell object with basic informations about the scanned IP-Range include IP-Address, Hostname (with FQDN) and Status.

## Description

I built this powerful asynchronous IP-Scanner, because every script i found on the Internet was very slow. Most of them do there job, but ping every IP/Host in sequence and/or no one could ping more than /24. This is Ok if you have a few host, but if you want to scan a large IP-Range, you need a lot of coffee :)

This Script can scan every IP-Range you want. To do this, just enter a Start IP-Address and an End IP-Address. You don't need a specific subnetmask (for example 172.16.1.47 to 172.16.2.5 would work).

You can modify the threads at the same time, the wait time if all threads are busy and the tries for each IP in the parameter (use Get-Help for more details).
  
If all IPs are finished scanning, the script returns a custom PowerShell object which include IP-Address, Hostname (with FQDN) and the Status (Up or Down). You can easily process this PSObject in a foreach-loop like every other object in PowerShell.
    
If you found a bug or have some ideas to improve this script... Let me know. You find my Github profile in the links below.

## Syntax

```powershell
.\ScanNetworkAsync.ps1 [-StartIPAddress] <IPAddress> [-EndIPAddress] <IPAddress> [[-Threads] <Int32>] [[-Tries] <Int32>] [[-IncludeInactive]] [<CommonParameters>]
```

## Example

Simple IP-Range Scan
```powershell
.\ScanNetworkAsync.ps1 -StartIPAddress 192.168.1.1 -EndIPAddress 192.168.1.200
```

Include inactive devices
```powershell 
.\ScanNetworkAsync.ps1 -StartIPAddress 172.16.0.1 -EndIPAddress 172.16.1.254 -Threads 50 -Tries 1 -IncludeInactive
```

## Output

 ```powershell
IPv4Address     Hostname                       Status
-----------     --------                       ------
172.16.0.1      FRITZ.BOX                      Up
172.16.0.21     ANDROID-01.FRITZ.BOX           Up
172.16.0.22     ANDROID-02.FRITZ.BOX           Up
172.16.0.23     VM-2012R2-01.FRITZ.BOX         Up
172.16.0.28     VPC-TEST-01.FRITZ.BOX          Up

 ```
