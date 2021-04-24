+++
title = "วิธีทำ Key-based Authentication สำหรับ OpenSSH บน Windows"
description = "Key-based Authentication for OpenSSH"
tags = [
    "mongo",
    "user"
]
date = 2020-12-28T06:43:18Z
author = "Kananek Thongkam"
+++

**Admin Users**

If the user account on the server you are connecting to is in the local Administrators group, the public key must be placed in the `C:\ProgramData\ssh\administrators_authorized_keys` instead of the user's .ssh folder.  Additionally, only the Administrators group and SYSTEM account can have access to that file, for security purposes.  After copying your key into the file and saving it, you can use this script to set the correct permissions on it.  Here are the complete steps:

1. Open the public key file in Notepad.  If using default path, it is `C:\Users\myuser\.ssh\id_rsa.pub`
2. Copy the contents of the file to clipboard.  Ensure you get the entire file.
3. Connect to the server with Remote Desktop.
4. Open Notepad as administrator
5. In Notepad, paste in the key you copied earlier
6. Save the file as `C:\ProgramData\ssh\administrators_authorized_keys` with no extension.  You may need to make file extensions visible to ensure you can remove the .txt extension.
7. Use the below PowerShell script to set the correct permissions on the file

```powershell
$acl = Get-Acl C:\ProgramData\ssh\administrators_authorized_keys
$acl.SetAccessRuleProtection($true, $false)
$administratorsRule = New-Object system.security.accesscontrol.filesystemaccessrule("Administrators","FullControl","Allow")
$systemRule = New-Object system.security.accesscontrol.filesystemaccessrule("SYSTEM","FullControl","Allow")
$acl.SetAccessRule($administratorsRule)
$acl.SetAccessRule($systemRule)
$acl | Set-Acl
```

If you don't do this, and instead only place the file in the .ssh folder for the user, you'll either get prompted for your password (instead of using the key file), or your connection will fail with "Too many authentication attempts".

REF: https://www.concurrency.com/blog/may-2019/key-based-authentication-for-openssh-on-windows