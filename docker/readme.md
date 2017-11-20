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
