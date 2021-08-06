### Golang

[TOC]

## Install

### Windows

1. 进入VS环境前，先在CMD中操作如下环境调整命令，改Go代理；第3行的命令是我自己侥幸测试出来的。环境是1.16.6，似乎在VS里面go插件怎么也没起作用后，可以先下载数据到本地

```cmd
go env -w GO111MODULE=on
go env -w GOPROXY=https://goproxy.cn,direct
go.exe get -v -d github.com/stamblerre/gocode
```

安装成功提示
```cmd
Tools environment: GOPATH=C:\Users\SKIPPER\go
Installing 10 tools at C:\Users\SKIPPER\go\bin in module mode.
  gopkgs
  go-outline
  gotests
  gomodifytags
  impl
  goplay
  dlv
  dlv-dap
  staticcheck
  gopls

Installing github.com/uudashr/gopkgs/v2/cmd/gopkgs (C:\Users\SKIPPER\go\bin\gopkgs.exe) SUCCEEDED
Installing github.com/ramya-rao-a/go-outline (C:\Users\SKIPPER\go\bin\go-outline.exe) SUCCEEDED
Installing github.com/cweill/gotests/gotests (C:\Users\SKIPPER\go\bin\gotests.exe) SUCCEEDED
Installing github.com/fatih/gomodifytags (C:\Users\SKIPPER\go\bin\gomodifytags.exe) SUCCEEDED
Installing github.com/josharian/impl (C:\Users\SKIPPER\go\bin\impl.exe) SUCCEEDED
Installing github.com/haya14busa/goplay/cmd/goplay (C:\Users\SKIPPER\go\bin\goplay.exe) SUCCEEDED
Installing github.com/go-delve/delve/cmd/dlv (C:\Users\SKIPPER\go\bin\dlv.exe) SUCCEEDED
Installing github.com/go-delve/delve/cmd/dlv@master (C:\Users\SKIPPER\go\bin\dlv-dap.exe) SUCCEEDED
Installing honnef.co/go/tools/cmd/staticcheck (C:\Users\SKIPPER\go\bin\staticcheck.exe) SUCCEEDED
Installing golang.org/x/tools/gopls (C:\Users\SKIPPER\go\bin\gopls.exe) SUCCEEDED

All tools successfully installed. You are ready to Go :).
```

最后记得调整参数。
go env -w GO111MODULE=auto