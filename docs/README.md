<h1><div style="text-align:center">ArmKVM 官方文档</div></h1>
<p><div style="text-align:center">～性价比高、功能强大、易于使用、易于扩展的 IP-KVM 远程带外管理解决方案～</div>

> 欢迎参阅 ArmKVM 官方文档！在这里，您将会了解到关于 ArmKVM 的一切信息。如果还有其它的问题，请移步以下群组。
> - [QQ 群组](https://qm.qq.com/cgi-bin/qm/qr?_wv=1027&k=j4lvqFQAPLveE6DqOvLRsAP4AYs4F8ux&authKey=fWVysZsgwuAip563uOlXKcUlnIHd0Jd%2FhWRxCMXCARQH3JmqT%2B2uUikukKZp5Yj%2F&noverify=0&group_code=710527664)
> - [Telegram 群组]()

# ArmKVM 入门

## 简介

ArmKVM 是一款类似于 IPMI、PiKVM 和 Open IP-KVM 等远程带外管理解决方案的 IP-KVM 硬件产品，可以在不接入显示器、键盘、鼠标的情况下，通过网络对服务器或
PC 主机进行 BIOS 级的远程桌面、电源管理、远程串口、镜像挂载和重装系统等操作。ArmKVM 的特点是性价比高、功能强大、易于使用、易于扩展。

## 硬件规格

| 型号    |                ArmKVM Standard V1                |        PiKVM        |
|-------|:------------------------------------------------:|:-------------------:|
| SoC   |                     全志 H616                      |         BCM         |
| 内存    |                   512MB / 1GB                    |       2G / 4G       |
| 存储    |                     外接 TF 卡                      |       外接 TF 卡       |
| USB   |                        1                         |          1          |
| 以太网   |                   10 / 100Mbps                   | 10 / 100 /1000 Mbps |
| Wi-Fi | 支持外接 RTL8811 / RTL8812 / RTL8821 / RTL8822 (WIP) |                     |
| 尺寸    |                    68mm×79mm                     |          1          |
| 重量    |                        1                         |          1          |
| 价格    |                        1                         |          1          |

## 功能规格

| 功能           | ArmKVM Standard V1 | PiKVM |
|--------------|:------------------:|:-----:|
| 中文 WebUI     |      √ (WIP)       |   x   |
| 远程画面推流       |         √          |   √   |
| 远程键盘鼠标控制     |         √          |   √   |
| 大容量存储驱动器模拟   |         √          |   √   |
| 网络串口 (SoL)   |         √          |   √   |
| ATX 电源控制     |         √          |   √   |
| 网页剪切板        |         √          |   √   |
| 网页终端         |         √          |   √   |
| GPIO 控制      |         √          |   √   |
| HDMI 切换器支持   |      √ (WIP)       |   √   |
| 远程网络唤醒 (WoL) |         √          |   √   |
| 本地看门狗        |         √          |   ×   |
| 远程看门狗        |      √ (WIP)       |   ×   |
| 全球快速连接技术     |       月付版支持        |   ×   |
| 独立/临时连接码     |       月付版支持        |   ×   |
| 独立二级域名       |       月付版支持        |   ×   |
| 自动 UPnP 端口转发 |       月付版支持        |   ×   |
| 内网穿透         |       月付版支持        |   ×   |
| 反向代理服务器      |       月付版支持        |   ×   |
| 邮件消息事件推送     |       月付版支持        |   ×   |
| 微信消息事件推送     |       月付版支持        |   ×   |

# 快速上手

## 系统烧录

!> 注意：烧录镜像前请务必确认您的 TF 卡规格至少为 `8GB` `Class 10` ，同时确保重要数据已经备份，因为烧录镜像会清除 TF
卡上的所有数据。

1. ArmKVM 镜像下载：

| 硬件版本               |           系统版本            |                                                                                                                  |                                                                                   
|--------------------|:-------------------------:|:----------------------------------------------------------------------------------------------------------------:|
| ArmKVM-Standard-V1 | PiKVM-Beta-1.0.0-20230516 | [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.8/balenaEtcher-Setup-1.18.8.exe) |

2. 下载Etcher烧录工具：[Etcher官网](https://etcher.balena.io)<br>
   Etcher官方提供了 Windows、MacOS 和 Linux 三个平台的版本，您可以根据自己的系统下载对应的版本。<br>
   Etcher官方下载地址较慢，您也可以从以下镜像链接下载：

| 系统      |   架构   | 类型        |   版本   |                                                                                                                     |
|---------|:------:|:----------|:------:|:-------------------------------------------------------------------------------------------------------------------:|
| Windows | X86_64 | 安装器 (exe) | 1.18.8 |  [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.8/balenaEtcher-Setup-1.18.8.exe)   |
| Windows | X86_64 | 便携版 (exe) | 1.18.8 | [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.8/balenaEtcher-Portable-1.18.8.exe) |
| MacOS   |  X64   | 安装器 (dmg) | 1.18.8 |     [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.8/balenaEtcher-1.18.8.dmg)      |
| Linux   |  X64   | 安装器 (deb) | 1.18.8 |  [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.8/balena-etcher_1.18.8_amd64.deb)  |
| Linux   | X86_64 | 安装器 (rpm) | 1.18.8 | [下载](https://cors.isteed.cc/github.com/balena-io/etcher/releases/download/v1.18.8/balena-etcher-1.18.8.x86_64.rpm)  |

3. 打开Etcher烧录工具，选择下载好的镜像文件，选择您的TF卡，点击`烧录`按钮开始烧录。
   烧录并校验完成后，您的TF卡会被弹出，您可以将TF卡插入ArmKVM中。

## 硬件连接

## 连接到 ArmKVM

### 自动搜寻 (推荐)

1. 通过 GlobalConnect 功能，您可以在不知道 ArmKVM 的 IP 地址的情况下，自动搜寻到局域网内的 ArmKVM 设备。
   请确保您的ArmKVM和电脑在同一局域网内，然后访问[GlobalConnect](http://find.ikvm.top)，点击`搜寻`按钮即可。
2. 搜寻到的 ArmKVM 设备会显示在列表中，点击对应的`连接`按钮即可连接到 ArmKVM 的 Web 控制台。

### 手动连接

如果您的 ArmKVM 或电脑无法连接到 GlobalConnect 服务，或者您不想使用 GlobalConnect 功能，您可以通过以下方式手动连接到
ArmKVM 的 Web 控制台：

1. 登录您的路由器后台，查看 DHCP 客户端列表，找到 ArmKVM 的 IP 地址。<br>
   一般情况下，ArmKVM 的主机名为 `ArmKVM-xxxx`，其中 `xxxx` 为 ArmKVM 的后四位 MAC 地址。

!> 如果 ArmKVM 不在您路由器的 DHCP 客户端列表中，请检查 ArmKVM 的电源是否已经打开、电源指示灯是否已经亮起、网线是否已经连接、网口灯是否已经亮起并闪烁。

2. 在浏览器中输入 ArmKVM 的 IP 地址，回车即可。

## 登录 Web 管理控制台

ArmKVM 的 Web 管理控制台默认用户名为 `admin`，默认密码为 `admin`，双因素身份验证留空，点击`登录`按钮。您现在可以愉快地使用
ArmKVM 提供的各项功能了，Enjoy it!

# 基本使用

## 远程桌面 (KVM)

## 镜像挂载 (MSD)

## ATX 电源管理 (ATX Power Control)

## 网页终端 (WebTTY)

## 远程串口 (SoL)

# 进阶使用

## 无线网络配置

## 端口转发

### 自动

### 手动

## 内网穿透

## 虚拟局域网 (VPN)

# 常见问题

## 版本与规格

## 外设支持列表

## 产品特性

## 产品优势

## 产品应用场景

## 产品规格

## 产品外观

## 产品接口

## 产品包装

## 产品配件

## 产品安装

## 产品使用

## 产品维护

## 产品升级

## 产品故障排除

## 产品常见问题

## 产品技术支持

## 产品保修

## 产品销售渠道

## 产品售后服务

## 产品质量保证

## 产品认证

## 产品环境保护

## 产品安全保护

## 产品知识产权

## 产品免责声明

## 产品法律声明

## 产品版权声明

## 产品商标声明

## 产品著作权声明

## 产品专利声明

## 产品其他声明

## 产品致谢

## 产品参考文献

## 产品附录

## 产品历史版本

## 产品更新日志

## 产品开发日志

## 产品开发计划

## 产品开发进度

## 产品开发任务

## 产品开发人员

## 产品开发团队

## 产品开发机构

## 产品开发公司

## 产品开发组织
