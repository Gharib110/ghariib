---
title: "Preventing secrets from leaking through Clipboard"
date: 2025-01-19
categories: 
  - "cybersecurity"
  - "cybersecurity-awareness"
  - "security"
  - "vulnerabilities"
---

For decades users have been pressing Ctrl+C or relying on copy buttons. All these tricks and shortcuts to speed up text processing have become natural and intuitive to us. We do not pay attention to what is happening to copied information besides the fact that we can paste it. It’s safe to assume that most of us consider the clipboard as temporary data sharing. Once you copy something previous data in the clipboard will be overwritten. People rely on this assumption when they copy sensitive information such as passwords.

## Security aspect of added convenience

Pressing Ctrl+C in Windows 10 no longer does only what it was doing in Windows 3.0. Windows can now also preserve copied data in Clipboard History and sync it across devices. This may be very handy when you need to transfer information from one device to another.

The _temporary_ effect of Ctrl+C is no longer temporary. For example, a password can stay unnoticed in local history forever.

The _local_ effect of Ctrl+C is no longer local. For example, recovery codes copied last week on one device can appear in the clipboard of another PC for the same user.

In Windows 10 it is now possible to look up secrets from connected devices by pressing Windows+V on the unlocked system. There will be no audit trails and no authentication challenge. How many of us lock their system every time we go to get a cup of coffee?

## What have we improved?

Starting with Firefox 94 and ESR 91.3, your browser keeps the temporary and local promise of clipboard in certain places where users expect privacy, and will not share that data with either Clipboard History or Cloud Clipboard. This protects users when they copy passwords and usernames from the Passwords page, and will protect everything people copy to the clipboard from a Private Browsing window.

We do this by using appropriate clipboard formats for sensitive data. The corresponding CVE can be found at https://www.cve.org/CVERecord?id=CVE-2021-38505.

Technology makes our lives better every day, but it also introduces new risks. Risks that most people are not aware of. Firefox strives to keep everyone safe and this is one step in that direction.

The post Preventing secrets from leaking through Clipboard appeared first on Mozilla Security Blog.

Go to Source
