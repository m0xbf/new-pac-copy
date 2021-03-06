**2019年12月7日发布。**

***

Trojan模仿了互联网上最常见的 HTTPS 协议，以诱骗GFW封锁认为它就是 HTTPS，从而不被识别。Trojan处理来自外界的 HTTPS 请求，如果是合法的，那么为该请求提供服务，否则将该流量转交给 web 服务器 Nginx，由 Nginx 为其提供服务。基于这个工作过程可以知道，Trojan的一切表现均与 Nginx 一致，不会引入额外特征，从而达到无法识别的效果。

**整个教程分四步**：

第一步：购买VPS服务器

第二步：购买域名

第三步：一键搭建服务器

第四步：一键加速VPS服务器 


***

**第一步：购买VPS服务器**

VPS服务器需要选择国外的，首选国际知名的vultr，速度不错、稳定且性价比高，按小时计费，能够随时开通和删除服务器，新服务器即是新ip。

vultr注册地址： https://www.vultr.com/?ref=7777564-4F （vultr2019年1月的活动，新用户赠送50美元，有效期1个月。全球15个服务器位置可选，kvm框架。如果以后这个vultr注册地址被墙了，那么就用翻墙软件打开，或者用[ss/ssr免费账号](https://github.com/Alvin9999/new-pac/wiki/ss%E5%85%8D%E8%B4%B9%E8%B4%A6%E5%8F%B7)） 

<a href="https://www.vultr.com/?ref=7777564-4F"><img src="https://www.vultr.com/media/banner_2.png" width="468" height="60"></a>

虽然是英文界面，但是现在的浏览器都有网页翻译功能，鼠标点击右键，选择网页翻译即可翻译成中文。

注册并邮件激活账号，充值后即可购买服务器。充值方式是支付宝或paypal，使用paypal有银行卡（包括信用卡）即可。paypal注册地址：https://www.paypal.com （paypal是国际知名的第三方支付服务商，注册一下账号，绑定银行卡即可购买国外商品）

2.5美元/月的服务器配置信息：单核   512M内存  20G SSD硬盘   带宽峰值100M    500G流量/月   (**不推荐，仅提供ipv6 ip，不推荐**)

3.5美元/月的服务器配置信息：单核   512M内存  20G SSD硬盘   带宽峰值100M    500G流量/月   (**推荐**)

5美元/月的服务器配置信息：  单核   1G内存    25G SSD硬盘   带宽峰值100M    1000G流量/月  (**推荐**)
 
10美元/月的服务器配置信息： 单核   2G内存    40G SSD硬盘   带宽峰值100M    2000G流量/月  

20美元/月的服务器配置信息： 2cpu   4G内存   60G SSD硬盘    带宽峰值100M    3000G流量/月  

40美元/月的服务器配置信息： 4cpu   8G内存   100G SSD硬盘   带宽峰值100M    4000G流量/月  

**注意：2.5美元套餐只提供ipv6 ip，一般的电脑用不了，所以建议选择3.5美元及以上的套餐。另外，并非所有地区都有3.5美元的套餐，需要自己去看。由于资源的短缺，有的地区有时候有3.5美元的套餐，有时候没有。**

**vultr实际上是折算成小时来计费的，比如服务器是5美元1个月，那么每小时收费为5/30/24=0.0069美元 会自动从账号中扣费，只要保证账号有钱即可。如果你部署的服务器实测后速度不理想，你可以把它删掉（destroy），重新换个地区的服务器来部署，方便且实用。因为新的服务器就是新的ip，所以当ip被墙时这个方法很有用。当ip被墙时，为了保证新开的服务器ip和原先的ip不一样，先开新服务器，开好后再删除旧服务器即可。**


计费从你开通服务器开始算的，不管你有没有使用，即使服务器处于关机状态仍然会计费，如果你没有开通服务器就不算。比如你今天早上开通了服务器，但你有事情，晚上才部署，那么这段时间是会计费的。同理，如果你早上删掉服务器，第二天才开通新的服务器，那么这段时间是不会计费的。在账号的Billing选项里可以看到账户余额。

温馨提醒：同样的服务器位置，不同的宽带类型和地区所搭建的账号的翻墙速度会不同，这与中国电信、中国联通、中国移动国际出口带宽和线路不同有关，所以以实测为准。可以先选定一个服务器位置来按照教程进行搭建，熟悉搭建方法，当账号搭建完成并进行了bbr加速后，测试下速度自己是否满意，如果满意那就用这个服务器位置的服务器。如果速度不太满意，就一次性开几台不同的服务器位置的服务器，然后按照同样的方法来进行搭建并测试，选择最优的，之后把其它的服务器删掉，按小时计费测试成本可以忽略。

