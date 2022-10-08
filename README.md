# Erha-miner
使用二哈矿工构建加密隧道实现安全挖矿  
  
erha-miner安全隧道使用的是 http+tls 的协议，目的是伪装成普通的网页流量访问，让流量特征监控失效。  
1，支持构建ETH/ETC/BTC/LTC/CFX/ERGO/RVN/KASPA矿池的加密隧道中转。  
2，调整加密难度增强混淆系数。  
3，分布式防掉线客户端自动更换节点。  
4，支持国内外常用安全矿池。  
5，长期支持版本，放心免费使用。  
6，支持win/os版本,下载客户端一键启动中转。  
7，支持更多币种，让你无缝切换。  
8，支持币种双挖，多挖。
9，低至千分三的Gas费率。

下载连接：https://github.com/erha-miner/tool/releases/tag/5.0.6  

官网现已启动新域名：https://www.erha-miner.com    

后期更新请关注官网域名，更新时效更快更准
    
免责协议：请您务必在当地法律法规允许的前提下进行    

stratum协议是目前最常用的矿机和矿池之间的TCP通讯协议，只有在挖矿场景才会用到。  

常用的是有stratum+tcp和stratum+SSL两种，有些朋友以为用了stratum+SSL就是安全的，无法监测得到，这种想法是错误的。   

stratum+tcp和stratum+SSL只是内容数据包有没有加密的区别，但是用了SSL只是数据明文变成了加密数据，其外部特征不变的，且该协议特征明显，只有挖矿才会用到，所以经过大量数据训练，通过机器学习，该协议非常容易就能够被识别。  

举个例子，就像一辆汽车，TCP就是没有拉上窗帘，外面的人一眼就可以看到车里面的人，SSL就像拉上了窗帘，外面的人是看不到车里的人，但是还是可以一眼就看得出这是一辆汽车，而且这种车型，只有挖矿的数据才会乘坐。  

二哈矿工加密隧道介绍：  
二哈矿工安全隧道使用的是 http+tls 的协议，目的是伪装成普通的网页流量访问，让流量特征监控失效。

![image](https://github.com/erha-miner/tool/blob/main/erha-miner.png)

  
官网在这里  https://github.com/erha-miner/tool  
最新版下载在这里 https://github.com/erha-miner/tool/releases/tag/5.0.0  


使用方法（windows系统）：  

解压erha-miner.zip，右击编辑start.bat脚本，配置好本地端口和矿池IP  
脚本例子：erha-miner.exe -L=6666 -P=asia2.ethermine.org:5555  
参数含义：  
-L ： 本地端口，默认为6666  
-P :   挖矿地址，目前支持E池,鱼池,币印,凤池,欧易,币安,蚂蚁,hive 池,2miners,独角兽,ezil ,支持SSL方式，格式：域名+端口  
  
配置好bat文件之后，双击运行，保留窗口开启  
按文件夹里面配置好开启自动启动  

![image](https://github.com/erha-miner/tool/blob/main/1.png)


2、挖矿脚本调整：  

挖矿脚本需要调整为执行本地/局域网IP+本地端口进行加密隧道中转，本质来说就是替换原本矿池Ip，指向到本地加密去特征码后转发，达到安全的环境（因为走的是本地内网，只需要配置为TCP模式即可）  

NBminer:  
nbminer.exe -a ethash -o stratum+tcp://127.0.0.1:6666 -u YOUR_WALLET_ADDRESS.RIG_ID  

轻松矿工：新增矿池即可  
![image](https://github.com/erha-miner/tool/blob/main/3.png)


局域网内其他矿机加密隧道设置：
如果你有多台矿机，或者Hiveos等系统，
可以在其中一台windows矿机上运行并记录下该台机器的内网IP如192.168.1.88，
其他矿机挖矿地址填写 192.168.1.88:6666 即可统一通过隧道加密流量出去

仅供学习，请勿用于非法用途  

如果你的矿池暂时还没支持，可以去Github提交issue，我们会尽快加上  
或者联系telegram:https://t.me/+hyrPYOuIfv5iZDFh


win10系统如何设置开机自启动  
1，打开文件夹，输入C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp  
2，把bat脚本生成快捷方式，然后拉到这个启动目录下面（需要管理员权限）  


# linux / os 使用方法：  
进入os的ssh面板输入  
下载文件：  
wget https://raw.githubusercontent.com/erha-miner/tool/main/erha-miner-os  

更改执行权限：  
chmod 777 erha-miner-os  
  
启动二哈加密隧道(对应矿池脚本，参数为-L为挖矿端口，-P是对应官网矿池地址)：  
./erha-miner-os -L=6666 -P=asia-eth.2miners.com:12020   
  
后台启动方式(注意结尾&)：  
nohup ./erha-miner-os -L=6666 -P=asia-eth.2miners.com:12020 &   
  
重启应用（或者更换矿池）：   
找到进程：  
ps -fe|grep erha-miner-os     
（结果例如：root     2106547 2093677  0 09:12 pts/0    00:00:00 grep --color=auto erha-miner-os ）  
终结进程（对应上面结果的进程号）：  
 kill -9 2106547    
重新启动上面erha-miner-os脚本即可  
  
os的开机启动：  
  
1.编辑rc.local文件  
[root@localhost ~]# vi /etc/rc.local  
  
2.修改rc.local文件，在 exit 0 前面加入以下命令。保存并退出。  
nohup ./erha-miner-os -L=6666 -P=asia-eth.2miners.com:12020 &
   
os局域网内也是可以互通使用，注意检查防火墙的开启和关闭。  

  


