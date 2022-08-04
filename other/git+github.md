### Git[^1]

Git作为一个**分布式版本控制**软件，这类系统软件解决了工程师们在开发过程中，防止因为过多的版本迭代和代码修改，而造成的管理混乱。

它可以系统的记录每一次开发过程中的更改记录和版本历史以及都是谁做出的修改都能详细记录。就像下图一样。这样就能大大的提升开发的效率！

![img](https://pic2.zhimg.com/80/v2-2687ad3e74a73b889d89c205c29ec539_720w.jpg)

**【工作区】**电脑中能看到的目录、文件夹，add到暂存区

**【版本库/仓库/Repository】**

**【分支】**创建一个副本，不影响主干，想提交就提交，开发完毕后再合并到原来的分支



#### 和Github的关系[^1]

集中式的版本控制系统就是把代码集中统一存放到一个中央服务器，不论是谁要做什么事，都需要去这个中央服务器把最新的代码版本扒拉下来干活，干完活以后，便又要再一次推送给中央服务器。一旦当中央服务器挂了，就意味着代码库挂了，那就代表之前的努力都付诸东流了。

分布式版本管理系统，并不需要这个所谓的中央服务器，每个人各自的电脑里面都有一个完整的代码库，而且及时未能联网，你也依旧能愉快的工作，等完成了任务，待到有网之时，再同步到远程服务器即可。

虽然说分布式的版本控制系统，不需要要一个明确的中央服务器，但一般在实际的开发过程中，都会有这么一个东西，但它也仅仅只是扮演同步代码的角色，而GitHub就是扮演着这个角色。

GitHub扮演着托管Git代码的“中央服务器”角色。Git是一个软件，一个系统，而GitHub就是一个网站，一个基于Git而诞生的文件托管网站。我们可以通过Git的命令行来管理我们Github的项目版本管理。



#### Git操作入门[^2][^3]

- 安装Git
- Github创建项目仓库
- 本地Git，下载项目、添加文件、提交到Github



#### Git指令[^5]

- 初始操作

  ```bash
  # 在新建文件夹中初始化，生成.git文件夹
  git init
  ```

  

- 本地操作

  ```bash
  # 查看本地状态
  git status
  ```

  

- 分支操作

  ```bash
  # 查看分支
  git branch
  
  # 创建分支
  git branch 分支名
  
  # 切换到分支
  git checkout 分支名
  
  # 合并分支
  git merge 分支名
  
  # 删除分支
  git branch -d 分支名
  ```

  

- 设置操作

  ```bash
  # 设置用户名、密码, --global 表示全局设置，所有仓库都是
  git config --global user.name xxx
  git config --global user.email yyy
  ```

  

- 仓库操作

  新建和添加操作：

  ```bash
  # 现在仓库中建立个readme.txt, 再向仓库添加
  git add readme.txt
  
  # 提交
  git commit -m "提交说明"
  
  # 如果在本地修改readme.txt
  # 查看修改状态
  git status 
  
  # 查看具体修改内容
  git diff readme.txt
  
  #再次提交
  git add readme.txt
  git commit -m xxx
  ```

  版本回退：

  ```bash
  # 查看历史版本提交
  git log
  
  # 回退到上个版本
  git reset --hard HEAD^
  
  # 回退到上上一个版本
  git reset --hard HEAD^^
  
  # 回退上100个
  git reset --hard HEAD~100
  
  #回退了又想撤销
  git reset --hard 版本号（前几个字即可）
  
  # 只撤销在工作区的修改,回到最近commit的情况
  git checkout -- readme.txt
  
  # 已经add，撤销暂存区的修改
  git reset HEAD readme.txt
  
  # 如果在本地工作区删除某文件
  # 错删回复
  git checkout -- xx
  
  # 在版本库同样删除
  git rm xx.txt
  ```

  
  
- 远程仓库

  本地仓库推送到远程仓库（先有本地库)：

  ```bash
  # 在github上创建一个和本地同名的仓库后，连在一起, github上的仓库名为origin
  git remote add origin https://github.com/yuyan77/test.git
  
  # 把本地库主分支main的内容推送到远程库origin,第一次推送加-u表示把本地main分支推送到远程新的main分支，且本地main和远程main关联起来，以后推送可以简化
  git push -u origin main
  
  # 以后只要本地commit，就可以通过以下命令推送到远程
  git push origin main
  ```

  从远程库克隆(先有远程库)：

  ```bash
  # 从远程克隆一个本地库
  git clone (远程库地址)https://github.com/yuyan77/TestDemo.git
  
  # clone 私人仓库时 github.com 换成用户名yuyan或alex ，必须用ssh克隆
  git clone (远程库地址)git@alex:alex199773/mergedemo.git
  ```



