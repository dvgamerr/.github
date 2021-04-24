+++
title = "Unlock Internet in RIS"
description = "Unlock Internet in RIS at central group cmd"
tags = [
    "ris",
    "window",
    "curl"
]
date = 2018-06-21T03:01:40Z
author = "Mr.Kananek Thongkam"
+++

ต้องการโปรแกรม `curl.exe` บน windows ถ้าหากไม่มีโหลดได้จาก chocolatey.

```bash
@echo off
SET USER=your_username
SET PASS=your_password
curl -ik https://proxyauthentication.central.co.th:6082/login.api ^
  -H "X-Requested-With: XMLHttpRequest" ^
  -H "Content-Type: application/json" ^
  -H "Origin: https://proxyauthentication.central.co.th:6082" ^
  -H "Referer: https://proxyauthentication.central.co.th:6082/php/uid.php?vsys=1&rule=10" ^
  -d "{\"userName\":\"%USER%\",\"password\":\"%PASS%\"}"
PAUSE
```

สร้างไฟล์จาก script ด้านบน `init.bat` และรันภายใต้ไวไฟหรือแลนบริษัทที่ชื่อ `@wifi-office` เพื่อเข้าใช้งาน internet โดยไม่ต้องเข้าหน้าเว็บเพื่อ login