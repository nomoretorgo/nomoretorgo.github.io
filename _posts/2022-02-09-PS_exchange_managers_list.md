---
published: true
---

#  Mining user assigned mangers via Powershell 
## Pulling workable data

Summary:  365 exchange allows admins to specify an assigned manager for each users mailbox in exchange.  These instructions pull all users searching for the managers.  Then you can Get the mailboxes into an array for creating new groups or whatever you wish.


### Get list of mangers from exchange and assign them to an array
$real_list=Get-User -ResultSize unlimited | Select-Object Manager | ?{$_.Manager -ne $null} | Sort-Object -Property manager -Unique | select -ExpandProperty manager


### Create an ArrayList
$real_obj_list = [System.Collections.ArrayList]::new()

### Populate that arraylist with objects
for ($i=0;$i -lt $real_list.Count; $i++) {
  $temp=get-mailbox -Identity $real_list[$i];
  $real_obj_list.add($temp);
}

### Create an office 365 group with our array of objects
New-UnifiedGroup -Name peopleleaders -DisplayName "People Leaders" -Members $real_obj_list.primarysmtpaddress
