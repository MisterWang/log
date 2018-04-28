---
title: PHPUnit中打印变量
categories: 
- php
- PHPUnit
tags:
- php
- PHPUnit
layout: post
---

```php
fwrite(STDOUT,print_r($var,true));        
```

```shell
phpunit --debug
```

## codecept
```shell
codecept -d 
```

```php
\Codeception\Util\Debug:debug($var);
```
