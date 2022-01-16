---
layout: post
title: Azure AD authentication with AVD VM's
published: false
---

![AVDImg.png]({{site.baseurl}}/_posts/AVDImg.png)
## 3 Key items after setting up your AVD environment to check


- Add one of the following IAM Roles in each VM your deploying.
-- Virtual desktop admin
-- Virtual desktop user

[AVD logo]: https://github.com/nomoretorgo/nomoretorgo.github.io/blob/master/_posts/AVDImg.png
[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"
![AVDImg.png]({{site.baseurl}}/_posts/AVDImg.png)

- Authetication with Azure AD
-- This is a particularly irritating missing configuration on microsofts part.  You must add targetisaadjoined:i:1 in order to successfully authenticate with Azure AD accounts.
-- set this in hostpool->rdp properties -> advanced


- MFA will block login attempts.
--you need to get conditional access going and set the app as excluded.


![AVDImg.png]({{site.baseurl}}/_posts/AVDImg.png)