- 分支管理

  ​        如果在分支上修改或添加文件，没有add、commit，切换分支后也可以看到这些文件，因为没有add、commit的不属于任何一个分支，即工作区和暂存区是公共的。

  ​        如果main和dev分支都同同一文件同一行修改，合并时会冲突，此时手动修改文件，并add & commit，main分支上的就修改为最新了，而dev分支没有改动，需要切换到dev分支上和main合并

  ```bash
  # 创建分支
  git branch 分支名
  
  # 切换到分支
  git checkout 分支名
  
  # 创建并切换到分支
  git switch -c 分支名
  
  # 查看当前分支
  git branch
  
  # 切换回主分支并合并dev
  git checkout main
  git merge dev
  
  # 合并完可以删除分支
  git branch -d dev
  
  
  
  # 远程仓库创建分支后拉到本地
  git checkout -b 本地分支名 origin/远程分支名
  
  # 本地创建分支后推送到远程
  git push origin 本地分支名:远程分支名（没有会新建）
  ```

- 多人协作

  ```bash
  # 此时，另一个小伙伴在另一个电脑/文件夹git clone
  
  # 创建远程的dev分支到本地(创建并切换到dev分支，该分支和origin上的dev分支关联起来，接下来的git push origin dev就可以推送到origin的dev分支上)
  git checkout -b dev origin/dev
  
  # 如果两个人都对同一文件修改，且add & commit，push产生冲突
  # 先 指定本地dev分支到远程origin/dev的链接
  git branch --set-upstream-to=origin/dev dev
  
  # 再git、pull把最新的提交（another修改过的提交）抓下来
  git pull
  
  # 操作同分支冲突，在本地修改（加上自己修改的部分）再提交
  git add txt
  git commit -m xxx
  git push origin dev
  
  # 查看本地分支和远程分支的关联关系
  git branch -vv
  ```

  

- 给别人代码Pr

  ```bash
  # fork到自己仓库
  
  # git clone到本地
  
  #新建一个本地分支，与远程仓库分支关联
  git checkout -b dev origin/dev
  
  #修改本地仓库分支,推送到远程仓库
  git add & commit
  git push -u origin dev:main
  
  # 存在原始仓库也修改过代码的可能
  # 建立原始仓库和本地仓库的连接
  git remote add upstream 原始仓库地址
  
  # 获取更新
  git fetch upstream
  
  # 本地合并更新
  git rebase upstream/main
  
  
  ```

- 同一个电脑多个github账号

  ```python
  # .ssh文件夹中的config文件 配置
  
  # 生成多个密钥
  cd ~/.ssh
  ssh-keygen -t rsa -f id_rsa_xx
  
  # github 上添加rsa_pub
  
  # 添加私钥
  cd ~/.ssh
  ssh-agent bash
  ssh-add id_rsa
  ssh-add id_rsa_2
  
  #查看私钥
  ssh-add -l
  
  # 测试ssh-key
  ssh -T git@yuyan
  ssh -T git@alex
  
  PS: 在ssh文件夹bash中改到d盘才能用？
  ```

  



### GitHub[^3]

面向开源及私有项目的托管平台，只支持Git作为版本库格式进行托管。

**【Repo】**即Repository，仓库。项目放在仓库中，建立项目之前先建立仓库。

**【Issue】**即问题，如果看他人代码并发现bug，可以提出Issue等待他人修改。

**【Fork】**即拉分支，将这个项目复制到自己账号中，独立原项目，我们可以在复制的项目上开发。

**【Pr】**即pull request，理解为提交请求，假如我们fork了一个项目，并进行修改，可以对原项目拥有人提出pull请求，对自己的请求审核，通过的话自己修改的内容可以合并到原项目中。

**【Merge】**Pr审核之后可以合并

### Ref

[^1]:[Git和GitHub的入门简介 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/183817184)
[^2]:[Git和Github初识 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/65614381)
[^3]:[还不会使用 GitHub ？ GitHub 教程来了！万字图文详解 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/369486197)
[^4]:[Git 工作区、暂存区和版本库 | 菜鸟教程 (runoob.com)](https://www.runoob.com/git/git-workspace-index-repo.html)
[^5]:[Git教程 - 廖雪峰的官方网站 (liaoxuefeng.com)](https://www.liaoxuefeng.com/wiki/896043488029600)
