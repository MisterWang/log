---
title: 执行迁移命令报错
categories: 
- php
- yii
tags:
- php
layout: post
---

## 执行迁移命令报错

Exception 'yii\base\InvalidConfigException' with message 'You should configure "authManager" component to use database before executing this migration.'

配置 console/web.php

```php
'components' => [
    "authManager" => [
        "class" => 'yii\rbac\DbManager',
        "defaultRoles" => ["guest"],
    ],
]
```
