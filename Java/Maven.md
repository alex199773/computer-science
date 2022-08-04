#### Maven目录结构[^2]

==约定优于配置==



![img](https://img-blog.csdnimg.cn/20210308172405716.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzIxMzcwNDE5,size_16,color_FFFFFF,t_70)





#### 介绍

- Maven是项目管理工具，一个项目往往依赖于其他的项目和第三方的组件才能顺利完成，Maven 提供了仓库的功能，让这些依赖项放进仓库中，项目可以随时从仓库中去取，如果其他项目组也需要这些依赖，同样也可以从仓库中去取。

- Maven 是 Java 项目构建工具，可以用于管理 Java 依赖，还可以用于编译、打包以及发布 Java 项目。

- 组成：

  ![img](http://mvnbook.com/static/image/maven-core.png)





#### Maven仓库[^1]

开发中引入的大量第三方库都放在Maven仓库中，maven仓库帮助管理这些jar。

运行 Maven 的时候，Maven 所需要的任何构件都是直接从本地仓库获取的。如果本地仓库没有，它会首先尝试从远程仓库下载构件至本地仓库，然后再使用本地仓库的构件。

![Maven仓库介绍](http://mvnbook.com/static/image/repository.png)



#### Maven项目创建[^3]

### 参考

[^1]:[Maven仓库 | Maven教程网 (mvnbook.com)](http://mvnbook.com/maven-repository.html)
[^2]:[Maven 标准项目目录 | Maven教程网 (mvnbook.com)](http://mvnbook.com/maven-standard-project-directory.html)

[^3]:[如何创建Maven项目 | Maven教程网 (mvnbook.com)](http://mvnbook.com/maven-how-to-create-a-project.html)