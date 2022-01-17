---
layout: post
title: Azure AD authentication with AVD VM's
published: true
---

![AVD](https://github.com/nomoretorgo/nomoretorgo.github.io/raw/master/_posts/azure.microsoft.com.png)

## 3 Key items after setting up your AVD environment to check


- Add one of the following IAM Roles in each VM your deploying.
-- Virtual desktop admin
-- Virtual desktop user


- Authetication with Azure AD
-- You must add targetisaadjoined:i:1 in order to successfully authenticate with Azure AD accounts.
-- set this in hostpool->rdp properties -> advanced


- MFA will block login attempts.
--you need to get conditional access going and set the app as excluded.
