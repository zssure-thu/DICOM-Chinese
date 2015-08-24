<h1><font face="Microsoft YaHei" color=blue>通告与免责声明</font></h1>
关于本出版物所含内容的专业可靠性，所有设计和审批该文档的参与者已达成共识，但这并不意味着全体参与者一致通过而毫无异议。<br>
本文档属于美国电气制造商协会(NEMA,National Electrical Manufactures Association)标准指南类出版物，遵循“自愿协商一致性”的标准流程。该流程汇集志愿者并找出对出版物某项议题感兴趣的人。NEMA监督整个流程并制定规则以促进达成共识的公平性，但NEMA并不编写文档，不进行独立测试、评估或验证任何信息的准确性和完整性、以及任何判断的可靠性。<br>
对于间接或直接使用该文档所产生的任何人身伤害、财产损失、或其他任何自然的、特殊的、间接性、连带性、补偿性的伤害，NEMA不承担任何责任。NEMA声明对于文档中的内容以及该内容是否能够满足读者特定目的或需求不做任何明确或暗示的担保和保证，另外NEMA不保证任何制造商或销售商的产品或服务遵循该标准<br>
....<br>
....<br>
....<br>

<h1><font face="Microsoft YaHei" color=blue>前言</font></h1>
DICOM标准由DICOM标准委员会制定。<br>
根据ISO/IEC Directives第三部分指导，DICOM标准文档被分成多个部分。<br>
<h1><font face="Microsoft YaHei" color=blue>1 应用范围与领域</font></h1>
该文档PS 3部分中介绍的通信协议<u>严格遵循</u>ISO国际化标准组织规定的开放系统互联参考模型（Open Systems Interconnection Basic Reference Model，参见ISO 7498-1 图1-1）。主要涉及的相关层有：物理层、数据链路层、网络层、传输层、会话层、表示层和应用层中的关联控制服务（ACSE，Association Control Services）。本文档中的通信协议符合TCP/IP通用标准，而并不只针对于本标准。应用层协议的其他方面放到本标准的其他部分（PS3.1)来讨论。<br>
<center>![Figure 1-1 ISO OSI Basic Reference Model](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_1-1.jpg)</center><br>
<center>Figure 1-1 ISO OSI Basic Reference Model</center><br>

----------

<h1><font face="Microsoft YaHei" color=blue>6 网络通信支持环境</font></h1>
本文档PS3.8中规定的网络通信服务，是支持DICOM应用实体通信的一套基础服务，是OSI表示层（ISO 8822)和OSI关联控制服务ACSE（ISO 8649)的子集，被称为上层服务或UL服务（即，the Upper Layer Service or UL Service）。关于DICOM UL服务详细内容在第7章节介绍。<br>
上层服务（UL Service）由第9章节中的TCP/IP顶层协议提供。<br>
图6-1展示了支持DICOM应用实体通信的TCP/IP协议栈。<br>
<center>![Figure 6-1](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_6-1.jpg)</center><br>
<center>Figure 6-1. DICOM Network Protocol Architecture</center><br>
<h1><font face="Microsoft YaHei" color=blue>7 DICOM应用实体的OSI上层服务</font></h1>
该章节将介绍如何使用OSI关联控制服务元(ACSE)和表示层构建上层服务为DICOM应用实体间的通信提供必要的支持。该上层服务完全遵循关联控制服务元以及OSI表示层规范。<br>
上层服务内容列于表7-1，如下所示：<br>
<center>Table 7-1 Upper Layer Services</center><br>
<center>![Table 7-1](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_Table7-1.jpg)</center><br>
除了介绍上层服务规范，本章节给出了DICOM应用实体使用上层服务各元素时的参数定义。关于上层服务的使用指南在标准第7部分有介绍（参见[PS3.7](http://dicom.nema.org/medical/dicom/current/output/html/part07.html#PS3.7))。<br>
<h2><font face="Microsoft YaHei" color=green>7.1 A-ASSOCIATE连接服务</font></h2>
两个DICOM应用实体间连接的建立需要通过关联控制服务元的请求、指示、响应、确认四种原语来完成。下文中将服务的发起者称之为请求方，将接收A-ASSOCIATE指示的使用者称之为接收方。该连接服务是一种确认服务。<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>A-ASSOCIATE连接服务相当于通过点对点接口创建一个信道(详情可参见已弃用的标准第九部分PS3.9）<b></b></font><br>
图7-1描述了两个DICOM应用实体间连接的建立。<br>
<center>![Figure 7-1](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_7-1.jpg)</center><br>
<center>Figure 7-1 Associate Request</center><br>
<h3><font face="Microsoft YaHei" color=purple>7.1.1 A-ASSOCIATE参数</font></h3>

