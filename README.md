# 科学上网：VPS 搭建 X-ui 面板，用 DNS 申请 SSL 证书

## 使用 X-ui 搭建代理服务，具有以下优点：

- 支持系统状态监控：如 CPU、内存、硬盘等状态
- 支持多用户多协议，网页可视化操作
- 支持流量统计
- 支持自定义 Xray 配置模板
- 支持HTTPS访问面板
- 支持面板自定义端口，账号与密码
- 快速生成分享连接或二维码
- 支持 CDN 套用
- 支持 Fallback 分流设置

### 与本期视频相关教程

本期合作 VPS 六六云：https://bit.ly/3hBENuF

域名注册教程：https://youtu.be/2uJQdWpM46k

Cloudflare 接管域名教程：https://youtu.be/1GtDTWybJNM

X-ui 搭建教程一：https://youtu.be/n5koU-pj094

## 准备工作

- 1、域名一个，托管到 Cloudflare （方法见上）

- 2、VPS 一台，例如：Debian/Ubuntu/CentOS

- 3、下载并安装 FinalShell SSH 工具

Windows 版本下载地址:
http://www.hostbuf.com/downloads/finalshell_install.exe

MacOS 版本下载地址:
http://www.hostbuf.com/downloads/finalshell_install.pkg

 

## 更新安装系统
下面环境的安装方式，大家根据自己的系统选择命令安装就好了。
### 1、Debian/Ubuntu 系统执行以下命令：
    apt update -y         
    apt install -y curl    
    apt install -y socat    
    
### 2、CentOS 系统执行以下命令：   

    yum update -y         
    yum install -y curl   
    yum install -y socat   

 ## 安装 BBR 加速
 本脚本建议在Debian≥9或是CentOS≥8以上的系统中使用
 
    wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
    
    安装过后先选2，重启后选7
 
 ## 一键安装面板
    bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
 
 完成 X-ui 安装以后，我们可以输入 VPSIP:端口（如1.1.1.1:12345） 登录 X-ui 的管理面板（可以登录代表安装成功）

## 利用 DNS 申请证书

在 VPS 输入<code> x-ui</code>  命令，进入 X-ui 的命令菜单
选择 16，申请 SSL 的证书。（申请需要有 Cloudflare API ，可以 观看视频 获取 API）

申请的时候是申请的泛域名证书，所以，填写域名的时候，只填入 域 也就好了，例如<code>  xxx.com</code>  的格式。

申请成功以后，证书和密钥文件在 VPS 目录的<code> /root/cert </code>文件夹里面

##  访问并设置 Xray 管理面板
在浏览器中输入刚才解析的域名 cs.kjxlu1.top ，用户名 admin ，密码 admin

修改必要的面板参数 SSL证书以及密钥（绝对地址）、面板端口、登录标题 等，其他若是你不清楚，请保持默认

-  重要：若是设置了 SSL证书以及密钥 ，再次登录需要输入 https://cs.kjxlu1.top:54321 访问，注意，是 https
 
 ## 添加科学上网节点
 这一步扩展性很强，大家可以根据自己的需求设置相关的节点规则。

## 关于x-ui节点电脑V2ray能连接上，扫描导入手机V2rayNG连接不了？
在 X-ui面板设置中，“面板证书公钥文件路径”，不要用带自己域名的证书，输入<code> /root/cert/fullchain.cer</code> （这是标准的CA证书集的文件之一）的路径。然后重启面板。在创建的节点时候，公钥文件路径同样填入 <code> /root/cert/fullchain.cer</code> 。
这样设置之后，解决了问题： io read/write on closed pipe

 ----------------
这种 Xray 可视化管理面板 的方式，也是支持伪装网站以及多网站并存的，包括支持宝塔面板的搭建方式。


https://www.youtube.com/watch?v=AHnoF5FyFy8&list=LL&index=21&t=1132s  视频教程

修改必要的面板参数 SSL证书以及密钥（绝对地址）、面板端口、登录标题 等，其他若是你不清楚，请保持默认教程
修改必要的面板参数 SSL证书以及密钥（绝对地址）、面板端口、登录标题 等，其他若是你不清楚，请保持默认
