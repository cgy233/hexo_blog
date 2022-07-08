---
title: Hexo+Github配置个人博客问题总结
abbrlink: 2db31772
---

# Hexo+Github 配置个人博客(Windows10)

> 来源(<http://github.com/xinetzone.github.io.git>)

## 版本问题

**项目环境**:

- Node.js
- Hexo
- Git
- Yarn
- Pandoc (为 KateX 提供支持)

第一个踩坑的地方在 Node.js 的版本问题，导入这个项目时，我的 node.js 是最新版本14.4.0，回退长期支持版本12.18.1才能使项目正常运行，建议：对各种软件的选择应当选择LTS版本（长期支持），以避免出现不必要的麻烦。

第二个就是关于pandoc的版本问题，因为我的电脑中配置了Anaconda3的环境，里面存在Pandoc 2.2.*, 不支持KateX,编译失败,Pandoc官网的最新版本已经更新到2.9.\*,到官网下载最新版本的安装包安装即可。

---

## Git的使用

在这个项目中，我第一次在实践中使用git版本控制工具，上学期学习Android时已经安装好Git，第一次正式使用。

## 基本流程

### 一、配置ssh

打开git，输入以下命令(生成跟GitHub联系的密钥key):

```sh
ssh-keygen -t rsa
```

连续回车至结束后，会在用户根目录下生成两个文件id_rsa、id_rsa.pub,用记事本打开id_ras.pub，复制里面的内容。

登录GitHub
打开Settings=>点击左侧SSH and GPG keys=>new SSH keys
title随意，输入刚才复制的id_ras内容到第二个框内 点击确定即可。

测试连接：
打开git，输入以下命令：

```sh
ssh -T git@github.com
```

### 将本地仓库代码提交到GitHub

将GitHub上的仓库clone到本地

```sh
git clone 仓库链接
```

将所有文件添加到仓库中

```sh
git add .
```

提交申请

```sh
git commit - m '附加信息'
```

开始推送

```sh
git push origin master
```

**一般情况不要使用强推，深刻教训!!!**

---

### 第二种方式

初始化本地仓库

```sh
git init
```

关联本地仓库和远程仓库

```sh
git remote add origin git@github.com:github_username/github_name.git
```

拉取远程仓库文件

```sh
git pull origin master
```

添加新建的文件到仓库中

```sh
git add .
```

提交到本地仓库

```sh
git commit -m '附加信息'
```

推送到远程仓库

```sh
git push origin master
```

---

### 总结

**主要是在依赖的版本上出现了一些问题，另外就是对git的使用还不是很熟悉，不过积小成多，继续肝。**
