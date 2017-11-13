# docker


## docker 删除所有容器
```shell
docker stop $(docker ps -q) & docker rm $(docker ps -aq)
#sudo docker stop $(sudo docker ps -q) & sudo docker rm $(sudo docker ps -aq)
```
