# phpredis

## 错误
Fatal error: Uncaught exception 'RedisException' with message 'read error on connection'

估计是超时了，发现受到php.ini中default_socket_timeout的影响，在程序前加上
```php
ini_set('default_socket_timeout', -1);
```
