+++
title = "Unlock Internet in RIS"
description = "Unlock Internet in RIS at central group cmd"
tags = [
    "ris",
    "window",
    "curl"
]
date = 2018-06-21T03:01:40Z
author = "Kananek T."
+++

Require software `curl` for windows or install from chocolatey.

```bash
@echo off
TITLE Central.co.th initialize.
SET USER=your_username
SET PASS=your_password
curl -ik https://proxyauthentication.central.co.th:6082/login.api ^
  -H "X-Requested-With: XMLHttpRequest" ^
  -H "Content-Type: application/json" ^
  -H "Origin: https://proxyauthentication.central.co.th:6082" ^
  -H "Sec-Fetch-Site: same-origin" ^
  -H "Sec-Fetch-Mode: cors" ^
  -H "Sec-Fetch-Dest: empty" ^
  -H "Referer: https://proxyauthentication.central.co.th:6082/php/uid.php?vsys=1&rule=10" ^
  -d "{\"userName\":\"%USER%\",\"password\":\"%PASS%\"}"
PAUSE
```

create file `init.bat` and run after connect `@wifi-office` to access internet without join domain.
