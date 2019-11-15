## 查看容器信息

容器创建成功后，用户可以通过`docker inspect`命令查看容器的详细信息，这些详细信息包括
容器id、容器名、环境变量、运行命令、主机配置、网络配置以及数据卷配置等信息。执行部分结果如下图：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115161105225.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiZWxldGhhbg==,size_16,color_FFFFFF,t_70)

使用format参数可以只查看用户关系的数据，例如：

   1. 查看容器运行状态
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115161332330.png)
   
   2. 查看容器ip地址
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115161441963.png)
   
   3. 查看容器名、容器ID
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115163527217.png)
   
   4. 查看容器主机信息
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115161832986.png)
   
## 查看容器进程

使用`docker top`命令可以查看容器中正在运行的进程，首先确保容器已经启动，然后执行
`docker top`命令。如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115163228782.png)

## 查看容器日志

交互型容器查看日志很方便，但是对于后台型容器，如果要查看日志，则可以使用`docker logs`
命令来查看，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115163625520.png)

如下图，首先启动一个不停打日志的容器，然后利用`docker logs`命令查看日志，但是默认情况下只能看到历史日志
，无法查看实时日志，使用`-f`参数后，就可以查看实时日志了。

使用`--tail`参数可以精确控制日志的输出行数，`-t`参数则可以显示日志的输出时间
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115162708688.png)

该命令在执行的过程中，首先输出最后的五行日志，同时由于添加了`-f`参数，因此，还会有其他日志持续输出。
同时，应为添加了`-t`参数，时间随用日志一起打印出来了。
