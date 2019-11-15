`docker`的一大优势就是可移植性，容器因此`docker`容器可以随意的进行导入导出操作。

## 容器导出

使用`export`命令可以导出容器，具体操作如下：
   1. 创建一个容器进行基本的配置操作
   
本案例中我们首先创建一个`nginx`容器，然后启动，启动成功后，将本地一个index.html文件上传到容器中，
修改`nginx`首页的显示内容。具体操作步骤如下：

```bash
docker run -itd --name nginx -p 80:80 nginx
docker cp ./usr/local/www/html/indext.html nginx:/usr/share/nginx/html/
```

首先运行一个名为`nginx`的容器，然后在宿主主机中编辑一个index.html文件，编辑完成后，将该文件上传到容器中。
然后在浏览器输入`http://localhost`可以看到如下结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115164640817.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiZWxldGhhbg==,size_16,color_FFFFFF,t_70)

容器已经修改成功了。

接下来通过export命令将容器导出，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019111516531115.png)

该命令将容器导出到`nginx`

## 容器导入

接下来可以将`docker`中和`nginx`相关的容器和镜像删除。然后执行如下命令重新导入容器：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191115165907708.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiZWxldGhhbg==,size_16,color_FFFFFF,t_70)

容器导入成功后，就可以使用`docker run`命令运行了。
