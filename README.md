# 蓝牙温湿度计数据采集
[ENGLISH](README_EN.md)

## 功能简介
从 **米家蓝牙温湿度计2** (LYWSD03MMC) 循环读取温湿度数据，并存储到 SQLite 数据库文件中。

> **重要提示**：设备必须已刷入 **第三方固件** (pvvx ATC_v56.bin) 才能正常使用本脚本。

## 前提条件

### 硬件要求
- 米家蓝牙温湿度计2 (LYWSD03MMC)
- 支持蓝牙的计算机

### 固件要求
必须刷入第三方固件：**pvvx ATC_v56.bin**

## 固件刷写指南

### 1. 获取刷机工具
- **固件及刷机工具**：[ATC_MiThermometer](https://github.com/pvvx/ATC_MiThermometer)
- **设备信息提取工具**：[Tokens-Extractor](https://github.com/PiotrMachowski/Xiaomi-cloud-tokens-extractor)

### 2. 浏览器设置（Chrome）
1. 打开 Chrome 浏览器
2. 访问：`chrome://flags/#enable-experimental-web-platform-features`
3. 将该选项设置为 **Enabled**
4. 重启浏览器

### 3. 获取设备参数
使用 **Tokens-Extractor** 工具获取以下参数：
- `Device known id`
- `MAC Address`
- `Mi Token`
- `Mi Bind Key`

### 4. 刷机步骤
1. 访问 `ATC_MiThermometer` 的 Web 界面
2. 点击 `Connect` 按钮
3. 在设备列表中选择名为 `LYWSD03MMC` 开头的蓝牙设备（可能需要多次尝试）
4. 连接成功后，填入从 `Tokens-Extractor` 获取的参数
5. 选择固件：`Custom Firmware: ATC_v56.bin`
6. 点击 `Start Flashing` 开始刷机
7. 当提示 `Finished`，且设备名称变为 `ATC_xx` 格式时，表示刷机完成

## 脚本使用说明

### 1. 安装依赖
```bash
pip install bleak bthome-ble
```

### 2. 配置脚本
打开 `LYWSD03MMC_db.py` 文件，修改第 23 行的 `DEVICE_MAC` 变量：
```python
DEVICE_MAC = "您的设备MAC地址"  # 替换为从 Tokens-Extractor 获取的 MAC Address 
```

### 3. 运行脚本
```bash
python LYWSD03MMC_db.py
```
运行后选择选项 2 开始读取设备数据，直到终端提示"数据保存正常"。
注意：请确保设备已开启蓝牙并处于可连接状态，可能需要进行多次尝试。
