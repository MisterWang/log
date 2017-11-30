# virtualbox

## 在windows下以共享文件形式与虚拟机中的linux共享文件夹时，静态文件(css,js,html）修改后，服务器(nginx,apache)无法识别，但vim中打开正常
测试似乎与atime,mtime无关

似乎是nginx 的缓存
设置sendfile后正常
```nginx
sendfile off;
```
TODO 排查 nginx缓存原因(vboxsf) 以及apache缓存的设置