**账号充值如图**：

![](https://raw.githubusercontent.com/Alvin9999/pac2/master/pp100.png)

![](https://raw.githubusercontent.com/Alvin9999/pac2/master/pp101.png)


**开通服务器步骤如图**：

![](https://raw.githubusercontent.com/Alvin9999/crp_up/master/pac教程01.png)

![](https://raw.githubusercontent.com/Alvin9999/crp_up/master/pac教程02.png)

![](https://raw.githubusercontent.com/Alvin9999/crp_up/master/pac教程04.png)


### trojan安装脚本仅支持Centos7或8。


**开通服务器时，当出现了ip，不要立马去ping或者用xshell去连接，再等5分钟之后，有个缓冲时间。完成购买后，找到系统的密码记下来，部署服务器时需要用到。vps系统的密码获取方法如下图：**

![](https://raw.githubusercontent.com/Alvin9999/crp_up/master/pac教程05.png)

![](https://raw.githubusercontent.com/Alvin9999/crp_up/master/pac教程06.png)

**删掉服务器步骤如下图**：

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/ss/de4.PNG)

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/ss/de2.PNG)

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/ss/de5.png)

一个被墙ip的vps被删掉后，其ip并不会消失，会随机分配给下一个在这个服务器位置新建服务器的人，这就是为什么开新服务器会有一定几率开到被墙的ip。被墙是指在国内地区无法ping通服务器，但在国外是可以ping通的，vultr是面向全球服务，如果这个被墙ip被国外的人开到了，它是可以被正常使用的，半年或1年后这个被墙的ip可能会被国内防火墙解封，那么这就是一个良性循环。

***


**第二步：购买域名**

有免费的域名，但为了稳定，建议选择付费的域名，因为免费的域名很可能会用不了多长时间。域名一般很便宜，1年几十人民币。推荐用国外的域名服务商：[Godaddy](https://www.godaddy.com/tlds/com-domain)、[Namecheap](https://www.namecheap.com)、[Gandi](https://www.gandi.net/zh-Hans)

购买域名后，登录域名网站管理页面，将自己的vps ip指向域名。

***

**第三步：一键搭建VPS服务器**

购买服务器后，需要部署一下。因为你买的是虚拟东西，而且又远在国外，我们需要一个叫Xshell的软件来远程部署。Xshell windows版下载地址：

[国外云盘下载](http://108.61.224.82/lib5/Xshell_setup_wm.exe) 


如果你是苹果电脑操作系统，更简单，无需下载xshell，系统可以直接连接VPS。打开**终端**（Terminal），输入ssh root@ip  其中“ip”替换成你VPS的ip, 按回车键，然后复制粘贴密码，按回车键即可登录。粘贴密码时有可能不显示密码，但不影响， [参考设置方法](http://www.cnblogs.com/ghj1976/archive/2013/04/19/3030159.html)  如果不能用MAC自带的终端连接的话，直接网上搜“MAC连接SSH的软件”，有很多，然后通过软件来连接vps服务器就行，具体操作方式参考windows xshell。

***

部署教程：

下载windows xshell软件并安装后，打开软件

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/xshell11.png)

选择文件，新建

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/xshell12.png)

随便取个名字，然后把你的服务器ip填上

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/xshell13.png)

连接国外ip即服务器时，软件会先后提醒你输入用户名和密码，用户名默认都是root，密码是你购买的服务器系统的密码。

### 如果xshell连不上服务器，没有弹出让你输入用户名和密码的输入框，表明你开到的ip是一个被墙的ip，遇到这种情况，重新开新的服务器，直到能用xshell连上为止，耐心点哦！如果同一个地区开了多台服务器还是不行的话，可以换其它地区。

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/xshell14.png)

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/ss/xshell2.png)

连接成功后，会出现如上图所示，之后就可以复制粘贴代码部署了。

一键安装trojan脚本代码（Centos7/Centos8）：

***

curl -O https://raw.githubusercontent.com/atrandys/trojan/master/trojan_centos7.sh && chmod +x trojan_centos7.sh && ./trojan_centos7.sh

***

复制上面整个代码到vps服务器中进行安装，安装过程中会提示输入域名，最终安装完成后，会展示一条下载地址，复制地址，并下载下来即可。解压缩下载的trojan-cli.zip的压缩包，进入文件夹，双击start.bat，开启Trojan服务，Trojan会监听本地1080端口。

浏览器代理设置成socks5，直接指向127.0.0.1：1080即可。

***

**第三步：一键加速VPS服务器**

**总共有2种加速方法，锐速加速和bbr加速，选择1种。**

**【加速教程1：破解版锐速加速教程】**

此加速教程为破解版锐速加速,Vultr的服务器centos6系统官方进行了更新，导致目前**不支持BBR的部署**，**但锐速应该是可以部署的**，故增加了此部署脚本，加速后对速度的提升很明显，所以推荐部署加速脚本。该加速方法是开机自动启动，部署一次就可以了。

**第一步，先更换服务器内核（脚本只支持centos系统，其它系统可以直接尝试第二步）**

yum -y install wget

wget --no-check-certificate https://blog.asuhu.com/sh/ruisu.sh && bash ruisu.sh

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/rs1.PNG)

不动的时候敲回车键，在上图时需要多等一会儿。

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/rs2.PNG)

