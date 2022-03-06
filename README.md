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



