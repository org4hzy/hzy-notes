## just remember! 
* 基于讨论理解 https://github.com/jawil/blog/issues/14

![TCP报头字段](https://github.com/org4hzy/hzy-notes/blob/master/pic/tcp字段.jpg)

## TCP三次握手
![TCP三次握手](https://github.com/org4hzy/hzy-notes/blob/master/pic/tcp三次握手.png)

### 言简意赅说一下:
1. client连server,发送SYN-SEND报文。内容 SYN=1, seq=x.
2. server回client,发送SYN-RECV报文。内容 ACK=1,SYN=1,seq=y,ack=x+1.
3. client回server,发送ESTABLISHED报文。内容 ACK=1,seq=x+1,ack=y+1. 双方都置为established状态。

* 理解
三次握手的本质: 信道不可靠，内容要可靠。在不可靠的信道上可靠的传输信息，就必须三次握手(当然也可以握手更多次 :-) )。
也就是说，client发起SYN报文后， client和server都必须至少回复一次准确的(基于上次报文校验)答复的报文
(这样建立的连接才是双方都可靠的，能听懂对方逻辑的)。

* 字段含义
seq - Sequence Number (32bit) 发送序列号 
ack - Acknowledgment Number(32bit) 确认序列号
ACK - 标记位 应答域 1有效 0无效 [[ TCP协议规定，只有ACK=1时有效，也规定连接建立后所有发送的报文的ACK必须为1 ]]
SYN - 标记位 同步序号 synchronization


## TCP四次挥手
![TCP四次挥手](https://github.com/org4hzy/hzy-notes/blob/master/pic/tcp四次挥手.jpg)

### 过程
1. A发B, FIN_WAIT_1报文，内容 FIN=1,seq=u.
2. B回A, ClOSE_WAIT报文，内容 ACK=1,seq=v,ack=u+1. A到FIN_WAIT_2状态
3. B再回A, LAST_ACK报文，内容 FIN=1,ACK=1,seq=w,ack=u+1.
4. A回B, CLOSED报文，内容 ACK=1,seq=u+1,ack=w+1. 双方都closed状态

* 理解(说三次！)
四次挥手的本质: 要等双方都把话说完，才分手！
也就是说，A说准备closed，B先说收到(立即答复对方，礼貌)，B把话说完(packet可能有多个包，继续发完)。
B最后说准备closed，A立即回复收到(tcp报文是可靠传输，若B说的话有问题，则应该等待B重传,所以A要回复一声)。

* 字段含义
FIN - 标记位 finish FIN =1 表明此报文段的发送方的数据已经发送完毕，并要求释放连接。


