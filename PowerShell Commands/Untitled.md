

>To see what is available : 
>
	Get-WindowsCapability -Name RSAT* -Online | Select-Object -Property DisplayName, State
>



>To install what is available online : 
>
>	`Add-WindowsCapability –online –Name Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0`






Add-WindowsCapability –online –Name Rsat.Dns.Tools~~~~0.0.1.0 ;  Add-WindowsCapability –online –Name Rsat.FileServices.Tools~~~~0.0.1.0  ;  Add-WindowsCapability –online –Name Rsat.GroupPolicy.Management.Tools~~~~0.0.1.0 ;  Add-WindowsCapability –online –Name Rsat.RemoteAccess.Management.Tools~~~~0.0.1.0 ;  
Add-WindowsCapability –online –Name Rsat.RemoteDesktop.Services.Tools~~~~0.0.1.0 ;  Add-WindowsCapability –online –Name Rsat.ServerManager.Tools~~~~0.0.1.0  ;  Add-WindowsCapability –online –Name Rsat.WSUS.Tools~~~~0.0.1.0  ;  


