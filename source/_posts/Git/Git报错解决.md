---
title: Git报错解决
data: 2021/12/29
updated: 2021/12/29
tag: Git
categories: 技术
---

## OpenSSL SSL_read: Connection was reset, errno 10054 错误解决

造成这个错误很有可能是网络不稳定，连接超时导致的，
如果再次尝试后依然报错，可以执行下面的命令。

打开 Git 命令页面，执行 git 命令脚本：修改设置，解除 ssl 验证

```bash
git config --global http.sslVerify "false"
```

---

## The authenticity of host 'github.com(ip 地址)' can't be estalished.

新生成密钥的时候，git clone 或者 push 的时候，经常会报这样的错误

原因是少了一个 known_hosts 文件，本来密钥文件应该是三个，现在是两个，便报了这样的错误，造成这样的问题可能是没有输入 yes，直接回车了，此时选择 yes 回车之后，便可，同时生成了缺少了的 known_hosts 文件：

```bash
Are you sure you want to continue connection(yes/no)? // 输入yes, 回车
```