出现上图时表示已成功替换内核并服务器自动重启。

**完成后会重启，2分钟后重新连接服务器，连上后开始第二步的操作。**

**第二步，一键安装锐速**

wget -N --no-check-certificate https://raw.githubusercontent.com/91yun/serverspeeder/master/serverspeeder-all.sh && bash serverspeeder-all.sh

卸载加速代码命令为：

chattr -i /serverspeeder/etc/apx* && /serverspeeder/bin/serverSpeeder.sh uninstall -f

但有些内核是不适合的，部署过程中需要手动选择推荐的，当部署时出现以下字样：

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/%E9%94%90%E9%80%9F2.PNG)

提示没有完全匹配的内核,随便选一个内核就行,按照提示来输入数字,按回车键即可

锐速安装成功标志如下：

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/%E9%94%90%E9%80%9F3.png)

出现running字样即可!


***

**【加速教程2：谷歌BBR加速教程】**

**vultr服务器的centos6不支持bbr加速，但centos7系统支持bbr加速，所以如果你想用bbr加速教程，vps操作系统需要选择centos7或其它系统。**

yum -y install wget

wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh

chmod +x bbr.sh

./bbr.sh

把上面整个代码复制后粘贴进去，不动的时候按回车，然后耐心等待，最后重启vps服务器即可。

演示开始，如图：

复制并粘贴代码后，按回车键确认

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/ss/18.png)

如下图提示，按任意键继续部署

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/ss/19.png)

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/ss/20.png)

部署到上图这个位置的时候，等待3～6分钟

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/ss/21.png)

最后输入y重启服务器，如果输入y提示command not found ，接着输入reboot来重启服务器，确保加速生效，bbr加速脚本是开机自动启动，装一次就可以了。

服务器重启成功并重新连接服务器后，输入命令lsmod | grep bbr  如果出现tcp_bbr字样表示bbr已安装并启动成功。如图：

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/demo/tcp_bbr.PNG)

**注意1**：根据反馈，少部分人安装bbr脚本并重启后，几分钟过去了，发现xshell无法连接服务器且服务器ip无法ping通。解决方法是：开新服务器或者重装系统，然后先安装bbr脚本再安装ssr脚本，或者改用锐速加速脚本。

重装系统方法，点击vultr服务器设置界面——“Server Reinstall”，如下图：

![](https://raw.githubusercontent.com/Alvin9999/PAC/master/demo/reinstall.png)

重装过程一般需要5～10分钟。

**注意2**：如果创建的是centos7的服务器，安装bbr加速后需要使用命令关闭防火墙，否则无法使用代理。CentOS 7.0默认使用的是firewall作为防火墙。

查看防火墙状态命令：firewall-cmd --state

停止firewall命令：systemctl stop firewalld.service

禁止firewall开机启动命令：systemctl disable firewalld.service 

***

**常见问题参考解决方法**：

1、Trojan客户端打开无法运行，提示缺少找不到vcruntime140.dll或找不到msvcp140.dll。

原因缺少运行库，点击[下载链接](https://www.microsoft.com/en-us/download/details.aspx?id=48145)中的两个软件，一个是32位一个是64位，请全部安装即可。

2、如果遇到vcruntime140_1的错误，下载下面的文件放到C:\windows\system32目录下即可

[点击下载140_1.dll](https://github.com/atrandys/trojan/raw/master/vcruntime140_1.dll)

