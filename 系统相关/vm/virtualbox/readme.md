# virtualbox

## 在windows下以共享文件形式与虚拟机中的linux共享文件夹时，静态文件(css,js,html）修改后，服务器(nginx,apache)无法识别，但vim中打开正常
测试似乎与atime,mtime无关

似乎是nginx sendfile 导致的
关闭sendfile后正常
```nginx
sendfile off;
```
TODO SEDNFILE

[vagrant](https://www.vagrantup.com/docs/synced-folders/virtualbox.html)
[issue](https://github.com/hashicorp/vagrant/issues/351#issuecomment-1339640)

[参考](https://qiita.com/liubin/items/c2d39ef63a44bb3c2d66)

[最早出现在10年前](https://www.virtualbox.org/ticket/81)
