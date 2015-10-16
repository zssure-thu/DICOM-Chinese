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
<center>图1-1 ISO OSI Basic Reference Model</center><br>

----------
<h1><font face="Microsoft YaHei" color=blue>5 约定</font></h1>
下文中描述各项服务的表格中用到的约定如下：<br>
(=)<br>
指示（确认）使用的参数值与请求（响应）中的相同。<br>
C<br>
有条件的（用户可选的）<br>
M<br>
强制使用
MF<br>
强制使用确定数值<br>
NU<br>
未使用的<br>
P<br>
初始化t提供<br>
U<br>
用户可选的<br>
UF<br>
用户可选但数值固定<br>
<br>
空白项不适用上述约定。<br>





<h1><font face="Microsoft YaHei" color=blue>6 网络通信支持环境</font></h1>
本文档PS3.8中规定的网络通信服务，是支持DICOM应用实体通信的一套基础服务，是OSI表示层（ISO 8822)和OSI关联控制服务ACSE（ISO 8649)的子集，被称为上层服务或UL服务（即，the Upper Layer Service or UL Service）。关于DICOM UL服务详细内容在第7章节介绍。<br>
上层服务（UL Service）由第9章节中的TCP/IP顶层协议提供。<br>
图6-1展示了支持DICOM应用实体通信的TCP/IP协议栈。<br>
<center>![Figure 6-1](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_6-1.jpg)</center><br>
<center>图6-1. DICOM网络协议框架</center><br>
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
<center>图7-1 连接请求</center><br>
<b><font color=gray>译者注：</font></b>
><font color=gray>所谓服务原语，是代表响应服务的符号和参数的一种格式化、规范化的表示，它与服务的具体实现方式无关。原语都是发送给服务实体相邻层的，层与层之间的通信原语分为请求（Request）、指示（Indication）、响应（Response）、确认（Confirm）四种。</font><br><br>
><font color=gray>图7-1中的SAP，全称Service Accessing Point，即服务访问点。是上层访问下层所提供服务的点。在计算机体系结构中，下层是为相邻上层提供服务的，而下层对它的所有上层都是透明的。</font><br><br>
>在传统的点对点（或端到端）的模型中四种原语体现的不是很具体，其原因是点对点（或端到端）的模型将双方实体抽象成了一个点，而未考虑各自内部的OSI开放模型。如果将每个端点展开为OSI层模型，即可理解上述四种服务原语。<br>


