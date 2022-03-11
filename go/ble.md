# Raspberry Pi BLE with Go Bluetooth

## Point

* use "go Bluetooth" in RPi

## Reference

* <https://github.com/tinygo-org/bluetooth.git>
* <https://pkg.go.dev/github.com/go-ble/ble>

## Practice

* install bluez

```bash
sudo apt update
sudo apt install bluez
```

* Git Clone Go Bluetooth

```bash
git clone https://github.com/tinygo-org/bluetooth.git
```

Compiling as Scanner

```bash
cd bluetooth
go run ./examples/scanner
```

Compiling as nusserver (UART by pass)

```bash
cd bluetooth
go run ./examples/nusserver
# now you could open your iphone connect with RPi and send data to it.
# you also could send data from iphone to Rpi 
```
