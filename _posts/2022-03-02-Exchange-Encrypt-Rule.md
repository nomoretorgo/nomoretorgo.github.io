---
published: true
---
# Allow Encrypted messages, Block those with Sensitive

![how-to-encrypt-email_thumb800.jpg]({{site.baseurl}}/how-to-encrypt-email_thumb800.jpg)


## Issues with Exchange control statements

Summary:  Exchange rules are setup to allow or block message flow based on rules which allow control logic.  However, this control logic does not function correctly and a work around is required.

### Goal:  
-  Create a rule to block all emails that contain sensitive information, but allow them if encrypted.

### Preconfigured assumptions:  
-  Sensitivity labels need to be created and published to facilitate encryption 

### Core issue:  
-  While you can add an exception to your Rule for messages that are “encrypted” this functionality actually DOES NOT WORK.  This is also incredibly frustrating because rules can take time to propagate and test.


### Work around
-  First create a rule for all encrypted messages that does NOTHING.  This rule must have a higher priority. This will allow encrypted messages to be sent.
-  Second create the rule to block all messages that contain sensitive information with less priority than the first rule.