<h3><font face="Microsoft YaHei" color=purple>7.1.1 A-ASSOCIATE参数</font></h3>
表7-2列出了DICOM应用实体使用A-ASSOCIATE服务时所需的各项参数。<br>
<center>Table 7-2 Key A-ASSOCIATE Service Parameters</center><br>
<center>![Table 7-2](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_Table7-2.jpg)</center><br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>关于表中的约定参见该部分第5章节。</font><br>
表7-3列出了DICOM应用实体在A-ASSOCIATE服务中的固定值参数或不需要的参数。<br>
<center>Table 7-3. A-ASSOCIATE Service Parameter (Fixed or Not Used)</center></br>
<center>![Table 7-3](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_Table7-3.jpg)</center></br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.1 模式（固定值）</font></h4>
该参数允许使用OSI-ACSE服务中的可选模式进行协商。在DICOM应用实体之间仅允许使用默认的“normal”（正常），因此该参数应始终被设定为“normal”。<br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.2 应用上下文名称</font></h4>
该参数定义了请求方建议的应用上下文名称。接收方可以返回相同或不同的应用上下文名称。返回的名称用于标定本次链接应用上下文。关于应用上下文名称的详细讨论请参见[附录A]()。<br>
应用上下文是一个定义明确的集合，包括应用服务元素、相关选项、以及应用实体间完成交互必须的其他信息。<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red><font color=yellow>接收方返回的应用上下文提供了限定协商的机制。</font>倘若请求方不能按照接收方提供的应用上下文进行操作，应当发布一个A-Abort（放弃）请求原语。在标准第7部分（PS3.7）中定义了DICOM应用实体应用上下文名称以及使用规则。</font><br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.3 呼叫方应用实体名称</font></h4>
该参数定义了包含A-ASSOCIATE链接服务请求方的应用实体，基于源DICOM应用名称。关于DICOM应用名称与应用实体名称之间的关系参见[附录C]()。呼叫方应用实体名称与在连接中传递的DICOM消息所含的发起方地址可能相同也可能不同。<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>接收到A-ASSOCIATE-RQ链接请求的上层用户负责验证呼叫方应用实体名称是否属于已知的远程DICOM应用名称。</font><br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.4 被叫方应用实体名称</font></h4>
该参数用于定义包含预期A-ASSOCIATE服务接收方的应用实体，基于目标DICOM应用名称。关于DICOM应用名称与应用实体名称之间的关系参见[附录C]()。被叫方应用实体名称与在连接中传递的DICOM消息所含的接收方地址可能相同也可能不同。<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>接收到A-ASSOCIATE-RQ链接请求的上层用户负责验证被叫方应用实体名称是否是它的DICOM应用名称（或其DICOM应用名称之一）。</font><br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.5 响应应用实体名称（固定值）</font></h4>
该参数定义了实际A-ASSOCIATE服务接收者的应用实体名称。在本标准中（[DICOM3.0](http://dicom.nema.org/standard.html)）该参数值应当始终与A-ASSOCIATE指示原语中的被叫方应用实体名称相同。<br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.6 用户信息</font></h4>
该参数包括链接的请求方和接收方的DICOM应用实体中的用户信息，其具体含义依赖于原语的应用长下文。关于该参数的详细介绍参见[附录D]()。<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>1. 该参数给出与‘应用上下文名称’参数相对应的DICOM应用实体的初始化信息。<br>
2. 附录D详细介绍了用户信息的各个子项，附加子项的定义参见标准第7部分（即PS3.7），另外关于子项中服务类应用消息的详细介绍需要参见标准第4部分（即PS3.4）</font><br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.7 结果</font></h4>
该参数或由连接请求接收方的上层服务提供者的关联控制服务相关函数提供，或<u><font color=yellow>直接</font></u>由上层服务提供者的表示层相关函数提供，用于表示使用连接服务的结果。该参数取下述值之一：<br>
a. 接受；<br>
b. 拒绝（永久）；<br>
c. 拒绝（临时）；<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>当连接请求方得到的返回结果是“拒绝（永久）”时，意味着该连接请求没有后续接入的必要。例如当远端DICOM应用名称未知时，该状态用于阻止连接的建立。<br>
</font><br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.8 结果来源</font></h4>
该参数值由上层服务提供者给出，指出了产生结果参数以及诊断参数（如果有的话）的来源。参数值如下：<br>
a. 上层服务使用者；<br>
b. 上层服务提供者（关联控制服务相关函数）;<br>
c. 上层服务提供者（表示层相关函数）;<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>如果7.1.1.7的结果参数返回值为“接受”,该参数对应取值为“上层服务使用者”，即a。<br>
</font><br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.9 错误报文</font></h4>
该参数仅在<b>7.1.1.7 结果</b>参数返回值为“拒绝（永久）”或“拒绝（临时）”时使用，给出与A-ASSOCIATE连接服务结果相关的错误诊断信息。<br>
如果<b>7.1.1.8 结果来源</b>参数返回值为“上层服务使用者”，该参数取值如下：<br>
a. 没有可参考原因<br>
b. 应用上下文名称不支持<br>
c. 请求应用实体名称无法识别<br>
d. 被请求应用实体名称无法识别<br>
e. 请求应用实体限定词无法识别（参见注释）<br>
f. 请求应用过程调用标识无法识别（参见注释）<br>
g. 请求应用实体调用标识无法识别（参见注释）<br>
h. 被请求应用实体限定词无法识别（参见注释）<br>
i. 被请求应用过程调用标识无法识别（参见注释）<br>
j. 被请求应用实体调用标识无法上识别（参见注释）<br>

如果<b>7.1.1.8 结果来源</b>参数返回值为“上层服务提供者（关联控制服务相关功能）”，该参数取值如下：<br>
a. 没有可参考原因<br>
b. 非一般（常用）上层服务版本<br>

如果<b>7.1.1.8 结果来源</b>参数返回值为“上层服务提供者（表现层相关功能）”，该参数取值如下：<br>
a. 没有可参考原因<br>
b. 临时阻塞<br>
c. 本地负荷溢出<br>
d. 被请求方地址（表现层）未知<br>
e. 表现层协议版本不支持<br>
f. 表现层服务访问点不可用<br>

<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>尽管上述部分取值在本标准中未使用，但允许使用其提示由于非法使用参数导致的错误信息。</font><br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.10 请求方表现层地址</font></h4>
该参数是结构化目标地址，包含一个明确的全球网络地址，通常是一个TCP/IP地址。详情参见附录C。<br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.11 被请求方表现层地址</font></h4>
该参数是结构化目标地址，包含一个明确的全球网络地址，通常是一个TCP/IP地址。详情参见附录C。<br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.12 响应中的表现层地址</font></h4>
DICOM3.0标准中，响应中的表现层地址应该与A-ASSOCIATE连接指示原语中的被请求方表现层地址相同。该参数包含一个明确唯一的全球网络地址。<br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.13 表示上下文定义列表</font></h4>
该参数用在A-ASSOCIATE的请求或指示原语中，是一个列表，包含一个或多个表示上下文。列表中每一项包含表示上下文标号，抽象语义名称，传输语义名称列表三部分。<br>
在交互时，表示上下文标号用于区分同一个连接中的不同表示上下文（不同的表示上下文在不同的连接中的标号可能相同）。该标号由连接请求方负责设定，确保每个标号不同即可，且该标号与表示上下文列表中排序无关。<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>在表示上下文定义列表中，每个表示上下文都与某个抽象语义名称相关联。如果列表中同一个抽象语义名称出现不止一次，每个抽象语义名称下必须单独定义表示上下文，因为每个表示上下文中只允许一种传输语义。<br>
</font><br>
DICOM应用实体使用的抽象语义的详细定义参见标准第4部分，即PS3.4；传输语义的详细定义参见标准第5部分，即PS3.5。另外附录B中有关于抽象语义和传输语义的进一步讨论。<br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.14 表示上下文定义结果列表</font></h4>
该参数用在A-ASSOCIATE的响应和确认原语中，标明请求或指示原语的表示上下文列表（即7.1.1.13中的参数）中每个表示上下文的接受或拒绝情况。表示上下文结果定义列表以结果列表的形式一一对应给出表示上下文定义列表中每一项的结果。每项结果由上层服务使用者在响应服务原语中给出，结果可能是接受（acceptance）、可能是用户端拒绝（user-rejection），也可能是提供端拒绝（provider-rejection），结果可被以任意顺序传送。<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>结果的顺序可能与原始的排序不同，因此结果不应该按照标号进行排序，且指示方不应假定或依赖于结果的特定顺序。<br>
</font><br>
标准规定每一个表示上下文只允许一种传输语义，即使表示上下文定义列表中给出了多种可供选择的传输语义。<br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.15 表示规定（固定值）</font></h4>
该参数允许对除了“表示核心”之外的表示功能单元进行协商，但DICOM应用实体中只用到了核心功能单元。因此本协议中该参数总是设置为“Presentation Kernel”，即表示核心。<br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.16 会话规定（固定值）</font></h4>
该参数允许对除了“会话核心”之外的会话功能单元进行协商，但DICOM应用实体只使用具有全双工的核心功能单元。<br>
<h4><font face="Microsoft YaHei" color=purple>7.1.1.17 其他参数</font></h4>
其他在DICOM应用实体交互时非必须的以及本标准中未使用的参数,此处不单独介绍。相关定义可参见开放系统互连中的关联控制服务，即OSI ACSE（ISO 8649)，以及表示层服务，即OSI Presentation Service（ISO 8822）。<br>
<h3><font face="Microsoft YaHei" color=purple>7.1.2 A-ASSOCIATE服务流程</font></h3>
<b>7.1.2.1</b><br> DICOM应用实体（包括上层服务使用者）通过发起A-ASSOCIATE请求原语期望建立一个连接。被请求应用实体由请求原语中的参数定义。在接收到A-ASSOCIATE确认原语之前请求方不允许触发除放弃请求原语（即A-ABORT）以外的任何原语。<br>
<b>7.1.2.2</b><br> 上层服务提供者发出A-ASSOCIATE指示原语到被请求应用实体。<br>
<b>7.1.2.3</b><br> 被请求应用实体通过发送包含适当结果参数的A-ASSOCATE响应原语，来表示接受或拒绝该链接。上层服务提供者应当发出包含相同结果参数的A-ASSOCIATE确认原语，此时结果源参数应该被设置为上层服务使用者。<br>
<b>7.1.2.4</b> 如果接收方接受请求后，该链接方可使用。双方应用实体可使用DICOM应用上下文中规定的除A-ASSOCIATE之外的任何有效服务。<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font color=red>这意味着一旦建立连接，双方即可传输DICOM消息（关于DICOM消息的定义参见标准第7部分，即PS3.7）<br>
</font><br>
<b>7.1.2.5</b> 如果被请求方应用实体拒绝，该链接建立失败。<br>
<b>7.1.2.6</b> 上层服务提供者有可能无法支持该请求连接，此刻应当返回包含适当结果参数（即拒绝）的A-ASSOCIATE确认原语给请求方，与此同时设置结果源参数为“上层服务提供者（ACSE相关功能）”或“上层服务提供者（表示层相关功能）”。不发送指示原语，拒绝建立连接。<br> 
<b>7.1.2.7</b> 连接请求方或接收方都有可能通过发送放弃请求原语（即A-ABORT)中断连接服务流程(详情参见7.3章节）。此时远端应用实体会接收到A-ABORT指示原语，中断建立该连接。<br>
<h2><font face="Microsoft YaHei" color=green>7.2 A-RELEASE解除服务</font></h2>
应用实体双方间标准的释放服务应当通过关联控制服务中A-RELEASE的请求、指示、响应和确认原语来完成。下文中服务发起者被称为请求方，接收A-RELEASE指示的服务使用者被称为接收方。A-RELEASE释放服务是确认服务。<br>
图7-2给出了连接双方应用实体间正常的释放服务。<br>
![](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_7-2.jpg)
<center>图7-2 连接释放</center>
<h3><font face="Microsoft YaHei" color=purple>7.2.1 A-RELEASE参数</font></h3>
表7-4列出了A-RELEASE服务的各种参数，包括固定值或本标准中DICOM应用实体未使用的参数。<br>
<center>Table 7-4 A-RELEASE服务参数</center><br>
<center>![](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_Table7-7.jpg)</center>
<h4><font face="Microsoft YaHei" color=purple>7.2.1.1 原因（固定值）</font></h4>
请求原语中用该参数来定义请求的紧迫程度。本标准中该参数使用设定为“正常”，即“normal”。<br>
<h4><font face="Microsoft YaHei" color=purple>7.2.1.2 结果（固定值）</font></h4>
在本标准中，该参数总是设置为“确定”，即“affirmative”。
<h3><font face="Microsoft YaHei" color=purple>7.2.2 A-RELEASE服务流程</font></h3>
<b>7.2.2.1</b> 上层服务使用者要释放连接时需要发送A-RELEASE请求原语，待接收到A-RELEASE确认原语后，再发送A-ABORT请求原语。<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font face="Microsoft YaHei" color=red>倘若A-RELEASE服务请求方没有发送A-ABORT原语，它依然可以接收P-DATA指示原语。</font><br>
><b>译者注：</b>上述“注意”的意思是说在A-RELEASE服务使用过程中，如果请求方没有完成整个流程（如上所述中提到的只发送了A-RELEASE请求原语，接收到A-RELEASE确认原语后未接着发送A-ABORT原语），连接不会断开，依然可以接收P-DATA数据。<br>

<b>7.2.2.2</b> 上层服务提供者需要发送A-RELEASE指示原语给接收者，随后接收者可发送A-RELEASE响应原语，或A-ABORT请求原语，或P-DATA请求原语。
><b>译者注：</b>之前关于服务原语（service primitive）在7.1中简单介绍过。如前文所述：在传统的点对点（或端到端）的模型中四种原语体现的不是很具体，其原因是点对点（或端到端）的模型将双方实体抽象成了一个点，而未考虑各自内部的OSI开放模型。如果将每个端点展开为OSI层模型，即可理解上述四种服务原语。下图Figure 7-1-zs将Figure 7-1的OSI模型进行了展开，使得服务原语一目了然。<br>

<center>![](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_7-1-zs.jpg)</center>
<center>Figure 7-1-zs(译者注）</center><br>
<b>7.2.2.3</b> 为了完成A-RELEASE服务，接收方在接收到A-RELEASE指示原语后需要反馈A-RELEASE响应原语。作为接收方的DICOM应用实体总是返回结果参数（即7.1.2）为“确定”（即“affirmative”）的A-RELEASE响应原语用于接受请求方释放连接的请求。<br>
<b>7.2.2.4</b> 在接收方发送A-RELEASE响应原语后，不应在该连接上发送任何原语包括P-DATA请求。<br>
<b>7.2.2.5</b> 上层服务提供者应当总是发送结果参数（即7.1.2）为“确定”的A-RELEASE确认原语。<br>
<b>7.2.2.6</b> 双方应用实体均可发送A-ABORT终止请求来中断A-RELEASE释放服务流程。接收方在接收到A-ABORT指示原语后会直接释放连接，但可能造成正在传输中的数据丢失。<br>
<b>7.2.2.7</b> 当双方应用实体同时发送A-RELEASE服务原语时会发生冲突。此时双方上层服务使用者会受到意外的A-RELEASE指示原语。正确释放连接的流程如下：<br>
a. 连接请求方发送A-RELEASE响应原语。<br>
b. 连接接收方等待对方的A-RELEASE确认原语，带接收后发送A-RELEASE响应原语<br>
c. 连接请求方接收到A-RELEASE确认原语。<br>
连接应当在ACSE服务使用者双方都收到A-RELEASE确认原语后释放。<br>
<h2><font face="Microsoft YaHei" color=green>7.3 A-ABORT中止服务</font></h2>
><b>译者注：</b>**中止**，指（做事）中途停止；使中途停止；**终止**，停止，不再继续。这里翻译成中止比较恰当。


双方应用实体的任意一方皆可通过发起ACSE的中止服务来非正常释放当前连接。该操作是非确认操作（<b><font color=gray>译者注：即不需要握手</font></b>）。然而，由于A-ABORT中止服务的流程可能会发生冲突，因而不确保指示原语的传输。当发生冲突时，双方应用实体意识到该连接已经被中断。A-ABORT中止服务通过A-ABORT中止请求原语和A-ABORT指示原语完成。（<b><font color=gray>译者注：即对应上文中的“non-confirmed”非确认</font></b>）<br>
<b><i><font face="Microsoft YaHei" color=red>注意：</font></i></b><br>
<font face="Microsoft YaHei" color=red>在已建立的连接上发送A-ABORT中止服务请求原语可能会破坏正在传输中的数据。</font><br>
图7-3给出了在两个应用实体间中止已建立连接的过程。<br>
<center>[](https://raw.githubusercontent.com/zssure-thu/DICOM-Chinese/master/Figure/Part%208/PS3.8_7-3.jpg)</center>
