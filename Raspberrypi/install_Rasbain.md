# 安裝作業系統 Raspberry Pi

## Point

* 安裝各版本的作業系統

```text
 RPi4 使用 64bit ARM no desktop
 RPi3 使用 64bit ARM no desktop
 Rpi0 使用 32bit ARM lite no desktop
```

* 安裝後基礎設定

```bash
# 第一次登錄的帳號密碼為 username:pi,password:raspberry
# 進入設定, 至少修改以下項目
# 設定Wi-Fi
# 設定時區
# 設定密碼
sudo raspi-config

# 更新
sudo apt-get update
sudo apt-get upgrade
```


## 網站
* <https://www.raspberrypi.com/software/>
* <https://www.raspberrypi.com/software/operating-systems/>

## Reference

* <http://www.bluez.org>
* <https://www.jeremymorgan.com/tutorials/raspberry-pi/install-go-raspberry-pi/>

## 問題排解

* 出現 IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!

問題排除的方法

```bash
ssh-keygen -R 192.168.2.151
```

來源 <https://ithelp.ithome.com.tw/articles/10083004>

