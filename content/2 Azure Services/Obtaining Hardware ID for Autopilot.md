In order to onboard an endpoint device, we need to obtain the hardware ID of the device. 
To begin, run PowerShell as Administrator:

![[Pasted image 20240806074914.png]]

We can use this PowerShell Script to create a folder named 'HWID', install, and run the 'Get-WindowsAutoPilotInfo' script:

```
New-Item -Type Directory -Path "C:\HWID"
Set-Location -Path "C:\HWID"
$env:Path += ";C:\Program Files\WindowsPowershell\Scripts"
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
Install-Script -Name Get-WindowsAutoPilotInfo
Get-WindowsAutopilotInfo -OutputFile AutoPilotHWID.csv
```

Paste this script into the PowerShell command line and run the script:

![[Pasted image 20240806075123.png]]

The execution policy and the NuGet provider will popup. Agree to all:

![[Pasted image 20240806075210.png]]

Once the script has run, navigate to where the script created a folder and saved the .csv file:

![[Pasted image 20240806075334.png]]

As you can see here, the file has been created containing the Device Serial Number, Windows Product ID, and Hardware Hash:

![[Pasted image 20240806080304.png]]