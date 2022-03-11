# Raspberry Pi BLE as Peripheral Device

## Point

* use "go Bluetooth" in RPi

## Reference

* <http://www.bluez.org>
* <https://www.jeremymorgan.com/tutorials/raspberry-pi/install-go-raspberry-pi/>

## Practice

Configure Go Setting

```bash
nano ~/.profile
```

edit .profile as below

```text
PATH=$PATH:/usr/local/go/bin
GOPATH=$HOME/go
```

update shell as configure

```bash
source ~/.profile
```

* install bluez

```bash
sudo apt update
sudo apt install bluez
```

* Git Clone Go Bluetooth

```bash
git clone https://github.com/tinygo-org/bluetooth.git
```

Compiling

```bash
cd bluetooth
go run ./examples/scanner
```