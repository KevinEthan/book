## 容器启动

### 启动

如果开发者使用了`docker run`命令创建了容器，则创建完成后容器就已经启动了，如果使用了
`docker create`命令创建了容器，则需要执行`docker start`命令来启动容器，使用`docker start`
命令结合容器id或者容器name可以启动一个容器，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115142532218.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiZWxldGhhbg==,size_16,color_FFFFFF,t_70)

`docker start`启动的是一个已经存在的容器，要使用该命令启动一个容器，必须要先知道容器的id或者name，
开发者可以通过两个属性启动一个容器（案例中，`nginx`是通过name启动的，而`centos`则是通过id启动） 
一般来说，第一次可以使用`docker run`启动一个容器，以后直接使用`docker start`即可。

### 重启

容器在运行过程中，会不可避免的出问题，出了问题时，需要能够自动重启，在容器启动时使用 --restart
参数可以实现这一需求。根据`docker`官方的解释，`docker`的重启策略可以分为4种，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115143704625.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiZWxldGhhbg==,size_16,color_FFFFFF,t_70)

四种的含义分别如下：

   1. `no` 表示不自动重启容器，默认即此。
   2. `on:failure:[max-retries]`表示在退出状态为非0时才会重启（非正常退出），有一个可选择参数：
      最大重启次数，可以设置最大重启次数，重启次数达到上限后就会放弃重启
   3. `always`表示始终重启容器，当`docker`守护进程启动时，也会无论容器当时的状态为何，都会尝试重启容器
   4. `ubless-stopped`表示始终重启容器，但是当`docker`守护进程启动时，如果容器已经停止运行，则不会去重启它。

## 容器暂停

通过`docker stop`命令可以终止一个容器，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115153322720.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiZWxldGhhbg==,size_16,color_FFFFFF,t_70)

可以通过name或者id终止一个容器

## 容器删除

### 单个删除

容器停止后还依然存在，如果需要，还可以通过`docker start`命令再次重启一个容器，如果不需要一个容器，
则可以通过`docker rm`命令删除一个容器。删除容器时，只能删除已经停止运行的容器，不能删除正在运行的
容器。如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115153720132.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiZWxldGhhbg==,size_16,color_FFFFFF,t_70)

同样可以通过name或者id删除一个容器。如果非要删除一个正在运行的容器，可以通过-f参数实现，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115154127701.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiZWxldGhhbg==,size_16,color_FFFFFF,t_70)

### 批量删除

容器也可以批量删除，命令如下：

```bash
docker rm $(docker ps -a -q)
```

`docker ps -a -q`会列出所有容器的id，供rm命令删除。

如下命令也支持删除已退出的孤立的容器：

```bash
docker container prune
```
