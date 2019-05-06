# 概述

对于当前`办公室`需要手工处理的`报销`、`打印`；

- 以整个学校效率出发改进，`个人`的效率服从`团队`效率，中代价高昂的；
- 在符合`行政`的基础上的制定虽高但却是简化的；





# 审批

PC客户端：





# 打印机

通过一台公共主机147接入的方式：

怎么设置呢

无线接入：



## 通过共享打印机

- 打印机服务端（203门口台式机）

WIN10 ：WIN->打印机 ->管理->打印机属性

- 安装`组策略`

  ```BAT
  @echo off
  pushd "%~dp0"
  dir /b C:\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >List.txt
  dir /b C:\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>List.txt
  for /f %%i in ('findstr /i . List.txt 2^>nul') do dism /online /norestart /add-package:"C:\Windows\servicing\Packages\%%i"
  pause
  ```

- 开启GUEST用户

  ![1556596498861](media/1556596498861.png)

- 配置策略组

![1556596115963](media/1556596115963.png)

在右侧策略处找到`账户:使用空白密码的本地账户只允许进行控制台登录`，此策略默认是已启用；双击打开“账户:使用空白密码的本地账户只允许进行控制台登录”，将其改为“已禁用”



- 设置打印机为共享





## CANON MF4712

- 有如下故障：双页打印过程
- 使用废纸：正面朝下



## 共享FTP

ftp://ruianva@192.168.1.147

- 服务端防火墙开端口
- 服务端设置port实用被动模式

![1557044482848](media/1557044482848.png)

## DocuCentre S2110

下载：`施乐复印机s2011驱动程序.exe` DocuCentre S2110 UG_SC.pdf

登陆按4s->输入5个1->启动->输入202

- 设置固定IP 

  - 192.168.1.148 端口：9100

  3117

![1557042675731](media/1557042675731.png)

![1555508474834](media/1555508474834.png)

  ![1555508498382](media/1555508498382.png)

  ![1555508527186](media/1555508527186.png)

  ![1555508552694](media/1555508552694.png)

  

  

- CANON imageClassLBP161



- EPSON L6168
  - 位置、网络

  

- 扫描机

  - EPSON: [对于非装订，自动双面扫描](https://detail.tmall.com/item.htm?spm=a230r.1.14.22.3a362a4fcQQ6rf&id=39982630894&ns=1&abbucket=5&skuId=3654013253560)
  - CZUR成者科技：[装订书](https://detail.tmall.com/item.htm?spm=a230r.1.14.6.f57c5bb8qvvuAw&id=574849632380&cm_id=140105335569ed55e27b&abbucket=5)

