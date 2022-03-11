# 設定 RASPBERRY PI ZERO AS LORAWAN GATEWAY

## 知識點

* 安裝 raspberry pi
* 初始化 Rpi linux system
* 安裝 lora_gateway driver
* 安裝 package forwarder
* 安裝 Heltec driver

## 實戰

```bash
#系統會自動將所有已經安裝在系統內的套件升級為最新版本。
sudo apt-get update
sudo apt-get upgrade -y
#安裝git套件
sudo apt-get install git
# 製作Lora資料夾並移動到該資料夾目錄
mkdir lora
cd lora
# 下載 LoRa Gateway drivers
git clone https://github.com/Lora-net/lora_gateway.git
# 下載 packet forwarding software
git clone https://github.com/Lora-net/packet_forwarder.git
# 下載  Heltec SDK 
git clone https://github.com/HelTecAutomation/lorasdk.git
# 安裝 LoRa Gateway drivers
cd /home/pi/lora/lora_gateway
make clean all
# 安裝 packet_forwarder
cd /home/pi/lora/packet_forwarder
make clean all
# 安裝 Heltec install.sh
cd /home/pi/lora/lorasdk
chmod +x install.sh 
# 執行 install.sh
./install.sh
# 執行lorasdk後會讓開機時自動執行LoRa Gateway drivers與packet_forwarder
#將Freq.plan 設為 "global_conf_AS923_2" 你也可以修改成你要的Freq.plan 可以在/home/pi/lora/lorasdk/找到對應的範本
sudo cp -f /home/pi/lora/lorasdk/global_conf_AS923_2.json /home/pi/lora/packet_forwarder/lora_pkt_fwd/global_conf.json
# 編輯設定檔
nano /home/pi/lora/packet_forwarder/lora_pkt_fwd/global_conf.json
```

```text
# 只要編輯目標network server網址就可以, 如果在本機上執行network server的話這裡就設定為localhost就可以了
# 設定 network server address
```

```bash
#最後確認一下安裝有沒有正常
sudo systemctl status lrgateway
然後就成功了
```

## Reference

<https://delorescetleh.medium.com/lora-lorawan-%E7%AC%AC%E5%8D%81%E4%B9%9D%E7%AF%80-e3ac22bcd88>
