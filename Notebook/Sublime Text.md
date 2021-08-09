# Sublime Text

## Sublime Text 4 正式版发布了，自己动手注册激活以及汉化

[Sublime Text 4 激活方法](https://51.ruyo.net/17264.html)

**激活软件,不太推荐使用网上的破解工具~  以下方法亲测可行！**

1. 在软件的安装目录找到 sublime_text.exe 文件。

2. 使用十六进制编辑器，打开 sublime_text.exe 文件。

3. 然后查找以下字节并且替换（不同的软件版本替换的内容略有不同，一定要看好软件版本）。

```
软件版本 4113 依此替换下方 2 组字节！
C3 C6 01 00 C3 替换为 C3 C6 01 01 C3
51 31 C0 88 05 替换为 51 b0 01 88 05
```

## Sublime Text  汉化

安装 ChineseLocalizations,帮助中“Language”里面切换。