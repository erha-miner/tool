# Erha-miner
使用二哈矿工构建加密隧道实现安全挖矿  

stratum协议是目前最常用的矿机和矿池之间的TCP通讯协议，只有在挖矿场景才会用到。  

常用的是有stratum+tcp和stratum+SSL两种，有些朋友以为用了stratum+SSL就是安全的，无法监测得到，这种想法是错误的。   

stratum+tcp和stratum+SSL只是内容数据包有没有加密的区别，但是用了SSL只是数据明文变成了加密数据，其外部特征不变的，且该协议特征明显，只有挖矿才会用到，所以经过大量数据训练，通过机器学习，该协议非常容易就能够被识别。  

举个例子，就像一辆汽车，TCP就是没有拉上窗帘，外面的人一眼就可以看到车里面的人，SSL就像拉上了窗帘，外面的人是看不到车里的人，但是还是可以一眼就看得出这是一辆汽车，而且这种车型，只有挖矿的数据才会乘坐。  

二哈矿工加密隧道介绍：  
二哈矿工安全隧道使用的是 http+tls 的协议，目的是伪装成普通的网页流量访问，让流量特征监控失效。

![image](https://github.com/erha-miner/tool/blob/main/erha-miner.png)

  
官网在这里  https://github.com/erha-miner/tool  
最新版下载在这里 https://github.com/erha-miner/tool/releases


本工具收取极少Gas费用为0.1%,用于维护和升级，这个费用并不多，1000块钱每天就费用只有1块钱，大部分每天只需要支出几毛钱就可以使用到绝对安全的隧道加密通道，开发不容易，请多理解  

免责协议：请您务必在当地法律法规允许的前提下进行  

使用方法（windows系统）：  

解压erha-miner.zip，右击start.bat脚本，配置好本地端口和矿池IP  
脚本例子：erha-miner.exe -L=6666 -P=asia2.ethermine.org:5555  
参数含义：  
-L ： 本地端口，默认为6666  
-P :   挖矿地址，目前支持E池,鱼池,币印,凤池,欧易,币安,蚂蚁,hive 池,2miners,独角兽,ezil ,支持SSL方式，格式：域名+端口  
  
配置好bat文件之后，双击运行，保留窗口开启  


2、挖矿脚本调整：  

挖矿脚本需要调整为执行本地/局域网IP+本地端口进行加密隧道中转，本质来说就是替换原本矿池Ip，指向到本地加密去特征码后转发，达到安全的环境（因为走的是本地内网，只需要配置为TCP模式即可）  

lolMiner:  
lolMiner.exe --algo ETHASH --pool 127.0.0.1:6666 --user YOUR_WALLET_ADDRESS.RIG_ID  

Gminer:  
miner.exe --algo ethash --server 127.0.0.1:6666 --user YOUR_WALLET_ADDRESS.RIG_ID  

T-Rex:  
t-rex.exe -a ethash -o stratum+tcp://127.0.0.1:6666 -u YOUR_WALLET_ADDRESS -w RIG_ID -p x  

Red Miner:  
teamredminer.exe -a ethash -o stratum+tcp://127.0.0.1:6666 -u YOUR_WALLET_ADDRESS.RIG_ID -p x  

NBminer:  
nbminer.exe -a ethash -o stratum+tcp://127.0.0.1:6666 -u YOUR_WALLET_ADDRESS.RIG_ID  

Bminer:  
bminer.exe -uri ethproxy://YOUR_WALLET_ADDRESS.RIG_ID@127.0.0.1:6666  

轻松矿工：新增矿池即可  





