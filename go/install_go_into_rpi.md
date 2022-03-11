# RASPBERRY PI 安裝 golang

## 知識點

* 安裝在 raspberry pi 4B+
* 安裝在 raspberry pi 0
* Linux 遠端文件傳輸指令 SCP

## 網站

<https://golang.org/dl/>

## 實戰

下載最新版的Go軟體並安裝(RPi 4)

```bash
# 下載最新版的Go軟體並安裝(RPi 4)
sudo apt-get install golang
# 設定go路徑
nano ~/.profile
```

```text
export GOROOT=/usr/lib/go
export GOPATH=$HOME/go
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
```

更新 profile

```bash
source ~/.profile
```

RPi4 編譯測試 Hello world

```bash
# mkdir -p $GOPATH/src/github.com/user
mkdir -p $GOPATH/src/github.com/livinghuang/hello
cd $GOPATH/src/github.com/livinghuang/hello
nano hello.go
```

```text
package main

import "fmt"

func main() {
    fmt.Println("Hello, world.")
}
```

```bash
go run hello.go
# 然後就成功了 Hello, world.
```

將他安裝到系統上，讓他在各地都可以執行

```bash
go install github.com/livinghuang/hello
cd ~
hello
# 然後又成功了 Hello, world.
```

將Rpi4編譯bin檔傳送到Rpi0執行

```bash
#(在 RPI4 上)
# 從本地端複製到遠端
# scp /path/file1 myuser@192.168.0.1:/path/file2
scp ~/go/hello pi@192.168.1.101:~/go/hello
```

```bash
#(在 RPI0 上)
./hello
```

## 參考

<https://zh-tw.coderbridge.com/@Jemmy1234/59d6b40fb69a4461b40ae72a030c509a>
