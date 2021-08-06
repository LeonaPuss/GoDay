# Git

[TOC]

## How to learn Git?

[Git尚学堂](https://www.bilibili.com/video/BV1pW411A7a5?p=26)

[廖雪峰的Git课程](https://www.liaoxuefeng.com/wiki/896043488029600/897013573512192)

[GitGuide 简化汉字版](https://github.com/ZJDoc/GitGuide "«GitGuide»记录了版本管理操作规范、工具以及托管平台使用")

## Git 权威著作

[Pro Git](https://git-scm.com/book/en/v2)

[Pro Git 简化汉字版](https://git-scm.com/book/zh/v2)

[Git Offical Docs](https://git-scm.com/docs/)

[Bitbucket Learn Git](https://www.atlassian.com/git/tutorials/syncing/git-pull)

## github ssh

[git ssh key配置](https://blog.csdn.net/lqlqlq007/article/details/78983879)

[使用TortoiseGit，设置ssh方式连接git仓库。](https://blog.csdn.net/dengdi8489/article/details/102010452)

[Configure TortoiseGitPlink to autoload key for a specific URL](https://stackoverflow.com/questions/36163639/configure-tortoisegitplink-to-autoload-key-for-a-specific-url)

[troubleshooting-ssh](https://docs.github.com/en/github/authenticating-to-github/troubleshooting-ssh/error-permission-denied-publickey)

## Git merge

[How to resolve merge conflicts in a Git repository](https://stackoverflow.com/questions/161813/how-to-resolve-merge-conflicts-in-a-git-repository
)

[Git mergetool: Specifying Which Merge Tool Git Should Use](https://www.intertech.com/git-mergetool-specifying-which-merge-tool-git-should-use/
)

```git
git config --global merge.tool myfavtool
git config --global mergetool.myfavtool.cmd myfavtool_executable $BASE $LOCAL $REMOTE $MERGED
```


[VIM 简述](https://fx.tmioe.com/800.html)

vim vimdiff diff 使用及命令
https://www.cnblogs.com/mfryf/p/4936907.html

How do I jump to the next/prev diff in GIT difftool?
https://stackoverflow.com/questions/27151456/how-do-i-jump-to-the-next-prev-diff-in-git-dif

:diffg RE 操作提示如下：
E93: More than one match for RE
尝试
:diffget REMOTE

## Wget a script and run it
[Wget a script and run it](https://serverfault.com/questions/226386/wget-a-script-and-run-it)

### Non-Interactive Scripts

```bash
wget -O - http://website.com/my-script.sh | bash  
```

多数是这种
Note that when using this method, interactive scripts will not work.


### Interactive Scripts

In order to get interactive scripts working, you can use this:

```bash
bash <(wget -qO- http://website.com/my-script.sh)
```


### Interactive Scripts that need to be run as root

Warning: This is extremely dangerous. Not recommended.

```bash
sudo su -c "bash <(wget -qO- http://website.com/my-script.sh)" root
```

Note that you cannot simple use sudo bash since using <(...) will create a virtual file and it's file descriptor will not be accessible from roots bash instance. It must be executed on the same user that needs to read the virtual file, so it has to be sent as it's own command inside the root users shell.

How to use git push force the right way
https://www.datree.io/resources/git-push-force

IntelliJ IDEA 2021.1.3 破解激活安装教程
https://www.exception.site/article/31

公众号：Java学习者社区 -IDEA

mklink /d 符号链接（硬链接快捷）itunes备份文件路径方法
https://jingyan.baidu.com/article/466506580dde28f549e5f817.html


## git add 多个文件和文件夹的方法

方法三 添加指定目录下的文件
config目录下及子目录下所有文件，home目录下的所有.php文件

```
git config/*
git home/*.php
```

1
2
方法四 git add . 添加所有的文件， 或者 git add --all 添加所有的文件

```
git add .
git add --all
```
1
2
git add 文件夹
git add 文件夹名
———————————————
版权声明：本文为CSDN博主「一筐大白菜啊」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/sphinx1122/article/details/89789929

NAS 2021 Jun 1 装机方案
https://www.youtube.com/watch?v=lpNGeonJtJw

[An Intro to Git and GitHub for Beginners (Tutorial)](https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners)

[Collaborating with pull requests](https://docs.github.com/en/github/collaborating-with-pull-requests)

[Pull Request 用命令行管理](http://www.ruanyifeng.com/blog/2017/07/pull_request.html)

[搭建基于WordPress的个人网站](https://flyzy2005.github.io/2018/01/25/build-home-page-with-wordpress/)

[如何在 GitHub 提交第一个 pull request](https://chinese.freecodecamp.org/news/how-to-make-your-first-pull-request-on-github/)

### End of line EOL
[EOL vs-code-and-git](https://medium.com/@csmunuku/windows-and-linux-eol-sequence-configure-vs-code-and-git-37be98ef71df)
UNIX \n LF is BEST !

VS Code "Ctrl+Alt+P" "EOL"

```
git config --global core.autocrlf true
```
