---
published: false
---
# Outbound Forwarding policy fun with Exchange 365

## Summary:  In the name of security, Microsoft has set an outbound spam filter policy which blocks any attempt from it’s users to create a forward on their mailbox.  This is typically a great thing, but there are instances when a user or shared mailbox needs a forward.  So how do we set this forward for the specific user or group?  This is usually an easy step of creating an outbound spam filter policy.   HOWEVER, I was attempting this today when the default policy was still taking priority blocking my forward attempts.  Time to jump into powershell and see whats going on.  I ended up force deleting the default policy which is auto created, then creating two new policies to one, allow my shared group forward.  And two, block other forwarding attempts.

# Force remove the default policy
Remove-HostedOutboundSpamFilterPolicy -Identity Default -Force


# create a new policy 
New-HostedOutboundSpamFilterPolicy -Name "Forwarding Rule for helpdesk" -AutoForwardingMode On

#  create a rule to apply user → policy
New-HostedOutboundSpamFilterRule -Name "Forward Members" -HostedOutboundSpamFilterPolicy "Forwarding Rule for helpdesk" -From helpdesk


#  Create a new forward blocking rule for everyone else 
 New-HostedOutboundSpamFilterPolicy -Name "Anti-spam outbound policy" -AutoForwardingMode automatic


# Check our results
Get-HostedOutboundSpamFilterPolicy

![hostedoutbound.png]({{site.baseurl}}/hostedoutbound.png)
