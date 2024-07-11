Since the Windows 11 update, viewing the [[Bit Locker]] keys in [[Active Directory Users and Computers]] now requires the use of a PowerShell script to install. 

To begin, open up PowerShell with administrator privileges:

![[Pasted image 20240710120035.png]]

Once in PowerShell, run this command:

``` 
Add-WindowsCapability -Online -Name Rsat.Bitlocker.Recovery.Tools~~~~0.0.1.0
```


![[Pasted image 20240710120241.png]]

Wait for the script to run, it will take a while:

![[Pasted image 20240710120312.png]]

Once the script is complete, restart your computer and run Active Directory Users and Computers:

![[Pasted image 20240710121153.png]]

Now [[Active Directory Users and Computers]] should have the BitLocker recovery keys as one of the tabs:

![[Pasted image 20240710122305.png]]

You can now obtain [[Bit Locker]] Keys in [[Active Directory Computers and Users]]. 

