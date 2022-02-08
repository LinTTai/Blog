---
title: 新设备GitHub配置流程
data: 2021/12/28
tags: Git
categories: 技术
---

#### 一、概要

本地生成公钥，将本地公钥配置到远程 github，这个公钥就等于本地和远程 github 的链接桥梁。

#### 二、准备

github 账户密码，本地安装好 git

#### 三、ssh 配置

##### （1）本地配置

打开 git bash 工具，检查用户名和邮箱是否配置

```shell
$ git config --global --list
```

![image-20210827145839996](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210827145839996.png)

如未配置，则执行下面的命令进行配置

```shell
$ git config --global user.name "用户名"

$ git config --global user.eamil "邮箱"
```

接下来生成密钥

```
$ ssh-keygen -t rsa -C "邮箱"
```

1.确认秘钥的保存路径（如果不需要改路径则直接回车）；

2.如果上一步置顶的保存路径下已经有秘钥文件，则需要确认是否覆盖（如果之前的秘钥不再需要则直接回车覆盖，如需要则手动拷贝到其他目录后再覆盖）；

3.创建密码（如果不需要密码则直接回车）；

4.确认密码如果不需要密码则直接回车)；

在指定的保存路径下会生成 2 个名为 id_rsa 和 id_rsa.pub 的文件

##### （2）添加公钥到远程仓库(github)

进行 github 网页的配置选项：Settings -- SSH and GPG keys

![image-20210827150659824](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210827150659824.png)

添加本地生成的 ssh 秘钥，选择 New SSH key（这里已经配置了一个 key，如果是未配置秘钥的用户，这里是空的）

![image-20210827150752012](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210827150752012.png)

Title：自定义命名

Key：复制 id_rsa.pub 公钥内容

##### （3）测试配置是否成功

用 ssh 链接 git：

```shell
ssh -T git@github.com
```

![image-20210827151108168](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210827151108168.png)
