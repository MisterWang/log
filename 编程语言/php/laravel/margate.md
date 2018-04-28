---
title: laravel SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long; max key length is 1000 bytes
categories: 
- php
- laravel
tags:
- php
layout: post
---
# 数据迁移

## 一些报错
```mysql
SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long; max key length is 1000 bytes
```
解决办法: 修改AppServiceProvider,boot方法中添加Schema::defaultStringLength(191);
```php
namespace App\Providers;

use Illuminate\Support\ServiceProvider;
use Illuminate\Support\Facades\Schema;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        Schema::defaultStringLength(191);
    }

    /**
     * Register any application services.
     *
     * @return void
     */
    public function register()
    {
        //
    }
}
```
[from](http://www.cnblogs.com/betx/p/6544090.html)
[原因](https://laravel.com/docs/master/migrations#creating-indexes)
