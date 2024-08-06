In order to on board an endpoint device, we need to obtain the hardware ID of the device. 
We can use this Powershell Script below:

```
New-Item -Type Directory -Path "C:\HWID"
Set-Location -Path "C:\HWID"
$env:Path += ";C:\Program Files\WindowsPowershell\Scripts"
Set-ExecutionPolicy -Scope Processes -ExecutionPolicy RemoteSigned
Install-Script -Name Get-WindowsAutoPilotInfo
Get-WindowsAutopilotInfo -OutputFile AutoPilotHWID.csv
```