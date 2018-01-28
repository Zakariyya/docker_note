command:

```

docker rm   //delete container
docker rmi  //delete image
docker cp   // copy the file  between the host and container
docker commit  // save a image when the image been modify
```

#命令

### images

```
docker images
```

### pull

```shell
docker pull hub.c.163.com.library/nginx:latest
```

### ps

```
docker ps  //查看当前进程
```

### run

```
docker run -d <images name> //后台运行一个docker镜像，并返回一个容器ID
docker run -d -p 8080:80 容器的名字
docker run -d -P 容器名字

-d : 后台运行
-p : 端口映射 前面（本机端口）：后面（容器端口）
-P : 所有的主机端口都会跟主机建立映射（随机端口）

```

### exec

```
docker exec -it 容器ID bash
```

###stop	

```
docker stop 容器ID
```

###构建一个Docker镜像

####build(构建一个容器)

``` 
先新建一个DockerFile文件
格式：
-----------------
from tomcat  ##声明这是依赖于Tomcat创建的镜像
MAINTAINER anan  ##作者
COPY at.war /usr/local/tomcat/webapps   ##把at.war包放到tomcat的webapps中

-----------------
docker build .  //在DockerFile的目录下运行，创建属于自己的镜像
docker build -t 新镜像的名字 .

```

#####编辑Dockerfile

> Dockerfile用来创建一个自定义的image，包含了用户指定的软件依赖等

```
FROM centos
MAINTAINER anan
RUN yum -y install httpd
ADD start.sh /usr/local/bin/start.sh
ADD index.html /var/www/html/index.html

注释：
FROM centos  ##FROM基于哪个镜像
MAINTAINER anan  ##镜像的创建者
RUN yum -y install httpd  ## RUN 安装软那件
ADD start.sh /usr/local/bin/start.sh  
ADD index.html /var/www/html/index.html
##ADD  将文件<src>拷贝到新产生的镜像的文件系统对应的路径<dest>。所有拷贝到新镜像中的文件和文件夹权限为0755,uid 和 gid 为0。
```

####commit

```
docker commit 容器ID  image名字 //保存container的当前状态到image后，然后生成对应的image
docker commit 857386165d5c mysql:me
```

###Docker镜像的发布

#### save Image To TarBall

```
保存Image到tar包
语法：docker save -o 导出的镜像名.tar  本地镜像名


```

#### push Image To Docker Hub

```
1. 注册一个账号
2. 登陆docker hub
   # docker login -u userabc -p 123456 -e userab@gmail.com
3.发布镜像到hub
  #docker push centos:httpd    ##上传
4.从hub上拉镜像                       
  # docker pull  userabc/centos:httpd    ##下载  用户名/镜像名
```

### info

```
docker info  //查看docker的信息
```

### search

```
docker search centos  //搜索镜像（images）
```

### load

```
docker load -i /root/centos-latest-docker-image.tar  //把之前下载好的image镜像导入到image
导入：docker load -i 准备导入的镜像.tar
-i : centos-latest-docker-images.tar  制定载入的镜像归档
```

### restart

```
docker restart 容器ID
```

### cp

```
> 用于容器与主机之间的数据拷贝。
 docker cp /www/runoob 96f7f14e99ab:/www/  ## 将主机/www/runoob目录拷贝到容器96f7f14e99ab的/www目录下。
 
 docker cp /www/runoob 96f7f14e99ab:/www  ## 将主机/www/runoob目录拷贝到容器96f7f14e99ab中，目录重命名为www。
 
 docker cp  96f7f14e99ab:/www /tmp/  ##将容器96f7f14e99ab的/www目录拷贝到主机的/tmp目录中。
```

###  container prune

```

清理所有处于终止状态的容器
用 docker container ls -a 命令可以查看所有已经创建的包括终止状态的容器，如果数量太多要一个个删除可能会很麻烦，用下面的命令可以清理掉所有处于终止状态的容器。
> docker container prune
```

###rm

```
可以使用 docker container rm 来删除一个处于终止状态的容器。例如

$ docker container rm  trusting_newton
trusting_newton
```



***

## linux

```
which nginx  //在nginx下，查看nginx的位置
```
