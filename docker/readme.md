# docker


## docker 删除所有容器
```shell
docker stop $(docker ps -q) & docker rm $(docker ps -aq)
#sudo docker stop $(sudo docker ps -q) & sudo docker rm $(sudo docker ps -aq)
```

## windows 7 toolbox 
[toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/)

### 配置其他cmd
```shell
docker-machine env default
```


### babun中
[babun.sh](toolbox-babun)

### .babunrc
[babunrc.sh](toolbox-babunrc)


### 一个容器间互相访问的问题
因为监听了127.0.0.1这个ip。

#### 127.0.0.1与0.0.0.0的区别
127.0.0.1只能本机访问，无法通过它对外提供服务。

0.0.0.0 则表示本机所有ip。如本机有192.168.0.2，10.0.0.2和127.0.0.1三个ip,使用它表示同时监听这些ip的某个端口。
[from](http://www.mamicode.com/info-detail-1144209.html)
