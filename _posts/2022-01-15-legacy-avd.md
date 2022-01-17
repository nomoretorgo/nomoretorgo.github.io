---
published: true
---
# What now for our existing Legacy AVD environments?
![AVD Classic](https://github.com/nomoretorgo/nomoretorgo.github.io/blob/master/_posts/avd-classic.png?raw=true)


## What to do with our Azure classic (WVD) environments?

Azure classic aka WVD has been discontinued by Microsoft replaced by AVD.  Just speaking with Microsoft support I got some interesting news that AVD is also still in beta.  So to be clear, Microsoft discontinued WVD and replaced it with a product which is still in beta...   

Couple differences between WVD and AVD I’ve run across that are note worthy: 

-WVD boxes are either joined to an on premise AD server or Cloud only Active Directory with no domain controller..

-WVD infrastructure requires Azure Active Directory Domain Services.  While there are surly many companies that require this, there are a ton that don’t and AVD doesn’t require AADDS be installed.  That’s equals $$$ saved.

-There is a big issue where existing Hostpool VM’s have the option of joining Azure AD completely stipped from the settings menu. 

## How do we migrate these legacy systems to the new and improved AVD

I have talking to Microsoft regarding this issue this week.  It turns out there is no automated way to achieve this goal.  The manual method found here: https://docs.microsoft.com/en-us/azure/virtual-desktop/manual-migration#how-to-migrate-manually which essentially involves creating a new AVD environment then migrating the VM through a series of steps.  Summed up, the manual nature and long series of steps for migration result in downtime for your client.  

It’s also still not clear on how to add these existing VM’s to Azure Active Directory.  VM’s launched in Azure Hostpools have been missing the join Azure AD option with absolutely no explanation of why.  Support hasen’t provided a good explanation for this to me, but one individual suggested the reinstallation of the Azure Virtual Desktop Agent Bootloader in a AVD hostpool will join the VM to Azure AD.  I’ve yet to get this to function however.

Thus we come to the concussion I’m sure you guessed at the beginning.  Migration of WVD to AVD is simply not worth the effort.   Instead manually migrate your data to a new AVD environment and hope Microsoft doesn’t depreciate this environment in the same way next year.
