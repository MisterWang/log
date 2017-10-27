# 配置

## apache 多php版本
```apache
<VirtualHost *:80>
    ServerName 7test
    ServerAlias
    FcgidInitialEnv PHPRC "/usr/local/php-7.0.23"
    FcgidWrapper "/usr/local/php-7.0.23/bin/php-cgi" .php
    DocumentRoot "path"
    ErrorLog "logs/error.log"
    CustomLog "logs/access.log" common
    
    <Directory path >
        Options FollowSymLinks ExecCGI
        AllowOverride ALL
        require all granted
        #Order deny,allow
        #Deny from all
    </Directory>
</VirtualHost>
```
