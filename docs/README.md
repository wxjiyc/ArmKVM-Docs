<h1><div style="text-align:center">ArmKVM 官方文档</div></h1>
<p><div style="text-align:center">～ 性价比高、功能强大、易于使用、易于扩展的 IP-KVM 远程带外管理解决方案 ～</div>

> 欢迎参阅 ArmKVM 官方文档！在这里，您将会了解到关于 ArmKVM 的一切信息。如果还有其它的问题，请移步以下群组。
> - [QQ 群组](https://qm.qq.com/cgi-bin/qm/qr?_wv=1027&k=j4lvqFQAPLveE6DqOvLRsAP4AYs4F8ux&authKey=fWVysZsgwuAip563uOlXKcUlnIHd0Jd%2FhWRxCMXCARQH3JmqT%2B2uUikukKZp5Yj%2F&noverify=0&group_code=710527664)
> - [Telegram 群组]()

# ArmKVM 入门

## 简介

ArmKVM 是一款类似于 IPMI、PiKVM 和 Open IP-KVM 等远程带外管理解决方案的 IP-KVM 硬件产品，可以在不接入显示器、键盘、鼠标的情况下，通过网络对服务器或
PC 主机进行 BIOS 级的远程桌面、电源管理、远程串口、镜像挂载和重装系统等操作。ArmKVM 的特点是性价比高、功能强大、易于使用、易于扩展。

## 购买链接

### ArmKVM Standard V1

闲鱼渠道：[购买](https://m.tb.cn/h.5cBm7ge?tk=OJWPdFPHoU2)

## 硬件规格

| 型号      |              ArmKVM Standard V1              | PiKVM V3 Pre-Assembled |
|---------|:--------------------------------------------:|:----------------------:|
| SoC     |                   全志 H616                    |       博通 BCM2711       |
| 内存      |                 512MB / 1GB                  |        2G / 4G         |
| 存储      |                   外接 TF 卡                    |        外接 TF 卡         |
| USB     | 1 * USB Type-A / 2 * USB Type-A + 2 * USB 插针 |     4 * USB Type-A     |
| 以太网     |                10 / 100 Mbps                 |  10 / 100 / 1000 Mbps  |
| Wi-Fi   |  支持外接 RTL8811 / RTL8812 / RTL8821 / RTL8822  |           板载           |
| 尺寸 (含壳) |           86.5 mm x 74 mm x 27 mm            | 92 mm x 75 mm x 45 mm  |
| 重量 (含壳) |                     100g                     |          410g          |
| 售价      |                  $45 / $55                   |          $265          |

## 功能规格

| 功能           | ArmKVM Standard V1 | PiKVM |
|--------------|:------------------:|:-----:|
| 中文 WebUI     |      √ (WIP)       |   x   |
| 远程画面推流       |         √          |   √   |
| 远程键盘鼠标控制     |         √          |   √   |
| 大容量存储驱动器模拟   |         √          |   √   |
| 网络串口终端 (SoL) |         √          |   √   |
| ATX 电源控制     |         √          |   √   |
| 网页剪切板        |         √          |   √   |
| 网页终端         |         √          |   √   |
| GPIO 控制      |         √          |   √   |
| HDMI 切换器支持   |         √          |   √   |
| 远程网络唤醒 (WoL) |         √          |   √   |
| 本地看门狗        |         √          |   √   |
| 远程看门狗        |       √ (登录)       |   ×   |
| 全球快速连接技术     |       √ (登录)       |   ×   |
| 独立/临时连接码     |       √ (订阅)       |   ×   |
| 独立二级域名       |       √ (订阅)       |   ×   |
| 自动 UPnP 端口转发 |       √ (登录)       |   ×   |
| 内网穿透         |       √ (订阅)       |   ×   |
| 反向代理服务器      |       √ (订阅)       |   ×   |
| 邮件消息事件推送     |       √ (订阅)       |   ×   |
| 微信消息事件推送     |       √ (订阅)       |   ×   |

# 快速上手

## 系统烧录

!> 注意：烧录镜像前请务必确认您的 TF 卡规格至少为 `8GB` `Class 10` ，推荐的规格为 `64GB` `Class 10`
，同时确保重要数据已经备份，因为烧录镜像会清除 TF 卡上的所有数据。

1. ArmKVM 最新镜像下载：

| 硬件版本               | 系统环境       | IP-KVM 功能 | 发布版本                                      |                                                                                                                  |                                                                                   
|--------------------|------------|:---------:|-------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| ArmKVM-Standard-V1 | Arch Linux |   PiKVM   | arch-linux-pikvm-full-unstable-2307300201 | [下载](http://jsz.myds.me:10000/ArmKVM/images/ArmKVM-Standard-V1_Arch-Linux-PiKVM-Full-Unstable-2307300201.img.gz) |
| ArmKVM-Standard-V1 | Arch Linux |   PiKVM   | arch-linux-pikvm-minimal-unstable-230719  | [~~下载~~]()                                                                                                       |
| ArmKVM-Standard-V1 | BusyBox    |  ArmKVM   | buildroot-armkvm-unstable-230719          | [~~下载~~]()                                                                                                       |
| ArmKVM-Standard-V1 | BusyBox    |     ×     | buildroot-unstable-230719                 | [~~下载~~]()                                                                                                       |
| ArmKVM-Standard-V1 | Armbian    |     ×     | armbian-minimal-230719                    | [~~下载~~]()                                                                                                       |

> 历史镜像归档：[浏览](https://jsz.myds.me:10000/ArmKVM/images/archive)

2. 下载 Etcher 烧录工具：[Etcher 官网下载](https://etcher.balena.io)<br>
   Etcher 官方提供了 Windows、MacOS 和 Linux 三个平台的版本，您可以根据自己的系统下载对应的版本。<br>
   Etcher 官方下载地址较慢，您也可以从以下镜像链接下载：

|   系统    |   架构   | 类型        | 版本      |                                                                                                                       |
|:-------:|:------:|-----------|---------|-----------------------------------------------------------------------------------------------------------------------|
| Windows | X86_64 | 安装器 (exe) | 1.18.11 | [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.11/balenaEtcher-Setup-1.18.11.exe)    |
| Windows | X86_64 | 便携版 (exe) | 1.18.11 | [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.11/balenaEtcher-Portable-1.18.11.exe) |
|  MacOS  |  X64   | 安装器 (dmg) | 1.18.11 | [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.11/balenaEtcher-1.18.11.dmg)          |
|  Linux  |  X64   | 安装器 (deb) | 1.18.11 | [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.11/balena-etcher_1.18.11_amd64.deb)   |
|  Linux  | X86_64 | 安装器 (rpm) | 1.18.11 | [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.11/balena-etcher-1.18.11.x86_64.rpm)  |

3. 打开 Etcher 烧录工具，选择下载好的镜像文件，选择您的TF卡，点击 `烧录` 按钮开始烧录。
   烧录并校验完成后，您的TF卡会被弹出，您可以将TF卡插入 ArmKVM 中。

## 硬件连接

### ArmKVM Standard V1

[![ArmKVM Standard V1 接口资源](https://s1.ax1x.com/2023/07/29/pPSIhiq.png)](https://imgse.com/i/pPSIhiq)

#### 供电与网络 (必要)

ArmKVM Standard V1 的供电接口位于主板左下角，主板丝印标注为 `POWER&UART` ，需要使用随机附带的 `USB Type-B 连接线`
连接到输出电压为 `5V`,供电能力至少为 `1A` 的电源上。

!> 注意：使用输出电压为 `5V` 以上的电源将会对设备产生不可逆损伤。

以太网端口位于供电口上方，主板丝印标注为 `ETH`，需要使用 `五类` 及以上标准的网线将其接入路由器或交换机。

> 以下功能所需的硬件连接是可选的，您可以根据自己的需求选择是否连接。

#### HDMI 采集功能 (可选)

HDMI 采集接口位于主板右下角，主板丝印标注为 `HDMI IN`，需要使用 `HDMI 1.4` 及以上标准的HDMI高清线将其与被控主机或服务器的HDMI端口连接。

#### USB 键盘/鼠标/存储设备模拟 (可选)

`USB 键盘/鼠标/存储设备模拟` 功能由 ArmKVM 的 USB OTG 端口提供，位于 HDMI 采集接口的上方，主板丝印标注为 `USB OTG`
，需要使用随机附带的 `USB Type-B 连接线` 连接到被控主机或服务器。

#### ATX 电源管理控制 (可选)

`ATX 电源管理控制` 功能由 ArmKVM 上外形规格为 `RJ45` 的端口提供，位于主板右上方，主板丝印标注为 `ATX POWER CTL`
，需要使用 `五类` 及以上标准的网线将其接入随机附带的 `主机电源管理小板`。<br>

[![连接示意图](https://s1.ax1x.com/2023/07/29/pPSHN1P.png)](https://imgse.com/i/pPSHN1P)

使用随机附带的 `杜邦线` 连接 `主机电源管理小板` 上的 `主板面板线插针`
和被控主机或服务器主板上的插针。如果同时需要使用机箱面板上的电源按钮等功能，需要将 `机箱面板线` 连接到 `电源管理小板`
上的 `主机机箱面板线插针`。

[![主机电源管理小板 插针定义](https://s1.ax1x.com/2023/07/29/pPSbX2q.png)](https://imgse.com/i/pPSbX2q)

!> 注意：`主机电源管理小板` 上的 `主板面板线插针` 和 `机箱面板线插针` 的插针排列顺序可能与您的主板不同，您需要根据主板的数据手册上的定义进行合理接线。

!> 注意：部分主板的 `主板面板线插针` 定义设计不规范，可能存在如正负极颠倒的情况，从而导致 `主机电源管理小板`
无法正常工作，此时需要您翻转相关杜邦线的正负极。

#### 网络串口终端 (可选)

`网络串口终端` 功能由 ArmKVM 上外形规格为 `RJ45` 的串口提供，位于 USB OTG 端口的上方，主板丝印标注为 `RS232 COM`
，因此需要被控主机或服务器具有 `RS232` 通信标准的可收发串口。软路由的串口一般为 `RJ45` 外形规格，可以直接使用普通网线将其接入
ArmKVM 的 `RS232 COM` 口；服务器或工控设备的串口一般为 `DB9` 外形规格，需要使用 `RJ45 转 RS232 串口线` 将其接入 ArmKVM
的 `RS232 COM` 口。

## 连接到 ArmKVM

### 自动搜寻 (推荐)

> 该功能测试中，近期上线

1. 通过 GlobalConnect 功能，您可以在不知道 ArmKVM 的 IP 地址的情况下，自动搜寻到局域网内的 ArmKVM 设备。
   请确保您的 ArmKVM 和电脑在同一局域网内，然后访问 [GlobalConnect](https://find.ikvm.top) ，点击 `搜寻` 按钮即可。
2. 搜寻到的 ArmKVM 设备会显示在列表中，点击对应的`连接`按钮即可连接到 ArmKVM 的 Web 管理控制台。

### 手动连接

如果您的 ArmKVM 或电脑无法连接到 GlobalConnect 服务，或者您不想使用 GlobalConnect 功能，您可以通过以下方式手动连接到
ArmKVM 的 Web 控制台：

1. 登录您的路由器后台，查看 DHCP 客户端列表，找到 ArmKVM 的 IP 地址。<br>
   一般情况下，ArmKVM 的主机名为 `pikvm` ~~`ArmKVM-xxxx`，其中 `xxxx` 为 ArmKVM 的后四位 MAC 地址~~。

!> 如果 ArmKVM 不在您路由器的 DHCP 客户端列表中，请检查 ArmKVM 的电源是否已经打开、电源指示灯是否已经亮起、网线是否已经连接、网口灯是否已经亮起并闪烁。

2. 在浏览器中输入 ArmKVM 的 IP 地址，回车即可。

## 登录 Web 管理控制台

ArmKVM 的 Web 管理控制台默认用户名为 `admin`，默认密码为 `admin`，双因素身份验证留空，点击 `登录` 按钮。您现在可以愉快地使用
ArmKVM 提供的各项功能了，Enjoy it!
[![登录](https://s1.ax1x.com/2023/07/29/pPSOp4J.jpg)](https://imgse.com/i/pPSOp4J)

# 基本使用

[![菜单](https://s1.ax1x.com/2023/07/29/pPSOAu6.jpg)](https://imgse.com/i/pPSOAu6)

## 远程桌面 (KVM)

[![KVM](https://s1.ax1x.com/2023/07/29/pPSOn4H.jpg)](https://imgse.com/i/pPSOn4H)

## 镜像挂载 (MSD)

[![MSD](https://s1.ax1x.com/2023/07/29/pPSOhx1.png)](https://imgse.com/i/pPSOhx1)

## ATX 电源管理 (ATX Power Control)

[![ATX](https://s1.ax1x.com/2023/07/29/pPSOd8s.png)](https://imgse.com/i/pPSOd8s)

## 网页终端 (WebTTY)

[![WebTTY](https://s1.ax1x.com/2023/07/29/pPSOOGd.jpg)](https://imgse.com/i/pPSOOGd)

## 网络串口终端 (SoL)

在 `网页终端` 界面输入 `sol` 命令并回车，按照提示输入与被控主机或服务器通信的串口波特率，回车即可登录到串口通信窗口。

# 进阶使用

## 切换至 root 用户

在 `网页终端` 界面输入 `su -` 命令并回车，按照提示输入 root 用户的默认密码 `root`，回车即可切换至 root 用户。

## 文件系统只读/读写模式切换

在 `网页终端` 界面输入 `rw` 命令并回车，即可切换至读写模式。再次输入 `ro` 命令并回车，即可切换至只读模式。

## 无线网络配置

!> 注意：使用 `nmtui` 命令配置无线网络前，请先切换至 root 用户并将文件系统切换至读写模式。

将受支持的USB无线网卡接入ArmKVM，在 `网页终端` 界面输入 `nmtui` 命令并回车。
[![NetworkManager TUI](https://s1.ax1x.com/2023/07/29/pPpFYZ9.jpg)](https://imgse.com/i/pPpFYZ9)
进入 `NetworkManager TUI` 界面后，使用方向键选择 `Activate a connection` 并回车，即可扫描并选择您的无线网络。
[![无线网络列表](https://s1.ax1x.com/2023/07/30/pPpFhz8.jpg)](https://imgse.com/i/pPpFhz8)

## 端口转发

### 自动

### 手动

## 内网穿透

## 虚拟局域网 (VPN)

# 常见问题

## 版本与规格

## 外设支持列表