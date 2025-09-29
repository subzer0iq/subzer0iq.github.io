---
layout: post
title: "Memory notes"
categories: misc
---

###### WDAC
```C:\Windows\System32\CodeIntegrity\CiPolicies\Active\{PolicyId GUID}.cip
C:\Windows\System32\CodeIntegrity\SiPolicy.p7b
```
---
Visibility from 2 to 1 on each subkey in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Component Based Servicing\Packages`
```DISM /online /Get-Packages
DISM /online /Add-Package /PackageName:Microsoft-Windows-PhotoPremiumPackage~31bf3856ad364e35~amd64~~6.1.7601.17514
DISM /online /Remove-Package /PackageName:Microsoft-Windows-PhotoPremiumPackage~31bf3856ad364e35~amd64~~6.1.7601.17514
```
---
```reg load HKLM\TempHiv %WinDRV%\Windows\system32\config\system
reg add HKLM\TempHiv\ControlSet001\Control\Diagnostics\Performance /v DisableDiagnosticTracing /t REG_DWORD /d 0/f
reg unload HKLM\TempHiv
```
---
```%LocalAppData%\Microsoft\Windows\WinX
C:\Users\Alexander\AppData\Local\Microsoft\Windows\WinX\Group2
%windir%\explorer.exe shell:::{2559a1f8-21d7-11d4-bdaf-00c04f60b9f0}
```
---
```sc EnumDepend <service>
Get-Service <service> -DependentServices
Start-Process -FilePath 'RunDll32.exe' -ArgumentList 'InetCpl.cpl, ResetIEtoDefaults' -Wait
sc query state=all type=all
sc query type= driver
sc config cdrom start=disabled
ncpa.cpl
explorer.exe shell:MyComputerFolder
```
---
`https://www.google.com/search?udm=14&q=%s`
```C:\Users\Username\AppData\Local\Chromium\Application\chrome.exe --proxy-server="socks5://192.168.0.100:3128" --proxy-bypass-list="localhost;192.168.0.0/24"
"C:\Program Files\Mozilla Firefox\firefox.exe" -no-deelevate -app "C:\Program Files\Mozilla Firefox\browser\application.ini"
```
---
https://www.catalog.update.microsoft.com/home.aspx
https://uupdump.net/
