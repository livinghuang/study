# RASPBERRY PI 安裝 golang

## 知識點

* 安裝在 raspberry pi 4B+
* 安裝在 raspberry pi 0
* ARMv6 Arch for RPi4 , RPi0
* Linux 遠端文件傳輸指令 SCP

## 網站

<https://golang.org/dl/>

## 實戰

下載最新版的Go軟體並安裝

```bash
mkdir ~/src && cd ~/src
# 下載最新版的軟體
wget https://go.dev/dl/go1.17.8.linux-armv6l.tar.gz
wget https://go.dev/dl/go1.17.8.linux-arm64.tar.gz
# 解壓縮
sudo tar -C /usr/local -xzf go1.17.8.linux-armv6l.tar.gz
sudo tar -C /usr/local -xzf go1.17.8.linux-arm64.tar.gz
# 清除安裝檔
rm go1.17.8.linux-armv6l.tar.gz

export GOPATH=$HOME/goexport PATH=$PATH:/usr/local/go/bin
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
go install github.com/livinghuang/hello
```

將Rpi4編譯bin檔傳送到Rpi0執行

```bash
#(在 RPI4 上)
# 從本地端複製到遠端
# scp /path/file1 myuser@192.168.0.1:/path/file2
scp ~/go/helo pi@192.168.1.101:~/go/helo
```

```bash
#(在 RPI0 上)
./helo
```

## 參考
<https://www.jeremymorgan.com/tutorials/raspberry-pi/install-go-raspberry-pi/>
<https://openhome.cc/Gossip/Go/HelloWorld.html>

## 問題排解

```bash
cd /var/lib/dpkg/
sudo mv info/ info_bak # 現將info資料夾更名
sudo mkdir info # 再新建一個新的info資料夾
sudo apt-get update # 更新
sudo apt-get -f install # 修復
sudo mv info/* info_bak/ # 執行完上一步操作後會在新的info資料夾下生成一些檔案，現將這些檔案全部移到info_bak資料夾下
sudo rm -rf info # 把自己新建的info資料夾刪掉
sudo mv info_bak info # 把以前的info資料夾重新改回
```
