+++
title = "Create user and root account in mongodb"
description = "Create user and root mongodb init server."
tags = [
    "mongo",
    "user"
]
date = 2020-12-08T02:13:50Z
author = "Kananek T."
+++

After create mongodb service or run in docker

```shell
use admin
db.createUser({ user: "root", pwd: "123123", roles: ["root"] })

use yourDb
db.createUser({ user: "user", pwd: "123123", roles: ["readWrite", "dbOwner"] })
```

add command `mongod --auth` authication mongodb

```shell
use admin
db.auth('root','123123')
# output: 1
```


[go]: <https://golang.org/>
[gohtmltemplate]: <https://golang.org/pkg/html/template/>