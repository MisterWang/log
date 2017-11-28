# virtualbox

## 在windows下以共享文件形式与虚拟机中的linux共享文件夹时，静态文件(css,js,html）修改后，服务器(nginx,apache)无法识别，但vim中打开正常
测试似乎与atime,mtime无关

TODO 排查 nginx缓存 或者是文件系统缓存(vboxsf)
