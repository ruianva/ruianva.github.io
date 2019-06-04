# 概述

关于it办公自动化：
- 以整个学校效率出发改进，`个人`效率服从`团队`效率；
- 通过it手段简化传统`行政合规`的各种必须但又繁琐的环节；



# 远程服务

确保在一个LAN上，对于windows 10家庭版https://blog.csdn.net/BaoBeiDeXiaoDaiGua/article/details/79314700；





# 共享FTP

使用方法：启动文件浏览器，键入`ftp://ruianva@192.168.1.147`，密码同`ruianva`的wifi密码，可问`shangrong`;

![1557197020326](media/1557197020326.png)

- 服务端
  - 安装filezilla server；
  - 设置被动模式；
  - 防火墙开`入端口`：21,60000-60020
  - 创建目录以及相应用户

![1557044482848](./media/1557044482848.png)



# 扫描

扫描



# 打印机

请`勿插拔`离203门口最近的两台打印机：

1. 若你使用203门口的公用电脑，那么你可以直接使用其连接这两台打印机； 

2. 若你使用个人电脑打印，请直接连接203wifi后，无线接入 公用共享打印机；

   使用方法：启动文件浏览器，键入`\\192.168.1.147 `(若提示要求输入账号，输入登陆账号lenovo，密码20171220。)

   双击你要使用的打印机，安装后就可以使用该打印机。

![share](./media/shareprint.gif)



Q&A 弹出

解决方法：
１、运行 服务，`services.msc`打开服务窗口；
２、开启以下三个服务；
       Computer Browser
       Server
      Workstation

３、关闭防火墙：关闭"Windows Firewall"服务；



## 设置共享打印机

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



### 提示驱动更新

通常是由于客户机为32bit os导致，设置打印机服务器增加32 bit驱动即可。



### 删除默认登陆密码

以前用A身份访问工作组里一台服务器(保存了用户名和密码)，现在想用身份B登录那台服务器。怎么才能使A身份实效呢?我用 net use * /d /y和net session 計算機名 /delete提示操作成功，但是仍然可以连接，不起作用。
　　回答：
　　根据我的研究，您可以通过以下方法清空计算机上存储的用户名和密码，具体的操作步骤如下：1. 单击“开始”，单击“运行”，键入“control userpasswords2”或　输入“control keymgr.dll”，然后按 Enter. 2. 单击“高级”选项卡，然后单击“管理密码”。
  　　3. 移除所有存储的密码。
       “存储用户名和密码”的行为根据我的测试，无论是移除所有存储的密码，还是使用net use * /d删除所有的已有连接，都需要重新启动计算机才会在访问该共享文件夹的时候，重新出现输入用户名和密码的提示。如果您不希望重启计算机的话，可以重启“workstation”服务来进行测试。



## 203-1.CANON MF4712

- 有如下故障：双页打印过程
- 使用废纸：正面朝下

- 换墨盒流程：
  - ![1558669519450](media/1558669519450.png)
  - 

- 卡纸处理：

## 203-2.DocuCentre S2110

下载：`施乐复印机s2011驱动程序.exe` DocuCentre S2110 UG_SC.pdf

登陆按4s->输入5个1->启动->输入202->启动两次

- 设置固定IP 

  - 192.168.1.148 端口：9100

  3117

![1557042675731](media/1557042675731.png)

![1555508474834](media/1555508474834.png)

  ![1555508498382](media/1555508498382.png)

  ![1555508527186](media/1555508527186.png)

  ![1555508552694](media/1555508552694.png)

## 203-3.CANON imageClassLBP161



- EPSON L6168
  - 位置、网络

  

- 扫描机

  - EPSON: [对于非装订，自动双面扫描](https://detail.tmall.com/item.htm?spm=a230r.1.14.22.3a362a4fcQQ6rf&id=39982630894&ns=1&abbucket=5&skuId=3654013253560)
  - CZUR成者科技：[装订书](https://detail.tmall.com/item.htm?spm=a230r.1.14.6.f57c5bb8qvvuAw&id=574849632380&cm_id=140105335569ed55e27b&abbucket=5)

