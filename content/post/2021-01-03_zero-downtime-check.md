+++
title = "ทำ zero downtime บน k8s"
description = "Zero downtime monitor check after restart k8s"
tags = [
    "k8s",
    "linux",
    "curl"
]
date = 2021-01-03T17:30:40Z
author = "Kananek Thongkam"
+++

เปิด `terminal` รันคำสั่ง healthcheck เป็น loop ทิ้งไว้ จะได้เห็นผลลัพธ์ชัดเจน

```bash
HOST=dev.slick-checkout.ppe-api
URL=http://20.195.37.247/v1/_health
while true; do echo $(curl -X GET -Is -H 'Host: $HOST' $URL | head -n 1); sleep 1; done
```

Comming Soon...

