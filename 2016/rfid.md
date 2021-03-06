---
layout: default
---

# RRID
2016.06.14

### RRID分类
RFID (Radio Frequency Identification) (也称作标签) 指无线数据传输的微芯片，它们通常被附着在需要认证的实体上。在实际的RFID应用系统中，通常包括阅读器(reader/transceiver)、应答器 (tag/transponder) 和后端数据库 (back-end database) 三部分。阅读器由天线、芯片等组成，可以从RFIDs读取或写入信息；应答器包括天线、芯片等部件，一般来说都是用RFID作为应答器芯片；而后端数据库主要用于存储信息，提供RFIDs的初始化以及使用过程的一些通信需求。通信流程如下：阅读器发送信号给应答器，应答器收到信号后给出相应的响应。
根据RFID芯片处理器主频，一般可以分为如下几类。<br>

|       主频                             |   阅读器与应答器距离   |   读数据速率   |   应用场景                               |
|   -----------------                    |  ------------------   |  ------------  |  -----------------                      |
|30 – 300K低频 (LF)<br>常见125K, 134K    |        10cm内         |       低       |  智能卡访问权限识别 <br>生理数据收集等　　|
|3 – 30M高频 (HF)<br>常见13.56M　　　       |     10cm – 1m         |       中       |       无线支付等                         |
|300M – 3G 超高频 (UHF)<br>常见860 - 960M|      1 - 12m          |       高       |       检查防护应用<br>智能交通等          |


根据应答器能耗的供应主体，一般包括主动应答器 (Active RFID)、被动应答器 (Passive RFID)以及电池协助被动应答器 (Battery-Assisted Passive)三类。主动应答器通过电池供应运行；被动应答器通过阅读器的电磁波驱动运行；电池协助被动应答器通过电池启动，后续依靠阅读器的电磁波运行，主动应答器比被动应答器成本高很多。<br>

### RFID上整个安全机制的性能评价

<i>大多的需求都是针对整个RFID系统的安全体制，并没有直接介绍具体RFID上对密码算法的软硬件需求，只能根据相关参数做估计。这部分内容主要来自《Networked RFID Systems and Lightweight Cryptography》这本书的第8章——An Evaluation Framework[1]，不足的是这本书是2008年的，不是很新。</i><br><br>
    RFID上安全机制的性能主要包括以下4点：1) 硬件实现成本(Tag Implementation Cost)，2) 后台资源需求及管理费用(Backend Resources and Overhead Costs)，3) 能耗(Power Consumption)，4) 软件性能(Performance)。其中第1) 3) 4)点与具体的密码算法有关系，第二点更多的是与整个安全机制有关。<br>

* 硬件实现成本一般指设备制造所需要的硅元素的面积，通常在物理上直接实现所需的成本高而且实现过程复杂，因此可以通过在FPGA(Field Programmable Gate Array) 上实现来评估密码算法实现所需的逻辑门数量，进而估计密码算法的硬件实现成本。通常一个低频的RFID只集成了7K-15K的逻辑门，其中大约有2K-5K用于保证数据通信的安全。

* 实际的RFID系统中都包括后台数据库，主要用来保存一些秘密信息如密钥等，这就要求RFID能够实时访问后台数据库，这些会带来数据库以及网络通信的成本。管理费用主要表现在RFIDs的初始化以及使用过程中的一些其它操作。

* 能耗直接关系到RFIDs的使用寿命，要求能耗不超过10微瓦特。

* 需要实时交互的系统要求能在5-10毫秒内响应；根据C1G2协议的描述，从应答器到阅读器的最大数据传输速率是640kbps，从阅读器到应答器的最大数据传输速率是126kbps。


[1] P.H. Cole, D.C. Ranasinghe, Networked RFID Systems and Lightweight Cryptography, Chapter 8: An Evaluation Framework, Springer Berlin Heidelberg 2008, page 157-161,  URL [http://link.springer.com/book/10.1007%2F978-3-540-71641-9]
