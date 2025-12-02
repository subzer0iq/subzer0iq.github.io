---
layout: post
title: "Memory notes"
categories: misc
---
##### Python
```
unicode_line.translate(str.maketrans('', '', '!@#$'))
inputstring.split('"')[1::2]
```
##### Linux
```
cat /etc/systemd/system/sshd.service.d/01-sshd-dependency.conf
[Service]
ExecStartPre=/bin/sleep 2
```
```
git reset # This will unstage all files you might have staged with git add
git checkout . # This will revert all local uncommitted changes (should be executed in repo root)
git checkout [some_dir|file.txt] # You can also revert uncommitted changes only to particular file or directory
```
##### Windows
###### pnputil
```
pnputil.exe /enum-drivers
pnputil.exe /export-driver * D:\drivers
pnputil.exe /export-driver oem20.inf d:\drivers\realtek

pnputil.exe -e
pnputil.exe –f –d oem<number>.inf

pnputil.exe /add-driver C:\drivers\*.inf /subdirs /install
```
###### sc
```
sc EnumDepend <service>
sc query state= all type= all
sc query type= driver
sc config cdrom start= disabled
sc config NcbService start= demand
```
###### CertUtil
```
certutil -hashfile <file>
CertUtil -hashfile C:\TEMP\File.img MD5 #MD2 MD4 MD5 SHA1 SHA256 SHA384 SHA512
$(CertUtil -hashfile C:\TEMP\File.img MD5)[1] -replace " ",""
```
###### wevtutil
```
for /f %a in ('wevtutil el') do wevtutil cl "%a"
wevtutil cl "Windows PowerShell"
```
###### WDAC
```
C:\Windows\System32\CodeIntegrity\CiPolicies\Active\{PolicyId GUID}.cip
C:\Windows\System32\CodeIntegrity\SiPolicy.p7b
```
---
```
Boot        0x0
System      0x1
Automatic   0x2
Manual      0x3
Disabled    0x4
```
---
Visibility from 2 to 1 on each subkey in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Component Based Servicing\Packages`
```
DISM /online /Get-Packages
DISM /online /Add-Package /PackageName:Microsoft-Windows-PhotoPremiumPackage~31bf3856ad364e35~amd64~~6.1.7601.17514
DISM /online /Remove-Package /PackageName:Microsoft-Windows-PhotoPremiumPackage~31bf3856ad364e35~amd64~~6.1.7601.17514
```
---
```
reg load HKLM\TempHiv %WinDRV%\Windows\system32\config\system
reg add HKLM\TempHiv\ControlSet001\Control\Diagnostics\Performance /v DisableDiagnosticTracing /t REG_DWORD /d 0/f
reg unload HKLM\TempHiv
```
---
```
%LocalAppData%\Microsoft\Windows\WinX
C:\Users\Alexander\AppData\Local\Microsoft\Windows\WinX\Group2
```
---
```
explorer.exe shell:MyComputerFolder
Get-Service <service> -DependentServices
Start-Process -FilePath 'RunDll32.exe' -ArgumentList 'InetCpl.cpl, ResetIEtoDefaults' -Wait
ncpa.cpl
more /P file.txt > file2.txt
%WINDIR%\Setup\Scripts\SetupComplete.cmd
findstr /c:"something" %windir%\Logs\CBS\CBS.log > %userprofile%\Desktop\file.txt
tasklist /m /fi "imagename eq netbeans.exe"
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61

taskkill /f /im explorer.exe
start explorer.exe
```
```
echo $PROFILE
Get-Module -ListAvailable
notepad $PROFILE
$PSModuleAutoLoadingPreference = 'None'
Import-Module Microsoft.PowerShell.Utility
Import-Module Microsoft.PowerShell.Management
```
---
`https://www.google.com/search?udm=14&q=%s`
```
C:\Users\Username\AppData\Local\Chromium\Application\chrome.exe --proxy-server="socks5://192.168.0.100:3128" --proxy-bypass-list="localhost;192.168.0.0/24"
"C:\Program Files\Mozilla Firefox\firefox.exe" -no-deelevate -app "C:\Program Files\Mozilla Firefox\browser\application.ini"
```
```
FTYPE SMCFile="C:\some_path\SMCProgram.exe" -some_option %1 %*
ASSOC .smc=SMCFile
```
```
rename or delete a file association in HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\FileExts\<extension>\UserChoice
>assoc .pl
.pl=Perl
>ftype perl
perl="C:\Perl64\bin\perl.exe" "%1" %*
```
```
assoc .pdf
assoc|more
ftype AcroExch.Document.DC

ASSOC .csv=txtfile

assoc .tx1=tx1file
ftype tx1file="%programfiles(x86)%\"Notepad++\notepad++.exe" "%1"

Dism.exe /Online /Export-DefaultAppAssociations:C:\PS\DefaultAssoc.xml
Dism.exe /Online /Import-DefaultAppAssociations:C:\PS\DefaultAssoc.xml

Dism /Mount-Image /ImageFile:C:\mnt\images\install.wim /MountDir:C:\mnt\offline
Dism.exe /Image:C:\mnt\offline /Import-DefaultAppAssociations:\\Server1\Share\DefaultAssoc.xml
Dism.exe /Image:C:\mnt\offline /Get-DefaultAppAssociations

Dism.exe /Online /Remove-DefaultAppAssociations
```
```
KEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager
BootExecute
Exclude disk C from check
autocheck autochk /k:C *
Exclude all disks
autochk /k:* *
```
```
wmic useraccount get domain,name,sid
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\SystemProtectedUserData\<SID>\AnyoneRead\LockScreen
HideLogonBackgroundImage 1
```
---
###### What to disable
Display adapters:
- Intel graphics

Network adapters:
- All WAN miniports
- Microsoft ISATAP Adapter

Storage controllers:
- Microsoft iSCSI Initiator

System devices:
- Composite Bus Enumerator
- Intel Management Engine / AMD PSP
- Intel SPI (flash) Controller
- Microsoft GS Wavetable Synth
- Microsoft Virtual Drive Enumerator (if not using virtual drives)
- NDIS Virtual Network Adapter Enumerator
- Remote Desktop Device Redirector Bus
- SMBus
- System speaker
- Terminal Server Mouse/Keyboard drivers
- UMBus

---
<https://www.catalog.update.microsoft.com/home.aspx>

<https://uupdump.net/>

<https://www.geeksforgeeks.org/python/regular-expression-python-examples/>

<https://www.askpython.com/python/string/adding-commas-into-number-string>

<https://woshub.com/managing-default-file-associations-in-windows-10/>

<https://bin.entware.net/armv7sf-k2.6/Packages.html>
