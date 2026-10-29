# 思科网络工程师实战通关图谱：CCNA→CCNP→CCIE 十八板块手册
> 一句话定位：这不是一份"命令抄写本"，而是一套**按数据包旅行路线重排**的能力训练体系。18 个板块，每个板块都回答同一个问题——**这个技术解决什么问题、怎么配、怎么验、怎么炸、怎么修、怎么记**。

---

## README · 导览
### README_1 这份知识库的设计逻辑
网络技术的学习材料通常有两个通病：**按设备类型排列**（学的人不知道"为什么先学这个"），以及**只写到"配通"为止**（不写为什么这么配、炸了怎么办、怎么验证才算过关）。

本库的取舍是：把知识**按数据包的旅行路线**重排，并把每个技术点讲到"能落地、能验证、能排错"为止。

具体做了三件事：

| 设计动作 | 具体做法 |
| --- | --- |
| **重排顺序** | 按"物理线缆 → 交换机 VLAN/Trunk → 网关 → 路由选路 → NAT → 外网"这条数据包的旅行路线重排，与 CCNA→CCNP→CCIE 三级能力体系对齐 |
| **补结构** | 每个板块统一为「原理要点 → 落地配置 → 验证调试 → 故障排查 → 场景笔记 → 进阶延伸」六段式 |
| **补血肉** | 加入真实故障小故事、可复制的实验记录模板、可勾选的验证清单，把"看懂"变成"做出来" |

**贯穿全库的三个坚持**：

1. **命令真实可复现**——所有配置片段都能在 Packet Tracer / EVE-NG 中敲出来，输出按设备真实返回的样子给出；
2. **不回避"老东西"**——ISL、VTP、PIX、16AM 拨号这些已淘汰或正在淘汰的技术仍然保留，因为在网设备里还有大量这类配置，你迟早要读懂它们；
3. **每个结论都给判据**——不只说"这样配"，还说"看到什么算对""计数不增长说明什么"。

---

### README_2 板块总览（建议按顺序阅读）
| 板块 | 标题 | 核心内容 | 层级 | 主线周次 |
| --- | --- | --- | --- | --- |
| 板块0 | 学习路径与认证地图 | 三级认证体系、六大知识域权重、14 周推进表、实验环境、笔记方法论总纲 | 全局 | W0 |
| 板块1 | 设备接入与IOS命令行基座 | 带外/带内管理、IOS 模式体系、初始化 SOP、SSH 加固、密码恢复 | CCNA | W1 |
| 板块2 | 交换基础与二层安全 | VLAN 新旧命令对比、Trunk、VTP 域与灾难防护、二层安全三件套 | CCNA | W2 |
| 板块3 | 生成树与链路聚合 | STP 选举三步、状态机与定时器、RSTP、PortFast/BPDU Guard、LACP、MST | CCNA | W3 |
| 板块4 | VLAN间路由与三层交换SVI | 子接口 dot1q、SVI + ip routing、TTL 判读、方案决策矩阵 | CCNA | W4 |
| 板块5 | IP路由基础与静态路由 | 路由表五要素、管理距离表、静态/默认/浮动静态、DCE 时钟、IP SLA | CCNA | W5 |
| 板块6 | OSPF动态路由 | 链路状态原理、区域类型、cost 推导、单区域实战、LSA 六类、DR/BDR、多区域与认证 | CCNA+CCNP | W6-W7 |
| 板块7 | NAT与NAPT地址转换 | 四地址术语、三种 NAT、overload、转换表解读、服务器发布、NAT 处理顺序 | CCNA | W8 |
| 板块8 | 广域网与远程接入 | HDLC/PPP、CHAP 认证、16AM 拨号逐条解析、PPPoE、MSS | CCNA+CCNP | W9 |
| 板块9 | 网关冗余HSRP_VRRP_GLBP | HSRP 逐行拆解、track/preempt、VRRP/GLBP 对比、联动设计 | CCNA+CCNP | W10 |
| 板块10 | 网络安全ACL设备加固与VPN | 标准/扩展 ACL、NAT 协同、设备加固清单、CoPP、IPsec 两阶段、NAT 豁免 | CCNA+CCNP | W11 |
| 板块11 | 防火墙从PIX到ASA与状态化策略 | PIX 安装流程解析、conduit 参数、PIX→ASA 命令对照、对象 NAT、packet-tracer、DMZ | CCNA+CCNP | W11 |
| 板块12 | 网络服务与运维管理 | DHCP/中继、NTP、Syslog、SNMPv3、NetFlow、QoS 四步、SPAN、备份升级与回滚 | CCNA+CCNP | W12 |
| 板块13 | IPv6与双栈部署 | 地址格式与类型、EUI-64、SLAAC/DHCPv6、OSPFv3、过渡技术、IPv6 安全 | CCNA 强化 | W13 |
| 板块14 | 无线局域网基础 | WLAN 组件、Wi-Fi 6、轻量 AP + WLC、CAPWAP 八步状态机、WPA3、信道规划 | CCNA 强化 | W13 |
| 板块15 | 排错方法论与故障案例库 | 分层排错法、命令地图、12 个真实故障案例、实验报告模板、综合演练 | 全层级 | W14 |
| 板块16 | CCNP_CCIE进阶与网络自动化 | CCNP 核心+集中结构、ENCOR 能力域、CCIE Lab 备考、Python/RESTCONF/Ansible、SD-WAN | CCNP+CCIE | 进阶 |
| 板块17 | 命令速查与附录 | 全库命令速查、报错对照表、地址规划模板、线缆速查、全库索引 | 全层级 | 全程 |

---

### README_3 每个板块的统一结构（六段式）
1. **原理要点**——用一句话说清这项技术解决什么问题，配一张 ASCII 原理图；
2. **落地配置**——完整可复现的配置片段，**逐条命令解读**，而不是命令堆砌；
3. **验证调试**——真实 show 输出 + 逐字段解释，告诉你"看到什么才算对"；
4. **故障排查**——现象 → 排查 → 根因 → 修复 → 经验，配一个**案例小故事**；
5. **场景笔记**——这一章该记什么、怎么记、记完怎么复盘（附可复制模板）；
6. **进阶延伸**——CCNP/CCIE 阶段的加深内容与实验作业。

---

### README_4 配图说明（重要）
本库**全部原理图、拓扑图、流程图一律使用 ASCII 字符画**，直接放在代码块里——不依赖任何外链图床，因此在离线、内网、导出的任何一种环境下都能正常显示：

```latex
         ┌──────────┐
         │  Router  │
         └────┬─────┘
              │
    ┌─────────┴─────────┐
    │                   │
┌───┴───┐           ┌───┴───┐
│ PC-A  │           │ PC-B  │
└───────┘           └───────┘
```

这样做的好处：

+ GitHub、VS Code、纯文本编辑器**全部可直接渲染**，不依赖外链、不依赖图床；
+ 离线可读、可复制、可 diff、可搜索；
+ 需要配图时，你可以直接在代码块里改字符，比改图片快得多。

> 若你的阅读器支持 Mermaid，部分流程图也可自行转写为 mermaid 代码块；本库为保证最大兼容性，统一使用 ASCII。

---

### README_5 推荐使用方式
1. **按板块0 的周计划推进**，每个板块完成"配置 + 验证 + 人为故障复现"三件事；
2. **用板块17 做考前速查**，用板块15 做排错能力训练；
3. **走完 CCNA 主线（板块1–14）后**，以板块16 的 CCNP/CCIE 技术清单作为下一阶段路线图；
4. **每个实验当场写场景笔记**——本库的笔记模板不是"作业"，是给你半年后排查同类故障时用的检索入口。

---

### README_6 免责与版本提醒
认证考试的代码、权重与蓝图版本会随 Cisco 官方调整而变化（例如 ENCOR 的无线内容逐步独立、SD-WAN 与自动化权重提升、CCNA 迭代至 v1.1）。**报考前请以 Cisco 官方 Exam Topics 页面为准**。

本知识库提供的是**能力框架与可落地实操内核**，不替代官方考纲。涉及考试代码与费用处，均以"参考"标注，不写死具体年份。

## 板块0 · 学习路径与认证地图（18 板块总纲）
> 一句话定位：本板块回答三件事——**考什么、按什么顺序学、练到什么程度算过关**。板块1–17 是这张地图的展开。

---

### 0_0 本板块知识地图
```latex
                    ┌─────────────────────────────┐
                    │   思科认证三级能力阶梯        │
                    └─────────────────────────────┘

   CCIE  ────────────────────────────────────────────  8 小时高压交付
     ▲    规划 / 部署 / 优化 / 自动化，受约束条件下出方案
     │
   CCNP  ────────────────────────────────────────────  设计与排错
     ▲    给一个约束，选出合理方案并解释为什么，断了能定位
     │
   CCNA  ────────────────────────────────────────────  会不会配
          给一个需求，搭出一个能通的网络

   ─────────────────────────────────────────────────────────────
   底座：IOS 命令行（板块1）→ 二层（2/3）→ 三层（4/5/6）
         → 出口（7/8/9）→ 安全（10/11）→ 服务（12）
         → 新域（13/14）→ 排错（15）→ 进阶（16）→ 速查（17）
```

---

### 0_1 认证三级体系：能力递进，而不是考试堆叠
#### 0_1.1 三层认证到底差在哪
思科认证的三层，考的是**三种不同的能力**，而不是三份难度递增的题库：

| 层级 | 认证 | 考试构成 | 时长 / 费用（参考） | 能力定位 |
| --- | --- | --- | --- | --- |
| 助理级 | CCNA 200-301（当前为 v1.1 蓝图） | 单科笔试，含拖拽题与实验模拟题 | 约 120 分钟 / 约 300 美元 | 独立完成中小型网络的搭建、连通与基础安全 |
| 专业级 | CCNP Enterprise | 核心 350-401 ENCOR + 任选一门集中考试（300-410 ENARSI / 300-415 ENSDWI / 300-420 ENSLD / 300-430 ENWLSI / 300-435 ENAUTO 等） | 每科约 120 分钟 / 每科约 300–400 美元 | 设计并排错大中型企业网络，覆盖双栈、VPN、自动化、SD-WAN |
| 专家级 | CCIE Enterprise Infrastructure | ENCOR 笔试（资格）+ 8 小时 Lab（Design 模块 + DOO 模块） | Lab 8 小时 / 约 1600 美元 | 限时交付复杂企业网的规划、部署、优化与自动化 |

**一句话区分**：

+ **CCNA** 考"会不会配"——给一个需求，能搭出一个能通的网络；
+ **CCNP** 考"能不能设计与排错"——给一个约束，能选出合理方案并**解释为什么**，断了能快速定位；
+ **CCIE** 考"8 小时高压下的交付能力"——给一份需求文档，能规划、部署、优化并自动化一个复杂网络。

#### 0_1.2 三条必须先知道的现实约束
1. **蓝图会迭代，原理不会变。** 例如 ENCOR 350-401 的无线内容已逐步独立到 CCNP Wireless 体系，SD-WAN 与自动化的权重持续提升；CCNA 也在 v1.1 中强化了 IPv6、无线 Wi-Fi 6、二层安全与自动化。**报名前务必核对 Cisco 官方 Exam Topics**，本库提供的是能力框架与实操内核。
2. **证书有效期 3 年**，需通过更高等级考试或累计 Continuing Education 学分完成重认证。
3. **笔试已大量引入实验模拟题。** ENCOR 更是把 performance-based 题型集中在考试前段——**只会背命令的人会在这里被直接暴露**。

#### 0_1.3 案例小故事：两个人的第一次割接
> 小李和小王同一批入职，都过了 CCNA。
> 第一次园区网割接，凌晨两点，核心交换机换机后全网不通。
> **小李**的反应是翻笔记，找"核心交换机配置模板"，一条条往里敲：`vlan`、`trunk`、`standby`……敲到一半发现新的核心是三层交换机，而他背的是路由器模板。四十分钟后，他开始怀疑是光模块坏了。
> **小王**的反应是先掏出手机拍下旧设备的 `show run`，然后按"数据包旅行路线"倒推：PC 拿到地址了吗（DHCP）→ 能 ping 通网关吗（SVI 起来了吗）→ 网关能出去吗（上行路由）→ 出去能回来吗（回程路由/NAT）。四步走完，第五分钟就定位到：**新核心忘开 **`ip routing`，跨 VLAN 的包根本没被转发。一条命令，全网恢复。
> 区别不在于谁背的命令多，而在于**谁脑子里有一张能逐层收敛的地图**。这张地图，就是本库 18 个板块要帮你建的东西。

---

### 0_2 CCNA v1.1 六大知识域与权重
理解权重，才知道时间该花在哪。CCNA 200-301 v1.1 大致划分为六个域：

| 域 | 约占比 | 本库对应板块 |
| --- | --- | --- |
| Network Fundamentals 网络基础 | 约 20% | 板块1、板块5、板块13（IPv6） |
| Network Access 网络接入 | 约 20% | 板块2、板块3、板块4、板块14（无线） |
| IP Connectivity IP 连通性 | 约 25% | 板块5、板块6、板块9 |
| IP Services IP 服务 | 约 10% | 板块7、板块12 |
| Security Fundamentals 安全基础 | 约 15% | 板块10、板块11 |
| Automation & Programmability 自动化 | 约 10% | 板块16 |

**读表结论**：IP 连通性 + 网络基础 + 网络接入三项合计约 65%。也就是说，把板块1–6 打穿，你就已经站在及格线以上；其余板块决定你考 700 分还是 900 分。

#### 0_2.1 v1.1 的关键变化（要重点补的三块）
+ **IPv6 深度明显加强**：不只是地址格式，还包括 SLAAC、双栈部署、OSPFv3；
+ **无线更新到 Wi-Fi 6（802.11ax）特性**：OFDMA、MU-MIMO、TWT、BSS Coloring；
+ **安全域新增二层防护**：Port-Security、DHCP Snooping、DAI 与设备加固；
+ **自动化从概念层面扩展到 REST / JSON / YANG 的实用认知**。

---

### 0_3 新手入门顺序：沿"数据包的旅行路线"学
**不要按考试大纲顺序学，要按数据包的旅行顺序学。**

一个包从 PC1 出发到服务器，依次经过：

```latex
   物理线缆 → 交换机 VLAN/Trunk → 网关 → 路由选路 → NAT → 外网
      │            │                │          │         │
   板块1/8      板块2/3/4        板块4/9     板块5/6    板块7
```

学习顺序应与之一致。下面是 14 周推进表：

| 周次 | 主题 | 板块 | 关键实验（必须亲手敲） | 过关标志 |
| --- | --- | --- | --- | --- |
| W1 | 设备与 IOS | 1 | Console 登录、主机名、特权密码、SSH/Telnet、保存与擦除 | 能从 PC 远程登录设备并看到 running-config |
| W2 | 交换与 VLAN | 2 | VLAN 创建、access/trunk、VTP、allowed VLAN 裁剪 | 同 VLAN 通跨 VLAN 不通，且能解释原因 |
| W3 | 生成树与聚合 | 3 | 根桥选举、PortFast/BPDU Guard、LACP EtherChannel | 能说出哪个口被阻塞及原因 |
| W4 | VLAN 间路由 | 4 | 单臂路由（子接口 dot1q）、三层交换 SVI + ip routing | 两种方案都能通，能说出选型差异 |
| W5 | 静态路由 | 5 | 串口 DCE 时钟、静态路由、默认路由、浮动静态 | 不用动态协议实现三网段互通并主备切换 |
| W6–W7 | OSPF | 6 | 单区域 OSPF、反掩码、cost 推导、邻居状态机、LSA | 能解释 `O [110/65]` 的每一个字段 |
| W8 | NAT / NAPT | 7 | inside/outside、地址池 overload、静态 PAT 发布服务器 | 能读出转换表四个地址字段 |
| W9 | 广域网 | 8 | HDLC/PPP、CHAP 双向认证、16AM 拨号、PPPoE | 串口链路稳定 up，认证失败能定位 |
| W10 | 网关冗余 | 9 | HSRP 主备、优先级、抢占、track 上行口 | 关掉主用接口，业务 15 秒内恢复 |
| W11 | 安全与防火墙 | 10、11 | 标准/扩展 ACL、设备加固、PIX/ASA 策略 | 能写出"只放通某网段某端口"的规则 |
| W12 | 服务与运维 | 12 | DHCP/中继、NTP、Syslog、SNMP、QoS、备份与升级 | 日志能落到服务器，配置能回滚 |
| W13 | IPv6 与无线 | 13、14 | 双栈地址配置、SLAAC、OSPFv3、WLAN 组件与 CAPWAP | 能独立规划一个 /64 子网 |
| W14 | 排错综合 | 15 | 分层排错 + 故障案例复现 | 人为制造故障后 5 分钟内定位 |
| 进阶 | CCNP / CCIE | 16 | 多区域、重分发、BGP、自动化脚本 | 见板块16 的路线 |

#### 0_3.1 顺序不可颠倒的三个理由
1. **先学 VLAN 再学路由**，你才明白"网关子接口为什么要打 dot1q"；
2. **先学静态再学 OSPF**，你才理解"路由表每一条从哪来"；
3. 跳过前序直接学协议，只能背下 `network` 命令，却说不清**反掩码为什么是 0.0.0.255**。

> 这三句话是整张地图的"骨架"。任何时候你觉得学不下去了，回来读一遍这三条，通常能找到卡点。

---

### 0_4 三级能力自检清单
#### 0_4.1 CCNA 阶段：要形成条件反射
拿到设备与需求时，下面每一条都应该**不假思索**地做出来：

+ **拿到新设备**：Console 登录 → 主机名 → 特权加密密码 → 管理 IP → 远程登录方式 → 保存；
+ **拿到网段需求**：划 VLAN、配 trunk、起 SVI 或子接口、验网关连通性；
+ **拿到跨网段需求**：判断用静态还是 OSPF，配完能读出路由表条目含义；
+ **拿到上网需求**：配 NAT inside/outside 与 PAT，解释"为什么没有流量时转换表是空的"；
+ **拿到安全需求**：写 ACL 并放对接口方向（靠近源还是靠近目标）；
+ **ping 不通**：按物理层 → 二层 → 三层 → 上层逐层收敛。

#### 0_4.2 CCNP 阶段：新增"设计 + 排错"维度
CCNP 不再问"能不能通"，而是问"**为什么这条路最优**"：

+ **选路解释力**：管理距离、度量值、重分发、路由过滤、策略路由；
+ **冗余与收敛**：HSRP/VRRP、STP 调优、EtherChannel、BFD、快速收敛；
+ **规模化**：多区域 OSPF、OSPFv3、EIGRP、BGP 选路、组播、VRF-Lite、DMVPN/IPsec。

#### 0_4.3 CCIE 阶段：交付能力
+ 在**明确约束**下出方案（如"禁止使用静态路由""不得新增子网"）；
+ 每完成一个子任务**立刻验证**，而不是全部做完再验；
+ 自动化能力从"加分项"变成"必选项"。

---

### 0_5 实验环境搭建：三种可选方案
| 方案 | 能做什么 | 做不到什么 | 适合谁 |
| --- | --- | --- | --- |
| **Cisco Packet Tracer** | 板块1–14 的绝大多数实验：VLAN、STP、单臂路由、静态/OSPF、NAT、HSRP、ACL、DHCP、无线（含 WLC 基础） | 不支持真实 IOS 全部特性；无 PIX/ASA 完整命令行；Python/RESTCONF 无法实践 | 零基础入门到 CCNA |
| **EVE-NG / GNS3** | 跑真实 IOS / IOS-XE / ASA / CSR1000v 镜像，可做 IPsec、DMVPN、BGP、自动化 | 吃内存（建议 32G+），镜像需自备，搭建门槛较高 | CCNP / CCIE 备考 |
| **真机机架** | 手感、串口线、光模块、Console 服务器、密码恢复 | 贵、吵、占地方 | 需要做物理层实验（如 16AM 拨号、堆叠）时 |

#### 0_5.1 环境的最小可用配置建议
+ **CCNA 阶段**：一台 8G 内存的笔记本 + Packet Tracer 足够；
+ **CCNP 阶段**：EVE-NG 社区版 + 32G 内存 + 至少 200G SSD；
+ **通用习惯**：所有实验拓扑文件按 `板块号_实验名_日期` 命名保存，例如 `B06_OSPF单区域_v1.pkt`。**版本要留旧**——当你改坏了又想回退时，会感谢自己。

---

### 0_6 场景笔记方法论总纲（贯穿全库的记录方法）
> 这一节是全库通用方法。后面每个板块的「场景笔记」小节都是它的具体化。

#### 0_6.1 为什么必须写场景笔记
网络技术的遗忘曲线极陡：一个 OSPF 的 LSA 类型，今天背下来，两周后会忘一半；但**你亲手制造过一次"LSA 没同步导致路由缺失"的故障，并写下当时的现象和排查路径，两年后都还记得**。

笔记的价值不在"记录"，而在**给未来的自己留一个可检索的故障入口**。

#### 0_6.2 统一实验记录模板（每个实验都按这个写）
```latex
【实验编号】B04-01（板块号-序号）
【实验名称】单臂路由实现 VLAN 间互通
【日期 / 耗时】____ / ____ 分钟
【拓扑】贴 ASCII 拓扑图 + 设备型号与 IOS 版本
【地址规划】
  | 设备 | 接口 | IP | 掩码 | 网关 |
  |------|------|----|------|------|
【需求描述】用一句话写清楚"要让谁访问谁"（不要写"配置单臂路由"）
【关键配置】（只贴关键 5–15 行，不要整份 show run）
【预期结果】同 VLAN 通 / 跨 VLAN 通 / 到网关通 —— 逐条写
【实际结果】贴真实 show / ping 输出（含首包超时这类"正常异常"）
【验证清单】
  [ ] show ip route 看到两条直连
  [ ] PC 之间 ping 通，第二次 0 丢包
  [ ] show ip int brief 所有接口 up/up
【人为故障复现】
  制造故障：把主接口 shutdown
  现象：____
  定位命令：____
  根因：____
  修复：____
【复盘一句话】本次学到的、下次能直接复用的一点
【遗留问题】还没搞懂的，留给下一轮
```

#### 0_6.3 记笔记的四条纪律
1. **贴真实输出，不贴"理想输出"**。设备给你的才是真的，教材给的常是剪辑版；
2. **异常不删**。首包超时、接口抖一下、日志刷一行警告——这些"噪声"往往是后来排错的关键线索；
3. **每个实验必须有"人为故障复现"**。没故意弄坏过的实验，等于没做过；
4. **每周末花 20 分钟回看本周 3 条笔记**，只做一件事：把"复盘一句话"抄进板块17 的速查表。

#### 0_6.4 本库笔记的分层
| 笔记类型 | 记录时机 | 存放位置建议 |
| --- | --- | --- |
| **实验笔记**（上文模板） | 每次敲完实验当场 | 每个板块一个笔记本/目录 |
| **现象卡** | 遇到没见过的报错/现象 | 板块15 故障案例库，追加条目 |
| **命令卡** | 发现一条好用的 show / debug | 板块17 速查表，追加一行 |
| **设计卡** | 遇到"两种方案选哪个" | 板块0 的设计决策清单（见下） |

---

### 0_7 场景笔记模板：设计决策卡（CCNP 阶段启用）
从 CCNP 开始，笔记要多记一类东西——**为什么选 A 不选 B**。

```latex
【决策问题】核心层用三层交换 SVI 还是单臂路由？
【约束条件】
  - 预算：____
  - 流量规模：____
  - 运维人力：____
【候选方案】
  A. 三层交换 SVI：硬件转发、线速、微秒级延迟；设备成本高
  B. 单臂路由：省接口、成本低；所有跨 VLAN 流量挤一条链路、软件转发
【选择】A
【理由】跨 VLAN 流量预计超过上行链路 40%，单臂路由会成为瓶颈
【什么情况下会反过来选 B】分支站点，VLAN 少于 4 个、流量小、已有闲置路由器
【验证方式】上线后用 NetFlow 观察跨 VLAN 流量占比，超过 60% 需扩容
```

> **判断标准**：如果你的笔记里只有"选了 A"，那不是决策记录；有"什么情况下会反过来选 B"，才是设计能力。

---

### 0_8 老技术与新写法：为什么本库要保留"已淘汰"的东西
你会在本库里遇到一些看起来"过时"的内容：ISL 封装、VTP、`vlan database`、PIX 的 `conduit`、16AM 拨号模块。**它们不是凑字数**——原因有两条：

1. **在网设备里还有大量这类配置**。接手一台跑了十年的 Catalyst 2900XL 或 PIX，你不能说"这技术淘汰了我不看"；
2. **老命令往往是理解新命令的最短路径**。看懂 `nat 1` + `global 1` 的编号配对，你才真正明白 ASA 对象 NAT 为什么要改成"对象 + 规则"绑定在一起。

下面是本库涉及的几组主要对照，遇到时知道去哪一节查：

| 技术 | 老写法（需能识别） | 现代写法（需能配置） | 所在板块 |
| --- | --- | --- | --- |
| 创建 VLAN | `vlan database` + `vlan 10 name X` | `config-vlan` 模式：`vlan 10` / `name X` | 板块2 |
| Trunk 封装 | ISL（Cisco 私有） | 802.1Q（dot1q） | 板块2 |
| VLAN 自动同步 | VTP Server/Client | 不用 VTP，全 transparent + 自动化模板下发 | 板块2 |
| 防火墙 NAT | `nat` / `global` / `static` / `conduit` | 对象 NAT + ACL（**ACL 写真实地址**） | 板块11 |
| 远程接入 | 16AM/8AM 模拟 Modem 拨号 | PPPoE、IPsec/SSL VPN、SD-WAN | 板块8 |
| VLAN 间路由 | 多物理口 / 单臂路由 | 三层交换 SVI（硬件转发） | 板块4 |
| 生成树 | PVST+（每 VLAN 一棵树） | Rapid-PVST+ / MST（多 VLAN 映射到一个实例） | 板块3 |

> **读表方法**：左列是"考试可能考你认不认得、现网可能要你维护"，中列是"你要能独立配出来"。**两列都要会，但会的方式不同**——前者重识别，后者重实操。

---

### 0_9 本板块的验证清单与过关标志
**验证清单（勾选即过关）**：

- [ ] 能不看资料说出 CCNA / CCNP / CCIE 的能力差异各一句话；
- [ ] 能说出 CCNA 六大域中权重最高的两个域及其对应板块；
- [ ] 能解释"为什么先学 VLAN 再学路由"；
- [ ] 已搭好实验环境（Packet Tracer 或 EVE-NG），并完成一次 Console 登录；
- [ ] 已按 0_6.2 模板建立第一个实验笔记文件。

**过关标志**：把 14 周表打印出来贴在显示器旁，且**知道本周自己在哪一格**。

---

### 0_10 进阶延伸：从"学完"到"考过"
1. **用板块17 做考前一页纸**：考前两周，把每个板块的"复盘一句话"合并成一页；
2. **用板块15 做限时排错训练**：给自己 5 分钟，随机挑一个故障案例复现并定位；
3. **每走完一个板块，回来看一次本板块的周次表**，确认没有偏离主线；
4. **CCNA 考完不要停**：直接进入板块16 的 CCNP 技术清单，中间断档超过两个月，手感会明显下滑。

---

## 板块1 · 设备接入与 IOS 命令行基座
> 一句话定位：**所有网络配置最终都落在 IOS 上，IOS 不熟，后面全是空中楼阁。** 本板块不止于"能登录"，而是把初始化、远程管理、配置生命周期、密码恢复串成一条可复用的标准作业流程（SOP）。

---

### 1_0 本板块知识地图
```latex
   ┌─────────────── 设备的两条接入通道 ───────────────┐
   │                                                  │
   │  [PC]──Console 线──[设备]       带外：不占业务带宽 │
   │                                 新机/断网唯一入口 │
   │                                                  │
   │  [PC]══网络══[Telnet/SSH]──[设备] 带内：日常运维   │
   │                                 明文 Telnet 禁用  │
   └──────────────────────────────────────────────────┘
                          │
                          ▼
         IOS 模式体系（User → Privileged → Global → 子模式）
                          │
                          ▼
   初始化 SOP → 远程加固 → 配置生命周期（保存/备份/擦除/恢复）
```

---

### 1_1 设备管理的两条通道：带外与带内
| 管理方式 | 通道 | 是否占用业务带宽 | 使用场景 | 典型入口 |
| --- | --- | --- | --- | --- |
| **带外管理（Out-of-band）** | Console 口 + 配置线 | 不占用 | 新设备上架、密码遗忘、网络中断时的唯一入口 | 9600 / 8 / 无校验 / 1 停止位 / 无流控 |
| **带内管理（In-band）** | Telnet / SSH / HTTP(S) / SNMP | 占用 | 日常远程运维 | `ssh -l admin 192.168.1.1` |

#### 1_1.1 关键认知
**第一次配置设备必须走 Console**——此时设备既无 IP 也无账号，带内通道根本不存在。这也是机房里永远要给每台设备留一条 Console 线的原因。

```latex
   带外通道                          带内通道
   ┌────────┐  Console               ┌────────┐  网络
   │   PC   │───────────┐            │   PC   │═══════════┐
   └────────┘           │            └────────┘           │
                        ▼                                 ▼
                 ┌─────────────┐                  ┌─────────────┐
                 │   Router    │◄─────────────────│   Router    │
                 │  (Console)  │     同一台设备    │  (vty 线路)  │
                 └─────────────┘                  └─────────────┘

   业务网全断时：带内全灭，带外仍在 → 这是"最后一条命"
```

#### 1_1.2 生产经验
中大型网络建议部署 **Console 服务器（终端服务器）** 做带外管理。业务网全断时，它是你唯一还能"摸到"设备的通道。

> 真实代价：某公司因核心交换机配置错误导致带内全断，而机房未部署 Console 服务器，工程师必须开车 40 分钟到现场插 Console 线。如果当初花几千块部署一台终端服务器，这 40 分钟就是 0。

---

### 1_2 IOS 模式体系：每条命令都落在某一层
| 提示符 | 模式名称 | 能做什么 |
| --- | --- | --- |
| `Router>` | 用户模式 User EXEC | 只能看少量状态 |
| `Router#` | 特权模式 Privileged EXEC | 全部查看权 + 配置入口 |
| `Router(config)#` | 全局配置模式 | 影响整机的配置 |
| `Router(config-if)#` | 接口配置模式 | 接口 IP、no shutdown |
| `Router(config-subif)#` | 子接口配置模式 | 单臂路由的 dot1q 封装 |
| `Router(config-line)#` | 线路配置模式 | console / vty / aux |
| `Router(config-router)#` | 路由进程配置模式 | OSPF / EIGRP / RIP |
| `Router(vlan)#` | VLAN 数据库模式 | 老平台建 VLAN（见板块2） |

#### 1_2.1 进出规则（必须形成肌肉记忆）
| 动作 | 命令 | 记忆点 |
| --- | --- | --- |
| 用户 → 特权 | `enable`（`en`） | 需要特权密码 |
| 特权 → 全局 | `configure terminal`（`conf t`） | 配设备第一步 |
| 全局 → 接口 | `interface gi0/0`（`int gi0/0`） | 简写不要省空格 |
| 返回上一层 | `exit` | 逐级退 |
| 直接回特权 | `end` 或 `Ctrl+Z` | 保存前常用 |
| 撤销某条命令 | 原命令前加 `no` | `no shutdown` = 打开接口（**反直觉点**） |
| 恢复接口出厂 | `default interface gi0/0` | 比逐条 no 干净 |

#### 1_2.2 效率三件套
+ `?` 看当前模式可用命令；`s?` 看以 s 开头的所有命令；`命令?` 看该命令的参数；
+ `Tab` 自动补全；命令可缩写到**唯一可识别**为止（`conf t`、`int gi 0/0`、`ip add`）；
+ `show history` 看历史命令；`terminal history size 50` 调大缓存；`↑` 复用上一条。

> **缩写为什么会失效？** 因为 IOS 只在"能唯一识别"时接受缩写。`sh ip int br` 能补全是因为没有第二条以 `sh ip int br` 开头的命令；而 `sh i` 会失败，因为 `show ip`、`show interfaces`、`show ipv6` 都匹配。**这不是设备变笨了，是你在给它出多选题。**

---

### 1_3 实战：一台新路由器的标准初始化
**场景**：你是新入职网管，机房有一台全新 Router_2811，PC 通过 Console 线连接。要求：改名 R1、设置加密特权密码、配置管理 IP、允许远程登录。

```latex
    Router>en
    Router#conf t
    Router(config)#hostname R1
    R1(config)#enable secret 123456          ←用 secret 不用 password（MD5 型哈希存储）
    R1(config)#exit
    R1#exit                                  ←退到用户模式，验证密码是否生效
    R1>en
    Password:                                ←输入不回显，连续输错会有延迟惩罚
    R1#conf t
    R1(config)#line vty 0 4                  ←允许 5 条并发远程会话（0~4）
```

#### 1_3.1 这段配置里藏着 6 个考点
1. `enable secret`** vs **`enable password`：前者用 MD5 型哈希存储，后者为明文/弱加密；同时配置时 **secret 优先**。
2. `service password-encryption`：全局开启后，明文密码（如 vty password）以 Type 7 显示，**仅防"肩膀冲浪"，不是真正的安全加密**（Type 7 可逆）。
3. `login`** 与 **`login local`：前者用线路密码，后者调用本地 `username` 数据库。生产推荐 `login local`。
4. `no shutdown`** 字面像"关闭"，实为打开接口**——新人最常踩的坑。
5. `copy running-config startup-config`**（可简写 **`wr`**）**：running-config 在 RAM（掉电丢失），startup-config 在 NVRAM（永久保存）。
6. **敲错命令时 **`R1#password`** 会触发域名解析、卡住数秒**：

```latex
    R1#password
    Translating "password"...domain server (255.255.255.255)
    % Unknown command or computer name, or unable to find computer address
```

这是把不存在的命令当主机名做 DNS 解析。实验室随手加一条即可解决：

```latex
    R1(config)#no ip domain-lookup
```

#### 1_3.2 完整初始化 SOP（可直接当 checklist 用）
```latex
! 第1步 基础身份
hostname R1
no ip domain-lookup                 ← 防手抖触发 DNS 解析
banner motd #未授权禁止访问#          ← 法律与合规上的必要提示

! 第2步 密码与账号
enable secret Str0ngEn@ble
service password-encryption
username admin secret Str0ngP@ss

! 第3步 管理接口
interface gi0/0
 description ## To-Core ##
 ip address 192.168.1.1 255.255.255.0
 no shutdown

! 第4步 远程登录（见 1_4，生产用 SSH）
line vty 0 4
 transport input ssh
 login local
 exec-timeout 10 0

! 第5步 保存
end
write memory
```

---

### 1_4 远程管理加固：从 Telnet 升级到 SSH
**Telnet 的问题不是"不好用"，而是账号密码与所有交互内容全部明文传输，抓包即可还原。** CCNA 考概念、CCNP 考部署、生产环境禁用 Telnet。

#### 1_4.1 SSH 配置五步法（缺一不可）
```latex
R1(config)#hostname R1                              ←第1步必须有主机名（用于生成密钥对）
R1(config)#ip domain-name example.com               ←第2步必须有域名
R1(config)#username admin secret StrOngP@ss         ←第3步本地用户（secret 加密）
R1(config)#crypto key generate rsa modulus 2048     ←第4步生成 RSA 密钥（modulus ≥ 1024）
R1(config)#ip ssh version 2                         ←第5步强制 SSHv2（v1 有已知漏洞）
R1(config)#line vty 0 4
R1(config-line)#transport input ssh                 ←只接受 SSH，彻底关闭 Telnet
R1(config-line)#login local
R1(config-line)#exec-timeout 10 0                   ←10 分钟无操作自动断开
R1(config-line)#exit
R1(config)#access-list 10 permit 192.168.10.0 0.0.0.255   ←限定管理网段
R1(config)#line vty 0 4
R1(config-line)#access-class 10 in
```

**为什么「1」「2」「4」缺一不可**：RSA 密钥对的"名字"由 `主机名.域名` 构成。没有主机名或域名，IOS 会拒绝生成密钥——这是 SSH 配不出来的第一大原因。

#### 1_4.2 验证
```latex
R1#show ip ssh        ←SSH 版本与启用状态
R1#show ssh           ←当前 SSH 会话
R1#show line vty 0 4  ←线路允许的协议与空闲超时
```

更进一步应接入 **AAA**（`aaa new-model` + RADIUS/TACACS+），实现集中认证与操作审计，这是等保与内控的常见硬性要求（见板块10）。

---

### 1_5 配置的生命周期：保存、备份、擦除、恢复
| 操作 | 命令 | 说明 |
| --- | --- | --- |
| 保存当前配置 | `copy running-config startup-config` / `wr` | RAM → NVRAM |
| 查看运行配置 | `show running-config`（`sh run`） | 当前生效配置 |
| 查看启动配置 | `show startup-config`（`sh start`） | 下次启动加载的配置 |
| 备份到 TFTP | `copy running-config tftp:` | 按提示填服务器 IP 与文件名 |
| 从 TFTP 恢复 | `copy tftp: running-config` | 注意会**合并**而非覆盖 |
| 擦除配置 | `erase startup-config` + `delete vlan.dat` | 交换机还要删 vlan.dat |
| 重启 | `reload` | 擦除后必须重启才生效 |
| 查看配置差异 | `show archive` / `archive config` | 配合 `archive log config` 做变更审计 |

#### 1_5.1 密码恢复（原理与流程）
**原理**：让设备启动时**跳过 startup-config 的加载**（修改配置寄存器值为 `0x2142`），进入无密码状态后，把配置捞回来、改密码、再把寄存器改回 `0x2102`。

```latex
第1步 Console 连接，重启设备，启动时按 Ctrl+Break 进入 rommon
第2步 rommon 1 > confreg 0x2142
第3步 rommon 2 > reset                      ←重启，跳过 startup-config
第4步 Router#copy startup-config running-config   ←把原配置捞回内存（注意是 start→run）
第5步 Router(config)#enable secret 新密码
第6步 Router(config)#config-register 0x2102
第7步 Router#write memory
第8步 Router#reload
```

> **关键细节**：第 第4步 步方向必须是 `start → run`。如果写反成 `copy run start`，你会把空配置覆盖掉原配置，密码是"恢复"了，业务配置全没了——这是密码恢复事故的头号原因。

---

### 1_6 验证与调试：看到什么才算对
#### 1_6.1 接口状态判读（现场第一命令）
```latex
R1#show ip interface brief

Interface        IP-Address   OK? Method Status                Protocol
GigabitEthernet0/0  192.168.1.1  YES manual up                    up
GigabitEthernet0/1  unassigned   YES manual administratively down  down
Serial2/0           192.168.3.1  YES manual up                     down
```

三列状态的含义：

| 显示 | 含义 | 下一步 |
| --- | --- | --- |
| `up / up` | 物理与协议都正常 | 可以开始测连通性 |
| `administratively down / down` | 人为 shutdown 了 | `no shutdown` |
| `up / down` | 物理通协议不通 | 串口查 DCE 时钟与封装；以太网查双工/速率 |
| `down / down` | 线缆没插好或对端没起 | 换线、查对端 |

#### 1_6.2 值得养成的验证三连
```latex
R1#show version              ←IOS 版本、配置寄存器、开机时长
R1#show running-config | section line vty    ←只看 vty 段，避免被整份配置淹没
R1#show ip ssh               ←确认 SSH 已启用及版本
```

管道符 `|` 是 IOS 的高效工具：`| include`（含）、`| exclude`（不含）、`| section`（段落）、`| begin`（从某行开始）。

---

### 1_7 案例小故事：一句 `no shutdown` 的深夜代价
> 老张是某制造企业的网管。一次机房搬迁后，新装的一台路由器怎么都 telnet 不上。他检查了 IP、掩码、网关，甚至重配了 vty 线路，折腾到凌晨一点。
> 第二天带教师傅来了，只敲了一条命令：`show ip interface brief`。屏幕上赫然写着：
> 一句 `no shutdown`，全网通。
> **复盘**：老张的问题不是不懂 `no shutdown`，而是**没有从设备的视角去看状态**——他一直在自己的思路里绕（"我配过 IP 了啊"），而不是问设备（"你现在是什么状态"）。
> **这条经验后来成了他的第一条现场纪律**：任何"不通"的问题，**第一个命令永远是 **`show ip interface brief`，让设备先开口说话。

```latex
GigabitEthernet0/0  192.168.1.1  YES manual administratively down  down
```

**根因归类**：接口管理性关闭（administratively down）。  
**通用解法**：先 `show ip int brief` 看双 up，再往上查三层。  
**延伸**：Cisco 接口默认是 `shutdown` 的；而部分厂商默认 `no shutdown`。跨厂商设备混用时，这个差异会反复坑人。

---

### 1_8 场景笔记：这一章该记什么
#### 1_8.1 必记的四类内容
1. **你的设备型号与 IOS 版本**（`show version` 输出贴一行）——不同版本命令支持度不同，查资料时这是第一过滤条件；
2. **初始化 SOP 的本地化版本**——把你公司/实验室的固定参数（域名、管理网段、密码策略、banner 文案）填进 1_3.2 模板，固化为可粘贴的一段；
3. **密码恢复的实际耗时**——真机做一次，记下从 Ctrl+Break 到重启完成花了多久，这个值决定了你在真实割接窗口敢不敢做密码恢复；
4. `show ip int brief`** 的四种状态组合解读**——背下来，它是全库排错的起点。

#### 1_8.2 本板块实验记录模板（可直接复制）
```latex
【实验编号】B01-01
【实验名称】新路由器初始化 + SSH 加固
【日期 / 耗时】____ / ____ 分钟
【拓扑】
    [PC]──Console──[R1]──gi0/0──管理网 192.168.1.0/24
【地址规划】
  | 设备 | 接口 | IP        | 掩码          |
  | R1   | gi0/0| 192.168.1.1| 255.255.255.0 |
【需求】PC 能通过 SSH 登录 R1，明文 Telnet 不可用
【关键配置】
  hostname R1 / ip domain-name / crypto key gen rsa 2048 /
  ip ssh version 2 / transport input ssh / login local
【预期结果】
  - Telnet 连接被拒绝
  - SSH 用 admin 账号可登录
  - show ip ssh 显示 version 2.0, enabled
【实际结果】贴真实输出
【验证清单】
  [ ] show ip ssh 显示 SSH Enabled - version 2.0
  [ ] 从 PC telnet 192.168.1.1 → 连接被拒
  [ ] 从 PC ssh -l admin 192.168.1.1 → 登录成功
  [ ] show line vty 0 4 显示 transport input = ssh
  [ ] 从非 192.168.10.0/24 网段 SSH → 被 ACL 拒绝
【人为故障复现】
  制造故障：把 ip domain-name 删掉后重做 SSH
  现象：crypto key generate 报错 % Please define a domain-name first
  根因：密钥名由 主机名.域名 构成
  修复：补上 ip domain-name
【复盘一句话】____（建议写：SSH 五步法里最容易漏的是哪一步）
【遗留问题】____
```

#### 1_8.3 本板块的实用验证清单
- [ ] 能用 Console 登录一台"从未配置过"的设备；
- [ ] 能在一分钟内完成 hostname + enable secret + 管理 IP + 保存；
- [ ] 能配出 SSH 并**证明 Telnet 已被拒绝**；
- [ ] 能在真机或模拟器上完成一次密码恢复；
- [ ] 能解释 `up/down` 与 `administratively down/down` 的区别；
- [ ] 已把初始化 SOP 固化成自己可粘贴的一段配置。

---

### 1_9 进阶延伸
1. **AAA 与集中认证**：`aaa new-model` + TACACS+（设备登录审计）/ RADIUS（网络接入认证），见板块10；
2. **配置归档与自动化基线**：`archive` + `kron` 定时自动备份 running-config 到 TFTP，把"人记得保存"变成"系统自己保存"；
3. **自动化的第一步**：用 Python + Netmiko 批量采集 50 台设备的 `show version`（见板块16），你会发现批量能力才是运维的分水岭；
4. **IOS 升级与回滚**：`copy tftp: flash:` → 改 `boot system` → `reload`，务必保留旧镜像做回退（见板块12）。

---

## 板块2 · 交换基础 — VLAN、Trunk、VTP 与二层安全
> 一句话定位：**二层决定广播域的边界，三层决定数据怎么跨过去。** 本板块讲"怎么切"，板块4 讲"切完怎么连"。

---

### 2_0 本板块知识地图
```latex
    不划 VLAN：一台交换机 = 一个广播域
    ┌──────────────────────────────┐
    │  ARP 广播泛洪到所有端口        │
    │  所有主机二层互通，无隔离      │
    └──────────────────────────────┘
                  │ 划 VLAN
                  ▼
    ┌──────────────────────────────┐
    │  VLAN 10 (技术部)  │ VLAN 20 (销售部) │
    │    PC1  PC2       │    PC3  PC4      │
    └────────┬──────────┴────────┬─────────┘
             │                   │
             └───── Trunk ───────┘  802.1Q 打 Tag，一条线承载多 VLAN
```

---

### 2_1 VLAN 的本质：一台交换机切成多台"虚拟交换机"
**不划 VLAN 会怎样**：整个交换网络是一个广播域。ARP 请求等广播帧会泛洪到所有端口，主机越多广播越泛滥，带宽与 CPU 被白白消耗；同时所有主机二层互通，安全隔离无从谈起。

**VLAN 做什么**：把一个物理 LAN 在逻辑上切成多个广播域。**同 VLAN 二层直接通信，不同 VLAN 之间必须经三层设备**（见板块4）。

#### 2_1.1 关键数字（必记）
| 项目 | 值 | 说明 |
| --- | --- | --- |
| 普通范围 VLAN | 1–1005 | 存在 vlan.dat，可被 VTP 同步 |
| 扩展范围 VLAN | 1006–4094 | 需交换机处于 VTP transparent 模式才能创建 |
| VLAN 1 | 默认 VLAN | 所有端口默认归属；管理流量与 CDP/STP 控制报文默认走它 |
| 保留 VLAN | 1002–1005 | FDDI / Token Ring 遗留，不可删除 |
| 802.1Q Tag | 12 bit VLAN ID | 决定最多 4096 个 VLAN（0 与 4095 保留） |
| 2900XL 限制 | 最多 64 个激活 VLAN，ID 1–1005 | 老平台限制，现代平台无此约束 |

#### 2_1.2 生产建议（写进上架 SOP）
+ **绝不让用户端口停留在 VLAN 1**；
+ **管理 VLAN 改为独立 ID**（如 VLAN 99）；
+ **全网统一 native VLAN 且不使用 VLAN 1**。

> 为什么强调 VLAN 1？因为所有设备的默认配置都在 VLAN 1，攻击者也知道这一点。把用户流量挪出 VLAN 1，等于让"默认攻击面"上没有人。

---

### 2_2 创建 VLAN：老平台 vlan database vs 现代 IOS
#### 2_2.1 老平台（2900XL）的写法——VLAN 数据库模式
```latex
Switch# vlan database
Switch(vlan)# vtp domain domain-name
Switch(vlan)# vtp server
Switch(vlan)# vlan vlan-id name vlan-name
Switch(vlan)# show vtp status
Switch(vlan)# no vlan vlan-id        ←删除 VLAN
```

#### 2_2.2 现代 Catalyst（2960/3560/9200 等）的写法——全局配置模式
```latex
Switch(config)#vlan 10
Switch(config-vlan)#name Tech
Switch(config-vlan)#exit
Switch(config)#vlan 20
Switch(config-vlan)#name Sales
Switch(config-vlan)#end
Switch#show vlan brief
```

#### 2_2.3 两种写法对比
| 对比项 | `vlan database`（老） | `configure terminal`（新） |
| --- | --- | --- |
| 生效时机 | exit 并 apply 后写入 vlan.dat | 立即生效 |
| 配置存放 | vlan.dat（Flash） | vlan.dat + running-config |
| 扩展 VLAN 支持 | 否 | 需 transparent 模式 |
| 考试要求 | **只需能识别** | **必须掌握** |

#### 2_2.4 把端口划入 VLAN
```latex
Switch(config)#interface gi0/2
Switch(config-if)#switchport mode access     ←显式设为 access，避免 DTP 自动协商带来不确定性
Switch(config-if)#switchport access vlan 10
Switch(config-if)#spanning-tree portfast     ←接终端时启用，跳过 STP 侦听/学习（省约 30 秒）
Switch(config-if)#exit
Switch(config)#interface range gi0/3-8       ←批量配置，现场效率关键
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport access vlan 20
```

更省事的接入端口模板（一条顶三条）：

```latex
Switch(config-if-range)#switchport host      ←= access + portfast + nonegotiate
```

#### 2_2.5 验证
```latex
Switch#show vlan brief
Switch#show interfaces gi0/2 switchport      ←看 Operational Mode 与 Access Mode VLAN
Switch#show mac address-table                ←看 MAC、端口、VLAN 的对应关系
```

`show interfaces gi0/2 switchport` 里最容易看的两行：

```latex
Administrative Mode: static access     ←你配的
Operational Mode: static access        ←实际跑的（两者不一致 = 配置没生效或协商被拒）
```

---

### 2_3 VTP：让 VLAN 自动同步，也是最容易"炸全网"的功能
VTP（VLAN Trunking Protocol）在一个域内同步 VLAN 的增删改，避免逐台手工录入。

#### 2_3.1 四种模式
| VTP 模式 | 能否创建/删除 VLAN | 是否同步他人 | 是否转发通告 | 配置存于 |
| --- | --- | --- | --- | --- |
| **Server（默认）** | ✅ | ✅ | ✅ | vlan.dat |
| **Client** | ❌ | ✅ | ✅ | 不保存（重启后从 Server 学） |
| **Transparent** | ✅（仅本地有效） | ❌ | ✅（转发但不采纳） | vlan.dat + running-config |
| **Off（VTPv3）** | ✅ | ❌ | ❌ | — |

#### 2_3.2 配置
```latex
Switch#vlan database
Switch(vlan)#vtp domain HQ
Switch(vlan)#vtp domain HQ password VtpP@ss   ←域名与密码参与修订号校验
Switch(vlan)#vtp server
Switch(vlan)#vtp v2-mode                      ←启用 VTP V2（默认是 V1）
Switch(vlan)#vtp transparent                  ←想"关闭 VTP"，把模式改为 transparent 即可
Switch(vlan)#exit
Switch#show vtp status
```

#### 2_3.3 `show vtp status` 关键行解读
```latex
VTP Version                  : 2
Configuration Revision       : 7      ←配置修订号，每改一次 VLAN 加 1
VTP Operating Mode           : Server
VTP Domain Name              : HQ
VTP Pruning Mode             : Disabled
VTP V2 Mode                  : Enabled
```

#### 2_3.4 必须知道的"VTP 灾难"
**一台配置修订号更高的旧交换机接入网络，即使它是 Client 或 Server，也会把它携带的 VLAN 数据库反向覆盖整个域——全网 VLAN 被清空，业务瞬间中断。**

```latex
   现网 VTP 域 HQ，修订号 = 7
              │
              │  接入一台从库房翻出的旧交换机（修订号 = 42）
              ▼
   旧交换机："我的修订号更高，听我的"
              │
              ▼
   全网 VLAN 被替换为旧交换机那套（可能只有 VLAN 1）
              │
              ▼
   所有 access 口落到不存在的 VLAN → 业务全断
```

#### 2_3.5 四条防护规则（写入上架 SOP）
1. 新交换机上架前先 `erase startup-config` + `delete vlan.dat`，并把模式设为 **transparent** 再接入；
2. 接入后确认 **Configuration Revision 归 0**，再改回 Server/Client；
3. 全网统一**域名 + 密码**；
4. 现代生产网络建议**直接不使用 VTP（全部 transparent）**，由自动化模板统一下发 VLAN，可控性更好。

---

### 2_4 Trunk：一条链路承载多个 VLAN
Trunk 干两件事：给帧打上 VLAN 标识（Tagging），让对端知道这个帧属于哪个 VLAN。

#### 2_4.1 两种封装
| 封装 | 标准 | 是否打 Tag | 现状 |
| --- | --- | --- | --- |
| **802.1Q（dot1q）** | IEEE 标准 | 是（**native VLAN 不打 Tag**） | 事实标准，跨厂商兼容 |
| **ISL** | Cisco 私有 | 是（整体封装） | 已淘汰，仅见于 2900XL/3500XL 等老设备 |

#### 2_4.2 配置
```latex
! 老平台（ISL 封装）
Switch(config)#interface fa0/1
Switch(config-if)#switchport mode trunk
Switch(config-if)#switchport trunk encapsulation isl

! 现代平台（3560 及以上必须先指定封装再设 trunk）
Switch(config)#interface gi0/1
Switch(config-if)#switchport trunk encapsulation dot1q
Switch(config-if)#switchport mode trunk
Switch(config-if)#switchport trunk native vlan 99
Switch(config-if)#switchport trunk allowed vlan 10,20,99
```

> **顺序陷阱**：3560 及以上平台必须先敲 `switchport trunk encapsulation dot1q` 再敲 `switchport mode trunk`，反了会报 `% Command rejected`。而 2960 只支持 dot1q，没有这条封装命令。考试里给设备型号，就是在考你这个差异。

#### 2_4.3 精细裁剪流量
```latex
Switch(config-if)#switchport trunk allowed vlan 10,20,99       ←白名单，最严格
Switch(config-if)#switchport trunk allowed vlan add 30          ←增量添加
Switch(config-if)#switchport trunk allowed vlan remove 2-9      ←增量删除
Switch(config-if)#switchport trunk allowed vlan all             ←放开全部（默认，不推荐）
```

**为什么要裁剪**：Trunk 上放行的 VLAN 越多，广播/未知单播泛洪的范围越大。一个 20 台交换机的网络，如果不裁剪，VLAN 10 的 ARP 会飞到所有交换机的所有 trunk 口。

#### 2_4.4 Native VLAN  mismatch：最常见的 trunk 故障
**两端 native VLAN 不一致时**，交换机会报 `%CDP-4-NATIVE_VLAN_MISMATCH`，且该 VLAN 的流量会"串"到对端的另一个 VLAN 里——这是 VLAN 跳跃攻击的原理之一。

```latex
   本端 native = 99        对端 native = 1（默认）
         │                        │
         └── 本端发出的无 Tag 帧 ──┘
                   │
                   ▼
        对端把它当成 VLAN 1 的帧 → 流量串到管理 VLAN
```

**修复**：两端 `switchport trunk native vlan 99` 保持一致。

#### 2_4.5 验证
```latex
Switch#show interfaces trunk

Port      Mode   Encapsulation  Status    Native vlan
Gi0/1     on     802.1q         trunking  99

Port      Vlans allowed on trunk
Gi0/1     10,20,99

Port      Vlans allowed and active in management domain
Gi0/1     10,20,99

Port      Vlans in spanning tree forwarding state and not pruned
Gi0/1     10,20,99
```

四段输出要一起看：**允许了（allowed）不等于激活（active）**，激活了不等于在转发（forwarding）。

---

### 2_5 二层安全三件套（CCNA v1.1 新增重点）
#### 2_5.1 Port-Security：一个端口只允许指定 MAC
```latex
Switch(config)#interface gi0/5
Switch(config-if)#switchport port-security
Switch(config-if)#switchport port-security maximum 2
Switch(config-if)#switchport port-security mac-address sticky   ←学到的 MAC 自动写入配置
Switch(config-if)#switchport port-security violation restrict   ←违规时丢弃并告警（不关端口）
```

三种违规动作：

| 动作 | 行为 | 适用 |
| --- | --- | --- |
| `shutdown`（默认） | 端口 err-disable | 高安全区域 |
| `restrict` | 丢弃违规帧 + 计数 + 发 SNMP trap | **生产推荐**，不中断业务 |
| `protect` | 静默丢弃，不记日志 | 极少用 |

验证：`show port-security interface gi0/5`、`show port-security address`。

#### 2_5.2 DHCP Snooping：只信任合法 DHCP 服务器
```latex
Switch(config)#ip dhcp snooping
Switch(config)#ip dhcp snooping vlan 10
Switch(config)#interface gi0/24        ←上联合法 DHCP 服务器/中继的口
Switch(config-if)#ip dhcp snooping trust
Switch(config)#interface gi0/5
Switch(config-if)#ip dhcp snooping limit rate 10   ←限速，防 DHCP 饿死攻击
```

**原理**：所有用户口默认 untrusted，只丢弃 DHCP Server 响应报文（Offer/ACK），不影响客户端请求。这样私接的路由器就无法给大家分配假网关。

验证：`show ip dhcp snooping binding`（这就是后面 DAI 的数据源）。

#### 2_5.3 DAI（动态 ARP 检测）+ IPSG
```latex
Switch(config)#ip arp inspection vlan 10        ←依赖 DHCP Snooping 绑定表
Switch(config)#interface gi0/24
Switch(config-if)#ip arp inspection trust       ←上联口要 trust
Switch(config)#interface gi0/5
Switch(config-if)#ip verify source port-security  ←IPSG：校验 IP-MAC-端口绑定
```

```latex
   三件套的依赖关系：
   DHCP Snooping（建绑定表）
            │
            ├──► DAI（校验 ARP 报文）──► 防 ARP 欺骗
            │
            └──► IPSG（校验 IP 源地址）──► 防 IP 冒充
```

> **上线顺序警告**：先配 DHCP Snooping 并确认绑定表有数据，**再**开 DAI。反过来会导致全网 ARP 不通——因为 DAI 没有绑定表可查，只能丢弃一切。

---

### 2_6 案例小故事：一台"从库房翻出来"的交换机
> 某园区网扩容，需要新增一台接入交换机。工程师小陈从库房翻出一台旧 2960，擦了配置就直接上架，插上 trunk 线。
> 三分钟后，整栋楼的 Wi-Fi 断了、办公网断了、门禁也失联了。
> 应急小组远程登录核心一看，`show vlan brief` 里只剩 VLAN 1。原来这台旧交换机的 vlan.dat 没删干净，**VTP 配置修订号是 118，远高于现网的 23**。它一接入就"反向同步"，把全网 VLAN 数据库覆盖成了它自己那套（只有 VLAN 1）。所有 access 口落到不存在的 VLAN，自然全断。
> 恢复用了 40 分钟：拔线 → 逐台改 transparent → 重建 VLAN → 逐台核对端口。
> **复盘后写进 SOP 的三条**：
> 1. 任何二手/库存设备上架前，`delete vlan.dat` + `erase startup-config` + `reload`；
> 2. 上架时 VTP 模式先设 **transparent**，确认修订号为 0 再考虑改 Server；
> 3. 生产网干脆**全 transparent**，VLAN 由自动化模板下发（见板块16）。

**现象**：全网业务瞬间中断，`show vlan brief` 只剩 VLAN 1。  
**排查**：`show vtp status` 看 Configuration Revision 是否异常跳变。  
**根因**：高修订号交换机反向覆盖 VTP 域。  
**修复**：拔线隔离 → 恢复原 VLAN 数据库 → 重建。  
**经验**：VTP 是"便利性"功能，但它的代价是**把全网的 VLAN 数据库交给了修订号最高的那台设备**。这个风险大多数人第一次遇到才知道。

---

### 2_7 场景笔记：这一章该记什么
#### 2_7.1 必记内容
1. **你的网络的 VLAN 规划表**（VLAN ID / 名称 / 网段 / 用途 / native 是否统一）——这是后面所有板块都要引用的基础表；
2. **trunk 口的 allowed VLAN 清单**，以及为什么这么裁剪；
3. `show interfaces trunk`** 的四段输出含义**（allowed / active / forwarding 三者的区别）；
4. **VTP 灾难的复现过程**——在模拟器里亲手做一次"高修订号覆盖"，比读十遍记得牢。

#### 2_7.2 实验记录模板
```latex
【实验编号】B02-01
【实验名称】VLAN 划分 + Trunk 打通 + VTP 灾难复现
【日期 / 耗时】____ / ____ 分钟
【拓扑】
   [SW1]══Trunk══[SW2]
     │              │
   PC1(V10)      PC3(V10)
   PC2(V20)      PC4(V20)
【VLAN 规划表】
  | VLAN | 名称  | 网段            | 用途     |
  | 10   | Tech  | 192.168.10.0/24 | 技术部   |
  | 20   | Sales | 192.168.20.0/24 | 销售部   |
  | 99   | Mgmt  | 192.168.99.0/24 | 管理/native |
【需求】同 VLAN 通跨 VLAN 不通
【关键配置】vlan / switchport mode access / trunk encapsulation dot1q /
          native vlan 99 / allowed vlan 10,20,99
【验证清单】
  [ ] show vlan brief 两个交换机 VLAN 一致
  [ ] show interfaces trunk 显示 Native vlan = 99（两端一致）
  [ ] PC1 ping PC3 通（同 VLAN）
  [ ] PC1 ping PC2 不通（跨 VLAN，符合预期）
  [ ] 无 %CDP-4-NATIVE_VLAN_MISMATCH 日志
  [ ] show mac address-table 能看到 PC 的 MAC 与对应 VLAN
【人为故障复现 1】
  操作：把 SW2 的 native 改成 1
  现象：日志报 NATIVE_VLAN_MISMATCH
  根因：两端 native 不一致
  修复：改回 99
【人为故障复现 2（VTP 灾难）】
  操作：给一台交换机预置高修订号（多次增删 VLAN）后接入
  现象：全网 VLAN 被清空
  定位：show vtp status 看 Configuration Revision 跳变
  修复：拔线 → transparent → 重建 VLAN
【复盘一句话】____
【遗留问题】____
```

#### 2_7.3 实用验证清单
- [ ] 能在 5 分钟内完成 4 个 VLAN 的创建与 8 个端口的批量划分；
- [ ] 能说出 `switchport host` 等价于哪三条命令；
- [ ] 能解释为什么 3560 上 `switchport mode trunk` 会报 rejected；
- [ ] 能不查资料说出 VTP 三种模式的"能否创建/是否同步/是否转发"；
- [ ] 已亲手写过一次 Port-Security + DHCP Snooping 的组合配置。

---

### 2_8 进阶延伸
1. **Voice VLAN**：`switchport voice vlan 150`，让 IP 电话与 PC 共用一个物理口但分属不同 VLAN（PC 走 access VLAN，电话走 voice VLAN，带 802.1p 标记）；
2. **Private VLAN**：同一子网内进一步隔离（isolated / community），常用于酒店、数据中心多租户；
3. **802.1X**：端口级准入认证，与 ISE 联动，从"MAC 绑定"升级为"身份绑定"（CCNP 重点，见板块10、16）；
4. **VLAN 与自动化**：用 Ansible 的 `ios_vlan` 资源模块批量下发 VLAN，彻底摆脱 VTP（见板块16）。

---

## 板块3 · 生成树与链路聚合 — STP / RSTP / EtherChannel
> 一句话定位：**冗余链路是高可用之本，也是二层环路之源。** 生成树负责"防环"，链路聚合负责"让冗余链路别闲着"。

---

### 3_0 本板块知识地图
```latex
           冗余带来环路                     STP 的解法：逻辑阻塞
    ┌─────┐        ┌─────┐              ┌─────┐        ┌─────┐
    │ SW1 │════════│ SW2 │              │ SW1 │════════│ SW2 │
    └──┬──┘        └──┬──┘              └──┬──┘        └──┬──┘
       │              │                    │              │
       ╰──────────────╯                    ╰──────X───────╯
        广播帧无限循环                        逻辑上剪断一条
        MAC 表反复漂移                        故障时才打开
        CPU 几秒内打满

                       EtherChannel 的思路：把多条"合成"一条
    ┌─────┐  gi0/1 ┐                   ┌─────┐
    │ SW1 │────────┤ Port-Channel 1 ───│ SW2 │  STP 视为单链路
    └─────┘  gi0/2 ┘                   └─────┘  带宽叠加、无阻塞口

   协议演进：802.1D（30–50 秒）→ RSTP/802.1w（秒级）→ MST/802.1s（多 VLAN 合一）
   接入端口三件套：PortFast + BPDU Guard + Root/Loop Guard
```

---

### 3_1 为什么必须有 STP
二层没有 TTL 字段。一旦存在物理环路，一个广播帧会在环路里**无限循环并被不断泛洪复制**，几秒内就能打满带宽、耗尽交换机 CPU——这就是**广播风暴**。同时交换机的 MAC 表会在不同端口间反复"漂移"，导致单播帧也被错误转发。

STP 的解法：**在保留物理冗余的前提下，逻辑上阻塞某条链路**，把拓扑修剪成一棵无环的树；当活动链路故障时，被阻塞的链路自动打开。

> **为什么二层不能有 TTL**：IP 包头有 TTL，每过一跳减 1，到 0 就丢弃，所以三层环路只是"慢"，不会死。以太网帧头里没有这个字段，一个广播帧可以在环路里永远转下去，而且每转一圈就被复制一次。**这是二层最危险的地方，也是 STP 存在的全部理由。**

---

### 3_2 802.1D STP 的选举三步
| 步骤 | 选举内容 | 判定规则 |
| --- | --- | --- |
| 第1步 **选根桥** | 全网一个根 | Bridge ID 最小者胜（优先级 + MAC；默认优先级 32768，步长 4096） |
| 第2步 **选根端口 RP** | 每台非根交换机一个 | 到达根桥累计路径开销最小；相同则比上级交换机 BID；再相同比端口 ID |
| 第3步 **选指定端口 DP** | 每段链路一个 | 该网段上到达根桥开销最小的端口；**其余端口进入 Blocking** |

#### 3_2.1 端口状态与收敛时间
| 状态 | 行为 | 默认停留 |
| --- | --- | --- |
| Blocking | 只收 BPDU，不转发数据 | Max Age 20s |
| Listening | 构建拓扑，不学 MAC | Forward Delay 15s |
| Learning | 学 MAC，不转发 | Forward Delay 15s |
| Forwarding | 正常转发 | — |
| Disabled | 管理性关闭 | — |

**从阻塞到转发最长约 50 秒（20+15+15）**，这正是"接上网线要等半分钟才能上网"的原因，也是 RSTP 存在的理由。

#### 3_2.2 路径开销（按速率）
| 链路速率 | 传统 cost（802.1D） | 现代 cost（802.1w 长格式） |
| --- | --- | --- |
| 10 Mbps | 100 | 2 000 000 |
| 100 Mbps | 19 | 200 000 |
| 1 Gbps | 4 | 20 000 |
| 10 Gbps | 2 | 2 000 |

> **易混点**：考试与实验里最常见的是**传统 cost**（10M=100、100M=19、1G=4）；OSPF 的 cost 计算口径不同（见板块6），两者**不要混淆**。

#### 3_2.3 选举过程可视化
```latex
   SW-A (BID 优先级 32768, MAC 0000.0000.1111)
   SW-B (BID 优先级 32768, MAC 0000.0000.2222)
   SW-C (BID 优先级 32768, MAC 0000.0000.3333)

   第1步 选根桥：优先级相同 → 比 MAC → SW-A 的 MAC 最小 → SW-A 为根桥

   第2步 每台非根选一个根端口（到根累计 cost 最小）
      SW-B：直连 SW-A 的口 cost=19 → 该口为 RP
      SW-C：直连 SW-A 的口 cost=19 → 该口为 RP

   第3步 每段链路选一个指定端口
      SW-A—SW-B 段：SW-A 侧（离根更近）→ DP
      SW-B—SW-C 段：两侧到根 cost 相同 → 比 BID → SW-B 侧 → DP
                    → SW-C 侧端口进入 Blocking
```

---

### 3_3 从 STP 到 RSTP：收敛从 50 秒到秒级
| 特性 | STP（802.1D） | RSTP（802.1w） |
| --- | --- | --- |
| 状态 | 5 个（Blocking/Listening/Learning/Forwarding/Disabled） | 3 个（Discarding/Learning/Forwarding） |
| 收敛 | 约 30–50 秒 | 通常 1 秒内（点到点链路） |
| 端口角色 | RP / DP / 非指定 | 增加 **Alternate**（根端口备份）与 **Backup**（指定端口备份） |
| BPDU 处理 | 只有根桥发，逐级转发 | 所有交换机自主每 Hello 发送 |
| Cisco 实现 | PVST+ | **Rapid-PVST+（Catalyst 默认）** |

```latex
Switch(config)#spanning-tree mode rapid-pvst
Switch#show spanning-tree summary
```

#### 3_3.1 加速与防护三件套（接入端口标配）
```latex
Switch(config-if)#spanning-tree portfast                    ←接终端，直接进入 Forwarding
Switch(config-if)#spanning-tree bpduguard enable            ←收到 BPDU 立即 err-disable（防私接交换机）
Switch(config)#spanning-tree portfast bpduguard default     ←全局对所有 portfast 口生效
Switch(config)#errdisable recovery cause bpduguard          ←允许自动恢复
Switch(config)#errdisable recovery interval 300             ←5 分钟后自动恢复
```

| 特性 | 作用 | 典型部署位置 |
| --- | --- | --- |
| **PortFast** | 跳过 Listening/Learning | 接 PC、服务器、打印机的 access 口 |
| **BPDU Guard** | 收到 BPDU 就关端口 | 同上，防止用户私接交换机造成环路 |
| **Root Guard** | 阻止本端口成为根端口 | 接入层下联口，保护根桥位置 |
| **Loop Guard** | 单向链路时不误转为 Forwarding | 光纤上联链路 |
| **UDLD** | 检测单向光纤（能收不能发） | `udld aggressive`，光纤链路必配 |

> **PortFast 的边界**：它只应在**接终端**的口上开。如果在交换机互联口上开 PortFast，等于绕过 STP 的环路检测——一旦有物理环路，立刻广播风暴。**开 PortFast 前先问一句：这个口对面是终端还是网络设备？**

---

### 3_4 实战：STP 负载分担
默认 STP 只留一条活动路径，另一条只能干等。利用 **PVST+ 每 VLAN 一棵树**的特性，可以让不同 VLAN 走不同上行链路。

实现负载分担有两种手段：

```latex
! 方案一：调端口优先级（值越小越优先，默认 128，范围 0-240，步长 16）
Switch_1(config)#interface fa0/1
Switch_1(config-if)#spanning-tree vlan 8,9,10 port-priority 10
Switch_1(config)#interface fa0/2
Switch_1(config-if)#spanning-tree vlan 3,4,5,6 port-priority 10

! 方案二：调路径开销（cost 越小路径越优）
Switch_1(config)#interface fa0/1
Switch_1(config-if)#spanning-tree vlan 2,3,4 cost 30
Switch_1(config)#interface fa0/2
Switch_1(config-if)#spanning-tree vlan 8,9,10 cost 30
```

**效果解读**：

+ 方案一让 VLAN 8-10 在 fa0/1 上优先级更高 → fa0/1 对它们而言是 Forwarding；VLAN 3-6 走 fa0/2；
+ 方案二让 VLAN 2-4 在 fa0/1 上的 cost 变成 30（变差）→ 这些 VLAN 改走 fa0/2；VLAN 8-10 相反；
+ 两条上行链路都承担流量，任一故障时另一条全部接管。

#### 3_4.1 更常用的做法：直接指定每个 VLAN 的根桥
```latex
! 核心交换机A：VLAN 10/20 的主根，VLAN 30/40 的备根
CoreA(config)#spanning-tree vlan 10,20 priority 4096
CoreA(config)#spanning-tree vlan 30,40 priority 8192

! 核心交换机B：反过来
CoreB(config)#spanning-tree vlan 30,40 priority 4096
CoreB(config)#spanning-tree vlan 10,20 priority 8192
```

比逐端口调参更清晰，一眼能看出"哪个 VLAN 走哪台核心"。

#### 3_4.2 设计要点（板块9 会再用到）
**三层网关（HSRP Active）应与该 VLAN 的 STP 根桥落在同一台设备**，否则流量会白白绕行。

```latex
   错误设计：                            正确设计：
   VLAN10 的 STP 根 = CoreA              两者都在 CoreA
   VLAN10 的 HSRP Active = CoreB
        │                                     │
        ▼                                     ▼
   流量绕行 CoreA→CoreB→上行              流量直接 CoreA→上行
```

---

### 3_5 EtherChannel：让冗余链路全部参与转发
**STP 的思路是"堵"，EtherChannel 的思路是"合"**——把多条物理链路绑成一条逻辑链路，STP 视为单链路，于是没有端口被阻塞，带宽叠加，且具备冗余。

#### 3_5.1 三种协商模式
| 协议 | 模式 | 说明 |
| --- | --- | --- |
| **LACP（标准 802.3ad）** | `active` / `passive` | 跨厂商通用，**生产首选** |
| **PAgP（Cisco 私有）** | `desirable` / `auto` | 仅 Cisco 设备之间 |
| **静态** | `on` | 不做协商，两端都必须 on；配错易出问题 |

**组合规则**：

```latex
active + active     ✅
active + passive    ✅
passive + passive   ❌（都不主动）
on + on             ✅
on + LACP           ❌（协议不同，无法协商）
```

#### 3_5.2 配置（二层 EtherChannel）
```latex
Switch(config)#interface range gi0/1-2
Switch(config-if-range)#switchport mode trunk
Switch(config-if-range)#switchport trunk allowed vlan 10,20,99
Switch(config-if-range)#channel-group 1 mode active       ←物理口加入通道组 1
Switch(config-if-range)#exit
Switch(config)#interface port-channel 1                   ←在逻辑口上配 trunk 参数
Switch(config-if)#switchport mode trunk
Switch(config-if)#switchport trunk allowed vlan 10,20,99
Switch(config)#port-channel load-balance src-dst-ip       ←负载均衡算法
```

> **配置顺序陷阱**：先配物理口还是先配 port-channel？稳妥做法是**先把物理口全部 shutdown，加入 channel-group，再配 port-channel 逻辑口，最后统一 no shutdown**。否则两端协商不一致时会出现部分口被 err-disable。

#### 3_5.3 负载均衡算法怎么选
| 算法关键字 | 依据 | 适用 |
| --- | --- | --- |
| `src-dst-ip` | 源+目的 IP | **通用推荐** |
| `src-dst-mac` | 源+目的 MAC | 二层环境 |
| `src-dst-port` | 源+目的四层端口 | 少量主机、多会话 |

> 注意：EtherChannel **不会**把单个流拆开跑多条链路。一个 10G 的文件传输仍然只走一条物理链路——它提升的是**多流并发总带宽**，不是单流速度。这是面试高频追问点。

#### 3_5.4 验证
```latex
Switch#show etherchannel summary

Flags:  D - down        P - bundled in port-channel
        I - stand-alone s - suspended
        (SU) - Layer2  (P) - in port-channel

Group  Port-channel  Protocol    Ports
------+-------------+-----------+--------------------------------
1      Po1(SU)       LACP        Gi0/1(P)   Gi0/2(P)
```

看到 `Po1(SU)` 且两个口都是 `(P)`，才算真正绑定成功。若显示 `(I)`（stand-alone）说明没协商上。

---

### 3_6 案例小故事：会议室网口引发的"全网瘫痪"
> 某公司例会，十几个人带笔记本进会议室，发现墙上只有一个网口。行政同事从工位顺手拿了个八口小交换机接上，大家纷纷插线。
> 五分钟后，整层楼网络变慢，随后彻底不通。
> 网管到场时，所有交换机指示灯在疯狂同步闪烁——典型的广播风暴特征。他拔掉会议室那根线，网络十秒内恢复。
> **根因**：小交换机被接上网口后，有人把网线**两头都插在了同一个小交换机上**（一根线从墙口接入，另一根接回墙口），形成物理环路。而那个办公室网口**没开 BPDU Guard**，STP 虽然会阻塞环路，但廉价小交换机不透传 BPDU，STP 根本"看不见"它，环路在 STP 域外形成，风暴直接灌进上层网络。
> **整改三条**：
> 1. 所有接入端口全局开启 `spanning-tree portfast bpduguard default`；
> 2. 接入端口开 `switchport port-security maximum 3`（一个口后面挂十台设备立刻告警）；
> 3. 会议室统一改为 AP 覆盖，减少墙口私接需求。
> **复盘**：这次故障的真正教训不是"STP 没配"，而是**STP 只能保护它看得见的设备**。对于不透传 BPDU 的廉价交换机，唯一的防线是 BPDU Guard + Port-Security 的组合。

**现象**：全网变慢后不通，交换机灯同步狂闪。  
**排查**：`show interfaces` 看广播包计数是否爆增；`show processes cpu` 看 CPU 是否被中断占满。  
**根因**：STP 域外物理环路，廉价交换机不透传 BPDU。  
**修复**：拔线 + 全局 BPDU Guard + Port-Security 限制 MAC 数。  
**经验**：风暴类故障的现场特征是"**所有灯一起闪**"，看到这个先拔最近新增的线。

---

### 3_7 场景笔记：这一章该记什么
#### 3_7.1 必记内容
1. **你的网络里每个 VLAN 的根桥是谁**——`show spanning-tree vlan 10` 里的 Root ID，抄成一张表；
2. **每个阻塞口的位置及原因**——"为什么是它"，能说出来才算懂；
3. **50 秒收敛的实测值**——在模拟器里 shutdown 一个口，用长 ping 测实际中断时长，记下数字；
4. **EtherChannel 的协商组合表**——背下 active/passive/on 的五种组合。

#### 3_7.2 实验记录模板
```latex
【实验编号】B03-01
【实验名称】STP 根桥控制 + EtherChannel 绑定
【日期 / 耗时】____ / ____ 分钟
【拓扑】
    ┌────────┐  gi0/1 ══  ┌────────┐
    │  SW-A  │  gi0/2 ══  │  SW-B  │   （双链路）
    └────────┘            └────────┘
【需求】
  - SW-A 做 VLAN10 根桥，SW-B 做 VLAN20 根桥
  - 两条链路绑成 EtherChannel，无阻塞口
【关键配置】
  spanning-tree mode rapid-pvst
  spanning-tree vlan 10 priority 4096
  channel-group 1 mode active / port-channel load-balance src-dst-ip
【预期结果】
  - show spanning-tree 每个 VLAN 的 Root ID 符合设计
  - show etherchannel summary 显示 Po1(SU)，两口都是 (P)
  - show spanning-tree 中无 Blocking 端口（被 EtherChannel 合并）
【实际结果】贴真实输出（重点看 Root ID 与 Port 角色）
【验证清单】
  [ ] show spanning-tree vlan 10 → This bridge is the root
  [ ] show spanning-tree summary → 模式为 rapid-pvst
  [ ] show etherchannel summary → Po1(SU)，Gi0/1(P) Gi0/2(P)
  [ ] 断开 gi0/1 后业务不中断（长 ping 观察丢包数）
  [ ] 恢复 gi0/1 后自动重新加入（无 flapping）
【人为故障复现 1】
  操作：一端 active 一端 passive 之外的错误组合（passive+passive）
  现象：Po1 显示 (I) stand-alone
  根因：双方都不主动发 LACP
  修复：至少一端改 active
【人为故障复现 2（风暴）】
  操作：两根线交叉插同一交换机，接入未开 BPDU Guard 的口
  现象：广播风暴，CPU 飙升
  根因：STP 域外环路
  修复：拔线 + 全局 bpduguard default
【收敛实测】shutdown 一条链路 → 长 ping 丢包 ____ 个，恢复耗时 ____ 秒
【复盘一句话】____
【遗留问题】____
```

#### 3_7.3 实用验证清单
- [ ] 能不查资料说出 STP 选举三步及每步的 tie-breaker；
- [ ] 能解释"为什么要等 50 秒"以及 RSTP 为什么快；
- [ ] 能说出 PortFast 与 BPDU Guard 的区别，以及为什么必须成对使用；
- [ ] 能独立配置 LACP EtherChannel 并证明它工作；
- [ ] 已亲手制造过一次广播风暴（模拟器内），并写出处置步骤。

---

### 3_8 进阶延伸
#### 3_8.1 MST（多实例生成树）——CCNP 必考
**为什么需要 MST**：PVST+ 是"每 VLAN 一棵树"，200 个 VLAN 就要维护 200 棵 STP 实例、发送 200 份 BPDU。**MST 把多个 VLAN 映射到同一个实例**，比如 200 个 VLAN 只跑 2 个实例，BPDU 数量直接降到 1/100。

```latex
! 同一 MST 区域内所有交换机的配置必须完全一致（配置名、修订号、VLAN 映射表）
Switch(config)#spanning-tree mode mst
Switch(config)#spanning-tree mst configuration
Switch(config-mst)#name REGION-A                 ←第1步配置名
Switch(config-mst)#revision 1                    ←第2步修订号
Switch(config-mst)#instance 1 vlan 10,20,30      ←第3步实例 1 承载 VLAN 10/20/30
Switch(config-mst)#instance 2 vlan 40,50,60      ←第4步实例 2 承载 VLAN 40/50/60
Switch(config-mst)#exit
Switch(config)#spanning-tree mst 1 priority 4096 ←本交换机作为实例 1 的根
Switch(config)#spanning-tree mst 2 priority 8192 ←作为实例 2 的备根
```

**MST 的三条铁律**：

1. **区域四要素必须一致**：配置名（name）、修订号（revision）、VLAN→实例映射表、MST 模式。任一不一致，两台交换机就不在同一个 MST 区域，会被当成不同的"区域边界"；
2. **未映射的 VLAN 默认落在 IST（Instance 0）**——不要忘了 IST 也是一棵树，也需要规划根桥；
3. **改完映射表要 **`exit`** 才会生效**，且修订号要手动 +1（部分 IOS 会自动提示）。

验证：

```latex
Switch#show spanning-tree mst configuration      ←看区域名、修订号、VLAN 映射
Switch#show spanning-tree mst 1                  ←看实例 1 的根桥与端口角色
Switch#show spanning-tree mst configuration digest  ←★对比全网 digest 是否一致
```

> **排错捷径**：MST 区域没合并时，第一件事是比较两台设备的 **配置摘要（digest）**。digest 不同 = 映射表或区域名不一致，交换机根本不认为彼此是同区域成员。

**与 PVST+ 的互操作**：MST 区域对外表现为一台"虚拟交换机"，通过 IST 与外部的 PVST+/CST 域对接。混合组网时，MST 区域的根桥必须是**区域边界上能与外部 CST 根通信的那台**，否则会出现次优路径。

**其他进阶方向**：

2. **堆叠与跨设备链路聚合**：StackWise / VSS / vPC，把两台物理设备"合成"一台逻辑设备，**从根本上消除 STP 阻塞口**（CCNP/CCIE 重点）；
3. **Loop Guard 与 UDLD 的配合使用**：光纤单向链路场景下，两者定位不同——UDLD 检测物理层单向，Loop Guard 防止逻辑上误转 Forwarding；
4. **STP 与自动化校验**：用 Ansible 采集 `show spanning-tree` 并断言"根桥必须是 CoreA"，把设计约束变成可执行的检查（见板块16）。

---

## 板块4 · VLAN 间路由 — 单臂路由与三层交换 SVI
> 一句话定位：**VLAN 把网络切开，三层设备决定它们能不能、以及多快地重新连起来。** 本板块把"两种方案各做一遍"升级为"知道什么时候该用哪一种"。

---

### 4_0 本板块知识地图
```latex
   方案A 单臂路由                       方案B 三层交换 SVI
   ┌──────────┐                        ┌──────────────────┐
   │  Router  │                        │ 三层交换机 (3560) │
   │ f0/0.1 ──┼── VLAN2 网关            │  SVI VLAN2 ───── │ 网关 .1
   │ f0/0.2 ──┼── VLAN3 网关            │  SVI VLAN3 ───── │ 网关 .1
   └────┬─────┘                        └────────┬─────────┘
        │ 一条 trunk                            │ 内部硬件转发
        ▼                                       ▼
   ┌──────────┐                        ┌──────────────────┐
   │ Switch   │                        │  二层接入交换机    │
   │ V2 │ V3  │                        └──────────────────┘
   └──────────┘
   进出都挤一条链路                      一次路由，多次交换（ASIC）
```

---

### 4_1 三种实现 VLAN 间互通的方案
| 方案 | 连接方式 | 优点 | 缺点 | 适用场景 |
| --- | --- | --- | --- | --- |
| **多物理接口** | 每个 VLAN 一条线接到路由器一个物理口 | 概念最简单 | 消耗大量路由器接口，扩展性极差 | 仅教学演示 |
| **单臂路由（Router-on-a-Stick）** | 一条 trunk 上联，路由器用子接口做各 VLAN 网关 | 省接口、成本低 | 所有跨 VLAN 流量挤一条链路；软件转发 | VLAN 少、流量小的分支/实验室 |
| **三层交换 SVI** | 三层交换机为每个 VLAN 建交换虚拟接口（SVI） | 硬件转发、线速、微秒级延迟 | 设备成本较高 | **园区网、数据中心主流方案** |

#### 4_1.1 "一次路由，多次交换"
三层交换机对同一条流的**第一个包**做路由查表，随后生成硬件转发表项（CEF/MLS），后续同流报文直接由 **ASIC 交换**，不再走路由引擎。这是它比单臂路由快一个数量级的根本原因。

```latex
   第一个包：查路由表 → 生成 CEF/MLS 表项 → 转发（走路由引擎，慢）
   后续包  ：命中硬件表项 → 直接由 ASIC 交换（走硬件，线速）

   所以：ping 的第一个包慢（毫秒级），后续包快（微秒级）
```

#### 4_1.2 方案决策矩阵（这是本板块的核心产出）
| 判断维度 | 选单臂路由 | 选三层交换 SVI |
| --- | --- | --- |
| VLAN 数量 | ≤ 4 | > 4 |
| 跨 VLAN 流量占比 | 低于上行带宽的 20% | 超过上行带宽的 40% |
| 是否已有闲置路由器 | 是 | 否 |
| 预算 | 紧张 | 允许采购三层交换机 |
| 未来扩展 | 基本不变 | 会持续增加 VLAN |
| 延迟敏感度 | 普通办公 | 语音/视频/数据库 |

> **一句话决策**：分支小站点用单臂路由省钱；园区网核心一律三层交换。**判断标准是"跨 VLAN 流量会不会把那条 trunk 打满"**。

---

### 4_2 方案一：单臂路由实战
**场景**：技术部（VLAN 2，192.168.1.0/24）与销售部（VLAN 3，192.168.2.0/24）需要互通，只有一台 Router_2811 与一台 Switch_2960。

#### 4_2.1 交换机侧
```latex
Switch>en
Switch#conf t
Switch(config)#vlan 2
Switch(config-vlan)#exit
Switch(config)#vlan 3
Switch(config-vlan)#exit
Switch(config)#int fa 0/2
Switch(config-if)#switchport access vlan 2        ←PC1（技术部）
Switch(config-if)#exit
Switch(config)#int fa 0/3
Switch(config-if)#switchport access vlan 3        ←PC2（销售部）
Switch(config-if)#exit
Switch(config)#int fa 0/1
Switch(config-if)#switchport mode trunk           ←上联路由器的口必须是 trunk
Switch(config-if)#end
Switch#show vlan brief
```

#### 4_2.2 路由器侧（核心：子接口 + dot1q 封装）
```latex
Router>en
Router#conf t
Router(config)#int fa 0/0
Router(config-if)#no shutdown                     ←主接口必须打开，子接口才能 up
Router(config-if)#exit
Router(config)#int fa 0/0.1
Router(config-subif)#encapsulation dot1q 2        ←子接口号 .1 ≠ VLAN 号，靠这条命令绑定 VLAN 2
Router(config-subif)#ip address 192.168.1.1 255.255.255.0
Router(config-subif)#exit
Router(config)#int fa 0/0.2
Router(config-subif)#encapsulation dot1q 3        ←绑定 VLAN 3
Router(config-subif)#ip address 192.168.2.1 255.255.255.0
Router(config-subif)#end
Router#show ip route

C    192.168.1.0/24 is directly connected, FastEthernet0/0.1
C    192.168.2.0/24 is directly connected, FastEthernet0/0.2
```

**三个最容易错的点**：

1. **主接口必须 **`no shutdown`——子接口依赖主接口物理状态；
2. **子接口号与 VLAN 号无需一致**，靠 `encapsulation dot1q {vlan-id}` 绑定（建议做成一致，减少认知负担）；
3. **忘了 **`encapsulation`** 就配 IP** → 报 `% Configuring IP routing on a LAN subinterface is only allowed if that subinterface is already configured as part of an IEEE 802.10, IEEE 802.1Q, or ISL vLAN.`

#### 4_2.3 数据流向逐跳拆解（理解单臂路由的关键）
```latex
1. PC1(192.168.1.2) 判断目标 192.168.2.2 不在本网段 → 把包发给网关 192.168.1.1
2. 交换机从 access 口收到无 Tag 帧，内部标记 VLAN2，
   查 MAC 表从 trunk 口 fa0/1 发出，插入 802.1Q Tag=2
3. 路由器子接口 fa0/0.1 识别 Tag2，解封装，
   查路由表发现 192.168.2.0/24 直连在 fa0/0.2
4. 从 fa0/0.2 发出时重新打上 Tag=3，经同一条物理链路回送交换机
5. 交换机按 Tag3 转发到 fa0/3，剥掉 Tag 交给 PC2
```

> **注意**：进出都走同一条物理链路，所以 **trunk 带宽是所有跨 VLAN 流量的共享上限**——这就是单臂路由的性能天花板。

#### 4_2.4 测试结果解读（真实输出）
```latex
PC>ping 192.168.2.2

Request timed out.                                    ←第一个包超时
Reply from 192.168.2.2: bytes=32 time=20ms TTL=127
Reply from 192.168.2.2: bytes=32 time=22ms TTL=127
Reply from 192.168.2.2: bytes=32 time=23ms TTL=127

Ping statistics for 192.168.2.2:
    Packets: Sent = 4, Received = 3, Lost = 1 (25% loss)
```

**首包超时不是故障，是 ARP 解析**：PC1 要先解析网关 MAC，等待期间该 ICMP 包被丢弃；第二次 ping 全通。

**TTL=127 说明经过 1 跳三层设备**（Windows 初始 TTL=128，每经过一台三层设备减 1）。这是判断"数据包走了几跳"的免费探针：

```latex
发起端初始 TTL    →  收到的 TTL  →  经过的三层设备数
Windows: 128          127             1 跳
Linux/网络设备: 64    63              1 跳
```

> 考试与面试常考：**"首包丢包" ≠ 网络有问题，判断依据是第二次 ping 是否 0 丢包。** OSPF、NAPT 实验中同样会出现。

---

### 4_3 方案二：三层交换 SVI 实战
**场景**：2960 二层接入 + 3560 三层核心；PC1/PC3 属 VLAN 2（192.168.1.0/24），PC2 属 VLAN 3（192.168.2.0/24）。

#### 4_3.1 地址规划
| 设备 | IP | 子网掩码 | 网关 |
| --- | --- | --- | --- |
| PC1 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1（SVI VLAN 2） |
| PC3 | 192.168.1.3 | 255.255.255.0 | 192.168.1.1 |
| PC2 | 192.168.2.2 | 255.255.255.0 | 192.168.2.1（SVI VLAN 3） |

#### 4_3.2 二层交换机（2960）
```latex
Switch>en
Switch#conf t
Switch(config)#vlan 2
Switch(config-vlan)#exit
Switch(config)#vlan 3
Switch(config-vlan)#exit
Switch(config)#int fa 0/2
Switch(config-if)#switchport access vlan 2
Switch(config-if)#int fa 0/3
Switch(config-if)#switchport access vlan 3
Switch(config-if)#int fa 0/1
Switch(config-if)#switchport mode trunk          ←上联三层核心
Switch(config-if)#end
```

#### 4_3.3 三层交换机（3560）
```latex
Switch>en
Switch#conf t
Switch(config)#hostname CoreSW
CoreSW(config)#vlan 2
CoreSW(config-vlan)#exit
CoreSW(config)#vlan 3
CoreSW(config-vlan)#exit
CoreSW(config)#ip routing                        ←★ 最关键的一条，缺它一切白搭
CoreSW(config)#interface vlan 2
CoreSW(config-if)#ip address 192.168.1.1 255.255.255.0
CoreSW(config-if)#no shutdown
CoreSW(config-if)#interface vlan 3
CoreSW(config-if)#ip address 192.168.2.1 255.255.255.0
CoreSW(config-if)#no shutdown
CoreSW(config-if)#end
CoreSW#show ip route
```

#### 4_3.4 SVI 起不来的三个常见原因
| 现象 | 原因 | 修复 |
| --- | --- | --- |
| SVI 状态 down/down | 该 VLAN 在交换机上不存在，或无任何活动端口 | 创建 VLAN 并确保至少一个 access/trunk 口处于 up |
| SVI up/down | 老平台缺少 `no shutdown` | SVI 下敲 `no shutdown` |
| 配了 SVI 但跨 VLAN 不通 | **没开 **`ip routing` | 全局 `ip routing` |

> **SVI 的 up 条件**：VLAN 必须存在，且该 VLAN 至少有一个 **up 状态**的二层端口（access 或 trunk）。如果 VLAN 10 里没有任何活动端口，`interface vlan 10` 就是 down 的——这是"配了 SVI 却不生效"的头号原因。

#### 4_3.5 三层交换 vs 单臂路由：一份可粘贴的对照
```latex
! 单臂路由（路由器侧）
interface fa0/0
 no shutdown
interface fa0/0.1
 encapsulation dot1q 2
 ip address 192.168.1.1 255.255.255.0

! 三层交换（交换机侧）
ip routing
vlan 2
interface vlan 2
 ip address 192.168.1.1 255.255.255.0
 no shutdown
```

---

### 4_4 案例小故事：一条 `ip routing`，全网通了
> 园区网割接换新核心（一台三层交换机），配置一条条敲完：VLAN 建了、trunk 通了、SVI 地址配了、`show ip route` 里两条直连路由都在。
> 但 PC 之间就是 ping 不通。
> 大家开始怀疑：是不是 trunk 没放行 VLAN？是不是 STP 阻塞了？是不是光模块有问题？四十分钟过去，有人已经准备回滚了。
> 带队的师傅这时做了一件事：他没有继续猜，而是**回到"三层设备凭什么转发"这个基本问题**。三层交换机出厂默认是二层交换机——它不会在 VLAN 之间转发，**除非你明确打开 IP 路由**。
> 一秒钟后，全楼恢复。
> **复盘**：
> + **现象**：`show ip route` 有路由，但数据不通；
> + **根因**：未开启 IP 路由转发，三层交换机只做二层交换，跨 VLAN 数据包被丢弃；
> + **修复**：`ip routing`；
> + **经验**：**控制平面与数据平面必须分开验证。路由表正确 ≠ 转发正常。** 路由表是"控制平面"的产物，转发是"数据平面"的行为，两者可能不一致。这条经验会贯穿后面所有板块。

```latex
CoreSW(config)#ip routing
```

**同类陷阱清单**（"有路由但不通"的其他可能）：

1. 三层交换机未开 `ip routing`；
2. interface 是 `shutdown` 状态；
3. ACL 拦在 SVI 上；
4. 对端没有回程路由（单向可达）；
5. ARP 表项缺失（下一跳不可达）。

---

### 4_5 场景笔记：这一章该记什么
#### 4_5.1 必记内容
1. **TTL 判读技巧**：`TTL=127` 意味着什么；不同操作系统的初始 TTL；
2. **"首包超时"的判据**：第二次 ping 是否 0 丢包；
3. `ip routing`** 这个坑**：写在笔记第一页，每次配三层交换机先敲；
4. **你的网络的方案选型理由**：为什么这里用 SVI 而不是单臂路由，把决策卡（板块0 模板）填好。

#### 4_5.2 实验记录模板
```latex
【实验编号】B04-01
【实验名称】单臂路由 + 三层交换 SVI 双方案对比
【日期 / 耗时】____ / ____ 分钟
【拓扑】（两个拓扑各画一张 ASCII 图）
【地址规划】
  | 设备 | IP          | 掩码          | 网关        | VLAN |
  | PC1  | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 | 2    |
  | PC2  | 192.168.2.2 | 255.255.255.0 | 192.168.2.1 | 3    |
【需求】VLAN2 与 VLAN3 互通；两种方案都要跑通
【关键配置】
  单臂：encapsulation dot1q 2 / 主接口 no shutdown
  SVI ：ip routing / interface vlan 2 / no shutdown
【预期结果】
  - 两种方案下 PC1 都能 ping 通 PC2
  - 第二次 ping 0 丢包
  - TTL = 127（Windows）
【实际结果】贴真实 ping 输出（含首包超时那一行，不要删）
【验证清单】
  [ ] show ip route 有两条直连（或 SVI 的两条 C）
  [ ] 单臂：show vlans / show ip int brief 子接口 up/up
  [ ] SVI：show ip interface brief 里 Vlan2、Vlan3 都是 up/up
  [ ] 第二次 ping 0 丢包
  [ ] TTL 值符合预期（记录实际值：____）
  [ ] show mac address-table 能看到两台 PC 的 MAC
【人为故障复现 1】
  操作：SVI 方案下 no ip routing
  现象：ping 全丢，但 show ip route 仍有直连路由
  根因：控制平面有路由，数据平面不转发
  修复：ip routing
  ★ 这条要重点记：路由表对 ≠ 能通
【人为故障复现 2】
  操作：删掉子接口的 encapsulation dot1q
  现象：子接口 down，路由消失
  根因：子接口无 VLAN 绑定
  修复：补回 encapsulation
【TTL 实测记录】
  从 PC1 ping PC2 收到 TTL = ____
  推断经过 ____ 跳三层设备
【复盘一句话】____
【遗留问题】____
```

#### 4_5.3 实用验证清单
- [ ] 能独立配通单臂路由，并解释子接口号与 VLAN 号的关系；
- [ ] 能独立配通三层交换 SVI，并说出 SVI up 的两个必要条件；
- [ ] 看到 `TTL=127` 能立刻说出"经过 1 跳"；
- [ ] 能说出单臂路由的性能瓶颈在哪，以及什么场景仍然该用它；
- [ ] 亲手复现过"有路由但不通"的故障，并知道排查顺序。

---

### 4_6 进阶延伸
1. **三层交换机上跑路由协议**：SVI 就是普通三层接口，可以直接 `network` 进 OSPF（见板块6 的 S3560 实战）；
2. **SVI + HSRP**：多个 SVI 各配一个 HSRP 组，实现网关冗余（见板块9）；
3. **DHCP 中继**：SVI 下 `ip helper-address` 指向 DHCP 服务器（见板块12）；
4. **VRF-Lite 下的 SVI**：把不同 VLAN 放进不同 VRF 做租户隔离（CCNP，见板块16）；
5. **性能验证**：用 `show interfaces vlan 2` 看转发包速率，或用 NetFlow 观察跨 VLAN 流量占比，验证选型是否合理。

---

## 板块5 · IP 路由基础与静态路由
> 一句话定位：**路由表是路由器的"地图"，静态路由是地图上手画的第一条线。**

---

### 5_0 本板块知识地图
```latex
    数据包到达路由器
          │
          ▼
   查路由表（三条规则依次生效）
          │
   第1步 最长前缀匹配  ── /24 胜过 /16，默认路由 /0 永远最后
          │
   第2步 管理距离 AD   ── 不同协议之间比"可信度"，越小越可信
          │
   第3步 度量值 Metric ── 同一协议内比"代价"，越小越优；相等则负载均衡
          │
          ▼
   确定出接口 + 下一跳 → 转发
```

---

### 5_1 路由表五要素：看懂一张路由表才算入门
```latex
O    192.168.4.0/24 [110/65] via 192.168.3.2, 00:01:00, Vlan20
S    192.168.2.0/24 [1/0] via 192.168.3.2
C    192.168.1.0/24 is directly connected, FastEthernet1/0
```

| 字段 | 示例 | 含义 |
| --- | --- | --- |
| 路由来源标记 | `O` / `S` / `C` | O=OSPF、S=静态、C=直连、R=RIP、D=EIGRP、B=BGP、i=IS-IS |
| 目标网络/掩码 | 192.168.4.0/24 | 要去的目的网段 |
| [管理距离/度量值] | [110/65] | 110 是 OSPF 默认管理距离；65 是累计 cost |
| 下一跳 | via 192.168.3.2 | 数据包交给谁 |
| 出接口 | Vlan20 / FastEthernet1/0 | 从哪个口发出去 |
| 存活时间 | 00:01:00 | 该条目已存在多久 |

#### 5_1.1 转发决策的三条规则（必须按顺序理解）
1. **最长前缀匹配**：多条路由都能匹配目标 IP 时，选掩码最长的（192.168.1.0/24 优于 192.168.0.0/16，**默认路由 /0 永远最后才用**）；
2. **管理距离（AD）**：来自不同协议的多条**相同前缀**路由，选 AD 小的；
3. **度量值（Metric）**：同一协议内多条路径，选度量值小的（相等则等价负载均衡）。

> **常见误解**：以为"管理距离小的协议一定赢"。实际是**先比前缀长度，再比 AD，最后比 metric**。一条 /24 的静态路由会击败一条 /16 的 OSPF 路由，哪怕 OSPF 看起来"更高级"。

#### 5_1.2 管理距离表（必背）
| 路由来源 | AD | 路由来源 | AD |
| --- | --- | --- | --- |
| 直连路由 | 0 | OSPF | 110 |
| 静态路由 | 1 | IS-IS | 115 |
| EIGRP 汇总路由 | 5 | RIP v1/v2 | 120 |
| eBGP | 20 | EGP | 140 |
| EIGRP（内部） | 90 | ODR | 160 |
| IGRP | 100 | 外部 EIGRP | 170 |
| — | — | iBGP | 200 |
| — | — | 未知/不可信 | 255（不会进表） |

**AD=255 表示完全不可信，路由器直接丢弃该路由**——这也是制造"路由黑洞"的一个技巧。

#### 5_1.3 记忆法
```latex
   0  直连     —— 我自己身上的，最可信
   1  静态     —— 我亲手写的，次可信
   20 eBGP    —— 外部邻居说的
   90 EIGRP   —— 自家的，很信
   110 OSPF   —— 自家的，信
   120 RIP    —— 老协议，勉强信
   255 不可信  —— 不进表
```

---

### 5_2 静态路由：什么时候用
| 优点 | 缺点 | 典型场景 |
| --- | --- | --- |
| 简单、可控、可预测 | 拓扑变化不会自动收敛 | 末节网络（只有一条出口） |
| 不占用 CPU/带宽 | 大规模维护成本爆炸 | 小型分支、默认路由指向 ISP |
| 安全性高（不广播路由） | **容易出现"单向路由"** | 浮动静态做备份路径 |

> **"单向路由"是静态路由的头号事故**：只在 A 上配了去 B 的路由，忘了在 B 上配回 A 的路由。现象是"能发出去但回不来"，`ping` 全丢，但 `show ip route` 看起来一切正常。**永远双向都配。**

---

### 5_3 实战：两校区通过 DDN 专线互通
**场景**：新旧两个校区各是一个局域网，出口各有一台路由器，中间申请一条 2M DDN 专线（串口 V.35）相连。

```latex
   新校区                                       旧校区
   ┌────┐      ┌────┐  s2/0 ═══════ s2/0  ┌────┐     ┌────┐
   │PC1 │──────│ R1 │  DCE(要配时钟)  DTE │ R2 │─────│PC2 │
   └────┘      └────┘                     └────┘     └────┘
   192.168.1.0/24     192.168.3.0/24        192.168.2.0/24
```

#### 5_3.1 地址规划
| 设备/接口 | IP | 说明 |
| --- | --- | --- |
| PC1 | 192.168.1.2/24 | 网关 192.168.1.1 |
| R1 fa1/0 | 192.168.1.1/24 | 新校区内网网关 |
| R1 s2/0 | 192.168.3.1/24 | **DCE 端，需配时钟** |
| R2 s2/0 | 192.168.3.2/24 | DTE 端 |
| R2 fa1/0 | 192.168.2.1/24 | 旧校区内网网关 |
| PC2 | 192.168.2.2/24 | 网关 192.168.2.1 |

#### 5_3.2 R1 配置
```latex
R1>en
R1#conf t
R1(config)#hostname R1
R1(config)#int fa 1/0
R1(config-if)#no shutdown
R1(config-if)#ip address 192.168.1.1 255.255.255.0
R1(config-if)#exit
R1(config)#int serial 2/0
R1(config-if)#no shutdown
R1(config-if)#ip address 192.168.3.1 255.255.255.0
R1(config-if)#clock rate 64000      ←DCE 端必配；实验室常用 64000，真实专线由运营商提供时钟
R1(config-if)#end
R1#show ip route
```

#### 5_3.3 R2 配置
```latex
R2>en
R2#conf t
R2(config)#hostname R2
R2(config)#int fa 1/0
R2(config-if)#no shutdown
R2(config-if)#ip address 192.168.2.1 255.255.255.0
R2(config-if)#exit
R2(config)#int serial 2/0
R2(config-if)#ip address 192.168.3.2 255.255.255.0
R2(config-if)#no shutdown            ←DTE 端不需要 clock rate
R2(config-if)#end
```

#### 5_3.4 配置静态路由（双向都要配！）
```latex
! R1：去往旧校区网段，下一跳是 R2 的串口地址
R1(config)#ip route 192.168.2.0 255.255.255.0 192.168.3.2

! R2：回指新校区网段，下一跳是 R1 的串口地址
R2(config)#ip route 192.168.1.0 255.255.255.0 192.168.3.1
```

真实输出：

```latex
R1#show ip route
C    192.168.1.0/24 is directly connected, FastEthernet1/0
S    192.168.2.0/24 [1/0] via 192.168.3.2
```

#### 5_3.5 静态路由的三种写法与区别
| 写法 | 示例 | 特点 |
| --- | --- | --- |
| 指定下一跳 | `ip route 192.168.2.0 255.255.255.0 192.168.3.2` | **推荐**，以太多路访问网络无 ARP 负担 |
| 指定出接口 | `ip route 192.168.2.0 255.255.255.0 s2/0` | 点对点串口可用；以太网口会导致每个目的 IP 都触发 ARP |
| 两者都指定 | `ip route 192.168.2.0 255.255.255.0 s2/0 192.168.3.2` | 最明确，避免递归查找 |

> **为什么以太网口不能只写出接口**：路由器会认为"目标地址直连在这个口上"，于是对每个要转发的目的 IP 发 ARP 请求。如果下一跳设备开了 proxy ARP 还能通，没开就全丢。这是"配置看起来对但不通"的经典场景。

---

### 5_4 默认路由、浮动静态与黑洞路由
#### 5_4.1 默认路由
```latex
R1(config)#ip route 0.0.0.0 0.0.0.0 200.1.1.2
```

`0.0.0.0/0` 匹配一切，但**前缀长度最短**，永远最后才被使用。这就是"最长前缀匹配"规则给它安排的位置。

#### 5_4.2 浮动静态路由（主备切换）
```latex
! 主路径：走专线，AD=1（静态默认）
R1(config)#ip route 192.168.2.0 255.255.255.0 192.168.3.2

! 备份路径：走 4G/拨号，AD=130，大于任何动态协议常见 AD
R1(config)#ip route 192.168.2.0 255.255.255.0 10.0.0.2 130
```

**原理**：主路径存在时，备份路径因 AD 更大而不进表；主路径失效（出接口 down）后，备份路径浮现进表。

```latex
   正常：路由表里只有 [1/0] via 192.168.3.2
   故障：192.168.3.2 不可达 → [130/0] via 10.0.0.2 浮现
```

> **浮动静态的局限**：它只在**出接口 down** 时切换。如果对端设备宕机但本端接口仍 up（如中间经过交换机），浮动静态不会切换。这时要用 **IP SLA + track**（见 5_4.4）。

#### 5_4.3 黑洞路由（防环）
```latex
R1(config)#ip route 192.168.0.0 255.255.0.0 null0 110
```

用途：做路由汇总时，防止"汇总路由吸引流量、明细路由缺失"造成的环路。数据包被丢到 null0 直接丢弃，不会在路由器之间来回打转。

#### 5_4.4 IP SLA + track：真正的链路健康检查
```latex
! 第1步 定义探测：每 5 秒向 8.8.8.8 发 ICMP，超时 1000ms
R1(config)#ip sla 1
R1(config-ip-sla)#icmp-echo 8.8.8.8 source-interface gi0/0
R1(config-ip-sla-echo)#frequency 5
R1(config-ip-sla-echo)#exit
R1(config)#ip sla schedule 1 life forever start-time now

! 第2步 定义 track 对象，跟踪 SLA 状态
R1(config)#track 1 ip sla 1 reachability

! 第3步 静态路由绑定 track：探测失败则路由失效
R1(config)#ip route 0.0.0.0 0.0.0.0 200.1.1.2 track 1

! 第4步 备份路由（AD 更大，平时不进表）
R1(config)#ip route 0.0.0.0 0.0.0.0 10.0.0.2 200

! 验证
R1#show ip sla statistics
R1#show track
```

> **这是静态路由从"手工"走向"自动"的关键一步**，也是 CCNP 的考点。同样可应用于 HSRP 的 track（见板块9）。

---

### 5_5 验证与调试
```latex
R1#show ip route                          ←全表
R1#show ip route 192.168.2.0              ←看某条目的匹配过程
R1#show ip route static                   ←只看静态路由
R1#show ip route 192.168.2.5              ←★最佳用法：路由器告诉你它会选哪条
R1#traceroute 192.168.2.2                 ←看实际路径
R1#ping 192.168.2.2 source 192.168.1.1    ←★指定源地址测试（避免被"默认用出口口地址"误导）
R1#debug ip routing                       ←看路由表变化（实验室用）
```

#### 5_5.1 `show ip route {目标IP}` 为什么最好用
它不只是显示一条路由，而是显示**路由器为到达这个 IP 实际选择的条目**，包括最长匹配的判定结果。当你怀疑"为什么走了这条路"时，这条命令直接给答案。

#### 5_5.2 ping 必须带 source
```latex
R1#ping 192.168.2.2
```

不带 source 时，路由器用**出接口的地址**作为源；带 source 时，你能模拟"从内网某台主机发起"的真实场景。

> 排查"单向可达"时，`ping {目标} source {内网地址}` 是必备动作。不带 source 的 ping 通了，不代表业务能通。

---

### 5_6 案例小故事：只配了一半的静态路由
> 两个校区专线割接完成，新校区能 ping 通旧校区的服务器，但旧校区访问新校区的 OA 系统一直超时。
> 工程师在新校区 R1 上 `ping 192.168.2.2`，通；在旧校区 R2 上 `ping 192.168.1.2`，也通。于是判定"网络没问题，是 OA 系统的事"，把工单转给了应用组。应用组查了两天，一无所获。
> 第三天，一位老工程师做了一件事：他从**旧校区的 PC 上** ping 新校区的 PC——不通。而从**路由器上** ping——通。
> 差别在哪？路由器 ping 时用的是**出接口地址 192.168.3.2** 作源，这个地址两端都有直连路由；而 PC ping 时用的是 **192.168.2.2** 作源，R1 上没有回程路由到 192.168.2.0/24……等等，有啊？
> 再仔细看 `show ip route`：R1 上的静态路由写的是 `ip route 192.168.2.0 255.255.255.0 192.168.3.2`，**下一跳写的是自己的接口地址**。这条路由 AD=1 进了表，但下一跳不可达，实际不生效。而 R2 上的回程路由干脆**漏配了**。
> 补上 `R2(config)#ip route 192.168.1.0 255.255.255.0 192.168.3.1`，业务立刻恢复。
> **复盘三条**：
> 1. **测试必须从"业务主机"发起，不能从路由器发起**——路由器有自己的地址，会掩盖回程问题；
> 2. `ping`** 要带 **`source`，模拟真实流量；
> 3. **静态路由永远双向配**，配完立刻在对端验证。

**现象**：路由器之间通，主机之间不通。  
**排查**：`ping {目标} source {内网接口地址}`；两端各 `show ip route` 核对去程与回程。  
**根因**：单向路由（漏配回程静态路由）。  
**修复**：补上反向静态路由。  
**经验**：网络问题很大比例出在"单向可达"。**永远在两端各测一次。**

---

### 5_7 场景笔记：这一章该记什么
#### 5_7.1 必记内容
1. **管理距离表**——抄一遍，贴显示器旁；
2. **三条转发规则的优先级顺序**（前缀 > AD > metric），这是面试高频；
3. **每个网段的"去程+回程"对照表**——每配一条静态路由，就在表里填两行；
4. **DCE 端的识别方法**：`show controllers s2/0`，这是串口故障的第一命令。

#### 5_7.2 实验记录模板
```latex
【实验编号】B05-01
【实验名称】两校区静态路由互通 + 浮动静态主备切换
【日期 / 耗时】____ / ____ 分钟
【拓扑】
   [PC1]─[R1]══s2/0══[R2]─[PC2]
   （标出哪端是 DCE）
【地址规划】
  | 设备/接口 | IP            | 说明        |
  | R1 s2/0   | 192.168.3.1/24| DCE，配时钟 |
【需求】三网段互通；主链路故障时用备份路径
【关键配置】
  clock rate 64000 / ip route 双向 / 浮动静态 AD=130
【验证清单】
  [ ] show controllers s2/0 确认 DCE/DTE 角色
  [ ] show ip int brief 串口 up/up（物理与协议都 up）
  [ ] R1 上 show ip route 有到 192.168.2.0 的 S 条目
  [ ] R2 上 show ip route 有到 192.168.1.0 的 S 条目  ←★双向
  [ ] 从 PC1 ping PC2 通（第二次 0 丢包）
  [ ] 从 PC2 ping PC1 通（反向必须测）
  [ ] shutdown 主链路 → 备份路由浮现进表（记录耗时 ____ 秒）
  [ ] no shutdown 后主路由恢复
【人为故障复现 1】
  操作：删掉 R2 上的回程静态路由
  现象：PC1 ping PC2 全丢，但 R1 ping R2 通
  定位：ping 192.168.1.2 source 192.168.2.1（反向带源测试）
  根因：单向路由
  修复：补回程路由
【人为故障复现 2】
  操作：DCE 端不配 clock rate
  现象：串口 up / down（协议 down）
  定位：show controllers s2/0
  根因：无时钟
  修复：clock rate 64000
【人为故障复现 3】
  操作：两端封装不一致（一端 PPP 一端 HDLC）
  现象：串口 up / down 反复
  修复：两端统一 encapsulation ppp
【复盘一句话】____
【遗留问题】____
```

#### 5_7.3 实用验证清单
- [ ] 能背出管理距离表的关键值（0/1/20/90/110/120/255）；
- [ ] 能解释"为什么 /24 静态会赢 /16 OSPF"；
- [ ] 能独立配通双向静态路由并解释下一跳写法差异；
- [ ] 能配出浮动静态并实测切换；
- [ ] 知道浮动静态的局限，能说出 IP SLA + track 的用途；
- [ ] 已用 `ping source` 复现并定位过一次"单向可达"。

---

### 5_8 进阶延伸
1. **IP SLA 的更多探针**：除 icmp-echo 外，还支持 tcp-connect、udp-jitter（语音质量）、http，可与 HSRP/策略路由联动；
2. **BFD**：毫秒级故障检测，与 OSPF/EIGRP/BGP/静态路由联动，是 CCNP 快速收敛的核心（见板块16）；
3. **策略路由 PBR**：`route-map` + `ip policy route-map`，按源地址/应用选路，突破"只按目标地址选路"的限制；
4. **递归查找与负载均衡**：同一目标多条等价静态路由时，IOS 默认按目标地址做负载均衡（`ip load-sharing per-packet` 可改按包，但会导致乱序，生产一般不用）。

---

## 板块6 · OSPF 动态路由 — 从单区域到多区域
> 一句话定位：**OSPF 是企业网的地基协议，也是 CCNA 权重最高、CCNP/CCIE 挖得最深的路由协议。**

---

### 6_0 本板块知识地图
```latex
   链路状态协议三步走
   ┌──────────────────────────────────────────────┐
   │ 第1步 建邻接：互发 Hello，发现邻居、协商参数        │
   │ 第2步 同步 LSDB：LSA 洪泛，全网拥有一致的拓扑地图   │
   │ 第3步 独立算路：各自以自己为根跑 SPF(Dijkstra)      │
   └──────────────────────────────────────────────┘

   距离矢量（RIP）：听邻居说路怎么走 → 慢、易环、15 跳上限
   链路状态（OSPF）：自己看地图算路 → 快、无环、可分区扩展
```

---

### 6_1 链路状态协议在做什么
**核心机制三步**：

1. **建邻接**：路由器互发 Hello，发现邻居并协商参数；
2. **同步 LSDB**：通过 LSA（链路状态通告）洪泛"我有哪些链路、连着谁、开销多少"，所有路由器最终拥有**完全一致**的链路状态数据库；
3. **独立算路**：每台路由器以自己为根运行 SPF（Dijkstra）算法，算出最短路径树装进路由表。

| 对比项 | 链路状态（OSPF/IS-IS） | 距离矢量（RIP） |
| --- | --- | --- |
| 传递内容 | 链路状态（拓扑地图） | 路由条目（别人算好的结果） |
| 收敛速度 | 快（触发更新 + 增量洪泛） | 慢（周期性广播整表） |
| 环路风险 | 算法层面无环 | 需水平分割/毒性逆转等抑制 |
| 资源消耗 | 内存与 CPU 较高 | 较低 |
| 适用规模 | 分区域可扩展到大型网络 | 15 跳上限，仅小型网络 |

**一句话记忆**：距离矢量是"**听邻居说路怎么走**"，链路状态是"**自己看地图算路**"。

---

### 6_2 区域（Area）：OSPF 可扩展的秘密
#### 6_2.1 五种区域类型
| 区域类型 | 特征 | 适用场景 |
| --- | --- | --- |
| **标准区域** | 接收链路更新与路由汇总 | 默认区域 |
| **骨干区域 Area 0** | 所有其他区域必须与之相连，负责区域间路由传递 | 必须存在，网络核心 |
| **存根区域 Stub** | 不接收外部 AS 路由（Type-5 LSA），改用默认路由 | 分支末节，减小 LSDB |
| **完全存根 Totally Stubby** | Cisco 私有；不收外部路由，也不收区域间汇总，只留默认路由 | 分支末节（最省资源） |
| **NSSA** | 类似 stub，但允许引入外部路由（Type-7 LSA，ABR 转为 Type-5） | 分支需要引入本地外部路由时 |

```latex
                    ┌──────────────┐
                    │    Area 0    │  ← 骨干，必须连续
                    └───┬──────┬───┘
                        │      │
              ┌─────────┘      └─────────┐
              ▼                          ▼
        ┌──────────┐                ┌──────────┐
        │  Area 10 │                │  Area 20 │
        │  (stub)  │                │  (NSSA)  │
        └──────────┘                └──────────┘
        只留默认路由                  可引入本地外部路由
```

#### 6_2.2 规划原则
+ **Area 0 必须连续**；非骨干区域必须连接到 Area 0（无法直连时用**虚链路 virtual-link** 临时补救）；
+ 区域边界尽量落在**汇聚层**，避免一个区域横跨过多设备；
+ **中小型园区网：全放 Area 0（单区域）完全可行**，简单可靠；超过约 50 台路由器再考虑分区域。

---

### 6_3 度量值 Cost：与带宽成反比
```latex
接口 Cost = 参考带宽（默认 100 Mbps） / 接口带宽
到达目标网段的总 Cost = 路径上所有"出接口" Cost 之和
```

| 链路 | 计算 | Cost |
| --- | --- | --- |
| 10M 以太网 | 100/10 | 10 |
| 100M 以太网 | 100/100 | 1 |
| 1000M 以太网 | 100/1000 → 小于 1 | **1（无法区分！）** |
| 1.544M 串口 | 100/1.544 ≈ 64.7 | 64 |
| 2M E1 | 100/2 | 48 |

#### 6_3.1 生产必做：调整参考带宽
千兆及以上网络必须调整参考带宽，否则 **1G 与 10G 链路的 cost 都是 1**，OSPF 会"看不见"带宽差异，可能把流量导到 1G 链路上去。

```latex
Router(config)#router ospf 1
Router(config-router)#auto-cost reference-bandwidth 100000   ←单位 Mbps，此处设为 100G
! 全网所有路由器必须设置相同的值，否则 cost 口径不一致会带来次优路径甚至环路风险

! 也可手工指定
Router(config-if)#ip ospf cost 30          ←直接指定接口开销（优先于计算值）
Router(config-if)#bandwidth 2000           ←或修改逻辑带宽（单位 Kbps），影响 cost 计算
```

---

### 6_4 实战：三层交换机 + 双路由器 OSPF 单区域
**场景**：校园网通过一台三层交换机连到出口路由器 R1，R1 与校外 R2 相连，要求校内主机与校外主机互通。

```latex
   ┌────┐      ┌───────┐        ┌────┐  s2/0 ═══ s2/0  ┌────┐     ┌────┐
   │PC1 │──────│ S3560 │════════│ R1 │   192.168.4.0   │ R2 │─────│PC2 │
   └────┘      └───────┘        └────┘                 └────┘     └────┘
   192.168.1.0/24  192.168.3.0/24                    192.168.2.0/24
   (Vlan10)        (Vlan20)
```

#### 6_4.1 地址规划
| 设备 | 接口 | IP | 网段 |
| --- | --- | --- | --- |
| S3560 | Vlan10 | 192.168.1.1/24 | 192.168.1.0（PC1） |
| S3560 | Vlan20 | 192.168.3.1/24 | 192.168.3.0（上联 R1） |
| R1 | Fa0/0 | 192.168.3.2/24 | 192.168.3.0 |
| R1 | Serial2/0（DCE） | 192.168.4.1/24 | 192.168.4.0 |
| R2 | Serial2/0 | 192.168.4.2/24 | 192.168.4.0 |
| R2 | Fa0/0 | 192.168.2.1/24 | 192.168.2.0（PC2） |

PC1：192.168.1.2/24，网关 192.168.1.1；PC2：192.168.2.2/24，网关 192.168.2.1。

#### 6_4.2 S3560 三层交换机
```latex
Switch>en
Switch#conf t
Switch(config)#hostname S3560
S3560(config)#vlan 10
S3560(config-vlan)#exit
S3560(config)#vlan 20
S3560(config-vlan)#exit
S3560(config)#int fa 0/10
S3560(config-if)#switchport access vlan 10
S3560(config-if)#exit
S3560(config)#int fa 0/20
S3560(config-if)#switchport access vlan 20
S3560(config-if)#exit
S3560(config)#interface vlan 10
S3560(config-if)#ip address 192.168.1.1 255.255.255.0
S3560(config-if)#no shutdown
S3560(config-if)#interface vlan 20
S3560(config-if)#ip address 192.168.3.1 255.255.255.0
S3560(config-if)#no shutdown
S3560(config-if)#exit
S3560(config)#ip routing                       ←★ 别忘了
S3560(config)#router ospf 1
S3560(config-router)#network 192.168.1.0 0.0.0.255 area 0
S3560(config-router)#network 192.168.3.0 0.0.0.255 area 0
```

#### 6_4.3 R1（DCE 端）与 R2
```latex
! R1
R1(config)#interface fa0/0
R1(config-if)#ip address 192.168.3.2 255.255.255.0
R1(config-if)#no shutdown
R1(config-if)#interface serial 2/0
R1(config-if)#ip address 192.168.4.1 255.255.255.0
R1(config-if)#clock rate 64000                 ←DCE 端
R1(config-if)#no shutdown
R1(config-if)#exit
R1(config)#router ospf 1
R1(config-router)#network 192.168.3.0 0.0.0.255 area 0
R1(config-router)#network 192.168.4.0 0.0.0.255 area 0

! R2
R2(config)#interface serial 2/0
R2(config-if)#ip address 192.168.4.2 255.255.255.0
R2(config-if)#no shutdown
R2(config-if)#exit
R2(config)#router ospf 1
R2(config-router)#network 192.168.2.0 0.0.0.255 area 0
R2(config-router)#network 192.168.4.0 0.0.0.255 area 0
```

#### 6_4.4 `network` 命令的三个要素
```latex
network {网络号或接口IP} {通配符掩码} area {区域号}
```

+ **通配符掩码**：0 表示必须匹配，255 表示不关心。`0.0.0.255` = 前 24 位必须匹配；
+ **匹配逻辑**：用命令中的网络号去匹配**本地接口的 IP**，命中的接口才启用 OSPF（开始发 Hello、把接口网段放进 LSA）；
+ 想精确宣告单个接口，可写接口地址 + `0.0.0.0`：

```latex
network 192.168.3.2 0.0.0.0 area 0
```

> **常见错误**：把通配符写成子网掩码。`network 192.168.1.0 255.255.255.0 area 0` 在语法上不报错，但含义完全变了（IOS 会把它当成"匹配所有位"），结果是**要么命中过多接口，要么一个都不命中**。

#### 6_4.5 更现代的写法：接口下直接启用
```latex
R1(config)#interface gi0/0
R1(config-if)#ip ospf 1 area 0
```

**推荐**：接口级配置更精确、不受地址变更影响，也是 CCNP/CCIE 的推荐写法。

---

### 6_5 邻居建立：七个状态与失败排查
```latex
   Down → Init → 2-Way → ExStart → Exchange → Loading → Full
          │       │                                      │
          │       └─ 看到对方的 Hello 里有自己的 Router-ID │
          │          （广播网络在此选 DR/BDR）              │
          │                                               │
          └───────────── LSDB 同步完成，邻接建立 ──────────┘
```

#### 6_5.1 邻居起不来的 checklist（按顺序查）
| 检查项 | 命令 | 常见不匹配 |
| --- | --- | --- |
| 接口是否 up/up | `show ip int brief` | 物理或协议 down |
| 是否在同一子网 | `show ip int brief` | 地址/掩码配错 |
| Area ID 是否一致 | `show ip ospf interface` | 两端 area 号不同 |
| Hello/Dead 定时器 | `show ip ospf interface` | 一端改过 timers |
| 认证是否一致 | `show ip ospf interface` | 一端配了认证 |
| 网络类型是否一致 | `show ip ospf interface` | 一端 broadcast 一端 point-to-point |
| MTU 是否一致 | `show ip ospf neighbor`（卡 ExStart） | 一端改了 MTU |
| 是否被动接口 | `show ip protocols` | `passive-interface` 配错 |
| Router-ID 是否冲突 | `show ip ospf` | 两台设备 RID 相同 |

#### 6_5.2 卡在不同状态的典型原因
```latex
卡在 Init      → 单向可达（ACL 拦了、或一端收不到 Hello）
卡在 2-Way     → 正常（DROther 之间本就只到 2-Way）
卡在 ExStart   → MTU 不匹配
卡在 Exchange  → MTU 或 LSA 数量超限
卡在 Loading   → 链路质量差、丢包严重
反复 Full/Down → 链路抖动或认证密钥不一致
```

#### 6_5.3 DR/BDR
**广播多路访问网络（以太网）需要选 DR/BDR**，目的是减少邻接数量：

```latex
   没有 DR：5 台路由器两两建邻接 = 10 个邻接，LSA 洪泛爆炸
   有 DR  ：所有路由器只与 DR/BDR 建邻接 = 稳定可控
```

+ 选举依据：**接口优先级（默认 1，0 表示不参与）→ Router-ID 最大者胜**；
+ 地址为 `224.0.0.5`（AllSPFRouters）与 `224.0.0.6`（AllDRouters）；
+ **DROther 之间停留在 2-Way 是正常的**，不是故障；
+ 点到点链路（串口 PPP/HDLC）**不选 DR**。

---

### 6_6 LSA 类型：OSPF 的"词汇表"
| 类型 | 名称 | 产生者 | 传播范围 | 携带内容 |
| --- | --- | --- | --- | --- |
| **1** | Router LSA | 每台路由器 | 本区域内 | 自己的链路与 cost |
| **2** | Network LSA | DR | 本区域内 | 该网段的掩码与成员 |
| **3** | Summary LSA | ABR | 区域间 | 区域间的网段汇总 |
| **4** | ASBR Summary | ABR | 区域间 | 到 ASBR 的路由 |
| **5** | External LSA | ASBR | 全 AS（除 stub） | 外部路由（重分发进来的） |
| **7** | NSSA External | ASBR（在 NSSA 内） | NSSA 内 | 外部路由，出 NSSA 时由 ABR 转为 Type-5 |

```latex
   Area 10        Area 0        外部网络(RIP/EIGRP)
   ┌──────┐      ┌──────┐      ┌──────┐
   │ LSA1 │─ABR─►│ LSA3 │      │      │
   │ LSA2 │      │ LSA5 │◄─ASBR┼──────┤
   └──────┘      └──────┘      └──────┘
   stub 区域：LSA5 被替换成一条默认路由
   NSSA   ：内部产生 LSA7，出区域时转成 LSA5
```

**记忆口诀**：1 自己、2 DR、3 跨区、4 找 ASBR、5 外部、7 NSSA 专用。

---

### 6_7 验证与调试
```latex
R1#show ip ospf neighbor              ←邻居表（第一命令）
R1#show ip ospf neighbor detail
R1#show ip ospf interface gi0/0       ←接口开销、网络类型、DR/BDR、定时器
R1#show ip ospf database              ←LSDB 摘要
R1#show ip ospf database router       ←看 Type-1 LSA
R1#show ip route ospf                 ←只看 OSPF 学到的路由
R1#show ip protocols                  ←进程号、RID、宣告网段、被动接口
R1#debug ip ospf hello                ←看 Hello 收发（实验室）
R1#debug ip ospf adj                  ←看邻接建立全过程
R1#clear ip ospf process              ←重启 OSPF 进程（生产慎用）
```

#### 6_7.1 `show ip ospf neighbor` 输出解读
```latex
Neighbor ID     Pri   State      Dead Time   Address         Interface
192.168.4.2       0   FULL/  -   00:00:34    192.168.4.2     Serial2/0
2.2.2.2           1   FULL/BDR  00:00:36    192.168.3.1     GigabitEthernet0/0
```

+ `FULL/-`：点到点链路，无 DR 选举，正常；
+ `FULL/BDR`：以太网，对端是 BDR；
+ `2-WAY/DROTHER`：DROther 之间，正常；
+ **没有条目 = 邻居没起来**；卡在 `EXSTART` = MTU 问题。

#### 6_7.2 读懂 `O [110/65]`
```latex
O    192.168.4.0/24 [110/65] via 192.168.3.2
│                     │   │
│                     │   └─ Metric：累计 cost（到目标的出接口 cost 之和）
│                     └───── AD：OSPF 默认 110
└─────────────────────────── O = OSPF（区域内），O IA = 区域间，O E2 = 外部
```

**过关标志**：能解释 `[110/65]` 的每一个字段，包括 65 是怎么算出来的。

---

### 6_8 多区域、认证与优化
#### 6_8.1 区域间汇总（在 ABR 上做）
```latex
ABR(config)#router ospf 1
ABR(config-router)#area 10 range 172.16.0.0 255.255.240.0
```

把 Area 10 的多条明细汇总成一条发给 Area 0，**减少 LSDB 规模、抑制明细抖动**。

#### 6_8.2 外部路由汇总（在 ASBR 上做）
```latex
ASBR(config-router)#summary-address 10.0.0.0 255.255.0.0
```

#### 6_8.3 认证（三种）
```latex
! 接口明文
R1(config-if)#ip ospf authentication
R1(config-if)#ip ospf authentication-key Cisc0123

! 接口 MD5
R1(config-if)#ip ospf authentication message-digest
R1(config-if)#ip ospf message-digest-key 1 md5 Cisc0123

! 区域级 MD5（推荐，一次配全区域）
R1(config-if)#ip ospf authentication message-digest
R1(config-router)#area 0 authentication message-digest
```

#### 6_8.4 被动接口与默认路由下发
```latex
R1(config-router)#passive-interface gi0/1        ←接终端的口不发 Hello，安全且省资源
R1(config-router)#passive-interface default
R1(config-router)#no passive-interface gi0/0     ←例外放开

R1(config-router)#default-information originate  ←把默认路由通告给全网
R1(config-router)#default-information originate always   ←即使本地没有默认路由也下发
```

#### 6_8.5 快速收敛
```latex
R1(config-if)#ip ospf hello-interval 1
R1(config-if)#ip ospf dead-interval 4
R1(config-if)#ip ospf network point-to-point     ←以太网改点到点，跳过 DR 选举，收敛更快
R1(config-if)#ip bfd enable                      ←BFD（CCNP，毫秒级检测）
```

> 改 Hello 时间必须**两端一致**，否则邻居 down。Dead 时间会自动按 4 倍调整，但显式配置更稳妥。

---

### 6_9 案例小故事：通配符写成子网掩码的那两小时
> 某分支站点新加一台路由器，OSPF 配完，`show ip ospf neighbor` 空空如也。
> 工程师检查了：接口 up/up ✅、地址同网段 ✅、area 都是 0 ✅、定时器默认 ✅、没配认证 ✅。他甚至抓了包，看到 Hello 包在链路上飞。但邻居就是起不来。
> 两小时后，他把自己配的 `network` 语句和对端的放在一起对比：
> 通配符写成了子网掩码。`0.0.0.255` 意思是"前 24 位必须匹配"，而 `255.255.255.0` 意思是"前 24 位不关心，最后 8 位必须匹配"——结果这条语句**匹配上了不该匹配的接口，或压根没匹配上目标接口**，导致 OSPF 压根没在那个口上启用。
> 改成 `0.0.0.255` 后，邻居三秒内 FULL。
> **复盘**：
> + **现象**：Hello 在飞但邻居起不来（说明对端在发，本端没在这个口上启用 OSPF）；
> + **根因**：通配符掩码写成子网掩码；
> + **修复**：改用正确通配符，或**直接用 **`ip ospf 1 area 0`**（接口级配置）**；
> + **经验**：**接口级 **`ip ospf {pid} area {id}`** 是避免这类错误的根本办法**——它不依赖你算通配符，也就没有算错的机会。

```latex
对端：network 192.168.4.0 0.0.0.255 area 0
自己：network 192.168.4.0 255.255.255.0 area 0   ←★
```

**同类高频错误清单**：

| 错误 | 现象 | 修复 |
| --- | --- | --- |
| 通配符写成子网掩码 | 邻居起不来 | 改通配符 / 用接口级配置 |
| 三层交换机未开 `ip routing` | 有路由不通 | `ip routing` |
| 一端改了 Hello 定时器 | 邻居 down | 两端一致 |
| MTU 不一致 | 卡在 ExStart | 统一 MTU 或 `ip ospf mtu-ignore` |
| Router-ID 冲突 | 邻接反复翻动 | 手工配 `router-id` |
| 区域号不同 | 邻居起不来 | 统一 area |

---

### 6_10 场景笔记：这一章该记什么
#### 6_10.1 必记内容
1. **你的网络的 OSPF 区域规划图**（哪台是 ABR、哪个区域是什么类型）；
2. **每个网段的 cost 推导过程**——不是背数字，是把"100/带宽"的算式写出来；
3. **邻居起不来的 9 项 checklist**——贴显示器旁；
4. **LSA 六类的口诀**——1 自己、2 DR、3 跨区、4 找 ASBR、5 外部、7 NSSA。

#### 6_10.2 实验记录模板
```latex
【实验编号】B06-01
【实验名称】OSPF 单区域：三层交换机 + 双路由器
【日期 / 耗时】____ / ____ 分钟
【拓扑】
   [PC1]─[S3560]══[R1]══s2/0══[R2]─[PC2]
【地址规划】（贴表，含每个接口）
【需求】全网互通；能解释每条 O 路由的 cost
【关键配置】
  ip routing / network 0.0.0.255 area 0 / clock rate 64000
  或接口级 ip ospf 1 area 0
【预期结果】
  - 三台设备两两 FULL
  - 每台都有到其他两个网段的 O 路由
  - PC1 ping PC2 第二次 0 丢包
【实际结果】
  贴 show ip ospf neighbor + show ip route ospf 输出
【cost 推导练习】
  R1 到 192.168.1.0/24 的 cost = ____
  推导过程：出接口 ____ 带宽 ____，cost = 100/____ = ____，累计 ____
【验证清单】
  [ ] show ip ospf neighbor 三台都 FULL
  [ ] show ip ospf interface 看网络类型与 cost 是否符合预期
  [ ] show ip route ospf 每台的路由条目数正确
  [ ] show ip ospf database 三台 LSA 数量一致（LSDB 同步标志）
  [ ] PC1 ping PC2 第二次 0 丢包
  [ ] 能说出 O / O IA / O E2 分别代表什么
【人为故障复现 1】
  操作：把 R1 的 network 通配符改成 255.255.255.0
  现象：邻居消失
  定位：show ip protocols 看宣告网段
  修复：改回 / 改用接口级配置
【人为故障复现 2】
  操作：一端改 hello-interval 1
  现象：邻居 down，日志报 mismatched hello parameters
  定位：show ip ospf interface 对比 timers
  修复：两端一致
【人为故障复现 3】
  操作：S3560 上 no ip routing
  现象：路由表有 O 条目但 ping 不通（长 ping 观察）
  修复：ip routing
【收敛实测】
  在 R1 上 shutdown 一个口 → 长 ping 丢包 ____ 个，恢复耗时 ____ 秒
【复盘一句话】____
【遗留问题】____
```

#### 6_10.3 实用验证清单
- [ ] 能独立配通三设备 OSPF 单区域；
- [ ] 能解释 `O [110/65]` 每个字段，并手推 65 的来历；
- [ ] 能说出邻居起不来的 9 项检查，并独立排掉至少 3 种；
- [ ] 能说出 LSA 1/2/3/4/5/7 的产生者与传播范围；
- [ ] 知道 stub / totally stub / NSSA 的区别与适用场景；
- [ ] 能用接口级 `ip ospf 1 area 0` 替代 `network` 语句配通一遍。

---

### 6_11 进阶延伸
1. **OSPFv3**：基于链路运行（不再基于网段）、支持地址族、实例 ID、认证依赖 IPsec（CCNP 必考，见板块13）；
2. **多区域与虚链路**：Area 0 不连续时的临时补救，以及为什么虚链路是"设计失败的标志"；
3. **重分发与路径控制**：双向重分发、route-map、distribute-list、prefix-list、防环与次优路径（板块16）；
4. **OSPF 与 BFD / IP SLA**：毫秒级收敛组合；
5. **自动化校验**：用 Ansible 采集 `show ip ospf neighbor` 并断言"邻居数必须等于 N"，把邻接状态纳入 CI 检查。

---

## 板块7 · NAT 与 NAPT 地址转换
> 一句话定位：**NAT 是 IPv4 地址枯竭时代的续命技术，也是企业上网的必经一跳。**

---

### 7_0 本板块知识地图
```latex
   内网                      NAT 边界                 外网
   ┌──────┐               ┌──────────┐            ┌────────┐
   │PC1   │ 192.168.1.2   │          │            │        │
   │      ├──── inside ──►│   R1     ├── outside ─►│ Server │
   │PC2   │ 192.168.1.3   │          │ 200.1.1.3  │200.1.2.2│
   └──────┘               └──────────┘            └────────┘

   内部本地 192.168.1.2  ──转换──►  内部全局 200.1.1.3
   外部全局 200.1.2.2    ──同址──►  外部本地 200.1.2.2
```

---

### 7_1 先分清四个地址：看懂 NAT 的唯一门槛
| 术语 | 英文 | 含义 | 本实验中的例子 |
| --- | --- | --- | --- |
| **内部本地地址** | Inside Local | 内网主机的真实私有 IP | 192.168.1.2 |
| **内部全局地址** | Inside Global | 内网主机对外表现的公网 IP | 200.1.1.3 |
| **外部本地地址** | Outside Local | 外部主机在内网视角下的地址（通常与 Outside Global 相同） | 200.1.2.2 |
| **外部全局地址** | Outside Global | 外部主机的真实公网 IP | 200.1.2.2 |

配合接口方向一起理解：

+ `ip nat inside`：连接内网的接口（本实验 R1 的 fa0/0）；
+ `ip nat outside`：连接外网的接口（本实验 R1 的 s2/0）。

**记忆法**：

```latex
inside / outside 说的是"接口在哪里"
local  / global  说的是"地址从谁的视角看"

换个视角，同一个 IP 的叫法就变了：
   200.1.2.2 在外网视角 = 外部全局
   200.1.2.2 在内网视角 = 外部本地（NAT 后的话可能不同）
```

---

### 7_2 三种 NAT 类型
| 类型 | 映射关系 | 是否节省公网地址 | 典型用途 | 关键命令 |
| --- | --- | --- | --- | --- |
| **静态 NAT** | 1:1 固定 | 否 | 内网服务器对外发布 | `ip nat inside source static 192.168.1.10 200.1.1.10` |
| **动态 NAT** | 多:多，从地址池临时分配 | 否（池子用完就拒绝） | 内网主机数 ≈ 公网地址数 | `ip nat inside source list 1 pool P1`（**不加 overload**） |
| **NAPT / PAT** | 多:1，靠端口号区分会话 | ✅ 是 | 全公司共享一个（或少量）公网 IP 上网 | `ip nat inside source list 1 pool P1 overload` 或 `ip nat inside source list 1 interface s2/0 overload` |

#### 7_2.1 为什么 NAPT 是绝对主流
**收益**：

+ 极致节省公网地址：一个 IP 可提供数万个端口，足够几百人同时上网；
+ 天然隐藏内网拓扑：外网看不到内网真实地址，无法直接发起连接，等于一层隐式防护。

**代价也要清楚**：

+ 外网无法主动访问内网（除非做静态映射）；
+ 端到端可追溯性变差（需配合日志留存，等保有要求）；
+ FTP、SIP 等协议需要 ALG 支持。

#### 7_2.2 核心区分（一个单词决定实验成败）
```latex
动态 NAT：ip nat inside source list 1 pool P1
          → 多对多、一次占用一个地址、池满即拒绝

NAPT/PAT：ip nat inside source list 1 pool P1 overload
          → 多对一 + 端口复用   ★就差这一个单词
```

---

### 7_3 实战：全公司通过一个公网 IP 上网
**场景**：公司办公网需接入互联网，只向 ISP 申请了一条专线、一个公网 IP，要求全公司主机都能访问外网服务器。

```latex
   ┌────┐        ┌────┐  s2/0 ═══════ s2/0  ┌────┐       ┌────────┐
   │PC1 │────────│ R1 │ 200.1.1.1   200.1.1.2│ R2 │───────│ Server │
   │PC2 │        └────┘                      └────┘       │200.1.2.2│
   └────┘       inside  fa0/0                 fa0/0  200.1.2.1
   192.168.1.0/24  192.168.1.1             200.1.2.0/24
```

#### 7_3.1 地址规划
| 设备 | IP | 掩码 | 网关 |
| --- | --- | --- | --- |
| PC1 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 |
| PC2 | 192.168.1.3 | 255.255.255.0 | 192.168.1.1 |
| Server（外网） | 200.1.2.2 | 255.255.255.0 | 200.1.2.1 |
| R1 fa0/0 | 192.168.1.1 | 255.255.255.0 | — |
| R1 s2/0（DCE） | 200.1.1.1 | 255.255.255.0 | — |
| R2 s2/0 | 200.1.1.2 | 255.255.255.0 | — |
| R2 fa0/0 | 200.1.2.1 | 255.255.255.0 | — |

#### 7_3.2 第一步：R1 与 R2 基础配置
```latex
R1>en
R1#conf t
R1(config)#host R1
R1(config)#int fa 0/0
R1(config-if)#ip address 192.168.1.1 255.255.255.0
R1(config-if)#no shutdown
R1(config-if)#int s 2/0
R1(config-if)#ip address 200.1.1.1 255.255.255.0
R1(config-if)#no shutdown
R1(config-if)#clock rate 64000

R2>en
R2#conf t
R2(config)#host R2
R2(config)#int s 2/0
R2(config-if)#ip address 200.1.1.2 255.255.255.0
R2(config-if)#no shutdown
R2(config-if)#int fa 0/0
R2(config-if)#ip address 200.1.2.1 255.255.255.0
R2(config-if)#no shutdown
```

#### 7_3.3 第二步：静态路由（先让网络"通"，再谈 NAT）
```latex
! R1：去往外网服务器网段
R1(config)#ip route 200.1.2.0 255.255.255.0 200.1.1.2

! R2：回指公司内网网段
R2(config)#ip route 192.168.1.0 255.255.255.0 200.1.1.1
```

> **实验设计上的重要提醒（本实验最大的认知陷阱）**：  
本拓扑中 R2 有一条回指 192.168.1.0/24 的静态路由，因此 **PC 不配 NAT 也能 ping 通 Server**（实验环境下可验证）。但真实互联网中不存在这条回程路由——**私有地址在公网不可路由，所以必须靠 NAT**。
> **判断标准很简单**：看外网路由器是否有到内网私有网段的回程路由。真实环境的答案永远是没有。很多人做完实验发现"不配 NAT 也能通"就误以为 NAT 可有可无。

#### 7_3.4 第三步：配置 NAPT（端口多路复用）
```latex
R1(config)#int fa 0/0
R1(config-if)#ip nat inside                                     ←第1步定义内网接口
R1(config-if)#int s 2/0
R1(config-if)#ip nat outside                                    ←第2步定义外网接口
R1(config-if)#exit
R1(config)#access-list 1 permit 192.168.1.0 0.0.0.255           ←第3步ACL 圈定要转换的内网地址
R1(config)#ip nat pool jaking 200.1.1.3 200.1.1.3 netmask 255.255.255.0   ←第4步地址池（起止 IP 相同）
R1(config)#ip nat inside source list 1 pool jaking overload     ←第5步overload 开启端口复用
R1(config)#end
R1#show ip nat translations
```

#### 7_3.5 第 第5步 条命令逐词拆解（务必能解释）
```latex
ip nat inside source list 1 pool jaking overload
│   │   │      │      │   │    │      │
│   │   │      │      │   │    │      └─ 开启端口复用（PAT）
│   │   │      │      │   │    └──────── 使用名为 jaking 的地址池
│   │   │      │      │   └───────────── 引用 ACL 1
│   │   │      │      └───────────────── ACL 编号
│   │   │      └──────────────────────── 转换"源"地址
│   │   └─────────────────────────────── 对 inside → outside 方向的流量
│   └─────────────────────────────────── NAT
└─────────────────────────────────────── ip
```

**等价写法（更常用，直接复用出接口地址）**：

```latex
R1(config)#ip nat inside source list 1 interface serial 2/0 overload
```

不需要地址池，直接用出接口的公网 IP。这是中小企业最常见的写法。

---

### 7_4 转换表解读与服务器发布
#### 7_4.1 `show ip nat translations` 输出解读
```latex
Pro  Inside global      Inside local       Outside local      Outside global
icmp 200.1.1.3:1        192.168.1.2:1      200.1.2.2:1        200.1.2.2:1
tcp  200.1.1.3:1025     192.168.1.2:1025   200.1.2.2:80       200.1.2.2:80
tcp  200.1.1.3:1026     192.168.1.3:1025   200.1.2.2:80       200.1.2.2:80
```

四列对应 7_1 的四个地址术语。**看第二行与第三行**：两台内网主机（.2 和 .3）的源端口都是 1025，但转换后一个保持 1025、一个变成 1026——**这就是 NAPT 靠端口号区分会话的实证**。

```latex
R1#show ip nat statistics        ←看 hits（命中数），判断 NAT 是否工作
R1#clear ip nat translation *    ←清空转换表（注意：生产慎用，会断现有会话）
```

#### 7_4.2 静态 PAT：发布内网服务器
```latex
! 把内网 192.168.1.10 的 80 端口映射到公网 200.1.1.10 的 80
R1(config)#ip nat inside source static tcp 192.168.1.10 80 200.1.1.10 80

! 整台服务器 1:1 映射
R1(config)#ip nat inside source static 192.168.1.10 200.1.1.10
```

> **注意**：静态 NAT 是双向的——配了之后，外网可以主动访问内网。**这意味着安全边界被打开了一个洞**，必须配合 ACL 或防火墙（见板块10、11）。

#### 7_4.3 NAT 处理顺序（决定 ACL 写什么地址）
| 方向 | 顺序 | ACL 该写什么地址 |
| --- | --- | --- |
| **inside → outside** | 先路由 → 再 NAT → 最后出方向 ACL | 出方向 ACL 写**转换后的公网地址** |
| **outside → inside** | 先 NAT → 再路由 → 最后入方向 ACL | 入方向 ACL 写**转换后的内网地址**（ASA 8.3+ 同样写真实地址） |

```latex
   出方向：包先查路由（决定从哪出）→ 做 NAT（改源地址）→ 匹配出方向 ACL
           所以 ACL 里要写 200.1.1.x，不是 192.168.1.x

   入方向：包先做 NAT（把目的地址从公网改成内网）→ 查路由 → 匹配入方向 ACL
           所以 ACL 里要写 192.168.1.x（真实地址）
```

> **现场高频错误**：按内网地址写 ACL 却应用在出方向，导致规则永远匹配不上。**判断方法就是 **`show access-lists`** 看计数是否增长。**

---

### 7_5 案例小故事：转换表是空的，到底算不算故障？
> 新人小赵配完 NAPT，兴冲冲地敲 `show ip nat translations`，结果**什么都没有**。他慌了，以为 NAT 没生效，开始反复检查 ACL、地址池、inside/outside 接口——折腾一小时，配置确认无误，但表还是空的。
> 带教师傅过来看了一眼，问了一句："你 ping 了吗？"
> 小赵：啊？
> 师傅从 PC1 上 `ping 200.1.2.2`，然后让他再看 `show ip nat translations`——表项出现了，四列地址清清楚楚。
> **师傅的解释**：NAT 是**按流触发**的。没有从 inside 到 outside 的实际流量，就不会生成任何转换表项。这不是配置错误，这是 NAT 的工作方式。
> **复盘三条**：
> 1. **先制造流量，再看转换表**；
> 2. 判断 NAT 是否工作看 `show ip nat statistics` 的 **hits**；若为 0，说明流量根本没被 ACL 或方向规则命中；
> 3. `show ip nat translations` 为空时，**不要急着改配置**，先 ping 一下。

```latex
没有流量 → 没有表项 → 正常
有流量但没表项 → 才叫故障（查 ACL / inside-outside 方向 / 路由）
```

**现象**：`show ip nat translations` 无输出。  
**排查**：先 ping 制造流量 → 再看表 → 看 `show ip nat statistics` 的 hits。  
**根因**：NAT 按流触发，无流量即无表项。  
**修复**：不是故障，无需修复。  
**经验**：区分"表空"与"NAT 不工作"，看 hits 而非看表项数。

**延伸：真正该排查的三种"NAT 不工作"**

| 症状 | 根因 | 修复 |
| --- | --- | --- |
| ping 了但表仍空、hits=0 | ACL 没匹配到内网地址 | 检查 `access-list 1 permit` 网段 |
| hits 有增长但不通 | inside/outside 配反或漏配 | 检查两个接口方向 |
| 转换成功但回不来 | 外网无回程路由（真实环境靠公网地址，一般不存在此问题） | 检查外网路由 |

---

### 7_6 场景笔记：这一章该记什么
#### 7_6.1 必记内容
1. **四个地址术语的对照表**——每次看转换表都对照一遍，直到形成条件反射；
2. **NAT 处理顺序图**（出/入方向各一张）——直接决定 ACL 怎么写；
3. **你的网络的公网地址规划**：有几个公网 IP、哪些做了静态发布、端口分别是什么；
4. **"不配 NAT 也能通"的陷阱说明**——写在实验笔记最显眼的位置。

#### 7_6.2 实验记录模板
```latex
【实验编号】B07-01
【实验名称】NAPT 全家上网 + 静态 PAT 发布服务器
【日期 / 耗时】____ / ____ 分钟
【拓扑】
   [PC1][PC2]─[R1]══[R2]─[Server]
   inside    outside
【地址规划】（贴表，标注哪个是 inside 接口、哪个是 outside）
【需求】
  - 内网 192.168.1.0/24 通过一个公网 IP 上网
  - 内网 Web 服务器对外发布
【关键配置】
  ip nat inside / ip nat outside / access-list 1 / ip nat pool / overload
  或 ip nat inside source list 1 interface s2/0 overload
【验证清单】
  [ ] 未 ping 时 show ip nat translations 为空（记录这个"正常现象"）
  [ ] ping 之后出现表项，四列地址能逐一解释
  [ ] show ip nat statistics 的 hits > 0
  [ ] 两台 PC 同时访问外网，转换表中端口号不同（NAPT 实证）
  [ ] 静态 PAT 配置后，外网能访问内网服务器 80 端口
  [ ] 反掩码/ACL 网段正确（show access-lists 计数增长）
【转换表抄录】（贴真实输出，并手写四列对应关系）
  Inside local ____ → Inside global ____
  Outside global ____ → Outside local ____
【人为故障复现 1】
  操作：忘记 overload
  现象：只有一台 PC 能上网，第二台失败（池里只有一个地址）
  根因：动态 NAT 池满即拒绝
  修复：加 overload
【人为故障复现 2】
  操作：inside / outside 配反
  现象：hits=0，转换表为空
  定位：show ip nat statistics / show run | include nat
  修复：改回
【人为故障复现 3】
  操作：出方向 ACL 写内网地址
  现象：show access-lists 计数不增长
  根因：出方向 ACL 应写转换后地址
  修复：改 ACL
【思考题】
  为什么本实验不配 NAT 也能通？真实环境为什么不行？
  答：____（写清楚"回程路由是否存在"这个判据）
【复盘一句话】____
【遗留问题】____
```

#### 7_6.3 实用验证清单
- [ ] 能不查资料说出四个地址术语并对应到转换表四列；
- [ ] 能解释 `overload` 一个单词带来的本质差异；
- [ ] 能独立配出 NAPT 与静态 PAT；
- [ ] 能说出 NAT 处理顺序，并判断 ACL 该写公网还是内网地址；
- [ ] 知道"转换表为空不是故障"，并能用 hits 判断 NAT 是否工作。

---

### 7_7 进阶延伸
1. **NAT 与 IPsec 的冲突**：IPsec 隧道流量被 PAT 改写后不再匹配感兴趣流，必须做 **NAT 豁免**（见板块10、15 案例 11）；
2. **NAT64 / NAT66**：IPv6 过渡技术中的地址转换（见板块13）；
3. **Carrier-Grade NAT（CGNAT）**：运营商级 NAT，家庭宽带拿不到公网 IP 的原因；
4. **NAT 日志与合规**：`ip nat log translations syslog`，配合日志留存满足等保"可追溯"要求；
5. **ASA 上的 NAT 语法差异**：ASA 8.3+ 用对象 NAT，ACL 里写**真实地址**（见板块11）。

---

## 板块8 · 广域网与远程接入
> 一句话定位：**局域网负责"快"，广域网负责"远"和"贵"——封装、认证、时钟、拨号，每个细节都直接决定能不能通。**

---

### 8_0 本板块知识地图
```latex
   一条串口要跑起来，必须同时满足两层：

   物理层      DCE 端提供时钟 ──── clock rate 64000（实验室）
                                  现网由运营商提供，路由器侧为 DTE 不配
        │
        ▼
   数据链路层  两端封装一致 ────  HDLC（Cisco 默认，私有）
                                 PPP（推荐：支持认证、多协议）
                                      ├── PAP：两次握手，明文
                                      └── CHAP：三次握手，只传哈希 ★

   上层演进：16AM 拨号（已淘汰） → ISDN → PPPoE → 专线 + IPsec VPN
```

---

### 8_1 广域网链路的两层要素
一条串口要真正跑起来，需要同时满足：

| 层级 | 要素 | 常见配置 |
| --- | --- | --- |
| **物理层** | DCE 端提供时钟 | `clock rate 64000`（实验室）；现网由运营商设备提供时钟，路由器侧作为 DTE 不配 |
| **数据链路层** | 两端封装协议一致 | 默认 HDLC（Cisco 私有）/ PPP（推荐，支持认证与多协议） |

```latex
R1#show controllers s2/0              ←判断本端是 DCE 还是 DTE（最可靠）
R1(config-if)#encapsulation ppp       ←两端必须一致，否则协议 down
R1(config-if)#encapsulation hdlc      ←Cisco 串行链路默认封装
```

> **现网提醒**：运营商线路（E1/SDH/MSTP）已由运营商设备提供时钟，路由器侧作为 DTE **不需要 clock rate**。只有在实验环境用 V.35 背靠背线缆，或由本端设备提供时钟时才需要配。

---

### 8_2 PPP 与两种认证：为什么 CHAP 是标配
PPP 相比 HDLC 的三点优势：**支持认证**、支持多网络层协议（IPv4/IPv6）、支持链路质量监控与压缩协商。

| 认证 | 握手 | 密码传输 | 重放安全 | 结论 |
| --- | --- | --- | --- | --- |
| **PAP** | 两次握手，直接发送用户名 + 密码 | **明文** | 否 | 仅用于兼容老设备 |
| **CHAP** | 三次握手：挑战（随机数）→ 响应 MD5（随机数+密码）→ 确认 | 不传密码，只传哈希 | ✅ 每次挑战值不同 | **生产首选** |

```latex
   CHAP 三次握手
   第1步 主验方 ──挑战(随机数+本端主机名)──► 被验方
   第2步 被验方 ──响应(MD5(随机数+密码))──► 主验方
   第3步 主验方 本地算一遍比对 ──成功/失败──►

   关键点：密码从不上链路，链路上只有随机数与哈希
```

#### 8_2.1 配置
```latex
! R1（本端 hostname 必须与对端 username 一致）
R1(config)#username R2 password Cisc0123
R1(config)#int s2/0
R1(config-if)#encapsulation ppp
R1(config-if)#ppp authentication chap
R1(config-if)#clock rate 64000

! R2
R2(config)#username R1 password Cisc0123        ←两边密码必须相同
R2(config)#int s2/0
R2(config-if)#encapsulation ppp
R2(config-if)#ppp authentication chap
```

#### 8_2.2 三条铁律
1. **用户名 = 对端设备的 hostname**，两端密码一致；
2. `ppp authentication chap` 是**发起挑战**的命令，两端都配 = 双向认证；
3. 想让 CHAP 失败时用 PAP 兜底：`ppp authentication chap pap`。

#### 8_2.3 验证
```latex
R1#show interfaces s2/0           ←看 LCP/IPCP 是否 Open
R1#debug ppp authentication       ←实时看认证过程（实验室神器）
R1#debug ppp negotiation          ←看 LCP/NCP 协商
```

**现象识别**：认证失败时接口**物理 up、协议反复 up/down**，日志刷 `PPP authentication failed`。优先查 hostname / username / 密码三处是否完全对应（**大小写敏感**）。

#### 8_2.4 PPP 附加能力
```latex
R1(config-if)#ppp multilink                  ←多条串口捆绑（MLPPP），带宽叠加
R1(config-if)#ppp quality 80                 ←链路质量低于 80% 时关闭链路
R1(config-if)#compress stac                  ←载荷压缩（窄带链路）
R1(config-if)#ip tcp header-compression      ←TCP 头压缩
```

---

### 8_3 实战解析：16AM 拨号模块
**场景**：Cisco 2620 插入 16AM（16 口模拟 Modem）模块，为不在办公大楼的员工提供 Modem 拨号接入；拨入用户通过内网 DHCP 服务器自动获取 IP（含 DNS），并可经防火墙访问 Internet。

```latex
   远程 PC ──电话线──► [16AM 模块]
                          │ PPP + CHAP 认证
                          ▼
                    从 DHCP 拿地址（含 DNS）
                          │
                          ▼
                    默认路由 → 防火墙 192.168.1.4
                          │
                          ▼
                    内网服务器 / Internet
```

#### 8_3.1 逻辑接口配置（Group-Async）
```latex
Cisco2620(config)#interface Group-Async1
Cisco2620(config-if)# ip unnumbered FastEthernet0/0
Cisco2620(config-if)# encapsulation ppp
Cisco2620(config-if)# ip tcp header-compression passive
Cisco2620(config-if)# async mode dedicated
Cisco2620(config-if)# peer default ip address dhcp
Cisco2620(config-if)# ppp authentication chap
Cisco2620(config-if)# group-range 33 48
```

#### 8_3.2 逐条拆解"为什么这么配"
| 命令 | 作用与设计考量 |
| --- | --- |
| `interface Group-Async1` | 创建异步组接口，把 16 条异步线路的配置**模板化**，避免对 33–48 号口逐条重复配置 |
| `ip unnumbered FastEthernet0/0` | 借用内网口地址作为本接口 IP 源，**不额外消耗地址段**（拨号链路若逐条编址会非常浪费） |
| `encapsulation ppp` | 采用 PPP 才能支持 CHAP 认证与地址协商（SLIP 已淘汰） |
| `ip tcp header-compression passive` | 被动式 TCP 头压缩：Modem 带宽极低（33.6K/56K），20 字节 TCP 头占比可观，压缩后明显提升小包应用响应速度 |
| `async mode dedicated` | 线路专用于异步 PPP 拨号，**不允许交互模式（exec）登录**，杜绝未认证访问 |
| `peer default ip address dhcp` | 客户端 IP 由局域网 DHCP 服务器统一分配——优势：节约地址、同时下发 DNS 等参数，与内网策略保持一致 |
| `ppp authentication chap` | 拨入用户必须认证（配合全局 `username`） |
| `group-range 33 48` | 把 16 个物理异步口（line 33–48）纳入 Group-Async1，一次性套用上述配置 |

#### 8_3.3 物理线路（Line）参数
```latex
Cisco2620(config)#line 33 48
Cisco2620(config-line)# session-timeout 30
Cisco2620(config-line)# autoselect during-login
Cisco2620(config-line)# autoselect ppp
Cisco2620(config-line)# login local
Cisco2620(config-line)# modem InOut
Cisco2620(config-line)# transport input all
Cisco2620(config-line)# stopbits 1
Cisco2620(config-line)# flowcontrol hardware
```

| 命令 | 解读 |
| --- | --- |
| `session-timeout 30` | 空闲 30 分钟自动挂断，释放线路并控制费用 |
| `autoselect during-login` / `autoselect ppp` | 自动识别拨入的是 PPP 会话还是字符终端，无需用户手动敲命令 |
| `login local` | 调用本地用户数据库做口令校验 |
| `modem InOut` | 允许拨入 + 拨出双向（仅拨入可用 `modem dialin`） |
| `transport input all` | 允许所有传输协议进入该线路 |
| `stopbits 1` | 异步串行参数：1 位停止位（与客户端一致才能通信） |
| `flowcontrol hardware` | 硬件流控（RTS/CTS），避免高速数据冲垮 Modem 缓冲区 |

#### 8_3.4 用户账号与路由
```latex
Cisco2620(config)#username shixuegang password abc123
Cisco2620(config)#ip route 0.0.0.0 0.0.0.0 192.168.1.4     ←默认路由指向防火墙内网口
```

**整条链路**：远程 PC → 电话线 → 16AM 模块（PPP + CHAP 认证）→ 从 DHCP 拿地址（含 DNS）→ 经默认路由交给防火墙 192.168.1.4 → 访问内网服务器或 Internet。

> **虽然是淘汰技术，但这段配置值得精读**，因为它展示了三个至今通用的设计思想：
> 1. **接口模板化**（Group-Async）——批量配置思想的雏形；
> 2. **地址复用**（ip unnumbered）——节省地址规划；
> 3. **认证与地址下发分离**（CHAP 认证 + DHCP 分配）——现代 802.1X + DHCP 也是这个结构。

---

### 8_4 时代演进：从 16AM 到现代远程接入
| 阶段 | 技术 | 速率 | 现状 |
| --- | --- | --- | --- |
| 早期 | 16AM/8AM 模拟 Modem 拨号、ISDN BRI/PRI | 56K / 64K–2M | 已淘汰，只需理解原理与识别老配置 |
| 过渡期 | PPPoE（ADSL）、帧中继、ATM | 数 M–数十 M | PPPoE 仍在部分宽带使用 |
| 当前主流 | MSTP/专线、IPsec VPN、SSL VPN、SD-WAN | 百 M–10G+ | 在网运行，是学习的重点 |

#### 8_4.1 PPPoE（理解要点）
```latex
! 路由器作为 PPPoE 客户端（常见于小企业宽带）
R1(config)#interface dialer 1
R1(config-if)#ip address negotiated
R1(config-if)#encapsulation ppp
R1(config-if)#ppp chap hostname user@isp
R1(config-if)#ppp chap password 0 ispPass
R1(config-if)#ip mtu 1492                    ←★ 关键：PPPoE 头占 8 字节
R1(config-if)#ip tcp adjust-mss 1452         ←★ 配套动作
R1(config-if)#dialer pool 1
R1(config)#interface gi0/0
R1(config-if)#pppoe-client dial-pool-number 1
```

> **PPPoE 的 MTU 坑**：标准以太网 MTU 1500，PPPoE 头部占 8 字节，因此 PPPoE 链路的有效 MTU 是 **1492**，TCP MSS 相应应设为 **1452**（1492 − 20 IP 头 − 20 TCP 头）。不改就会出现"小网页能开、大文件必断"的经典故障（见板块15 案例 10）。

#### 8_4.2 MSS 调整：隧道场景的通用解药
```latex
R1(config-if)#ip tcp adjust-mss 1452
```

适用：PPPoE、IPsec/GRE 隧道、任何中间链路 MTU 小于 1500 的场景。**建议作为隧道配置的默认项。**

---

### 8_5 验证与调试
```latex
R1#show controllers s2/0              ←DCE/DTE 判定（串口第一命令）
R1#show interfaces s2/0               ←LCP/IPCP 状态、封装类型
R1#show ip interface brief            ←up/up 双绿
R1#debug ppp authentication           ←认证过程
R1#debug ppp negotiation              ←LCP/NCP 协商
R1#ping 192.168.3.2                   ←连通性
R1#show ppp multilink                 ←MLPPP 状态
```

`show interfaces s2/0` 关键行：

```latex
Serial2/0 is up, line protocol is up
  Encapsulation PPP, LCP Open
  Open: IPCP, CDPCP, loopback not set
```

`LCP Open`** + **`IPCP Open`** = PPP 完全正常**。若 LCP Open 但 IPCP 未 Open，问题在三层（IP 地址协商）；若 LCP 都未 Open，问题在物理层或封装。

---

### 8_6 案例小故事：大小写引发的"反复 up/down"
> 两条专线割接，R1 和 R2 都配好了 PPP + CHAP。接口灯亮着，但 `show ip int brief` 里串口状态在 `up/up` 与 `up/down` 之间反复跳，日志不停刷：
> 工程师检查了三遍密码——`Cisc0123`，两边一样。检查了封装——都是 PPP。检查了时钟——DCE 端配了。
> 最后有人把两台设备的配置并排放在一起：
> R2 的 hostname 是**小写 **`r2`，而 R1 里配的用户名是**大写 **`R2`。CHAP 认证时，R1 用"R2"作为用户名查找，R2 收到挑战后发现对端的 hostname 与自己不匹配，认证失败。
> 把 R2 改成 `hostname R2`，链路三秒内稳定，不再翻动。
> **复盘**：
> + **现象**：物理 up、协议反复 up/down，日志刷 `AUTHFAIL`；
> + **根因**：hostname 大小写不一致，CHAP 用户名匹配失败；
> + **修复**：统一 hostname 大小写；
> + **经验**：CHAP 认证失败，**先查 hostname / username / 密码三处是否完全对应，且大小写敏感**。这三处是 CHAP 故障的 90%。

```latex
%LINK-3-UPDOWN: Interface Serial2/0, changed state to up
%PPP-4-AUTHFAIL: PPP authentication failed
%LINK-3-UPDOWN: Interface Serial2/0, changed state to down
```

```latex
R1: hostname R1           username R2 password Cisc0123
R2: hostname r2           username R1 password Cisc0123   ←★
```

**CHAP 故障排查四步**：

```latex
第1步 show running-config | include hostname      ←确认两端 hostname
第2步 show running-config | include username      ←确认 username = 对端 hostname
第3步 确认两端密码完全相同（含大小写、特殊字符）
第4步 debug ppp authentication                   ←看实际交互
```

---

### 8_7 场景笔记：这一章该记什么
#### 8_7.1 必记内容
1. **DCE/DTE 判定方法**：`show controllers s2/0`——串口故障第一条永远是"DCE 端有没有配时钟"；
2. **CHAP 三处匹配清单**：hostname / username / 密码，且大小写敏感；
3. **PPPoE 的 MTU 与 MSS 数值**：1492 / 1452，背下来；
4. **16AM 那段配置的三条设计思想**（模板化 / 地址复用 / 认证与地址分离）——面试时讲这个能加分。

#### 8_7.2 实验记录模板
```latex
【实验编号】B08-01
【实验名称】PPP + CHAP 双向认证 + PPPoE MTU 验证
【日期 / 耗时】____ / ____ 分钟
【拓扑】
   [R1]══s2/0══[R2]   （标出 DCE 端）
【需求】串口链路稳定 up/up，CHAP 双向认证通过
【关键配置】
  encapsulation ppp / ppp authentication chap / username 对端hostname / clock rate
【验证清单】
  [ ] show controllers s2/0 确认 DCE/DTE 角色
  [ ] show interfaces s2/0 显示 LCP Open、IPCP Open
  [ ] show ip int brief 串口 up/up 且不再翻动
  [ ] 两端互 ping 通
  [ ] debug ppp authentication 能看到三次握手成功
【人为故障复现 1】
  操作：DCE 端不配 clock rate
  现象：show ip int brief 显示 up/down
  定位：show controllers
  根因：无时钟
  修复：clock rate 64000
【人为故障复现 2】
  操作：一端改 hostname 大小写
  现象：物理 up、协议反复 up/down，日志 AUTHFAIL
  定位：debug ppp authentication + 对比 hostname
  根因：CHAP 用户名大小写不匹配
  修复：统一 hostname
【人为故障复现 3】
  操作：一端 HDLC 一端 PPP
  现象：封装不匹配，协议 down
  修复：统一 encapsulation
【MTU 实验】
  标准以太网 MTU = ____
  PPPoE 有效 MTU = ____
  对应 TCP MSS 应为 ____
  验证：ping -l 1500 -f（带 DF 位）是否失败 → 记录结果
【复盘一句话】____
【遗留问题】____
```

#### 8_7.3 实用验证清单
- [ ] 能不查资料说出串口 up/down 的头号原因；
- [ ] 能独立配通 PPP + CHAP 双向认证；
- [ ] 能说出 CHAP 与 PAP 的本质区别（是否明文、是否防重放）；
- [ ] 知道 PPPoE 场景必须调整 MTU/MSS 及其数值；
- [ ] 已用 `debug ppp authentication` 看过一次完整的三次握手。

---

### 8_8 进阶延伸
1. **MLPPP 与多链路捆绑**：把多条 E1 绑成一条逻辑链路，带宽叠加（等价于广域网版的 EtherChannel）；
2. **GRE over IPsec**：用 GRE 承载动态路由协议，用 IPsec 加密，是经典的企业组网方案（见板块10、16）；
3. **DMVPN**：多点动态 VPN，分支之间按需建立隧道，无需中心站点中转（CCNP/CCIE 重点）；
4. **SD-WAN**：用策略替代传统路由，按应用质量动态选路，是广域网的当前主流演进方向（见板块16）；
5. **WAN 自动化**：用 Python 批量采集 `show interfaces` 的 CRC 错误计数，提前发现线路劣化（见板块16）。

---

## 板块9 · 网关冗余 — HSRP / VRRP / GLBP
> 一句话定位：**网关是主机的最后一条命脉，网关挂了，网络再健壮也没用。**

---

### 9_0 本板块知识地图
```latex
   主机网关写死 192.168.1.1
            │
            ▼
   ┌────────────────────────────────┐
   │   虚拟网关 IP 192.168.1.1       │  ← 主机只认这个
   │   虚拟 MAC 0000.0C07.ACxx      │
   └───────┬────────────────┬───────┘
           │                │
      ┌────┴────┐      ┌────┴────┐
      │  R1     │      │  R2     │
      │ Active  │      │ Standby │
      │ pri 110 │      │ pri 100 │
      └────┬────┘      └────┬────┘
           │                │
        上行口            上行口
           └── track Serial0/0/0 decrement 30 ──┘
                出口断了 → 优先级降到 80 → R2 抢占
```

---

### 9_1 为什么需要第一跳冗余协议（FHRP）
主机的默认网关通常写死一个 IP（如 192.168.1.1）。当这台网关路由器宕机，**即使网络里还有另一条出口路径，主机也不会自动换网关**——它会继续把包发给那个已不存在的地址。

**FHRP 的解法**：让多台路由器虚拟出共同的网关 IP 与虚拟 MAC，主机网关指向这个虚拟地址。同一时刻由其中一台（Active/Master）转发，其余待命；主设备故障时备用在数秒内接管，**主机侧配置完全不用改**。

#### 9_1.1 三种协议对比
| 特性 | HSRP | VRRP | GLBP |
| --- | --- | --- | --- |
| 归属 | Cisco 私有 | IEEE 标准（RFC 5798） | Cisco 私有 |
| 角色 | Active / Standby | Master / Backup | AVG（地址管理）+ 多个 AVF（转发者） |
| 负载均衡 | 需配多组 | 需配多组 | ✅ 单组内多网关同时转发 |
| 虚拟 MAC | 0000.0C07.ACxx（v1，xx=组号十六进制） | 0000.5E00.01xx | 0007.B400.xxyy |
| 组播地址 | 224.0.0.2（v1）/ 224.0.0.102（v2） | 224.0.0.18 | 224.0.0.102 |
| 默认 Hello/Hold | 3s / 10s | 1s / 3s | 3s / 10s |
| **抢占** | **默认关闭** | 默认开启 | 默认关闭 |
| 跟踪上行链路 | `standby track` | `vrrp track` | `glbp weighting track` |
| 典型场景 | 纯 Cisco 园区网 | 多厂商混合 | 需真正负载分担且全 Cisco |

> **HSRP 抢占默认关闭**是高频考点：不配 `preempt`，主设备故障恢复后**不会切回来**，业务会一直走备机——很多人以为是故障，其实是设计如此。

---

### 9_2 逐行拆解原始 HSRP 配置
以一台 Cisco 路由器 r1 的以太网口 E0 为例，典型配置如下：

```latex
interface Ethernet0
 ip address 136.147.107.101 255.255.0.0
 no ip redirects
 standby 150 timers 5 15
 standby 150 priority 150
 standby 150 preempt
 standby 150 authentication cisco
 standby 150 ip 136.147.107.100
 standby 150 track Ethernet0
```

| 命令 | 解读 |
| --- | --- |
| `standby 150 ip 136.147.107.100` | 定义组 150 的**虚拟网关 IP**（主机网关填这个）。**HSRP 唯一必配项** |
| `standby 150 priority 110` | 优先级 0–255，默认 100，越大越优先。本端 110 → 成为 Active |
| `standby 150 preempt` | 抢占：本端优先级更高或故障恢复后主动夺回 Active。**默认关闭**，不配则故障恢复后不会切回 |
| `standby 150 timers 5 15` | Hello 5 秒一次，15 秒收不到 Hello 判定对端失效（Hold 通常 ≥ 3×Hello） |
| `standby 150 authentication cisco` | 明文认证串，防止非法设备加入 HSRP 组劫持网关 |
| `standby 150 track Ethernet0` | 跟踪指定接口，down 时自动降低优先级让备用接管 |
| `no ip redirects` / `no ip directed-broadcast` | 关闭 ICMP 重定向与定向广播，防重定向欺骗与 SMURF 攻击 |

#### 9_2.1 对端（r2）的配套配置
```latex
interface Ethernet0
 ip address 136.147.107.102 255.255.0.0
 standby 150 ip 136.147.107.100
 standby 150 priority 100          ←低于 110，作为 Standby
 standby 150 timers 5 15           ←必须与主设备一致
 standby 150 preempt
 standby 150 authentication cisco
 standby 150 track Ethernet0
```

#### 9_2.2 一处值得指出的设计瑕疵
`track Ethernet0`** 跟踪的是自身承载 HSRP 的接口。** 接口真 down 了，HSRP 自然失效，跟踪意义不大。

工程上应跟踪**上行广域网接口**（如 Serial0），这样"**内网口还活着但出口已断**"时也能切换，才是 track 的真正价值。

```latex
   错误：track 自身内网口  → 内网口一断 HSRP 本就没了，多此一举
   正确：track 上行出口口  → 内网口还活着、出口断了 → 才需要切换 ★
```

#### 9_2.3 现代化的等价写法（推荐）
```latex
R1(config)#interface gi0/0
R1(config-if)#ip address 136.147.107.101 255.255.0.0
R1(config-if)#standby version 2                          ←HSRPv2（支持 IPv6、组号范围更大）
R1(config-if)#standby 150 ip 136.147.107.100
R1(config-if)#standby 150 priority 110
R1(config-if)#standby 150 preempt
R1(config-if)#standby 150 timers msec 200 msec 600       ←亚秒级切换
R1(config-if)#standby 150 authentication md5 key-string HsrpK3y
R1(config-if)#standby 150 track Serial0/0/0 30           ←上行口 down 时优先级降 30
```

#### 9_2.4 为什么 track 要带减值（decrement）——最容易忽略的算术
`track {接口} 30` 表示接口失效时优先级**减 30**。上例中 `110 − 30 = 80`，低于对端的 100，于是对端抢占为 Active。

```latex
   R1: priority 110, track Serial0/0/0 decrement 30
   R2: priority 100

   R1 上行口正常 → 110 > 100 → R1 是 Active ✅
   R1 上行口故障 → 110-30 = 80 < 100 → R2 抢占为 Active ✅

   ★ 如果 decrement 设成 5：110-5 = 105，仍 > 100 → 不会切换 ❌
   ★ 减值必须足够大才能触发切换，这是设计中最容易忽略的算术
```

---

### 9_3 验证与切换测试（实验必做）
```latex
R1#show standby                    ←组号、虚拟 IP、自身角色、优先级、对端信息
R1#show standby brief              ←简洁视图
R1#show standby gi0/0 150          ←指定接口与组
R1#debug standby                   ←观察状态迁移
```

#### 9_3.1 关键输出解读
```latex
GigabitEthernet0/0 - Group 150 (version 2)
  State is Active                                    ←本端角色
  Virtual IP address is 136.147.107.100              ←主机网关填这里
  Active virtual MAC address is 0000.0C9F.F096       ←HSRPv2 的虚拟 MAC
  Hello time 3 sec, hold time 10 sec
  Preemption enabled                                 ←抢占已开启
  Active router is local
  Standby router is 136.147.107.102, priority 100 (expires in 9.232 sec)
  Priority 110 (configured 110)
  Track interface Serial0/0/0 state Up decrement 30
```

#### 9_3.2 切换测试的标准动作
```latex
第1步 在 PC 上开长 ping：ping -t 136.147.107.100（Windows）
第2步 在 R1 上 shutdown 内网口（或上行口，验证 track）
第3步 观察 PC 上丢包数量与恢复时间
第4步 no shutdown，观察是否切回（验证 preempt）
第5步 记录：丢包 ____ 个，恢复耗时 ____ 秒
```

> **过关标志（板块0 周计划 W10）**：关掉主用接口，**业务 15 秒内恢复**。配了亚秒级 timers 后应能做到 1 秒内。

---

### 9_4 VRRP 与 GLBP 的落地要点
#### 9_4.1 VRRP（多厂商环境）
```latex
R1(config)#interface gi0/0
R1(config-if)#vrrp 10 ip 192.168.1.1
R1(config-if)#vrrp 10 priority 110
R1(config-if)#vrrp 10 preempt                    ←VRRP 默认已开启，可省略
R1(config-if)#vrrp 10 track 1 decrement 30
R1(config-if)#vrrp 10 authentication md5 key-string VrrpK3y
R1#show vrrp brief
```

**要点**：VRRP 的 Master IP 可以是**真实的接口 IP**（这点和 HSRP 不同——HSRP 的虚拟 IP 不能与任何真实接口 IP 相同）。这能节省一个地址。

#### 9_4.2 GLBP（真正负载分担）
```latex
R1(config-if)#glbp 10 ip 192.168.1.1
R1(config-if)#glbp 10 priority 110
R1(config-if)#glbp 10 preempt
R1(config-if)#glbp 10 load-balancing round-robin
R1(config-if)#glbp 10 weighting 100 lower 90 upper 100
R1(config-if)#glbp 10 weighting track 1 decrement 30
R1#show glbp brief
```

```latex
   GLBP：一个虚拟 IP，多个虚拟 MAC
   ┌──────────────┐
   │ AVG (R1)     │  负责应答 ARP，按算法返回不同 AVF 的虚拟 MAC
   └──────┬───────┘
          │
    ┌─────┴─────┐
    ▼           ▼
  AVF1(R1)   AVF2(R2)     ←两台都转发，带宽都用上
```

**关键差异**：HSRP/VRRP 同一时刻**只有一台**在转发（备用闲置）；GLBP **多台同时转发**，这是它唯一的、也是最强的优势。

---

### 9_5 联动设计：FHRP 与 STP 的位置关系
**设计要点（承接板块3）**：三层网关（HSRP Active）应与该 VLAN 的 **STP 根桥落在同一台设备**。

```latex
   错配后果：
   VLAN10 的 STP 根 = CoreA，但 VLAN10 的 HSRP Active = CoreB
        │
        ▼
   接入层流量先绕到 CoreA（STP 最短路径）
   再从 CoreA 绕到 CoreB（网关在这里）
   最后从 CoreB 上行
        │
        ▼
   多绕一跳，浪费上行带宽，且故障路径不可预测

   正确：CoreA 同时是 STP 根 + HSRP Active → 流量直达上行
```

**落地做法（成对配置）**：

```latex
! CoreA：VLAN10 的 STP 主根 + HSRP Active
CoreA(config)#spanning-tree vlan 10 priority 4096
CoreA(config-if)#standby 10 priority 110
CoreA(config-if)#standby 10 preempt

! CoreB：VLAN10 的 STP 备根 + HSRP Standby
CoreB(config)#spanning-tree vlan 10 priority 8192
CoreB(config-if)#standby 10 priority 100
CoreB(config-if)#standby 10 preempt
```

再把 VLAN 20/30 反过来配，实现**双核心互为备份 + 负载分担**。

---

### 9_6 案例小故事：主设备宕机了，业务却没切
> 某园区网做了双核心 + HSRP，设计文档写得漂亮。一次计划内演练：关掉主核心 CoreA 的内网口，验证业务切换。
> 结果业务断了整整 40 秒才恢复，远超预期的 10 秒。更糟的是，恢复后流量一直走 CoreB，即使 CoreA 起来了也不切回来。
> 排查发现两个问题：
> **问题一：Hello 定时器是默认的 3s/10s，且两台设备的 timers 不一致。** CoreA 配了 `standby 10 timers 5 15`，CoreB 是默认 3/10。定时器不匹配导致 Hello 报文被当作异常，Hold 超时后才会切换，白白多等了十几秒。
> **问题二：CoreB 上没配 **`preempt`**。** 按 HSRP 默认行为，备用设备**不会主动夺回** Active，所以 CoreA 恢复后只能干等着。
> 另外还查出一处隐患：两台设备的 HSRP 认证串不一致（一个是 `cisco`，一个是 `Cisco`），导致**双方都认为自己是 Active**——这是 HSRP 最危险的状态，会造成流量黑洞。
> **整改**：
> 重新演练：丢包 1 个，恢复耗时 **0.8 秒**。
> **复盘（写进 SOP）**：
> 1. **HSRP 参数必须两端对称**：版本、组号、虚拟 IP、timers、认证；
> 2. **必须配 **`preempt`，否则故障恢复后不会切回；
> 3. **认证串必须一致**（大小写敏感），否则出现双 Active；
> 4. **冗余设计的核心是对称性**——主备两台的所有业务配置（路由/NAT/ACL/HSRP）必须一致，否则切换只是把故障从设备转移到配置。

```latex
CoreA/CoreB(config-if)#standby version 2
CoreA/CoreB(config-if)#standby 10 timers msec 200 msec 600
CoreA/CoreB(config-if)#standby 10 preempt
CoreA/CoreB(config-if)#standby 10 authentication md5 key-string HsrpK3y
```

**现象**：主设备宕机后业务未切换（或切换极慢）。  
**排查**：`show standby brief` 看两台角色；`show standby` 看 timers 与认证；`debug standby` 看状态迁移。  
**根因**：timers 不一致 / 未配 preempt / 认证不一致 / 备用缺少对称配置。  
**修复**：参数对称 + preempt + 认证一致 + 配置对称。  
**经验**：**冗余系统的故障，九成出在"两台设备不一样"。**

---

### 9_7 场景笔记：这一章该记什么
#### 9_7.1 必记内容
1. **每个 VLAN 的 HSRP 主备归属表**——哪个 VLAN 的 Active 在 CoreA，哪个在 CoreB；
2. **track 减值的算术过程**——写下来：`110 − 30 = 80 < 100 → 切换`；
3. **切换实测数据**：丢包几个、耗时几秒，优化前后对比；
4. **HSRP 参数对称性检查清单**（版本/组号/虚拟IP/timers/认证/preempt）。

#### 9_7.2 实验记录模板
```latex
【实验编号】B09-01
【实验名称】HSRP 主备 + track 上行口 + 抢占验证
【日期 / 耗时】____ / ____ 分钟
【拓扑】
   [PC]─[SW]─┬─[R1]─上行
             └─[R2]─上行
【地址规划】
  | 设备 | 接口IP          | 虚拟IP        | 优先级 | 角色 |
  | R1   | 136.147.107.101 | 136.147.107.100| 110   | Active |
  | R2   | 136.147.107.102 | 136.147.107.100| 100   | Standby |
【需求】主设备故障时 15 秒内业务恢复；故障恢复后能切回
【关键配置】
  standby version 2 / ip / priority / preempt / timers / track Serial0/0/0 30
【track 算术验证】
  R1 pri ____，decrement ____，故障后 = ____
  对端 pri ____
  ____ < ____ ? 是 → 会切换 / 否 → 不会切换（请调整 decrement）
【验证清单】
  [ ] show standby brief 显示一台 Active、一台 Standby
  [ ] 无"双 Active"现象（认证一致）
  [ ] show standby 显示 Preemption enabled
  [ ] 主机长 ping 虚拟 IP 不丢包
  [ ] shutdown R1 上行口 → 观察切换，记录丢包 ____ 个、耗时 ____ 秒
  [ ] R2 变 Active（show standby brief 确认）
  [ ] no shutdown → R1 抢占回 Active（验证 preempt）
  [ ] show standby 中 Track interface 状态与 decrement 显示正确
【人为故障复现 1】
  操作：删掉 R1 的 preempt
  现象：R1 恢复后仍是 Standby，不切回
  根因：HSRP 抢占默认关闭
  修复：补 preempt
【人为故障复现 2】
  操作：把 decrement 改成 5
  现象：上行口 down 后不切换（110-5=105 仍 > 100）
  根因：减值不足
  修复：改成 30
【人为故障复现 3】
  操作：两端认证串改成一个大写一个小写
  现象：双 Active，流量黑洞
  定位：show standby brief 两台都 Active；debug standby 报认证失败
  修复：统一认证串
【切换实测对比表】
  | 配置 | 丢包数 | 恢复耗时 |
  | 默认 timers 3/10 | ____ | ____ |
  | msec 200/600     | ____ | ____ |
【复盘一句话】____
【遗留问题】____
```

#### 9_7.3 实用验证清单
- [ ] 能说出 HSRP/VRRP/GLBP 三者的核心差异与适用场景；
- [ ] 能独立配通 HSRP 主备并证明切换成功；
- [ ] 能算出 track decrement 是否足以触发切换；
- [ ] 知道 HSRP 抢占默认关闭，VRRP 抢占默认开启；
- [ ] 能解释"HSRP Active 应与 STP 根桥同设备"的原因；
- [ ] 亲手做过双 Active 故障，并知道如何识别。

---

### 9_8 进阶延伸
1. **HSRP 与 IP SLA / object tracking 联动**：跟踪的不只是接口 up/down，还可以是"到某个 IP 的可达性"（见板块5 的 IP SLA）；
2. **多组 HSRP 实现负载分担**：VLAN 10 的 Active 在 CoreA，VLAN 20 的 Active 在 CoreB，两台都用上；
3. **HSRP + NAT 的对称性问题**：主备两台都要能转换相同的地址池，否则切换后会话中断（CCNP 重点）；
4. **HSRP over 三层链路**：跨汇聚层的 HSRP 部署与 Filter（HSRP 报文过滤）的设计；
5. **自动化校验**：用 Ansible 采集 `show standby brief`，断言"每个 VLAN 有且仅有一台 Active"，纳入变更后的自动检查。

---

## 板块10 · 网络安全 — ACL、设备加固与 VPN
> 一句话定位：**连通性让网络能用，安全策略决定谁能用用到什么程度。**

---

### 10_0 本板块知识地图
```latex
   企业安全的五个层次（自外向内）

   第5步 接入层安全  Port-Security / DHCP Snooping / DAI / 802.1X   （板块2、10_7）
   第4步 加密与隧道  IPsec VPN / NAT 豁免                            （10_6）
   第3步 流量过滤    ACL（三层/四层）                                 （10_2）
   第2步 管理平面    vty ACL / SNMPv3 / 日志审计                      （10_5）
   第1步 设备自身    口令 / SSH / 关无用服务 / AAA                     （10_5）

   核心原则：默认拒绝（Default Deny）+ 最小权限
```

---

### 10_1 企业安全的五个层次
| 层次 | 关注点 | 本板块位置 |
| --- | --- | --- |
| 设备自身加固 | 口令、SSH、关闭无用服务、AAA | 10_5 |
| 管理平面保护 | vty ACL、SNMPv3、日志审计 | 10_5 |
| 流量过滤 | ACL（三层/四层） | 10_2 |
| 加密与隧道 | IPsec VPN、NAT 豁免 | 10_6 |
| 接入层安全 | Port-Security、DHCP Snooping、DAI、802.1X | 板块2、10_7 |

**核心原则**：**默认拒绝（Default Deny）+ 最小权限**。任何安全策略都从"什么都不允许"开始，再逐条放通必要流量。

---

### 10_2 ACL：最常用的过滤器
#### 10_2.1 标准 ACL vs 扩展 ACL
| 类型 | 编号范围 | 能匹配 | 放置位置 | 典型用途 |
| --- | --- | --- | --- | --- |
| **标准 ACL** | 1–99、1300–1999 | 仅源 IP | **尽量靠近目标** | 限制管理网段（vty）、简单过滤 |
| **扩展 ACL** | 100–199、2000–2699 | 源/目的 IP、协议、端口、TCP 标志位 | **尽量靠近源** | 精确的业务访问控制 |
| **命名 ACL** | `ip access-list standard/extended NAME` | 同上 | 同上 | 可读性更好，支持逐条增删 |

> **放置原则的记忆法**：标准 ACL 只能看源地址，放近了会把"不该拦的"也拦掉，所以**远离源、靠近目标**；扩展 ACL 能精确匹配，越早拦越省带宽，所以**靠近源**。

#### 10_2.2 配置示例
```latex
! 标准 ACL：只允许 192.168.10.0/24 远程管理设备
R1(config)#access-list 10 permit 192.168.10.0 0.0.0.255
R1(config)#line vty 0 4
R1(config-line)#access-class 10 in

! 扩展 ACL：只允许内网访问外网 Web
R1(config)#access-list 101 permit tcp 192.168.1.0 0.0.0.255 any eq 80
R1(config)#access-list 101 permit tcp 192.168.1.0 0.0.0.255 any eq 443
R1(config)#access-list 101 deny ip any any
R1(config)#int gi0/0
R1(config-if)#ip access-group 101 in

! 命名 ACL（推荐，便于维护）
R1(config)#ip access-list extended WEB-ONLY
R1(config-ext-nacl)#permit tcp 192.168.1.0 0.0.0.255 host 200.1.2.2 eq 80
R1(config-ext-nacl)#deny ip any any log          ←log 产生日志，便于排错
```

#### 10_2.3 五个必须记住的 ACL 规则
1. **末尾隐含 **`deny ip any any`：忘了写 permit 就等于全断；
2. **自上而下逐条匹配，命中即停**：最具体的规则要放前面；
3. **每接口每方向每协议只能应用一个 ACL**；
4. **ACL 不过滤本设备自身产生的流量**（如自己发出的 ping、路由协议报文），需另用控制平面策略（CoPP）；
5. **通配符掩码**：0 匹配、255 忽略。`host 10.1.1.1` = `10.1.1.1 0.0.0.0`；`any` = `0.0.0.0 255.255.255.255`。

#### 10_2.4 验证与排错
```latex
R1#show access-lists            ←每条规则的匹配计数（排错第一手证据）
R1#show ip interface gi0/0      ←接口应用的 in/out ACL
R1#clear access-list counters   ←清零计数，便于重新观察
```

> **排错技巧**：`show access-lists` 中某条规则的**匹配计数是否增长**，是判断"流量到底有没有走到这里"的**决定性证据**。计数不增长 = 流量压根没走到这个 ACL，去查路由而不是查 ACL 内容。

#### 10_2.5 命名的端口与常用写法
```latex
permit tcp any any eq www          ←可用名字代替端口号（www = 80）
permit tcp any any eq 22
permit udp any any eq domain       ←DNS 53
permit tcp any any established     ←只允许已建立会话的返回流量（有状态过滤的简易形态）
deny ip any any log-input          ←log-input 会记录入接口与源 MAC
```

---

### 10_3 ACL 与 NAT 的协同（决定规则写公网地址还是内网地址）
回顾板块7 的 NAT 处理顺序：

| 方向 | 顺序 | ACL 该写什么地址 |
| --- | --- | --- |
| **inside → outside** | 先路由 → 再 NAT → 最后出方向 ACL | 出方向 ACL 写**转换后的公网地址** |
| **outside → inside** | 先 NAT → 再路由 → 最后入方向 ACL | 入方向 ACL 写**转换后的内网地址**（ASA 8.3+ 同样写真实地址） |

**现场高频错误**：按内网地址写 ACL 却应用在出方向，导致规则永远匹配不上。  
**判断方法**：`show access-lists` 看计数是否增长。

---

### 10_4 时间型 ACL 与策略组合
```latex
R1(config)#time-range WORKTIME
R1(config-time-range)#periodic weekdays 09:00 to 18:00
R1(config)#ip access-list extended WEB-POLICY
R1(config-ext-nacl)#permit tcp 192.168.1.0 0.0.0.255 any eq 80 time-range WORKTIME
R1(config-ext-nacl)#deny ip any any
R1#show time-range
```

适用于"工作时间开放、下班后禁止"的场景，避免人工频繁修改策略。

> **前提**：时间型 ACL 依赖**准确的设备时间**。设备时间错了，策略就会在错误的时间生效——所以**必须先配 NTP**（见板块12）。这是"看起来不相关的两个配置其实强耦合"的典型例子。

---

### 10_5 设备自身加固清单（CCNA 考点 + 生产基线）
```latex
! 第1步 强口令与加密存储
R1(config)#enable secret Str0ngEn@ble
R1(config)#service password-encryption
R1(config)#username admin secret Str0ngP@ss

! 第2步 关闭无用服务
R1(config)#no ip http server
R1(config)#no ip http secure-server      ←如不使用 Web 管理
R1(config)#no cdp run                    ←如不需要 CDP（或用 no cdp enable 精确到接口）
R1(config)#no ip source-route
R1(config)#no service tcp-small-servers
R1(config)#no service udp-small-servers
R1(config)#no ip bootp server
R1(config)#no ip domain-lookup           ←除非需要 DNS 解析

! 第3步 登录加固
R1(config)#line vty 0 4
R1(config-line)#transport input ssh
R1(config-line)#login local
R1(config-line)#exec-timeout 10 0
R1(config-line)#access-class 10 in
R1(config)#login block-for 120 attempts 3 within 60   ←防暴力破解

! 第4步 日志与时间戳
R1(config)#logging host 192.168.100.20
R1(config)#logging trap informational
R1(config)#logging source-interface Loopback0
R1(config)#service timestamps log datetime msec localtime

! 第5步 配置变更审计
R1(config)#archive
R1(config-archive)#log config
R1(config-archive-log-cfg)#logging enable
R1(config-archive-log-cfg)#notify syslog

! 第6步 AAA（生产推荐）
R1(config)#aaa new-model
R1(config)#aaa authentication login default group TACACS+ local
R1(config)#tacacs server TAC
R1(config-server-tacacs)#address ipv4 192.168.1.50
R1(config-server-tacacs)#key TacKey123
```

**加固完成后建议用扫描器（虚拟机环境内）对比加固前后开放的端口差异，形成可验证的基线报告。**

#### 10_5.1 控制平面保护（CoPP，CCNP）
限制到达设备自身的流量速率，防止 DoS 打死 CPU：

```latex
R1(config)#access-list 120 permit tcp any any eq 22
R1(config)#class-map match-all MGMT
R1(config-cmap)#match access-group 120
R1(config)#policy-map COPP
R1(config-pmap)#class MGMT
R1(config-pmap-c)#police 8000 conform-action transmit exceed-action drop
R1(config)#control-plane
R1(config-cp)#service-policy input COPP
```

> **注意**：CoPP 配错会把自己锁在外面。**先配 **`permit`** 管理流量，再配限速，最后才应用。** 生产环境务必在维护窗口操作并保留 Console 通道。

---

### 10_6 IPsec VPN：两阶段与 NAT 豁免
#### 10_6.1 两阶段（IKE Phase 1 / Phase 2）
```latex
   Phase 1（ISAKMP/IKE SA）：建"管理通道"
     - 协商加密/哈希/认证/DH 组/生命周期
     - 结果：一条双向的 ISAKMP SA
        │
        ▼
   Phase 2（IPsec SA）：在管理通道保护下建"数据通道"
     - 协商感兴趣流（ACL 定义的流量）
     - 结果：两条单向的 IPsec SA
        │
        ▼
   数据开始加密传输
```

#### 10_6.2 经典站点到站点配置
```latex
! 第1步 定义感兴趣流（两端镜像对称）
R1(config)#access-list 100 permit ip 192.168.1.0 0.0.0.255 10.0.0.0 0.0.255.255

! 第2步 Phase 1 策略
R1(config)#crypto isakmp policy 10
R1(config-isakmp)#encryption aes 256
R1(config-isakmp)#hash sha256
R1(config-isakmp)#authentication pre-share
R1(config-isakmp)#group 14
R1(config-isakmp)#lifetime 86400
R1(config)#crypto isakmp key VpnK3y address 200.1.1.2

! 第3步 Phase 2 变换集
R1(config)#crypto ipsec transform-set TS esp-aes 256 esp-sha256-hmac
R1(cfg-crypto-trans)#mode tunnel

! 第4步 加密映射并应用到出接口
R1(config)#crypto map CMAP 10 ipsec-isakmp
R1(config-crypto-map)#set peer 200.1.1.2
R1(config-crypto-map)#set transform-set TS
R1(config-crypto-map)#match address 100
R1(config)#interface gi0/0
R1(config-if)#crypto map CMAP
```

#### 10_6.3 NAT 豁免：IPsec 最经典的坑
**问题**：出站 PAT 会把源地址改写，改写后的流量**不再匹配感兴趣流 ACL**，于是不会进入隧道——隧道起来了，业务却不走隧道。

```latex
   内网 192.168.1.0/24 ──► 要去 10.0.0.0/8（走 VPN，不做 NAT）
   内网 192.168.1.0/24 ──► 要去 Internet（做 PAT）

   ★ 关键：在 NAT 的 ACL 里先 deny 掉 VPN 流量，再 permit 其他
```

```latex
R1(config)#access-list 101 deny   ip 192.168.1.0 0.0.0.255 10.0.0.0 0.0.255.255
R1(config)#access-list 101 permit ip 192.168.1.0 0.0.0.255 any
R1(config)#ip nat inside source list 101 interface gi0/0 overload
```

> **顺序不能反**：ACL 自上而下匹配，`deny VPN 流量` 必须在 `permit any` **前面**。

#### 10_6.4 现代写法：VTI（虚拟隧道接口）
```latex
R1(config)#interface Tunnel0
R1(config-if)#ip address 172.16.0.1 255.255.255.252
R1(config-if)#tunnel source gi0/0
R1(config-if)#tunnel destination 200.1.1.2
R1(config-if)#tunnel protection ipsec profile IPSEC-PROF
```

**VTI 的优势**：隧道变成一个**真实的三层接口**，可以在上面跑动态路由协议（OSPF/EIGRP/BGP），不必再维护感兴趣流 ACL——这是 CCNP 推荐的现代做法。

#### 10_6.5 验证
```latex
R1#show crypto isakmp sa          ←QM_IDLE = Phase 1 成功
R1#show crypto ipsec sa           ←看加解密包数是否增长
R1#show crypto map
R1#debug crypto isakmp
R1#debug crypto ipsec
```

**判读口诀**：`show crypto isakmp sa` 看到 **QM_IDLE** 说明 Phase 1 好了；`show crypto ipsec sa` 里 **pkts encrypt/decrypt 都在涨** 说明数据真的在走隧道。

---

### 10_7 案例小故事：ACL 上线，业务全断
> 需求很普通：只允许办公网访问财务服务器的 443 端口，其他一律拒绝。
> 工程师写了：
> 自信地应用到接口，结果**整个办公网断了**——不只是访问财务服务器，连上网、DNS、打印全都不通。
> 他懵了：我只写了一条 permit，怎么会全断？
> 师傅过来一看就笑了：**ACL 末尾有一条隐含的 **`deny ip any any`。你只放通了 443，其余所有流量——包括 DNS 查询、HTTP 上网——全被这条看不见的规则丢弃了。
> **正确的上线姿势**（这是生产环境的标准做法）：
> 第三步花了两天——期间发现了 DNS、NTP、域控 LDAP、杀软更新四个"没想到"的流量。如果第一天直接收紧，这些业务会陆续"爆雷"，而且每次都是用户先发现。
> **复盘**：
> + **现象**：ACL 应用后业务全断；
> + **根因**：忽略末尾隐含 `deny ip any any`；
> + **修复**：先 permit any 兜底 → 观察 → 逐条收紧；
> + **经验**：**ACL 上线永远分两步走**。先放后收，用 `show access-lists` 的计数作为决策依据，而不是拍脑袋；
> + **附带收获**：编号 ACL 只适合临时观察，**定稿一律用命名 ACL**——因为它支持按序号插入、逐条删除，而编号 ACL 的 `no access-list 101 ...` 会连带删掉整张表。

```latex
access-list 101 permit tcp 192.168.1.0 0.0.0.255 host 10.1.1.10 eq 443
```

```latex
! 第一步：末尾加一条"兜底放行"，先让业务不受影响
access-list 101 permit tcp 192.168.1.0 0.0.0.255 host 10.1.1.10 eq 443
access-list 101 permit ip any any          ←临时兜底

! 第二步：跑一段时间，用 show access-lists 看实际命中情况
!        看哪些流量真的需要（DNS? NTP? 域控? 杀毒软件更新?）

! 第三步：改用命名 ACL 定稿（★编号 ACL 无法干净地逐条删除，定稿一律用命名 ACL）
ip access-list extended TO-FINANCE
 permit tcp 192.168.1.0 0.0.0.255 host 10.1.1.10 eq 443   ←原需求
 permit udp any any eq domain                             ←DNS（观察期发现的）
 permit udp any any eq ntp                                ←时间同步（观察期发现的）
 permit tcp any host 10.1.1.20 eq 389                     ←域控 LDAP（观察期发现的）
 permit tcp 192.168.1.0 0.0.0.255 any eq 80               ←HTTP 上网
 permit tcp 192.168.1.0 0.0.0.255 any eq 443              ←HTTPS 上网
 permit ip any any                                        ←仍是兜底，观察期结束再删
interface gi0/0
 ip access-group TO-FINANCE in

! 第四步：观察期结束后删掉兜底，让末尾隐含的 deny ip any any 生效
ip access-list extended TO-FINANCE
 no permit ip any any
 deny ip any any log                                      ←显式写出来，并记录被拒流量
```

**延伸：ACL 排错的黄金判据**

```latex
show access-lists 某条规则计数增长了吗？
   增长 → 流量命中了这个 ACL，问题在规则内容（放/拦判断）
   不增长 → 流量没走到这里，问题在路由/接口方向，去查别处
```

---

### 10_8 场景笔记：这一章该记什么
#### 10_8.1 必记内容
1. **你的网络的 ACL 台账**：编号/名称、应用接口、方向、用途、最后修改时间与变更人；
2. **ACL 上线的两步法**——先兜底后收紧，写进变更流程；
3. **NAT 豁免的 ACL 顺序**（deny VPN 在 permit any 之前）；
4. **加固基线的本地化版本**——把公司要求的密码策略、日志服务器地址、AAA 服务器地址填进 10_5 模板。

#### 10_8.2 实验记录模板
```latex
【实验编号】B10-01
【实验名称】扩展 ACL + NAT 协同 + IPsec NAT 豁免
【日期 / 耗时】____ / ____ 分钟
【拓扑】（画 ASCII 图，标出 ACL 应用的接口与方向）
【需求】
  - 只允许办公网访问服务器的 443
  - VPN 流量不被 NAT 转换
【关键配置】
  ip access-list extended / ip access-group in / time-range
  crypto isakmp / ipsec transform-set / crypto map
  NAT 豁免 ACL（deny 在前）
【验证清单】
  [ ] show access-lists 能看到规则与匹配计数
  [ ] 放通的业务通，未放通的被拒（分别测）
  [ ] 计数随测试流量增长（截图/抄录数字）
  [ ] 时间型 ACL：改设备时间验证策略生效/失效
  [ ] IPsec：show crypto isakmp sa 显示 QM_IDLE
  [ ] show crypto ipsec sa 的 pkts encrypt 与 decrypt 都在增长
  [ ] 隧道内业务互通，且 show ip nat translations 中无隧道流量（豁免成功）
【人为故障复现 1】
  操作：ACL 只写 permit 443，不加兜底
  现象：全网断
  根因：末尾隐含 deny ip any any
  修复：先 permit ip any any 兜底，观察后再收紧
【人为故障复现 2】
  操作：ACL 应用在错误方向（in 写成 out）
  现象：规则不生效，计数不增长
  定位：show ip interface 看 in/out
  修复：改方向
【人为故障复现 3（NAT 豁免）】
  操作：NAT ACL 中 permit any 写在 deny VPN 之前
  现象：隧道起来了但业务不走隧道，show crypto ipsec sa 计数不涨
  根因：VPN 流量先被 PAT 改写，不再匹配感兴趣流
  修复：deny VPN 语句移到最前
【ACL 观察记录】
  兜底期间发现的"意外流量"清单：
  1. ____ 端口 ____ 用途 ____
  2. ____ 端口 ____ 用途 ____
【复盘一句话】____
【遗留问题】____
```

#### 10_8.3 实用验证清单
- [ ] 能说出标准 ACL 与扩展 ACL 的放置原则及原因；
- [ ] 能背出 ACL 五条规则（尤其是隐含 deny）；
- [ ] 能独立配通时间型 ACL 并验证；
- [ ] 能说出 CoPP 的作用与上线风险；
- [ ] 能解释 IPsec 两阶段各自建立什么；
- [ ] 能独立配出 NAT 豁免并解释 deny 语句的顺序要求。

---

### 10_9 进阶延伸
1. **802.1X + ISE**：从"端口绑定 MAC"升级为"身份绑定"，支持动态 VLAN 下发与终端合规检查（CCNP 安全重点）；
2. **MACsec**：二层加密，防止局域网窃听与中间人（CCNP ENCOR 考点）；
3. **DMVPN**：多点动态 VPN，分支间按需建隧道，与 NHRP、mGRE、IPsec 配合使用；
4. **零信任网络访问（ZTNA）**：以身份与设备状态为访问判据，替代传统"内网可信"假设；
5. **ACL 与自动化**：用 Ansible 的 `ios_acls` 资源模块管理 ACL 集合，配置变更可评审、可回滚（见板块16）。

---

## 板块11 · 防火墙 — 从 PIX 到 ASA 与状态化策略
> 一句话定位：**ACL 是"无状态过滤"，防火墙是"状态化边界"——它记住每一条连接，出方向自适应、入方向显式授权。**

---

### 11_0 本板块知识地图
```latex
   安全级别（security level）是 PIX/ASA 体系的基石

   inside  = 100  ──────────────►  高可信
   dmz     = 50   ──────────────►  半可信
   outside = 0    ──────────────►  不可信

   ┌─────────┐        ┌──────────┐        ┌─────────┐
   │ inside  │───────►│   ASA    │───────►│ outside │
   │  100    │  允许  │          │  允许  │    0    │
   └─────────┘        └────┬─────┘        └─────────┘
                           │
                     ┌─────▼─────┐
                     │  DMZ (50) │  需显式 ACL 才能被 outside 访问
                     └───────────┘

   高 → 低：默认放行，返回流量靠状态表自动允许
   低 → 高：默认拒绝，必须 静态映射（或对象 NAT）+ ACL 放通
```

---

### 11_1 状态化防火墙的核心模型
PIX/ASA 的**安全级别（security level）**是整个体系的基石：

+ inside 默认级别 **100**，outside 默认 **0**；数值越高越可信；
+ **从高安全级别访问低安全级别**：默认放行（返回流量自动允许，因为状态表已记录该连接）；
+ **从低安全级别访问高安全级别**：默认拒绝，必须显式配置（静态映射 + ACL）。

```latex
   内部用户 → 访问外网 → 状态表记录会话 → 返回流量自动放行 ✅
   外部用户 → 访问内网 → 无会话记录 → 默认丢弃 ❌（需静态映射 + ACL）
```

**"状态化"的含义**：防火墙为每条连接维护一个条目（源/目的 IP、端口、协议、TCP 状态、空闲计时器）。返回流量能匹配已有条目就直接放行，无需再写一条反向 ACL——这与路由器上的 `established` 关键字思路一致，但更完整。

---

### 11_2 PIX 6.x 初始化流程逐条解析
PIX 6.x 时代的初始化是 14 步流程。这套命令已被 ASA 8.3+ 的对象 NAT 取代，但**背后的逻辑完全一致**——读懂它，你就能读懂任何一台在网运行的老防火墙。

| 步骤 | 命令 | 作用与解读 |
| --- | --- | --- |
| 1–4 | 上架、Console 连接、`enable`、`configure terminal` | `pixfirewall>` → `pixfirewall#` → `(config)#` 的模式切换，与 IOS 一致 |
| 5 | `interface ethernet0 auto` / `interface ethernet1 auto` | 网口速率双工自适应 |
| 6 | `ip address inside ip_address netmask` / `ip address outside ip_address netmask` | 划分内外网接口并配地址 |
| 7 | `global 1 ip_address-ip_address` | 定义全局地址池（编号 1），即内网外出时使用的公网地址范围 |
| 8 | `nat 1 ip_address netmask` | 指定哪些内网地址要被转换；`nat 1` 与 `global 1` 通过**编号 1 配对** |
| 9 | `route inside 0 0 {网关}` / `route outside 0 0 {网关}` | 内外方向的默认路由 |
| 10 | `static outside ip_address inside ip_address` | 静态地址映射（把内网服务器映射到公网地址） |
| 11 | `conduit global_ip port[-port] protocol foreign_ip [netmask]` | 允许外部 IP 访问被映射地址的指定端口（在防火墙上"开洞"） |
| 12 | `telnet local_ip [netmask]` | 限定允许通过 Telnet 管理 PIX 的源地址（不配则只能用 Console） |
| 13 | `wr mem` | 保存配置（对应 IOS 的 write memory） |
| 14 | `ping`、`show interface`、`show static` | 连通性测试与配置核查 |

#### 11_2.1 conduit 命令的四个参数
```latex
conduit permit|deny  {协议}  {被控制的全局地址} {端口}  {外部地址}

                             └─ 被访问（被控制）的地址
```

**示例**：允许外网任意主机访问映射到公网 202.100.1.10 的内网 Web 服务：

```latex
static (inside,outside) 202.100.1.10 192.168.1.10 netmask 255.255.255.255
conduit permit tcp host 202.100.1.10 eq 80 any
```

#### 11_2.2 完整 PIX 初始化示例
```latex
pixfirewall> enable
Password:
pixfirewall# configure terminal
pixfirewall(config)# interface ethernet0 auto
pixfirewall(config)# interface ethernet1 auto
pixfirewall(config)# ip address inside 192.168.1.1 255.255.255.0
pixfirewall(config)# ip address outside 202.100.1.1 255.255.255.0
pixfirewall(config)# global 1 202.100.1.5-202.100.1.10
pixfirewall(config)# nat 1 192.168.1.0 255.255.255.0
pixfirewall(config)# route outside 0 0 202.100.1.254
pixfirewall(config)# route inside 192.168.10.0 255.255.255.0 192.168.1.254
pixfirewall(config)# static (inside,outside) 202.100.1.10 192.168.1.10 netmask 255.255.255.255
pixfirewall(config)# conduit permit tcp host 202.100.1.10 eq 80 any
pixfirewall(config)# telnet 192.168.1.0 255.255.255.0
pixfirewall(config)# exit
pixfirewall# wr mem
pixfirewall# show interface
pixfirewall# show static
```

> **注意 **`nat 1`** 与 **`global 1`** 的配对关系**：编号必须一致，这是 PIX 时代最容易写错的地方。现代 ASA 的对象 NAT 不再依赖编号，而是直接把地址对象与转换规则绑在一起——这是一个明显的进步。

---

### 11_3 从 PIX 到 ASA：命令体系对照表
现代 ASA（8.3 及以后）用**对象（Object）+ 对象 NAT + ACL** 取代旧的 nat/global/static/conduit 体系。

| 需求 | PIX 6.x 体系 | 现代 ASA 8.3+ |
| --- | --- | --- |
| 内网 PAT 上网 | `nat 1 192.168.1.0 255.255.255.0` + `global 1 202.100.1.5` | `object network INSIDE-NET` → `subnet 192.168.1.0 255.255.255.0` → `nat (inside,outside) dynamic 202.100.1.5` |
| 复用出接口地址 | `global 1 interface` | `nat (inside,outside) dynamic interface` |
| 发布内网服务器 | `static (inside,outside) 202.100.1.10 192.168.1.10` | `object network WEB-SRV` → `host 192.168.1.10` → `nat (inside,outside) static 202.100.1.10` |
| 允许外网访问服务器 | `conduit permit tcp host 202.100.1.10 eq 80 any` | `access-list OUTSIDE-IN extended permit tcp any host 192.168.1.10 eq 80` + `access-group OUTSIDE-IN in interface outside` |
| 安全管理地址 | `telnet 192.168.1.0 255.255.255.0` | `ssh 192.168.1.0 255.255.255.0 inside` |
| 保存 | `wr mem` | `write memory` |
| 查看映射 | `show static`、`show nat` | `show nat`、`show xlate` |
| 查看连接 | `show conn` | `show conn detail` |

#### 11_3.1 ASA 8.3+ 最容易被搞错的一点
> **ACL 中引用的是真实（内网）地址，而非映射后的公网地址。**
> 旧配置里写公网地址（202.100.1.10），**新配置里必须写内网真实地址**（192.168.1.10）。

这是从 PIX 迁移到 ASA 时踩坑率最高的一条。

---

### 11_4 现代 ASA 完整最小配置模板
```latex
! 1. 接口与安全级别
hostname FW
interface GigabitEthernet0/0
 nameif inside
 security-level 100
 ip address 192.168.1.1 255.255.255.0
 no shutdown
interface GigabitEthernet0/1
 nameif outside
 security-level 0
 ip address 202.100.1.1 255.255.255.0
 no shutdown

! 2. 路由
route outside 0.0.0.0 0.0.0.0 202.100.1.254
route inside 192.168.10.0 255.255.255.0 192.168.1.254

! 3. 内网 PAT 上网
object network INSIDE-NET
 subnet 192.168.0.0 255.255.0.0
 nat (inside,outside) dynamic interface

! 4. 发布内网 Web 服务器
object network WEB-SRV
 host 192.168.1.10
 nat (inside,outside) static 202.100.1.10

! 5. 放通外网访问（★ ACL 里写真实地址 192.168.1.10）
access-list OUTSIDE-IN extended permit tcp any host 192.168.1.10 eq 80
access-group OUTSIDE-IN in interface outside

! 6. 管理
ssh 192.168.1.0 255.255.255.0 inside
write memory
```

#### 11_4.1 DMZ 设计
```latex
   outside (0)
       │
       │  显式 ACL：any → 10.10.10.10:80
       ▼
   ┌──────────────┐
   │  DMZ (50)    │  Web 服务器 10.10.10.10
   └──────┬───────┘
          │  显式 ACL：DMZ → inside 仅允许访问 DB:1433
          ▼
   ┌──────────────┐
   │  inside(100) │  数据库、内网办公
   └──────────────┘
```

**DMZ 的价值**：即使 Web 服务器被攻陷，攻击者也只拿到 DMZ 的立足点，**不能直接横扫内网**——因为 DMZ → inside 是被显式 ACL 严格限制的。

---

### 11_5 packet-tracer：ASA 上最强大的排错工具
```latex
FW# packet-tracer input inside tcp 192.168.1.10 1025 8.8.8.8 80 detail
```

它会**模拟**一个数据包从指定接口进入防火墙后的完整处理过程，并告诉你每一步的结果。典型输出结构如下（以 inside → outside 的访问为例）：

```latex
FW# packet-tracer input inside tcp 192.168.1.10 1025 8.8.8.8 80 detail

Phase: 1
Type: ROUTE-LOOKUP
Subtype: Resolve Egress Interface
Result: ALLOW
Config:
Additional Information:
found next-hop 202.100.1.254 using egress ifc  outside

Phase: 2
Type: ACCESS-LIST
Subtype: log
Result: ALLOW
Config:
access-group INSIDE-IN in interface inside
access-list INSIDE-IN extended permit ip any any
Additional Information:

Phase: 3
Type: NAT
Subtype:
Result: ALLOW
Config:
object network INSIDE-NET
 nat (inside,outside) dynamic interface
Additional Information:
Dynamic translate 192.168.1.10/1025 to 202.100.1.1/1025

Phase: 4
Type: IP-OPTIONS
Subtype:
Result: ALLOW
Config:
Additional Information:

Phase: 5
Type: NAT
Subtype: rpf-check          ←反向路径校验：回程流量能否匹配已有转换
Result: ALLOW
Config:
object network INSIDE-NET
 nat (inside,outside) dynamic interface
Additional Information:

Phase: 6
Type: FLOW-CREATION         ←创建状态表项（"状态化"就体现在这一步）
Subtype:
Result: ALLOW
Config:
Additional Information:
New flow created with id 12, packet dispatched to next module

Result:
input-interface: inside
input-status: up
input-line-status: up
output-interface: outside
output-status: up
output-line-status: up
Action: allow
```

**六个 Phase 各看什么**（记住这三句就够用）：

| Phase | 作用 | 被 DROP 时说明什么 |
| --- | --- | --- |
| ROUTE-LOOKUP | 查路由决定出接口 | 防火墙没有到目标的路由（先看 `show route`） |
| ACCESS-LIST | 匹配接口 ACL | 策略没放通——**绝大多数发布失败的卡点** |
| NAT | 做地址转换 | 没有匹配的 NAT 规则，或 ACL 写了公网地址 |
| IP-OPTIONS | 检查 IP 选项字段 | 存在 ASA 不支持的 IP 选项 |
| NAT（rpf-check） | 反向路径校验 | 回程流量无法匹配已有转换（常见于非对称路由） |
| FLOW-CREATION | 创建状态表项 | 连接数超限或资源不足 |

**使用场景**：

+ 业务不通时，先用 `packet-tracer` 模拟，看它卡在哪个 Phase；
+ 上线新策略前，用它预演"这条规则会不会生效"；
+ 比 `capture` 轻量，不需要真实流量。

> **这是 ASA 排错与 IOS 排错最大的区别**：IOS 上你只能等真实流量来，再 `show access-lists` 看计数；ASA 上你可以**主动模拟**，在没有业务流量时就能判断策略是否正确。

---

### 11_6 案例小故事：发布了服务器，外网还是访问不了
> 公司在 ASA 上发布一台内网 Web 服务器，配置看起来完全正确：对象 NAT 配了、ACL 也放通了 80 端口。但外网用户就是打不开网站。
> 工程师检查了三遍配置，逐字对照文档，没发现错误。他甚至怀疑是运营商封了 80 端口。
> 最后用 `packet-tracer` 模拟：
> 关键线索就在 Phase 1 的最后一行：**包的目的地址已经被 UN-NAT 翻译成了 192.168.1.10**，而 ACL 里写的还是 202.100.1.10——两者对不上，Phase 2 必然 DROP。
> **ACL 里写的是公网地址 202.100.1.10，而 ASA 8.3+ 要求写真实地址 192.168.1.10。**
> 这条规则在配置里静静躺着，从来没匹配过任何流量（因为经过 NAT 处理后，包的目的地址已经变成 192.168.1.10 了）。改成真实地址后，网站立刻可访问。
> **复盘**：
> + **现象**：对象 NAT 正确、ACL 存在，但服务不可达；
> + **根因**：ASA 8.3+ 的 ACL 应引用**真实（内网）地址**，配置里写成了映射后的公网地址；
> + **定位工具**：`packet-tracer` 明确告知 DROP 发生在 ACCESS-LIST 阶段；
> + **修复**：ACL 改为 `permit tcp any host 192.168.1.10 eq 80`；
> + **经验**：**从 PIX 迁移到 ASA，最危险的不是不会配，而是"按老习惯配，看起来完全对"。** `packet-tracer` 是唯一能在不产生真实流量的情况下暴露这类问题的工具。

```latex
FW# packet-tracer input outside tcp 8.8.8.8 1025 202.100.1.10 80

Phase: 1
Type: UN-NAT
Subtype: static
Result: ALLOW
Config:
object network WEB-SRV
 nat (inside,outside) static 202.100.1.10
Additional Information:
NAT divert to egress interface inside
Untranslate 202.100.1.10/80 to 192.168.1.10/80   ←★注意：地址已被翻译成真实地址

Phase: 2
Type: ACCESS-LIST
Subtype: log
Result: DROP                                      ←★卡在这里
Config:
access-list OUTSIDE-IN extended permit tcp any host 202.100.1.10 eq 80
Additional Information:

Result:
input-interface: outside
output-interface: inside
Action: drop
Drop-reason: (acl-drop) Flow is denied by configured rule
```

**ASA 排错四步**：

```latex
第1步 show run nat / show nat                                        → 确认转换规则
第2步 show xlate                                                     → 看实际生成的转换表项
第3步 packet-tracer input outside tcp 8.8.8.8 1025 192.168.1.10 80   → 模拟，定位卡在哪个 Phase
第4步 show conn / show logging                                       → 看真实连接与日志
```

> **第 第3步 步的两种写法都能用**：写公网地址 202.100.1.10 时，Phase 1 的 UN-NAT 会把翻译结果告诉你；写真实地址 192.168.1.10 时，则跳过 UN-NAT 直接进 ACL 检查。**先用公网地址测，能顺便验证 NAT 规则是否正确。**

---

### 11_7 场景笔记：这一章该记什么
#### 11_7.1 必记内容
1. **"ACL 写真实地址"这句话**——写在实验笔记第一页，每次配 ASA ACL 都默念一遍；
2. `packet-tracer`** 的标准用法与输出结构**——五个 Phase 分别做什么；
3. **你的网络的安全级别规划**：inside/dmz/outside 各多少，为什么；
4. **PIX → ASA 的对照表**——用于读懂老设备的配置（现网仍有大量 PIX 时代的配置在跑）。

#### 11_7.2 实验记录模板
```latex
【实验编号】B11-01
【实验名称】ASA 最小配置：PAT 上网 + 发布 DMZ 服务器
【日期 / 耗时】____ / ____ 分钟
【拓扑】
   [内网]─inside(100)─[ASA]─outside(0)─[Internet]
                        │
                     dmz(50)─[Web服务器]
【地址规划】
  | 区域   | 接口 | 地址           | 安全级别 |
  | inside | Gi0/0| 192.168.1.1/24 | 100 |
  | outside| Gi0/1| 202.100.1.1/24 | 0   |
  | dmz    | Gi0/2| 10.10.10.1/24  | 50  |
【需求】
  - 内网可上网（PAT）
  - 外网可访问 DMZ 的 Web 服务
  - DMZ 只能访问内网数据库的 1433 端口
【关键配置】
  nameif / security-level / object network / nat dynamic interface
  object network WEB-SRV / nat static / access-list（★真实地址）
【验证清单】
  [ ] show nameif 三个接口名称与级别正确
  [ ] show nat 能看到动态与静态 NAT 规则
  [ ] 内网 PC 能 ping 通外网
  [ ] packet-tracer input inside tcp 192.168.1.10 1025 8.8.8.8 80 → 结果 ALLOW
  [ ] packet-tracer input outside tcp 8.8.8.8 1025 202.100.1.10 80 → 结果 ALLOW
  [ ] 完整抄录一次 packet-tracer 输出，标出六个 Phase 各自做了什么
  [ ] show xlate 能看到生成的转换项
  [ ] DMZ → inside 1433 允许，其他被拒（分别测）
【人为故障复现 1】
  操作：ACL 里写公网地址
  现象：服务不可达
  定位：packet-tracer 显示 ACCESS-LIST 阶段 DROP
  根因：ASA 8.3+ 要求写真实地址
  修复：改成 192.168.1.10
【人为故障复现 2】
  操作：不给 DMZ 接口配 nameif
  现象：接口不参与转发
  根因：ASA 接口必须 nameif 才生效
  修复：补 nameif 与 security-level
【packet-tracer 输出抄录】
  贴一次完整输出，标注每个 Phase 的作用
【复盘一句话】____
【遗留问题】____
```

#### 11_7.3 实用验证清单
- [ ] 能解释安全级别模型（高→低默认放行、低→高需显式配置）；
- [ ] 能说出 PIX 的 `nat`/`global`/`static`/`conduit` 各自作用；
- [ ] 能独立配出 ASA 的对象 NAT + ACL 发布；
- [ ] 知道 ASA 8.3+ 的 ACL 必须写真实地址；
- [ ] 能熟练使用 `packet-tracer` 定位策略问题；
- [ ] 能设计一个简单的 DMZ 分区并说明其安全价值。

---

### 11_8 进阶延伸
1. **ASA 高可用（Active/Standby Failover）**：两台 ASA 的主备配置同步与切换，注意与 HSRP 的区别（Failover 同步的是整个状态表）；
2. **ASA 上的 IPsec 与 AnyConnect**：远程接入 VPN，配合 AAA 与动态访问策略；
3. **Firepower 与下一代防火墙（NGFW）**：应用识别、入侵防御（IPS）、URL 过滤，从"端口级"走向"应用级"；
4. **策略迁移与审计**：从 PIX 配置自动翻译为 ASA 对象 NAT 的思路，以及迁移后必须逐条验证；
5. **自动化**：用 Ansible 的 `asa_acls` 模块管理 ASA 策略，确保变更可评审、可回滚（见板块16）。

---

## 板块12 · 网络服务与运维管理
> 一句话定位：**配置能让网络跑起来，服务与运维决定它能不能长期、稳定、可追溯地跑。**

---

### 12_0 本板块知识地图
```latex
   网络服务与运维的几大件（按"先让它跑起来，再让它可观测"排序）

   DHCP   ── 地址自动分配（含中继）     → 用户不用手配
   NTP    ── 时间同步                   → 日志/证书/排错的地基
   Syslog ── 日志外送与留痕             → 事故后可追溯
   SNMP   ── 监控采集                   → 知道设备是否还活着
   NetFlow─ 流量分析                    → 知道是谁占了带宽
   QoS    ── 拥塞时的分配规则            → 关键业务优先
   SPAN   ── 端口镜像                    → 直接看包里装的什么

   配置管理：备份 / 升级 / 回滚 / 归档审计

   ─────────────────────────────────────────────
   排错时的取数顺序：
     "出事了没" → Syslog
     "哪台设备/哪个口" → SNMP
     "谁占的带宽" → NetFlow
     "包里到底是什么" → SPAN（最后手段）
```

---

### 12_1 DHCP：让地址分配自动化
#### 12_1.1 场景 A：路由器/三层交换机做 DHCP 服务器
```latex
R1(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.10   ←排除网关与保留地址
R1(config)#ip dhcp pool VLAN10
R1(dhcp-config)#network 192.168.1.0 255.255.255.0
R1(dhcp-config)#default-router 192.168.1.1        ←Option 3：网关
R1(dhcp-config)#dns-server 114.114.114.114 8.8.8.8   ←Option 6：DNS
R1(dhcp-config)#domain-name example.com           ←Option 15
R1(dhcp-config)#lease 0 8 0                       ←租期 0 天 8 小时 0 分
R1(dhcp-config)#exit
R1#show ip dhcp binding        ←已分配的地址与 MAC 绑定
R1#show ip dhcp pool           ←地址池使用率
R1#show ip dhcp conflict       ←地址冲突
R1#clear ip dhcp binding *     ←清空租约
```

**排错要点**：

+ DHCP 请求源地址是 `0.0.0.0`、目标是 `255.255.255.255`，**跨网段必须靠中继**；
+ 路由器必须有到地址池网段的**直连或静态路由**，否则不会响应。

#### 12_1.2 场景 B：DHCP 中继（跨 VLAN / 跨网段）
```latex
! 在网关接口（SVI 或子接口）上配
R1(config)#interface vlan 10
R1(config-if)#ip helper-address 192.168.100.10    ←指向 DHCP 服务器
```

`ip helper-address` 默认转发 8 类 UDP 广播（DHCP 67/68、TFTP 69、DNS 53、Time 37、NetBIOS 137/138、TACACS 49）。精简方式：

```latex
R1(config)#ip forward-protocol udp 67             ←只转发指定端口
R1(config)#no ip forward-protocol udp 69 53 37 137 138 49
```

**验证**：`show ip interface vlan 10` 查看 Helper address 行；PC 上 `ipconfig /renew`。

> **最常见的 DHCP 故障**：客户端拿不到地址，但服务器正常。九成是**中继没配**或**中继地址写错**。判断方法：在服务器上抓包，看有没有收到来自网关的 DHCP 请求——没有就是中继问题。

---

### 12_2 NTP：时间是一切日志与证书的地基
**为什么必须先做 NTP**：日志关联分析、证书校验、计费、排错时间线，全都依赖准确时间。**设备时间错了，跨设备排错就成了灾难**——你会发现 A 设备的日志显示 03:00，B 设备显示 03:47，根本无法判断因果。

```latex
! 基础配置
R1(config)#ntp server 192.168.100.1 prefer
R1(config)#ntp server 192.168.100.2
R1(config)#ntp source Loopback0
R1(config)#clock timezone CST 8                  ←中国标准时间

! 认证（生产推荐）
R1(config)#ntp authenticate
R1(config)#ntp authentication-key 1 md5 NtpK3y
R1(config)#ntp trusted-key 1

! 作为 NTP 服务器给下游设备
R1(config)#ntp master 3                          ← stratum 3
```

```latex
R1#show ntp status          ←是否 synchronized
R1#show ntp associations    ←关联状态与层级
R1#show clock detail        ←当前时间与时间源
```

#### 12_2.1 状态判读
`show ntp associations` 中地址前的符号：

| 符号 | 含义 |
| --- | --- |
| `*` | 当前同步源 |
| `~` | 本机 |
| `#` | 已配置但不可达 |
| `+` | 候选源 |

出现 `.INIT.` 或 `insane/invalid` 说明时钟源不可信（**层级差太大或时间跳跃过大**）。

> **NTP 的隐藏依赖**：时间型 ACL（板块10）、证书校验（IPsec/HTTPS）、日志关联分析，全都建立在 NTP 之上。**NTP 应该是你配置任何设备时的第一批命令之一，而不是最后想起来补的。**

---

### 12_3 Syslog：让设备"说话"并留痕
八个日志级别（数字越小越严重）：

| 级别 | 名称 | 含义 | 典型场景 |
| --- | --- | --- | --- |
| 0 | Emergency | 系统不可用 | 设备崩溃 |
| 1 | Alert | 需立即处理 | 温度过高 |
| 2 | Critical | 严重 | 模块失效 |
| 3 | Error | 错误 | 接口 down、认证失败 |
| 4 | Warning | 警告 | BPDU Guard 触发 |
| 5 | Notification | 正常但重要 | 线路协议变化、配置变更 |
| 6 | Informational | 信息 | 一般性提示 |
| 7 | Debugging | 调试 | debug 输出 |

```latex
R1(config)#logging host 192.168.100.20
R1(config)#logging source-interface Loopback0
R1(config)#logging trap informational                        ←发送级别 0–6
R1(config)#service timestamps log datetime msec localtime show-timezone
R1(config)#service timestamps debug datetime msec localtime
R1(config)#logging buffered 16384 informational
R1(config)#logging console warnings          ←控制台只显示警告及以上，避免刷屏
R1(config)#logging synchronous               ←日志不打断正在输入的命令
R1(config)#archive
R1(config-archive)#log config
R1(config-archive-log-cfg)#logging enable    ←记录配置变更（谁在何时改了什么）
R1(config-archive-log-cfg)#notify syslog
```

> **生产经验**：一定要开 `archive log config`。当出现"谁动了配置"的争议时，配置变更日志是最有力的证据。

**验证**：`show logging` 看缓冲区内容；在日志服务器上确认收到（UDP 514）。

---

### 12_4 SNMP：监控系统的通用语言
| 版本 | 安全模型 | 特点 | 建议 |
| --- | --- | --- | --- |
| **v1/v2c** | Community String（明文） | 简单、兼容好 | 内网只读监控可用，写权限与公网禁用 |
| **v3** | 用户 + 认证 + 加密 | authPriv（认证 + 加密） | **生产唯一推荐** |

```latex
! v2c（实验室 / 内网只读）
R1(config)#snmp-server community PublicRO RO 10        ←10 是标准 ACL，限定来源
R1(config)#snmp-server location 机房A-机柜3
R1(config)#snmp-server contact netops@example.com

! v3（生产推荐）
R1(config)#snmp-server group MONITOR v3 priv
R1(config)#snmp-server user monuser MONITOR v3 auth sha AuthP@ss priv aes 128 PrivP@ss
R1(config)#snmp-server host 192.168.100.30 version 3 priv monuser
```

**常用 OID**：

| 指标 | OID |
| --- | --- |
| 接口入向字节数 | 1.3.6.1.2.1.2.2.1.10（ifInOctets） |
| 接口出向字节数 | 1.3.6.1.2.1.2.2.1.16（ifOutOctets） |
| CPU 5 分钟利用率 | cpmCPUTotal5min |
| 内存已用 | ciscoMemoryPoolUsed |

> **SNMP v2c 的安全提醒**：community string 明文传输，且很多人用默认的 `public`/`private`。生产环境务必限定来源 ACL，且**绝不给 RW（写）权限**——拿到 RW 就等于能改设备配置。

---

### 12_5 NetFlow / IPFIX：看清"谁在跟谁通信"
**SNMP 回答"接口有多忙"，NetFlow 回答"是谁占了带宽、走的什么协议"。**

```latex
R1(config)#interface gi0/0
R1(config-if)#ip flow ingress                     ←在入方向采集
R1(config)#ip flow-export destination 192.168.100.40 9996
R1(config)#ip flow-export version 9
R1(config)#ip flow-export source Loopback0

R1#show ip flow interface
R1#show ip cache flow                            ←看 Top Talkers
```

`show ip cache flow` 能直接看到源/目的 IP、端口、字节数——**排查"带宽被谁吃了"最快的一招**。

**现代演进**：Flexible NetFlow 与**模型驱动遥测（MDT，基于 gRPC/gNMI）**，后者可做到秒级甚至亚秒级采集，是 CCNP/CCIE 网络保障域的重点（见板块16）。

---

### 12_6 QoS：拥塞发生时的分配规则
**一句话心智模型**：**QoS 不创造带宽。** 链路没拥塞时它几乎不起作用；一旦链路满了，它决定哪些包先走（语音、视频）、哪些等待（批量传输）、哪些丢弃（清道夫流量）。

#### 12_6.1 四步流水线
```latex
   第1步 分类 Classify  →  第2步 标记 Mark  →  第3步 队列 Queue  →  第4步 调度 Schedule
         │                  │                │                 │
    识别流量类型      打上 DSCP/CoS      放进不同队列      按策略出队
    (ACL/NBAR)      便于下游识别        (优先/保证/默认)   (PQ/CBWFQ/LLQ)
```

| 步骤 | 做什么 | 载体 |
| --- | --- | --- |
| 第1步 分类 Classify | 识别流量类型（ACL / NBAR / 已有标记） | class-map |
| 第2步 标记 Mark | 打 DSCP / CoS / IP Precedence | policy-map 里 `set dscp` |
| 第3步 队列 Queue | 把流量放进不同队列，分配带宽 | policy-map 里 `bandwidth` / `priority` |
| 第4步 调度 Schedule | 决定出队顺序与丢弃策略 | CBWFQ / LLQ / WRED |

#### 12_6.2 配置示例（语音优先）
```latex
! 第1步 分类：识别语音流量
R1(config)#class-map match-all VOICE
R1(config-cmap)#match dscp ef

! 第2步 分类：识别业务流量
R1(config)#class-map match-all BUSINESS
R1(config-cmap)#match access-group 110

! 第3步 策略：语音走优先队列，业务保证带宽
R1(config)#policy-map WAN-QOS
R1(config-pmap)#class VOICE
R1(config-pmap-c)#priority 512                 ←LLQ：严格优先，最多 512K
R1(config-pmap-c)#class BUSINESS
R1(config-pmap-c)#bandwidth 2048               ←CBWFQ：保证 2M
R1(config-pmap-c)#class class-default
R1(config-pmap-c)#fair-queue                   ←其余公平排队

! 第4步 应用到出接口
R1(config)#interface gi0/0
R1(config-if)#service-policy output WAN-QOS
```

#### 12_6.3 关键概念辨析
| 概念 | 作用 | 常见误区 |
| --- | --- | --- |
| **LLQ（priority）** | 严格优先队列，低延迟，但**有带宽上限**（防止饿死其他队列） | 以为配了 priority 就无限优先 |
| **CBWFQ（bandwidth）** | 保证最小带宽，拥塞时可用更多 | 以为它限制最大带宽（不限制） |
| ** policing（限速）** | 超速直接丢弃，硬限速 | 与 shaping 混淆 |
| ** shaping（整形）** | 超速先缓存，平滑发送 | 以为它丢包（它不丢，只是延迟） |

> **部署位置提醒**：QoS 只在**出方向、链路拥塞处**生效。把 service-policy 应用在 10G 核心口上，而瓶颈在 2M 的 WAN 口——那等于没配。**先找到瓶颈链路，再配 QoS。**

---

### 12_7 配置备份、升级与回滚
```latex
! 备份到 TFTP
R1#copy running-config tftp:
! 或使用 archive 定时自动备份
R1(config)#archive
R1(config-archive)#path tftp://192.168.100.50/$h-$t
R1(config-archive)#write-memory                 ←每次 write 自动备份
R1(config-archive)#time-period 1440             ←每 1440 分钟（1 天）自动备份

! IOS 升级（镜像名以 show version 里看到的为准，此处为 2900 系列示例）
R1#show version                                  ←先确认当前镜像文件名与 Flash 剩余空间
R1#copy tftp: flash:                             ←按提示填 TFTP 服务器 IP 与源文件名
R1(config)#boot system flash:c2900-universalk9-mz.SPA.155-3.M4a.bin
R1(config)#do write memory
R1#reload

! 回滚：改回原镜像的 boot system，reload
R1#show version                                  ←确认当前运行的镜像
```

**升级三原则**：

1. **保留旧镜像**——Flash 空间足够就别删，回滚靠它；
2. **先备份配置到设备外**——升级失败可能丢配置；
3. **确认 boot 变量指向正确**——`show boot` 检查，避免反复重启。

---

### 12_8 案例小故事：日志救了那次"甩锅"
> 一个分支机构周一早上报障：上周五还好好的，周一整个办公网上不了外网。
> 运维 A 说："我没动过配置。" 运维 B 说："我也没动。" 厂商说："设备没问题，是你们配置改了吧。"
> 争执了半天，有人想起这台路由器开了 `archive log config` 并外送 Syslog。登上日志服务器一查：
> 周五晚上 19:42，有人通过 vty（远程）登录，把默认路由的下一跳从专线网关改成了 10.0.0.254——那个地址根本不可达。配置变更记录、时间、来源 IP 一清二楚。
> 顺着 IP 查到是当晚做"网络优化"的第三方工程师。一条命令改回去，全网恢复。
> **复盘**：
> + **现象**：办公网上不了外网，无人承认改过配置；
> + **根因**：周五晚有人修改了默认路由，且新下一跳不可达；
> + **定位手段**：Syslog 中的配置变更记录（archive log config）+ 时间戳 + 来源 IP；
> + **经验三条**：
>     1. `archive log config`** 是"甩锅防御系统"**，成本几乎为零，价值极高；
>     2. **NTP 是它的前提**——时间不准，日志就无法与其他系统的记录对齐；
>     3. **变更必须走流程**——事后能查到是谁，不如事前有审批。

```latex
周五 19:42:17  %SYS-5-CONFIG_I: Configured from console by admin on vty0 (192.168.100.55)
周五 19:42:17  ip route 0.0.0.0 0.0.0.0 10.0.0.254
周五 19:42:18  no ip route 0.0.0.0 0.0.0.0 200.1.1.2
```

**同类场景的排错路径**：

```latex
业务异常
   │
   ├─ 是配置变了？ → show archive / 看 Syslog 的 CONFIG_I 记录
   ├─ 是时间问题？ → show ntp status（证书过期、时间型 ACL 失效）
   ├─ 是地址耗尽？ → show ip dhcp pool（使用率 100%）
   └─ 是带宽占满？ → show ip cache flow（Top Talkers）+ show interfaces
```

---

### 12_9 场景笔记：这一章该记什么
#### 12_9.1 必记内容
1. **NTP 服务器地址与同步状态**——`show ntp associations` 里哪个是 `*`；
2. **日志服务器地址与 trap 级别**——以及"能不能收到"的验证结果；
3. **SNMP 的 community / v3 用户**——写在密码本里，别写在文档里；
4. **QoS 策略的应用位置**——贴在哪个接口、出方向还是入方向、为什么瓶颈就在那里；
5. **SPAN 会话的开关记录**——抓完包是否 `no monitor session` 关掉了（忘关是 CPU 偏高的常见原因）；
6. **配置备份的存放路径与恢复演练结果**——备份从没恢复过的，等于没备份。

#### 12_9.2 实验记录模板
```latex
【实验编号】B12-01
【实验名称】DHCP 中继 + NTP + Syslog + QoS 基础
【日期 / 耗时】____ / ____ 分钟
【拓扑】（画 ASCII 图，标出服务器位置与 IP）
【需求】
  - 跨 VLAN 的 PC 能从中心 DHCP 服务器拿到地址
  - 设备时间与 NTP 服务器同步
  - 配置变更能外送到 Syslog 服务器
【关键配置】
  ip helper-address / ntp server / logging host / archive log config
【验证清单】
  [ ] 客户端 ipconfig /renew 能拿到正确网段、网关、DNS
  [ ] show ip dhcp binding 有对应表项
  [ ] show ip interface vlan 10 显示 Helper address
  [ ] show ntp associations 中至少有一个 *（已同步）
  [ ] show clock detail 时间与时区正确
  [ ] 改一条配置 → 日志服务器收到 CONFIG_I 记录（贴出来）
  [ ] show logging 本地缓冲区有内容
  [ ] SNMP：网管能读到接口流量（或 snmpwalk 有返回）
【人为故障复现 1】
  操作：删掉 ip helper-address
  现象：PC 拿不到地址（169.254.x.x）
  定位：服务器上抓包，无 DHCP 请求到达
  修复：补回 helper-address
【人为故障复现 2】
  操作：把设备时间改错（clock set 到错误时间）
  现象：日志时间错乱，时间型 ACL 行为异常
  定位：show ntp status
  修复：等 NTP 同步 / 手工校正
【人为故障复现 3】
  操作：logging trap 级别设成 emergencies（0）
  现象：日志服务器几乎收不到东西
  修复：改成 informational
【QoS 观察】
  瓶颈链路在哪个接口？____
  service-policy 应用在：接口 ____ 方向 ____
  拥塞时语音是否优先？测试方法：____
【复盘一句话】____
【遗留问题】____
```

#### 12_9.3 实用验证清单
- [ ] 能独立配通 DHCP 服务器与中继，并解释跨网段为何必须中继；
- [ ] 能说出 NTP 同步失败的判读方法（`*` / `#` / `.INIT.`）；
- [ ] 能背出 Syslog 八个级别的数字与名称；
- [ ] 能说出 SNMP v2c 与 v3 的区别及生产建议；
- [ ] 能解释 QoS 四步流水线，并知道 LLQ 与 CBWFQ 的差别；
- [ ] 已配置 `archive log config` 并验证能记录变更。

---

### 12_10 SPAN / RSPAN：把流量复制给抓包分析设备
前面所有手段回答的是"发生了什么"（Syslog/SNMP/NetFlow），**SPAN 回答"包里到底装的什么"**——它是排错的最后一道手段，也是唯一能看到报文内容的手段。

**本地 SPAN（源与目的在同一台交换机）**：

```latex
Switch(config)#monitor session 1 source interface gi0/1 both    ←抓取 gi0/1 的进出双向流量
Switch(config)#monitor session 1 destination interface gi0/24   ←复制到 gi0/24（接抓包机）
Switch#show monitor session 1
```

`both` 可换成 `rx`（只收）、`tx`（只发）。也可以按 VLAN 抓：

```latex
Switch(config)#monitor session 1 source vlan 10 rx              ←抓整个 VLAN 10 的入方向
```

**RSPAN（跨交换机远程镜像）**：源交换机把流量打上专用 VLAN（RSPAN VLAN）送到目的交换机。

```latex
! 源交换机
SW-Src(config)#vlan 900
SW-Src(config-vlan)#remote-span                       ←★声明这是 RSPAN VLAN
SW-Src(config)#monitor session 1 source interface gi0/1 both
SW-Src(config)#monitor session 1 destination remote vlan 900

! 目的交换机（同样要建 VLAN 900 并 remote-span）
SW-Dst(config)#monitor session 1 source remote vlan 900
SW-Dst(config)#monitor session 1 destination interface gi0/24
```

```latex
   [被监控口 gi0/1] ──► [SW-Src] ══ RSPAN VLAN 900 ══ [SW-Dst] ──► [抓包机 gi0/24]
```

**四个必知的限制（考试与现场都常考）**：

| 限制 | 说明 |
| --- | --- |
| 目的口不能当普通口用 | 被设为 destination 的端口**停止正常转发**，只输出镜像流量 |
| 目的口可以"偷走"带宽 | 如果源流量总和超过目的口速率，会丢包，抓到的不全 |
| 一个会话的源与目的 | 可以多个源，但通常只能一个目的口（部分平台支持多目的） |
| RSPAN VLAN 要全网放行 | 中间交换机 trunk 必须允许 RSPAN VLAN 通过 |

> **生产提醒**：SPAN 会消耗交换机资源，**排错完记得 **`no monitor session 1`** 关掉**。忘记关闭的 SPAN 会话长期运行，是交换机 CPU 莫名偏高的常见原因之一。

---

### 12_11 进阶延伸
走完本板块，你应该已经能回答"网络上发生了什么"和"包里装的什么"。下一步是把这些能力变成**常态化的、不依赖人的**机制：

2. **IP SLA**：主动探测（ICMP/TCP/UDP/HTTP），与浮动静态、HSRP、策略路由联动（见板块5）；
3. **模型驱动遥测（MDT）**：gRPC/gNMI 订阅式采集，秒级粒度，替代传统 SNMP 轮询；
4. **Catalyst Center（原 DNA Center）保障流程**：自动化地把"设备健康/客户端健康/应用健康"可视化；
5. **网络即代码**：用 Ansible 批量下发 NTP/Syslog/SNMP 基线配置，保证全网一致（见板块16）。

---

## 板块13 · IPv6 与双栈部署
> 一句话定位：**IPv4 地址早就分完了，IPv6 不是"未来技术"而是"现在就得会"——CCNA v1.1 已明显加强 IPv6 的考查深度。**

---

### 13_0 本板块知识地图
```latex
   IPv6 地址结构（128 位，8 段，每段 4 位十六进制）

   2001 : 0db8 : 0085 : a300 : 0000 : 0000 : 8a2e : 0370 : 7334
   └──┬──┘ └──┬──┘                                      
   全局路由前缀  子网ID                    接口ID（64 位）

   缩写规则「1」：每段前导零省略 → 2001:db8:85:a300:0:0:8a2e:370:7334
   缩写规则「2」：连续全零段用 :: 代替（★全地址中只能出现一次）
             → 2001:db8:85:a300::8a2e:370:7334
```

---

### 13_1 为什么要 IPv6
| 对比项 | IPv4 | IPv6 |
| --- | --- | --- |
| 地址长度 | 32 位（约 43 亿） | 128 位（约 3.4×10³⁸） |
| 表示法 | 点分十进制 192.168.1.1 | 冒号十六进制 2001:db8:85a3::8a2e:370:7334 |
| 头部 | 13 个字段，20–60 字节可变 | 8 个字段，**固定 40 字节**，复杂功能交给扩展头 |
| 广播 | 有 | **取消，改用组播 + 任播** |
| 配置 | 主要靠 DHCP | **SLAAC 无状态自动配置 + DHCPv6** |
| 分片 | 路由器可分片 | **只有源端分片，路由器不分片** |
| IPSec | 可选外挂 | 设计之初即内置 |
| NAT | 普遍使用 | 设计上不需要（但实践中仍有 NAT66/NAT64） |
| ARP | 有 | **取消，改用 ICMPv6 邻居发现（NDP）** |

#### 13_1.1 一个关键思维转变
**IPv6 的世界里每台设备都能有公网地址，NAT 不再是必需品。** 这同时意味着安全防护思路要变——**不能再依赖 NAT 的"隐式隐藏"，必须靠防火墙显式策略**。

```latex
   IPv4 思维：私网地址 + NAT = 天然隔离（其实不是安全机制）
   IPv6 思维：全球单播地址 + 防火墙显式策略 = 真实的安全边界
```

---

### 13_2 IPv6 地址：格式、缩写与类型
#### 13_2.1 缩写规则（必会）
```latex
原始：2001:0db8:0085:a300:0000:0000:8a2e:0370:7334

规则「1」 每段前导零可省略
     → 2001:db8:85:a300:0:0:8a2e:370:7334

规则「2」 连续的一个或多个全零段可用 :: 代替（全文中只能出现一次）
     → 2001:db8:85:a300::8a2e:370:7334
```

> **常见错误**：写两个 `::` 会导致地址无法唯一还原。`::`** 在一个地址里只能用一次。**

#### 13_2.2 地址类型
| 类型 | 前缀 | 作用 | 类比 IPv4 |
| --- | --- | --- | --- |
| **全球单播 GUA** | 2000::/3 | 公网可路由 | 公网地址 |
| **唯一本地 ULA** | FC00::/7（常用 FD00::/8） | 内网使用，不可在公网路由 | 私有地址（10/8 等） |
| **链路本地 LLA** | FE80::/10 | 每段链路必备，用于邻居发现与路由协议的下一跳 | 169.254.0.0/16 |
| **组播** | FF00::/8 | 取代广播 | 广播 |
| **任播** | 从单播空间分配 | 同一地址分配给多台设备，路由到"最近"的一台 | 无直接对应 |
| `::1` / `::` | — | 环回 / 未指定地址 | 127.0.0.1 / 0.0.0.0 |

#### 13_2.3 常用组播地址
| 地址 | 含义 |
| --- | --- |
| FF02::1 | 链路上的所有节点 |
| FF02::2 | 链路上的所有路由器 |
| FF02::5 / FF02::6 | OSPFv3 的 AllSPFRouters / AllDRouters |
| FF02::1:2 | DHCPv6 服务器/中继 |
| **请求节点组播 FF02::1:FFXX:XXXX** | 由目标 IPv6 地址后 24 位映射而来，**取代 ARP 广播** |

**取代 ARP 的机制**：主机要给 2001:db8:1::10 发包时，向 `FF02::1:FF00:10` 发送邻居请求（NS），只有对应主机会应答——把"广播打扰所有人"变成"**组播只打扰相关者**"。

#### 13_2.4 EUI-64：从 MAC 生成接口 ID
```latex
MAC: 00:1B:44:11:3A:B7

第1步 中间插入 FFFE：  00:1B:44:FF:FE:11:3A:B7
第2步 第 7 位取反（U/L 位）：02:1B:44:FF:FE:11:3A:B7

接口 ID = 021B:44FF:FE11:3AB7
配合前缀 2001:db8:1::/64 → 2001:db8:1:0:21b:44ff:fe11:3ab7
```

> **隐私提醒**：由于 EUI-64 会暴露 MAC 地址并带来隐私追踪问题，**现代操作系统默认使用随机生成的临时接口 ID（RFC 4941）**。这也意味着你在真机上看到的地址往往与 MAC 无关。
> 排错含义：**不能靠"从 MAC 推地址"来定位主机**，必须查邻居表或 DHCPv6 绑定表。

---

### 13_3 地址配置：SLAAC 与 DHCPv6
| 方式 | 获取什么 | 特点 |
| --- | --- | --- |
| **SLAAC（无状态自动配置）** | 前缀（来自 RA）+ 自生成接口 ID + 默认网关 | 无需服务器；**DNS 需另配** |
| **DHCPv6 无状态** | 只给 DNS、域名等附加参数（地址仍由 SLAAC 生成） | RA 中设置 `other-config-flag` |
| **DHCPv6 有状态（托管模式）** | 分配完整地址（类似 DHCPv4） | 便于地址审计与管理 |

#### 13_3.1 SLAAC 的工作流程
```latex
1. 路由器周期性发送 RA（Router Advertisement），携带前缀与默认网关信息
2. 主机用前缀 + EUI-64 或随机值生成接口 ID
3. 执行 DAD（重复地址检测）确保地址不冲突
4. 把 RA 的源地址（链路本地地址）作为默认网关
```

#### 13_3.2 配置示例
```latex
! 三层交换机/路由器：开启 IPv6 路由并配置 SLAAC
Core(config)#ipv6 unicast-routing                      ←★ 等价于 IPv4 的 ip routing
Core(config)#interface vlan 20
Core(config-if)#ipv6 address 2001:db8:0:20::1/64
Core(config-if)#ipv6 address fe80::1 link-local
Core(config-if)#no shutdown

! DHCPv6 无状态（RA 中提示主机去找 DHCPv6 拿 DNS）
Core(config-if)#ipv6 nd other-config-flag
Core(config-if)#ipv6 dhcp relay destination 2001:db8:0:10::100

! DHCPv6 有状态（托管模式）
Core(config-if)#ipv6 nd managed-config-flag
```

#### 13_3.3 路由器端 DHCPv6 服务器（有状态）
```latex
R1(config)#ipv6 dhcp pool VLAN20
R1(config-dhcpv6)#address prefix 2001:db8:0:20::/64
R1(config-dhcpv6)#dns-server 2001:db8:0:10::53
R1(config-dhcpv6)#domain-name example.com
R1(config)#interface vlan 20
R1(config-if)#ipv6 dhcp server VLAN20
```

#### 13_3.4 验证
```latex
R1#show ipv6 interface vlan 20       ←地址、组播组、RA 相关标志
R1#show ipv6 neighbors               ←★邻居表（取代 ARP 表）
R1#show ipv6 route
R1#show ipv6 dhcp binding
```

---

### 13_4 IPv6 路由：静态与 OSPFv3
#### 13_4.1 静态路由
```latex
R1(config)#ipv6 route 2001:db8:2::/64 2001:db8:1::2
R1(config)#ipv6 route ::/0 2001:db8:1::2          ←默认路由
R1(config)#ipv6 route 2001:db8:2::/64 2001:db8:1::2 130    ←浮动静态
```

> **注意**：IPv6 静态路由写下一跳时，可以用**对端的链路本地地址**（这是 IPv6 的常见写法，因为 LLA 在链路上稳定），但必须带出接口：

```latex
R1(config)#ipv6 route 2001:db8:2::/64 gi0/0 FE80::2
```

#### 13_4.2 OSPFv3
OSPFv3 与 OSPFv2 的关键差异：

| 对比项 | OSPFv2（IPv4） | OSPFv3（IPv6） |
| --- | --- | --- |
| 运行基础 | 基于**网段**（network 语句） | 基于**链路**（接口级启用） |
| 认证 | 自身支持（明文/MD5） | **依赖 IPsec**（AH/ESP） |
| Router-ID | 可自动选取 | **必须手工配置**（否则无 IPv4 地址时起不来） |
| 地址族 | 仅 IPv4 | 支持地址族，可同时承载 IPv4/IPv6 |
| 邻居标识 | 用 Router-ID 标识 | 同样用 Router-ID（仍是 32 位点分十进制格式） |
| 组播地址 | 224.0.0.5 / 224.0.0.6 | FF02::5 / FF02::6 |

**OSPFv3 的 LSA 名称已重命名**（这是考试常考的对照关系）：

| 类型 | OSPFv2 名称 | OSPFv3 名称 |
| --- | --- | --- |
| 1 | Router LSA | Router-LSA |
| 2 | Network LSA | Network-LSA |
| 3 | Summary LSA | Inter-Area-Prefix-LSA |
| 4 | Summary ASBR LSA | Inter-Area-Router-LSA |
| 5 | AS External LSA | AS-External-LSA |
| 7 | NSSA External LSA | NSSA-LSA |
| 8 | （无） | **Link-LSA**（仅在链路内泛洪，通告链路本地地址） |
| 9 | （无） | **Intra-Area-Prefix-LSA**（承载前缀信息） |

> **为什么 OSPFv3 要新增 8/9 两类**：OSPFv2 的 Type-1/2 LSA 里同时携带"拓扑"和"前缀"两件事；OSPFv3 把拓扑与前缀彻底解耦——拓扑靠 1/2 类，前缀靠 8/9 类。好处是**前缀变化时不需要重跑 SPF**，收敛更快。这是 OSPFv3 设计上最本质的改进。

```latex
! 方式一：接口级启用（推荐）
R1(config)#ipv6 unicast-routing
R1(config)#ipv6 router ospf 1
R1(config-rtr)#router-id 1.1.1.1                  ←★必须手工配
R1(config-rtr)#exit
R1(config)#interface gi0/0
R1(config-if)#ipv6 ospf 1 area 0

! 验证
R1#show ipv6 ospf neighbor
R1#show ipv6 ospf interface gi0/0
R1#show ipv6 route ospf
```

---

### 13_5 双栈部署与过渡技术
```latex
   双栈（Dual Stack）：设备同时跑 IPv4 与 IPv6
   ┌────────────────────────────┐
   │  应用层                     │
   │  ┌─────────┐ ┌─────────┐  │
   │  │  IPv4   │ │  IPv6   │  │  ← 两端都配，按 DNS 返回结果选
   │  └────┬────┘ └────┬────┘  │
   │       └───────────┘       │
   │        同一张二层网         │
   └────────────────────────────┘
```

| 过渡技术 | 原理 | 适用 |
| --- | --- | --- |
| **双栈** | 同时运行 v4/v6 | **首选**，最简单的长期方案 |
| **NAT64 / DNS64** | v6 -only 主机访问 v4 资源，边做地址转换 | 移动端/新建 IPv6 单栈网络 |
| **6to4 / ISATAP** | 把 IPv6 包封装在 IPv4 隧道里 | 过渡期临时方案 |
| **GRE / 手动隧道** | 手工建隧道打通 v6 孤岛 | 小规模互联 |

> **实用建议**：新建网络直接规划双栈；**不要为了"省事"把 IPv6 关掉**——关掉短期省事，长期会成为技术债，而且关闭 IPv6 本身在部分系统上就会引入奇怪问题。

---

### 13_6 IPv6 安全要点
1. **RA Guard**：防止非法路由器发送 RA 劫持网关（类似 DHCP Snooping 的思路）；

```latex
Switch(config)#ipv6 nd raguard policy HOST
Switch(config-nd-raguard)#device-role host
Switch(config)#interface gi0/5
Switch(config-if)#ipv6 nd raguard attach-policy HOST
```

2. **DHCPv6 Guard**：防止私接 DHCPv6 服务器；
3. **ND Inspection**：基于绑定表校验邻居发现报文；
4. **防火墙显式策略**：IPv6 下所有主机都有公网可达地址，**必须靠 ACL/防火墙**，不能指望 NAT；
5. **不要忽略链路本地地址**：FE80::/10 的流量在链路上自由流动，边界设备应过滤。

---

### 13_7 案例小故事：IPv6 配好了，就是不通
> 工程师在核心交换机上配好了 IPv6：地址配了、`ipv6 unicast-routing` 开了、OSPFv3 邻居也 FULL 了。但 PC 之间就是 ping 不通。
> 他检查了地址（`show ipv6 interface brief` 都对）、邻居表（有表项）、路由（`show ipv6 route` 有条目）——一切正常。
> 最后发现：**PC 上根本没拿到 IPv6 地址**。`ipconfig` 里只有 169.254 开头的链路本地地址，没有 2001:db8 开头的全球单播地址。
> 原因：核心交换机的 SVI 上**没有发 RA**。原来他用的是 `ipv6 address 2001:db8:0:20::1/64`，但接口上配了 `ipv6 nd ra suppress`——这是从别的配置模板里复制过来的一条命令，作用是**抑制 RA 发送**。没有 RA，主机就不知道前缀，SLAAC 自然无从谈起。
> 删掉 `ipv6 nd ra suppress`，PC 立刻拿到地址，ping 通。
> **复盘**：
> + **现象**：网络设备侧一切正常，主机侧拿不到 IPv6 地址；
> + **根因**：接口抑制了 RA 发送（`ipv6 nd ra suppress`），SLAAC 无法进行；
> + **排查路径**：`show ipv6 interface vlan 20` 看 RA 相关标志 → 主机 `ipconfig` 看是否拿到 GUA；
> + **经验**：**配置模板是效率工具，也是风险源。** 复制来的每一条命令都要知道它干什么。这一条在"只做 IPv6 静态地址"的场景下无害，在 SLAAC 场景下就是致命的。

**IPv6 不通的排查四步**：

```latex
第1步 主机拿到地址了吗？ipconfig / ifconfig（看有没有 GUA，而不只是 fe80::）
第2步 设备发 RA 了吗？show ipv6 interface（看 RA 标志）
第3步 邻居学到了吗？show ipv6 neighbors（取代 show ip arp）
第4步 路由通吗？show ipv6 route + ping ipv6
```

---

### 13_8 场景笔记：这一章该记什么
#### 13_8.1 必记内容
1. **你的网络的 IPv6 地址规划**：全球前缀是什么、每个 VLAN 分哪个 /64、服务器怎么编址；
2. **缩写规则的练习**：每天随手缩写三个地址，一周形成肌肉记忆；
3. **SLAAC / DHCPv6 的选择理由**：为什么这个网段用无状态，那个用有状态；
4. **OSPFv3 必须手工配 router-id**——这条最容易忘，写进检查清单。

#### 13_8.2 实验记录模板
```latex
【实验编号】B13-01
【实验名称】IPv6 双栈 + SLAAC + OSPFv3
【日期 / 耗时】____ / ____ 分钟
【拓扑】（画 ASCII 图，标出 IPv4/IPv6 双地址）
【地址规划】
  | 设备 | 接口 | IPv4 | IPv6 |
  | Core | Vlan20 | 192.168.20.1/24 | 2001:db8:0:20::1/64 |
【需求】
  - 网络侧 IPv6 互通
  - PC 通过 SLAAC 自动获取地址
  - OSPFv3 宣布网段
【关键配置】
  ipv6 unicast-routing / ipv6 address / ipv6 router ospf 1 / router-id
  interface 下 ipv6 ospf 1 area 0
【缩写练习】
  原始：2001:0db8:0000:0020:0000:0000:0000:0001
  缩写：________________（写两遍，规则第1步和第2步各做一次）
【验证清单】
  [ ] show ipv6 interface brief 接口有 GUA 与 LLA
  [ ] show ipv6 interface vlan 20 显示 RA 未被抑制
  [ ] PC 上 ipconfig 能看到 2001:db8 开头的地址（★不只是 fe80）
  [ ] show ipv6 neighbors 有 PC 的邻居表项
  [ ] show ipv6 route 有 OSPFv3 学到的路由（OI）
  [ ] show ipv6 ospf neighbor 状态 FULL
  [ ] ping ipv6 对端地址通
  [ ] 双栈：IPv4 与 IPv6 同时可用
【人为故障复现 1】
  操作：接口下 ipv6 nd ra suppress
  现象：PC 只拿到 fe80:: 地址，无 GUA
  定位：PC ipconfig + show ipv6 interface
  根因：RA 被抑制，SLAAC 无法进行
  修复：no ipv6 nd ra suppress
【人为故障复现 2】
  操作：OSPFv3 不配 router-id
  现象：进程起不来或邻居异常
  定位：show ipv6 ospf
  修复：router-id 1.1.1.1
【人为故障复现 3】
  操作：忘记 ipv6 unicast-routing
  现象：有地址但不转发（等价于 IPv4 的 ip routing）
  修复：ipv6 unicast-routing
【复盘一句话】____
【遗留问题】____
```

#### 13_8.3 实用验证清单
- [ ] 能独立缩写与还原 IPv6 地址，且知道 `::` 只能用一次；
- [ ] 能说出 GUA/ULA/LLA 三类地址的前缀与用途；
- [ ] 能手工完成一次 EUI-64 推导；
- [ ] 能独立配通 SLAAC 并验证主机拿到地址；
- [ ] 能说出 SLAAC / 无状态 DHCPv6 / 有状态 DHCPv6 的区别；
- [ ] 能独立配通 OSPFv3，并知道必须手工配 router-id。

---

### 13_9 进阶延伸
1. **OSPFv3 地址族（AF）**：同一进程同时承载 IPv4 与 IPv6，是 CCNP 的重点写法；
2. **IPv6 过渡技术深入**：NAT64/DNS64 的工作原理与部署场景；
3. **IPv6 组播（MLD / PIMv6）**：MLD Snooping 与 IPv6 组播路由；
4. **IPv6 与自动化**：用 Python 的 `ipaddress` 模块做 IPv6 子网划分与地址规划，比手算可靠得多；
5. **IPv6 安全加固**：RA Guard、DHCPv6 Guard、ND Inspection 的组合部署（CCNP ENCOR 考点）。

---

## 板块14 · 无线局域网基础
> 一句话定位：**无线网络是大多数用户的"第一跳"，也是 CCNA v1.1 明确强化的内容（Wi-Fi 6 / 802.11ax）。**

---

### 14_0 本板块知识地图
```latex
   企业无线架构：轻量 AP + WLC（Split-MAC）

   ┌────────┐                      ┌─────────────┐
   │  AP    │◄── CAPWAP 隧道 ────►│    WLC      │
   │(轻量)  │   UDP 5246 控制       │ 集中管理/策略 │
   └───┬────┘   UDP 5247 数据      └─────────────┘
       │
   无线空口
       │
   ┌───┴───┐ ┌───────┐ ┌───────┐
   │ 手机   │ │ 笔记本 │ │ IoT   │
   └───────┘ └───────┘ └───────┘

   AP 只管射频与实时帧处理；管理、认证、策略全部由 WLC 下发
```

---

### 14_1 无线网络的基本概念
| 术语 | 含义 |
| --- | --- |
| **SSID** | 网络名称，用户看到并选择的那个"WiFi 名" |
| **BSS** | 基本服务集：一个 AP 覆盖范围内的一组终端 |
| **BSSID** | 该 BSS 的标识，通常就是 AP 射频口的 MAC 地址 |
| **ESS** | 扩展服务集：多个 BSS 用同一 SSID 组成一张大网，支持漫游 |
| **信道 Channel** | 2.4GHz 与 5GHz 频段被划分的若干信道；**2.4G 只有 1/6/11 三个互不重叠信道** |
| **RSSI / SNR** | 信号强度指示 / 信噪比；SNR 越高（一般 ≥ 25dB）通话与高速率越稳定 |
| **AP** | 无线接入点，负责把无线帧转成有线帧 |
| **WLC** | 无线局域网控制器，集中管理大量 AP 与策略 |

#### 14_1.1 频段与代际
| 标准 | 名称 | 频段 | 关键改进 |
| --- | --- | --- | --- |
| 802.11n | Wi-Fi 4 | 2.4G / 5G | MIMO、40MHz 信道 |
| 802.11ac | Wi-Fi 5 | 5G | 更宽信道（80/160MHz）、更高阶调制 |
| **802.11ax** | **Wi-Fi 6 / 6E** | 2.4G / 5G / 6G | **OFDMA 上下行、MU-MIMO、TWT 省电、BSS Coloring 抗干扰** |

**Wi-Fi 6 的核心价值**不在"单设备峰值速率"，而在**高密度场景下的多设备并发效率**：

+ **OFDMA** 把信道切成更小的资源单元，同时服务多个终端（等于把"一次发一个大包"变成"一次发多个小包给不同的人"）；
+ **TWT（Target Wake Time）** 让物联网终端按约定时间唤醒以省电；
+ **BSS Coloring** 给不同 AP 的信号"染色"，减少同频干扰带来的退避。

---

### 14_2 自治 AP 与轻量 AP：两种架构
| 架构 | 特点 | 适用 |
| --- | --- | --- |
| **自治 AP（Autonomous）** | 每台 AP 独立配置 SSID、安全、VLAN，各自为政 | 家庭、小型办公室 |
| **轻量 AP + WLC（Split-MAC）** | AP 只负责射频与实时帧处理；管理、认证、策略由 WLC 集中下发 | 企业网、校园、医院 |

Split-MAC 架构下，**控制与管理功能集中在 WLC**：

+ 802.11 管理帧（认证、关联）处理；
+ 802.1X/EAP 认证与密钥管理；
+ 策略下发（SSID、VLAN、QoS、安全）；
+ 射频管理 RRM（信道、功率自动调整）。

---

### 14_3 CAPWAP：AP 与 WLC 之间的隧道
CAPWAP（Control And Provisioning of Wireless Access Points）提供 AP 与 WLC 之间的控制与数据传输：

| 通道 | 端口 | 内容 |
| --- | --- | --- |
| **控制通道** | UDP 5246 | 管理报文，经 **DTLS 加密** |
| **数据通道** | UDP 5247 | 用户数据（可选 DTLS 加密） |

#### 14_3.1 AP 加入 WLC 的八步状态机
```latex
   第1步 AP 启动：加载小型 IOS，必须先拿到 IP 地址（DHCP 或静态）
   第2步 WLC 发现：AP 寻找可加入的控制器
   第3步 CAPWAP 隧道：建立 DTLS 安全通道，双方用数字证书互相认证
   第4步 Join：AP 从候选列表中选择一个 WLC，发送 Join Request，WLC 回 Join Response
   第5步 下载镜像：若 AP 版本与 WLC 不一致，从 WLC 下载镜像并重启，然后回到第1步
   第6步 下载配置：拉取 RF、SSID、安全、QoS 等参数
   第7步 RUN 状态：开始提供 BSS 并接受无线客户端
   第8步 Reset：被 WLC 重置时拆除隧道与客户端关联，重启后重新走完整状态机
```

#### 14_3.2 WLC 发现方式（按顺序尝试）
1. 本地子网广播（CAPWAP Discovery Request）；
2. **DHCP Option 43**（在 DHCP 服务器上配置 WLC 地址）——**生产环境最常用**；
3. DNS 解析 `CISCO-CAPWAP-CONTROLLER.localdomain`；
4. 静态配置（AP 上手工指定）；
5. 已记住的上次连接过的 WLC。

> **排错要点（本板块第一考点）**：**AP 拿不到 IP 地址就不会启动 CAPWAP 流程。** 所以"AP 不上线"的第一检查项**永远是 DHCP 与 VLAN 划分**，而不是无线配置本身。
> **运维提示**：如果 AP 可能在两台 WLC 之间切换（rehome），必须保证两台 WLC 的**软件版本一致**，否则 AP 每次切换都要下载镜像重启，造成长时间中断。

---

### 14_4 SSID、VLAN 与流量模型
企业无线通常把不同 SSID 映射到不同 VLAN：

```latex
   员工 SSID "Corp"  → VLAN 10  → 内网资源
   访客 SSID "Guest" → VLAN 99  → 只能上网
```

| 模式 | 特点 |
| --- | --- |
| **集中转发（Local / Central Switching）** | 用户流量经 CAPWAP 隧道回到 WLC 再进入网络，策略集中、便于管控 |
| **本地交换（FlexConnect Local Switching）** | 分支 AP 的流量直接在本地交换出去，节省 WAN 带宽，WLC 仅做管理 |

> **选型**：总部用集中转发（策略统一、便于审计）；分支用本地交换（省专线带宽，即使 WLC 不可达，本地业务仍能跑）。

---

### 14_5 无线安全：从 WEP 到 WPA3
| 标准 | 特点 | 现状 |
| --- | --- | --- |
| **WEP** | 静态密钥，RC4 存在严重缺陷 | **已彻底淘汰，禁止使用** |
| **WPA / WPA2-Personal** | PSK 预共享密钥 | WPA2 仍广泛部署，但已被 KRACK 等攻击削弱 |
| **WPA2-Enterprise** | 802.1X + RADIUS，每用户独立密钥 | **企业推荐** |
| **WPA3-Personal** | SAE（对等同时认证），抗离线字典攻击 | 新网络首选 |
| **WPA3-Enterprise** | 802.1X + 192 位加密套件，更强 | 高安全要求场景 |
| **OWE / Enhanced Open** | 增强开放：无需认证但仍加密，防止被动窃听 | 咖啡厅等公共热点，替代"完全开放"网络 |

#### 14_5.1 考试要点对照
+ **PSK vs 802.1X（Enterprise）**：前者所有人共用一个密码（**离职后需全网改密码**），后者每用户独立凭证、可集中吊销；
+ **RADIUS/TACACS+ 在无线中的角色**：WLC 作为**认证者（Authenticator）**，把用户凭证转给 RADIUS 服务器做实际校验；
+ **802.1X 的三个角色**：请求者（Supplicant，终端）、认证者（Authenticator，AP/WLC/交换机）、认证服务器（AS，RADIUS/ISE）。

---

### 14_6 无线规划与优化要点
| 主题 | 要点 |
| --- | --- |
| **信道规划** | 2.4G 只用 1/6/11；5G 优先用非 DFS 信道；相邻 AP 用不同信道减少同频干扰 |
| **功率调整** | **不要一味开最大功率**——过大会导致同频干扰与"粘性客户端" |
| **覆盖标准** | 语音场景一般要求 ≥ −67dBm、SNR ≥ 25dB；数据场景可放宽到 −70dBm |
| **AP 布放** | 避免金属遮挡、远离微波炉与无绳电话等 |
| **5G 优先（Band Steering）** | 引导双频终端优先连 5GHz，把 2.4G 留给老旧设备 |
| **漫游** | 802.11r（快速 BSS 切换）、802.11k（邻区报告）、802.11v（网络辅助）配合实现快速无缝漫游 |
| **RRM** | WLC 自动调整信道与功率，但重大场景仍需人工规划后交给 RRM 微调 |

> **"功率不是越大越好"是新手最反直觉的一点**：AP 功率开满，终端能"听到"AP，但 AP 听不到终端的弱信号回传（**上下行不对称**），而且相邻 AP 互相干扰，整体容量反而下降。正确做法是**降低功率、增加 AP 密度**。

---

### 14_7 Packet Tracer 中的无线实验（可动手）
Packet Tracer 支持无线路由器、无线 AP、无线终端，可完成基础实验。

**企业级（WLC + LAP）建议在 Packet Tracer 中练的最小集合**：

1. 给 AP 所在的接入交换机端口划分管理 VLAN，确保 DHCP 可达；
2. 配置 DHCP 服务器的 **Option 43**（或 DNS 的 CISCO-CAPWAP-CONTROLLER 记录）；
3. 在 WLC 上创建两个 SSID（Corp → VLAN 10，Guest → VLAN 99）；
4. 观察 AP 依次进入 Downloading → Config → RUN 状态；
5. 终端分别关联两个 SSID，验证拿到的地址属于不同网段。

---

### 14_8 排错清单
| 现象 | 排查方向 |
| --- | --- |
| **AP 一直不上线** | AP 是否拿到 IP（DHCP 作用域/中继）；Option 43 或 DNS 记录是否配置；WLC 与 AP 之间三层是否可达；版本是否匹配 |
| AP 卡在 Downloading | AP 与 WLC 镜像版本不一致（会自动下载重启）；检查 WLC 上的镜像文件 |
| 终端搜不到 SSID | SSID 是否 enable；是否配置了隐藏；AP 是否在 RUN 状态；信道是否被禁 |
| 终端连上但拿不到地址 | SSID→VLAN 映射是否正确；该 VLAN 的 DHCP 是否可达；交换机 trunk 是否放行该 VLAN |
| 能连上但很慢 | 信号强度（RSSI）；SNR 是否 ≥ 25dB；同频干扰（信道规划）；AP 上终端数是否过多 |
| 漫游时断线 | 是否开启 802.11r/k/v；AP 间信号覆盖是否有盲区；认证方式（802.1X 会加重漫游延迟） |
| 部分终端连不上 | 终端是否支持该加密方式（老设备不支持 WPA3）；是否启用了 5G-only 而终端只有 2.4G |

---

### 14_9 案例小故事：AP 不上线，问题却在网络线那头
> 新大楼无线部署，二十个 AP 全部装好通电，但 WLC 上一个都没上线。
> 无线工程师检查了 WLC 配置、SSID、安全策略、Option 43——全对。他甚至怀疑是 AP 硬件批次问题，准备联系供应商换货。
> 网络组的同事过来随口问了一句："AP 拿到地址了吗？"
> 在接入交换机上看 `show ip dhcp snooping binding`——**空的**。再看 AP 所在端口：
> 施工方把 AP 接到了**默认 VLAN 1**，而 DHCP 服务器只给管理 VLAN 100 分配地址。AP 拿不到 IP，根本不会启动 CAPWAP——**它连"找 WLC"这一步都还没开始**。
> 把端口改到 VLAN 100，AP 三十秒内全部上线。
> **复盘**：
> + **现象**：AP 全部不上线，无线侧配置无异常；
> + **根因**：AP 所在接入端口 VLAN 划分错误，AP 拿不到 IP；
> + **排查路径**：先查 AP 有没有 IP（DHCP 绑定表 / 交换机 MAC 表），而不是先查 WLC；
> + **经验**：**"AP 不上线"的第一检查项永远是 DHCP 与 VLAN 划分。** 无线问题的很大一部分，根因其实在有线侧——这也就是为什么无线工程师必须懂交换。
> 后来他们把这条写进了施工验收清单：**AP 通电后，先在交换机上确认"端口 VLAN 正确 + AP 拿到地址"，再交给无线组调 WLC。**

```latex
interface Gi0/5
 switchport access vlan 1        ←★ 默认 VLAN，管理 VLAN 是 100
```

---

### 14_10 场景笔记：这一章该记什么
#### 14_10.1 必记内容
1. **AP 到 WLC 的八步状态机**——能说出 AP 卡在哪一步意味着什么；
2. **你的网络的 SSID → VLAN 映射表**：每个 SSID 对应哪个 VLAN、什么安全策略、给谁用；
3. **信道规划图**：每层楼的 AP 用哪几个信道（2.4G 只用 1/6/11）；
4. **覆盖验收标准**：语音 −67dBm/SNR 25dB，数据 −70dBm——这是验收时吵架的依据。

#### 14_10.2 实验记录模板
```latex
【实验编号】B14-01
【实验名称】WLC + LAP 部署：双 SSID 映射不同 VLAN
【日期 / 耗时】____ / ____ 分钟
【拓扑】
   [AP]─[接入交换机]─[三层核心]─[WLC]
                        │
                    [DHCP服务器]
【地址与 VLAN 规划】
  | VLAN | 用途     | 网段           | 说明 |
  | 100  | AP 管理  | 192.168.100.0/24 | AP 从这里拿地址 |
  | 10   | Corp     | 192.168.10.0/24  | 员工 |
  | 99   | Guest    | 192.168.99.0/24  | 访客 |
【需求】
  - AP 能上线
  - 两个 SSID 拿到的地址属于不同网段
【关键配置】
  接入交换机端口 VLAN / DHCP Option 43 / WLC 上创建 SSID 与 VLAN 映射
【验证清单】
  [ ] 交换机上看到 AP 的 MAC，且端口 VLAN = 管理 VLAN
  [ ] DHCP 绑定表里有 AP 的地址（★第一检查项）
  [ ] WLC 上 AP 状态为 RUN
  [ ] 两个 SSID 都能搜到
  [ ] 终端连 Corp 拿到 192.168.10.x
  [ ] 终端连 Guest 拿到 192.168.99.x
  [ ] Guest 不能访问内网（按设计）
【人为故障复现 1】
  操作：把 AP 端口改回 VLAN 1
  现象：AP 不上线
  定位：先看 DHCP 绑定表（空），再查端口 VLAN
  根因：AP 拿不到 IP，CAPWAP 无法启动
  修复：端口改到管理 VLAN
【人为故障复现 2】
  操作：删掉 DHCP Option 43
  现象：AP 拿到 IP 但找不到 WLC
  定位：AP 控制台看 discovery 过程
  修复：补回 Option 43
【人为故障复现 3】
  操作：SSID → VLAN 映射配错
  现象：终端连上但拿到错误网段地址
  修复：改映射
【复盘一句话】____
【遗留问题】____
```

#### 14_10.3 实用验证清单
- [ ] 能说出 BSS/BSSID/ESS/SSID 的区别；
- [ ] 能说出 Wi-Fi 6 相对 Wi-Fi 5 的三个关键改进及其价值；
- [ ] 能背出 CAPWAP 的两个端口号（5246/5247）；
- [ ] 能说出 AP 加入 WLC 的八步，以及卡在 Downloading 的原因；
- [ ] 能解释 PSK 与 802.1X 的本质差异与企业选型理由；
- [ ] 知道"AP 不上线先查 DHCP 与 VLAN"。

---

### 14_11 进阶延伸
1. **CCNP Wireless 体系**：ENWLSI/ENWLSD 已独立成体系，涵盖高密度设计、频谱分析、漫游优化；
2. **802.11ax 深入**：OFDMA 资源单元分配、BSS Coloring 的实际部署效果；
3. **无线与 ISE 联动**：基于身份的动态 VLAN 下发、BYOD 自助注册、终端合规检查；
4. **AI/ML 辅助射频优化**：Catalyst Center 的 AI Enhanced RRM；
5. **无线自动化**：用 WLC 的 REST API 批量创建 SSID、采集 AP 状态（见板块16 的自动化部分）。

---

## 板块15 · 排错方法论与故障案例库
> 一句话定位：**配置能力决定你能走多快，排错能力决定你能走多远。**

---

### 15_0 本板块知识地图
```latex
   分层排错法：自下而上，每层只回答一个问题

   第4步 传输/应用层   端口/服务/DNS/MTU
   第3步 网络层        IP/掩码/网关/路由/ACL/NAT
   第2步 数据链路层    VLAN/trunk/MAC/STP
   第1步 物理层        线缆/接口灯/DCE 时钟/双工速率

        ▲  从下往上逐层排除，或从上往下快速定位
        │
   四条执行原则：
   第1步 先近后远    第2步 双向验证
   第3步 一次只改一处 第4步 先恢复后查因
```

---

### 15_1 分层排错法：用 OSI 模型切分问题空间
网络排错最大的敌人是"**这里改改、那里试试**"。分层排错要求自下而上逐层排除，**每层只回答一个问题**。

| 层级 | 要确认的问题 | 关键命令 |
| --- | --- | --- |
| 第1步 **物理层** | 线缆接对了吗？接口灯亮吗？DCE 端配时钟了吗？双工速率匹配吗？ | `show ip int brief`、`show controllers s2/0`、`show interfaces`（errors/CRC） |
| 第2步 **数据链路层** | VLAN 划分对吗？trunk 放行了吗？MAC 学到了吗？STP 有没有阻塞？ | `show vlan brief`、`show interfaces trunk`、`show mac address-table`、`show spanning-tree` |
| 第3步 **网络层** | IP/掩码/网关对吗？路由表有去程和回程吗？ACL 拦了吗？NAT 转换了吗？ | `show ip route`、`show access-lists`、`show ip nat translations`、`ping`/`traceroute` |
| 第4步 **传输/应用层** | 端口放通了吗？服务在监听吗？DNS 解析对吗？MTU/MSS 合适吗？ | `telnet {目标IP} {端口}`、带 DF 位的 ping、`show ip nat statistics` |

#### 15_1.1 四条执行原则
1. **先近后远**：先 ping 自己网关，再 ping 下一跳，再 ping 目标。每一跳都通，才能把范围缩小到两点之间；
2. **双向验证**：网络问题很大比例出在"单向可达"——去程通回程没路由。**永远在两端各测一次**；
3. **一次只改一处**：改完立刻验证。不验证就继续改，等于同时引入多个变量，永远查不出根因；
4. **先恢复后查因**：现网优先用回退/切换手段恢复业务，把取证（配置快照、日志、抓包）留到恢复之后。

---

### 15_2 命令地图：按症状直接检索
| 症状 | 第一命令 | 后续命令 |
| --- | --- | --- |
| 接口起不来 | `show ip int brief` | `show interfaces {接口名}`、`show controllers`（串口） |
| 同网段不通 | `show vlan brief`、`show mac address-table` | `show interfaces trunk`、`show spanning-tree` |
| 跨网段不通 | `show ip route` | `show ip protocols`、`show ip ospf neighbor` |
| 网关 ping 不通 | `show ip int brief`、`show standby brief` | `show ip arp`、`debug arp` |
| 上网不通 | `show ip nat translations` | `show ip nat statistics`、`show access-lists`、`show ip route` |
| 部分流量不通 | `show access-lists`（看计数） | `show ip interface`（看 ACL 方向） |
| 时快时慢/丢包 | `show interfaces`（errors、CRC、collisions） | `show logging`、`show processes cpu` |
| 路由抖动 | `show ip route {目标网段}`、`show logging` | `show ip ospf neighbor`、`debug ip routing` |
| 设备不可管 | `show line vty 0 4`、`show ip ssh` | `show running-config |
| 配置莫名丢失 | `show startup-config`、`show version` | `show archive` |

---

### 15_3 十二个真实故障案例
#### 案例 1：三层交换机上 OSPF 路由表正常，但主机 ping 不通
**现象**：

```latex
PC>ping 192.168.2.2
Request timed out. ×4
Packets: Sent = 4, Received = 0, Lost = 4 (100% loss)
```

**排查**：S3560 上 `show ip route` 已通过 OSPF 学到 `O 192.168.2.0/24`，路由条目齐全；PC 网关配置正确。

**根因**：三层交换机未开启 IP 路由转发。此时只做二层交换，跨 VLAN 数据包被丢弃。

**修复**：`S3560(config)#ip routing`

**经验**：**控制平面与数据平面必须分开验证。路由表正确 ≠ 转发正常。**

---

#### 案例 2：首包超时，第二次 ping 全通
**现象**（静态路由、单臂路由、三层交换实验中均出现）：

```latex
Request timed out.
Reply from 192.168.2.2: bytes=32 time=28ms TTL=126 ×3
Packets: Sent = 4, Received = 3, Lost = 1 (25% loss)
```

**根因**：ARP 解析过程。PC 发包前需先获取网关 MAC，ARP 期间第一个 ICMP 包被丢弃。

**判断方法**：立刻再 ping 一次，若 0% 丢包即为正常。

**经验**：区分"首包 ARP 超时"与"真故障"的依据是**连续第二次 ping 的结果**。

---

#### 案例 3：OSPF 修复后前几包超时，随后全部通
**现象**（执行 `ping -t` 长 ping）：

```latex
Request timed out. ×3
Reply from 192.168.2.2: bytes=32 time=18ms TTL=125
Reply from 192.168.2.2: bytes=32 time=23ms TTL=125
```

**根因**：`ip routing` 刚启用，OSPF 邻接与路由表仍在收敛，叠加 ARP 解析。

**经验**：动态协议环境下判断故障是否恢复要用**长 ping + 观察趋势**，而不是单次 4 包的结论。

---

#### 案例 4：串口物理 up、协议 down
**现象**：`Serial2/0 up down`。

**根因**：DCE 端未配 `clock rate 64000`，或两端封装不一致（一端 PPP、一端 HDLC）。

```latex
R1#show controllers s2/0        ←确认本端 DCE/DTE
R1(config-if)#clock rate 64000
R1(config-if)#encapsulation ppp
```

**经验**：**串口故障第一条永远是"DCE 端有没有配时钟"。**

---

#### 案例 5：配置了 NAPT，但转换表是空的
**现象**：`show ip nat translations` 无输出。

**根因**：NAT 是**按流触发**的——没有内网到外网的实际流量就不会生成表项。这不是配置错误。

**判断**：看 `show ip nat statistics` 的 **hits**；若为 0，说明流量根本没被 ACL 或方向规则命中。

**修复**：先制造流量（ping），再看表。

---

#### 案例 6：ACL 应用后业务全断
**根因**：ACL 末尾存在隐含的 `deny ip any any`，配置 permit 不足。

**稳妥的上线方法**：先在末尾加 `permit ip any any` 跑一段时间，看实际需要哪些流量，再逐步收紧。

---

#### 案例 7：网关 ping 得通，但访问不了外网
**排查路径**：网关 `show ip route`（有无外网路由/默认路由）→ `show ip nat translations`（有无转换表项）→ 外网侧 `show ip route`（有无回程路由）。

**三种根因**：第1步 网关缺默认路由；第2步 NAT 未生效（地址未转换，外网回不来）；第3步 外网设备无回程路由。

**黄金判断法**：**逐跳 ping**——网关 → 出口路由器 → 对端接口 → 目标主机，**第一跳失败处即故障点**。

---

#### 案例 8：主设备宕机后业务没有切换
**三种常见原因**：

1. 备用设备未配置 HSRP；
2. 认证/Hello 参数不一致导致双方都认为自己是 Active；
3. 备用设备缺少对称的路由/NAT/ACL 配置。

**经验**：**冗余设计的核心是对称性。** 主备两台的所有业务配置必须一致，否则切换只是把故障从设备转移到配置。

---

#### 案例 9：新增交换机后全网 VLAN 消失
**根因**：VTP 配置修订号覆盖。该交换机 vlan.dat 中的 Configuration Revision 高于现网，接入后反向同步，清空现网 VLAN 数据库。

**修复与预防**：

```latex
第1步 立即拔线隔离故障交换机
第2步 在现网交换机上重建 VLAN（或从备份恢复）
第3步 所有新设备上架前：erase startup-config + delete vlan.dat + 设 transparent
第4步 接入后确认 Configuration Revision 归 0
```

---

#### 案例 10：能开小网页，但大文件传输必断
**根因**：MTU/MSS 不匹配。常见于 PPPoE（MTU 1492）、IPsec/GRE 隧道封装、或中间链路 MTU 小于 1500 而分片被丢弃。

```latex
! 测试方法（带 DF 位，不允许分片）
C:\> ping -f -l 1500 目标地址        ←若提示"需要拆分数据包但设置 DF"，说明 MTU 不足

! 通用解药
R1(config-if)#ip tcp adjust-mss 1452
```

**经验**：`ip tcp adjust-mss` 是穿越隧道/PPPoE 场景的标准动作，**建议作为隧道配置的默认项**。

---

#### 案例 11：IPsec 隧道起来了，业务却不通
**现象**：`show crypto isakmp sa` 显示 QM_IDLE，阶段二也有加解密计数，但两端内网互访失败。

**根因（最常见）**：未做 NAT 豁免——出口的 PAT 把源地址改写后，流量不再匹配感兴趣流 ACL，于是不会进入隧道。

```latex
R1(config)#access-list 101 deny   ip 192.168.1.0 0.0.0.255 10.0.0.0 0.0.255.255
R1(config)#access-list 101 permit ip 192.168.1.0 0.0.0.255 any
R1(config)#ip nat inside source list 101 interface gi0/0 overload
```

**经验**：**deny VPN 流量必须写在 permit any 之前。**

---

#### 案例 12：AP 全部不上线
**现象**：WLC 上 AP 列表为空。

**根因**：AP 未拿到 IP 地址（接入端口 VLAN 划分错误，或 DHCP 作用域/中继未配置）。

**排查**：先在接入交换机上 `show mac address-table`、`show ip dhcp snooping binding`，确认 AP 是否拿到地址。

**经验**：**AP 不上线的第一检查项永远是 DHCP 与 VLAN 划分**，而不是无线配置。

---

### 15_4 排错的"剧本化"流程（可直接照做）
```latex
【第一步：定界】业务不通，先问三个问题
  ├─ 影响范围：一台主机？一个 VLAN？全楼？全公司？
  ├─ 起始时间：什么时候开始的？之前改过什么？
  └─ 是否对称：去程通吗？回程通吗？（两端各测一次）

【第二步：分层】按物理→二层→三层→上层逐层排除
  ├─ show ip int brief      → 接口双 up 吗？
  ├─ show vlan / trunk / mac → 二层通吗？
  ├─ show ip route          → 路由有去有回吗？
  └─ show access-lists / nat → 被拦或被改了吗？

【第三步：定点】用逐跳 ping 找到"第一跳失败处"
  网关 → 下一跳 → 对端接口 → 目标主机

【第四步：修复与验证】
  ├─ 一次只改一处，改完立刻验证
  ├─ 现网优先恢复业务（回退/切换），取证留到恢复后
  └─ 写故障记录：现象→排查→根因→修复→经验

【第五步：复盘】
  ├─ 这个故障能不能通过监控提前发现？
  ├─ 能不能通过自动化检查避免？（见板块 16）
  └─ 更新板块 15 的案例库与板块 17 的速查表
```

---

### 15_5 案例小故事：五分钟定位，靠的不是聪明
> 一次演练：导师在实验拓扑里随机制造了一个故障，要求新人五分钟内定位。
> 新人 A 一上来就开始翻配置，从核心交换机看到路由器，再看 ACL，越看越乱，五分钟到点还没头绪。
> 新人 B 是这么做的：
> 两分钟解决。
> 导师点评：**A 在"找自己认为可能错的地方"，B 在"问设备现在是什么状态"。** 排错的效率差距，本质上是**方法论的差距**，不是知识量的差距。
> B 用的就是"先近后远"：先确认最近的一跳（网关）通不通，把问题空间从"整个网络"缩小到"PC 到网关之间"，然后一条 `show ip int brief` 就锁定答案。
> **可复用的三条习惯**：
> 1. **第一命令固定为 **`show ip int brief`——让设备先开口说话；
> 2. **先近后远逐跳 ping**——每通一跳，就把嫌疑范围缩小一段；
> 3. **不猜，只问**——用命令输出作为判断依据，而不是"我觉得应该是"。

```latex
第 30 秒：在 PC 上 ping 自己的网关      → 不通
第 60 秒：show ip int brief（网关设备） → 发现 Vlan20 是 administratively down
第 90 秒：no shutdown
第 120 秒：再 ping → 通，业务恢复
```

---

### 15_6 场景笔记：故障记录的标准模板
#### 15_6.1 故障记录模板（每次故障都按这个写）
```latex
【故障编号】F-____（按流水号）
【发生时间 / 恢复时间 / 业务中断时长】____ / ____ / ____
【影响范围】____（多少人、哪些业务、哪些区域）
【现象描述】
  - 用户视角：____
  - 设备视角：____（贴 show 输出）
【排查过程】（按时间线记录，包括走过的弯路）
  HH:MM  做了什么 → 看到什么 → 得出什么结论
  HH:MM  做了什么 → 看到什么 → 得出什么结论
  （每条一行，一直记到定位根因为止；走过的弯路同样要记，它比正确答案更有价值）
【根因】一句话：____
【修复动作】具体命令/操作：____
【验证】恢复后怎么确认的：____
【经验教训】
  - 这次学到的：____
  - 下次能更快的方法：____
  - 能不能提前发现（监控/告警）：____
  - 能不能自动检查（自动化断言）：____
【遗留问题 / 后续项】____
```

#### 15_6.2 现象卡（遇到没见过的报错就记一张）
```latex
【现象/报错原文】（逐字抄录设备输出，不要改写）
%CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch discovered on Gi0/1
【出现场景】____
【含义】____
【处置】____
【关联知识】板块 2 · Trunk native VLAN
```

#### 15_6.3 每周复盘的三件事
1. 本周记了几条故障/现象卡？**少于 3 条说明实验量不够**；
2. 有没有一条故障是"上次遇到过但没记住"的？有就把它升级到板块17 速查表；
3. 随机抽一张旧现象卡，能否在 30 秒内说出处置方法？说不出就重新做一遍实验。

---

### 15_7 综合演练：三个限时挑战
| 挑战 | 任务 | 时限 | 过关标准 |
| --- | --- | --- | --- |
| **挑战一** | 在拓扑中随机注入一个二层故障（VLAN/trunk/STP），定位并修复 | 5 分钟 | 能说出根因，且业务恢复 |
| **挑战二** | 随机注入一个三层故障（路由/ACL/NAT），定位并修复 | 5 分钟 | 用逐跳 ping 找到第一跳失败处 |
| **挑战三** | 随机注入一个服务类故障（DHCP/NTP/HSRP），定位并修复 | 8 分钟 | 用对应 show 命令证明根因 |

**演练规则**：

+ 由他人注入故障，自己**不看注入过程**；
+ 全程记录时间线（这就是 15_6.1 的模板内容）；
+ 结束后对照"标准排查路径"找差距——**不是看有没有修好，而是看走了多少弯路**。

---

### 15_8 实用验证清单（板块过关标志）
- [ ] 能背出分层排错法的四层及每层的关键命令；
- [ ] 能说出四条执行原则，并解释"为什么一次只改一处"；
- [ ] 看到"部分流量不通"能立刻想到 `show access-lists` 看计数；
- [ ] 看到"串口 up/down"能立刻想到 `show controllers` 查 DCE；
- [ ] 能独立完成三个限时挑战中的至少两个；
- [ ] 已按模板写过至少 3 份故障记录。

---

### 15_9 进阶延伸
1. **把排错变成自动化断言**：用 Ansible 采集 `show ip route`、`show standby brief` 并断言"必须存在某条路由""每个 VLAN 有且仅有一台 Active"，把人工排错变成 CI 检查（见板块16）；
2. **遥测驱动的主动发现**：MDT/gNMI 秒级采集，在用户报障前发现异常；
3. **故障演练文化（Game Day）**：定期在生产环境做可控故障演练，验证冗余是否真的有效；
4. **根因分析（RCA）方法**：5 Whys 与鱼骨图，把"设备坏了"推进到"流程为什么会允许它坏"；
5. **知识库闭环**：故障记录 → 现象卡 → 速查表 → 自动化断言，形成持续改进的闭环。

---

## 板块16 · CCNP / CCIE 进阶与网络自动化
> 一句话定位：**CCNA 让你配得通，CCNP 让你设计得对，CCIE 让你在 8 小时高压下交付一个可用网络——而自动化是三者共同的分水岭。**
> 说明：考试代码、权重与蓝图版本会随 Cisco 官方调整（如 ENCOR 无线内容逐步独立、SD-WAN 与自动化权重提升），**报名前请以官方 Exam Topics 为准**。本板块提供能力框架与实操内核。

---

### 16_0 本板块知识地图
```latex
   CCNP Enterprise = 核心（ENCOR）+ 集中（任选一门）
                          │
        ┌─────────────────┼─────────────────┐
        ▼                 ▼                 ▼
   300-410 ENARSI    300-415 ENSDWI   300-435 ENAUTO
   高级路由与排错      SD-WAN            自动化
                          
   CCIE EI = ENCOR 笔试（资格）+ 8 小时 Lab（Design + DOO）

   自动化的三层能力模型：
   基础：CLI 脚本化（Python + Netmiko）
   进阶：结构化数据（YANG）+ NETCONF/RESTCONF
   高阶：编排（Ansible/Terraform）+ 遥测（gNMI/MDT）+ CI/CD
```

---

### 16_1 CCNP Enterprise：核心 + 集中，两门考试
| 类别 | 考试 | 定位 |
| --- | --- | --- |
| **核心（必考）** | 350-401 ENCOR（Implementing and Operating Cisco Enterprise Network Core Technologies） | 双栈架构、虚拟化、基础设施、网络保障、安全、自动化六大域 |
| **集中（任选一门）** | 300-410 ENARSI | 高级路由与排错（OSPF/EIGRP/BGP/MPLS L3 VPN/DMVPN）——**最主流** |
| 集中（任选一门） | 300-415 ENSDWI | SD-WAN 实施（Catalyst SD-WAN） |
| 集中（任选一门） | 300-420 ENSLD | 企业网络设计 |
| 集中（任选一门） | 300-425 ENWLSD / 300-430 ENWLSI | 无线网络设计与实施 |
| 集中（任选一门） | 300-435 ENAUTO | 企业自动化（Python/API/Ansible） |

> **选哪门集中考试？** 三条经验：第1步 走路由交换主线、想最快拿证，选 **ENARSI**（与本库板块5/6/15 衔接最紧）；第2步 所在企业已上 SD-WAN，选 **ENSDWI**；第3步 想往自动化/网络开发转型，选 **ENAUTO**，它与板块16_4 的内容高度重合。

#### 16_1.1 ENCOR 的能力域（参考比例，随版本调整）
| 域 | 大致权重 | 关键内容 |
| --- | --- | --- |
| Architecture | 约 15% | 双栈设计、高可用SD-WAN 架构、SD-Access 控制/数据平面 |
| Virtualization | 约 10% | 虚拟化、VRF、GRE、IPsec 路径隔离 |
| **Infrastructure** | **约 30%** | **权重最高**：二层（STP/EtherChannel）、三层（EIGRP/OSPFv2/v3/BGP 选路）、IP SLA |
| Network Assurance | 约 10% | SPAN/RSPAN、NetFlow/IPFIX、Syslog/SNMP、模型驱动遥测、Catalyst Center 保障 |
| Security | 约 20% | 设备访问控制、REST API 安全、基础设施 ACL、802.1X、MACsec、零信任框架 |
| Automation | 约 15% | Python/JSON/XML、RESTCONF/NETCONF/YANG、Ansible/Terraform |

#### 16_1.2 考试形式的重要变化
**ENCOR 已把实验题（performance-based）集中在考试前段，后段为选择题。** 这意味着：

+ 前一个小时必须高效完成动手题，**不能在实验题上卡死导致后段时间不够**；
+ 备考方式要变：**用计时器模拟两段式节奏，把每次练习都当成限时排错**。

---

### 16_2 CCNP 阶段必须补齐的技术清单
#### 16_2.1 路由
| 技术 | 要点 |
| --- | --- |
| **OSPFv2 多区域** | ABR/ASBR、LSA 1/2/3/4/5/7、stub/NSSA、虚链路、区域间汇总、认证、快速收敛、BFD |
| **OSPFv3** | 基于链路运行、地址族、实例 ID、认证依赖 IPsec |
| **EIGRP** | DUAL 算法、可行距离/报告距离/可行后继、非等价负载均衡（variance）、命名模式、stub |
| **BGP** | eBGP/iBGP、属性（Weight/Local Preference/AS_PATH/MED/Origin）、选路规则、路由反射器、联邦、社群、next-hop-self |
| **重分发与路径控制** | 双向重分发、管理距离调整、route-map、distribute-list、prefix-list、offset-list、防环与次优路径 |
| **PBR** | 按源地址/应用选路：`route-map` + `ip policy route-map` |
| **VRF-Lite** | 多租户路由隔离与路由泄漏 |
| **组播** | IGMPv2/v3、IGMP Snooping、PIM-SM/DM、RP（静态/Auto-RP/BSR）、RPF |
| **IP SLA** | 探测下一跳可达性，与浮动静态路由/track/HSRP 联动 |

#### 16_2.2 交换
| 技术 | 要点 |
| --- | --- |
| **MST** | 多实例生成树，实例与 VLAN 映射，与 PVST+ 互操作 |
| **EtherChannel** | LACP/PAgP、二层与三层、负载均衡算法、误配保护 |
| **堆叠与虚拟化** | StackWise/VSS/vPC（跨设备链路聚合，消除 STP 阻塞端口） |
| **二层安全** | Port-Security、DHCP Snooping、DAI、IPSG、风暴控制、802.1X |

#### 16_2.3 服务与保障
QoS（分类/标记/队列/调度/监管整形，见板块12）、NTP/SNMPv3/NetFlow/遥测、SPAN/RSPAN、IP SLA、Catalyst Center 保障流程。

#### 16_2.4 安全与 VPN
基础设施 ACL、CoPP、MACsec、802.1X+ISE、站点到站点 IPsec（IKEv2/VTI）、DMVPN、零信任网络访问（ZTNA）。

---

### 16_3 CCIE Enterprise Infrastructure Lab：8 小时的压力测试
| 模块 | 内容 | 特点 |
| --- | --- | --- |
| **Design（设计模块）** | 给定业务需求与约束，产出设计方案文档 | 评分看**约束满足度与技术论证**，不是"画得好看" |
| **DOO（Deploy/Operate/Optimize）** | 在机架上完成配置、排错与优化 | 两模块连续进行，**必须同场次都通过** |

#### 16_3.1 与笔试的本质差异
+ 笔试考"**你知道什么**"，Lab 考"**你在约束下能交付什么**"。题目会明确限制手段（如"禁止使用静态路由""不得新增子网"），方案必须同时满足功能与约束；
+ **Lab 明确要求自动化能力**：用脚本或 API 完成配置与校验，而非纯手工敲命令；
+ **时间管理是核心能力**：8 小时里纠结一个 2 分的点、丢掉后面 20 分的题，是最常见的失败原因。

#### 16_3.2 备考节奏建议（12–18 个月）
```latex
阶段一（1–3 月）   补齐 ENCOR 全部考点，完成笔试
阶段二（4–8 月）   按技术领域专题突破（BGP/组播/IPsec/自动化各 1 个月）
阶段三（9–12 月）  全真模拟，每周 1–2 次 8 小时完整 Lab，练时间分配与体力
阶段四（考前 2 月）机架手速训练 + 设计文档模板固化 + 错题本复盘
```

> **经验之谈**：CCIE 的失败原因很少是"不会"，而是"**做完但没验证**"和"**时间分配崩了**"。每完成一个子任务立刻用对应 show 命令验证，是唯一的护身符。

---

### 16_4 网络自动化：三层能力模型
| 层级 | 技术 | 能力目标 |
| --- | --- | --- |
| **基础** | CLI 脚本化（Python + Netmiko/Paramiko） | 批量下发配置、批量采集 |
| **进阶** | 结构化数据（YANG 模型）+ NETCONF/RESTCONF | 模型驱动读写配置，具备校验能力 |
| **高阶** | 编排（Ansible/Terraform）+ 遥测（gNMI/MDT）+ CI/CD | 网络即代码，变更可评审、可回滚 |

#### 16_4.1 示例 1：Python + Netmiko 批量下发 VLAN
```python
# pip install netmiko
from netmiko import ConnectHandler

DEVICES = [
    {"host": "192.168.1.11", "username": "admin", "password": "P@ssword",
     "device_type": "cisco_ios"},
    {"host": "192.168.1.12", "username": "admin", "password": "P@ssword",
     "device_type": "cisco_ios"},
]

VLAN_CONFIG = [
    "vlan 10",
    " name Tech",
    "vlan 20",
    " name Sales",
]

for dev in DEVICES:
    net = ConnectHandler(**dev)
    prompt = net.find_prompt()
    print(f"===== {prompt} =====")
    output = net.send_config_set(VLAN_CONFIG)
    print(net.send_command("show vlan brief"))
    net.disconnect()
```

**价值**：把 50 台交换机的重复劳动压缩到几秒，且**永不敲错命令**——这正是自动化的本质：**幂等 + 可重复 + 无差错**。

#### 16_4.2 示例 2：RESTCONF 读取接口信息（模型驱动）
```python
import requests
import urllib3
urllib3.disable_warnings()

HOST = "192.168.1.11"
USER, PASS = "admin", "P@ssword"

url = f"https://{HOST}/restconf/data/ietf-interfaces:interfaces"
headers = {"Accept": "application/yang-data+json"}
resp = requests.get(url, auth=(USER, PASS), headers=headers, verify=False)
print(resp.status_code)
print(resp.json())
```

**与 CLI 抓取的本质区别**：RESTCONF 返回的是**结构化 JSON**，字段有明确定义，不依赖字符串解析。这正是"把 CLI 的脆弱性丢掉"的第一步。

#### 16_4.3 示例 3：Ansible 批量配置（网络即代码）
```yaml
# vlans.yml
- name: 批量下发接入交换机 VLAN
  hosts: access_switches
  gather_facts: false
  tasks:
    - name: 创建 VLAN
      cisco.ios.ios_vlans:
        config:
          - name: Tech
            vlan_id: 10
          - name: Sales
            vlan_id: 20
        state: merged

    - name: 把端口划入 VLAN 10
      cisco.ios.ios_l2_interfaces:
        config:
          - name: GigabitEthernet0/2
            access:
              vlan: 10
        state: merged
```

运行：`ansible-playbook -i inventory.ini vlans.yml`

> **自动化的正确姿势**：**不要在脚本里 **`show running-config`** 后做字符串匹配**——那是把 CLI 的脆弱性继承了下来。要用 **NAPALM / YANG 模型 / Ansible 资源模块**这类"有状态抽象"的工具，才能真正做到**幂等与可回滚**。

#### 16_4.4 学习路径（约 12 周）
```latex
1. Python 基础（变量、列表、字典、函数、文件读写、requests）  2 周
2. Netmiko 批量采集与下发                                    2 周
3. JSON/YAML 数据格式与 REST 概念                             1 周
4. RESTCONF/NETCONF 实践，读懂 YANG 模型树                   3 周
5. Ansible 完成一个完整项目（如"新大楼接入交换机批量开局"）     4 周
```

---

### 16_5 案例小故事：50 台交换机，两个人，一个下午 vs 一个脚本
> 新办公楼交付，50 台接入交换机需要开局：创建 8 个 VLAN、把 30 个端口按区域划进不同 VLAN、配管理 IP、开 SSH、关 Telnet、设 NTP 与 Syslog。
> **方案 A（老办法）**：两个人一台台敲。每人一天能敲 8–10 台，还要反复核对。预计 5 个工作日。第三天上，已经出现了两台配置不一致的问题（一个端口划错 VLAN），排查又花半天。
> **方案 B（自动化）**：一个人花了半天写一个 Ansible playbook + 一份 Excel 地址表（每台设备的管理 IP、端口-VLAN 映射）。跑一遍 **7 分钟**，全部完成，配置完全一致。
> 更关键的是后续：**哪台改错了，改表重跑一遍即可**，不用人肉回忆"上次是怎么配的"。
> **复盘**：
> + **表面收益**：5 天 → 7 分钟；
> + **真实收益**：**配置一致性**与**可重复性**。人肉敲 50 台一定会有差异，而这些差异就是半年后那次"莫名其妙故障"的种子；
> + **隐藏收益**：playbook 本身就是**文档**——新同事看一遍 YAML 就知道这个网络是怎么建的，比看 50 份 show run 强一百倍。
> **给犹豫者的建议**：不要一上来就想"做平台"。从**最枯燥的那件重复劳动**开始——批量改密码、批量采集版本、批量备份配置。第一个脚本能省下两小时，你就再也不想回去了。

**自动化的三个落地陷阱（提前避坑）**：

| 陷阱 | 表现 | 规避 |
| --- | --- | --- |
| **字符串匹配** | `show run` 里 grep 关键字判断状态 | 用结构化接口（RESTCONF/NAPALM/资源模块） |
| **非幂等** | 脚本跑两次结果不同（如重复加 VLAN） | 用 `state: merged/replaced/overridden` 这类声明式写法 |
| **无回滚** | 跑错了只能手工改回去 | 每次变更前自动备份配置；用 Git 管理 playbook |

---

### 16_6 场景笔记：这一章该记什么
#### 16_6.1 必记内容
1. **你的自动化脚本仓库结构**——inventory、playbook、变量表分开放，变量与逻辑分离；
2. **每段脚本的"跑之前/跑之后"对照**——贴 `show` 输出，证明它真的生效了；
3. **踩过的坑与错误信息**——requests 的 SSL 警告、Netmiko 的 device_type 写错、Ansible 的集合没装……这些错误信息值得记，因为下次还会遇到；
4. **可复用片段库**：登录模板、批量采集模板、变更前后对比模板。

#### 16_6.2 实验记录模板
```latex
【实验编号】B16-01
【实验名称】Netmiko 批量采集 + Ansible 批量下发 VLAN
【日期 / 耗时】____ / ____ 分钟
【环境】EVE-NG / 真机 / 模拟器，设备型号与 IOS 版本：____
【需求】
  - 批量采集 5 台设备的 show version
  - 批量下发 2 个 VLAN 并验证
【关键代码】
  贴脚本核心部分（不要整份贴，贴关键 10–20 行）
【运行前状态】
  贴 show vlan brief（节选）
【运行后状态】
  贴 show vlan brief（节选）
【验证清单】
  [ ] 脚本能跑通，无异常退出
  [ ] 5 台设备全部执行成功（有成功计数）
  [ ] 设备上 show vlan brief 确认 VLAN 已创建
  [ ] 再跑一遍脚本 → 结果一致（幂等性验证 ★）
  [ ] 错误场景：故意写错一台的 IP，脚本能继续处理其他设备（异常处理）
【幂等性测试记录】
  第一次运行：新增 ____ 个 VLAN
  第二次运行：新增 ____ 个 VLAN（应为 0，且不报错）
【人为故障复现】
  操作：把 device_type 写成 cisco_asa
  现象：登录报错 ____
  修复：改回 cisco_ios
【效率对比】
  手工完成预计 ____ 分钟 / 脚本 ____ 分钟
【复盘一句话】____
【遗留问题】____
```

#### 16_6.3 实用验证清单
- [ ] 能说出 CCNP 的"核心 + 集中"结构与 ENCOR 六大域；
- [ ] 知道 ENCOR 实验题集中在考试前段，并能据此调整备考节奏；
- [ ] 能独立写一个 Netmiko 脚本完成批量采集；
- [ ] 能用 RESTCONF 读取一次接口信息（拿到 JSON）；
- [ ] 能写一个 Ansible playbook 完成批量下发，并**验证幂等性**；
- [ ] 能说出自动化的三个落地陷阱及规避方法。

---

### 16_7 进阶延伸
1. **SD-WAN**：以应用质量为判据动态选路，集中策略下发，是广域网的当前主流演进方向（对应 300-415 ENSDWI）；
2. **SD-Access**：基于 VXLAN 的自动化园区网，控制平面与数据平面分离（LISP + VXLAN + TrustSec）；
3. **模型驱动遥测（MDT）**：gRPC/gNMI 订阅式采集，把"分钟级轮询"变成"秒级推送"；
4. **网络即代码（CI/CD）**：Git 管理配置 → 变更评审（MR）→ 自动检查（lint + 断言）→ 灰度发布 → 自动回滚；
5. **把排错变成断言**：用 Ansible 采集 `show ip route`、`show standby brief`、`show ip ospf neighbor`，断言"必须存在某条路由""每个 VLAN 有且仅有一台 Active"，**让故障在变更当天就被发现，而不是半年后**。

---

## 板块17 · 命令速查与附录
> 一句话定位：**把前 16 个板块压缩成一张可检索的清单。** 考试前夜、排错现场、变更窗口，翻开这一页就够了。

---

### 17_1 IOS 导航与编辑快捷键
| 功能 | 命令 / 按键 |
| --- | --- |
| 进入特权模式 | `enable`（`en`） |
| 进入全局配置 | `configure terminal`（`conf t`） |
| 返回上一层 | `exit` |
| 直接回特权 | `end` / `Ctrl+Z` |
| 撤销命令 | 原命令前加 `no`（如 `no shutdown`） |
| 接口恢复出厂 | `default interface gi0/0` |
| 命令帮助 | `?`、`命令?`、`s?` |
| 自动补全 | `Tab` |
| 历史命令 | `↑`/`↓`、`show history` |
| 调大历史缓存 | `terminal history size 50` |
| 管道过滤 | ` |

#### 17_1.1 模式提示词速记
```latex
Router>                  用户模式      只能看少量状态
Router#                  特权模式      全部查看权 + 配置入口
Router(config)#          全局配置      影响整机
Router(config-if)#       接口配置      IP、no shutdown
Router(config-subif)#    子接口        dot1q 封装
Router(config-line)#     线路配置      console / vty / aux
Router(config-router)#   路由进程      OSPF / EIGRP / RIP
Router(vlan)#            VLAN 数据库   老平台建 VLAN
```

---

### 17_2 设备初始化与远程管理
```latex
! 基础身份
hostname R1
no ip domain-lookup                 ←防手抖触发 DNS 解析
banner motd #未授权禁止访问#

! 密码与账号
enable secret Str0ngEn@ble
service password-encryption
username admin secret Str0ngP@ss

! 接口
interface gi0/0
 description ## To-Core ##
 ip address 192.168.1.1 255.255.255.0
 no shutdown
 speed 100
 duplex full

! Telnet（不推荐，仅实验）
line vty 0
 password jaking
 login
 transport input telnet

! SSH（生产）
hostname R1
ip domain-name example.com
username admin secret StrOngP@ss
crypto key generate rsa modulus 2048
ip ssh version 2
line vty 0 4
 transport input ssh
 login local
 exec-timeout 10 0
 access-class 10
access-list 10 permit 192.168.10.0 0.0.0.255

! 串口（DCE 端）
interface s2/0
 clock rate 64000
 bandwidth 64
 encapsulation ppp
 ppp authentication chap
 no shutdown

! 保存与清理
copy running-config startup-config     （wr / write memory）
erase startup-config
delete vlan.dat                        （交换机清 VLAN 库）
reload
```

**验证**：`show ip ssh`、`show ssh`、`show line vty 0 4`、`show version`、`show ip interface brief`

---

### 17_3 二层交换
```latex
! VLAN
vlan 10
 name Tech
interface gi0/2
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast

! 批量端口
interface range gi0/3-8
 switchport mode access
 switchport access vlan 20
 switchport host              ←access + portfast + nonegotiate 模板

! Trunk（2960 无需指定封装；3560 及以上需先封装）
interface gi0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,99
 switchport trunk allowed vlan add 30
 switchport trunk allowed vlan remove 2-9

! VTP
vtp domain HQ
vtp password VtpP@ss
vtp mode server | client | transparent
vtp version 2
show vtp status

! STP
spanning-tree mode rapid-pvst
spanning-tree vlan 10 priority 4096
spanning-tree vlan 20 priority 8192
spanning-tree portfast bpduguard default
interface gi0/1
 spanning-tree vlan 8,9,10 port-priority 10
 spanning-tree vlan 2,3,4 cost 30
 spanning-tree bpduguard enable
 spanning-tree guard root

! EtherChannel
interface range gi0/1-2
 switchport mode trunk
 channel-group 1 mode active
interface port-channel 1
 switchport mode trunk
port-channel load-balance src-dst-ip

! MST（多实例生成树）——区域内所有交换机配置必须一致
spanning-tree mode mst
spanning-tree mst configuration
 name REGION-A
 revision 1
 instance 1 vlan 10,20,30
 instance 2 vlan 40,50,60
 exit                                  ←★改完映射表必须 exit 才生效
spanning-tree mst 1 priority 4096
spanning-tree mst 2 priority 8192

! 二层安全
interface gi0/5
 switchport port-security
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation restrict
ip dhcp snooping
ip dhcp snooping vlan 10
interface gi0/24
 ip dhcp snooping trust
ip arp inspection vlan 10
interface gi0/5
 ip verify source port-security
```

**验证**：

```latex
show vlan brief
show interfaces trunk
show interfaces gi0/1 switchport
show mac address-table
show spanning-tree vlan 10
show spanning-tree summary
show spanning-tree mst configuration            ←区域名/修订号/VLAN 映射
show spanning-tree mst configuration digest     ←★全网 digest 必须一致
show spanning-tree mst 1                        ←实例 1 的根桥与端口角色
show etherchannel summary
show port-security interface gi0/5
show ip dhcp snooping binding
show vtp status
```

---

### 17_4 三层路由
```latex
! 静态路由
ip route 192.168.2.0 255.255.255.0 192.168.3.2
ip route 0.0.0.0 0.0.0.0 200.1.1.2                  ←默认路由
ip route 192.168.2.0 255.255.255.0 192.168.3.2 130  ←浮动静态（AD=130 做备份）
ip route 192.168.0.0 255.255.0.0 null0 110          ←黑洞防环
ipv6 route 2001:db8:2::/64 2001:db8:1::2
ipv6 route ::/0 2001:db8:1::2

! 三层交换 / 单臂路由
ip routing                                          ←★三层交换机必开
interface vlan 10
 ip address 192.168.10.1 255.255.255.0
 no shutdown

interface fa0/0
 no shutdown
interface fa0/0.1
 encapsulation dot1q 2
 ip address 192.168.1.1 255.255.255.0

! OSPF
router ospf 1
 router-id 1.1.1.1
 network 192.168.1.0 0.0.0.255 area 0
 passive-interface gi0/1
 default-information originate
 auto-cost reference-bandwidth 100000
interface gi0/0
 ip ospf 1 area 0                                   ←接口级启用（推荐）
 ip ospf cost 30
 ip ospf hello-interval 1
 ip ospf dead-interval 4
 ip ospf network point-to-point

! OSPFv3
ipv6 unicast-routing
ipv6 router ospf 1
 router-id 1.1.1.1
interface gi0/0
 ipv6 ospf 1 area 0
```

**验证**：`show ip route`、`show ip route {目标IP}`、`show ip ospf neighbor`、`show ip ospf interface`、`show ip ospf database`、`show ip protocols`、`show ipv6 route`、`show ipv6 ospf neighbor`

#### 17_4.1 管理距离速查
```latex
0   直连        1   静态        5   EIGRP 汇总    20  eBGP
90  EIGRP内部   100 IGRP        110 OSPF          115 IS-IS
120 RIP         140 EGP         160 ODR           170 外部EIGRP
200 iBGP        255 不可信（不进表）
```

#### 17_4.2 路由表标记
```latex
C 直连   S 静态   O OSPF区域内   O IA 区域间
O E1/E2 外部   D EIGRP   R RIP   B BGP   i IS-IS
```

---

### 17_5 NAT 与网关冗余
```latex
! NAT / NAPT
interface fa0/0
 ip nat inside
interface s2/0
 ip nat outside
access-list 1 permit 192.168.1.0 0.0.0.255
ip nat pool jaking 200.1.1.3 200.1.1.3 netmask 255.255.255.0
ip nat inside source list 1 pool jaking overload
! 或复用出接口
ip nat inside source list 1 interface s2/0 overload
! 静态发布服务器
ip nat inside source static tcp 192.168.1.10 80 200.1.1.10 80
! NAT 豁免（VPN 流量，deny 必须在 permit 之前）
access-list 101 deny   ip 192.168.1.0 0.0.0.255 10.0.0.0 0.0.255.255
access-list 101 permit ip 192.168.1.0 0.0.0.255 any

! HSRP
interface gi0/0
 standby version 2
 standby 150 ip 136.147.107.100
 standby 150 priority 110
 standby 150 preempt
 standby 150 timers msec 200 msec 600
 standby 150 authentication md5 key-string HsrpK3y
 standby 150 track Serial0/0/0 30

! VRRP / GLBP
vrrp 10 ip 192.168.1.1
vrrp 10 priority 110
vrrp 10 track 1 decrement 30

glbp 10 ip 192.168.1.1
glbp 10 priority 110
glbp 10 preempt
glbp 10 load-balancing round-robin
```

**验证**：`show ip nat translations`、`show ip nat statistics`、`show standby brief`、`show standby`、`show vrrp brief`、`show glbp brief`

---

### 17_6 安全与 VPN
```latex
! 标准 ACL
access-list 10 permit 192.168.10.0 0.0.0.255
line vty 0 4
 access-class 10 in

! 扩展 ACL
access-list 101 permit tcp 192.168.1.0 0.0.0.255 any eq 80
access-list 101 permit tcp 192.168.1.0 0.0.0.255 any eq 443
access-list 101 deny ip any any log
interface gi0/0
 ip access-group 101 in

! 命名 ACL（推荐）
ip access-list extended WEB-ONLY
 permit tcp 192.168.1.0 0.0.0.255 host 200.1.2.2 eq 80
 deny ip any any log

! 时间型 ACL
time-range WORKTIME
 periodic weekdays 09:00 to 18:00

! IPsec
crypto isakmp policy 10
 encryption aes 256
 hash sha256
 authentication pre-share
 group 14
crypto isakmp key VpnK3y address 200.1.1.2
crypto ipsec transform-set TS esp-aes 256 esp-sha256-hmac
 mode tunnel
access-list 100 permit ip 192.168.1.0 0.0.0.255 10.0.0.0 0.0.255.255
crypto map CMAP 10 ipsec-isakmp
 set peer 200.1.1.2
 set transform-set TS
 match address 100
interface gi0/0
 crypto map CMAP
```

**验证**：`show access-lists`（看计数）、`show ip interface gi0/0`、`show crypto isakmp sa`（QM_IDLE）、`show crypto ipsec sa`（看加解密计数）、`show time-range`

---

### 17_7 服务与运维
```latex
! DHCP
ip dhcp excluded-address 192.168.1.1 192.168.1.10
ip dhcp pool VLAN10
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.1
 dns-server 114.114.114.114 8.8.8.8
 domain-name example.com
 lease 0 8 0
interface vlan 10
 ip helper-address 192.168.100.10        ←DHCP 中继

! NTP
ntp server 192.168.100.1 prefer
ntp source Loopback0
clock timezone CST 8
ntp authenticate
ntp authentication-key 1 md5 NtpK3y
ntp trusted-key 1

! Syslog
logging host 192.168.100.20
logging source-interface Loopback0
logging trap informational
service timestamps log datetime msec localtime show-timezone
logging buffered 16384 informational
logging console warnings
logging synchronous
archive
 log config
  logging enable
  notify syslog

! SNMP
snmp-server community PublicRO RO 10
snmp-server location 机房A-机柜3
snmp-server contact netops@example.com
snmp-server group MONITOR v3 priv
snmp-server user monuser MONITOR v3 auth sha AuthP@ss priv aes 128 PrivP@ss
snmp-server host 192.168.100.30 version 3 priv monuser

! NetFlow
interface gi0/0
 ip flow ingress
ip flow-export destination 192.168.100.40 9996
ip flow-export version 9
ip flow-export source Loopback0

! IP SLA
ip sla 1
 icmp-echo 8.8.8.8 source-interface gi0/0
 frequency 5
ip sla schedule 1 life forever start-time now
track 1 ip sla 1 reachability
ip route 0.0.0.0 0.0.0.0 200.1.1.2 track 1

! QoS
class-map match-all VOICE
 match dscp ef
policy-map WAN-QOS
 class VOICE
  priority 512
 class class-default
  fair-queue
interface gi0/0
 service-policy output WAN-QOS

! SPAN 端口镜像（排错完记得关掉）
monitor session 1 source interface gi0/1 both     ←both / rx / tx
monitor session 1 destination interface gi0/24    ←目的口停止正常转发
! RSPAN：两端建 VLAN 900 并 remote-span，源端 destination remote vlan 900，
!        目的端 source remote vlan 900
no monitor session 1                              ←★用完必关，否则推高 CPU

! 备份与升级
copy running-config tftp:
archive
 path tftp://192.168.100.50/$h-$t
 write-memory
boot system flash:c2900-universalk9-mz.SPA.155-3.M4a.bin
```

**验证**：`show ip dhcp binding`、`show ip dhcp pool`、`show ip interface vlan 10`（Helper address）、`show ntp associations`、`show clock detail`、`show logging`、`show ip cache flow`、`show ip sla statistics`、`show track`、`show policy-map interface`、`show monitor session 1`、`show version`（当前镜像）、`show archive`

---

### 17_8 IPv6
```latex
ipv6 unicast-routing                          ←★等价于 ip routing
interface vlan 20
 ipv6 address 2001:db8:0:20::1/64
 ipv6 address fe80::1 link-local
 ipv6 nd other-config-flag                    ←DHCPv6 无状态（只给 DNS）
 ipv6 nd managed-config-flag                  ←DHCPv6 有状态
 ipv6 dhcp relay destination 2001:db8:0:10::100
 no ipv6 nd ra suppress                       ←★允许发 RA，SLAAC 前提

ipv6 dhcp pool VLAN20
 address prefix 2001:db8:0:20::/64
 dns-server 2001:db8:0:10::53
 domain-name example.com
interface vlan 20
 ipv6 dhcp server VLAN20
```

**验证**：`show ipv6 interface brief`、`show ipv6 interface vlan 20`、`show ipv6 neighbors`（取代 ARP 表）、`show ipv6 route`、`show ipv6 dhcp binding`

**缩写规则**：前导零省略；连续全零段用 `::`（**全地址只能出现一次**）。  
**地址类型前缀**：GUA `2000::/3`、ULA `FC00::/7`、LLA `FE80::/10`、组播 `FF00::/8`。

---

### 17_9 无线速查
```latex
CAPWAP 控制通道   UDP 5246（DTLS 加密）
CAPWAP 数据通道   UDP 5247（可选 DTLS）
WLC 发现顺序      本地广播 → DHCP Option 43 → DNS CISCO-CAPWAP-CONTROLLER → 静态
AP 八步状态机     启动 → 发现 → DTLS → Join → 下载镜像 → 下载配置 → RUN → Reset
2.4G 非重叠信道   1 / 6 / 11
Wi-Fi 代际        n=Wi-Fi4 / ac=Wi-Fi5 / ax=Wi-Fi6(6E)
安全演进          WEP(禁用) → WPA2-PSK → WPA2-Enterprise(802.1X) → WPA3
排错第一检查项    AP 拿到 IP 了吗？（DHCP 与 VLAN）
```

---

### 17_10 报错与现象对照表（速查）
| 现象 / 报错 | 含义 | 处置 |
| --- | --- | --- |
| `administratively down` | 接口被 shutdown | `no shutdown` |
| 串口 `up / down` | DCE 无时钟或封装不一致 | `show controllers` → `clock rate`；统一 encapsulation |
| `%CDP-4-NATIVE_VLAN_MISMATCH` | 两端 native VLAN 不一致 | 统一 `switchport trunk native vlan` |
| `Translating "xxx"...domain server` | 把命令当主机名做 DNS 解析 | `no ip domain-lookup` |
| `%PPP-4-AUTHFAIL` | CHAP/PAP 认证失败 | 查 hostname / username / 密码（**大小写敏感**） |
| `% Command rejected`（trunk 封装） | 3560 上先敲了 mode trunk | 先 `switchport trunk encapsulation dot1q` |
| `Configuring IP routing on a LAN subinterface is only allowed if...` | 子接口未配 dot1q | 先 `encapsulation dot1q {vlan}` |
| ping 首包超时 | ARP 解析 | 再 ping 一次，0 丢包即正常 |
| `show ip nat translations` 空 | 无流量触发 | 先 ping；看 `show ip nat statistics` 的 hits |
| ACL 应用后全断 | 末尾隐含 `deny ip any any` | 先 `permit ip any any` 兜底，观察后收紧 |
| 双 Active（HSRP） | 认证串不一致 | 统一 `standby authentication` |
| AP 不上线 | 未拿到 IP | 查接入端口 VLAN 与 DHCP |
| 小网页能开、大文件必断 | MTU/MSS 不匹配 | `ip tcp adjust-mss 1452` |
| IPsec QM_IDLE 但业务不通 | 未做 NAT 豁免 | NAT ACL 中 `deny` VPN 流量（放最前） |
| `insane / invalid`（NTP） | 时钟源不可信 | 检查层级差或时间跳跃 |
| 全网 VLAN 消失 | VTP 修订号覆盖 | 拔线隔离 → 重建 VLAN → 上架前清 vlan.dat |

---

### 17_11 地址规划模板（可复制）
```latex
【站点名称】____
【公网地址】____（掩码 ____，网关 ____）
【内网网段规划】
  | VLAN | 名称     | 网段              | 网关            | 用途   | 预计主机数 |
  | 10   | Tech     | 192.168.10.0/24  | 192.168.10.1   | 技术部 | 60 |
  | 20   | Sales    | 192.168.20.0/24  | 192.168.20.1   | 销售部 | 50 |
  | 99   | Mgmt     | 192.168.99.0/24  | 192.168.99.1   | 管理   | 30 |
  | 100  | AP-Mgmt  | 192.168.100.0/24 | 192.168.100.1  | AP 管理 | 40 |
【互联地址】
  | 链路            | 网段              | 本端 | 对端 |
  | R1—R2 专线      | 192.168.3.0/30   | .1   | .2  |
【IPv6 规划】
  全球前缀：2001:db8:____::/48
  各 VLAN 分配 /64：____、____、____
【保留地址】
  网关用 .1，网络设备用 .2–.10，DHCP 池 .11–.254
```

---

### 17_12 线缆速查
| 线缆类型 | 用途 | 要点 |
| --- | --- | --- |
| **Console 线（RJ45-DB9 / USB）** | 带外管理 | 参数：9600 / 8 / 无校验 / 1 停止位 / 无流控 |
| **V.35 串口线（背靠背）** | 实验室广域网 | **DCE 端必须配 clock rate** |
| **直通线** | 不同设备互联（PC—交换机、交换机—路由器） | 两端线序一致 |
| **交叉线** | 同类设备互联（PC—PC、交换机—交换机） | 现代设备支持 Auto-MDIX，多数情况直通也能通 |
| **光纤跳线** | 上联/长距离 | 注意单模/多模匹配、收发方向（单向链路用 UDLD 检测） |
| **堆叠线** | 交换机堆叠 | 专用线缆，注意顺序与冗余环路 |

---
