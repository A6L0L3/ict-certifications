# H3C 认证三级跃迁实战知识库（NE→SE→IE）
> 一句话定位：这是一套**按能力层级组织、可直接粘到设备上落地**的 H3C 技术作战手册。  
它不是命令速查表，而是把"原理 → 选型 → 配置 → 验证 → 排障 → 交付"串成闭环的完整链路。

---

## 一、这套知识库解决什么问题
大多数网络学习资料的问题不是"不全"，而是**三处断裂**：

1. **原理与配置断裂**：背得下 STP 的五种端口状态，却在真机上不知道为什么 GE1/0/2 一直是 DISCARDING。
2. **配置与验证断裂**：命令敲完了，不知道用什么 `display` 证明它真的生效——而这恰恰是 H3CIE 实验考试的核心评分项。
3. **技术与交付断裂**：能配通中小企业网，却写不出一份让客户签字、让评委信服的方案与排错报告。

本知识库按 **H3CNE（工程师级）→ H3CSE（高级工程师级）→ H3CIE（技术专家级）** 的三级能力模型组织，每一章都同时回答三个问题：

| 问题 | NE 的答案 | SE 的答案 | IE 的答案 |
| --- | --- | --- | --- |
| 是什么 | 功能如何实现 | 什么时候该用失效边界在哪 | 对业务的影响面与替代方案 |
| 怎么配 | 照着敲能通 | 能按场景裁剪 | 能在约束条件下做取舍 |
| 怎么证 | 会一条 display | 会一组交叉验证 | 会形成证据链并写进报告 |

---

## 二、板块清单与能力映射
| 板块 | 标题 | 主题 | NE | SE | IE |
| --- | --- | --- | --- | --- | --- |
| 板块0 | 认证全景与学习路径建议 | 认证金字塔、考试科目、三阶段路线、实验环境、笔记方法 | ★★ | ★★ | ★★ |
| 板块1 | Comware系统基础与设备命令行 | 视图层级、配置管理、文件系统、固件升级、密码恢复 | ★★ | ★★ | ★★ |
| 板块2 | 设备登录与远程管理 | Console / Telnet / SSH / Web、用户角色、VTY 参数、登录排障 | ★★ | ★★ | ★★ |
| 板块3 | 以太网交换与端口管理 | 转发原理、端口参数、批量管理、状态查看、DOWN 排查 | ★★ | ★★ | ★★ |
| 板块4 | VLAN与三层互通 | VLAN / Access / Trunk / Hybrid / Vlan-interface / Super VLAN / QinQ | ★★ | ★★ | ★★ |
| 板块5 | 生成树与环路防护 | STP / RSTP / MSTP、保护机制、环路检测、环路定位 | ★★ | ★★ | ★★ |
| 板块6 | 链路聚合与IRF堆叠高可用 | 链路聚合、IRF2、MAD、M-LAG/DRNI、VRRP、BFD/NQA | ★ | ★★ | ★★ |
| 板块7 | IP路由基础与OSPF-ISIS-BGP | 静态路由、RIP、OSPF、IS-IS、BGP、路由策略、IPv6/SRv6 | ★★ | ★★ | ★★ |
| 板块8 | DHCP组播QoS与二层防护 | DHCP 与 Snooping、IGMP/PIM、QoS/MQC、IP Source Guard | ★★ | ★★ | ★★ |
| 板块9 | 广域网ACL-NAT与VPN | PPP/PPPoE、ACL、NAT、GRE/IPSec/L2TP、MPLS VPN、VXLAN/EVPN | ★★ | ★★ | ★★ |
| 板块10 | 等保2.0合规安全加固 | 密码策略、三权分立、SSH、ACL、SNMPv3、审计、自检清单 | ★★ | ★★ | ★★ |
| 板块11 | SecPath防火墙安全域与策略 | 安全域、策略、NAT、远程管理、RBM 双机热备、排障实录 | ★ | ★★ | ★★ |
| 板块12 | WLAN无线与网络准入控制 | AC+Fit AP、无线安全、802.1X/MAC/Portal、射频优化 | ★ | ★★ | ★★ |
| 板块13 | 网络运维管理与设备生命周期 | 过保查询、固件升级、NTP、LLDP、镜像、Telemetry、批量运维 | ★★ | ★★ | ★★ |
| 板块14 | 故障排查方法论与排错实验 | 排障模型、诊断工具、场景库、排错报告模板、实验训练法 | ★★ | ★★ | ★★ |
| 板块15 | 综合实战与项目交付 | 中小企业网、双核心园区网、割接实施、面试汇报、交付文档 | ★★ | ★★ | ★★ |

---

## 三、推荐阅读顺序
### 阶段一：零基础 → H3CNE-RS+（约 8 周）
```plain
板块0 → 板块1 → 板块2 → 板块3 → 板块4 → 板块7(7_1~7_3) → 板块9(9_2~9_3)
     → 板块8(8_1) → 板块15(15_1)
```

原则：**先保证"能配通"，再回头补安全与运维**。

### 阶段二：H3CNE → H3CSE-RS+（约 4~6 个月）
```plain
交换线（GB0-372）：板块5 → 板块6 → 板块8(8_3~8_5) → 板块10 → 板块12 → 板块13
路由线（GB0-382）：板块7(7_4~7_7)
广域优化线（GB0-392）：板块9(9_4~9_5)
```

两条主线**建议串行**：交换与路由的思维方式不同，并行容易互相干扰。先"交换"后"路由"，最后补"广域与安全优化"。

### 阶段三：H3CSE → H3CIE-RS+（约 6~12 个月）
```plain
主线：板块14（方法论 + 报告模板）→ 板块15（15_2、15_3、15_5）
训练：每周 3~4 小时实验，按板块 14 的四阶段训练法推进
```

---

## 四、使用约定
1. **命令版本**：默认基于 Comware V7。V5 设备（S3600/S5500 老版本、SecPath F1000-S 的 Version 5.20 等）的差异统一用「V5 差异」「V5 写法」标注。
2. **配置可粘贴**：代码块中的命令可直接粘贴到设备；涉及密码、IP、端口编号、VLAN ID 的部分按实际环境替换。
3. **验证命令不要跳过**：每个配置章节后都有对应的 `display` 验证项。H3CIE 实验考试的评分重点就是"验证习惯"。
4. **图片呈现**：统一采用 ASCII 拓扑图放在代码块中，确保在任何 Markdown 环境（Git 仓库）中都能正常加载，不依赖外链图片。
5. **实验环境**：推荐 HCL（H3C Cloud Lab）+ 真机组合。IRF、BFD MAD、光模块诊断等特性建议用真机验证。
6. **笔记方式**：每个板块末尾都提供「实验笔记模板 + 验收清单」，建议用"现象 → 假设 → 验证 → 结论"四段式记录，具体方法见板块0 的 0_7。

---

## 五、适配的考试科目
| 认证 | 科目代码 | 主要覆盖板块 |
| --- | --- | --- |
| H3CNE-RS+ | GB0-192 | 板块1~5、7（基础）、8（基础）、9（基础） |
| H3CSE-RS-SW | GB0-372 | 板块4、5、6、8（组播/QoS）、10、12（准入）、13 |
| H3CSE-RS-RT | GB0-382 | 板块7 全篇 |
| H3CSE-RS-NSO | GB0-392 | 板块9 全篇、板块8（QoS） |
| H3CSE-RS-IPv6 | GB0-330 | 板块7 的 7_8 |
| H3CSE-Security | GB0-530 / GB0-551 | 板块11、板块10 |
| H3CSE-WLAN | GB0-343 | 板块12 |
| H3CIE-RS+ | GB0-802 / HL0-202 / HI0-103 | 板块14、15 为主，全库为知识底座 |
| H3CIE-Security | GB0-560 / HL0-500 / HI0-500 | 板块11、10、9 |
| H3CIE-WLAN | GB0-353 / HL0-123 / HI0-202 | 板块12、3、4 |

---

## 六、免责与维护说明
+ 考试代码、费用有效期、改版通知以新华三官方最新公告为准（官网技术认证板块与「新华三技术认证」公众号）。本知识库中的考试信息整理自官方公开资料，**报考前务必复核**。考试政策在不同时期会有调整，请以当前官方口径为准。
+ 设备命令以对应型号的配置指导与命令手册为准，不同软件版本存在命令差异。
+ 生产环境变更前请务必备份配置、评估影响范围并准备回退方案（见板块15 的 15_4）。

# 板块0 · 认证全景与学习路径建议
> 本板块解决四个问题：H3C 认证到底是什么结构、从零基础到专家该按什么顺序走、实验环境怎么搭、笔记怎么记才不白记。  
后面所有板块都按「板块 N_M」二级编号组织，命令均可在 HCL 或真机（Comware V7）上落地。

---

## 0_1 认证金字塔：三级能力模型与定位
新华三技术认证体系覆盖路由交换、新网络（SDN）、无线、云计算、安全、服务器、存储、操作系统、工业互联网等九大技术领域，每个领域内按三个等级递进：

| 等级 | 名称 | 英文全称 | 能力定位 | 典型岗位 |
| --- | --- | --- | --- | --- |
| 工程师级 | H3CNE | H3C Certified Network Engineer | 中小网络规划、配置、维护；会敲命令、会搭拓扑 | 运维工程师、驻场工程师、售后初级 |
| 高级工程师级 | H3CSE | H3C Certified Senior Engineer | 大中型网络设计与复杂部署；会选型、会优化、会排障 | 系统集成工程师、项目实施工程师、原厂售后 |
| 技术专家级 | H3CIE | H3C Certified Internetwork Expert | 大型网络规划设计与疑难问题解决；会做决策、会讲方案 | 架构师、技术负责人、高级顾问 |

### 能力跃迁的本质：三个转变
1. **NE：功能实现** —— 知道 `vlan 100`、`port access vlan 100`、`ip route-static` 能把网络调通。
2. **SE：方案选型** —— 知道什么时候用 MSTP+VRRP，什么时候用 IRF，什么时候上 M-LAG/DRNI，以及各自的**失效边界**。
3. **IE：规划与排障闭环** —— 能在限定时间内从一个"被注入故障"的网络中定位并修复问题，写出规范的排错报告；能在面试里把设计理由讲清楚。

### 📌 案例手记：同一张拓扑，三种答案
某园区网新建项目，核心层两台 S5560，接入层 8 台 S5130，要求"核心冗余、链路不浪费"。

+ **NE 的做法**：两台核心各配网关地址，接入交换机双上行但被 STP 阻塞一半链路，跑通了，但上行带宽只用了一半，主核心挂了要几十秒才切。
+ **SE 的做法**：核心做 IRF 虚拟化成一设备 + 接入双上行链路聚合，既无环路也无阻塞链路，带宽翻倍，主备切换秒级。
+ **IE 的做法**：先问业务——"核心故障允许中断多久？""未来三年是否要上双活数据中心？"若金融客户要求零中断，则 IRF 升级需整机重启不满足，改选 M-LAG；若园区网允许分钟级维护窗口，IRF 更简单、运维成本更低。

**结论**：三级之间的差距从来不是命令量，而是**提问顺序**——NE 问"怎么配"，SE 问"选哪个"，IE 问"为什么要这个、代价是什么"。

---

## 0_2 考试科目与进阶规则全表
### 路由交换方向（RS，最经典的主赛道）
| 层级 | 考试代码 | 课程 / 科目 | 时长 | 题型与通过线 | 参考费用 |
| --- | --- | --- | --- | --- | --- |
| H3CNE-RS+ | GB0-192 | 路由交换技术基础 | 60 分钟 | 50 题，1000 分满分，600 分通过 | 约 ¥1200 |
| H3CSE-RS-SW（必选 1） | GB0-372 | 高级路由交换技术 1（交换方向） | 60 分钟 | 50 题，600 分通过 | 约 ¥1200 |
| H3CSE-RS-RT（必选 2） | GB0-382 | 高级路由交换技术 2（路由方向） | 60 分钟 | 50 题，600 分通过 | 约 ¥1200 |
| 可选三选一 | GB0-392 | 网络安全与优化 | 60 分钟 | 50 题，600 分通过 | 约 ¥1200 |
| 可选三选一 | GB0-330 | H3C IPv6 技术 | 60 分钟 | 50 题，600 分通过 | 约 ¥1200 |
| 可选三选一 | GB0-961 | 构建融合开放的智能管理中心 | 60 分钟 | 50 题，600 分通过 | 约 ¥1200 |
| H3CIE-RS+ 笔试 | GB0-802 | H3C 网络规划与排障 | 90 分钟 | 1000 分满分，800 分通过 | 约 ¥2000 |
| H3CIE-RS+ 实验 | HL0-202 | 实验室考试（真机排障） | 6 小时 | 1000 分满分，800 分通过 | 约 ¥8000 |
| H3CIE-RS+ 面试 | HI0-103 | 技术面试（项目汇报 + 问答） | 30 分钟 | 100 分满分，80 分通过 | 首次免费，补考另行收费 |

> 费用与政策会随官方调整而变化，**报考前请以新华三官方最新公告为准**。

### 关键规则（决定你的报考节奏）
+ **H3CSE-RS+** 需先持有有效的 H3CNE-RS+（或同等级）证书；2 门必选 + 1 门可选，**成绩有效期 12 个月**，一年之内必须三门全过。
+ **H3CIE-RS+** 无需强制进阶（不要求先拿 NE/SE），但首次报考需参加新华三人才研学中心认可的 H3CIE-RS+ 培训；笔试成绩有效期 12 个月，需在此期限内通过实验与面试。
+ **H3CIE 证书有效期 2 年 + 1 年缓冲期**；在缓冲期内通过技术面试可刷新，否则需笔试、实验、面试三科重考。
+ 旧版 H3CNE（GB0-190，对应 Comware V5）与旧版 H3CSE-RS（GB0-370/380/390）已下线，证书下线后有效期不再刷新，设备版本也已切到 Comware V7，**学习以 V7 命令为准**。

### 其他主流方向（按需切入）
| 方向 | 工程师级 | 高级工程师级 | 专家级 |
| --- | --- | --- | --- |
| 安全 Security | H3CNE-Security（GB0-510） | H3CSE-Security（GB0-530 构建安全网络架构 + GB0-551 部署内容安全系统） | H3CIE-Security（GB0-560 笔试 / HL0-500 实验 / HI0-500 面试） |
| 无线 WLAN | （需 H3CNE-RS+） | H3CSE-WLAN（GB0-343） | H3CIE-WLAN（GB0-353 笔试 / HL0-123 实验 / HI0-202 面试） |
| 云计算 Cloud | H3CNE-Cloud（GB0-713） | H3CSE-Cloud（GB0-722） | H3CIE-Cloud（GB0-770 / HL0-700） |
| 新网络 SDN | — | H3CSE-SDN（GB0-452） | H3CIE-SDN（AD-WAN / AD-DC / AD-Campus 等细分） |

**选型建议**：

+ 目标岗位以政企园区网、教育、电力、交通为主 → 走 **RS 主赛道**。
+ 已有网络基础、想提升单价 → **安全方向**政策扶持力度持续加大。
+ 做云平台与数据中心 → 走 **Cloud / SDN**。

---

## 0_3 零基础到 H3CNE-RS+ 的入门路线（约 8 周）
### 阶段一：建立"数据怎么走"的直觉（约 2 周）
1. 用 HCL 搭两台交换机 + 两台 PC 的最小拓扑，抓包看 ARP 请求、ICMP 全过程。
2. 必须自己讲清楚四个问题：
    - 同网段 PC1 怎么找到 PC2？（二层转发 + MAC 表）
    - 跨网段为什么要网关？（三层转发）
    - VLAN 是什么时候被打上去的？（802.1Q 与 PVID）
    - Trunk 与 Access 的差别在哪一跳生效？
3. 推荐教材：《路由交换技术基础》+ H3C 网络学院系列《路由交换技术详解与实践》第 1 卷。

### 阶段二：命令行肌肉记忆（约 2 周，对应板块1~4）
| 时间 | 内容 | 板块 |
| --- | --- | --- |
| Day 1-2 | Comware 视图与帮助体系、配置保存与回滚 | 板块1 |
| Day 3-4 | Console / Telnet / SSH 登录与用户角色 | 板块2 |
| Day 5-7 | 端口管理、批量操作、状态查看与 DOWN 排查 | 板块3 |
| Day 8-10 | VLAN 创建、Access/Trunk/Hybrid、Vlan-interface 三层互通 | 板块4 |
| Day 11-12 | 静态路由、默认路由、单臂路由小综合 | 板块7 |
| Day 13-14 | DHCP、NAT 出口、ACL 基础 | 板块8、9 |

### 阶段三：综合小项目（约 2 周）
按板块15 的"中小企业单核心组网"独立完成：

```plain
VLAN 划分 → 三层互通 → DHCP 下发 → 出口 NAT → 远程管理 SSH → 保存与备份
```

做完后**推倒重做一遍**，要求不看文档 40 分钟内配完。

### 阶段四：冲刺（约 1 周）
刷官方大纲逐条自查，重点补：**STP 端口状态机、802.1Q 帧格式、OSPF 邻居状态机、ACL 通配符掩码计算**。  
GB0-192 是 50 题 600 分，容错率约 40%，但题型含填空，**命令细节必须准**。

---

## 0_4 H3CNE → H3CSE-RS+ 进阶顺序
GB0-372（交换）与 GB0-382（路由）**建议串行学习**，不要并行——两者思维方式不同。

### 第一步 GB0-372：把园区网做"快"做"稳"
| 大纲模块 | 对应板块 |
| --- | --- |
| 园区网模型与层次化设计 | 板块15 |
| VLAN 技术（802.1Q、端口类型、MVRP、Super VLAN、Isolate-user-VLAN、QinQ） | 板块4 |
| 生成树（STP/RSTP/MSTP、保护机制） | 板块5 |
| 高可靠性（链路聚合、IRF、VRRP、BFD） | 板块6 |
| 组播与 QoS | 板块8 |
| 园区网安全与准入 | 板块10、12 |
| 网络管理与维护 | 板块13 |

### 第二步 GB0-382：把路由做"通"做"优"
| 大纲模块 | 对应板块 |
| --- | --- |
| 路由基础与静态路由 | 板块7（7_1、7_2） |
| OSPF 原理与多区域、特殊区域 | 板块7（7_4） |
| IS-IS 原理与配置 | 板块7（7_5） |
| BGP 原理、属性与选路 | 板块7（7_6） |
| 路由策略与引入控制 | 板块7（7_7） |
| IPv6 与 SRv6 | 板块7（7_8） |

### 第三步 GB0-392：广域与安全优化
板块9（9_4、9_5）+ 板块8 的 QoS 部分。

> **学习节奏建议**：每周固定 3 个晚上 + 1 个半天实验。每个技术点走"看原理 → 敲配置 → 做验证 → 故意改坏再修"四步，第三遍才算学会。

---

## 0_5 H3CSE → H3CIE-RS+ 冲刺路线
IE 阶段的核心不是"多学新技术"，而是**把已有知识组织成可输出的决策链**。

```plain
第一阶段（1~2 个月）：方法论重建
  板块14（14_1 三种模型、14_2 诊断工具箱、14_3 分层手册）

第二阶段（2~4 个月）：场景化训练
  板块14（14_4 场景库）逐个复现，每个场景限时 30 分钟

第三阶段（2~3 个月）：全真模拟
  板块15（15_2 双核心园区网）限时搭建 + 注入故障 + 自我修复

第四阶段（1~2 个月）：输出训练
  板块15（15_5 面试汇报）+ 排错报告写作，每次实验后必写报告
```

**训练纪律**：每周 3~4 小时实验，按板块14 的四阶段训练法推进，**单点修改、逐项验证**。

---

## 0_6 实验环境搭建：HCL + 真机组合
### HCL（H3C Cloud Lab）能做什么
| 特性 | HCL 支持度 | 说明 |
| --- | --- | --- |
| 二层交换、VLAN、STP | 完全支持 | 日常练习主力 |
| 三层路由、OSPF/BGP | 支持 | 拓扑不宜过大，注意内存占用 |
| 链路聚合 | 支持 | 可做静态与动态 |
| IRF | 部分支持 | 逻辑可配，但物理堆叠行为与真机有差异 |
| BFD MAD、光模块诊断 | 建议真机 | 模拟器无法体现硬件行为 |
| 无线 AC+AP | 有限 | 建议真机或官方镜像 |

### 真机最小配置建议
```plain
核心：S5560 或 S6520 系列 × 2（做 IRF / VRRP / M-LAG 实验）
接入：S5130 或 S5120 系列 × 2
路由：MSR 系列 × 1（做 PPPoE / NAT / IPSec）
防火墙：SecPath F100 系列 × 1（做安全域 / 策略 / NAT）
无线：AC + WA 系列 AP × 1
```

### HCL 使用避坑清单
1. **先画拓扑再开机**：HCL 设备启动慢，批量启动容易卡死，建议逐台启动。
2. **内存分配**：每台设备按需分配，总内存不要超过物理机的 70%。
3. **保存拓扑快照**：做完一个里程碑就导出一份，避免配置丢失后从头再来。
4. **抓包位置**：HCL 支持链路抓包，验证 ARP / DHCP / OSPF Hello 时比 `display` 更直观。
5. **模拟器与真机的差异**：涉及硬件特性（堆叠口、光模块、风扇电源）的行为，一律以真机为准。

---

## 0_7 笔记沉淀方法：让每次实验都可复用
### 为什么大多数人笔记白记了
常见的三种无效笔记：

| 类型 | 表现 | 问题 |
| --- | --- | --- |
| 抄命令型 | 把配置整段粘进笔记 | 下次遇到同样问题，不知道为什么这么配 |
| 流水账型 | "今天配了 OSPF，邻居起来了" | 没有记录失败过程，失败经验无法复用 |
| 无验证型 | 只记配置不记 display 输出 | 考试和现场都不敢确认是否真的生效 |

### 推荐：四段式实验笔记模板
```plain
## 实验名称：OSPF 多区域 + 路由引入
日期：____   环境：HCL / 真机型号____   版本：Comware ____

### 1. 目标与验收标准（先写，做完对照）
- [ ] 目标：Area 0 与 Area 10 互通，Area 10 配置为 Stub
- [ ] 验收：display ospf peer 状态为 Full；display ip routing-table 有对端网段

### 2. 拓扑（ASCII）
   [R1]----Area 0----[R2]----Area 10(Stub)----[R3]

### 3. 关键配置（只记关键行，不整段抄）
   [R2-ospf-1-area-0.0.0.10] stub

### 4. 现象 → 假设 → 验证 → 结论（核心）
- 现象：R3 学不到外部路由
- 假设：Stub 区域不接收 Type-5 LSA，属预期行为
- 验证：display ospf lsdb 看到只有 Type-1/2/3，无 Type-5
- 结论：Stub 区域靠缺省路由访问外部，若需引入外部路由改 NSSA

### 5. 踩坑与边界
- 两端 Stub 配置不一致会导致邻居起不来（区域类型必须一致）
```

### 排障笔记：五段式现场记录法
```plain
1. 现象：谁、什么时候、访问什么、什么方式、报错原文
2. 范围：单台 / 单 VLAN / 单楼 / 全网
3. 证据：每条 display 命令 + 关键输出（截图或文本）
4. 动作：改了什么、改之前的状态、改之后的状态
5. 结论：根因 + 验证方式 + 后续防范措施
```

> **纪律**：现场排障**一次只改一个变量**。一次改一堆配置，即使通了也不知道是哪个生效的，写报告时无法自圆其说。

---

## 0_8 常见误区与避坑清单
| 误区 | 后果 | 正确做法 |
| --- | --- | --- |
| 只看视频不动手 | 眼睛会了手不会 | 每个知识点至少敲三遍 |
| 背命令不理解原理 | 换个拓扑就懵 | 每个协议先问"它解决什么问题" |
| 配置完不验证 | 考试丢分、现场翻车 | 每个配置章节后必跑 display 验证清单 |
| 把 V5 命令用到 V7 | Unrecognized command | 上机先 `display version` |
| 生产环境直接改 | 业务中断无法回退 | 先备份配置、评估影响、准备回退方案 |
| 学完就扔不复习 | 三个月后归零 | 用四段式笔记，每月回顾一次场景库 |
| 只学不写 | 面试讲不出来 | 每个项目写一份方案说明，练"讲清楚"的能力 |

---

## 0_9 本板块验收清单
| 验收项 | 命令 / 方法 | 达标标准 |
| --- | --- | --- |
| 明确自己的目标等级与科目 | 对照 0_2 表格 | 能说出自己下一个要考的代码与有效期规则 |
| 实验环境可用 | 启动 HCL 或登录真机 | 能 `display version` 看到 Comware 版本号 |
| 掌握笔记方法 | 用 0_7 模板写一份笔记 | 笔记含"现象→假设→验证→结论"四段 |
| 理解三级能力差异 | 复述 0_1 的三个转变 | 能举例说明 NE/SE/IE 的不同处理方式 |

### 起步动作（今天就能做）
```bash
# 1. 打开 HCL 或登录一台设备，确认版本
<H3C> display version

# 2. 建一个知识库目录，按板块编号建文件夹
mkdir -p H3C-Lab/{00,01,02,03,04,05,06,07,08,09,10,11,12,13,14,15}

# 3. 用 0_7 的模板写第一份实验笔记：
#    主题 = "两台交换机 + 两台 PC 的二层转发全过程"
```

# 板块1 · Comware 系统基础、设备命令行与生命周期管理
> 本板块是所有后续配置的"地基"：视图层级、配置文件的保存与回滚、文件系统与固件升级、密码丢失后的恢复。  
学完标准：**拿到一台陌生设备，5 分钟内完成"识别版本 → 看清现状 → 备份配置 → 可安全修改"的标准动作。**

---

## 1_1 Comware 版本识别：V5 与 V7 的差异清单
H3C 设备从 Comware V5 演进到 V7，命令体系发生了结构性变化。考试与实战均以 V7 为准，但现网仍有大量 V5 设备（如 S3600/S5500 老版本、SecPath F1000-S 的 Version 5.20）。

### 第一步：上机先看版本
```plain
<H3C> display version
```

重点关注三行：

+ **Comware Software, Version**：V5 还是 V7，决定后面所有命令写法。
+ **H3C S5560-30C-EI**：设备型号，决定支持哪些特性。
+ **Uptime**：运行时长，判断设备是否近期重启过（排障第一线索）。

### 新旧命令对照（高频）
| 功能 | Comware V5（旧） | Comware V7（新，考试标准） |
| --- | --- | --- |
| 创建本地用户 | `local-user admin` | `local-user admin class manage` |
| 用户级别 | `authorization-attribute level 3` | `authorization-attribute user-role network-admin`（或 level-15） |
| 进入 VTY 线路 | `user-interface vty 0 4` | `user-interface vty 0 63`（数量扩展） |
| 端口加入 VLAN（Access） | `port access vlan 10` | `port access vlan 10`（同） |
| 端口默认 VLAN | `port access vlan 10` | `port default vlan 10`（V7 新增，等价写法） |
| Trunk 允许 VLAN | `port trunk permit vlan 10 20` | `port trunk permit vlan 10 20`（同） |
| 查看端口简要信息 | `display brief interface` | `display interface brief` |
| 关闭信息中心 | `undo info-center enable` | `undo info-center enable`（同） |

### V7 的三类用户角色
+ **network-admin**：管理员，等价 level-15，可执行所有配置。
+ **network-operator**：操作员，只读，能看不能改。
+ **level-0 ~ level-15**：传统级别，兼容旧体系。

等保场景推荐用 `user-role` 而非 `level`，见板块10。

### 📌 案例手记：一次割接前的"Unrecognized command"
某次接入层割接，工程师提前在家用 HCL（V7）写好 40 行配置脚本，现场粘到一台 S5500 上，第一行就报 `Unrecognized command`。

排查：`display version` 一看，Comware V5.20。脚本里的 `local-user admin class manage` 在 V5 上不存在，`user-interface vty 0 63` 也不支持。

代价：现场临时改写脚本，割接窗口从 1 小时拖到 3 小时。

**教训**：任何脚本落地前，先跑 `display version`。**版本号是配置的第一前提**。

---

## 1_2 视图层级与命令行帮助体系
### 视图结构
Comware 采用分层视图结构，提示符直接反映当前所处层级：

| 提示符 | 视图 | 进入方式 | 能干什么 |
| --- | --- | --- | --- |
| `` | 用户视图 | 登录即进入 | 查看、ping、tracert、save、reboot、debugging |
| `[H3C]` | 系统视图 | `system-view`（缩写 `sys`） | 全局配置 |
| `[H3C-GigabitEthernet1/0/1]` | 接口视图 | `interface gigabitethernet 1/0/1` | 端口参数 |
| `[H3C-vlan100]` | VLAN 视图 | `vlan 100` | VLAN 内加端口、开隔离 |
| `[H3C-Vlan-interface100]` | VLAN 接口视图 | `interface vlan-interface 100` | 三层接口 IP |
| `[H3C-irf-port1/2]` | IRF 端口视图 | `irf-port 1/2` | 堆叠绑定 |
| `[H3C-luser-manage-admin]` | 本地用户视图 | `local-user admin class manage` | 用户属性 |

导航命令：`quit` 退一级、`return`（或 Ctrl+Z）直接回用户视图。

### 帮助体系（考试高频）
```plain
[H3C] ?                                          # 列出当前视图所有命令
[H3C] dis?                                       # 列出以 dis 开头的命令
[H3C] display ver?                               # 补全并提示参数
[H3C] display ver<Tab>                           # Tab 键自动补全
[H3C-GigabitEthernet1/0/1] display this          # 查看当前视图下的生效配置（最常用）
[H3C] display current-configuration | include vlan   # 管道过滤
[H3C] display current-configuration | begin user-interface   # 从匹配行开始显示
[H3C] display current-configuration | exclude undo           # 排除匹配行
```

管道过滤符 `| include` / `| exclude` / `| begin` 是 **H3CIE 实验提速的关键**——6 小时考试里，靠 `include` 定位配置比翻页快一个数量级。

### 命令简写规则
Comware 支持唯一性前缀简写：

```plain
dis int br   =   display interface brief
int g1/0/1   =   interface gigabitethernet 1/0/1
```

但**考试与文档中写全名更稳妥**，排障时容易被简写歧义坑到。

---

## 1_3 设备基本信息查看与命名
```plain
<H3C> system-view
[H3C] sysname Core-SW-01                    # 命名，等保要求设备可唯一识别
[Core-SW-01] display device                 # 查看板卡 / 子卡 / 序列号 / 状态
[Core-SW-01] display device manuinfo        # 查看出厂日期与序列号（过保查询用）
[Core-SW-01] display version
[Core-SW-01] display interface brief        # 端口总览，开局第一步
[Core-SW-01] display vlan                   # VLAN 总览（V5 写法为 display vlan all）
[Core-SW-01] display ip interface brief     # 三层接口与 IP
[Core-SW-01] display mac-address            # MAC 地址表
[Core-SW-01] display arp                    # ARP 表
[Core-SW-01] display logbuffer              # 日志缓冲区（掉电、端口抖动全在这）
[Core-SW-01] display environment            # 温度 / 风扇 / 电源（机房巡检必看）
[Core-SW-01] display power                  # 电源模块状态
[Core-SW-01] display fan                    # 风扇状态
```

**序列号与过保查询**：`display device manuinfo`（部分型号为 `display device manuinfo slot 1`）可拿到设备序列号与生产日期，再到官方服务网站查询维保与过保状态。做扩容、续保、故障换件时第一步就是这个。

### 开局检查清单（建议固化为习惯）
```plain
1. display version            —— 版本、型号、Uptime
2. display device manuinfo    —— 序列号、生产日期（记录进台账）
3. display interface brief    —— 端口总览，哪些 UP / DOWN / ADM
4. display vlan               —— 现有 VLAN 规划
5. display ip interface brief —— 三层接口与 IP
6. display current-configuration —— 现有配置全貌
7. display logbuffer          —— 近期有无异常重启、端口抖动
8. display environment / power / fan —— 硬件健康度
9. save backup.cfg            —— 备份一份原始配置再动手
```

---

## 1_4 配置文件管理：保存、回滚与恢复出厂
Comware 有两个配置：

+ **运行配置**（current-configuration）：内存中的，断电丢失。
+ **保存配置**（saved-configuration）：Flash 中的下次启动文件。

所有"改完没保存，重启后配置丢了"的事故都源于混淆这两者。

### 核心命令
```plain
<H3C> display current-configuration        # 查看运行配置（简写 dis cu）
<H3C> display saved-configuration          # 查看保存配置
<H3C> display startup                      # 查看下次启动用的配置文件
<H3C> save                                 # 交互式保存，需确认 Y
<H3C> save force                           # 强制保存，不提示（批量脚本用）
<H3C> save backup.cfg                      # 另存为其他文件名
<H3C> compare configuration                # 对比运行配置与保存配置的差异（V7 强烈推荐）
<H3C> reset saved-configuration            # 清空保存配置（下次启动为空配，慎用）
<H3C> restore default                      # 恢复出厂默认配置，需重启生效
<H3C> reboot                               # 重启
```

### 配置回滚（V7）
```plain
[H3C] archive configuration                # 手动归档当前配置
[H3C] configuration replace file flash:/xxx.cfg   # 用归档文件替换当前配置
```

更实用的做法——**配置回退点**：

```plain
<H3C> save pre-change.cfg                  # 变更前先另存一份
# ... 执行变更 ...
<H3C> configuration replace file flash:/pre-change.cfg   # 出问题一键回退
<H3C> display diff current-configuration flash:/pre-change.cfg  # 看差异
```

### 📌 案例手记：一条 `save` 救回来的两小时
某次接入交换机改 VLAN，工程师改完业务正常，但没 `save`。两天后该交换机因电源故障重启，配置回到旧版本，半个楼层的终端拿不到地址。

现场恢复耗时两小时，而正确做法只需要在改完后多敲一条 `save force`。

**规则固化**：**任何变更完成并验证后，立即 **`save force`**；变更前必须先 **`save`** 一份带日期的备份文件。**

---

## 1_5 文件系统与配置文件导入导出
### 常用文件操作
```plain
<H3C> dir /all                             # 查看 Flash 中所有文件（含回收站）
<H3C> more startup.cfg                     # 查看文本文件内容
<H3C> delete vlan.dat                      # 删除文件（进回收站）
<H3C> delete /unreserved old-version.bin   # 彻底删除，不占回收站空间
<H3C> reset recycle-bin                    # 清空回收站，释放空间
<H3C> mkdir config-backup                  # 创建目录
<H3C> copy startup.cfg backup.cfg          # 复制文件
<H3C> fixdisk flash:                       # 修复文件系统（异常掉电后可能需要）
<H3C> format flash:                        # 格式化（极度危险，慎用）
```

### 配置文件的备份与恢复（FTP / TFTP）
```plain
# 备份配置到 TFTP 服务器
<H3C> tftp 192.168.1.100 put startup.cfg Core-SW-01-20260914.cfg

# 从 TFTP 服务器恢复配置
<H3C> tftp 192.168.1.100 get Core-SW-01-20260914.cfg startup.cfg
<H3C> reboot

# 用 FTP（需用户名密码，适合跨网段）
<H3C> ftp 192.168.1.100
[ftp] put startup.cfg
[ftp] bye
```

> **运维习惯**：把"型号 + 序列号 + 生产日期 + 维保截止日 + 版本号 + 最近一次备份配置"做成设备台账，每次变更后再补一份配置快照。

---

## 1_6 固件升级标准流程与风险控制
### 升级前检查（不可省略）
```plain
<H3C> display version          # 确认当前版本
<H3C> dir /all                 # 查看 Flash 空间是否足够
<H3C> save                     # 保存配置
<H3C> tftp 192.168.1.100 put startup.cfg pre-upgrade.cfg    # 配置备份到服务器
```

### 标准升级流程
```plain
# 1. 删除旧系统文件（空间不足时）
<H3C> delete /unreserved s3600v2_e-cmw520-r2111p02.bin

# 2. 从 FTP 下载新版本
<H3C> ftp 192.168.1.100
[ftp] get S5120LI-CMW520-R1519P06.bin
[ftp] bye

# 3. 升级 BootRom（视版本要求，非每次必做）
<H3C> bootrom update file S5120LI-CMW520-R1519P06.bin slot 1
# 提示是否加载，输入 Y

# 4. 指定下次启动文件
<H3C> boot-loader file flash:/S5120LI-CMW520-R1519P06.bin slot 1 main
# 提示保存新版本，输入 Y

# 5. 清理并重启
<H3C> reset recycle-bin
<H3C> reboot

# 6. 重启后验证
<H3C> display version
<H3C> dir /all
```

### 升级风险控制表
| 风险 | 控制措施 |
| --- | --- |
| 配置丢失 | 升级前 `save` + TFTP 导出配置 |
| 空间不足 | `dir /all` 检查 → `delete /unreserved` + `reset recycle-bin` |
| 新版本异常 | 用 `boot-loader` 命令把新版本指定为 main、旧版本保留为 backup 启动项 |
| 业务中断 | 选择业务低峰期窗口，提前公告，准备好回退方案 |
| 版本不匹配 | 通过官方渠道或代理商获取与型号、License 匹配的版本 |

> 涉及维保设备的升级，建议通过官方技术支持或代理商获取版本与补丁，避免用到不匹配的公版软件。

### 📌 案例手记：升级后配置"消失"的真相
一台 S5120 升级完成后，工程师发现所有 VLAN 配置都没了。

排查：`display startup` 显示下次启动配置文件为 NULL——升级时只改了启动文件，**配置文件的路径没有同步指定**。

原因：BootRom 升级重置了部分启动参数。

修复：重新指定配置文件并恢复：

```plain
<H3C> startup saved-configuration startup.cfg
<H3C> reboot
```

**教训**：升级前后都要跑一次 `display startup`，确认"主用启动文件 + 备用启动文件 + 下次启动配置文件"三项都在。

---

## 1_7 密码恢复与配置抢救
密码丢失是最常见的"进不去设备"场景，处理分两种思路。

### 思路一：有 Console 权限，跳过认证改密码
1. 通过 Console 口连接设备，重启设备。
2. 启动过程中按 **Ctrl+B** 进入 BootRom 菜单（不同型号按键可能不同，注意启动提示）。
3. 选择 **跳过当前配置启动**（Skip Current System Configuration）。
4. 设备以空配置启动后，用原配置文件恢复业务，并重新设置密码：

```plain
<H3C> startup saved-configuration startup.cfg    # 不要重启，先取出配置
<H3C> reboot
# 重启后配置生效，此时先用 Console 无认证进入
<H3C> system-view
[H3C] local-user admin class manage
[H3C-luser-manage-admin] password cipher NewPass@2024
[H3C-luser-manage-admin] service-type ssh terminal
[H3C-luser-manage-admin] authorization-attribute user-role network-admin
[H3C-luser-manage-admin] quit
[H3C] save force
```

### 思路二：直接删除 / 重置用户密码（保留配置）
部分设备支持在 BootRom 菜单中**清除认证密码但保留配置文件**，这是最理想的方式——业务配置不丢，只重置登录凭据。

### 恢复后的必做验证
```plain
<H3C> display current-configuration | include local-user     # 确认用户存在
<H3C> display local-user                                     # 确认服务类型与角色
<H3C> display startup                                        # 确认启动配置正确
<H3C> save force                                             # 立即保存
```

> **注意**：密码恢复属于高危操作，**必须在客户授权与变更窗口内进行**，并在操作前完整备份配置文件。恢复完成后应触发一次密码更换流程，因为原密码已失控。

---

## 1_8 实验笔记模板与验收清单
### 本板块实验笔记模板
```plain
## 实验：设备开局与配置生命周期管理
日期：____   设备型号：____   Comware 版本：____

### 1. 目标与验收标准
- [ ] 能识别 V5 / V7 并写出三条最常见差异
- [ ] 完成一次"备份 → 修改 → 验证 → 保存 → 回退"全流程
- [ ] 能独立完成配置文件导入导出

### 2. 关键记录
| 项目 | 操作前 | 操作后 |
| --- | --- | --- |
| 版本号 |  |  |
| 启动配置文件 |  |  |
| Flash 剩余空间 |  |  |

### 3. 现象 → 假设 → 验证 → 结论
（至少记录一条"改了没保存"或"版本不匹配"的复现过程）

### 4. 边界与坑
- V5 无 class manage，粘贴 V7 脚本必报错
- reset saved-configuration 后务必确认重启影响范围
```

### 验收清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| 版本识别正确 | `display version` | 能说出 V5/V7 与型号、Uptime |
| 配置文件双备份 | `save backup.cfg` + `tftp put` | Flash 与服务器各一份 |
| 变更可回退 | `compare configuration` | 能看出运行配置与保存配置的差异 |
| 启动项清楚 | `display startup` | 主/备启动文件与下次配置文件路径清晰 |
| 开局清单熟练 | 1_3 的 9 步 | 5 分钟内跑完并记录 |
| 升级风险可控 | 1_6 风险表 | 能说出四类风险与对应措施 |

# 板块2 · 设备登录与远程管理（Console / Telnet / SSH / Web）
> 学习目标：NE 要求会配通；SE 要求会加固（板块10 延伸）；IE 要求能在"登不上设备"的场景下 3 分钟内定位。  
核心认知：**Console 与 VTY 是两条独立的线路，配置互不干扰。**

---

## 2_1 登录方式总览与选型
| 登录方式 | 协议 | 安全性 | 适用场景 | 认证方式 |
| --- | --- | --- | --- | --- |
| Console（AUX 线路） | 串口 | 物理接触，最安全 | 开局、密码恢复、设备救砖 | none / password / scheme |
| Telnet（VTY 线路） | TCP 23，明文 | 低，等保禁止 | 临时调试、老设备兼容 | none / password / scheme |
| SSH（VTY 线路） | TCP 22，加密 | 高，**生产环境标准做法** | 日常远程运维 | password / publickey / password-publickey |
| Web | HTTP/HTTPS | 中（HTTPS 可用） | 快速查看、非命令行用户 | 本地用户 + 服务类型 web |

**H3CNE 考点**：Console 与 Telnet 是两条独立的线路，配置互不干扰。改 Console 认证不会影响 Telnet，反之亦然。这是新手最容易混淆的点——**配完 Telnet 登不上，问题往往出在 VTY 线路没配认证或没开服务**。

### 线路与编号规则
```plain
Console  ：user-interface console 0（部分设备为 aux 0）
VTY      ：user-interface vty 0 4（V5）/ vty 0 63（V7）
```

V7 的 VTY 数量扩展到 64 条，但**同时在线用户数仍受 License 与设备性能限制**。

### ASCII 拓扑：远程管理路径
```plain
  [运维PC]
     |
     |  (1) SSH/Telnet → 管理网段
     |
  [汇聚/核心交换机] ── (2) 三层可达 ── [接入交换机管理IP]
     |
     |  (3) 断网应急
     |
  [Console线 → USB转串口 → 笔记本]
```

---

## 2_2 Console 口登录的三种认证方式
### 方式一：无需认证（none）
```plain
<H3C> system-view
[H3C] user-interface console 0
[H3C-ui-console0] authentication-mode none
```

仅在实验环境或临时排障时使用。**生产环境配置 none，等保测评直接判不符合。**

登录界面直接回车即可进入：

```plain
******************************************************************************
* Copyright (c) ... H3C Technologies Co., Ltd. All rights reserved.          *
******************************************************************************

<H3C>
```

### 方式二：密码认证（password）
```plain
[H3C] user-interface console 0
[H3C-ui-console0] authentication-mode password
[H3C-ui-console0] set authentication password cipher Console@123
```

登录提示变为：

```plain
Password:
<H3C>
```

### 方式三：AAA 认证（scheme，用户名 + 密码）—— 生产推荐
```plain
[H3C] user-interface console 0
[H3C-ui-console0] authentication-mode scheme
[H3C-ui-console0] quit

[H3C] local-user admin class manage
[H3C-luser-manage-admin] password cipher Admin@2024#Con
[H3C-luser-manage-admin] service-type terminal          # 关键：终端服务类型
[H3C-luser-manage-admin] authorization-attribute user-role network-admin
[H3C-luser-manage-admin] quit
[H3C] save force
```

登录界面变为：

```plain
Login authentication
Username:admin
Password:
<H3C>
```

### 三个必错点
1. **忘配 **`service-type terminal`：scheme 认证下用户必须声明服务类型，否则即使密码正确也登不上。Telnet 用户要 `service-type telnet`，SSH 用户要 `service-type ssh`——这是"密码没错但就是登不上"的头号原因。
2. `authorization-attribute`** 漏配**：登上去只有查看权限，进不了系统视图，表现为 `Permission denied`。
3. **Console 属性改完立即生效**：通过 Console 口改 Console 口属性，可能中途断连。建议用 Telnet/SSH 改 Console 属性，改完用 Console 验证时保持终端参数一致（**9600 / 8 / 1 / None / None**）。

---

## 2_3 Telnet 配置（含完整排障）
### 最小可用配置（密码方式）
```plain
<H3C> system-view
[H3C] telnet server enable                       # 开服务（V5 部分设备默认关闭）
[H3C] interface Vlan-interface 1                 # 先有管理 IP 才能远程
[H3C-Vlan-interface1] ip address 192.168.1.1 255.255.255.0
[H3C-Vlan-interface1] undo shutdown
[H3C-Vlan-interface1] quit

[H3C] user-interface vty 0 4
[H3C-ui-vty0-4] authentication-mode password
[H3C-ui-vty0-4] set authentication password cipher Telnet@123
[H3C-ui-vty0-4] user privilege level 3           # 远程用户默认是 0 级，必须提级
[H3C-ui-vty0-4] idle-timeout 10 0                # 10 分 0 秒（等保要求 ≤20 分钟）
[H3C-ui-vty0-4] quit
[H3C] save force
```

### 用户名 + 密码方式（scheme）
```plain
[H3C] telnet server enable
[H3C] user-interface vty 0 4
[H3C-ui-vty0-4] authentication-mode scheme
[H3C-ui-vty0-4] quit

[H3C] local-user h3cadmin class manage
[H3C-luser-manage-h3cadmin] password cipher Telnet@123
[H3C-luser-manage-h3cadmin] service-type telnet
[H3C-luser-manage-h3cadmin] authorization-attribute user-role network-admin
[H3C-luser-manage-h3cadmin] quit
[H3C] save force
```

### Telnet 连不上的七步定位法
| 步骤 | 检查内容 | 不通时的处理 |
| --- | --- | --- |
| 第1步 | 本机 ping 管理 IP 通不通？ | 不通 → 查 IP、VLAN、网关、物理链路 |
| 第2步 | `telnet server enable` 开了吗？ | `display telnet server status` |
| 第3步 | VTY 线路配认证了吗？ | `display current-configuration | begin user-interface` |
| 第4步 | 用户 `service-type` 含 telnet 吗？ | `display local-user` |
| 第5步 | 用户级别 / 角色够吗？ | `display local-user`（否则进去不能 `sys`） |
| 第6步 | VTY 是否被占满？ | `display users`（线路占满后新的连不上） |
| 第7步 | 是否有 ACL 拦截？ | 查看 VTY 下的 `acl inbound` |

### 常用查看命令
```plain
[H3C] display users                       # 当前登录用户
[H3C] display user-interface              # 所有线路状态
[H3C] display user-interface vty 0        # 单条线路详情
[H3C] display tcp                         # 确认 23 端口是否在监听
[H3C] display local-user                  # 本地用户与服务类型
```

> **生产建议**：Telnet 明文传输，等保 2.0 明确要求远程管理走加密协议。配置完 SSH 后应 `undo telnet server enable` 关闭 Telnet，见板块10。

### 📌 案例手记：密码没错，为什么就是登不上？
新入职工程师给一台接入交换机配 Telnet：

```plain
[H3C] local-user netadmin class manage
[H3C-luser-manage-netadmin] password cipher Net@12345
[H3C-luser-manage-netadmin] authorization-attribute user-role network-admin
```

配置看着没问题，但从 PC Telnet 一直提示认证失败。

排查：执行 `display local-user`，发现 **Service type 一栏为空**——漏了 `service-type telnet`。V7 的 scheme 认证下，用户的服务类型必须与登录方式严格匹配，不匹配就拒绝。

修复：补上 `service-type telnet` 后立即登录成功。

**记忆口诀**：**scheme 认证三件套——**`service-type`**、**`authorization-attribute`**、**`authentication-mode scheme`**，缺一不可。**

---

## 2_4 SSH 配置（生产环境标准）
### 密码认证方式（基础 SSH）
```plain
# 1. 生成本地密钥对（SSH 的前置条件，没有密钥对 SSH 起不来）
[H3C] public-key local create rsa
The range of public key modulus is (512 ~ 2048).
Input the modulus length [default = 1024]: 2048      # 建议 2048，1024 已不安全

# 2. 开启 SSH 服务
[H3C] ssh server enable

# 3. VTY 线路仅允许 SSH
[H3C] user-interface vty 0 4
[H3C-ui-vty0-4] authentication-mode scheme
[H3C-ui-vty0-4] protocol inbound ssh
[H3C-ui-vty0-4] quit

# 4. 创建 SSH 登录用户
[H3C] local-user sysadmin class manage
[H3C-luser-manage-sysadmin] password cipher Admin@2024!SSH
[H3C-luser-manage-sysadmin] service-type ssh
[H3C-luser-manage-sysadmin] authorization-attribute user-role network-admin
[H3C-luser-manage-sysadmin] quit
[H3C] save force
```

### 公钥认证方式（更高安全等级）
```plain
# 1. 在客户端生成密钥对（以常见 SSH 工具为例），得到公钥文本
# 2. 在设备上导入客户端公钥
[H3C] public-key peer sshkey import sshkey.pub

# 3. 用户绑定公钥
[H3C] local-user keyuser class manage
[H3C-luser-manage-keyuser] authorization-attribute user-role network-admin
[H3C-luser-manage-keyuser] service-type ssh
[H3C-luser-manage-keyuser] public-key sshkey
[H3C-luser-manage-keyuser] quit

# 4. VTY 下指定认证方式
[H3C] user-interface vty 0 4
[H3C-ui-vty0-4] authentication-mode scheme
[H3C-ui-vty0-4] protocol inbound ssh
```

### SSH 加固建议
```plain
[H3C] ssh server acl 2000                 # 仅允许运维网段 SSH
[H3C] ssh server authentication-retries 3 # 认证重试次数
[H3C] ssh server timeout 60               # 认证超时
[H3C] ssh server compatible-ssh1x disable # 禁用不安全的 SSH1
```

### SSH 验证清单
```plain
<H3C> display ssh server status           # 服务是否开启、版本、端口
<H3C> display ssh server session          # 当前 SSH 会话
<H3C> display public-key local rsa public # 本地密钥对是否存在
<H3C> display tcp | include 22            # 22 端口监听状态
```

---

## 2_5 Web 网管与 HTTPS
```plain
[H3C] ip https enable                     # 开启 HTTPS（推荐）
[H3C] ip http enable                      # 开启 HTTP（不推荐，等保会扣分）
[H3C] local-user webadmin class manage
[H3C-luser-manage-webadmin] password cipher Web@2024
[H3C-luser-manage-webadmin] service-type https            # 或 http
[H3C-luser-manage-webadmin] authorization-attribute user-role network-admin
[H3C-luser-manage-webadmin] quit
```

**验证**：浏览器访问设备的管理 IP，`display ip https` 可确认 HTTPS 服务状态。

> **加固原则**：能用 HTTPS 就不用 HTTP；Web 管理仅在内网管理 VLAN 开放，出口与公网绝不暴露。

---

## 2_6 用户级别与角色体系
| 用户角色 / 级别 | 权限 | 典型用途 |
| --- | --- | --- |
| network-admin（level-15） | 全部配置权限 | 系统管理员 |
| level-2 | 部分配置权限 | 安全管理员（策略类） |
| network-operator（level-1） | 只读 | 审计管理员、监控账号 |
| level-0 | 仅网络诊断命令（ping、tracert） | 一线值守 |

### 命令行级别与用户级别的关系
+ **用户级别**决定能执行哪些级别的命令。
+ **命令级别**分 0~3 级（访问级、监控级、系统级、管理级）。
+ V7 推荐用 `user-role`（基于角色）而不是 `level`（基于数字），粒度更细 等保可解释性更好。

```plain
[H3C] local-user auditadmin class manage
[H3C-luser-manage-auditadmin] authorization-attribute user-role network-operator
[H3C-luser-manage-auditadmin] service-type ssh
```

---

## 2_7 登录类故障速查表
| 现象 | 最可能原因 | 定位命令 |
| --- | --- | --- |
| 密码正确但认证失败 | 缺 `service-type` | `display local-user` |
| 能登但进不了系统视图 | 缺 `authorization-attribute` 或级别不够 | `display local-user` |
| Telnet 连接被拒绝 | 服务未开 / ACL 拦截 | `display telnet server status` |
| SSH 连不上 | 未生成密钥对 / 服务未开 | `display public-key local rsa public` |
| 提示 VTY 占满 | 有僵死会话 | `display users` → `free user-interface vty X` |
| Console 无响应 | 终端参数不对 | 确认 9600/8/1/None/None |
| 远程能连但本地 ping 不通 | ICMP 被 ACL 拦或管理口未放开 | `display acl all` |

### 踢掉僵死会话
```plain
<H3C> display users
<H3C> free user-interface vty 2
```

---

## 2_8 实验笔记模板与验收清单
### 笔记模板
```plain
## 实验：Console / Telnet / SSH 三类登录配置与排障
日期：____   设备：____   版本：____

### 1. 目标与验收
- [ ] Console 三种认证方式各配一遍
- [ ] Telnet 配通并完成一次"故意漏配 service-type"的复现
- [ ] SSH 配通，且 telnet 已关闭
- [ ] 完成七步定位法的完整走查

### 2. 关键配置片段（只记关键行）
    local-user X class manage
     service-type ssh
     authorization-attribute user-role network-admin

### 3. 现象 → 假设 → 验证 → 结论
- 现象：Telnet 提示 Login failed
- 假设：service-type 缺失 / VTY 认证模式不匹配 / ACL 拦截
- 验证：display local-user 看服务类型为空
- 结论：scheme 模式下服务类型必须显式声明

### 4. 边界
- 改 Console 认证时不要在 Console 会话里改，避免断连
- VTY 数量 V5 与 V7 不同
```

### 验收清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| Console scheme 认证可用 | Console 登录 | 需用户名 + 密码，且能进系统视图 |
| Telnet 配通 | `display telnet server status` | 状态为 enabled，PC 可登录 |
| SSH 配通 | `display ssh server status` | 22 端口监听，可登录 |
| Telnet 已关闭 | `display telnet server status` | 生产环境为 disabled |
| 用户角色正确 | `display local-user` | 服务类型、角色与用途匹配 |
| 超时符合等保 | `display current-configuration | begin user-interface` | idle-timeout ≤ 20 分钟 |
| 排障熟练 | 七步定位法 | 能在 3 分钟内走完 |

# 板块3 · 以太网交换原理、端口管理与状态排查
> 本板块是 H3CNE 的核心得分板块，也是所有后续配置（VLAN、STP、堆叠）的物理载体。  
结构：原理 → 配置 → 排查，三段式推进。

---

## 3_1 交换机转发原理：必须能口述的三件事
### 3_1_1 MAC 地址学习
交换机收到数据帧后，用**源 MAC + 入端口 + VLAN** 三元组更新 MAC 地址表，然后用**目的 MAC + VLAN** 查表决定动作：

| 目的 MAC 类型 | 动作 |
| --- | --- |
| 单播且表中有表项 | 从对应端口单播转发；若出端口 = 入端口则丢弃 |
| 单播但表中无表项 | 泛洪到同 VLAN 内的其他所有端口 |
| 广播 / 组播（未开启组播优化） | 泛洪到同 VLAN 内的其他所有端口 |

### MAC 表查看与维护
```plain
[H3C] display mac-address                        # 查看整表
[H3C] display mac-address 00e0-fc23-f8d3         # 查某个 MAC
[H3C] display mac-address interface g1/0/1       # 查某端口学到的 MAC
[H3C] display mac-address vlan 100               # 查某 VLAN 的 MAC
[H3C] display mac-address count                  # MAC 表项统计（判断是否有 MAC 漂移/泛洪）
[H3C] display mac-address mac-move               # 查看 MAC 漂移记录（V7 支持）
[H3C] mac-address timer aging 300                # 修改老化时间（默认 300 秒）
```

**MAC 漂移排查**：同一 MAC 在两个端口间反复出现，通常意味着环路。这是"全网慢、丢包、CPU 飙升"最常见的根因之一。

### 3_1_2 三种交换模式
| 模式 | 特点 | 现状 |
| --- | --- | --- |
| 直通转发（Cut-through） | 读到目的 MAC 就转发，延迟低 | **不校验错误帧**，会转发残帧 |
| 存储转发（Store-and-forward） | 收完整帧并 CRC 校验后转发 | **主流，H3C 默认** |
| 无碎片（Fragment-free） | 读前 64 字节后转发 | 折中，少用 |

> 考题常问"哪一种会转发残帧"——答案：**直通转发**。

### 3_1_3 冲突域与广播域
+ 交换机**每个端口隔离冲突域** → 端口越多，冲突域越多。
+ 交换机**所有端口默认在同一广播域（VLAN 1）** → 只有 VLAN 才能隔离广播域。
+ **路由器 / 三层接口隔离广播域**。

### ASCII 示意：广播域与冲突域
```plain
   交换机（未划分 VLAN）
   +---------------------------+
   |  PC1   PC2   PC3   PC4    |   ← 4 个冲突域，1 个广播域
   +---------------------------+

   交换机（划分 VLAN10 / VLAN20）
   +---------------------------+
   | [PC1 PC2]   [PC3 PC4]     |   ← 4 个冲突域，2 个广播域
   |  VLAN10       VLAN20      |
   +---------------------------+
```

---

## 3_2 端口视图与基本参数配置
### 3_2_1 进入端口的三种写法
```plain
[H3C] interface GigabitEthernet 1/0/1     # 全写
[H3C] interface gigabitethernet 1/0/1     # 不区分大小写
[H3C] int g1/0/1                          # 简写（实战常用）
```

### 3_2_2 速率与双工
```plain
[H3C-GigabitEthernet1/0/1] speed 1000                 # 10 / 100 / 1000 / auto
[H3C-GigabitEthernet1/0/1] duplex full                # half / full / auto
[H3C-GigabitEthernet1/0/1] undo negotiation auto      # 关闭自协商（需先手工指定速率双工）
[H3C-GigabitEthernet1/0/1] negotiation auto           # 恢复自协商
```

**配置原则（非常重要）**：

+ 绝大多数场景**保持 auto**，两端自协商即可。
+ **一端强制、一端自协商是经典故障**：自协商端会 fallback 到半双工，导致大量 CRC 错误与丢包，现象是"能 ping 通但很慢"。
+ **光口不支持配置速率 / 双工**；端口加入聚合组后不能在成员口上单独配置速率双工。

### 3_2_3 端口描述、开关与其他参数
```plain
[H3C-GigabitEthernet1/0/1] description To-FileServer-01     # 描述，最长 80 字符
[H3C-GigabitEthernet1/0/1] shutdown                          # 关闭
[H3C-GigabitEthernet1/0/1] undo shutdown                     # 开启
[H3C-GigabitEthernet1/0/1] flow-control                      # 开启流控（默认关闭）
[H3C-GigabitEthernet1/0/1] broadcast-suppression 20          # 广播抑制 20%
[H3C-GigabitEthernet1/0/1] multicast-suppression 20          # 组播抑制
[H3C-GigabitEthernet1/0/1] unicast-suppression 20            # 未知单播抑制
[H3C-GigabitEthernet1/0/1] loopback internal                 # 内环测试（排查端口硬件故障）
[H3C-GigabitEthernet1/0/1] mdi auto                          # 自动翻转（normal 直通 / across 交叉）
[H3C-GigabitEthernet1/0/1] jumboframe enable 9216            # 开启巨帧（存储/视频网常用）
[H3C-GigabitEthernet1/0/1] default                           # 恢复端口默认配置
```

**端口描述是分水岭**：新手从不写 `description`，老手开局必写。一个 48 口交换机，没有描述的端口在故障排查时等于盲盒。等保测评也会检查这项。

### 📌 案例手记："能 ping 通但特别慢"的双工谜案
某单位文件服务器迁移后，员工反馈访问共享目录极慢，但 `ping` 只丢一两个包。

排查过程：

1. `display interface g1/0/5` —— 发现 **Input errors 中 CRC 计数持续增长**。
2. 看对端服务器网卡 —— 被人为设成 **100M 全双工强制**。
3. 交换机侧是 `negotiation auto` —— 自协商端 fallback 到 **100M 半双工**。
4. 结果：**一端全双工、一端半双工 = 典型的双工不匹配**，大量冲突与重传。

修复：两端统一为自协商（或两端都强制成相同参数），CRC 停止增长，访问速度恢复正常。

**口诀**：**速率双工要么两端都 auto，要么两端都手工且完全一致，绝不能一强一自。**

---

## 3_3 批量端口管理：interface range 与 port-group
### 3_3_1 interface range（临时批量，V7 推荐）
```plain
[H3C] interface range GigabitEthernet 1/0/1 to GigabitEthernet 1/0/24
[H3C-if-range] undo shutdown
[H3C-if-range] description TO-Office-PC
[H3C-if-range] port link-type access
[H3C-if-range] port access vlan 10
[H3C-if-range] stp edged-port enable
[H3C-if-range] quit

# 不连续端口（最多 5 组）
[H3C] interface range g1/0/1 g1/0/3 g1/0/5 to g1/0/8

# 命名端口组，方便反复调用
[H3C] interface range name PORT-GROUP1 g1/0/1 to g1/0/10
[H3C] interface range name PORT-GROUP1
[H3C-if-range] undo shutdown
```

### 3_3_2 port-group（持久端口组，适合长期维护）
```plain
[H3C] port-group manual IDLE-PORTS
[H3C-port-group-manual-idle-ports] group-member g1/0/25 to g1/0/48
[H3C-port-group-manual-idle-ports] quit

# 对整组端口做统一策略：关闭 + 加入隔离 VLAN
[H3C] interface range name IDLE-PORTS
[H3C-if-range] shutdown
[H3C-if-range] port access vlan 999
```

### 两者区别
| 对比项 | interface range | port-group |
| --- | --- | --- |
| 持久性 | 一次性，退出即失效 | 持久对象，保存在配置文件中 |
| 适用场景 | 临时批量操作 | 需要反复调整的集合（闲置端口组、边缘端口组） |

---

## 3_4 端口状态查看与过滤技巧
### 3_4_1 核心命令
```plain
<H3C> display interface brief
<H3C> display interface brief | include DOWN      # 只看 DOWN 的口
<H3C> display interface brief | include ADM       # 只看被手工关闭的口
<H3C> display interface g1/0/1                    # 单端口详细信息
<H3C> display interface g1/0/1 | include rate     # 看速率与双工
```

### 输出解读（二层部分）
```plain
GE1/0/1    UP     1G(a)   F(a)   A    1
GE1/0/2    DOWN   --      --     A    1
GE1/0/3    ADM    --      --     A    1    Disabled_Unused
```

| 字段 | 含义 |
| --- | --- |
| Link | UP / DOWN / ADM（Administratively Down，手工关闭） |
| Speed | 1G(a) 表示自协商成千兆，(f) 表示强制 |
| Duplex | F(a) 全双工自协商，H 表示半双工 |
| Type | A 表示 Access，T 表示 Trunk，H 表示 Hybrid |
| PVID | 端口默认 VLAN ID |

### Link 状态三态速查
| 状态 | 含义 | 处理 |
| --- | --- | --- |
| UP | 接口正常连通 | — |
| DOWN | 接口未接线或网线未插好 | 检查物理链路、对端端口 |
| ADM | 手动关闭（Administratively Down） | `undo shutdown` 开启 |

### 3_4_2 端口流量与错误统计
```plain
<H3C> display interface g1/0/1
# 重点关注：
#   Input:  packets, errors, CRC, align errors
#   Output: packets, errors, collisions
#   Last 300 seconds input rate / output rate

<H3C> reset counters interface g1/0/1     # 清零统计后观察增量（判断是否还在增长）
```

**排障技巧**：先看错误计数，**清零后等 5 分钟再看**。如果 CRC 还在涨，说明问题持续存在；如果不涨了，可能是历史遗留。

---

## 3_5 端口 DOWN 排查九宫格
| 现象 | 检查 | 处理 |
| --- | --- | --- |
| 端口 ADM | `display interface brief` | `undo shutdown` |
| 端口 DOWN 但线插着 | 换线、换口测试 | 排除线缆问题 |
| 一端 UP 一端 DOWN | `display dldp` | 单向链路，检查光纤收发，开启 DLDP |
| 光口 DOWN | `display transceiver diagnosis` | 查光功率、模块型号匹配、收发光纤是否交叉 |
| 电口 DOWN 但灯亮 | 查速率双工 | 统一 auto 或统一强制 |
| 端口频繁 UP/DOWN | `display logbuffer` | 线缆接触不良、模块故障、光衰过大 |
| CRC 持续增长 | `display interface` | 换线、查光衰、查双工 |
| 新设备端口全 DOWN | 查是否 `shutdown` 默认 | 批量 `undo shutdown` |
| 端口 UP 但无流量 | 查 VLAN、STP 状态 | 是否被 STP 阻塞 |

### 光模块诊断（真机）
```plain
<H3C> display transceiver interface Ten-GigabitEthernet 1/0/49
<H3C> display transceiver diagnosis interface Ten-GigabitEthernet 1/0/49
```

关注三项：**接收光功率（Rx Power）**、**发送光功率（Tx Power）**、**温度**。接收光功率过低（接近灵敏度下限）会导致误码甚至链路 DOWN。

---

## 3_6 端口镜像与抓包
### 本地端口镜像
```plain
[H3C] mirroring-group 1 local
[H3C] mirroring-group 1 mirroring-port g1/0/1 both      # 被镜像口（both = 双向）
[H3C] mirroring-group 1 monitor-port g1/0/24            # 观察口（接抓包 PC）
```

**验证**：

```plain
<H3C> display mirroring-group 1
```

### 远程端口镜像（跨设备，RSPAN 思路）
```plain
# 源设备
[H3C] mirroring-group 1 remote-source
[H3C] mirroring-group 1 mirroring-port g1/0/1 both
[H3C] mirroring-group 1 reflector-port g1/0/23
[H3C] mirroring-group 1 remote-probe vlan 999

# 目的设备
[H3C] mirroring-group 1 remote-destination
[H3C] mirroring-group 1 monitor-port g1/0/24
[H3C] mirroring-group 1 remote-probe vlan 999
```

### 设备自带抓包（V7 支持）
```plain
<H3C> packet-capture interface g1/0/1 inbound
# 按提示抓包并保存，可导出后分析
```

> **实战价值**：抓包是"证明流量到底有没有到设备"的终极手段。当 `display` 命令看不出问题时，抓包能一锤定音——DHCP 请求有没有上来、ARP 有没有响应、OSPF Hello 有没有发。

### 📌 案例手记：用镜像抓包定位"DHCP 拿不到地址"
故障：某楼层新装终端全部拿不到地址，其他楼层正常。

排查：

1. 在接入交换机上做本地镜像，把上行口流量镜像到笔记本。
2. 抓包发现：**终端的 DHCP Discover 有发出去，但没有收到 Offer**。
3. 顺着往上看：汇聚交换机的 `display dhcp relay` 显示中继地址配置成了**旧服务器地址**（服务器已迁移）。
4. 修正中继地址后立刻恢复。

**结论**：没有镜像抓包，很可能一直在接入层"换线、换口"打转。**先确认"请求有没有到响应有没有回"，再决定往哪查。**

---

## 3_7 端口安全（接入层防护基础）
```plain
[H3C-GigabitEthernet1/0/1] port-security enable
[H3C-GigabitEthernet1/0/1] port-security max-mac-count 1          # 只允许 1 个 MAC
[H3C-GigabitEthernet1/0/1] port-security port-mode autolearn      # 自动学习并绑定
[H3C-GigabitEthernet1/0/1] port-security intrusion-mode disableport  # 违规后关闭端口
```

**验证**：

```plain
<H3C> display port-security interface g1/0/1
<H3C> display mac-address security
```

**适用场景**：接入层防止私接 Hub、防止非法终端接入。但要注意——**接 IP 电话再接 PC 的场景需要放宽 MAC 数量**，否则会误伤。

---

## 3_8 实验笔记模板与验收清单
### 笔记模板
```plain
## 实验：端口管理与 DOWN 排查
日期：____   设备：____

### 1. 目标与验收
- [ ] 用 interface range 批量完成 24 口配置（含 description）
- [ ] 复现一次双工不匹配并观察 CRC 增长
- [ ] 完成一次本地镜像抓包

### 2. 关键记录
| 端口 | 期望速率/双工 | 实际 | 错误计数（5分钟增量） |
| --- | --- | --- | --- |
| g1/0/5 | 1G/F auto |  |  |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：ping 通但慢
- 假设：双工不匹配 / 广播风暴 / 上行拥塞
- 验证：display interface 看 CRC 增长 + 抓包看重传
- 结论：对端强制全双工导致本端 fallback 半双工

### 4. 边界
- 聚合成员口不能单独配速率双工
- 光口不支持速率/双工配置
```

### 验收清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| 端口总览清晰 | `display interface brief` | 能区分 UP / DOWN / ADM 与 PVID |
| 批量配置正确 | `display current-configuration interface` | 24 口配置一致且有描述 |
| 速率双工无 mismatch | `display interface | include rate` | 两端一致，无 CRC 增长 |
| 错误统计清零验证 | `reset counters` + 复查 | 5 分钟后无新增错误 |
| 镜像可用 | `display mirroring-group 1` | 抓包 PC 能收到被镜像流量 |
| 光模块健康 | `display transceiver diagnosis` | 收发光功率在正常范围 |
| 端口安全生效 | `display port-security interface` | 超限后按预期动作处理 |

# 板块4 · VLAN 与三层互通（从创建 VLAN 到跨网段通信）
> 本板块是整份知识库的重心。  
NE 要求"配得通"，SE 要求"选得对（Super VLAN / QinQ / MVRP）"，IE 要求"排得快"。  
VLAN 划分是项目应用中最频繁的操作，所有命令均可直接在 HCL 或真机上复现。

---

## 4_1 VLAN 原理与 802.1Q 帧格式
### 4_1_1 为什么需要 VLAN
一台二层交换机所有端口默认属于同一个广播域。广播域过大会带来三个问题：

1. **广播风暴风险**：ARP、DHCP 等广播报文被泛洪到所有端口，浪费带宽与终端 CPU。
2. **安全性差**：不同部门的终端在二层可直接互访，无法隔离。
3. **故障域大**：一台终端出问题（如环路）会影响全网。

VLAN（Virtual LAN）的本质是**在二层帧上打标记，把一台物理交换机逻辑切成多台交换机**。

### 4_1_2 802.1Q 标签格式（考试必考）
标准以太网帧在源 MAC 与类型字段之间插入 4 字节 Tag：

```plain
+----------+----------+--------+---------+--------+------+------+
| 目的MAC  | 源MAC    | TPID   |  TCI    | 类型   | 数据 | FCS  |
|  (6B)    |  (6B)    | 0x8100 | PRI+CFI| (2B)   |      | (4B) |
|          |          |  (2B)  | +VID   |        |      |      |
|          |          |        |  (2B)  |        |      |      |
+----------+----------+--------+---------+--------+------+------+
                          |         |
                          |         +-- PRI(3bit) + CFI(1bit) + VID(12bit)
                          +------------ TPID 固定 0x8100
```

| 字段 | 位数 | 值 |
| --- | --- | --- |
| TPID | 16 bit | 固定 0x8100，标识这是 802.1Q 帧 |
| PRI | 3 bit | 802.1p 优先级，0~7，用于 QoS |
| CFI | 1 bit | 规范格式指示，以太网中恒为 0 |
| VID | 12 bit | VLAN ID，范围 1~4094 |

**关键结论**：

+ VLAN ID 只有 12 bit，所以可用范围是 **1~4094**（0 和 4095 保留）。
+ **VLAN 1 是默认 VLAN，不可删除**，且默认所有端口都在 VLAN 1 中——这是现网最大的安全隐患之一，等保测评会要求把业务口移出 VLAN 1。
+ 带 Tag 的帧长度上限从 1518 字节变为 **1522 字节**。

### 4_1_3 VLAN 的三种划分方式
| 方式 | 依据 | 适用场景 | H3C 支持 |
| --- | --- | --- | --- |
| 基于端口（最常用） | 物理端口 | 固定终端接入 | 所有型号 |
| 基于 MAC 地址 | 终端 MAC | 移动办公 | 部分型号 |
| 基于协议 / 子网 | 三层协议或 IP 网段 | 特殊场景 | 支持 |
| 基于策略（组合） | MAC + IP + 端口组合 | 高安全准入 | 支持 |

考试与项目 90% 以上用**基于端口的 VLAN**，本板块以此为主。

---

## 4_2 一步步创建 VLAN（NE 核心操作）
### 4_2_1 最小三步法
```plain
<H3C> system-view                             # 第1步 进系统视图
[H3C] vlan 10                                 # 第2步 创建 VLAN 10（若不存在则自动创建）
[H3C-vlan10] port GigabitEthernet 1/0/1       # 第3步 把端口加入 VLAN
[H3C-vlan10] quit
[H3C] save force
```

就这么简单。但实际项目要做得更规范，见 4_2_3。

### 4_2_2 等价写法：在端口视图下加入
```plain
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] port link-type access      # 先设链路类型为 access
[H3C-GigabitEthernet1/0/1] port access vlan 10        # 再加入 VLAN（V7 等价：port default vlan 10）
```

两种方式效果相同，但有一个**关键差异**：

+ 在 **VLAN 视图**下用 `port` 命令**只能加 access 端口**，不能加 trunk/hybrid 端口。
+ 在 **端口视图**下 `port access vlan` 会**自动把端口链路类型设为 access**。

### 4_2_3 生产环境推荐写法（带描述与批量）
```plain
<H3C> system-view
[H3C] sysname ACC-SW-A

# 批量创建 VLAN 并命名
[H3C] vlan 10
[H3C-vlan10] name Office
[H3C-vlan10] quit
[H3C] vlan 20
[H3C-vlan20] name Finance
[H3C-vlan20] quit
[H3C] vlan 30
[H3C-vlan30] name Camera
[H3C-vlan30] quit
[H3C] vlan 99
[H3C-vlan99] name Mgmt
[H3C-vlan99] quit

# 批量端口加入 VLAN
[H3C] interface range GigabitEthernet 1/0/1 to GigabitEthernet 1/0/8
[H3C-if-range] description TO-Office-PC
[H3C-if-range] port link-type access
[H3C-if-range] port access vlan 10
[H3C-if-range] stp edged-port enable
[H3C-if-range] quit

[H3C] interface range GigabitEthernet 1/0/9 to GigabitEthernet 1/0/12
[H3C-if-range] description TO-Finance-PC
[H3C-if-range] port link-type access
[H3C-if-range] port access vlan 20
[H3C-if-range] stp edged-port enable
[H3C-if-range] quit
[H3C] save force
```

### 4_2_4 批量创建多个 VLAN
```plain
[H3C] vlan 10 to 20                      # 连续创建 VLAN 10~20
[H3C] vlan batch 10 20 30 40             # 部分版本支持 batch 关键字
```

### 4_2_5 删除 VLAN
```plain
[H3C] undo vlan 10        # 删除指定 VLAN
[H3C] undo vlan all       # 删除除缺省 VLAN 外的所有 VLAN（VLAN 1 不可删）
```

> **重要**：删除 VLAN 后，原属于该 VLAN 的端口会**回到 VLAN 1**，可能导致广播域意外扩大。删除前先 `display vlan 10` 确认端口归属。

---

## 4_3 Access / Trunk / Hybrid 与 PVID
### 4_3_1 三种链路类型对帧的处理方式
| 链路类型 | 接收帧的处理 | 发送帧的处理 | 典型用途 |
| --- | --- | --- | --- |
| Access | 收到无 Tag 帧 → 打上端口 PVID；收到带 Tag 帧 → 若 VID = PVID 则接收，否则丢弃 | **剥离 Tag 后发送**（始终不带 Tag） | 接 PC、打印机、服务器单 VLAN |
| Trunk | 无 Tag 帧 → 打上 PVID；带 Tag 帧 → 若在 permit 列表内则接收 | 若 VID = PVID → 剥离 Tag；否则**保留 Tag** | 交换机之间、交换机与路由器 |
| Hybrid | 同 Trunk | **可针对每个 VLAN 单独指定 tagged / untagged** | 灵活场景：一个口既接 PC 又传多 VLAN |

**Trunk 的 PVID 行为要特别注意**：Trunk 口发送 PVID 所属 VLAN 的帧时会**剥离 Tag**。如果两端 Trunk 的 PVID 不一致，会造成 VLAN 泄漏或通信异常——**trunk 线路两端的 PVID 必须一致**。

### 4_3_2 Access 配置
```plain
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] port link-type access
[H3C-GigabitEthernet1/0/1] port access vlan 20        # 等价 V7：port default vlan 20
```

### 4_3_3 Trunk 配置
```plain
[H3C] interface GigabitEthernet 1/0/24
[H3C-GigabitEthernet1/0/24] port link-type trunk
[H3C-GigabitEthernet1/0/24] port trunk permit vlan 10 20 30    # 只允许指定 VLAN 通过
[H3C-GigabitEthernet1/0/24] port trunk permit vlan all         # 允许所有（不推荐，广播域失控）
[H3C-GigabitEthernet1/0/24] port trunk pvid vlan 99            # 修改 PVID（慎用，两端必须一致）
[H3C-GigabitEthernet1/0/24] undo port trunk permit vlan 1      # 禁止 VLAN 1 通过（安全加固推荐）
```

**最佳实践**：Trunk 口**显式 permit 业务 VLAN + **`undo permit vlan 1`，而不是图省事用 `permit vlan all`。这是项目交付与等保检查的常见扣分项。

### 4_3_4 Hybrid 配置（SE 考点）
**场景**：服务器需要同时属于 VLAN 10（业务）和 VLAN 20（管理），且希望不同 VLAN 的帧以不同方式发出。

```plain
[H3C] interface GigabitEthernet 1/0/10
[H3C-GigabitEthernet1/0/10] port link-type hybrid
[H3C-GigabitEthernet1/0/10] port hybrid vlan 10 tagged        # VLAN 10 带 Tag 发出
[H3C-GigabitEthernet1/0/10] port hybrid vlan 20 untagged      # VLAN 20 剥 Tag 发出
[H3C-GigabitEthernet1/0/10] port hybrid pvid vlan 20          # 无 Tag 帧归入 VLAN 20
```

**典型应用**：

+ 服务器的网卡是普通 PC 网卡（不认 Tag），但又要承载多个业务 VLAN → Hybrid + 一个 untagged 业务 VLAN。
+ 交换机下接 AP，管理 VLAN untagged，业务 VLAN tagged → Hybrid。

### ASCII 示意：三种链路类型的 Tag 处理
```plain
                Access 口                     Trunk 口                    Hybrid 口
               (PVID=10)                 (PVID=1, permit 10,20)      (PVID=20, 10 tagged, 20 untagged)

PC --untag-->  [ 打上 VID10 ]             [ 打上 VID1 ]
PC <--untag--  [ 剥离 Tag   ]             [ VID=1 剥离，VID=10/20 保留 ]

交换机 --tag(V10)-->  [ 丢弃（VID≠PVID）]   [ 在 permit 内 → 接收 ]     [ VID10 → 带tag转发 ]
                                                                        [ VID20 → 去tag转发 ]
```

---

## 4_4 三层互通：Vlan-interface 与单臂路由
### 4_4_1 三层交换机实现 VLAN 间互通（主流做法）
```plain
[H3C] interface Vlan-interface 10
[H3C-Vlan-interface10] ip address 192.168.10.1 24
[H3C-Vlan-interface10] undo shutdown
[H3C-Vlan-interface10] quit

[H3C] interface Vlan-interface 20
[H3C-Vlan-interface20] ip address 192.168.20.1 24
[H3C-Vlan-interface20] undo shutdown
[H3C-Vlan-interface20] quit
```

**验证**：

```plain
<H3C> display ip interface brief          # Vlan-interface 状态与 IP
<H3C> display ip routing-table            # 直连路由是否生成
```

> **注意**：Vlan-interface 要 UP，必须满足两个条件之一：第1步 该 VLAN 内有**至少一个 Access 端口处于 UP**；第2步 有 Trunk 口 permit 该 VLAN 且端口 UP。否则接口状态为 DOWN，三层不通。

### 4_4_2 单臂路由（路由器子接口）
**场景**：只有二层交换机 + 一台路由器，需要实现 VLAN 间互通。

```plain
# 路由器侧
[H3C] interface GigabitEthernet 0/0.10
[H3C-GigabitEthernet0/0.10] vlan-type dot1q vid 10
[H3C-GigabitEthernet0/0.10] ip address 192.168.10.1 24
[H3C-GigabitEthernet0/0.10] quit

[H3C] interface GigabitEthernet 0/0.20
[H3C-GigabitEthernet0/0.20] vlan-type dot1q vid 20
[H3C-GigabitEthernet0/0.20] ip address 192.168.20.1 24
[H3C-GigabitEthernet0/0.20] quit

# 交换机侧：上联口配 Trunk
[H3C] interface GigabitEthernet 1/0/24
[H3C-GigabitEthernet1/0/24] port link-type trunk
[H3C-GigabitEthernet1/0/24] port trunk permit vlan 10 20
```

**优缺点**：

| 对比 | 三层交换机 | 单臂路由 |
| --- | --- | --- |
| 性能 | 硬件转发，线速 | 受路由器接口带宽限制，容易成瓶颈 |
| 成本 | 三层交换机较贵 | 已有路由器时可省成本 |
| 适用 | 园区网主流 | 小型网络、临时方案 |

### ASCII 拓扑：VLAN 间三层互通
```plain
        VLAN10                VLAN20                VLAN30
     192.168.10.0/24       192.168.20.0/24       192.168.30.0/24
          |                      |                      |
    +-----+------+         +-----+------+         +------+-----+
    |            |         |            |         |            |
   PC1          PC2       PC3          PC4       CAM1        CAM2
    |            |         |            |         |            |
    +-----+------+         +-----+------+         +------+-----+
          |                      |                      |
          +----------+-----------+----------+-----------+
                     |                      |
              [ 三层交换机 Core ]
              Vlan-int10: 192.168.10.1
              Vlan-int20: 192.168.20.1
              Vlan-int30: 192.168.30.1
                     |
              （各网段网关在此，VLAN 间通过直连路由互通）
```

### 📌 案例手记：网关能 ping 通，PC 之间不通
现象：核心交换机上创建了 Vlan-interface 10/20，PC 都能 ping 通自己的网关，但跨 VLAN 不通。

排查：

1. `display ip interface brief` —— Vlan-int 10 和 20 都是 **UP**，IP 正确。
2. `display ip routing-table` —— 两条直连路由都在。
3. 查 PC 的网关配置 —— 都填了正确的网关。
4. `ping` 测试：PC1 → 网关通，网关 → PC2 通，PC1 → PC2 **不通**。
5. 最后发现：**PC 上开了防火墙，禁用了 ICMP 回显**。

**结论**：三层交换机负责转发，**终端自身的防火墙也会拦截 ICMP**。排障要用"分段测试法"：PC→网关、网关→对端网关、对端网关→对端 PC，逐段定位。

**延伸教训**：如果分段测试中"网关→对端 PC"不通，那才是网络问题（查 VLAN、Trunk、ARP）。

---

## 4_5 Super VLAN 与 Isolate-user-VLAN（SE 考点）
### 4_5_1 Super VLAN（VLAN 聚合）
**解决问题**：每个 VLAN 一个 /24 子网会浪费大量 IP（子网号、广播地址、网关地址）。Super VLAN 让多个 Sub VLAN 共享一个三层网段，**Sub VLAN 之间二层隔离、三层通过 Super VLAN 接口互通**。

```plain
[H3C] vlan 100
[H3C-vlan100] supervlan                        # 配置为 Super VLAN
[H3C-vlan100] subvlan 10 20 30                 # 关联 Sub VLAN
[H3C-vlan100] quit

[H3C] interface Vlan-interface 100
[H3C-Vlan-interface100] ip address 192.168.1.1 24
[H3C-Vlan-interface100] quit
```

**Sub VLAN 间互通**：默认二层隔离，需要三层互通时开启本地代理 ARP：

```plain
[H3C-Vlan-interface100] local-proxy-arp enable
```

**验证**：

```plain
<H3C> display supervlan
<H3C> display subvlan
```

**典型场景**：酒店、宿舍楼、小区宽带——每个房间一个 Sub VLAN 做二层隔离，所有房间共享一个大网段，节省 IP。

### 4_5_2 Isolate-user-VLAN（端口隔离）
```plain
[H3C] vlan 10
[H3C-vlan10] isolate-user-vlan enable          # 开启用户隔离
[H3C-vlan10] quit
```

或更常用的端口隔离组：

```plain
[H3C] port-isolate group 1
[H3C] interface range g1/0/1 to g1/0/24
[H3C-if-range] port-isolate enable group 1
```

**效果**：同一 VLAN 内的端口之间二层不能互访，但都能访问上行口（网关）。

**验证**：

```plain
<H3C> display port-isolate group 1
```

**典型场景**：宾馆客房、会议室、运营商宽带接入——防止横向扫描与攻击。

### 两者对比
| 特性 | Super VLAN | Isolate-user-VLAN / 端口隔离 |
| --- | --- | --- |
| 层次 | 三层地址聚合 | 二层互访隔离 |
| 是否省 IP | 是 | 否 |
| 是否隔离二层 | Sub VLAN 间天然隔离 | 同 VLAN 内隔离 |
| 互通方式 | 通过 Super VLAN 接口 + 本地代理 ARP | 通过上行口（网关） |

---

## 4_6 QinQ 与 MVRP（SE 考点）
### 4_6_1 QinQ（802.1Q-in-Q）
**解决问题**：运营商或大型园区需要**透传用户的 VLAN**，但 4094 个 VLAN ID 不够用。QinQ 在用户 VLAN Tag 外面再打一层运营商 VLAN Tag。

```plain
      用户帧            QinQ 封装后
   [ 内层 C-Tag ]  →  [ 外层 S-Tag ][ 内层 C-Tag ]
      VLAN 10            VLAN 100      VLAN 10
```

**基本 QinQ 配置**：

```plain
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] port link-type trunk
[H3C-GigabitEthernet1/0/1] port trunk permit vlan 100
[H3C-GigabitEthernet1/0/1] qinq enable                 # 开启 QinQ
[H3C-GigabitEthernet1/0/1] qinq vlan-id 100            # 统一打外层 Tag 100
```

**灵活 QinQ**（按内层 VLAN 打不同外层 Tag）：

```plain
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] qinq enable
[H3C-GigabitEthernet1/0/1] qinq vlan-id-translation 10 to 20 100   # 内层 10~20 → 外层 100
```

**验证**：`display qinq interface`、`display vlan`。

### 4_6_2 MVRP（多 VLAN 注册协议，类 GVRP）
**作用**：在交换机之间**自动同步 VLAN 信息**，避免手工在每台设备上创建 VLAN。

```plain
# 全局开启
[H3C] mvrp global enable

# 端口开启（Trunk 口）
[H3C] interface GigabitEthernet 1/0/24
[H3C-GigabitEthernet1/0/24] port link-type trunk
[H3C-GigabitEthernet1/0/24] port trunk permit vlan all
[H3C-GigabitEthernet1/0/24] mvrp enable
[H3C-GigabitEthernet1/0/24] mvrp registration normal      # normal / fixed / forbidden
```

**三种注册模式**：

| 模式 | 含义 |
| --- | --- |
| normal | 正常注册与注销，动态学习对端 VLAN |
| fixed | 只传播本地静态 VLAN，不学习对端 |
| forbidden | 禁止该端口传播任何 VLAN |

**验证**：`display mvrp state`、`display mvrp statistics`。

> **实战建议**：MVRP 在大型园区网能大幅减少配置量，但**动态 VLAN 会让排障变复杂**（不知道 VLAN 是哪来的）。生产环境建议关键链路用 fixed 模式，边缘用 normal。

---

## 4_7 VLAN 排障与验证清单
### 典型故障与定位
| 现象 | 检查 | 处理 |
| --- | --- | --- |
| 同 VLAN 内不通 | `display vlan 10`、`display mac-address` | 核对端口是否在该 VLAN、链路类型是否正确 |
| 跨设备同 VLAN 不通 | `display port trunk` | Trunk 未 permit 该 VLAN |
| VLAN 1 泄漏 | `display vlan 1` | 业务口移出 VLAN 1，Trunk `undo permit vlan 1` |
| Vlan-interface DOWN | `display ip interface brief` | 该 VLAN 内无 UP 端口，检查 Trunk/成员口 |
| 网关通但跨网段不通 | `display ip routing-table` | 查三层路由 |
| Trunk 两端不通 | `display port trunk` | PVID 不一致 或 permit 列表不匹配 |
| 删 VLAN 后广播域变大 | `display vlan 1` | 端口回落到 VLAN 1，需重新规划 |

### 验证命令清单
```plain
<H3C> display vlan                            # VLAN 总览
<H3C> display vlan 10                         # 指定 VLAN 详情（含成员端口）
<H3C> display interface brief                 # 端口链路类型与 PVID
<H3C> display port trunk                      # Trunk 端口的 permit 与 PVID
<H3C> display ip interface brief              # Vlan-interface 状态
<H3C> display ip routing-table                # 直连路由
<H3C> display mac-address vlan 10             # 某 VLAN 的 MAC 表
<H3C> display supervlan / display subvlan     # Super VLAN 状态
<H3C> display port-isolate group 1            # 端口隔离组
<H3C> display qinq interface                  # QinQ 状态
<H3C> display mvrp state                      # MVRP 状态
```

### 📌 案例手记：Trunk PVID 不一致引发的"灵异"故障
现象：两台交换机之间，VLAN 10 的终端时通时断，VLAN 20 完全正常。

排查：

1. A 交换机 GE1/0/24：`port trunk pvid vlan 10`（有人为了"方便管理"改过）。
2. B 交换机 GE1/0/24：PVID 保持默认 1。
3. 结果：A 侧发出的 VLAN 10 帧被**剥离 Tag**（因为 VID=PVID），B 侧收到无 Tag 帧后打上 PVID=1，于是 VLAN 10 的流量被送进了 VLAN 1。

修复：两端 PVID 统一为 1（或统一为同一个非业务 VLAN），VLAN 10 立即恢复正常。

**铁律**：**Trunk 两端 PVID 必须一致，且不要用业务 VLAN 做 Trunk 的 PVID。**

---

## 4_8 实验笔记模板与验收清单
### 笔记模板
```plain
## 实验：VLAN 划分与三层互通
日期：____   设备：____

### 1. 目标与验收
- [ ] 批量创建 VLAN 并命名
- [ ] Access / Trunk / Hybrid 各配一遍并验证 Tag 行为
- [ ] 三层互通：PC1 ↔ PC2 跨 VLAN 通
- [ ] 完成一次 Super VLAN 或端口隔离实验

### 2. 规划表（先画再配）
| VLAN | 名称 | 网段 | 网关 | 端口范围 |
| --- | --- | --- | --- | --- |
| 10 | Office | 192.168.10.0/24 | .1 | g1/0/1-8 |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：跨设备同 VLAN 不通
- 假设：Trunk 未 permit / PVID 不一致 / 链路类型错
- 验证：display port trunk 对比两端
- 结论：PVID 不一致导致 Tag 被错误剥离

### 4. 边界
- VLAN 视图下只能加 access 口
- 删除 VLAN 会让端口回到 VLAN 1
- Vlan-interface UP 的前提是 VLAN 内有 UP 端口
```

### 验收清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| VLAN 创建正确 | `display vlan` | VLAN ID 与名称符合规划表 |
| 端口归属正确 | `display vlan 10` | 成员端口与规划一致 |
| Trunk 配置正确 | `display port trunk` | permit 列表精确，PVID 两端一致，已 undo vlan 1 |
| 三层接口 UP | `display ip interface brief` | Vlan-interface 状态 UP |
| 跨网段互通 | `ping` | PC1 能 ping 通 PC2 与其网关 |
| 隔离生效 | `ping`（隔离场景） | 同 VLAN 内两台 PC 不通，但都能通网关 |
| Super VLAN 正常 | `display supervlan` | Sub VLAN 关联正确，网段共享生效 |

# 板块5 · 生成树协议（STP / RSTP / MSTP）与环路防护
> 生成树是园区网"不出事"的底线技术。  
NE 要求懂原理会配置，SE 要求能做多实例负载分担，IE 要求能在"全网瘫痪"场景下 10 分钟内定位环路。

---

## 5_1 为什么需要生成树：二层环路的三大危害
冗余链路是高可用网络的必然选择，但二层冗余会形成环路，带来三个灾难性问题：

| 危害 | 机制 |
| --- | --- |
| 广播风暴 | 广播帧在环路中被无限循环转发，瞬间占满带宽，全网瘫痪 |
| MAC 地址表震荡 | 同一 MAC 从不同端口反复学习，MAC 表被反复覆盖，转发错乱 |
| 帧重复 | 同一数据帧多次到达目的端，上层协议处理异常 |

**关键认知**：二层帧**没有 TTL（生存时间）字段**，一旦成环就永不消失，只能靠物理断链或协议阻塞解决。这就是 STP 存在的唯一理由——**在保留物理冗余的同时，逻辑上阻塞部分端口，破除环路**。

### ASCII 示意：环路的形成与破除
```plain
       【环路形成】                        【STP 阻塞后】
        SW1 ---- SW2                        SW1 ---- SW2
         |        |                          |        |
         |        |                          |        |
        SW3 ------+                         SW3 ------X   ← 逻辑阻塞（BPDU 计算得出）
                                              |
   广播帧在 SW1→SW2→SW3→SW1 无限循环        逻辑树：SW1 为根，无环
   MAC 表反复震荡，CPU 飙升
```

### 📌 案例手记：一根网线放倒整栋办公楼
某公司前台为了方便，把墙上的两个网口用一根网线直接连了起来（接在同一台接入交换机上）。

结果：整栋楼的终端上网极慢，然后彻底断网。

现场现象：

+ 所有交换机端口灯疯狂闪烁。
+ 登录交换机非常卡（CPU 被打满）。
+ `display cpu-usage` 显示 90% 以上。
+ `display mac-address count` 暴涨，`display mac-address mac-move` 显示大量漂移记录。
+ `display stp brief` —— 发现这台交换机**根本没开 STP**（默认关闭）。

处理：拔掉那根网线，网络立刻恢复。随后全局开启 STP，并在所有接入端口配置边缘端口 + BPDU 保护。

**教训**：**H3C 设备的 STP 默认是关闭的，必须手工 **`stp enable`**。** 这是最容易被忽略、代价也最高的一条。

---

## 5_2 STP（802.1D）原理
### 5_2_1 基本思路
1. 选举**根桥**（Root Bridge）：全网桥 ID 最小的交换机。
2. 每个非根桥选一个**根端口**（Root Port）：到根桥路径开销最小的端口。
3. 每条链路选一个**指定端口**（Designated Port）。
4. 剩下的端口**阻塞**（Blocking）。

### 5_2_2 桥 ID 与端口 ID
```plain
桥 ID（Bridge ID）= 优先级（16 bit，默认 32768，步长 4096） + MAC 地址（48 bit）
端口 ID（Port ID） = 优先级（4 bit，默认 128，步长 16） + 端口号
```

### 路径开销标准
| 链路速率 | 802.1D 开销 | 802.1t（H3C 默认） |
| --- | --- | --- |
| 10 Mbps | 100 | 2,000,000 |
| 100 Mbps | 19 | 200,000 |
| 1 Gbps | 4 | 20,000 |
| 10 Gbps | 2 | 2,000 |
| 40 Gbps | 1 | 500 |

> **注意**：`stp pathcost-standard` 全网必须一致，否则计算结果会与预期不符。

### 5_2_3 BPDU 与定时器
BPDU（Bridge Protocol Data Unit）是 STP 的协议报文，默认每 2 秒发送一次，目的 MAC 为组播 **01-80-C2-00-00-00**。

| 定时器 | 默认值 | 作用 |
| --- | --- | --- |
| Hello Time | 2 秒 | 根桥发送 BPDU 的间隔 |
| Forward Delay | 15 秒 | Listening → Learning、Learning → Forwarding 各等 15 秒 |
| Max Age | 20 秒 | BPDU 老化时间，超时认为根桥失效 |

### 5_2_4 端口状态机（考试高频）
```plain
Blocking ──(Max Age 20s)──> Listening ──(15s)──> Learning ──(15s)──> Forwarding
   |                                                                      |
   +──────────────── 链路故障或拓扑变化 ─────────────────────────────────+

Blocking   ：只收 BPDU，不转发数据                 （20 秒 Max Age）
Listening  ：收发 BPDU，不学习 MAC，不转发数据     （15 秒 Forward Delay）
Learning   ：学习 MAC，不转发数据                  （15 秒 Forward Delay）
Forwarding ：正常转发                              （稳定态）
Disabled   ：端口未启用
```

**STP 收敛时间**：端口从阻塞到转发最多需要 **30~50 秒**（Max Age 20 + 2×Forward Delay 30）。这个速度在现代网络里是不可接受的，于是有了 RSTP。

---

## 5_3 RSTP（802.1w）：快速收敛
### 5_3_1 相比 STP 的改进
| 改进点 | 说明 |
| --- | --- |
| 端口状态简化 | 5 种 → 3 种：**Discarding / Learning / Forwarding** |
| 新增端口角色 | **Alternate**（根端口备份）、**Backup**（指定端口备份） |
| 收敛机制 | 引入 **P/A（Proposal/Agreement）握手机制**，可实现秒级收敛 |
| 边缘端口 | 接终端的端口可**立即进入 Forwarding**，无需等待 30 秒 |

### 5_3_2 P/A 机制简述
新链路 UP 后：

1. 两端先都假定自己是指定端口，互发 **Proposal 置位**的 BPDU。
2. 收到更优 BPDU 的一方**阻塞自己的端口**并回送 **Agreement**。
3. 上游收到 Agreement 后**立即进入 Forwarding**。
4. 这个过程逐段向下游推进，**无需依赖定时器**，因此收敛极快。

### 5_3_3 边缘端口
```plain
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] stp edged-port enable
```

边缘端口 UP 后立即进入 Forwarding，跳过 30 秒等待——这是**终端接入体验的关键**（否则开机后要等 30 秒才能上网，DHCP 还会超时）。

**批量配置**：

```plain
[H3C] interface range g1/0/1 to g1/0/24
[H3C-if-range] stp edged-port enable
```

---

## 5_4 MSTP（802.1s）：多实例负载分担
### 5_4_1 为什么需要 MSTP
STP/RSTP 的缺陷：**所有 VLAN 共用一棵生成树**，被阻塞的链路完全闲置，浪费带宽。  
MSTP 引入"实例"概念，把不同 VLAN 映射到不同实例，**每个实例独立计算生成树**，从而实现负载分担。

```plain
    实例 1（VLAN 10、20）：SW1 为主根 → 流量走左边链路
    实例 2（VLAN 30、40）：SW2 为主根 → 流量走右边链路
    结果：两条上行链路都被利用，且互为备份
```

### 5_4_2 MST 域三要素（必须一致，否则无法互通）
同一 MST 域内的交换机，以下三项配置必须**完全相同**：

1. **域名**（Region Name）
2. **修订级别**（Revision Level）
3. **VLAN 与实例的映射关系**

> 三要素不一致，交换机会被认为处于不同 MST 域，导致实例计算异常。这是 MSTP 最常见的配置错误。

### 5_4_3 MSTP 配置（SE 必会）
```plain
# 1. 进入 MST 域视图
[H3C] stp region-configuration
[H3C-mst-region] region-name H3C-Campus
[H3C-mst-region] revision-level 1
[H3C-mst-region] instance 1 vlan 10 20
[H3C-mst-region] instance 2 vlan 30 40
[H3C-mst-region] active region-configuration        # 必须激活，否则配置不生效
[H3C-mst-region] quit

# 2. 开启 STP 并设为 MSTP 模式
[H3C] stp enable
[H3C] stp mode mstp

# 3. 核心交换机 A：实例 1 主根、实例 2 备根
[H3C] stp instance 1 root primary                   # 优先级自动设为 0
[H3C] stp instance 2 root secondary                 # 优先级自动设为 4096

# 4. 核心交换机 B：相反
[H3C-B] stp instance 1 root secondary
[H3C-B] stp instance 2 root primary
```

**手工指定优先级（等价写法）**：

```plain
[H3C] stp instance 1 priority 4096      # 步长 4096，取值 0/4096/8192.../61440
```

### 5_4_4 查看与验证
```plain
<H3C> display stp                                # 全局 STP 状态
<H3C> display stp brief                          # 端口角色与状态速览（最常用）
<H3C> display stp instance 1 brief               # 指定实例
<H3C> display stp root                           # 查看根桥信息
<H3C> display stp region-configuration           # 查看 MST 域配置
<H3C> display stp interface g1/0/1               # 单端口 STP 详情
```

### display stp brief 输出解读
```plain
MST ID   Port                      Role   STP State     Protection
0        GigabitEthernet1/0/1      ROOT   FORWARDING    NONE
0        GigabitEthernet1/0/2      ALTE   DISCARDING    NONE
1        GigabitEthernet1/0/1      ROOT   FORWARDING    NONE
1        GigabitEthernet1/0/2      DESI   FORWARDING    NONE
```

**Role 列含义**：

| 角色 | 含义 |
| --- | --- |
| ROOT | 根端口（去往根桥的最优端口） |
| DESI | 指定端口（转发下游流量） |
| ALTE | Alternate 备份（根端口的备份） |
| BACK | Backup 备份（指定端口的备份） |

---

## 5_5 生成树保护机制（SE/IE 必会）
| 保护机制 | 作用 | 配置 | 适用场景 |
| --- | --- | --- | --- |
| BPDU 保护 | 边缘端口收到 BPDU 后立即关闭端口 | `stp bpdu-protection` | 接入层边缘端口 |
| 根保护 | 防止新接入的交换机抢占根桥 | 端口下 `stp root-protection` | 核心/汇聚下行口 |
| 环路保护 | 防止单向链路导致环路 | 端口下 `stp loop-protection` | 光纤链路 |
| TC 保护 | 限制 TC-BPDU 处理频率，防攻击 | `stp tc-protection` | 全局 |
| 防 TC-BPDU 攻击 | 单位时间内处理 TC-BPDU 的次数限制 | `stp tc-protection threshold 3` | 全局 |

### 配置示例
```plain
# 全局开启 BPDU 保护（配合边缘端口使用）
[H3C] stp bpdu-protection

# 边缘端口（收到 BPDU 会被 shutdown）
[H3C] interface range g1/0/1 to g1/0/24
[H3C-if-range] stp edged-port enable

# 根保护（在汇聚/核心的下行口）
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] stp root-protection

# 环路保护（光纤链路）
[H3C-GigabitEthernet1/0/1] stp loop-protection

# TC 保护
[H3C] stp tc-protection
[H3C] stp tc-protection threshold 3
```

> **BPDU 保护后的恢复**：被 shutdown 的端口默认不会自动恢复，需手工 `undo shutdown`，或配置自动恢复：

```plain
[H3C] shutdown-interval 300     # 部分版本支持定时自动恢复
```

---

## 5_6 环路检测与故障定位
### 5_6_1 环路检测（Loopback Detection）
```plain
# 全局开启
[H3C] loopback-detection global enable vlan 1 to 4094

# 端口开启并配置动作
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] loopback-detection enable vlan 1 to 4094
[H3C-GigabitEthernet1/0/1] loopback-detection action shutdown
```

**查看**：

```plain
<H3C> display loopback-detection
```

### 5_6_2 环路故障定位五步法
```plain
第1步 现象确认：全网慢 / 部分慢 / 时通时断？
第2步 CPU 检查：display cpu-usage（环路时通常 > 70%）
第3步 MAC 漂移：display mac-address mac-move（看漂移记录）
第4步 STP 状态：display stp brief（看是否有异常角色变化）
第5步 逐段拔线：在可疑交换机上逐个拔端口，观察 CPU 与现象变化
```

**辅助判据**：

```plain
<H3C> display interface | include broadcast      # 广播包是否异常增长
<H3C> display logbuffer                          # 是否有端口频繁 UP/DOWN
<H3C> display stp tc                             # TC 计数是否异常增长（拓扑震荡）
```

### 📌 案例手记：STP 没开 + 新交换机接入 = 全网瘫痪
某园区新增一台接入交换机，工程师接好线后没做任何配置就上电（该交换机 STP 默认关闭）。

结果：新交换机与原有网络形成环路，全网中断。

定位过程：

1. 核心交换机 `display cpu-usage` → 95%。
2. `display mac-address mac-move` → 大量 MAC 在两个上行口间漂移。
3. `display stp brief` → 新交换机的端口 STP 状态为 Disabled（未开启）。
4. 拔掉新交换机上行线 → CPU 立即恢复正常。

**整改**：

+ 全网统一开启 MSTP 并规划实例。
+ 所有接入端口配边缘端口 + BPDU 保护。
+ 接入交换机上线前先完成基础模板配置（含 STP、管理 IP、SSH）。

**沉淀成规范**：**新设备入网前必须套用标准模板，不允许裸机上线。**

---

## 5_7 生成树配置命令汇总
```plain
[H3C] stp enable                              # 开启 STP（默认关闭，必须手工开启！）
[H3C] stp mode { stp | rstp | mstp }          # 工作模式，默认 mstp
[H3C] stp priority 4096                       # 设置本交换机优先级（CIST 实例 0）
[H3C] stp root primary                        # 设为根桥（自动优先级 0）
[H3C] stp root secondary                      # 设为备份根桥（自动优先级 4096）
[H3C] stp pathcost-standard { dot1d-1998 | dot1t | legacy }   # 路径开销标准，全网必须一致
[H3C] stp timer forward-delay 1500            # 修改 Forward Delay（单位厘秒，一般不改）
[H3C] stp timer hello 200
[H3C] stp timer max-age 2000
[H3C] stp bpdu-protection                     # BPDU 保护
[H3C] stp tc-protection                       # TC 保护

# 端口级
[H3C-GigabitEthernet1/0/1] stp edged-port enable        # 边缘端口
[H3C-GigabitEthernet1/0/1] stp root-protection          # 根保护
[H3C-GigabitEthernet1/0/1] stp loop-protection          # 环路保护
[H3C-GigabitEthernet1/0/1] stp cost 20000               # 修改端口开销
[H3C-GigabitEthernet1/0/1] stp port priority 16         # 修改端口优先级
[H3C-GigabitEthernet1/0/1] stp disable                  # 端口关闭 STP（慎用）
```

---

## 5_8 实验笔记模板与验收清单
### 笔记模板
```plain
## 实验：MSTP 多实例负载分担 + 保护机制
日期：____   设备：____

### 1. 目标与验收
- [ ] MSTP 域三要素配置正确，两台核心实例主备相反
- [ ] 实例 1 与实例 2 的阻塞端口不同（证明负载分担生效）
- [ ] BPDU 保护生效：边缘端口接交换机后被 shutdown
- [ ] 人为制造环路，能在 5 分钟内定位

### 2. MST 域规划表
| 实例 | VLAN | 主根 | 备根 |
| --- | --- | --- | --- |
| 1 | 10,20 | SW-A | SW-B |
| 2 | 30,40 | SW-B | SW-A |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：实例 1 与实例 2 阻塞同一个口（负载分担没生效）
- 假设：MST 域三要素不一致 / 实例未激活 / 主备配置反了
- 验证：display stp region-configuration 对比两端
- 结论：忘记执行 active region-configuration

### 4. 边界
- STP 默认关闭，必须 stp enable
- 三要素不一致会被视为不同域
- BPDU 保护 shutdown 的端口需手工恢复
```

### 验收清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| STP 已开启 | `display stp` | 全局状态为 enabled |
| 工作模式正确 | `display stp` | 模式为 MSTP |
| MST 域一致 | `display stp region-configuration` | 域名、修订级别、映射三要素一致，已激活 |
| 根桥符合规划 | `display stp root` | 实例 1/2 的根桥与设计一致 |
| 负载分担生效 | `display stp brief` | 不同实例阻塞不同端口 |
| 边缘端口生效 | `display stp interface` | 接入口为边缘端口，状态 FORWARDING |
| 保护机制生效 | 人为接交换机测试 | 边缘口被 shutdown 并记录日志 |
| 环路可定位 | 五步法 | 5 分钟内定位并消除 |

# 板块6 · 网络高可靠性：链路聚合、IRF 堆叠、M-LAG、VRRP 与 BFD
> 本板块对应 H3CSE-RS-SW（GB0-372）的核心章节，也是 H3CIE 实验中"高可靠网络规划与部署"的必考内容。  
核心能力：**知道每种技术解决什么问题、失效边界在哪、什么时候该换另一种。**

---

## 6_1 链路聚合（Link Aggregation）
### 6_1_1 作用与模式
链路聚合把多条物理链路捆绑成一条逻辑链路，实现**带宽叠加 + 链路冗余 + 负载分担**。

| 模式 | 协议 | 特点 |
| --- | --- | --- |
| 静态聚合 | 无 | 手工配置，两端不协商；配置错误时可能形成环路或丢包 |
| 动态聚合 | LACP（802.3ad） | 通过 LACPDU 协商，自动检测对端，安全性高，**生产推荐** |

### 6_1_2 配置（V7 标准写法）
```plain
# 1. 创建二层聚合接口
[H3C] interface Bridge-Aggregation 1
[H3C-Bridge-Aggregation1] link-aggregation mode dynamic      # 动态 LACP（静态则无需此行）
[H3C-Bridge-Aggregation1] port link-type trunk
[H3C-Bridge-Aggregation1] port trunk permit vlan 10 20 30
[H3C-Bridge-Aggregation1] quit

# 2. 把物理端口加入聚合组
[H3C] interface GigabitEthernet 1/0/49
[H3C-GigabitEthernet1/0/49] port link-aggregation group 1
[H3C-GigabitEthernet1/0/49] quit

[H3C] interface GigabitEthernet 1/0/50
[H3C-GigabitEthernet1/0/50] port link-aggregation group 1
[H3C-GigabitEthernet1/0/50] quit
```

**配置顺序很重要**：先创建聚合接口并配置好属性，再把物理端口加入组。成员端口会**自动继承**聚合接口的 VLAN、STP 等二层配置，因此**不要在成员端口上单独配 VLAN**。

**三层聚合**（路由器之间或交换机三层互联）：

```plain
[H3C] interface Route-Aggregation 1
[H3C-Route-Aggregation1] ip address 10.0.0.1 30
[H3C-Route-Aggregation1] quit

[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] port link-aggregation group 1
```

### 6_1_3 负载分担模式
```plain
[H3C] link-aggregation global load-sharing mode source-mac destination-mac
[H3C] link-aggregation global load-sharing mode source-ip destination-ip source-port destination-port
```

可选依据：`source-mac`、`destination-mac`、`source-ip`、`destination-ip`、`source-port`、`destination-port`，可组合。

**选型建议**：

+ 二层环境用 **MAC 哈希**。
+ 三层环境用 **IP 哈希**。
+ 若流量集中在少数几台服务器（"大象流"），应加入**端口号做五元组哈希**，否则可能出现单条链路跑满、另一条空闲的"极化"现象。

### 6_1_4 查看与排错
```plain
<H3C> display link-aggregation verbose                        # 聚合组详细信息
<H3C> display link-aggregation summary                        # 聚合组汇总
<H3C> display link-aggregation verbose Bridge-Aggregation 1   # 指定聚合组
<H3C> display lacp system-id                                  # 本端 LACP 系统 ID
<H3C> display interface Bridge-Aggregation 1                  # 聚合接口流量
```

### 常见故障
| 现象 | 原因 | 处理 |
| --- | --- | --- |
| 成员口状态为 **I**（Individual） | 两端聚合模式不一致（一动一静） | 统一为 dynamic 或 static |
| 成员口未选中 | 端口速率 / 双工 / VLAN 配置不一致 | 统一成员端口基础配置 |
| 加入聚合组报错 | 端口上已有独立配置（如已配 VLAN） | `default` 清空端口配置后再加 |
| 聚合口不转发 | 聚合接口被 shutdown | `undo shutdown` |
| 流量只走一条 | 哈希算法与流量特征不匹配 | 改用五元组哈希 |

> **限制**：端口隔离与端口镜像的成员口**不能加入聚合组**。设置端口镜像或端口隔离的端口需先清除配置。

---

## 6_2 IRF 技术原理
### 6_2_1 什么是 IRF
IRF（Intelligent Resilient Framework，智能弹性架构）是 H3C 自研的**横向虚拟化技术**，IRF2 为第二代。  
核心思想：将多台物理设备通过堆叠链路连接，**虚拟化为一台逻辑设备**，在网络中以单一设备形态运行。

| 价值 | 说明 |
| --- | --- |
| 简化管理 | 多台变一台，统一 IP、统一配置，一机管理 |
| 提高性能 | 各成员设备有独立 CPU，可独立处理协议报文与转发 |
| 高可靠性 | Master 故障后 Slave 自动接替，实现 1:N 设备级备份 |
| 弹性扩展 | 按需增加成员设备，扩展端口密度与转发能力 |

### IRF 与 M-LAG 的选型
| 对比 | IRF | M-LAG / DRNI |
| --- | --- | --- |
| 控制平面 | 合一（一台逻辑设备） | 独立（两台设备仍是两台） |
| 配置复杂度 | 简单 | 较复杂 |
| 升级影响 | **需整机重启**，主备切换有秒级中断 | **可独立升级**，业务几乎无感知 |
| 适用场景 | 园区网（推荐） | 金融、数据中心核心（对中断零容忍） |

**一句话**：**园区网首选 IRF，数据中心核心首选 M-LAG。**

### 6_2_2 核心概念
#### 成员编号（Member ID）
+ 范围通常 1~10（不同机型略有差异）。
+ 建立 IRF 时各成员编号**必须唯一**，否则无法建立。
+ 修改后**必须保存配置并重启才生效**。
+ 主设备建议保持编号 1。

```plain
[H3C] irf member 1 renumber 2
<H3C> save force
<H3C> reboot
```

#### 成员优先级（Priority）
+ 缺省值 1，**数值越大越优先当选 Master**。
+ 推荐：主设备设 16~32，备设备保持默认或更低。

```plain
[H3C] irf member 1 priority 32
```

#### IRF 端口与连接铁律
每台设备有两个 IRF 逻辑端口：

| IRF 端口 | 连接规则 |
| --- | --- |
| IRF-Port1（irf-port 1/1） | **只能与邻居的 IRF-Port2 相连** |
| IRF-Port2（irf-port 1/2） | **只能与邻居的 IRF-Port1 相连** |

> 这是 IRF 堆叠的铁律：**本端 IRF-Port1 ****↔**** 对端 IRF-Port2**。接反了堆叠起不来，是最常见的现场错误。

**IRF 物理端口要求**：

+ 必须工作在**二层模式**才能与 IRF 端口绑定。
+ 一个 IRF 端口可绑定多个物理端口（提升带宽与可靠性）。
+ 所有物理端口均 down 时，IRF 端口才 down。
+ 绑定后自动关闭三层功能，转为专用堆叠通道。

#### IRF 域（Domain）
+ 一个 IRF 对应一个域，用 **Domain ID** 区分同一网络中的不同 IRF。
+ 缺省 Domain ID 为 0。
+ **重要**：若 LACP MAD / ARP MAD / ND MAD 组网的中间设备本身也是 IRF 系统，两者的 **Domain ID 必须不同**，否则会造成检测异常甚至业务中断。

```plain
[H3C] irf domain 10
```

### 6_2_3 角色选举规则（按优先级从高到低）
1. **当前 Master 优先** —— 已有 Master 的设备优先保持。
2. **本地主控板优先** —— 本地主控板优于本地备用主控板。
3. **优先级数值大优先** —— 缺省 1。
4. **系统运行时间长优先**。
5. **桥 MAC 地址小优先**。

> **软件升级机制**：升级 Master 时，其他成员设备自动同步升级，只需在 Master 上执行升级操作。

### 6_2_4 连接拓扑
| 拓扑 | 结构 | 特点 |
| --- | --- | --- |
| 链形（Daisy-Chain） | A—B—C | 配置简单、线缆少；**任一链路故障即导致 IRF 分裂** |
| 环形（Ring） | A—B—C—D—A | **推荐方案**；单链路故障时自动降级为链形，业务不中断；至少需 3 台成员 |

**生产环境强烈推荐环形连接**。两台设备时只能链形，此时更依赖 MAD 检测来防止分裂。

```plain
  链形：  [SW1] ══ [SW2] ══ [SW3]

  环形：  [SW1] ══ [SW2]
            ║        ║
          [SW4] ══ [SW3]
```

### 6_2_5 连接介质
| 介质 | 适用场景 |
| --- | --- |
| 专用堆叠线缆 + 专用接口卡 | 高性能、高可靠要求 |
| 以太网电缆（交叉线） | 成本敏感、短距离 |
| 光纤（SFP+ / SFP28） | 部署灵活、长距离 |
| DAC 铜缆（SFP+ 高速线缆） | 性价比高、防松动 |

> 线缆长度超过 3 米建议用光纤，避免信号衰减。

---

## 6_3 IRF 配置实战（完整可复现）
### 6_3_1 场景
两台交换机 DeviceA、DeviceB 组建 IRF2，每台用两个万兆口做堆叠口：

```plain
   DeviceA (Master)              DeviceB (Standby)
   Ten-Gig1/0/49          ←──→   Ten-Gig2/0/49
   Ten-Gig1/0/50          ←──→   Ten-Gig2/0/50

   连接规则：DeviceA 的 IRF-Port2 → DeviceB 的 IRF-Port1（交叉互联）
```

### 6_3_2 DeviceA 配置（主设备）
```plain
<H3C> system-view
[H3C] sysname DeviceA
[DeviceA] undo info-center enable                    # 关闭日志，避免刷屏（可选）

# 1. 配置成员编号与优先级（A 保持编号 1，设高优先级确保成为 Master）
[DeviceA] irf member 1 priority 32

# 2. 先关闭堆叠物理端口（必须先关，否则无法绑定到 IRF 端口）
[DeviceA] interface range Ten-GigabitEthernet 1/0/49 to Ten-GigabitEthernet 1/0/50
[DeviceA-if-range] shutdown
[DeviceA-if-range] quit

# 3. 创建 IRF 端口并绑定物理端口
[DeviceA] irf-port 1/2
[DeviceA-irf-port1/2] port group interface Ten-GigabitEthernet 1/0/49
[DeviceA-irf-port1/2] port group interface Ten-GigabitEthernet 1/0/50
[DeviceA-irf-port1/2] quit

# 4. 重新打开物理端口
[DeviceA] interface range Ten-GigabitEthernet 1/0/49 to Ten-GigabitEthernet 1/0/50
[DeviceA-if-range] undo shutdown
[DeviceA-if-range] quit

# 5. 激活 IRF 配置（关键步骤，容易漏）
[DeviceA] irf-port-configuration active
[DeviceA] save force
```

### 6_3_3 DeviceB 配置（备设备）
```plain
<H3C> system-view
[H3C] sysname DeviceB

# 1. 修改成员编号为 2（必须唯一，改完需重启生效）
[DeviceB] irf member 1 renumber 2
[DeviceB] quit
<DeviceB> save force
<DeviceB> reboot

# 重启后，端口号变为 Ten-GigabitEthernet 2/0/x
<H3C> system-view
[H3C] sysname DeviceB
[DeviceB] irf member 2 priority 1                    # 优先级低于 A

# 2. 关闭物理端口
[DeviceB] interface range Ten-GigabitEthernet 2/0/49 to Ten-GigabitEthernet 2/0/50
[DeviceB-if-range] shutdown
[DeviceB-if-range] quit

# 3. 创建 IRF 端口（注意：B 用 irf-port 2/1，与 A 的 1/2 交叉）
[DeviceB] irf-port 2/1
[DeviceB-irf-port2/1] port group interface Ten-GigabitEthernet 2/0/49
[DeviceB-irf-port2/1] port group interface Ten-GigabitEthernet 2/0/50
[DeviceB-irf-port2/1] quit

# 4. 打开物理端口
[DeviceB] interface range Ten-GigabitEthernet 2/0/49 to Ten-GigabitEthernet 2/0/50
[DeviceB-if-range] undo shutdown
[DeviceB-if-range] quit

# 5. 激活并保存
[DeviceB] irf-port-configuration active
[DeviceB] save force

# 6. 重启（两台设备重启后自动组建 IRF）
[DeviceB] quit
<DeviceB> reboot
```

> **注意**：两台设备都配置完成后**分别重启**，重启后自动完成 IRF 选举与合并。合并后备设备会自动同步主设备的配置。

### 6_3_4 验证
```plain
<H3C> display irf                        # IRF 成员信息与角色
<H3C> display irf configuration          # IRF 端口与物理端口绑定
<H3C> display irf topology               # 拓扑结构
<H3C> display irf link                   # 堆叠链路状态
<H3C> display device                     # 能看到两台成员设备
```

**正常输出特征**：

```plain
MemberID  Role    Priority  CPU-Mac         Description
1         Master  32        xxxx-xxxx-xxxx  DeviceA
2         Standby 1         xxxx-xxxx-xxxx  DeviceB
```

### 📌 案例手记：IRF-Port 接反了，堆叠死活起不来
现场两台 S5560 做 IRF，配置全部照抄，但重启后始终是两台独立设备。

排查：

1. `display irf link` —— 堆叠口状态为 DOWN。
2. 检查物理连接 —— A 的 49/50 口连到 B 的 49/50 口。
3. 检查配置 —— **A 用的是 irf-port 1/2，B 用的也是 irf-port 2/1**，看起来是对的。
4. 再查物理连线走向：A 的 Ten-Gig1/0/49 实际接的是 B 的 Ten-Gig2/0/50，而 A 的 50 接的是 B 的 49——**交叉了**。

**问题本质**：IRF 端口是逻辑绑定，要求"本端 IRF-Port1 只能连对端 IRF-Port2"。物理线交叉后，等于 A 的 IRF-Port2 一部分连到了 B 的 IRF-Port1、一部分没连上，导致协商失败。

修复：理顺物理连线（49↔49、50↔50，或统一规范为 49↔50、50↔49），堆叠立即建立。

**沉淀成规范**：**堆叠线缆两端贴标签，标注 "IRF-Port1/2 - A49"**，避免后期维护时接错。

---

## 6_4 MAD 检测机制（防分裂）
### 6_4_1 为什么需要 MAD
IRF 分裂（堆叠链路断开）后，两台设备都会有相同的 IP 与配置，造成**网络中出现两台"相同"的设备**——IP 冲突、转发混乱。MAD（Multi-Active Detection）的作用就是**检测到分裂后，让其中一半进入 Recovery 状态（业务口全部关闭）**，只保留一个 Active。

### 6_4_2 三种 MAD 方式
| 方式 | 原理 | 特点 |
| --- | --- | --- |
| LACP MAD | 通过 LACP 报文携带 Domain ID 与 Active ID | 需中间设备支持 LACP，**最常用** |
| ARP MAD / ND MAD | 通过免费 ARP / ND 报文检测 | 需中间设备，配置简单 |
| BFD MAD | 通过专用三层链路跑 BFD | **需独立 MAD 链路**，检测最快，最可靠 |

### 6_4_3 LACP MAD 配置（推荐）
```plain
# IRF 系统侧（聚合口开 LACP MAD）
[H3C] interface Bridge-Aggregation 1
[H3C-Bridge-Aggregation1] link-aggregation mode dynamic
[H3C-Bridge-Aggregation1] mad enable
[H3C-Bridge-Aggregation1] quit

# 中间设备侧（普通交换机，正常配置动态聚合即可）
[MID] interface Bridge-Aggregation 1
[MID-Bridge-Aggregation1] link-aggregation mode dynamic
[MID-Bridge-Aggregation1] quit
```

### 6_4_4 BFD MAD 配置（最可靠）
```plain
# 创建 MAD 专用 VLAN 与三层接口
[H3C] vlan 4000
[H3C-vlan4000] quit
[H3C] interface Vlan-interface 4000
[H3C-Vlan-interface4000] mad bfd enable
[H3C-Vlan-interface4000] mad ip address 192.168.255.1 24 member 1
[H3C-Vlan-interface4000] mad ip address 192.168.255.2 24 member 2
[H3C-Vlan-interface4000] quit

# 把 MAD 链路端口加入 VLAN 4000
[H3C] interface GigabitEthernet 1/0/48
[H3C-GigabitEthernet1/0/48] port access vlan 4000
[H3C-GigabitEthernet1/0/48] quit
[H3C] interface GigabitEthernet 2/0/48
[H3C-GigabitEthernet2/0/48] port access vlan 4000
[H3C-GigabitEthernet2/0/48] quit

# MAD 接口不参与 STP（避免被阻塞）
[H3C] undo stp enable vlan 4000        # 或在接口上关闭 STP
```

### 6_4_5 验证与恢复
```plain
<H3C> display mad                        # MAD 状态
<H3C> display mad verbose
```

**分裂恢复后**：故障修复、堆叠链路恢复，处于 Recovery 状态的设备需要**重启**才能重新加入 IRF。

> **关键提醒**：若 LACP/ARP/ND MAD 的中间设备本身也是 IRF 系统，**两者的 Domain ID 必须不同**。

---

## 6_5 M-LAG / DRNI（跨设备链路聚合）
### 6_5_1 原理
M-LAG（H3C 称 DRNI）把**两台独立设备**在逻辑上虚拟成一台，下游设备通过普通链路聚合分别与两台设备相连，实现：

+ **无阻塞转发**：两条链路都工作。
+ **控制平面独立**：两台设备可独立升级，业务几乎无感知。
+ **Peer-Link**：两台设备之间的同步链路，用于同步 MAC、ARP 与状态。

```plain
        [ SW-A ] ════ Peer-Link ════ [ SW-B ]
            ║                            ║
            ╚══════════╦═════════════════╝
                       ║  普通链路聚合（M-LAG 组）
                  [ 下游交换机 / 服务器 ]
```

### 6_5_2 配置要点
```plain
# SW-A
[SW-A] drni system-mac 0001-0001-0001          # 两端必须一致
[SW-A] drni system-number 1                    # 两端必须不同
[SW-A] drni system-priority 100                # 两端一致
[SW-A] drni keepalive ip destination 10.0.0.2 source 10.0.0.1    # Keepalive 链路

# Peer-Link（配置成聚合口）
[SW-A] interface Bridge-Aggregation 100
[SW-A-Bridge-Aggregation100] link-aggregation mode dynamic
[SW-A-Bridge-Aggregation100] port drni peer-link 1
[SW-A-Bridge-Aggregation100] quit

# M-LAG 成员口
[SW-A] interface Bridge-Aggregation 1
[SW-A-Bridge-Aggregation1] link-aggregation mode dynamic
[SW-A-Bridge-Aggregation1] drni group 1
[SW-A-Bridge-Aggregation1] quit
```

**验证**：

```plain
<SW-A> display drni                        # DRNI 系统状态
<SW-A> display drni summary
<SW-A> display drni keepalive              # Keepalive 状态
<SW-A> display drni drcp
```

### 6_5_3 IRF 与 M-LAG 决策表
| 决策因素 | 选 IRF | 选 M-LAG |
| --- | --- | --- |
| 需要简化管理（一台设备） | ✓ |  |
| 要求升级零中断 |  | ✓ |
| 园区网接入/汇聚 | ✓ |  |
| 数据中心核心 |  | ✓ |
| 团队运维能力一般 | ✓ |  |
| 已有两台高端核心 |  | ✓ |

---

## 6_6 VRRP（网关冗余）
### 6_6_1 原理
VRRP 把多台路由器/三层交换机组成一个**虚拟路由器**，对外提供一个虚拟 IP 作为网关。主机只配置虚拟 IP 作为网关，Master 故障时 Backup 接管。

### 6_6_2 配置
```plain
# 主设备（Master）
[H3C] interface Vlan-interface 10
[H3C-Vlan-interface10] ip address 192.168.10.2 24
[H3C-Vlan-interface10] vrrp vrid 10 virtual-ip 192.168.10.1
[H3C-Vlan-interface10] vrrp vrid 10 priority 120            # 优先级高者为主
[H3C-Vlan-interface10] vrrp vrid 10 preempt-mode timer delay 5    # 抢占延时
[H3C-Vlan-interface10] vrrp vrid 10 track 1 priority reduced 30   # 上行口追踪
[H3C-Vlan-interface10] quit

# 备设备（Backup）
[H3C-B] interface Vlan-interface 10
[H3C-B-Vlan-interface10] ip address 192.168.10.3 24
[H3C-B-Vlan-interface10] vrrp vrid 10 virtual-ip 192.168.10.1
[H3C-B-Vlan-interface10] vrrp vrid 10 priority 100          # 默认 100
```

**追踪上行口**（关键，避免"主设备上行断了但仍占着 Master"）：

```plain
[H3C] track 1 interface GigabitEthernet 1/0/24
```

**负载分担**（两个 VRRP 组互为主备）：

```plain
# SW-A：VRID 10 主，VRID 20 备
[SW-A-Vlan-interface10] vrrp vrid 10 priority 120
[SW-A-Vlan-interface20] vrrp vrid 20 priority 100

# SW-B：VRID 10 备，VRID 20 主
[SW-B-Vlan-interface10] vrrp vrid 10 priority 100
[SW-B-Vlan-interface20] vrrp vrid 20 priority 120
```

### 6_6_3 验证
```plain
<H3C> display vrrp                        # VRRP 概要
<H3C> display vrrp verbose                # 详细信息（含状态、优先级、追踪对象）
<H3C> display vrrp statistics             # 状态切换统计
```

**正常状态**：一台为 Master，另一台为 Backup；`display vrrp verbose` 中 Master 的虚拟 IP 与优先级符合规划。

---

## 6_7 BFD 与 NQA（快速故障检测）
### 6_7_1 BFD
BFD 提供**毫秒级**的链路故障检测，可与静态路由、OSPF、BGP、VRRP 联动。

```plain
# 静态路由 + BFD 联动（解决"对端死机但本端接口仍 UP"的问题）
[H3C] bfd session init-mode active
[H3C] track 1 bfd echo interface GigabitEthernet 1/0/1 remote ip 10.0.0.2 local ip 10.0.0.1
[H3C] ip route-static 0.0.0.0 0.0.0.0 10.0.0.2 track 1
```

**BFD 与路由协议联动**：

```plain
# OSPF
[H3C-GigabitEthernet1/0/1] ospf bfd enable

# BGP
[H3C-bgp-default] peer 10.0.0.2 bfd
```

**验证**：

```plain
<H3C> display bfd session
<H3C> display bfd session verbose
```

### 6_7_2 NQA
NQA（网络质量分析）可探测链路的时延、抖动、丢包，常用于**出口链路质量探测与选路**。

```plain
[H3C] nqa entry admin test
[H3C-nqa-admin-test] type icmp-echo
[H3C-nqa-admin-test-icmp-echo] destination ip 10.0.0.2
[H3C-nqa-admin-test-icmp-echo] frequency 5000
[H3C-nqa-admin-test-icmp-echo] reaction 1 checked-element probe-fail threshold-type consecutive 3 action-type trigger-only
[H3C-nqa-admin-test-icmp-echo] quit
[H3C] nqa schedule admin test start-time now lifetime forever
[H3C] track 2 nqa entry admin test reaction 1
```

**验证**：`display nqa result`、`display nqa statistics`。

### 📌 案例手记：主链路"假死"，浮动路由不切换
某企业两条出口专线，主链路走优先级 60 的静态路由，备链路 100。某次运营商光端机故障，主链路的**本端接口仍然是 UP**，路由不切换，业务中断半小时。

分析：**静态路由只能感知直连接口 down**，无法感知"对端设备死机但本端接口仍 UP"。

修复：增加 BFD 联动：

```plain
[H3C] track 1 bfd echo interface g1/0/1 remote ip 211.x.x.1 local ip 211.x.x.2
[H3C] ip route-static 0.0.0.0 0.0.0.0 211.x.x.1 track 1
[H3C] ip route-static 0.0.0.0 0.0.0.0 218.x.x.1 preference 100
```

**结论**：**任何"主备切换"类需求，都要问一句——故障能被本端感知吗？感知不到就必须用 BFD/NQA 联动。**

---

## 6_8 高可靠方案选型与验收清单
### 选型决策速查
| 需求 | 推荐方案 |
| --- | --- |
| 接入/汇聚上行带宽叠加 | 链路聚合（动态 LACP） |
| 园区网核心简化管理 + 冗余 | IRF（环形堆叠） + MAD |
| 数据中心核心零中断升级 | M-LAG / DRNI |
| 网关冗余（无堆叠场景） | VRRP + BFD 追踪 |
| 跨设备链路故障快速感知 | BFD 与路由/VRRP 联动 |
| 出口链路质量选路 | NQA + Track |

### 验收清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| 聚合组正常 | `display link-aggregation verbose` | 成员口状态为 S（Selected），非 I |
| 两端模式一致 | `display link-aggregation summary` | 同为 dynamic 或 static |
| IRF 建立成功 | `display irf` | 一主一备，成员编号唯一 |
| IRF 拓扑正确 | `display irf topology` | 与物理连线一致（环形/链形） |
| MAD 生效 | `display mad` | 状态正常；人为断开堆叠链路能触发 Recovery |
| DRNI 正常 | `display drni summary` | 两端角色正常，Peer-Link UP |
| VRRP 状态正确 | `display vrrp verbose` | 一主一备，虚拟 IP 一致，追踪对象正常 |
| BFD 会话 UP | `display bfd session` | State 为 Up |
| 切换时间达标 | 断开主链路计时 | 业务中断时间在预期范围内 |

### 实验笔记模板
```plain
## 实验：IRF 堆叠 + MAD + 链路聚合
日期：____   设备：____

### 1. 目标与验收
- [ ] 两台设备成功组建 IRF，一主一备
- [ ] 配置 BFD MAD 或 LACP MAD，人为断开堆叠链路验证分裂保护
- [ ] 下游交换机通过动态聚合双上行，带宽叠加

### 2. 关键参数记录
| 项目 | DeviceA | DeviceB |
| --- | --- | --- |
| 成员编号 | 1 | 2 |
| 优先级 | 32 | 1 |
| IRF 端口 | 1/2 | 2/1 |
| 物理端口 | Ten-Gig1/0/49-50 | Ten-Gig2/0/49-50 |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：堆叠起不来
- 假设：IRF-Port 接反 / 端口未 shutdown 就绑定 / 未 active / Domain ID 冲突
- 验证：display irf configuration + display irf link
- 结论：（记录实际原因）

### 4. 边界
- 改成员编号必须保存并重启
- irf-port-configuration active 不能漏
- MAD 中间设备 Domain ID 要区分
```

# 板块7 · IP 路由基础与 OSPF / IS-IS / BGP
> 本板块覆盖 H3CNE 的静态路由要求，以及 H3CSE-RS-RT（GB0-382）的主体内容：OSPF、IS-IS、BGP、路由控制、IPv6/SRv6。  
IE 阶段的核心不是"会配"，而是**"邻居起不来时能在 3 分钟内定位原因"**。

---

## 7_1 路由表与转发原理
### 7_1_1 路由表结构
```plain
<H3C> display ip routing-table

Destination/Mask     Proto    Pre   Cost    NextHop        Interface
0.0.0.0/0            Static   60    0       10.0.0.1       GE1/0/1
192.168.1.0/24       Direct   0     0       192.168.1.1    Vlan100
192.168.2.0/24       OSPF     10    2       10.1.1.2       GE1/0/2
```

| 字段 | 说明 |
| --- | --- |
| Destination/Mask | 目的网段 |
| Proto | 路由来源（Direct / Static / OSPF / IS-IS / BGP / RIP） |
| Pre（Preference） | 路由优先级，越小越优 |
| Cost | 路由度量，同协议内比较 |
| NextHop | 下一跳 |
| Interface | 出接口 |

### 7_1_2 路由优先级（必须背）
| 路由类型 | 默认优先级 |
| --- | --- |
| 直连（Direct） | 0 |
| OSPF 内部 | 10 |
| IS-IS | 15 |
| 静态（Static） | 60 |
| RIP | 100 |
| OSPF ASE / NSSA（外部） | 150 |
| IBGP | 255 |
| EBGP | 255 |

### 7_1_3 最长匹配原则
数据包转发时，选择**掩码最长（最精确）**的路由条目，而不是优先级最高的。  
例如同时存在 `192.168.0.0/16`（静态）与 `192.168.1.0/24`（OSPF），去往 192.168.1.10 的报文会走 **/24 的 OSPF 路由**。

> 优先级只在同一目的网段的不同来源之间比较；不同掩码之间先比掩码长度。

### 7_1_4 路由迭代（递归查找）
静态路由只指定下一跳 IP 时，设备需要再查一次路由表找到该下一跳的出接口，这个过程叫**路由迭代**。  
若下一跳不可达，该静态路由**不会出现在路由表中**——这是"配了静态路由但不生效"的常见原因。

---

## 7_2 静态路由
### 7_2_1 基本配置
```plain
# 指定下一跳（推荐，以太网环境）
[H3C] ip route-static 192.168.2.0 255.255.255.0 10.1.1.2
[H3C] ip route-static 192.168.2.0 24 10.1.1.2                 # 掩码简写

# 指定出接口（点对点链路如串口可用，以太网不推荐）
[H3C] ip route-static 192.168.2.0 24 GigabitEthernet 1/0/1

# 默认路由（出口网关，最常用）
[H3C] ip route-static 0.0.0.0 0.0.0.0 10.0.0.1

# 防火墙上添加到核心交换机的默认路由
[H3C] ip route-static 0.0.0.0 0.0.0.0 192.168.10.254
```

### 7_2_2 浮动静态路由（主备切换）
通过修改优先级实现主备：主链路走优先级 60 的静态路由，备链路配优先级 100（数值更大，主链路正常时不生效）。

```plain
[H3C] ip route-static 0.0.0.0 0.0.0.0 10.0.0.1                 # 主，优先级 60
[H3C] ip route-static 0.0.0.0 0.0.0.0 10.0.1.1 preference 100  # 备，优先级 100
```

**局限**：静态路由只能感知直连接口 down。如果主链路是对端设备死机而本端接口仍 UP，浮动路由不会切换——此时必须用 **BFD/NQA 联动**（见板块6 的 6_7）。

### 7_2_3 等价路由（负载分担）
```plain
[H3C] ip route-static 192.168.2.0 24 10.1.1.2
[H3C] ip route-static 192.168.2.0 24 10.1.2.2
```

两条同优先级静态路由同时生效，流量按流（默认）或按包分担。

### 7_2_4 黑洞路由（防环与聚合）
```plain
[H3C] ip route-static 10.0.0.0 255.255.0.0 NULL0
```

在做路由汇总时，必须配一条指向 NULL0 的黑洞路由，否则去往不存在子网的报文会在网络中来回转发（形成路由环路）。

### 7_2_5 查看
```plain
<H3C> display ip routing-table
<H3C> display ip routing-table 192.168.2.10             # 查看特定目的路由
<H3C> display ip routing-table protocol static
<H3C> display ip routing-table verbose
```

---

## 7_3 RIP（了解即可，NE 考点）
RIP 是基于距离矢量的协议，**跳数最大 15**，收敛慢，现网已基本淘汰，但考试仍考原理。

```plain
[H3C] rip 1
[H3C-rip-1] version 2
[H3C-rip-1] undo summary                                # 关闭自动汇总
[H3C-rip-1] network 192.168.1.0
[H3C-rip-1] quit

<H3C> display rip
<H3C> display rip 1 route
```

**防环机制**：水平分割、毒性逆转、触发更新、抑制计时器。  
**RIPv2** 支持 VLSM 与认证；**RIPv1** 是有类协议。

---

## 7_4 OSPF（GB0-382 核心）
### 7_4_1 基本原理
OSPF 是**链路状态协议**，用 SPF（Dijkstra）算法计算最短路径，以 **Cost = 100Mbps / 接口带宽**作为度量。

**三张表**：

+ 邻居表：`display ospf peer`
+ 链路状态数据库 LSDB：`display ospf lsdb`
+ 路由表：`display ip routing-table`

### 7_4_2 Router ID 与区域
```plain
[H3C] router id 1.1.1.1                                 # 建议手工指定（用 Loopback 地址）
[H3C] ospf 1 router-id 1.1.1.1
[H3C-ospf-1] area 0
[H3C-ospf-1-area-0.0.0.0] network 10.1.1.0 0.0.0.255
[H3C-ospf-1-area-0.0.0.0] network 192.168.1.0 0.0.0.255
[H3C-ospf-1-area-0.0.0.0] quit
```

**反掩码（wildcard mask）**：`0.0.0.255` 表示前 24 位精确匹配。反掩码写错（常写成正掩码）是 OSPF 最常见的配置错误。

**接口方式启用 OSPF（推荐，更精确）**：

```plain
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] ospf 1 area 0
```

### 7_4_3 邻居建立的七个状态
```plain
Down → Init → 2-Way → ExStart → Exchange → Loading → Full
```

| 状态 | 含义 |
| --- | --- |
| Down | 未收到任何 Hello |
| Init | 收到 Hello，但里面没有自己的 Router ID |
| 2-Way | 双方都看到对方的 Router ID（DR/BDR 在此选举） |
| ExStart | 协商主从关系与 DD 报文序列号 |
| Exchange | 交换 DD 报文（LSDB 摘要） |
| Loading | 请求缺失的 LSA（LSR/LSU/LSAck） |
| Full | LSDB 同步完成，邻接建立 |

### 7_4_4 邻居起不来的十大原因（排障清单，必背）
| 原因 | 检查命令 |
| --- | --- |
| 接口未 UP | `display interface brief` |
| Router ID 冲突 | `display ospf` / 日志 |
| 区域号不一致 | `display ospf interface` |
| 网络类型不匹配 | `display ospf interface`（Broadcast / P2P / NBMA / P2MP） |
| Hello / Dead 时间不一致 | `display ospf interface` |
| 认证类型或密码不一致 | `display ospf interface` |
| 掩码不一致（Broadcast 网络） | `display interface` |
| MTU 不一致（卡在 ExStart） | `display interface` |
| 区域类型不一致（Stub/NSSA） | `display ospf` |
| ACL 拦截 224.0.0.5 或协议号 89 | `display acl all` |

### 7_4_5 DR/BDR 选举
在 Broadcast / NBMA 网络中，需要选举 DR（指定路由器）与 BDR：

+ 比较**接口优先级**（默认 1，0 表示不参与）。
+ 优先级相同则比较 **Router ID**（大者优先）。
+ **DR 非抢占**：已经在位的 DR 不会被后来更高优先级的路由器顶替。

```plain
[H3C-GigabitEthernet1/0/1] ospf dr-priority 10
```

### 7_4_6 多区域与特殊区域
| 区域类型 | 允许的 LSA | 用途 |
| --- | --- | --- |
| 普通区域 | Type 1/2/3/4/5/7 | 默认 |
| Stub | 无 Type 5（用缺省路由代替） | 减少 LSDB 规模 |
| Totally Stub | 无 Type 3/4/5（仅缺省路由） | 进一步收敛 |
| NSSA | 允许引入外部路由（Type 7） | 需要引入外部路由又想做 Stub |
| Totally NSSA | 无 Type 3/4/5，允许 Type 7 | 两者结合 |

```plain
# Stub 区域（区域内所有路由器都要配）
[H3C-ospf-1-area-0.0.0.10] stub

# Totally Stub（只需在 ABR 上配）
[H3C-ospf-1-area-0.0.0.10] stub no-summary

# NSSA
[H3C-ospf-1-area-0.0.0.10] nssa
[H3C-ospf-1-area-0.0.0.10] nssa no-summary
```

### 7_4_7 路由引入与缺省路由下发
```plain
# 引入直连/静态
[H3C-ospf-1] import-route direct
[H3C-ospf-1] import-route static cost 100 type 2

# 下发缺省路由
[H3C-ospf-1] default-route-advertise                    # 本机有缺省路由才下发
[H3C-ospf-1] default-route-advertise always             # 无条件下发
```

### 7_4_8 常用验证命令
```plain
<H3C> display ospf peer                      # 邻居表（看状态是否 Full）
<H3C> display ospf peer brief
<H3C> display ospf lsdb                      # LSDB
<H3C> display ospf interface                 # 接口 OSPF 参数（Hello/Dead/网络类型/优先级）
<H3C> display ospf routing                   # OSPF 路由
<H3C> display ospf error                     # 错误统计（排障利器）
<H3C> display ospf brief
<H3C> display ospf abr-asbr                  # ABR / ASBR 信息
```

### 📌 案例手记：邻居卡在 ExStart，MTU 的锅
现场两台路由器通过专线互联，OSPF 邻居一直卡在 **ExStart**，反复协商不成功。

排查：

1. `display ospf peer` —— 状态在 ExStart ↔ Down 之间反复。
2. `display ospf error` —— 有 **MTU 相关错误计数**。
3. `display interface` —— 本端 MTU 1500，对端专线接口 MTU 被改成 4470（专线运营商要求）。
4. ExStart 阶段交换 DD 报文时会携带 MTU，两端不一致则无法进入 Exchange。

修复：统一两端 MTU（或开启 `ospf mtu-enable` 后保持一致），邻居立即 Full。

> **延伸**：MTU 问题在 **IPSec / GRE / VXLAN 隧道**上极为常见——封装后的报文变大，如果接口 MTU 不调整，会出现"能 ping 通小包、大包不通"的诡异现象。

---

## 7_5 IS-IS
### 7_5_1 基本原理
IS-IS 是**链路状态协议**，常用于运营商与大型园区骨干。

| 概念 | 说明 |
| --- | --- |
| NET 地址 | 如 `10.0000.0000.0001.00`，由 Area ID + System ID + SEL 组成 |
| Level-1 | 区域内路由（类似 OSPF 的普通区域） |
| Level-2 | 区域间路由（骨干） |
| Level-1-2 | 同时参与（类似 ABR） |
| DIS | 广播网络上选举的伪节点（类似 DR，但**可抢占**） |

### 7_5_2 配置
```plain
[H3C] isis 1
[H3C-isis-1] network-entity 10.0000.0000.0001.00
[H3C-isis-1] is-level level-2                          # 或 level-1 / level-1-2
[H3C-isis-1] cost-style wide                           # 使用宽度量（支持更大 cost 与 TE）
[H3C-isis-1] quit

[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] isis enable 1
[H3C-GigabitEthernet1/0/1] isis circuit-level level-2
[H3C-GigabitEthernet1/0/1] quit

# 接口下发布网段（Loopback 常用）
[H3C] interface LoopBack 0
[H3C-LoopBack0] isis enable 1
```

### 7_5_3 验证
```plain
<H3C> display isis peer
<H3C> display isis lsdb
<H3C> display isis route
<H3C> display isis interface
<H3C> display isis brief
```

### 7_5_4 IS-IS 与 OSPF 对比
| 对比项 | OSPF | IS-IS |
| --- | --- | --- |
| 封装 | IP 之上（协议号 89） | 二层之上（更贴近链路层） |
| 区域边界 | 在路由器上（接口属于区域） | 在链路上（路由器整体属于区域） |
| 扩展性 | 良好 | 更优（TLV 结构，易扩展） |
| 典型应用 | 企业网 | 运营商、大型骨干 |

---

## 7_6 BGP
### 7_6_1 基本原理
BGP 是**路径矢量协议**，用于自治系统（AS）之间，靠**丰富的属性**做策略控制，而非最短路径。

| 概念 | 说明 |
| --- | --- |
| EBGP | 不同 AS 之间，默认 TTL=1 |
| IBGP | 同一 AS 内部，默认 TTL=255 |
| 通告原则 | 只通告**最优且有效**的路由；从 IBGP 学到的不通告给 IBGP（需路由反射器或全互联） |
| 下一跳 | EBGP 通告时下一跳改变；IBGP 通告时下一跳默认不变（需 `next-hop-local`） |

### 7_6_2 配置
```plain
# EBGP
[H3C] bgp 65001
[H3C-bgp-default] router-id 1.1.1.1
[H3C-bgp-default] peer 10.1.1.2 as-number 65002
[H3C-bgp-default] address-family ipv4 unicast
[H3C-bgp-default-ipv4] network 192.168.1.0 24           # 必须是路由表中已存在的精确路由
[H3C-bgp-default-ipv4] peer 10.1.1.2 enable

# IBGP（用 Loopback 建邻 + next-hop-local）
[H3C-bgp-default] peer 2.2.2.2 as-number 65001
[H3C-bgp-default] peer 2.2.2.2 connect-interface LoopBack 0
[H3C-bgp-default-ipv4] peer 2.2.2.2 next-hop-local

# EBGP 多跳（用 Loopback 建 EBGP 邻居时）
[H3C-bgp-default] peer 3.3.3.3 ebgp-max-hop 2
```

### 7_6_3 BGP 状态机
```plain
Idle → Connect → Active → OpenSent → OpenConfirm → Established
```

**卡在 Idle/Active 的常见原因**：

| 原因 | 检查 |
| --- | --- |
| 对端不可达 | `ping` 对端地址 |
| 179 端口被 ACL 拦 | `display acl all` |
| AS 号配错 | `display bgp peer` |
| 未 `peer enable`（地址族下） | `display bgp peer` |
| 用 Loopback 建邻但未配 connect-interface | `display bgp peer` |
| EBGP 未配 ebgp-max-hop | `display bgp peer` |
| Router ID 冲突 | `display bgp peer` |

### 7_6_4 BGP 选路规则（13 条，记住前 8 条）
1. 优选 **Preferred-Value**（权重）最大的路由（H3C 私有，本地有效）。
2. 优选 **Local_Preference** 最大的路由。
3. 优选**本地生成**的路由（network > import > 聚合）。
4. 优选 **AS_PATH** 最短的路由。
5. 优选 **Origin** 类型最优的（IGP > EGP > Incomplete）。
6. 优选 **MED** 最小的路由。
7. 优选从 **EBGP** 学到的（EBGP > IBGP）。
8. 优选到 **下一跳 IGP 度量**最小的路由。
9. （后续：等价路由、Cluster_List 最短、Router ID 最小、对端地址最小等）

### 7_6_5 常用属性控制
```plain
# 用路由策略设置 Local_Preference
[H3C] route-policy SET-LP permit node 10
[H3C-route-policy-SET-LP-10] apply local-preference 200
[H3C-route-policy-SET-LP-10] quit
[H3C-bgp-default-ipv4] peer 10.1.1.2 route-policy SET-LP import

# 设置 MED
[H3C] route-policy SET-MED permit node 10
[H3C-route-policy-SET-MED-10] apply cost 100

# 设置 Preferred-Value
[H3C-bgp-default-ipv4] peer 10.1.1.2 preferred-value 100
```

### 7_6_6 验证
```plain
<H3C> display bgp peer                       # 邻居状态（Established 为正常）
<H3C> display bgp peer verbose
<H3C> display bgp routing-table              # BGP 路由表
<H3C> display bgp routing-table 192.168.1.0  # 查看某条路由的详细信息与属性
<H3C> display bgp routing-table community    # 按团体属性查看
```

---

## 7_7 路由策略与引入控制
### 7_7_1 工具箱
| 工具 | 作用 |
| --- | --- |
| ACL / 前缀列表 | **匹配**路由（抓取感兴趣路由） |
| route-policy | **匹配 + 修改**属性，可调用 if-match / apply |
| ip-prefix | 精确匹配路由前缀与掩码长度，比 ACL 更适合路由匹配 |
| filter-policy | **过滤**路由的发布与接收 |
| as-path-filter | 按 AS_PATH 过滤 BGP 路由 |
| community-filter | 按团体属性过滤 |

### 7_7_2 前缀列表（推荐用于路由匹配）
```plain
[H3C] ip prefix-list PL-1 index 10 permit 192.168.1.0 24
[H3C] ip prefix-list PL-1 index 20 permit 10.0.0.0 8 greater-equal 16 less-equal 24
```

### 7_7_3 route-policy 配置
```plain
[H3C] route-policy RP-OSPF-TO-BGP permit node 10
[H3C-route-policy-RP-OSPF-TO-BGP-10] if-match ip-prefix PL-1
[H3C-route-policy-RP-OSPF-TO-BGP-10] apply cost 100
[H3C-route-policy-RP-OSPF-TO-BGP-10] apply tag 100
[H3C-route-policy-RP-OSPF-TO-BGP-10] quit

# 在引入时调用
[H3C-bgp-default-ipv4] import-route ospf 1 route-policy RP-OSPF-TO-BGP
```

> **隐含规则**：route-policy 末尾有**隐含的 deny all**。若只想放行部分路由，需在末尾加一条空 permit 节点放行其余。

### 7_7_4 双向引入与环路防范
```plain
# 双点双向引入易产生环路，必须打 tag 防环
[H3C] route-policy DENY-TAG-100 deny node 10
[H3C-route-policy-DENY-TAG-100] if-match tag 100
[H3C-route-policy-DENY-TAG-100] quit

[H3C] route-policy SET-TAG-100 permit node 20
[H3C-route-policy-SET-TAG-100] apply tag 100
[H3C-route-policy-SET-TAG-100] quit

[H3C-ospf-1] import-route bgp route-policy DENY-TAG-100
[H3C-bgp-default-ipv4] import-route ospf 1 route-policy SET-TAG-100
```

### 📌 案例手记：一条 import-route 引发的"路由黑洞"
某企业 OSPF 与 BGP 双向引入，某天新增一台路由器后，部分网段突然不通。

排查：

1. `display ip routing-table` —— 发现去往某网段的下一跳指向了一台**没有回程路由**的设备。
2. 追查路由来源 —— 该路由是**从 BGP 引入到 OSPF，又被另一台设备重新引入回 BGP**，形成了次优路径。
3. 根因：双点双向引入**没有做 tag 防环**，也没有控制引入的路由范围。

修复：

+ 用前缀列表严格限制双向引入的网段。
+ 配置 tag 防环策略。
+ 在关键设备上配置黑洞路由 `ip route-static x.x.0.0 16 NULL0` 作为兜底。

**教训**：**路由引入是"高危操作"，必须限定范围 + 打 tag + 留黑洞路由兜底。**

---

## 7_8 IPv6 与 SRv6
### 7_8_1 IPv6 基础
```plain
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] ipv6 address 2001:db8:1::1/64
[H3C-GigabitEthernet1/0/1] quit

# IPv6 静态路由
[H3C] ipv6 route-static 2001:db8:2::/64 2001:db8:1::2

# 验证
<H3C> display ipv6 interface brief
<H3C> display ipv6 routing-table
<H3C> ping ipv6 2001:db8:1::2
```

### 7_8_2 OSPFv3
```plain
[H3C] ospfv3 1
[H3C-ospfv3-1] router-id 1.1.1.1
[H3C-ospfv3-1] quit

[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] ospfv3 1 area 0
```

### 7_8_3 IPv6 过渡技术
| 技术 | 用途 |
| --- | --- |
| 双栈 | 同时运行 IPv4/IPv6，最彻底 |
| 6to4 / ISATAP | 隧道过渡 |
| NAT64 | IPv6 网络访问 IPv4 资源 |

### 7_8_4 SRv6 概览（IE 拓展）
SRv6（Segment Routing over IPv6）基于源路由思想，用 **SRH（Segment Routing Header）** 携带路径信息，简化网络协议、支持可编程路径，是新一代承载网方向。

**学习建议**：IE 阶段了解原理与应用场景（业务链、灵活路径、TI-LFA 快速重路由）即可，重点仍在传统 IGP/BGP 的排障能力。

---

## 7_9 路由排障与验证清单
### 分层排查思路
```plain
第1步 接口 UP 吗？        display interface brief
第2步 IP 配了吗？         display ip interface brief
第3步 直连 ping 通吗？    ping 对端接口地址
第4步 邻居起来了吗？      display ospf peer / display bgp peer
第5步 路由在表里吗？      display ip routing-table
第6步 路由来源对吗？      display ip routing-table protocol ospf
第7步 有策略过滤吗？      display route-policy / display ip prefix-list
第8步 有 ACL 拦吗？       display acl all
```

### 验证清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| 静态路由生效 | `display ip routing-table` | 路由在表中，下一跳可达 |
| 浮动路由优先级正确 | `display ip routing-table verbose` | 主 60、备 100，主正常时备不出现 |
| OSPF 邻居 Full | `display ospf peer` | 状态 Full，DR/BDR 符合预期 |
| LSDB 同步 | `display ospf lsdb` | 两端 LSA 数量一致 |
| OSPF 路由正确 | `display ospf routing` | 目的网段与 Cost 符合规划 |
| 区域类型一致 | `display ospf` | Stub/NSSA 配置两端一致 |
| BGP 邻居 Established | `display bgp peer` | 状态为 Established |
| BGP 路由优选正确 | `display bgp routing-table x.x.x.x` | 最优路由标记 `>`，属性符合策略 |
| 引入范围受控 | `display ip routing-table protocol bgp` | 只看到规划内的引入路由 |
| 无路由环路 | `tracert` | 路径无重复跳 |

### 实验笔记模板
```plain
## 实验：OSPF 多区域 + BGP + 路由引入控制
日期：____   设备：____

### 1. 目标与验收
- [ ] OSPF 多区域邻居 Full，Stub 区域生效
- [ ] BGP 邻居 Established，路由优选符合策略
- [ ] 双向引入带 tag 防环，无次优路径

### 2. 规划表
| 设备 | Router ID | 区域 | 接口网段 |
| --- | --- | --- | --- |
| R1 | 1.1.1.1 | Area 0 | 10.1.1.0/30 |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：邻居卡在 ExStart
- 假设：MTU 不一致 / Router ID 冲突 / 网络类型不匹配
- 验证：display ospf error + display interface
- 结论：（记录实际原因）

### 4. 边界
- 反掩码不是正掩码
- route-policy 末尾隐含 deny all
- IBGP 需要 next-hop-local
- Stub 区域两端配置必须一致
```

# 板块8 · 园区网业务承载：DHCP、组播、QoS 与二层防护
> 本板块决定网络"跑得好不好"——能通只是及格线，**稳定、可控、可防私接**才是工程师水平。

---

## 8_1 DHCP 部署（服务器 / 中继 / 客户端）
### 8_1_1 三种角色
| 角色 | 说明 | 配置位置 |
| --- | --- | --- |
| DHCP 服务器 | 分配 IP、掩码、网关、DNS | 三层交换机 / 路由器 / 专用服务器 |
| DHCP 中继 | 转发跨网段的 DHCP 请求 | 三层交换机（汇聚 / 核心） |
| DHCP 客户端 | 交换机自身接口获取 IP | 设备接口视图 |

> **重要认知**：二层交换机不能提供 DHCP 服务，但可以提供 DHCP 中继 / 代理功能。三层交换机与路由器可以提供 DHCP 服务。

### ASCII 流程：DHCP 四步交互
```plain
  客户端                      服务器
    |  --- DHCP Discover (广播) -->  |
    |  <-- DHCP Offer    (单播/广播) |
    |  --- DHCP Request  (广播) -->  |
    |  <-- DHCP ACK      (单播/广播) |

  跨网段时：中继把广播转单播，并插入 giaddr（中继代理 IP）
  服务器根据 giaddr 判断该分配哪个地址池
```

### 8_1_2 交换机作为 DHCP 服务器（园区网主流）
```plain
[H3C] dhcp enable

# 排除不分配的静态地址（网关、服务器）
[H3C] dhcp server forbidden-ip 192.168.10.1
[H3C] dhcp server forbidden-ip 192.168.10.250 192.168.10.254

# 创建地址池
[H3C] dhcp server ip-pool VLAN10
[H3C-dhcp-pool-vlan10] network 192.168.10.0 mask 255.255.255.0
[H3C-dhcp-pool-vlan10] gateway-list 192.168.10.1
[H3C-dhcp-pool-vlan10] dns-list 223.5.5.5 114.114.114.114
[H3C-dhcp-pool-vlan10] expired day 1 hour 0 minute 0        # 租期
[H3C-dhcp-pool-vlan10] quit

# 为每个业务 VLAN 建一个地址池
[H3C] dhcp server ip-pool VLAN20
[H3C-dhcp-pool-vlan20] network 192.168.20.0 mask 255.255.255.0
[H3C-dhcp-pool-vlan20] gateway-list 192.168.20.1
[H3C-dhcp-pool-vlan20] dns-list 223.5.5.5
[H3C-dhcp-pool-vlan20] quit
```

### 8_1_3 静态绑定（打印机、服务器固定 IP）
```plain
[H3C] dhcp server ip-pool static-1
[H3C-dhcp-pool-static-1] static-bind ip-address 192.168.10.100 mask 255.255.255.0
[H3C-dhcp-pool-static-1] static-bind mac-address 00e0-fc23-f8d3
[H3C-dhcp-pool-static-1] gateway-list 192.168.10.1
[H3C-dhcp-pool-static-1] dns-list 223.5.5.5
[H3C-dhcp-pool-static-1] expired unlimited
[H3C-dhcp-pool-static-1] quit
```

> 绑定时 MAC 地址格式为 **xxxx-xxxx-xxxx**（H3C 格式）。

### 8_1_4 DHCP 中继（服务器在核心、终端在接入）
```plain
# 汇聚 / 接入交换机上配置中继
[H3C] dhcp enable
[H3C] interface Vlan-interface 10
[H3C-Vlan-interface10] dhcp select relay                  # 开启中继
[H3C-Vlan-interface10] dhcp relay server-address 10.0.0.5 # 指向 DHCP 服务器
[H3C-Vlan-interface10] quit

# 可选：中继地址池组（多台服务器冗余）
[H3C] dhcp relay server-group 1 ip 10.0.0.5
[H3C] dhcp relay server-group 1 ip 10.0.0.6
[H3C] interface Vlan-interface 10
[H3C-Vlan-interface10] dhcp relay server-select 1
```

**原理提示**：DHCP 请求是广播（目的 255.255.255.255），无法跨三层。中继把广播转成单播发给服务器，并在报文中插入 **giaddr**（中继代理 IP），服务器据此判断该分配哪个地址池。

### 8_1_5 交换机接口作为 DHCP 客户端
适用于管理地址需要动态获取的场景（如临时调试、小型网络）：

```plain
[H3C] interface Vlan-interface 20
[H3C-Vlan-interface20] ip address dhcp-alloc           # 通过 DHCP 获取 IP
[H3C-Vlan-interface20] undo ip address dhcp-alloc      # 取消
[H3C-Vlan-interface20] quit

[H3C] display dhcp                                     # 显示 DHCP 客户端信息
<H3C> debugging dhcp-alloc                             # 开启 DHCP 调试
<H3C> undo debugging dhcp-alloc
```

### 8_1_6 查看与排错
```plain
<H3C> display dhcp server ip-in-use                    # 已分配地址
<H3C> display dhcp server ip-in-use pool VLAN10
<H3C> display dhcp server conflict                     # 地址冲突
<H3C> display dhcp server statistics
<H3C> display dhcp relay                               # 中继信息
<H3C> reset dhcp server ip-in-use                      # 清空分配记录
```

| 故障 | 原因 | 处理 |
| --- | --- | --- |
| 全网拿不到地址 | 未 `dhcp enable` | 全局开启 |
| 跨网段拿不到 | 未配中继或中继指向错误 | 检查 `dhcp relay server-address` |
| 拿到 169.254.x.x | 服务器不可达，终端自动私有地址 | 查链路与中继 |
| 地址池耗尽 | 租期过长或终端过多 | 缩短租期、扩大地址池 |
| IP 冲突 | 存在私接 DHCP 服务器 | 开启 DHCP Snooping（见 8_2） |

---

## 8_2 DHCP Snooping（防私接 DHCP 服务器）
### 8_2_1 原理
私接家用路由器是最常见的网络故障源。DHCP Snooping 通过**端口信任机制**解决：

+ **信任端口（Trusted）**：只允许指定端口（上行口）发送 DHCP 服务器响应报文。
+ **非信任端口（Untrusted）**：丢弃来自该端口的 DHCP Offer/ACK，防止假冒服务器。

同时生成 **DHCP Snooping 绑定表**（IP + MAC + VLAN + 端口），供 IP Source Guard、ARP 检测使用。

### 8_2_2 配置
```plain
[H3C] dhcp snooping enable                             # 全局开启

# 上行口（连合法 DHCP 服务器方向）设为信任
[H3C] interface GigabitEthernet 1/0/48
[H3C-GigabitEthernet1/0/48] dhcp snooping trust
[H3C-GigabitEthernet1/0/48] quit

# 接入端口记录绑定表项
[H3C] interface range GigabitEthernet 1/0/1 to GigabitEthernet 1/0/24
[H3C-if-range] dhcp snooping binding record            # 配合 IPSG 使用
[H3C-if-range] quit

# 在 VLAN 视图下开启
[H3C] vlan 10
[H3C-vlan10] dhcp snooping enable
[H3C-vlan10] quit
```

### 8_2_3 防 DHCP 饿死攻击（限速）
```plain
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] dhcp snooping rate-limit 10      # 每秒最多 10 个 DHCP 报文
```

### 8_2_4 查看
```plain
<H3C> display dhcp snooping
<H3C> display dhcp snooping binding                    # 绑定表（IP+MAC+VLAN+端口）
<H3C> display dhcp snooping trust
```

### 📌 案例手记：一台家用路由器搅乱整层楼
某办公室员工自带无线路由器，把 LAN 口接到了墙上网口（WAN 口空着）。

结果：第二天整个楼层的终端陆续拿到 `192.168.1.x` 的地址（家用路由器网段），网关指向了那台路由器，全部上不了网。

排查：

1. 在交换机上 `display dhcp server ip-in-use` —— 没看到异常（因为终端根本没从合法服务器拿地址）。
2. 在终端上 `ipconfig /all` —— 发现 DHCP 服务器地址是 `192.168.1.1`。
3. `display mac-address` 顺着这个 MAC 找到物理端口 → 定位到具体工位。

修复与防范：

1. 拔掉私接路由器。
2. 全网开启 DHCP Snooping：上行口 trust，接入端口全部 untrusted。
3. 开启 IP Source Guard（见 8_5）防止终端私设静态 IP。

**沉淀**：**DHCP Snooping 是园区网接入层的标配，开启成本极低，收益极高。**

---

## 8_3 IP 组播
### 8_3_1 组播基础
| 概念 | 说明 |
| --- | --- |
| 组播地址 | IPv4 D 类：224.0.0.0 ~ 239.255.255.255 |
| 组播 MAC | 01-00-5E-xx-xx-xx（IPv4 组播地址**低 23 位**映射到 MAC 低 23 位） |
| 常用保留地址 | 224.0.0.1（所有主机）、224.0.0.2（所有路由器）、224.0.0.5（OSPF）、224.0.0.18（VRRP） |
| RPF | 反向路径转发，组播防环的核心机制 |

**应用场景**：视频监控、IPTV、视频会议、金融行情推送。

### 8_3_2 IGMP Snooping（二层组播，园区网必配）
**作用**：让二层交换机只把组播流量转发给"真正需要"的端口，而不是全网泛洪。

```plain
[H3C] igmp-snooping enable                             # 全局开启
[H3C] vlan 10
[H3C-vlan10] igmp-snooping enable
[H3C-vlan10] igmp-snooping version 3                   # 建议配 v3，支持 SSM
[H3C-vlan10] igmp-snooping querier                     # 无三层组播路由器时开启查询器
[H3C-vlan10] quit

# 静态组播成员端口（组播源 / 接收端固定时）
[H3C] interface GigabitEthernet 1/0/5
[H3C-GigabitEthernet1/0/5] igmp-snooping static-group 239.1.1.1
```

**查看**：

```plain
<H3C> display igmp-snooping
<H3C> display igmp-snooping group
<H3C> display igmp-snooping group vlan 10
```

### 8_3_3 三层组播（PIM）
| 模式 | 适用场景 |
| --- | --- |
| PIM-DM（密集模式） | 组成员密集，先泛洪后剪枝 |
| PIM-SM（稀疏模式） | 组成员分散，**主流**，需 RP（汇聚点） |

```plain
[H3C] multicast routing-enable
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] pim sm
[H3C-GigabitEthernet1/0/1] quit
[H3C] interface Vlan-interface 10
[H3C-Vlan-interface10] pim sm
[H3C-Vlan-interface10] igmp enable                     # 接收者侧开启 IGMP

# 配置 RP（静态方式）
[H3C] pim
[H3C-pim] static-rp 1.1.1.1
```

**验证**：`display pim neighbor`、`display pim routing-table`、`display igmp group`。

### ASCII 示意：IGMP Snooping 的作用
```plain
   未开启 Snooping：                   开启 Snooping 后：
   组播源 → 交换机 → 泛洪到所有口       组播源 → 交换机 → 只发给
            ↓↓↓↓↓↓↓↓                              ├─ 接收者1（加入组）
          所有 24 个口                              └─ 接收者2（加入组）
                                                  （其余 22 口不收）
```

---

## 8_4 QoS 与 MQC
### 8_4_1 QoS 三种服务模型
| 模型 | 说明 | 适用场景 |
| --- | --- | --- |
| Best-Effort | 尽力而为，无保障 | 默认 |
| IntServ | 预留资源（RSVP） | 规模小、要求高 |
| DiffServ | **差分服务，按优先级处理（主流）** | 园区网、运营商 |

### 8_4_2 MQC 三要素（配置套路固定）
```plain
流分类（traffic classifier）：定义"什么是重要流量"
流行为（traffic behavior）  ：定义"重要流量怎么对待"
流策略（traffic policy）    ：把分类与行为绑定，并应用到接口
```

### 8_4_3 配置示例：保障语音与视频会议
```plain
# 1. 流分类
[H3C] traffic classifier VOIP
[H3C-classifier-VOIP] if-match dscp ef                      # EF 为语音
[H3C-classifier-VOIP] quit

[H3C] traffic classifier VIDEO
[H3C-classifier-VIDEO] if-match dscp af41
[H3C-classifier-VIDEO] quit

# 2. 流行为
[H3C] traffic behavior VOIP
[H3C-behavior-VOIP] queue llq bandwidth pct 10              # 低时延队列，保证 10%
[H3C-behavior-VOIP] quit

[H3C] traffic behavior VIDEO
[H3C-behavior-VIDEO] queue af bandwidth pct 20              # 保证转发 20%
[H3C-behavior-VIDEO] quit

# 3. 流策略
[H3C] traffic policy QOS-POLICY
[H3C-trafficpolicy-QOS-POLICY] classifier VOIP behavior VOIP
[H3C-trafficpolicy-QOS-POLICY] classifier VIDEO behavior VIDEO
[H3C-trafficpolicy-QOS-POLICY] quit

# 4. 应用到接口（出方向）
[H3C] interface GigabitEthernet 1/0/24
[H3C-GigabitEthernet1/0/24] traffic-policy QOS-POLICY outbound
```

### 8_4_4 信任与标记
```plain
# 信任端口的 DSCP / 802.1p
[H3C-GigabitEthernet1/0/1] qos trust dscp
[H3C-GigabitEthernet1/0/1] qos trust dot1p

# 不信任时，重新标记
[H3C] traffic behavior REMARK
[H3C-behavior-REMARK] remark dscp ef
```

### 8_4_5 限速与流量监管
```plain
# 端口限速（出方向 10M）
[H3C-GigabitEthernet1/0/1] qos lr outbound cir 10000

# 流量监管（CAR）
[H3C] traffic behavior POLICE
[H3C-behavior-POLICE] car cir 2000 cbs 200000 ebs 0 green pass red discard
```

### 8_4_6 验证
```plain
<H3C> display traffic classifier user-defined
<H3C> display traffic behavior user-defined
<H3C> display traffic policy user-defined
<H3C> display qos policy interface g1/0/24              # 看命中统计
<H3C> display qos queue-statistics interface g1/0/24 outbound
```

---

## 8_5 二层防护（接入层纵深防御）
### 8_5_1 端口隔离
```plain
[H3C] port-isolate group 1
[H3C] interface range g1/0/1 to g1/0/24
[H3C-if-range] port-isolate enable group 1
```

### 8_5_2 IP Source Guard（防私设 IP）
基于 DHCP Snooping 绑定表，只允许报文的源 IP 与绑定表一致。

```plain
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] ip verify source ip-address mac-address
```

或 VLAN 视图下批量：

```plain
[H3C] vlan 10
[H3C-vlan10] ip verify source ip-address mac-address
```

**验证**：`display ip source binding`、`display dhcp snooping binding`。

### 8_5_3 动态 ARP 检测（DAI，防 ARP 欺骗）
```plain
[H3C] vlan 10
[H3C-vlan10] arp detection enable
[H3C-vlan10] quit

# 上行口设为 ARP 信任
[H3C] interface GigabitEthernet 1/0/48
[H3C-GigabitEthernet1/0/48] arp detection trust
```

### 8_5_4 MAC 地址数限制
```plain
[H3C-GigabitEthernet1/0/1] mac-address max-mac-count 2
[H3C-GigabitEthernet1/0/1] mac-address max-mac-count 2 action discard
```

### 8_5_5 风暴抑制（已在板块3 出现，此处补全策略视角）
```plain
[H3C-GigabitEthernet1/0/1] broadcast-suppression pps 100
[H3C-GigabitEthernet1/0/1] multicast-suppression 20
[H3C-GigabitEthernet1/0/1] unicast-suppression 20
```

### 二层防护能力对照表
| 威胁 | 防护技术 |
| --- | --- |
| 私接 DHCP 服务器 | DHCP Snooping（上行口 trust） |
| 私设静态 IP | IP Source Guard |
| ARP 欺骗 / 中间人 | 动态 ARP 检测（DAI） |
| 私接 Hub 导致多 MAC | 端口安全 / MAC 数限制 |
| 广播风暴 | 风暴抑制 + STP |
| 横向扫描 | 端口隔离 |
| DHCP 饿死攻击 | DHCP Snooping rate-limit |
| 环路 | STP + BPDU 保护 + 环路检测 |

### 📌 案例手记：ARP 欺骗导致的"时断时续"
现象：某部门每隔十几分钟就断网一次，几十秒后自动恢复，ARP 表里网关的 MAC 会变化。

排查：

1. `display arp` —— 发现网关 192.168.10.1 对应的 MAC 有时是真实的网关 MAC，有时是另一台 PC 的 MAC。
2. 定位到某台中毒终端在发 **ARP 欺骗报文**，冒充网关。
3. 拔掉该终端后恢复。

根治：

+ 开启 DHCP Snooping + DAI（动态 ARP 检测）。
+ 对网关做静态 ARP 绑定（关键服务器）。
+ 终端侧部署杀毒与准入。

**结论**：**二层防护不是"可选功能"，而是园区网接入层的必配基线。**

---

## 8_6 实验笔记模板与验收清单
### 笔记模板
```plain
## 实验：DHCP + Snooping + QoS 全套部署
日期：____   设备：____

### 1. 目标与验收
- [ ] 每 VLAN 一个地址池，终端能正常拿到地址
- [ ] 私接路由器无法分配地址（Snooping 生效）
- [ ] IPSG 生效：私设静态 IP 的终端不通
- [ ] QoS 策略命中，语音队列有流量

### 2. 地址池规划
| VLAN | 网段 | 网关 | 排除地址 | 租期 |
| --- | --- | --- | --- | --- |
| 10 | 192.168.10.0/24 | .1 | .1, .250-.254 | 1 天 |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：跨网段拿不到地址
- 假设：未开 dhcp enable / 中继地址错 / Snooping 把响应丢了
- 验证：display dhcp relay + display dhcp snooping trust
- 结论：（记录实际原因）

### 4. 边界
- Snooping 必须把上行口设为 trust，否则全部拿不到地址
- IPSG 依赖 Snooping 绑定表，静态 IP 终端需单独绑定
- QoS 策略应用方向：靠近源做标记，靠近拥塞点做调度
```

### 验收清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| DHCP 服务正常 | `display dhcp server ip-in-use` | 终端拿到正确网段地址 |
| 排除地址生效 | `display dhcp server forbidden-ip` | 网关与服务器地址未被分配 |
| 中继正常 | `display dhcp relay` | 中继指向正确服务器 |
| Snooping 生效 | `display dhcp snooping binding` | 绑定表有记录；私接服务器被拦 |
| IPSG 生效 | 私设 IP 测试 | 不符合绑定表的终端不通 |
| 组播可控 | `display igmp-snooping group` | 组播只发给成员端口 |
| QoS 命中 | `display qos policy interface` | 分类有匹配计数 |
| 端口隔离生效 | 同 VLAN 互 ping | 不通，但都能通网关 |

# 板块9 · 广域网接入、ACL、NAT 与 VPN 技术
> 本板块覆盖 H3CNE 的 ACL / NAT 要求与 H3CSE-RS-NSO（GB0-392）的主体内容：宽带接入、VPN、QoS、VXLAN/EVPN。

---

## 9_1 广域网接入技术
### 9_1_1 PPP 与 PPPoE
PPP（Point-to-Point Protocol）是串行链路上的二层协议，支持认证（PAP/CHAP）、协商 IP、链路质量检测。

```plain
# 串口 PPP 基本配置
[H3C] interface Serial 1/0
[H3C-Serial1/0] link-protocol ppp
[H3C-Serial1/0] ip address 10.1.1.1 30
[H3C-Serial1/0] quit

# 通过协商获取 IP（客户端侧）
[H3C-Serial1/0] ip address ppp-negotiate

# CHAP 认证（服务端）
[H3C] local-user usera class network
[H3C-luser-network-usera] password simple Pass@123
[H3C-luser-network-usera] service-type ppp
[H3C-luser-network-usera] quit
[H3C] interface Serial 1/0
[H3C-Serial1/0] ppp authentication-mode chap

# 客户端
[H3C-Serial1/0] ppp chap user usera
[H3C-Serial1/0] ppp chap password simple Pass@123
```

**PPPoE（PPP over Ethernet）** 是家庭宽带与企业拨号上网的标准：

```plain
[H3C] dialer-group 1 rule ip permit
[H3C] interface Dialer 1
[H3C-Dialer1] link-protocol ppp
[H3C-Dialer1] ppp chap user 057188880000
[H3C-Dialer1] ppp chap password simple 123456
[H3C-Dialer1] ip address ppp-negotiate
[H3C-Dialer1] dialer bundle 1
[H3C-Dialer1] dialer-group 1
[H3C-Dialer1] quit

[H3C] interface GigabitEthernet 0/0
[H3C-GigabitEthernet0/0] pppoe-client dial-bundle-number 1
[H3C-GigabitEthernet0/0] quit

[H3C] ip route-static 0.0.0.0 0.0.0.0 Dialer 1

<H3C> display pppoe-client session summary
```

### 9_1_2 常见宽带接入对比
| 技术 | 介质 | 典型带宽 | 场景 |
| --- | --- | --- | --- |
| PPPoE | 以太网 / 光纤 | 100M ~ 1G | 家庭宽带、企业拨号 |
| 专线（MSTP / OTN） | 光纤 | 2M ~ 10G | 企业总部互联 |
| SD-WAN | 任意叠加 | 灵活 | 多分支组网（H3CSE-SDN 方向） |

### 9_1_3 MTU 与 MSS 调整（出口必配）
隧道或 PPPoE 封装会占用额外字节，导致大包不通：

```plain
[H3C] interface GigabitEthernet 0/1
[H3C-GigabitEthernet0/1] tcp mss 1452            # PPPoE 场景常用 1452
[H3C-GigabitEthernet0/1] mtu 1492
```

> **典型症状**：能 ping 通能开部分网站，但某些网页或应用打不开——大概率是 MTU/MSS 问题。

---

## 9_2 ACL（访问控制列表）
### 9_2_1 ACL 类型
| 类型 | 编号范围 | 匹配能力 |
| --- | --- | --- |
| 基本 ACL | 2000 ~ 2999 | 仅源 IP |
| 高级 ACL | 3000 ~ 3999 | 源 / 目的 IP、协议、端口号 |
| 二层 ACL | 4000 ~ 4999 | 源 / 目的 MAC、VLAN、802.1p |
| 用户自定义 ACL | 5000 ~ 5999 | 报文偏移量匹配 |

### 9_2_2 通配符掩码（wildcard mask）
与子网掩码相反：**0 表示必须精确匹配，1 表示不关心**。

| 需求 | 通配符 |
| --- | --- |
| 匹配单台主机 192.168.1.10 | `0`（即 0.0.0.0） |
| 匹配 192.168.1.0/24 | `0.0.0.255` |
| 匹配 192.168.0.0/16 | `0.0.255.255` |
| 匹配所有 | `255.255.255.255` |
| 匹配 192.168.1.0/24 中的**奇数**地址 | `0.0.0.254` |
| 匹配 192.168.1.0/24 中的**偶数**地址 | `0.0.0.254`（配合基地址 192.168.1.0） |

### 9_2_3 基本 ACL 配置（控制管理访问）
```plain
# 仅允许运维网段管理设备
[H3C] acl basic 2000
[H3C-acl-ipv4-basic-2000] rule 5 permit source 192.168.100.0 0.0.0.255
[H3C-acl-ipv4-basic-2000] rule 10 deny source any
[H3C-acl-ipv4-basic-2000] quit

# 在 VTY 调用
[H3C] user-interface vty 0 4
[H3C-ui-vty0-4] acl 2000 inbound
```

### 9_2_4 高级 ACL 配置（控制业务流量）
```plain
# 禁止视频监控网段访问办公网
[H3C] acl advanced 3000
[H3C-acl-ipv4-adv-3000] rule 5 deny ip source 10.10.10.0 0.0.0.255 destination 192.168.30.0 0.0.0.255
[H3C-acl-ipv4-adv-3000] rule 10 permit ip
[H3C-acl-ipv4-adv-3000] quit

# 在 VLAN 接口调用（拦截业务流量）
[H3C] interface Vlan-interface 10
[H3C-Vlan-interface10] packet-filter 3000 outbound
[H3C-Vlan-interface10] quit

# 仅允许堡垒机访问 SSH 端口
[H3C] acl advanced 3001
[H3C-acl-ipv4-adv-3001] description Restrict_SSH_Access
[H3C-acl-ipv4-adv-3001] rule 5 permit tcp source 192.168.100.200 0 destination-port eq 22
[H3C-acl-ipv4-adv-3001] rule 10 deny tcp destination-port eq 22
[H3C-acl-ipv4-adv-3001] rule 15 permit ip
[H3C-acl-ipv4-adv-3001] quit
```

### 9_2_5 ACL 调用方式与方向
| 调用位置 | 命令 | 方向说明 |
| --- | --- | --- |
| 接口 | `packet-filter 3000 inbound/outbound` | inbound = 进入接口，outbound = 离开接口 |
| VTY 线路 | `acl 2000 inbound` | 限制登录源 |
| NAT | `nat outbound 3000` | 匹配需要转换的流量 |
| QoS | `if-match acl 3000` | 流分类 |
| 路由策略 | `if-match acl 2000` | 匹配路由 |

**方向判断口诀**：**以设备为中心**——从外部进入设备接口为 inbound，从设备接口发出为 outbound。

### 9_2_6 查看与排错
```plain
<H3C> display acl all
<H3C> display acl 3000
<H3C> display packet-filter interface g1/0/1
<H3C> display packet-filter statistics interface g1/0/1 inbound     # 看命中次数
```

> **重要**：H3C ACL **默认规则为允许**（未被任何 rule 匹配的报文默认放行）。因此"只允许某网段"必须**显式写 **`rule deny`。  
ACL 按 rule 编号**从小到大匹配，命中即停止**；无编号时按配置顺序自动分配 5 的步长（0、5、10、15 依次递增）。

### 📌 案例手记：一条 ACL 放倒整栋楼
**背景**：某公司要求"只有办公网段 `192.168.10.0/24` 能访问服务器网段 `192.168.100.0/24`，其余网段一律禁止"。

工程师在核心交换机上写了 ACL，并挂在了**连接出口路由器的上行口出方向**：

```plain
[H3C] acl advanced 3000
[H3C-acl-ipv4-adv-3000] rule 5 permit ip source 192.168.10.0 0.0.0.255 destination 192.168.100.0 0.0.0.255
[H3C-acl-ipv4-adv-3000] rule 10 deny ip
[H3C-acl-ipv4-adv-3000] quit
[H3C] interface GigabitEthernet 1/0/48
[H3C-GigabitEthernet1/0/48] packet-filter 3000 outbound
```

**结果**：ACL 一挂上去，整栋楼断网。不只是访问服务器断了，上网、打印、视频会议全部中断。

**根因拆解**（三个错误叠在一起）：

1. **兜底 deny 的作用范围被放大**。`rule 10 deny ip` 没有限定 `destination`，它拒绝的是**所有未被 rule 5 匹配的流量**——包括去往互联网的流量。这条规则一旦挂在流量必经之路上，等于把出口直接堵死。
2. **挂载位置选错**。控制"谁可以访问服务器"，应该在**服务器网段网关接口的 inbound 方向**做；挂在出口上行口，影响面从"访问服务器"被放大成"全部出向流量"。
3. **没有留 permit 兜底**。写 deny 之前没先想清楚"哪些流量必须放行"。

**正确做法**：先收紧规则的匹配范围，再挂到正确的位置与方向。

```plain
# 1. 限定作用范围：只对"去往服务器网段"的流量做控制，其余一律放行
[H3C] acl advanced 3000
[H3C-acl-ipv4-adv-3000] rule 5 permit ip source 192.168.10.0 0.0.0.255 destination 192.168.100.0 0.0.0.255
[H3C-acl-ipv4-adv-3000] rule 10 deny ip destination 192.168.100.0 0.0.0.255
[H3C-acl-ipv4-adv-3000] rule 1000 permit ip
[H3C-acl-ipv4-adv-3000] quit

# 2. 挂在服务器网段网关接口的入方向
[H3C] interface Vlan-interface 100
[H3C-Vlan-interface100] packet-filter 3000 inbound
```

**上线前的三道保险**：

1. **先宽后严**：首次上线一律先写 `rule 1000 permit ip` 兜底，观察一至两天业务正常后再考虑收紧。
2. **看命中计数**：

```plain
<H3C> display packet-filter statistics interface Vlan-interface 100 inbound
```

**命中数为 0 的 rule，说明你的方向或挂载位置判断有误**——这是最容易被忽略、也最有效的自检手段。

3. **留回退窗口**：远程操作前先设定定时重启或配置回滚，避免把自己锁在门外。

**教训**：**ACL 是"枪"，位置、方向、兜底三者任一出错都会打自己。** 写 deny 之前先问自己三个问题——这条规则影响的流量范围有多大？挂在哪里影响面最小？哪些流量必须放行？

---

## 9_3 NAT（地址转换）
### 9_3_1 三种 NAT 类型
| 类型 | 特点 | 应用 |
| --- | --- | --- |
| Easy IP（PAT） | 多对一，出接口 IP 做转换，复用端口 | 企业上网（最常用） |
| NAPT | 多对多，用地址池 | 有一定公网地址时 |
| NAT Server | 静态映射，外网访问内网服务器 | 发布 Web / 邮件服务 |

### 9_3_2 Easy IP（出向 NAT）
```plain
# 1. 用 ACL 匹配需要转换的内网流量
[H3C] acl basic 2000
[H3C-acl-ipv4-basic-2000] rule 5 permit source 192.168.0.0 0.0.255.255
[H3C-acl-ipv4-basic-2000] quit

# 2. 在出接口上配置 Easy IP
[H3C] interface GigabitEthernet 0/1
[H3C-GigabitEthernet0/1] nat outbound 2000

# 3. 默认路由指向运营商
[H3C] ip route-static 0.0.0.0 0.0.0.0 211.x.x.1
```

### 9_3_3 NAPT（地址池）
```plain
[H3C] nat address-group 1
[H3C-address-group-1] address 211.x.x.10 211.x.x.20
[H3C-address-group-1] quit

[H3C] interface GigabitEthernet 0/1
[H3C-GigabitEthernet0/1] nat outbound 2000 address-group 1
```

### 9_3_4 NAT Server（发布内网服务器）
```plain
# 把公网 211.x.x.100 的 80 端口映射到内网 192.168.100.10 的 80 端口
[H3C] interface GigabitEthernet 0/1
[H3C-GigabitEthernet0/1] nat server protocol tcp global 211.x.x.100 80 inside 192.168.100.10 80

# 端口映射（外网 8080 → 内网 80）
[H3C-GigabitEthernet0/1] nat server protocol tcp global 211.x.x.100 8080 inside 192.168.100.10 80
```

### 9_3_5 NAT ALG 与常见问题
| 问题 | 原因 | 处理 |
| --- | --- | --- |
| FTP 能连但传不了数据 | FTP 是多通道协议 | 开启 NAT ALG：`nat alg ftp` |
| 部分应用异常 | 应用层携带 IP 信息 | 开启对应 ALG（dns / h323 / sip 等） |
| 内网无法用公网 IP 访问内网服务器 | NAT 回流（Hairpin）问题 | 配置 `nat hairpin enable` 或内网 DNS 用内网地址 |
| NAT 会话占满 | 连接数过多或超时过长 | 调小会话老化时间、限制单主机连接数 |

```plain
[H3C] nat alg ftp
[H3C] nat alg dns
[H3C] interface GigabitEthernet 0/1
[H3C-GigabitEthernet0/1] nat hairpin enable
```

### 9_3_6 验证
```plain
<H3C> display nat session                      # 当前 NAT 会话
<H3C> display nat session verbose
<H3C> display nat outbound                     # 出向 NAT 配置
<H3C> display nat server                       # NAT Server 配置
<H3C> display nat statistics                   # 统计
<H3C> reset nat session                        # 清空会话（谨慎）
```

---

## 9_4 VPN 技术（GRE / IPSec / L2TP）
### 9_4_1 GRE（通用路由封装）
**特点**：简单、无加密，用于在隧道中运行路由协议或承载组播。

```plain
# 隧道源端
[H3C] interface Tunnel 0 mode gre
[H3C-Tunnel0] source 211.x.x.1
[H3C-Tunnel0] destination 211.x.x.2
[H3C-Tunnel0] ip address 10.255.1.1 30
[H3C-Tunnel0] quit

# 隧道上运行路由协议
[H3C] ospf 1
[H3C-ospf-1] area 0
[H3C-ospf-1-area-0.0.0.0] network 10.255.1.0 0.0.0.3
```

**验证**：`display interface Tunnel 0`、`display tunnel-info`。

> **注意**：GRE 无加密，敏感业务必须叠加 IPSec。

### 9_4_2 IPSec（加密隧道，主流）
**核心组件**：

| 组件 | 作用 |
| --- | --- |
| 安全提议（transform-set） | 定义加密算法、认证算法、封装模式 |
| IKE 提议 | 定义密钥交换参数 |
| IKE 对等体（keychain / profile） | 定义对端地址与预共享密钥 |
| 安全策略 | 绑定以上组件，定义感兴趣流 |
| 感兴趣流（ACL） | 定义哪些流量需要走 IPSec |

**配置示例（策略方式）**：

```plain
# 1. 定义感兴趣流（注意：两端 ACL 要镜像对称）
[H3C] acl advanced 3100
[H3C-acl-ipv4-adv-3100] rule 5 permit ip source 192.168.1.0 0.0.0.255 destination 192.168.2.0 0.0.0.255
[H3C-acl-ipv4-adv-3100] quit

# 2. 安全提议
[H3C] ipsec transform-set TS1
[H3C-ipsec-transform-set-TS1] esp encryption-algorithm aes-cbc-256
[H3C-ipsec-transform-set-TS1] esp authentication-algorithm sha256
[H3C-ipsec-transform-set-TS1] encapsulation-mode tunnel
[H3C-ipsec-transform-set-TS1] quit

# 3. IKE 提议与对等体
[H3C] ike proposal 10
[H3C-ike-proposal-10] encryption-algorithm aes-cbc-256
[H3C-ike-proposal-10] authentication-algorithm sha256
[H3C-ike-proposal-10] quit

[H3C] ike keychain KC1
[H3C-ike-keychain-KC1] pre-shared-key address 211.x.x.2 key simple H3C@IPSec123
[H3C-ike-keychain-KC1] quit

[H3C] ike profile PF1
[H3C-ike-profile-PF1] keychain KC1
[H3C-ike-profile-PF1] local-identity address 211.x.x.1
[H3C-ike-profile-PF1] match remote identity address 211.x.x.2
[H3C-ike-profile-PF1] proposal 10
[H3C-ike-profile-PF1] quit

# 4. 安全策略
[H3C] ipsec policy POLICY1 10 isakmp
[H3C-ipsec-policy-isakmp-POLICY1-10] security acl 3100
[H3C-ipsec-policy-isakmp-POLICY1-10] transform-set TS1
[H3C-ipsec-policy-isakmp-POLICY1-10] remote-address 211.x.x.2
[H3C-ipsec-policy-isakmp-POLICY1-10] ike-profile PF1
[H3C-ipsec-policy-isakmp-POLICY1-10] quit

# 5. 应用到出接口
[H3C] interface GigabitEthernet 0/1
[H3C-GigabitEthernet0/1] ipsec apply policy POLICY1
```

**IPSec 排障命令**：

```plain
<H3C> display ike sa
<H3C> display ipsec sa
<H3C> display ipsec sa brief
<H3C> display ipsec statistics
<H3C> debugging ike error
```

**IPSec 协商不起来的常见原因**：

| 原因 | 检查 |
| --- | --- |
| 两端 ACL 不对称 | `display acl 3100` 对比 |
| 预共享密钥不一致 | `display ike keychain` |
| 加密/认证算法不匹配 | `display ipsec transform-set` |
| 感兴趣流未触发 | 先 `ping -a` 触发流量 |
| NAT 穿越问题 | 配置 `nat traversal`（两端） |
| 路由不通 | `ping` 对端公网地址 |

### 9_4_3 L2TP（远程拨号 VPN）
常用于移动办公用户拨入企业内网。

```plain
# LNS 侧（企业端）
[H3C] l2tp enable
[H3C] l2tp-group 1 mode lns
[H3C-l2tp1] allow l2tp virtual-template 0 remote client
[H3C-l2tp1] tunnel name LNS
[H3C-l2tp1] tunnel password simple H3C@L2TP
[H3C-l2tp1] quit

[H3C] interface Virtual-Template 0
[H3C-Virtual-Template0] ip address 192.168.200.1 24
[H3C-Virtual-Template0] ppp authentication-mode chap
[H3C-Virtual-Template0] remote address pool 1
[H3C-Virtual-Template0] quit

[H3C] ip pool 1 192.168.200.2 192.168.200.100
```

### 9_4_4 SSL VPN 与选型
| 技术 | 场景 | 特点 |
| --- | --- | --- |
| IPSec | 站点到站点（分支互联） | 稳定，需客户端/设备 |
| L2TP over IPSec | 移动办公拨入 | 移动端原生支持 |
| SSL VPN | 移动办公、细粒度授权 | 免客户端（Web 方式），易于管控 |
| GRE over IPSec | 需要跑组播/路由协议 | 先 GRE 后加密 |

---

## 9_5 MPLS VPN 与 VXLAN / EVPN
### 9_5_1 MPLS VPN 基础概念
| 概念 | 说明 |
| --- | --- |
| CE | 用户边缘设备 |
| PE | 运营商边缘设备，维护 VRF |
| P | 运营商核心设备，只做标签转发 |
| VRF | 虚拟路由转发实例，实现路由隔离 |
| RD | 路由区分符，区分不同 VPN 的相同前缀 |
| RT | 路由目标，控制 VPN 路由的收发 |

**配置要点（PE 侧）**：

```plain
[H3C] ip vpn-instance VPN1
[H3C-vpn-instance-VPN1] route-distinguisher 100:1
[H3C-vpn-instance-VPN1] vpn-target 100:1 both
[H3C-vpn-instance-VPN1] quit

[H3C] interface GigabitEthernet 0/0
[H3C-GigabitEthernet0/0] ip binding vpn-instance VPN1
[H3C-GigabitEthernet0/0] ip address 192.168.1.1 24

[H3C] bgp 100
[H3C-bgp-default] ip vpn-instance VPN1
[H3C-bgp-default-VPN1] peer 192.168.1.2 as-number 65001
```

**验证**：`display ip vpn-instance`、`display bgp vpnv4 all routing-table`、`display mpls lsp`。

### 9_5_2 VXLAN / EVPN（数据中心主流）
VXLAN 在三层网络之上构建二层overlay，解决：

+ 传统 VLAN 4094 数量限制（VXLAN 有 1600 万个 VNI）。
+ 虚拟机跨三层迁移（大二层需求）。

| 概念 | 说明 |
| --- | --- |
| VTEP | VXLAN 隧道端点，负责封装/解封装 |
| VNI | VXLAN 网络标识（类似 VLAN ID） |
| EVPN | 用作 VXLAN 的控制平面，通过 BGP 通告 MAC/IP |

```plain
[H3C] interface Vsi-interface 10
[H3C-Vsi-interface10] ip address 192.168.10.1 24
[H3C-Vsi-interface10] quit

[H3C] vsi VPNA
[H3C-vsi-VPNA] vxlan 10
[H3C-vsi-VPNA-vxlan-10] quit
[H3C-vsi-VPNA] quit

[H3C] l2vpn enable
[H3C] interface GigabitEthernet 1/0/1
[H3C-GigabitEthernet1/0/1] xconnect vsi VPNA
```

**验证**：`display vxlan tunnel`、`display l2vpn vsi verbose`。

---

## 9_6 出口方案设计与验证清单
### 出口方案决策表
| 场景 | 方案 |
| --- | --- |
| 单条宽带，简单上网 | Easy IP + 默认路由 |
| 双出口，主备 | 浮动静态路由 + BFD/NQA 联动 |
| 双出口，负载分担 | 策略路由（PBR）按源网段分流 |
| 多分支互联 | IPSec / MPLS VPN / SD-WAN |
| 发布内网服务 | NAT Server + 安全策略 + ACL 限制源 |
| 移动办公 | SSL VPN / L2TP over IPSec |

### 策略路由示例（按源网段分流）
```plain
[H3C] acl basic 2001
[H3C-acl-ipv4-basic-2001] rule 5 permit source 192.168.10.0 0.0.0.255
[H3C-acl-ipv4-basic-2001] quit

[H3C] policy-based-route PBR1 permit node 10
[H3C-pbr-PBR1-10] if-match acl 2001
[H3C-pbr-PBR1-10] apply next-hop 211.x.x.1
[H3C-pbr-PBR1-10] quit

[H3C] interface Vlan-interface 10
[H3C-Vlan-interface10] ip policy-based-route PBR1
```

### 验证清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| NAT 生效 | `display nat session` | 内网地址已转换为出接口地址 |
| 上网正常 | `ping 223.5.5.5` | 通 |
| NAT Server 可访问 | 外网访问测试 | 能访问发布的服务 |
| ACL 命中正确 | `display packet-filter statistics` | 命中计数符合预期 |
| IPSec 隧道建立 | `display ike sa` / `display ipsec sa` | 阶段一/二均为 established/active |
| 隧道内流量通 | `ping -a` 内网地址 | 通 |
| 出口切换正常 | 断开主链路 | 业务中断时间符合预期 |
| MSS 调整 | 大包测试 | 无分片导致的访问异常 |

### 实验笔记模板
```plain
## 实验：出口 NAT + IPSec 分支互联
日期：____   设备：____

### 1. 目标与验收
- [ ] 内网通过 Easy IP 上网
- [ ] NAT Server 发布内网 Web 服务
- [ ] 两个站点间 IPSec 隧道建立，内网互访通

### 2. 参数记录
| 项目 | 站点A | 站点B |
| --- | --- | --- |
| 公网地址 |  |  |
| 内网网段 |  |  |
| 预共享密钥 | （一致） | （一致） |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：IPSec SA 建立不起来
- 假设：ACL 不对称 / 密钥不一致 / 算法不匹配 / 无感兴趣流触发
- 验证：display ike sa + display ipsec sa + ping -a 触发
- 结论：（记录实际原因）

### 4. 边界
- 两端 ACL 必须镜像对称
- IPSec 需要先有感兴趣流才会触发协商
- NAT 与 IPSec 同时存在时注意 NAT 穿越与 ACL 排除
```

# 板块10 · 等保 2.0 合规安全加固（交换机篇）
> 本板块按等保 2.0 的**测评项 → 配置实现 → 验证命令**三段式组织，可直接用于项目交付与测评整改。  
等保测评中，网络设备属于"安全区域边界"与"安全计算环境"两类控制点。

---

## 10_1 等保 2.0 对网络设备的核心要求
| 控制点 | 等保要求 | 对应章节 |
| --- | --- | --- |
| 身份鉴别 | 应对登录用户进行身份标识和鉴别，身份标识具有唯一性，身份鉴别信息具有复杂度要求并定期更换 | 10_3、10_4 |
| 访问控制 | 应对登录的用户分配账户和权限；应重命名或删除默认账户；应及时删除或停用多余的、过期的账户 | 10_4 |
| 安全审计 | 应启用安全审计功能，审计覆盖到每个用户，对重要的用户行为和重要安全事件进行审计 | 10_9 |
| 数据完整性 / 保密性 | 应采用校验技术或密码技术保证重要数据在传输过程中的完整性 / 保密性 | 10_5（SSH） |
| 入侵防范 | 应关闭不需要的系统服务、共享和高危端口 | 10_8 |
| 恶意代码防范 | 应安装防恶意代码软件或配置相应策略 | 10_7（端口安全） |
| 可信验证 | （三级以上）可基于可信根对设备进行可信验证 | 视设备支持 |

### 等保三级对网络设备的硬性指标（测评时逐条核对）
| 指标 | 要求 |
| --- | --- |
| 口令长度 | ≥ 8 位 |
| 口令复杂度 | 包含至少 3 种字符类型 |
| 口令更换周期 | ≤ 90 天 |
| 登录失败处理 | 失败 5 次锁定，锁定时间 ≥ 30 分钟 |
| 登录连接超时 | 空闲 ≤ 20 分钟（1200 秒）自动退出 |
| 远程管理 | 必须加密（禁用 Telnet） |
| 审计 | 必须启用（日志外送 syslog） |

---

## 10_2 设备基础信息配置
```plain
<H3C> system-view
[H3C] sysname Core-Switch-01                            # 设备命名，唯一且可识别
[H3C] interface Vlan-interface 1
[H3C-Vlan-interface1] ip address 192.168.1.10 255.255.255.0
[H3C-Vlan-interface1] undo shutdown
[H3C-Vlan-interface1] quit
```

### 查看命令速查（开局与测评都用）
```plain
<H3C> display current-configuration                     # 当前运行配置（简写 dis cu）
<H3C> display saved-configuration                       # 已保存配置
<H3C> display mac-address                               # MAC 地址表
<H3C> display mac-address xxxx-xxxx-xxxx                # 指定 MAC 信息
<H3C> display current-configuration interface           # 所有端口配置（简写 dis cu int）
<H3C> display interface brief                           # 接口简要状态
<H3C> display interface brief | include ADM             # 只看被手工关闭的端口
```

### Link 状态三态（测评与巡检必看）
| 状态 | 含义 | 处理 |
| --- | --- | --- |
| UP | 接口正常连通 | — |
| DOWN | 接口未接线或网线未插好 | 检查物理链路 |
| ADM | 手动关闭的端口（Administratively Down） | `undo shutdown` 开启 |

---

## 10_3 身份鉴别与口令安全（等保核心）
### 10_3_1 全局密码策略
```plain
[H3C] password-control enable                           # 开启密码管理功能
[H3C] password-control aging enable                     # 开启密码有效期
[H3C] password-control aging 90                         # 有效期 90 天（等保要求 ≤ 90）
[H3C] password-control length enable                    # 开启长度限制
[H3C] password-control length 8                         # 最小长度 8 位（等保要求 ≥ 8）
[H3C] password-control composition type-number 3 type-length 1   # 至少 3 种字符类型
[H3C] password-control complexity user-name check       # 不能包含用户名
[H3C] password-control complexity same-character check  # 不能包含连续 3 个相同字符
[H3C] password-control login-attempt 5 exceed lock-time 30       # 失败 5 次锁定 30 分钟
```

**四种字符类型**：大写字母、小写字母、数字、特殊字符。

### 10_3_2 单用户密码策略（优先级高于全局）
```plain
[H3C] local-user sysadmin class manage
[H3C-luser-manage-sysadmin] password-control aging 60
[H3C-luser-manage-sysadmin] password-control length 10
```

> 规则：**用户视图下配置了密码策略，则该用户的策略优先生效**；未配置则继承全局策略。

### 10_3_3 查看与验证
```plain
<H3C> display password-control                          # 全局策略
<H3C> display password-control super                    # 超级密码策略
<H3C> display local-user                                # 用户状态（是否被锁定）
<H3C> display local-user username sysadmin              # 单用户详情
```

> 注意：开启 Password Control 后，密码在配置文件中以密文存储；若忘记密码需按板块1 的 1_7 流程恢复。

---

## 10_4 三权分立账号体系
等保 2.0 要求**系统管理员、安全管理员、审计管理员三权分立**，权限互相隔离。

### 10_4_1 创建三权账号
```plain
# 系统管理员（配置与维护）
[H3C] local-user sysadmin class manage
[H3C-luser-manage-sysadmin] password cipher Sys@2024!Adm
[H3C-luser-manage-sysadmin] service-type ssh terminal
[H3C-luser-manage-sysadmin] authorization-attribute user-role network-admin
[H3C-luser-manage-sysadmin] quit

# 安全管理员（安全策略）
[H3C] local-user secadmin class manage
[H3C-luser-manage-secadmin] password cipher Sec@2024!Adm
[H3C-luser-manage-secadmin] service-type ssh
[H3C-luser-manage-secadmin] authorization-attribute user-role level-2
[H3C-luser-manage-secadmin] quit

# 审计管理员（只读 + 日志）
[H3C] local-user auditadmin class manage
[H3C-luser-manage-auditadmin] password cipher Aud@2024!Adm
[H3C-luser-manage-auditadmin] service-type ssh
[H3C-luser-manage-auditadmin] authorization-attribute user-role network-operator
[H3C-luser-manage-auditadmin] quit
```

### 10_4_2 删除默认账户（等保硬性要求）
```plain
[H3C] undo local-user admin                             # 删除默认 admin 账户
[H3C] display local-user                                # 确认所有账户均为实名账户
```

### 10_4_3 三权角色说明
| 角色 | 用户名 | 权限级别 | 职责 |
| --- | --- | --- | --- |
| 系统管理员 | sysadmin | level-15（network-admin） | 设备配置、系统维护、网络管理 |
| 安全管理员 | secadmin | level-2 | 安全策略配置、用户权限审批、漏洞处置 |
| 审计管理员 | auditadmin | level-1（network-operator） | 查看审计日志、日志备份管理 |

**实施要点**：三权账号必须**与实名人员一一对应**，不能多人共用一个账号。测评时会检查账号数量与人员名单是否匹配，以及是否存在长期未登录的僵死账号。

---

## 10_5 SSH 安全远程管理（禁用 Telnet）
等保明确要求：**远程管理必须加密，禁用 Telnet 等明文协议**。

### 10_5_1 完整配置
```plain
# 1. 生成本地密钥对（SSH 前置条件）
[H3C] public-key local create rsa
The range of public key modulus is (512 ~ 2048).
Input the modulus length [default = 1024]: 2048         # 建议 2048，1024 已不安全
[H3C] public-key local create ecdsa secp256r1           # 推荐 ECDSA

# 2. 开启 SSH 服务
[H3C] ssh server enable

# 3. VTY 线路仅允许 SSH
[H3C] user-interface vty 0 4
[H3C-ui-vty0-4] authentication-mode scheme
[H3C-ui-vty0-4] protocol inbound ssh
[H3C-ui-vty0-4] idle-timeout 20 0                       # 20 分钟（等保要求 ≤ 20 分钟）
[H3C-ui-vty0-4] acl 2000 inbound                        # 仅允许运维网段
[H3C-ui-vty0-4] quit

# 4. 创建 SSH 登录用户
[H3C] local-user sysadmin class manage
[H3C-luser-manage-sysadmin] password cipher Admin@2024!SSH
[H3C-luser-manage-sysadmin] service-type ssh
[H3C-luser-manage-sysadmin] authorization-attribute user-role network-admin
[H3C-luser-manage-sysadmin] quit

# 5. 关闭 Telnet 等高危服务
[H3C] undo telnet server enable
[H3C] undo ip http enable

# 6. 保存
[H3C] save force
```

### 10_5_2 验证
```plain
<H3C> display ssh server status
<H3C> display telnet server status                      # 应为 disabled
<H3C> display ip http                                   # HTTP 应为 disabled
<H3C> display ssh server session
```

---

## 10_6 SNMPv3 与日志外送
### 10_6_1 SNMPv3（加密 + 认证）
```plain
[H3C] snmp-agent
[H3C] snmp-agent sys-info version v3                    # 只用 v3，禁用 v1/v2c
[H3C] snmp-agent group v3 GRP-ADMIN privacy read-view DEFAULT write-view DEFAULT
[H3C] snmp-agent usm-user v3 snmpuser GRP-ADMIN simple authentication-mode sha Auth@2024 privacy-mode aes128 Priv@2024
[H3C] snmp-agent target-host trap address udp-domain 192.168.100.50 params securityname snmpuser v3 privacy
```

> **等保要求**：SNMP 团体名不能是默认的 public/private；v1/v2c 明文传输，应禁用或改为 v3。

### 10_6_2 日志外送（syslog）
```plain
[H3C] info-center enable
[H3C] info-center loghost 192.168.100.50 facility local5
[H3C] info-center source default loghost level informational
[H3C] info-center logbuffer size 1024
```

**验证**：

```plain
<H3C> display info-center
<H3C> display logbuffer
```

---

## 10_7 端口安全与边界防护
### 10_7_1 关闭闲置端口
```plain
[H3C] interface range g1/0/25 to g1/0/48
[H3C-if-range] description UNUSED-SHUTDOWN
[H3C-if-range] shutdown
[H3C-if-range] port access vlan 999                     # 划入隔离 VLAN（双保险）
[H3C-if-range] quit
```

### 10_7_2 端口安全（防私接）
```plain
[H3C-GigabitEthernet1/0/1] port-security enable
[H3C-GigabitEthernet1/0/1] port-security max-mac-count 1
[H3C-GigabitEthernet1/0/1] port-security intrusion-mode disableport
```

### 10_7_3 二层防护全套（与板块8 呼应）
```plain
[H3C] dhcp snooping enable
[H3C] vlan 10
[H3C-vlan10] dhcp snooping enable
[H3C-vlan10] arp detection enable                       # 动态 ARP 检测
[H3C-vlan10] ip verify source ip-address mac-address    # IP Source Guard
[H3C-vlan10] quit
```

### 10_7_4 业务口移出 VLAN 1
```plain
[H3C] interface range g1/0/1 to g1/0/24
[H3C-if-range] port access vlan 10                      # 业务口全部划入业务 VLAN
[H3C-if-range] quit

[H3C] interface g1/0/24                                 # Trunk 口
[H3C-GigabitEthernet1/0/24] undo port trunk permit vlan 1
```

---

## 10_8 关闭高危服务与端口
```plain
[H3C] undo telnet server enable                         # 关闭 Telnet
[H3C] undo ip http enable                               # 关闭 HTTP（保留 HTTPS）
[H3C] undo ftp server enable                            # 关闭 FTP（用 SFTP/SCP 替代）
[H3C] undo tftp server enable                           # 关闭 TFTP 服务（作为客户端可用）
[H3C] undo ip source-routing                            # 关闭源路由
[H3C] ip icmp rate-limit enable                         # ICMP 限速
[H3C] undo icmp redirect send                           # 关闭 ICMP 重定向
[H3C] ssh server compatible-ssh1x disable               # 禁用 SSH1
```

**验证**：

```plain
<H3C> display telnet server status
<H3C> display ip http
<H3C> display tcp                                       # 看哪些端口在监听
```

---

## 10_9 安全审计配置
```plain
[H3C] info-center enable
[H3C] info-center loghost 192.168.100.50
[H3C] info-center source default loghost level informational
[H3C] info-center timestamp loghost date                # 日志带日期时间戳

# 命令行审计（记录用户执行的命令）
[H3C] command-alias enable                              # 视版本支持
[H3C] info-center source COMMAND loghost level informational
```

**NTP 时间同步（审计的前提）**：

```plain
[H3C] ntp-service enable
[H3C] ntp-service unicast-server 192.168.100.1
[H3C] clock timezone Beijing add 08:00:00
```

> **关键**：日志**必须时间准确**，否则审计记录无法用于事件回溯。等保检查必看 NTP 配置与设备时间。

---

## 10_10 自检清单与整改报告模板
### 自检清单（测评前逐项打勾）
| 序号 | 检查项 | 检查命令 | 达标标准 |
| --- | --- | --- | --- |
| 1 | 设备命名唯一 | `display current-configuration | include sysname` | 命名唯一可识别 |
| 2 | 口令长度 ≥ 8 | `display password-control` | length ≥ 8 |
| 3 | 口令复杂度 ≥ 3 类 | `display password-control` | composition type-number 3 |
| 4 | 口令有效期 ≤ 90 天 | `display password-control` | aging ≤ 90 |
| 5 | 登录失败锁定 | `display password-control` | 5 次锁定 30 分钟 |
| 6 | 空闲超时 ≤ 20 分钟 | `display current-configuration | begin user-interface` | idle-timeout ≤ 20 |
| 7 | 三权分立 | `display local-user` | 三个角色账号，实名对应 |
| 8 | 默认账户已删 | `display local-user` | 无 admin 等默认账号 |
| 9 | Telnet 已关 | `display telnet server status` | disabled |
| 10 | SSH 已开且用 v2 | `display ssh server status` | enabled，version 2 |
| 11 | HTTPS 替代 HTTP | `display ip http` | HTTP disabled |
| 12 | SNMP 用 v3 | `display snmp-agent sys-info version` | 仅 v3 |
| 13 | 日志外送 | `display info-center` | loghost 已配置且可达 |
| 14 | NTP 同步 | `display ntp-service status` | 已同步 |
| 15 | 闲置端口关闭 | `display interface brief | include ADM` | 闲置口均为 ADM |
| 16 | 业务口移出 VLAN 1 | `display vlan 1` | 无业务端口 |
| 17 | ACL 限制管理源 | `display acl all` | 管理访问受限 |
| 18 | 二层防护开启 | `display dhcp snooping` | Snooping 已启用 |
| 19 | 密码密文存储 | `display current-configuration | include password` | cipher 形式 |

### 整改报告模板（交付用）
```plain
## 网络设备等保合规整改报告

### 一、整改范围
设备清单：（型号、管理 IP、位置、责任人）

### 二、整改依据
GB/T 22239-2019 信息安全技术 网络安全等级保护基本要求（相应级别）

### 三、问题与整改对照表
| 序号 | 测评项 | 问题描述 | 整改措施 | 整改后状态 | 验证命令与结果 |
| --- | --- | --- | --- | --- | --- |
| 1 | 身份鉴别 | 口令长度不足 | 配置 password-control length 8 | 已整改 | display password-control：length 8 |
| 2 | 访问控制 | 存在默认 admin 账号 | 删除并创建三权账号 | 已整改 | display local-user：无 admin |

### 四、遗留问题与风险说明
（无法整改项需说明原因与替代补偿措施）

### 五、附件
- 整改前后配置对比
- 验证命令输出截图
- 设备台账
```

### 📌 案例手记：一次测评整改的"翻车"与补救
某单位等保三级测评，网络设备的整改项有 12 条。工程师连夜改完，第二天复测仍有 5 条不通过。

复盘发现的问题：

1. **只改配置不改台账**：删除了 admin，但没确认是否有脚本在用 admin 登录监控系统——监控系统挂了。
2. **闲置端口关闭后没验证业务**：某台交换机的 25-48 口批量 shutdown，但有 2 个口实际接了设备（台账不准）。
3. **日志外送配了但没验证**：syslog 服务器 IP 写错，日志一条都没送过去，测评员要求提供最近的日志证据时拿不出来。
4. **NTP 配了但时区错**：日志时间差 8 小时，无法用于事件关联。

**正确做法**：

+ 整改前**先核对台账与实际接线**（用 `display lldp neighbor` 辅助确认）。
+ 每条整改**配完立即验证**，并保存命令输出作为证据。
+ 影响业务的整改**放在变更窗口**，提前通知相关方。

---

## 10_11 实验笔记模板
```plain
## 实验：等保 2.0 交换机加固全流程
日期：____   设备：____

### 1. 目标与验收
- [ ] 19 项自检清单全部达标
- [ ] 三权账号可正常登录且权限隔离
- [ ] Telnet 关闭、SSH 正常、日志外送可达

### 2. 整改前后对比
| 项目 | 整改前 | 整改后 |
| --- | --- | --- |
| 口令长度 | 无限制 | 8 |
| Telnet | enable | disable |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：加固后监控平台无法采集
- 假设：admin 账号被删 / SNMP 团体名变更 / ACL 拦截
- 验证：display acl 命中计数 + 在服务器上 telnet 设备端口
- 结论：（记录实际原因）

### 4. 边界
- 改密码策略可能导致现有账号过期，需提前规划
- 关闭闲置端口前必须核对实际接线
- 所有整改动作需留证据（配置 + 输出 + 截图）
```

### 本板块能力验收
逐项自检请对照 **10_10 的 19 项自检清单**。三个层级的达标标准如下：

| 层级 | 达标标准 |
| --- | --- |
| NE | 能按模板独立完成一台交换机的加固配置，并跑通自检清单前 6 项 |
| SE | 能在不影响业务的前提下完成整改，对 19 项逐条给出配置证据与 `display` 输出 |
| IE | 能输出一份测评整改报告，说清每项的风险等级、整改依据、遗留问题与回退方案 |

# 板块11 · SecPath 防火墙：安全域、策略与远程管理（含排障实录）
> 本板块把一次真实的现场调试过程拆解为"场景 → 配置 → 报错 → 定位 → 解决"的完整链路，并补充现代 V7 防火墙的配置对照。  
覆盖 H3CNE-Security → H3CSE-Security（GB0-530 构建安全网络架构）→ H3CIE-Security 的能力进阶。

---

## 11_1 场景说明与组网拓扑
### 11_1_1 典型场景
防火墙在机房，现场配置不便，目标是：先调测到可以通过核心交换机下面的一台跳板机访问，再远程调试。

### ASCII 拓扑
```plain
        [外网]
           |  第1步
           v
       [跳板机]
           |  第3步
           v
  [H3C 防火墙 GE0/0] 192.168.10.31/24
           |  第2步
           v
  [核心交换机] 192.168.10.254/24
```

**说明**：防火墙 GE0/0 口 IP 为 192.168.10.31/24，与核心交换机 192.168.10.254/24 三层互联。

### 11_1_2 版本差异提示（重要）
V5 设备（如 F1000-S 运行 Comware Version 5.20）的命令体系与 V7 有显著差异：

| 功能 | V5（老设备） | V7（现行标准） |
| --- | --- | --- |
| 用户级别 | `authorization-attribute level 3` | `authorization-attribute user-role network-admin` |
| 用户视图 | `[H3C-luser-admin]` | `[H3C-luser-manage-admin]`（带 class manage） |
| 安全策略 | `interzone policy default by-priority` | `security-policy ip` + `rule` |
| NAT | 接口下 `nat outbound` | `nat global-policy` 或接口下 `nat outbound` |

**学习建议**：考试以 V7 为准，但现场仍会遇到大量 V5 设备（尤其是早年上线的防火墙），**两套命令都要能认**。

---

## 11_2 配置过程：从零到可远程管理
### 第一步：开启远程管理服务
```plain
<H3C> sys
[H3C] telnet server enable            # V5 场景；V7 建议直接配 SSH
```

### 第二步：配置 VTY 线路与认证方式
```plain
[H3C] user-interface vty 0 4
[H3C-ui-vty0-4] authentication-mode scheme     # 用户名 + 密码认证
[H3C-ui-vty0-4] quit
```

### 第三步：创建访问用户
```plain
[H3C] local-user admin                                  # V5 写法；V7 为 local-user admin class manage
[H3C-luser-admin] password simple your_password
[H3C-luser-admin] authorization-attribute level 3       # 命令级别 3（管理级）
[H3C-luser-admin] service-type telnet                   # 服务类型为 telnet
[H3C-luser-admin] quit
```

**关键提醒**：`service-type` 必须与登录方式匹配。若该用户还能登录 Web，则需 `service-type web`；若只用 SSH，则必须改为 `service-type ssh`。

### 第四步：配置安全域（现场遇到报错）
```plain
[H3C] zone name trust
[H3C-zone-trust] import interface GigabitEthernet 0/0
Error: The interface has been added to another zone.     # 报错
```

**报错处理**：说明该接口已被加入其他安全域（如默认已在 Management 域）。先用 `display security-zone` 查看接口归属，必要时先从原域移除：

```plain
[H3C-zone-trust] quit
[H3C] display security-zone                              # 查看接口当前所属域
```

### 第五步：配置管理端口 IP
```plain
[H3C] interface GigabitEthernet 0/0
[H3C-GigabitEthernet0/0] dis this
#
interface GigabitEthernet0/0
 port link-mode route                                    # 三层路由模式（关键）
 ip address 192.168.0.1 255.255.255.0                    # 出厂默认地址
#
return

[H3C-GigabitEthernet0/0] ip address 192.168.10.31 255.255.255.0    # 改为与核心互联的地址
[H3C-GigabitEthernet0/0] quit
```

> `port link-mode route` 是防火墙接口的核心属性：防火墙接口**默认是三层路由模式**（可直接配 IP），与交换机的二层模式不同。若接口是 bridge 模式，则不能配 IP。

### 第六步：确认链路正常
配置完成后防火墙端口提示 UP：

```plain
%Feb 21 08:57:37:922 H3C IFNET/3/LINK_UPDOWN: GigabitEthernet0/0 link status is UP.
%Feb 21 08:57:37:923 H3C IFNET/5/LINEPROTO_UPDOWN: Line protocol on the interface
GigabitEthernet0/0 is UP.
```

自 ping 验证：

```plain
[H3C] ping 192.168.10.31
PING 192.168.10.31: 56 data bytes, press CTRL_C to break
Reply from 192.168.10.31: bytes=56 Sequence=0 ttl=255 time=1 ms
Reply from 192.168.10.31: bytes=56 Sequence=1 ttl=255 time=1 ms
Reply from 192.168.10.31: bytes=56 Sequence=2 ttl=255 time=1 ms
Reply from 192.168.10.31: bytes=56 Sequence=3 ttl=255 time=1 ms
Reply from 192.168.10.31: bytes=56 Sequence=4 ttl=255 time=2 ms

5 packet(s) transmitted
5 packet(s) received
0.00% packet loss
round-trip min/avg/max = 1/1/1 ms
```

**现场经验**：这一步在案例中是"去核心交换机上检查互联端口发现被 shutdown 了，取消 shutdown 后防火墙端口才 UP"。  
**防火墙端口 UP 但 ping 不通对端，先查对端端口是否被 shutdown**——这是跨厂商对接最常见的低级故障。

### 📌 案例手记：跨厂商对接，"灯亮着却不通信"
现场 H3C 防火墙与另一厂商核心交换机对接，防火墙端口配置完毕，指示灯正常亮起，但 ping 不通核心。

排查链条：

1. 防火墙侧 `display interface g0/0` —— 物理 UP、协议 UP，IP 配置正确。
2. 防火墙侧自 ping —— 通（说明本端 IP 层正常）。
3. 查核心交换机侧 —— 该互联口处于 **shutdown** 状态（配置模板里默认关闭，上线时漏了 undo）。
4. 在核心侧 `undo shutdown` —— 立即通。

**沉淀为检查表**（跨厂商对接必查）：

```plain
第1步 本端端口是否 UP（物理 + 协议）
第2步 对端端口是否 UP、是否被 shutdown
第3步 两端 IP 是否同网段、掩码是否一致
第4步 两端是否有 ACL / 安全策略拦截
第5步 两端速率双工是否匹配
第6步 是否有 VLAN / Trunk 封装差异
```

---

## 11_3 安全域（Security Zone）原理
### 11_3_1 什么是安全域
安全域是防火墙的核心概念：**接口必须加入某个安全域，域与域之间的流量默认不通，必须由安全策略显式放行**。

### 默认安全域（V5）
| 安全域 | ID | 优先级 | 用途 |
| --- | --- | --- | --- |
| Management | 0 | 100 | 设备管理 |
| Local | 1 | 100 | 防火墙自身（如 ping 防火墙自己） |
| Trust | 2 | 85 | 内网可信区域 |
| DMZ | 3 | 50 | 服务器区 |
| Untrust | 4 | 5 | 外网不可信区域 |

### 11_3_2 配置命令
```plain
# V5 写法
[H3C] zone name trust                                   # 创建 / 进入安全域
[H3C-zone-trust] priority 85                            # 设置优先级
[H3C-zone-trust] import interface GigabitEthernet 0/0   # 加入接口
[H3C-zone-trust] ip virtual-reassembly                  # 开启分片重组
[H3C-zone-trust] quit

# V7 写法
[H3C] security-zone name Trust
[H3C-security-zone-Trust] import interface GigabitEthernet 1/0/1
[H3C-security-zone-Trust] quit
```

### ASCII：安全域与流量方向
```plain
   Untrust (优先级 5)          DMZ (50)           Trust (85)
   [外网接口]                 [服务器接口]        [内网接口]
        |                          |                  |
        +---------- 域间流量默认不通，需策略放行 ------+

   出站（Trust → Untrust）：高优先级 → 低优先级
   入站（Untrust → Trust）：低优先级 → 高优先级（默认拒绝，需显式放行）
   Local 域：访问防火墙自身的流量（如 ping 防火墙、SSH 登录）
```

---

## 11_4 安全策略（核心）
### 11_4_1 V5 域间策略
```plain
[H3C] interzone source trust destination untrust
[H3C-interzone-trust-untrust] policy 1
[H3C-interzone-trust-untrust-policy-1] action permit
[H3C-interzone-trust-untrust-policy-1] policy source 192.168.10.0 0.0.0.255
[H3C-interzone-trust-untrust-policy-1] policy destination any
[H3C-interzone-trust-untrust-policy-1] policy service service-set http
[H3C-interzone-trust-untrust-policy-1] quit
```

### 11_4_2 V7 安全策略（推荐写法）
```plain
[H3C] security-policy ip
[H3C-security-policy-ip] rule 5 name Permit_Trust_to_Internet
[H3C-security-policy-ip-5-Permit_Trust_to_Internet] source-zone Trust
[H3C-security-policy-ip-5-Permit_Trust_to_Internet] destination-zone Untrust
[H3C-security-policy-ip-5-Permit_Trust_to_Internet] source-ip-subnet 192.168.10.0 24
[H3C-security-policy-ip-5-Permit_Trust_to_Internet] action pass
[H3C-security-policy-ip-5-Permit_Trust_to_Internet] quit

# 放行到防火墙自身的管理流量（Local 域）
[H3C-security-policy-ip] rule 10 name Permit_SSH_to_Local
[H3C-security-policy-ip-10-Permit_SSH_to_Local] source-zone Trust
[H3C-security-policy-ip-10-Permit_SSH_to_Local] destination-zone Local
[H3C-security-policy-ip-10-Permit_SSH_to_Local] service ssh
[H3C-security-policy-ip-10-Permit_SSH_to_Local] action pass
[H3C-security-policy-ip-10-Permit_SSH_to_Local] quit
```

### 11_4_3 策略设计原则
| 原则 | 说明 |
| --- | --- |
| 最小权限 | 只放行业务必需的源、目的、服务 |
| 顺序匹配 | 从上到下匹配，命中即停止；**精细策略放前面** |
| 默认拒绝 | 末尾配置 `action drop` 的兜底规则（V7 默认即拒绝） |
| 命名规范 | 用 `动作_源域_目的域_业务` 的可读命名 |

### 11_4_4 验证（最重要）
```plain
<H3C> display security-policy ip                        # 策略列表
<H3C> display security-policy ip rule 5                 # 单条策略
<H3C> display security-policy statistics                # 策略命中统计
<H3C> display security-policy statistics rule 5         # 单条命中次数
<H3C> display session table                             # 会话表
<H3C> display session table source-ip 192.168.10.10     # 按源查会话
```

**排障利器**：`display security-policy statistics` 看**命中计数**——如果策略计数为 0，说明流量根本没匹配到（可能源/目的/服务写错）；如果计数在涨但业务不通，说明匹配上了但被后续环节（NAT、路由）阻断。

---

## 11_5 NAT 与服务器发布
### 11_5_1 出向 NAT（内网访问外网）
```plain
# V7
[H3C] nat global-policy
[H3C-nat-global-policy] rule name NAT_Outbound
[H3C-nat-global-policy-rule-NAT_Outbound] source-zone Trust
[H3C-nat-global-policy-rule-NAT_Outbound] destination-zone Untrust
[H3C-nat-global-policy-rule-NAT_Outbound] source-ip-subnet 192.168.10.0 24
[H3C-nat-global-policy-rule-NAT_Outbound] action snat easy-ip
```

或接口方式：

```plain
[H3C] interface GigabitEthernet 1/0/2
[H3C-GigabitEthernet1/0/2] nat outbound
```

### 11_5_2 NAT Server（发布内网服务器）
```plain
# V7
[H3C] nat global-policy
[H3C-nat-global-policy] rule name Publish_Web
[H3C-nat-global-policy-rule-Publish_Web] destination-zone Untrust
[H3C-nat-global-policy-rule-Publish_Web] destination-ip-host 211.x.x.100
[H3C-nat-global-policy-rule-Publish_Web] service http
[H3C-nat-global-policy-rule-Publish_Web] action dnat ip-address 192.168.100.10 port 80
```

**配套**：发布服务还需在安全策略中放行 Untrust → DMZ（或 Trust）的对应服务，否则只有 NAT 没有策略，流量仍被丢弃。

### 11_5_3 验证
```plain
<H3C> display nat session
<H3C> display nat global-policy
<H3C> display nat statistics
```

---

## 11_6 RBM 双机热备
RBM（Remote Backup Management）实现防火墙双机热备，主设备故障时备设备接管会话与配置。

```plain
# 主设备
[H3C] remote-backup group
[H3C-remote-backup-group] remote-ip 10.255.1.2
[H3C-remote-backup-group] local-ip 10.255.1.1
[H3C-remote-backup-group] data-channel interface GigabitEthernet 1/0/9
[H3C-remote-backup-group] device-role primary
[H3C-remote-backup-group] backup-mode dual-active

# 备设备（device-role secondary）
```

**验证**：`display remote-backup group`、`display remote-backup status`。

> 关键：RBM 要求两台设备的**型号、版本、License、接口编号**保持一致；配置通过数据通道自动同步，**只需在主设备上配置**。

---

## 11_7 防火墙排障实录与验证清单
### 排障六步法（防火墙专用）
```plain
第1步 接口 UP 吗？        display interface brief
第2步 接口在哪个域？      display security-zone
第3步 有安全策略吗？      display security-policy ip
第4步 策略命中了吗？      display security-policy statistics
第5步 NAT 生效了吗？      display nat session
第6步 有会话吗？          display session table
```

### 典型故障对照表
| 现象 | 可能原因 | 定位命令 |
| --- | --- | --- |
| 内网不能上网 | 无出向策略 / 无 NAT / 无回程路由 | `display security-policy statistics`、`display nat session` |
| 能 ping 通但打不开网页 | 策略只放 ICMP / DNS 未放 | 看策略匹配的服务对象 |
| 外网访问不到内网服务器 | NAT Server 未配 / 策略未放行 Untrust→DMZ | `display nat global-policy` |
| 管理流量不通（SSH/HTTPS） | 未放通到 Local 域 | `display security-policy ip` |
| 部分网站打不开 | MTU/MSS 问题 | 调整 `tcp mss 1452` |
| 双机切换异常 | RBM 数据通道不通 | `display remote-backup status` |

### 📌 案例手记：策略"看着对"却不生效
客户内网新增一个网段，工程师按已有策略复制了一条新规则，但新网段依然不能上网。

排查：

1. `display security-policy ip` —— 新规则存在，配置看起来与老规则一致。
2. `display security-policy statistics rule X` —— **命中计数为 0**。
3. 仔细对比发现：新规则的**源地址对象**引用的是旧对象（复制时忘了改），仍指向老网段。
4. 修正源地址对象后立即生效。

**方法论沉淀**：**防火墙排障先看命中计数。** 计数为 0 → 匹配条件写错（五元组）；计数在涨 → 匹配上了，问题在后续（NAT/路由/应用）。

### 验证清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| 接口与域正确 | `display security-zone` | 每个业务接口归属正确的域 |
| 策略存在且有序 | `display security-policy ip` | 精细在前、兜底拒绝在后 |
| 策略被命中 | `display security-policy statistics` | 业务流量对应规则计数增长 |
| 会话正常 | `display session table` | 有正向与反向会话 |
| NAT 生效 | `display nat session` | 内网地址已转换 |
| 服务器可发布 | 外网访问测试 | 能访问发布的服务 |
| 日志记录 | `display logbuffer` | 关键拒绝动作有日志 |
| 双机正常 | `display remote-backup status` | 主备状态正常、配置已同步 |

### 实验笔记模板
```plain
## 实验：防火墙安全域 + 策略 + NAT Server
日期：____   设备：____   版本：V5 / V7

### 1. 目标与验收
- [ ] 三个安全域接口划分正确
- [ ] 内网能上网（策略 + NAT 均生效）
- [ ] 外网能访问发布的 Web 服务

### 2. 策略规划表
| 规则名 | 源域 | 目的域 | 源地址 | 目的地址 | 服务 | 动作 |
| --- | --- | --- | --- | --- | --- | --- |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：内网不能上网
- 假设：无策略 / 策略未命中 / 无 NAT / 无回程路由
- 验证：display security-policy statistics + display nat session
- 结论：（记录实际原因，并标注命中计数）

### 4. 边界
- 域间流量默认不通，必须显式放行
- 访问防火墙自身需放通到 Local 域
- NAT Server 必须配策略 + NAT 两处
- V5 与 V7 命令差异大，先确认版本
```

# 板块12 · WLAN 无线局域网与网络准入控制
> 本板块对应 H3CSE-WLAN（GB0-343）与 H3CIE-WLAN 方向，同时覆盖 GB0-372 中"园区网安全技术"要求的 802.1X、MAC 认证、Portal 认证与 EAD 方案。  
**70% 的"网络问题"其实是无线问题，而其中 70% 又是规划问题而非配置问题。**

---

## 12_1 无线基础概念
### 12_1_1 802.11 标准演进
| 标准 | 频段 | 最大速率 | 关键特性 |
| --- | --- | --- | --- |
| 802.11a | 5 GHz | 54 Mbps | OFDM |
| 802.11b/g | 2.4 GHz | 11 / 54 Mbps | — |
| 802.11n（Wi-Fi 4） | 2.4 / 5 GHz | 600 Mbps | MIMO、40 MHz 信道捆绑 |
| 802.11ac（Wi-Fi 5） | 5 GHz | 6.9 Gbps | MU-MIMO、80/160 MHz、256-QAM |
| 802.11ax（Wi-Fi 6） | 2.4 / 5 GHz | 9.6 Gbps | OFDMA、上下行 MU-MIMO、1024-QAM、TWT |

### 12_1_2 2.4G 与 5G 对比
| 对比项 | 2.4 GHz | 5 GHz |
| --- | --- | --- |
| 可用非重叠信道 | **1、6、11（仅 3 个）** | 国内 36/40/44/48、149/153/157/161/165 |
| 覆盖范围 | 大（穿墙好） | 小（穿墙差） |
| 干扰 | 严重（蓝牙、微波炉、邻居 Wi-Fi） | 少 |
| 速率 | 低 | 高 |

**规划原则**：高密度场景优先 5G，开启 **5G 优先（band-steering）**；2.4G 只做覆盖补盲。

### ASCII：2.4G 信道复用规划
```plain
  信道 1     信道 6     信道 11
   [AP1]      [AP2]      [AP3]
     |          |          |
     +---- 相邻 AP 用不同信道，避免同频干扰 ----+

  蜂窝式复用：1 / 6 / 11 三个信道循环使用
  同信道 AP 之间保持足够距离（降低同频干扰）
```

### 12_1_3 核心术语
| 术语 | 说明 |
| --- | --- |
| SSID | 无线网络名称 |
| BSSID | AP 的 MAC 地址（每个射频一个） |
| ESSID | 多个 AP 组成的同一无线网络 |
| AP | 无线接入点（Fit AP 需 AC 管理，Fat AP 独立工作） |
| AC | 无线控制器，集中管理 AP |
| CAPWAP | AC 与 AP 之间的隧道协议（控制端口 **UDP 5246**，数据端口 **UDP 5247**） |
| 漫游 | 终端在 AP 间切换，二层漫游同 VLAN，三层漫游跨 VLAN |

---

## 12_2 AC + Fit AP 组网配置（主流架构）
### 12_2_1 组网前提
+ AP 与 AC 之间**三层可达**（或直连二层）。
+ AP 能通过 DHCP 获取 IP，且能学到 AC 地址（**Option 43**）。
+ AC 上配置 AP 的管理 VLAN 与业务 VLAN。

### ASCII 拓扑
```plain
   [AC] 192.168.100.1
     |  (管理 VLAN 100)
     |
   [汇聚交换机] ── (业务 VLAN 200) ── [核心]
     |
   [接入 PoE 交换机]
     |      |      |
    AP1    AP2    AP3
     \      |      /
      \     |     /
       [无线终端 → SSID: H3C-Office → 业务 VLAN 200]
```

### 12_2_2 配置步骤
#### 步骤 1：AC 基础配置
```plain
[H3C] sysname AC-01
[AC-01] vlan 100                                    # AP 管理 VLAN
[AC-01-vlan100] quit
[AC-01] vlan 200                                    # 无线业务 VLAN
[AC-01-vlan200] quit

[AC-01] interface Vlan-interface 100
[AC-01-Vlan-interface100] ip address 192.168.100.1 24
[AC-01-Vlan-interface100] quit

[AC-01] interface Vlan-interface 200
[AC-01-Vlan-interface200] ip address 192.168.200.1 24
[AC-01-Vlan-interface200] quit
```

#### 步骤 2：配置 DHCP（给 AP 分配地址并下发 AC 地址）
```plain
[AC-01] dhcp enable
[AC-01] dhcp server ip-pool AP-MGMT
[AC-01-dhcp-pool-ap-mgmt] network 192.168.100.0 mask 255.255.255.0
[AC-01-dhcp-pool-ap-mgmt] gateway-list 192.168.100.1
[AC-01-dhcp-pool-ap-mgmt] option 43 hex 8007000001C0A86401    # 关键：告诉 AP，AC 在哪
[AC-01-dhcp-pool-ap-mgmt] quit
```

**Option 43 说明**：这是 AP 发现 AC 的核心机制。  
格式为 **80（类型）+ 07（长度）+ 0000 + 01（AC 数量）+ C0A86401（AC 的 IP 十六进制，此处为 192.168.100.1）**。  
若 AC 与 AP **二层直连**，AP 可通过广播自动发现 AC，无需 Option 43。

#### 步骤 3：创建无线服务模板（SSID）
```plain
[AC-01] wlan service-template 1 crypto
[AC-01-wlan-st-1] ssid H3C-Office
[AC-01-wlan-st-1] vlan 200                                   # 业务 VLAN
[AC-01-wlan-st-1] akm mode psk
[AC-01-wlan-st-1] preshared-key pass-phrase simple Office@2024
[AC-01-wlan-st-1] cipher-suite ccmp
[AC-01-wlan-st-1] security-ie rsn
[AC-01-wlan-st-1] service-template enable                    # 启用服务模板
[AC-01-wlan-st-1] quit
```

#### 步骤 4：创建 AP 并绑定服务模板
```plain
[AC-01] wlan ap ap-01 model WA6320                           # 型号需与实物一致
[AC-01-wlan-ap-ap-01] serial-id 210235A1B2C3D4E5F6G7         # AP 序列号
[AC-01-wlan-ap-ap-01] quit

# 或采用自动 AP 固化（先让 AP 上线再手工转固化）
[AC-01] wlan auto-ap enable
[AC-01] wlan auto-persistent enable
```

#### 步骤 5：配置射频并绑定服务模板（V7 方式）
```plain
[AC-01] wlan ap ap-01
[AC-01-wlan-ap-ap-01] radio 1                                # 2.4G 射频
[AC-01-wlan-ap-ap-01-radio-1] channel 6
[AC-01-wlan-ap-ap-01-radio-1] service-template 1
[AC-01-wlan-ap-ap-01-radio-1] radio enable
[AC-01-wlan-ap-ap-01-radio-1] quit

[AC-01-wlan-ap-ap-01] radio 2                                # 5G 射频
[AC-01-wlan-ap-ap-01-radio-2] channel 149
[AC-01-wlan-ap-ap-01-radio-2] service-template 1
[AC-01-wlan-ap-ap-01-radio-2] radio enable
[AC-01-wlan-ap-ap-01-radio-2] quit
```

### 12_2_3 查看与验证
```plain
<AC-01> display wlan ap all                         # AP 上线状态（State 为 R/M 表示正常）
<AC-01> display wlan ap name ap-01 verbose
<AC-01> display wlan client                         # 在线终端
<AC-01> display wlan client verbose
<AC-01> display wlan service-template
<AC-01> display wlan ap statistics
```

**状态说明**：

| State | 含义 |
| --- | --- |
| I（Idle） | 未上线 |
| R/M（Run/Master） | 正常运行 |
| DF（Downloading Firmware） | 正在下载版本 |
| JC（Join Confirm） | 正在确认加入 |

**AP 不上线的排查顺序**：

```plain
第1步 AP 是否拿到 IP？            display dhcp server ip-in-use
第2步 Option 43 配了吗？           display dhcp server ip-pool
第3步 AP 与 AC 三层可达吗？        ping AP 的管理地址
第4步 CAPWAP 端口通吗？            UDP 5246/5247（查中间 ACL）
第5步 AP 型号与序列号对吗？        display wlan ap all
第6步 AC 版本与 AP 版本匹配吗？    display version / display wlan ap verbose
```

---

## 12_3 无线安全与网络准入控制
### 12_3_1 认证方式对比
| 方式 | 安全性 | 用户体验 | 适用场景 |
| --- | --- | --- | --- |
| 开放 + Portal | 低 | 好（网页认证） | 访客网络 |
| PSK（WPA2/WPA3-Personal） | 中 | 好 | 中小企业、家庭 |
| 802.1X（WPA2/WPA3-Enterprise） | 高 | 需配客户端/证书 | 企业办公（推荐） |
| MAC 认证 | 低（MAC 可伪造） | 无感 | 打印机、摄像头等哑终端 |
| Portal + 短信/微信 | 中 | 好 | 商场、酒店 |

### 12_3_2 802.1X 认证配置（企业推荐）
```plain
# 1. 配置 RADIUS 方案
[H3C] radius scheme RADIUS-1
[H3C-radius-RADIUS-1] primary authentication 192.168.100.100
[H3C-radius-RADIUS-1] primary accounting 192.168.100.100
[H3C-radius-RADIUS-1] key authentication simple H3C@Radius
[H3C-radius-RADIUS-1] key accounting simple H3C@Radius
[H3C-radius-RADIUS-1] user-name-format without-domain
[H3C-radius-RADIUS-1] quit

# 2. 配置 ISP 域
[H3C] domain office
[H3C-isp-office] authentication lan-access radius-scheme RADIUS-1
[H3C-isp-office] authorization lan-access radius-scheme RADIUS-1
[H3C-isp-office] accounting lan-access radius-scheme RADIUS-1
[H3C-isp-office] quit

# 3. 服务模板启用 802.1X
[AC-01] wlan service-template 2 crypto
[AC-01-wlan-st-2] ssid H3C-Staff
[AC-01-wlan-st-2] vlan 210
[AC-01-wlan-st-2] akm mode dot1x
[AC-01-wlan-st-2] cipher-suite ccmp
[AC-01-wlan-st-2] security-ie rsn
[AC-01-wlan-st-2] dot1x domain office                 # 绑定认证域
[AC-01-wlan-st-2] service-template enable
```

### 12_3_3 MAC 认证（哑终端）
```plain
[H3C] mac-authentication domain office
[H3C-GigabitEthernet1/0/1] mac-authentication
```

### 12_3_4 Portal 认证（访客）
```plain
[H3C] portal server PORTAL-1 ip 192.168.100.200 key simple H3C@Portal
[H3C] portal web-server WEB-1 url http://192.168.100.200/portal
[H3C] interface Vlan-interface 220
[H3C-Vlan-interface220] portal enable method direct
[H3C-Vlan-interface220] portal server PORTAL-1
[H3C-Vlan-interface220] portal web-server WEB-1
```

### 12_3_5 验证
```plain
<H3C> display dot1x
<H3C> display dot1x sessions
<H3C> display mac-authentication
<H3C> display portal server
<H3C> display radius scheme
<H3C> display connection                          # 在线用户
```

---

## 12_4 射频规划与优化
### 12_4_1 关键参数
| 参数 | 说明 | 建议 |
| --- | --- | --- |
| 信道 | 2.4G 用 1/6/11；5G 用非重叠信道 | 相邻 AP 错开 |
| 发射功率 | 过大导致同频干扰，过小导致覆盖不足 | 按覆盖目标调整，通常 10~20 dBm |
| 信道带宽 | 20 / 40 / 80 MHz | 高密度用 20 MHz，少干扰环境可用 40/80 |
| 速率集 | 禁用低速率可提升整体性能 | 关闭 1/2/5.5 Mbps 等低速率 |
| 用户隔离 | 防止终端互访 | 访客网络必开 |

### 12_4_2 优化配置
```plain
[AC-01] wlan ap ap-01
[AC-01-wlan-ap-ap-01] radio 1
[AC-01-wlan-ap-ap-01-radio-1] channel 6
[AC-01-wlan-ap-ap-01-radio-1] max-power 15                  # 限制最大功率
[AC-01-wlan-ap-ap-01-radio-1] rate disabled 1 2 5.5          # 禁用低速率
[AC-01-wlan-ap-ap-01-radio-1] quit

# 用户隔离
[AC-01] wlan service-template 3 clear
[AC-01-wlan-st-3] ssid H3C-Guest
[AC-01-wlan-st-3] user-isolation enable                      # 终端隔离
[AC-01-wlan-st-3] service-template enable

# 5G 优先（频段引导）
[AC-01-wlan-ap-ap-01] band-navigation enable
```

### 12_4_3 自动射频优化（RRM）
```plain
[AC-01] wlan rrm
[AC-01-wlan-rrm] calibrate-channel self-decisive enable      # 自动信道调整
[AC-01-wlan-rrm] calibrate-power self-decisive enable        # 自动功率调整
```

---

## 12_5 漫游与高可靠
### 12_5_1 漫游类型
| 类型 | 说明 |
| --- | --- |
| 二层漫游 | 同一 VLAN 内，终端 IP 不变，最简单 |
| 三层漫游 | 跨 VLAN，需 AC 间隧道或集中转发保持 IP 不变 |

### 12_5_2 快速漫游优化
+ **802.11r**（快速 BSS 切换）：减少重认证时间。
+ **802.11k**（邻居报告）：帮助终端快速发现候选 AP。
+ **802.11v**（网络辅助切换）：网络侧引导终端切换。

```plain
[AC-01] wlan service-template 1
[AC-01-wlan-st-1] ft enable                        # 开启 802.11r 快速漫游
```

### 12_5_3 AC 高可靠
+ **AC 1+1 备份 / N+1 备份**：主 AC 故障时 AP 切换到备 AC。
+ **双链路备份**：AP 配置主备 AC 地址。

---

## 12_6 无线排障与验证清单
### 排障分层法（无线专用）
```plain
第1步 终端能看到 SSID 吗？      → 看不到：AP 未上线 / 射频未开 / SSID 未广播
第2步 能连上但拿不到 IP 吗？    → DHCP 问题（业务 VLAN / 中继 / 地址池）
第3步 能拿到 IP 但上不了网？    → 上行网络问题（网关 / NAT / 策略）
第4步 信号满格但网速慢？        → 同频干扰 / 低速率终端拖累 / 出口带宽
第5步 某个位置信号差？          → 覆盖盲区 / AP 功率 / 信道规划
第6步 走动时掉线？              → 漫游配置 / 切换阈值
```

### 典型故障对照表
| 现象 | 检查 | 处理 |
| --- | --- | --- |
| AP 不上线 | `display wlan ap all` | 查 Option 43、三层可达性、UDP 5246/5247 |
| 搜不到信号 | `display wlan ap verbose` | 射频是否 enable、信道是否合法 |
| 连上就掉 | `display wlan client verbose` | 查认证方式、密钥、终端兼容性 |
| 网速很慢 | `display wlan client` | 看终端速率、是否连在 2.4G、信道干扰 |
| 部分终端连不上 | 固件/驱动兼容性 | 调整加密方式、关闭 802.11r 测试 |
| 漫游掉线 | 漫游配置 | 检查 AC 间隧道、VLAN 一致性 |

### 📌 案例手记：会议室里"信号满格却开不了视频会"
现象：某大型会议室，终端显示 Wi-Fi 信号满格，但视频会议卡顿严重，speedtest 只有 2 Mbps。

排查：

1. `display wlan client verbose` —— 大量终端集中连在**同一个 AP** 的 2.4G 射频上（5G 覆盖不到该区域）。
2. 该 AP 的 2.4G 信道与隔壁 AP **同为信道 6**，同频干扰严重。
3. 大量低速率终端（老手机）占用空口时间，拖累整体性能。

优化措施：

1. 会议室新增一台 5G AP，开启 **band-steering** 引导终端走 5G。
2. 调整 2.4G 信道为 1/6/11 错开，降低发射功率避免跨区干扰。
3. 在 2.4G 射频禁用 1/2/5.5 Mbps 低速率。
4. 开启用户隔离，减少广播对空口的占用。

**结论**：**无线的瓶颈通常在空口（信道、干扰、终端分布）而不在带宽。规划比配置更重要。**

### 验证清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| AP 全部上线 | `display wlan ap all` | State 为 R/M |
| SSID 可见 | 终端扫描 | 目标 SSID 正常广播 |
| 终端能上线 | `display wlan client` | 终端获取到业务 VLAN 地址 |
| 业务可达 | ping 网关与外网 | 通 |
| 认证生效 | `display dot1x sessions` | 认证用户在线 |
| 信道合规 | `display wlan ap verbose` | 相邻 AP 信道错开 |
| 功率合理 | 现场测试 | 无跨区同频干扰 |
| 漫游正常 | 走动测试 | 不掉线、不重新认证 |
| 用户隔离生效 | 访客网互 ping | 不通 |

### 实验笔记模板
```plain
## 实验：AC + Fit AP 部署与无线优化
日期：____   设备：AC____ AP 型号____

### 1. 目标与验收
- [ ] AP 通过 Option 43 成功上线
- [ ] 两个 SSID（员工 + 访客）分别走不同业务 VLAN
- [ ] 员工 SSID 走 802.1X，访客走 Portal + 隔离

### 2. 规划表
| 项 | 值 |
| --- | --- |
| 管理 VLAN | 100 / 192.168.100.0/24 |
| 员工业务 VLAN | 210 |
| 访客业务 VLAN | 220 |
| AC 地址 | 192.168.100.1 |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：AP 拿不到地址 / 上不了线
- 假设：Option 43 错 / 三层不通 / 端口被拦 / 序列号错
- 验证：display dhcp server ip-in-use + display wlan ap all
- 结论：（记录实际原因）

### 4. 边界
- AP 型号与序列号必须与实物一致
- 自动 AP 上线后记得转固化
- 5G 优先需终端支持
- 用户隔离会影响投屏、共享类应用
```

# 板块13 · 网络运维管理：监控、日志、镜像与设备生命周期
> 本板块重构为一份"日常运维 + 生命周期管理 + 可视化监控"的完整体系。  
目标：把"救火式运维"变成"可预期、可追溯、可预防"的体系化运维。

---

## 13_1 设备信息采集与过保查询
### 13_1_1 关键采集命令
```plain
<H3C> display device manuinfo              # 查看出厂日期和序列号（过保查询用）
<H3C> display version                      # 查看设备版本与运行时长
<H3C> display device                       # 查看板卡、电源、风扇状态
<H3C> display environment                  # 温度、风扇、电源健康度
<H3C> display elabel                       # 电子标签（含序列号，部分型号）
```

### 采集示例
```plain
<H3C> display device manuinfo
Slot 1 CPU 0:
DEVICE NAME         : S5560-30C-EI
DEVICE SERIAL NUMBER: 210235A1B2C3D4E5F6G7
MANUFACTURING DATE  : 2021-05-18
VENDOR NAME         : H3C
```

### 13_1_2 过保查询
查询地址：官方服务与维保查询入口（如 `http://es.h3c.com/entitlement/`）。  
输入设备序列号（Bar Code / Serial Number）即可查询维保状态与截止时间。

### 服务状态说明
| 服务状态 | 说明 |
| --- | --- |
| 有效 | 服务开始日期早于或等于当前日期，服务结束日期大于或等于当前日期，设备可以正常享有合同所规定的服务 |
| 无效 | 服务结束日期早于当前日期，服务已经结束，设备不可享有合同所规定的服务 |
| 取消 | 由于各种原因合同被取消，不作为服务依据 |

### 设备台账模板（运维必备）
| 字段 | 示例 | 用途 |
| --- | --- | --- |
| 设备名称 | Core-SW-01 | 唯一标识 |
| 型号 | S5560-30C-EI | 备件与升级 |
| 序列号 | 210235A1B2C3D4E5F6G7 | 维保查询 |
| 生产日期 | 2021-05-18 | 生命周期判断 |
| 维保截止日 | — | 续保预警 |
| 软件版本 | Comware V7.x | 升级依据 |
| 管理 IP | 192.168.99.254 | 远程管理 |
| 物理位置 | 3 楼机房 A 柜 | 现场定位 |
| 责任人 | 张三 | 责任追溯 |
| 最近配置备份 | （日期 + 文件路径） | 变更与恢复 |

> **运维实践**：把"型号 + 序列号 + 生产日期 + 维保截止日 + 版本"做成设备台账，**维保到期前 3 个月启动续保流程**。维保过期的设备出故障时，备件与技术支持都无法及时到位，这是重大业务风险。

---

## 13_2 固件下载与升级流程
### 13_2_1 官方获取渠道
+ 官方网站的软件下载区（路由器 / 交换机 / 安全产品分类）。
+ 涉及维保设备的升级，建议通过官方技术支持或代理商获取版本与补丁，**避免用到不匹配的公版软件**。

> 下载通常需要账号权限；账号与权限政策以官网当前公布方式为准。

### 13_2_2 升级完整流程（与板块1 的 1_6 配套）
```plain
# 1. 升级前检查
<H3C> display version                                  # 确认当前版本
<H3C> dir /all                                         # 查看 Flash 空间是否足够
<H3C> save                                             # 保存配置
<H3C> tftp 192.168.1.100 put startup.cfg pre-upgrade.cfg    # 配置备份到服务器

# 2. 删除旧系统文件（空间不足时）
<H3C> delete /unreserved s3600v2_e-cmw520-r2111p02.bin

# 3. 从 FTP 下载新版本
<H3C> ftp 192.168.1.100
[ftp] get S5120LI-CMW520-R1519P06.bin
[ftp] bye

# 4. 升级 BootRom（视版本要求）
<H3C> bootrom update file S5120LI-CMW520-R1519P06.bin slot 1

# 5. 指定下次启动文件
<H3C> boot-loader file flash:/S5120LI-CMW520-R1519P06.bin slot 1 main

# 6. 清理并重启
<H3C> reset recycle-bin
<H3C> reboot

# 7. 重启后验证
<H3C> display version
<H3C> dir /all
```

### 13_2_3 升级风险控制
| 风险 | 控制措施 |
| --- | --- |
| 配置丢失 | 升级前 `save` + TFTP 导出配置 |
| 空间不足 | `dir /all` 检查 → `delete /unreserved` + `reset recycle-bin` |
| 新版本异常 | 用 `boot-loader` 命令把新版本指定为 main、旧版本保留为 backup 启动项 |
| 业务中断 | 选择业务低峰期，提前公告，准备回退方案 |
| 版本不匹配 | 通过官方渠道获取与型号、License 匹配的版本 |

---

## 13_3 运维三件套：NTP、LLDP、日志
### 13_3_1 NTP 时间同步（一切审计的前提）
```plain
[H3C] ntp-service enable
[H3C] ntp-service unicast-server 192.168.100.1
[H3C] clock timezone Beijing add 08:00:00

<H3C> display ntp-service status
<H3C> display ntp-service sessions
```

> **为什么必须先做 NTP**：日志、审计、故障回溯都依赖时间戳。没有 NTP 的设备，其日志在事件关联时基本无用。

### 13_3_2 LLDP（邻居发现，画拓扑的利器）
```plain
[H3C] lldp global enable
[H3C] interface range g1/0/1 to g1/0/48
[H3C-if-range] lldp enable
[H3C-if-range] quit

<H3C> display lldp neighbor-information list        # 邻居总览（最常用）
<H3C> display lldp neighbor-information verbose
<H3C> display lldp local-information
```

**实战价值**：

+ 快速摸清现场接线（尤其接手陌生网络时）。
+ 核对台账与实际连接是否一致。
+ 定位"这根线到底连到哪台设备的哪个口"。

### 13_3_3 日志与信息中心
```plain
[H3C] info-center enable
[H3C] info-center loghost 192.168.100.50 facility local5
[H3C] info-center source default loghost level informational
[H3C] info-center logbuffer size 1024

<H3C> display logbuffer
<H3C> display logbuffer | exclude INFO                # 只看非 INFO 日志
<H3C> display info-center
```

**日志分级**：

| 级别 | 说明 |
| --- | --- |
| emergencies | 系统不可用 |
| alerts | 必须立即处理 |
| critical | 严重 |
| errors | 错误 |
| warnings | 警告 |
| notifications | 通知（正常但重要） |
| informational | 一般信息 |
| debugging | 调试 |

---

## 13_4 端口镜像与 Telemetry
### 13_4_1 本地镜像（已在板块3 出现，此处补运维视角）
```plain
[H3C] mirroring-group 1 local
[H3C] mirroring-group 1 mirroring-port g1/0/1 both
[H3C] mirroring-group 1 monitor-port g1/0/24
```

### 13_4_2 NetStream / NetFlow（流量分析）
```plain
[H3C] sampler 1 mode random packet-interval 100      # 采样
[H3C] ip netstream export source interface Vlan-interface 99
[H3C] ip netstream export host 192.168.100.60 9996
[H3C] interface GigabitEthernet 1/0/24
[H3C-GigabitEthernet1/0/24] ip netstream inbound
[H3C-GigabitEthernet1/0/24] ip netstream outbound

<H3C> display ip netstream statistics
<H3C> display ip netstream cache
```

**用途**：看清"谁在跑流量、跑的是什么、走了哪条路"，用于容量规划与异常流量定位。

### 13_4_3 Telemetry（新一代监控）
Telemetry 是**主动推送**的监控方式（相比 SNMP 轮询），秒级甚至亚秒级采集，适合大规模网络与自动化运维。

```plain
[H3C] telemetry
[H3C-telemetry] subscription 1
[H3C-telemetry-subscription-1] sensor-group SG1 sample-interval 10
[H3C-telemetry-subscription-1] destination-group DG1
[H3C-telemetry-subscription-1] quit
```

**对比**：

| 方式 | 采集方式 | 精度 | 适用 |
| --- | --- | --- | --- |
| SNMP | 轮询（拉） | 分钟级 | 传统监控 |
| NetStream | 流采样 | 流级别 | 流量分析 |
| Telemetry | 主动推送（推） | 秒/亚秒级 | 大规模、精细运维 |

---

## 13_5 批量运维与自动化
### 13_5_1 批量备份配置（脚本思路）
```bash
#!/bin/bash
# 批量备份脚本示例：从设备列表读取 IP，通过 TFTP 拉取配置
DEVICES="192.168.99.1 192.168.99.11 192.168.99.12"
DATE=$(date +%Y%m%d)

for IP in $DEVICES; do
    echo "备份 $IP ..."
    # 实际环境中用 expect/telnetlib/paramiko 登录设备执行：
    # tftp <server> put startup.cfg ${IP}-${DATE}.cfg
done
```

### 13_5_2 批量检查（Python + SSH 思路）
```python
# 批量执行 display 命令并保存输出（示意）
# pip install paramiko
import paramiko, datetime

devices = ["192.168.99.1", "192.168.99.11"]
commands = ["display version", "display interface brief", "display cpu-usage"]

for ip in devices:
    ssh = paramiko.SSHClient()
    ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    ssh.connect(ip, username="opsuser", password="xxx")
    shell = ssh.invoke_shell()
    for cmd in commands:
        shell.send(cmd + "\n")
        # 读取输出并写入文件
    ssh.close()
```

> **运维纪律**：批量脚本先在**一台设备上验证**，确认无误再全网执行；批量变更必须分批进行，留出观察窗口。

### 13_5_3 配置合规检查清单
| 检查项 | 命令 | 频率 |
| --- | --- | --- |
| 版本与补丁 | `display version` | 季度 |
| 配置是否保存 | `compare configuration` | 每次变更后 |
| CPU / 内存 | `display cpu-usage`、`display memory` | 周 |
| 端口错误计数 | `display interface` | 周 |
| 温度 / 电源 / 风扇 | `display environment` | 月 |
| 日志异常 | `display logbuffer` | 周 |
| 配置备份 | `tftp put startup.cfg` | 月 + 每次变更 |
| 维保状态 | 官方查询 | 季度 |
| 账号审计 | `display local-user` | 季度 |

---

## 13_6 设备生命周期管理
### 生命周期阶段与动作
| 阶段 | 关键动作 | 关注点 |
| --- | --- | --- |
| 入网 | 台账登记、模板配置、命名规范、NTP/日志 | 不裸机上线 |
| 运行 | 定期巡检、配置备份、版本管理 | 变更留痕 |
| 维保 | 续保预警、备件准备 | 到期前 3 个月启动 |
| 退役 | 数据清除（`restore default`）、资产核销 | 配置与账号彻底清除 |

### 巡检清单（月度）
```plain
□ 设备台账是否与现网一致（用 LLDP 核对接线）
□ 所有设备 CPU / 内存是否在正常区间
□ 端口错误计数是否有增长
□ 温度、风扇、电源状态是否正常
□ 配置是否都已保存（compare configuration）
□ 配置备份是否完成并归档
□ 日志有无异常重启、端口抖动、安全事件
□ 账号是否有多余或长期未登录
□ 维保状态是否有即将到期设备
□ License 是否即将到期
```

### 📌 案例手记：台账不准，一次割接差点翻车
某核心交换机升级，工程师按台账判断"GE1/0/24 是上联口，割接时断这里没问题"。

结果断掉后，半个园区网中断——**GE1/0/24 实际接的是汇聚交换机**，台账是三年前画的，中间改过线没更新。

应急：立即恢复连接，改用 LLDP 重新摸清实际拓扑：

```plain
<H3C> display lldp neighbor-information list
```

确认真实上联口后重新规划割接窗口，第二次成功。

**沉淀规范**：

1. **重大变更前必须用 LLDP 核对实际接线**，不能只信台账。
2. 每次接线变更后**同步更新台账**。
3. 割接窗口内准备"回退线"——保留原线缆不拆，可在 5 分钟内恢复。

---

## 13_7 实验笔记模板与验收清单
### 笔记模板
```plain
## 实验：运维体系搭建（NTP + LLDP + 日志 + 备份）
日期：____   设备：____

### 1. 目标与验收
- [ ] 所有设备 NTP 同步，时间一致
- [ ] 用 LLDP 画出实际拓扑并与台账对比
- [ ] 日志外送成功，服务器能收到
- [ ] 批量备份脚本跑通

### 2. 台账核对结果
| 设备 | 台账记录上联 | LLDP 实际对端 | 是否一致 |
| --- | --- | --- | --- |

### 3. 现象 → 假设 → 验证 → 结论
- 现象：日志服务器收不到日志
- 假设：loghost 地址错 / 路由不通 / 防火墙拦截 / info-center 未开
- 验证：display info-center + 服务器侧抓包
- 结论：（记录实际原因）

### 4. 边界
- NTP 时区必须设置，否则差 8 小时
- LLDP 两端都要开启才能看到邻居
- 批量脚本先单机验证
```

### 验收清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| 时间同步 | `display ntp-service status` | 已同步，时区正确 |
| 邻居可见 | `display lldp neighbor-information list` | 能看到对端设备与端口 |
| 日志外送 | 服务器端验证 | 能收到设备日志 |
| 配置备份 | `dir /all` + 服务器目录 | 本地与远端各一份 |
| 硬件健康 | `display environment` | 温度、风扇、电源正常 |
| 资源正常 | `display cpu-usage`、`display memory` | 在阈值内 |
| 台账准确 | 台账 vs LLDP | 一致 |
| 维保可控 | 官方查询 | 无临期未处理设备 |

# 板块14 · 网络故障排查方法论与综合排错实验
> 本板块是 H3CIE-RS+ 实验室考试（HL0-202，限定时间真机排障）的核心训练内容，也是区分"会配命令"与"能解决问题"的分水岭。  
核心纪律：**单点修改、逐项验证。**

---

## 14_1 排障方法论：三种模型
### 14_1_1 分层法（最常用）
按 OSI 模型自下而上或自上而下逐层排除：

| 层级 | 检查内容 | 关键命令 |
| --- | --- | --- |
| 物理层 | 线缆、模块、光功率、端口 UP/DOWN | `display interface brief`、`display transceiver diagnosis` |
| 数据链路层 | VLAN、Trunk、MAC 表、STP | `display vlan`、`display mac-address`、`display stp brief` |
| 网络层 | IP 地址、路由表、ARP | `display ip interface brief`、`display ip routing-table`、`display arp` |
| 传输 / 应用层 | 端口、ACL、NAT、防火墙策略 | `display acl`、`display nat session`、`display security-policy statistics` |

**选择方向的经验**：

+ **自下而上**：适用于"完全不通"的故障（先确认灯亮不亮）。
+ **自上而下**：适用于"能 ping 通但业务不可用"（先确认应用，再看是否被策略拦截）。
+ **分而治之（二分法）**：沿流量路径取中点测试，一次排除一半，适用于长链路。

### 14_1_2 对比法
找一台"正常的"设备 / 端口 / 用户，与故障对象逐项对比配置：

```plain
<H3C> display current-configuration interface g1/0/1     # 故障口
<H3C> display current-configuration interface g1/0/2     # 正常口
# 逐行 diff，差异点就是嫌疑点
```

### 14_1_3 替换法
用确定正常的部件替代可疑部件（网线、模块、端口、设备），逐步收敛。  
**注意：一次只改一个变量**，否则无法确定根因。

### 14_1_4 排障五步流程（建议固化成习惯）
```plain
1. 收集现象：谁、什么时候、访问什么、用什么方式、报错是什么
2. 确定范围：单台终端？单 VLAN？单栋楼？全网？
3. 定位层次：分层法确定故障在哪一层
4. 定位点  ：用 display 命令缩小到具体设备 / 端口 / 配置
5. 验证修复：修改后必须验证，并确认无副作用，最后保存 + 记录
```

> **IE 实验的核心纪律**：一次改一堆配置，改完即使通了也不知道是哪个生效的，写排错报告时无法自圆其说，会被扣分。

---

## 14_2 诊断命令工具箱
### 14_2_1 连通性测试
```plain
<H3C> ping 192.168.1.1
<H3C> ping -a 192.168.10.1 192.168.20.1        # 指定源地址（最重要！）
<H3C> ping -c 10 -s 1472 192.168.1.1           # 指定次数与包大小（测 MTU）
<H3C> tracert 192.168.2.1
<H3C> tracert -a 192.168.10.1 192.168.2.1
```

> `-a` 参数是最容易被忽略但最重要的技巧：不带源地址 ping 时，设备用**出接口地址**作源，可能掩盖回程路由问题。用 `-a` 指定内网地址，才能真实模拟业务流量。

### 14_2_2 信息查看与过滤
```plain
<H3C> display interface brief | include DOWN               # 快速找出 DOWN 端口
<H3C> display current-configuration | begin user-interface # 从某处开始看
<H3C> display current-configuration | include vlan         # 过滤关键字
<H3C> display ip routing-table 192.168.2.10                # 查看特定目的路由
<H3C> display arp | include 192.168.1.10                   # 查 ARP 表项
<H3C> display mac-address | include 00e0                   # 查 MAC 表项
<H3C> display logbuffer | exclude INFO                     # 只看非 INFO 日志
```

### 14_2_3 实时诊断
```plain
<H3C> terminal monitor                # 开启日志实时显示（远程登录时默认关闭）
<H3C> terminal debugging
<H3C> debugging ospf event            # 调试 OSPF 事件
<H3C> undo debugging all              # 关闭所有调试（务必记得！）

<H3C> display cpu-usage               # CPU（环路、攻击时会飙升）
<H3C> display memory
<H3C> reset counters interface g1/0/1 # 清零统计后观察增量
```

> **调试命令警告**：`debugging` 会大量消耗 CPU，生产环境慎用；用完必须 `undo debugging all`。在 IE 实验中，不必要的 debugging 可能导致设备卡顿，反而浪费时间。

### 14_2_4 抓包
```plain
# 本地镜像抓包
[H3C] mirroring-group 1 local
[H3C] mirroring-group 1 mirroring-port g1/0/1 both
[H3C] mirroring-group 1 monitor-port g1/0/24

# 设备自带抓包（V7 支持，快速验证流量是否到达）
<H3C> packet-capture interface g1/0/1 inbound
```

---

## 14_3 分层排查手册
### 14_3_1 物理层故障
| 现象 | 检查 | 处理 |
| --- | --- | --- |
| 端口 DOWN | `display interface brief` | 换线、换模块、查对端 |
| 一端 UP 一端 DOWN | `display dldp` | 单向链路，检查光纤收发、开 DLDP |
| CRC 持续增长 | `display interface` | 换线、查光衰 |
| 端口频繁 UP/DOWN | `display logbuffer` | 线缆接触不良、模块故障、光衰过大 |
| 光功率异常 | `display transceiver diagnosis` | 换模块、清洁光纤接头 |

### 14_3_2 二层故障
| 现象 | 检查 | 处理 |
| --- | --- | --- |
| 同网段不通 | `display vlan`、`display mac-address` | 核对 VLAN 与端口类型 |
| 跨设备同 VLAN 不通 | `display port trunk` | Trunk 未 permit 该 VLAN |
| 全网慢 / 丢包（疑似环路） | `display cpu-usage`、`display stp brief` | 查环路，开 STP 与环路检测 |
| MAC 表震荡 | `display mac-address mac-move` | 查环路或 MAC 漂移攻击 |
| 广播风暴 | `display interface`（广播计数） | 查环路、开风暴抑制 |

### 14_3_3 三层故障
| 现象 | 检查 | 处理 |
| --- | --- | --- |
| 有直连但 ping 不通网关 | `display arp` | ARP 未解析，查二层 |
| 路由表中无条目 | `display ip routing-table` | 检查路由协议邻居、静态路由下一跳 |
| OSPF 邻居起不来 | `display ospf error` | 对照板块7 的十大原因 |
| 能去不能回 | `ping -a` 指定源测试 | 对端缺回程路由 |
| 能 ping 通但打不开网页 | DNS / ACL / MTU | 查 DNS、ACL、MSS |
| 路由不优（次优路径） | `display ip routing-table verbose` | 查路由策略与引入 |

### 14_3_4 应用层故障
| 现象 | 检查 | 处理 |
| --- | --- | --- |
| 网页打不开但 ping 通 | DNS 解析 | `display dns server`、终端 nslookup |
| 部分网站打不开 | MTU / MSS | 出口配 `tcp mss 1452` |
| 特定端口不通 | ACL / 防火墙策略 | `display security-policy statistics` |
| 某业务时断时续 | 会话数、NAT 老化、链路质量 | `display nat session`、抓包 |

---

## 14_4 典型场景库（排障训练用）
### 场景 1：终端拿不到 IP 地址
```plain
排查链：
第1步 终端网卡是否启用是否设置为自动获取
第2步 交换机端口是否 UP、VLAN 是否正确          display interface brief / display vlan
第3步 DHCP 是否开启                              display dhcp server / display dhcp relay
第4步 地址池是否耗尽                              display dhcp server ip-in-use
第5步 是否配了中继、中继地址是否正确              display dhcp relay
第6步 DHCP Snooping 是否把响应丢了                display dhcp snooping trust
第7步 抓包：Discover 是否发出、Offer 是否回来
```

### 场景 2：能上网但访问内网服务器不通
```plain
排查链：
第1步 同网段能通吗？（判断二层还是三层）
第2步 ping 网关通吗？
第3步 tracert 看断在哪一跳
第4步 服务器侧是否有回程路由？                    display ip routing-table（服务器网关侧）
第5步 中间是否有 ACL？                            display packet-filter statistics
第6步 防火墙策略是否放行？                        display security-policy statistics
第7步 服务器自身防火墙？
```

### 场景 3：全网变慢，疑似环路
```plain
排查链：
第1步 display cpu-usage（是否飙升）
第2步 display mac-address mac-move（是否有漂移）
第3步 display stp brief（角色是否异常）
第4步 display interface（广播包是否暴涨）
第5步 逐段拔线定位（在可疑交换机上）
第6步 找到后：拔掉环路 + 开启 STP + 配置边缘端口与 BPDU 保护
```

### 场景 4：OSPF 邻居起不来
```plain
排查链：
第1步 display interface brief（接口 UP 吗）
第2步 ping 直连地址（二层/三层可达吗）
第3步 display ospf interface（区域、网络类型、Hello/Dead、认证）
第4步 display ospf error（MTU、认证等错误计数）
第5步 display ospf peer（卡在哪个状态）
第6步 对照十大原因逐项排查
```

### 场景 5：VPN 隧道建立后业务不通
```plain
排查链：
第1步 display ike sa / display ipsec sa（阶段一/二是否正常）
第2步 两端 ACL（感兴趣流）是否镜像对称
第3步 是否触发了感兴趣流（用 ping -a 触发）
第4步 内网路由是否指向隧道
第5步 NAT 是否把 VPN 流量也转换了（需排除）
第6步 MTU/MSS 是否导致大包不通
```

### 📌 案例手记：一个"不可能"的故障——能 ping 通网关，却 ping 不通网关上的另一个地址
现象：终端 192.168.10.10 能 ping 通网关 192.168.10.1，但 ping 不通同设备上的管理地址 192.168.99.254。

排查：

1. `display ip interface brief` —— 两个地址都在，接口都 UP。
2. `display acl all` —— 发现 Vlan-interface 10 上挂了一条 ACL，把去往管理网段的流量 deny 了。
3. 该 ACL 是上次安全整改时加的，"防止业务网段访问管理网段"，但**误伤了设备管理地址**。

修复：在 ACL 中放行必要的管理访问（如只允许运维主机访问管理地址），其余仍然拒绝。

**教训**：**排障时不要只盯着"不通的两端"，要看中间的每一个环节（ACL、策略、路由、NAT）。** 用"分段测试 + 二分法"能快速缩小范围。

---

## 14_5 排错报告模板（IE 面试与项目交付用）
```plain
## 网络故障排查报告

### 一、故障概述
- 故障时间：____ 至 ____
- 影响范围：____（终端数 / 业务系统 / 区域）
- 故障现象：（用户视角的准确描述，含报错原文）

### 二、网络环境
- 拓扑图：（ASCII 或图）
- 关键设备与版本：
- 相关配置：（故障点前后的关键配置片段）

### 三、排查过程（核心，体现方法论）
| 步骤 | 动作 | 命令 | 观察结果 | 结论 |
| --- | --- | --- | --- | --- |
| 1 | 确认范围 | ping / 用户反馈 | 单 VLAN 不通 | 定位在三层 |
| 2 | 查 ARP | display arp | 无表项 | 二层或 ARP 问题 |
| 3 | 查 Trunk | display port trunk | 未 permit VLAN 30 | **根因** |

### 四、根因分析
（用一句话说清根因 + 为什么会这样）

### 五、处理措施
（改了什么，改之前/之后的状态对比）

### 六、验证结果
（用什么命令验证，结果如何；有无副作用）

### 七、改进建议
- 技术层面：（如开启 STP、配置保护机制）
- 流程层面：（如变更需核对台账、配置需双人复核）
- 监控层面：（如增加 XX 告警）
```

**报告写作要点**：

1. **有证据链**：每个结论都要有 `display` 输出支撑。
2. **有逻辑**：按"现象 → 假设 → 验证 → 结论"组织。
3. **有边界**：说明影响范围与临时规避方案。
4. **有改进**：不只修好，还要防止再犯。

---

## 14_6 实验考试四阶段训练法
### 阶段一：基础命令自动化（1~2 周）
目标：**不看文档能在 30 秒内敲出任何 display 命令**。

训练方式：

```plain
每天 15 分钟，随机抽取 10 个场景，限时写出对应命令：
- 看端口状态 → display interface brief
- 看 VLAN 成员 → display vlan 10
- 看 MAC 漂移 → display mac-address mac-move
- 看 STP 角色 → display stp brief
- 看路由表 → display ip routing-table
- 看 ARP 表项 → display arp
- 看 OSPF 邻居 → display ospf peer
- 看聚合组 → display link-aggregation verbose
- 看 VRRP 状态 → display vrrp
- 看 ACL 命中 → display packet-filter statistics
- 看 NAT 会话 → display nat session
- 看日志 → display logbuffer
- 看 CPU/内存 → display cpu-usage / display memory
```

### 阶段二：单点故障速排（2~4 周）
目标：**每个典型故障能在 5 分钟内定位**。

训练方式：在 HCL 中人为注入单点故障，自己计时排查：

| 注入故障 | 预期定位时间 |
| --- | --- |
| 端口 shutdown | 1 分钟 |
| Trunk 未 permit VLAN | 3 分钟 |
| OSPF 区域号错 | 3 分钟 |
| ACL 拦截 | 5 分钟 |
| DHCP 中继地址错 | 5 分钟 |
| STP 阻塞 | 5 分钟 |

### 阶段三：多故障综合（2~3 个月）
目标：**在多个故障并存时不慌乱**。

训练方式：一次注入 3~5 个不同层次的故障，按五步流程逐个击破，**每修一个就验证一个**。

### 阶段四：全真模拟 + 报告（1~2 个月）
目标：**限时完成 + 规范输出**。

训练方式：

```plain
1. 搭建完整拓扑（含 VLAN、路由、出口、无线）
2. 限时完成配置
3. 人为注入故障
4. 限时排查并修复
5. 写完整排错报告（用 14_5 模板）
6. 复盘：哪些地方慢了？为什么？
```

### 时间管理建议（以 6 小时实验为例）
| 阶段 | 时间分配 | 说明 |
| --- | --- | --- |
| 读题与规划 | 30 分钟 | 看清需求，画出检查表 |
| 故障定位 | 3 小时 | 按层次逐个定位 |
| 修复与验证 | 1.5 小时 | 单点修改、逐项验证 |
| 报告撰写 | 45 分钟 | 边做边记录，不要最后才写 |
| 复查与保存 | 15 分钟 | 确认所有配置已保存 |

> **关键习惯**：**边做边记**（记录每条命令与输出），不要等全部做完再回忆——考试结束前根本想不起来细节。

---

## 14_7 本板块验收清单
| 验收项 | 方法 | 达标标准 |
| --- | --- | --- |
| 掌握三种排障模型 | 复述 + 应用 | 能说出各自适用场景 |
| 熟练五步流程 | 模拟排障 | 每次都能按流程走 |
| 命令工具箱熟练 | 随机抽测 | 30 秒内写出对应命令 |
| 场景库能独立复现 | 实验 | 5 类场景各排一遍 |
| 报告规范 | 写一份完整报告 | 含证据链、根因、改进建议 |
| 时间管理 | 全真模拟 | 在限定时间内完成 |

# 板块15 · 综合实战：从中小企业网到大型园区网（含项目交付与面试）
> 本板块是整份知识库的"收敛层"：把前 14 个板块的技术点组装成三个可交付的完整方案，并补齐工程师最容易缺失的两项能力——**项目实施与割接**与**技术方案表达**。  
对应 H3CNE 综合实验、H3CSE 园区网设计、H3CIE 技术面试三大场景。

---

## 15_1 综合实验一：中小企业单核心组网（NE 级别）
### 15_1_1 ASCII 拓扑
```plain
                        [Internet]
                             |
                             |  GE0/0 (PPPoE/专线)
                       +-----+------+
                       | MSR Router |  192.168.99.1
                       +-----+------+
                             |  10.0.0.1/30 ←→ 10.0.0.2/30
                             |
                    GE1/0/24 |
                       +-----+--------+
                       |  Core-SW-01  |  192.168.99.254
                       |  (三层核心)   |
                       +--+---------+--+
                          |         |
                    GE1/0/1      GE1/0/2
                       (Trunk)    (Trunk)
                          |         |
                  +-------+--+   +--+-------+
                  | ACC-SW-A |   | ACC-SW-B |
                  | 192.168.99.11 | .99.12  |
                  +---+----+--+   +---+----++
                      |    |          |    |
                    PC   PC         PC   AP

  业务 VLAN：10 办公 / 20 财务 / 30 监控 / 40 无线 / 99 管理
```

### 15_1_2 需求分析
| 需求 | 实现方式 |
| --- | --- |
| 部门隔离 | VLAN10（办公）、VLAN20（财务）、VLAN30（监控）、VLAN99（管理） |
| 部门间受限互访 | 三层互通 + ACL（财务网段禁止办公访问） |
| 自动分配地址 | 核心做 DHCP 服务器（每 VLAN 一个地址池） |
| 上网 | 出口 NAT（Easy IP）+ 默认路由 |
| 远程管理 | SSH + ACL 限制运维网段 |
| 无线覆盖 | AC 管理 AP，独立 SSID 与业务 VLAN40 |

### 15_1_3 规划表（项目交付必须先行输出）
**VLAN 与地址规划**

| VLAN ID | 名称 | 网段 | 网关 | 用途 | 端口范围 |
| --- | --- | --- | --- | --- | --- |
| 10 | Office | 192.168.10.0/24 | 192.168.10.1 | 办公有线 | GE1/0/1-8 |
| 20 | Finance | 192.168.20.0/24 | 192.168.20.1 | 财务 | GE1/0/9-12 |
| 30 | Camera | 192.168.30.0/24 | 192.168.30.1 | 视频监控 | GE1/0/13-20 |
| 40 | Wireless | 192.168.40.0/24 | 192.168.40.1 | 无线 | 动态 |
| 99 | Mgmt | 192.168.99.0/24 | 192.168.99.1 | 设备管理 | 各设备管理地址 |

**设备管理地址**

| 设备 | 管理 IP | 说明 |
| --- | --- | --- |
| Core-SW-01 | 192.168.99.254 | 核心，同时是各业务网关 |
| ACC-SW-A | 192.168.99.11 | 接入 A |
| ACC-SW-B | 192.168.99.12 | 接入 B |
| MSR-Router | 192.168.99.1 | 出口路由器 |

### 15_1_4 核心交换机配置（完整）
```plain
<H3C> system-view
[H3C] sysname Core-SW-01

# ===== 1. 创建 VLAN =====
[Core-SW-01] vlan 10
[Core-SW-01-vlan10] name Office
[Core-SW-01-vlan10] quit
[Core-SW-01] vlan 20
[Core-SW-01-vlan20] name Finance
[Core-SW-01-vlan20] quit
[Core-SW-01] vlan 30
[Core-SW-01-vlan30] name Camera
[Core-SW-01-vlan30] quit
[Core-SW-01] vlan 40
[Core-SW-01-vlan40] name Wireless
[Core-SW-01-vlan40] quit
[Core-SW-01] vlan 99
[Core-SW-01-vlan99] name Mgmt
[Core-SW-01-vlan99] quit

# ===== 2. 三层网关接口 =====
[Core-SW-01] interface Vlan-interface 10
[Core-SW-01-Vlan-interface10] ip address 192.168.10.1 24
[Core-SW-01-Vlan-interface10] quit
[Core-SW-01] interface Vlan-interface 20
[Core-SW-01-Vlan-interface20] ip address 192.168.20.1 24
[Core-SW-01-Vlan-interface20] quit
[Core-SW-01] interface Vlan-interface 30
[Core-SW-01-Vlan-interface30] ip address 192.168.30.1 24
[Core-SW-01-Vlan-interface30] quit
[Core-SW-01] interface Vlan-interface 40
[Core-SW-01-Vlan-interface40] ip address 192.168.40.1 24
[Core-SW-01-Vlan-interface40] quit
[Core-SW-01] interface Vlan-interface 99
[Core-SW-01-Vlan-interface99] ip address 192.168.99.254 24
[Core-SW-01-Vlan-interface99] quit

# ===== 3. 下行 Trunk（接接入交换机）=====
[Core-SW-01] interface GigabitEthernet 1/0/1
[Core-SW-01-GigabitEthernet1/0/1] description TO-ACC-SW-A
[Core-SW-01-GigabitEthernet1/0/1] port link-type trunk
[Core-SW-01-GigabitEthernet1/0/1] port trunk permit vlan 10 20 30 40 99
[Core-SW-01-GigabitEthernet1/0/1] undo port trunk permit vlan 1
[Core-SW-01-GigabitEthernet1/0/1] quit

[Core-SW-01] interface GigabitEthernet 1/0/2
[Core-SW-01-GigabitEthernet1/0/2] description TO-ACC-SW-B
[Core-SW-01-GigabitEthernet1/0/2] port link-type trunk
[Core-SW-01-GigabitEthernet1/0/2] port trunk permit vlan 10 20 30 40 99
[Core-SW-01-GigabitEthernet1/0/2] undo port trunk permit vlan 1
[Core-SW-01-GigabitEthernet1/0/2] quit

# ===== 4. 上行三层口（接出口路由器）=====
[Core-SW-01] interface GigabitEthernet 1/0/24
[Core-SW-01-GigabitEthernet1/0/24] description TO-MSR-Router
[Core-SW-01-GigabitEthernet1/0/24] port link-mode route
[Core-SW-01-GigabitEthernet1/0/24] ip address 10.0.0.1 30
[Core-SW-01-GigabitEthernet1/0/24] quit

# ===== 5. 默认路由指向出口 =====
[Core-SW-01] ip route-static 0.0.0.0 0.0.0.0 10.0.0.2

# ===== 6. DHCP 服务 =====
[Core-SW-01] dhcp enable
[Core-SW-01] dhcp server forbidden-ip 192.168.10.1
[Core-SW-01] dhcp server ip-pool Office
[Core-SW-01-dhcp-pool-office] network 192.168.10.0 mask 255.255.255.0
[Core-SW-01-dhcp-pool-office] gateway-list 192.168.10.1
[Core-SW-01-dhcp-pool-office] dns-list 223.5.5.5 114.114.114.114
[Core-SW-01-dhcp-pool-office] quit
# （VLAN 20/30/40 同理各建一个地址池）

# ===== 7. 二层防护 =====
[Core-SW-01] dhcp snooping enable
[Core-SW-01] vlan 10
[Core-SW-01-vlan10] dhcp snooping enable
[Core-SW-01-vlan10] quit

# ===== 8. SSH 远程管理 =====
[Core-SW-01] public-key local create rsa
[Core-SW-01] ssh server enable
[Core-SW-01] local-user sysadmin class manage
[Core-SW-01-luser-manage-sysadmin] password cipher Admin@2024!SSH
[Core-SW-01-luser-manage-sysadmin] service-type ssh
[Core-SW-01-luser-manage-sysadmin] authorization-attribute user-role network-admin
[Core-SW-01-luser-manage-sysadmin] quit
[Core-SW-01] user-interface vty 0 4
[Core-SW-01-ui-vty0-4] authentication-mode scheme
[Core-SW-01-ui-vty0-4] protocol inbound ssh
[Core-SW-01-ui-vty0-4] idle-timeout 20 0
[Core-SW-01-ui-vty0-4] quit
[Core-SW-01] undo telnet server enable

# ===== 9. 部门间隔离（财务禁止被办公访问）=====
[Core-SW-01] acl advanced 3000
[Core-SW-01-acl-ipv4-adv-3000] rule 5 deny ip source 192.168.10.0 0.0.0.255 destination 192.168.20.0 0.0.0.255
[Core-SW-01-acl-ipv4-adv-3000] rule 10 permit ip
[Core-SW-01-acl-ipv4-adv-3000] quit
[Core-SW-01] interface Vlan-interface 10
[Core-SW-01-Vlan-interface10] packet-filter 3000 inbound
[Core-SW-01-Vlan-interface10] quit

# ===== 10. NTP 与日志 =====
[Core-SW-01] ntp-service enable
[Core-SW-01] ntp-service unicast-server 192.168.99.1
[Core-SW-01] info-center enable
[Core-SW-01] info-center loghost 192.168.99.50

[Core-SW-01] save force
```

### 15_1_5 接入交换机配置
```plain
<H3C> system-view
[H3C] sysname ACC-SW-A
[ACC-SW-A] vlan 10
[ACC-SW-A-vlan10] quit
[ACC-SW-A] vlan 20
[ACC-SW-A-vlan20] quit
[ACC-SW-A] vlan 99
[ACC-SW-A-vlan99] quit

# 上联口
[ACC-SW-A] interface GigabitEthernet 1/0/24
[ACC-SW-A-GigabitEthernet1/0/24] description TO-Core-SW-01
[ACC-SW-A-GigabitEthernet1/0/24] port link-type trunk
[ACC-SW-A-GigabitEthernet1/0/24] port trunk permit vlan 10 20 30 40 99
[ACC-SW-A-GigabitEthernet1/0/24] undo port trunk permit vlan 1
[ACC-SW-A-GigabitEthernet1/0/24] dhcp snooping trust
[ACC-SW-A-GigabitEthernet1/0/24] quit

# 接入端口批量
[ACC-SW-A] interface range g1/0/1 to g1/0/8
[ACC-SW-A-if-range] description TO-Office-PC
[ACC-SW-A-if-range] port link-type access
[ACC-SW-A-if-range] port access vlan 10
[ACC-SW-A-if-range] stp edged-port enable
[ACC-SW-A-if-range] dhcp snooping binding record
[ACC-SW-A-if-range] quit

[ACC-SW-A] interface range g1/0/9 to g1/0/12
[ACC-SW-A-if-range] description TO-Finance-PC
[ACC-SW-A-if-range] port link-type access
[ACC-SW-A-if-range] port access vlan 20
[ACC-SW-A-if-range] stp edged-port enable
[ACC-SW-A-if-range] quit

# 闲置端口关闭
[ACC-SW-A] interface range g1/0/13 to g1/0/23
[ACC-SW-A-if-range] description UNUSED
[ACC-SW-A-if-range] shutdown
[ACC-SW-A-if-range] quit

# 管理地址与网关
[ACC-SW-A] interface Vlan-interface 99
[ACC-SW-A-Vlan-interface99] ip address 192.168.99.11 24
[ACC-SW-A-Vlan-interface99] quit
[ACC-SW-A] ip route-static 0.0.0.0 0.0.0.0 192.168.99.254

# 生成树
[ACC-SW-A] stp enable
[ACC-SW-A] stp mode rstp
[ACC-SW-A] stp bpdu-protection

[ACC-SW-A] save force
```

### 15_1_6 出口路由器配置
```plain
<H3C> system-view
[H3C] sysname MSR-Router

# 内网口
[MSR-Router] interface GigabitEthernet 0/1
[MSR-Router-GigabitEthernet0/1] ip address 10.0.0.2 30
[MSR-Router-GigabitEthernet0/1] quit

# 回程路由（内网网段）
[MSR-Router] ip route-static 192.168.0.0 255.255.0.0 10.0.0.1

# 出向 NAT（Easy IP）
[MSR-Router] acl basic 2000
[MSR-Router-acl-ipv4-basic-2000] rule 5 permit source 192.168.0.0 0.0.255.255
[MSR-Router-acl-ipv4-basic-2000] quit
[MSR-Router] interface GigabitEthernet 0/0
[MSR-Router-GigabitEthernet0/0] ip address 211.x.x.2 30
[MSR-Router-GigabitEthernet0/0] nat outbound 2000
[MSR-Router-GigabitEthernet0/0] tcp mss 1452
[MSR-Router-GigabitEthernet0/0] quit

# 默认路由
[MSR-Router] ip route-static 0.0.0.0 0.0.0.0 211.x.x.1

[MSR-Router] save force
```

### 15_1_7 验收清单
| 验收项 | 命令 / 方法 | 达标标准 |
| --- | --- | --- |
| VLAN 与网关 | `display ip interface brief` | 各 Vlan-interface UP，IP 正确 |
| Trunk 正确 | `display port trunk` | permit 列表精确，已 undo vlan 1 |
| DHCP 下发 | 终端 ipconfig | 拿到对应网段地址、网关、DNS |
| 跨网段互通 | ping | 办公与监控互通，办公访问财务被拒 |
| 上网 | ping 公网 DNS、开网页 | 通 |
| 远程管理 | SSH 登录 | 成功，Telnet 已关闭 |
| 二层防护 | 私接路由器测试 | 无法分配地址 |
| 配置已保存 | `compare configuration` | 无差异 |

---

## 15_2 综合实验二：双核心园区网（SE 级别）
### 15_2_1 设计要点
```plain
                    [出口防火墙] ── [Internet]
                       |      |
                 [Core-A]  ══IRF/聚合══ [Core-B]
                    |   ╲        ╱   |
                    |     ╲    ╱     |
              [ACC-1]  [ACC-2]  [ACC-3]  [ACC-4]
                 (双上行链路聚合到双核心)
```

**关键设计决策**：

| 决策点 | 方案 | 理由 |
| --- | --- | --- |
| 核心冗余方式 | IRF（推荐）或 M-LAG | IRF 简化管理；金融等零中断场景用 M-LAG |
| 网关冗余 | IRF 场景天然统一；非 IRF 场景用 VRRP | 避免单点 |
| 上行带宽 | 链路聚合（动态 LACP） | 带宽叠加 + 冗余 |
| 生成树 | MSTP 多实例 | 负载分担，避免链路闲置 |
| 路由 | 核心与出口间跑 OSPF | 便于扩展与故障收敛 |
| 管理 | 独立管理 VLAN + SSH + 堡垒机 | 符合等保 |

### 15_2_2 关键配置片段
```plain
# ===== 核心 MSTP 负载分担 =====
[Core-A] stp region-configuration
[Core-A-mst-region] region-name Campus
[Core-A-mst-region] revision-level 1
[Core-A-mst-region] instance 1 vlan 10 20
[Core-A-mst-region] instance 2 vlan 30 40
[Core-A-mst-region] active region-configuration
[Core-A-mst-region] quit
[Core-A] stp enable
[Core-A] stp mode mstp
[Core-A] stp instance 1 root primary
[Core-A] stp instance 2 root secondary

[Core-B] stp instance 1 root secondary
[Core-B] stp instance 2 root primary

# ===== 接入双上行链路聚合 =====
[ACC-1] interface Bridge-Aggregation 1
[ACC-1-Bridge-Aggregation1] link-aggregation mode dynamic
[ACC-1-Bridge-Aggregation1] port link-type trunk
[ACC-1-Bridge-Aggregation1] port trunk permit vlan 10 20 30 40 99
[ACC-1-Bridge-Aggregation1] undo port trunk permit vlan 1
[ACC-1-Bridge-Aggregation1] quit

[ACC-1] interface range g1/0/23 to g1/0/24
[ACC-1-if-range] port link-aggregation group 1
[ACC-1-if-range] quit

# ===== VRRP 网关冗余（非 IRF 场景）=====
[Core-A-Vlan-interface10] ip address 192.168.10.2 24
[Core-A-Vlan-interface10] vrrp vrid 10 virtual-ip 192.168.10.1
[Core-A-Vlan-interface10] vrrp vrid 10 priority 120
[Core-A-Vlan-interface10] vrrp vrid 10 track 1 priority reduced 30

[Core-B-Vlan-interface10] ip address 192.168.10.3 24
[Core-B-Vlan-interface10] vrrp vrid 10 virtual-ip 192.168.10.1
[Core-B-Vlan-interface10] vrrp vrid 10 priority 100

# ===== 核心与出口间 OSPF =====
[Core-A] ospf 1 router-id 1.1.1.1
[Core-A-ospf-1] area 0
[Core-A-ospf-1-area-0.0.0.0] network 10.0.0.0 0.0.0.3
[Core-A-ospf-1-area-0.0.0.0] network 192.168.0.0 0.0.255.255
[Core-A-ospf-1] default-route-advertise
```

### 15_2_3 验收清单
| 验收项 | 命令 | 达标标准 |
| --- | --- | --- |
| IRF/聚合正常 | `display irf` / `display link-aggregation verbose` | 一主一备；成员口 Selected |
| MSTP 负载分担 | `display stp brief` | 不同实例阻塞不同端口 |
| VRRP 主备 | `display vrrp verbose` | 一主一备，追踪对象正常 |
| 网关可达 | 终端 ping 虚拟 IP | 通 |
| 核心故障切换 | 关掉主核心 | 业务中断在预期秒内 |
| OSPF 邻居 | `display ospf peer` | Full |
| 回程路由完整 | 出口设备 `display ip routing-table` | 有内网所有网段 |

---

## 15_3 割接实施（项目交付的关键动作）
### 15_3_1 割接前准备清单
```plain
□ 现网信息采集完整（配置、拓扑、台账、LLDP 核对）
□ 新方案设计通过评审（含回退方案）
□ 配置脚本提前编写并经过模拟器验证
□ 设备到货、版本确认、License 确认
□ 割接窗口获批（含客户、业务方签字）
□ 备件到位（光模块、线缆、备用设备）
□ 人员分工明确（指挥、操作、验证、应急）
□ 联系方式畅通（客户、厂商、运营商）
```

### 15_3_2 割接实施步骤
```plain
T-60 分钟：最终确认（设备状态、回退物资、人员到位）
T-30 分钟：备份现网配置（本地 + 远端双份）
T-15 分钟：再次确认业务低峰，通知相关方
T-0      ：开始割接（按脚本逐段执行）
每个步骤后：立即验证（ping、display、业务测试）
全部完成后：业务验证（核心业务 + 边缘业务）
稳定观察：30 分钟 ~ 2 小时
确认无误：清理临时配置、更新台账、签署验收单
```

### 15_3_3 割接中的"三线"原则
| 线 | 说明 |
| --- | --- |
| **时间线** | 每个步骤有预估时间，超时立即评估是否回退 |
| **回退线** | 设定明确的回退触发条件（如"XX 业务 30 分钟内未恢复即回退"） |
| **验证线** | 每步必验，不验证不进入下一步 |

### 📌 案例手记：一次没有回退线的割接
某园区网核心替换，工程师计划 4 小时完成。实际执行到第 3 小时，发现新核心与旧接入交换机的聚合协商不成功，反复调整无果。

因为没有设定"回退触发条件"，团队一直"再试一次"，直到业务方施压才回退，此时已超窗口 2 小时，第二天业务高峰受影响。

**改进后的做法**：

1. 割接前**明确回退触发条件**：如"核心业务在 T+60 分钟内未恢复即启动回退"。
2. 回退**不丢人**，超窗口才是事故。
3. 保留**物理回退能力**（旧设备不下电、原线缆不拆除），5 分钟可切回。

---

## 15_4 变更风险与回退方案
### 15_4_1 风险评估矩阵
| 风险 | 影响 | 概率 | 控制措施 |
| --- | --- | --- | --- |
| 配置丢失 | 高 | 中 | 变更前双备份（本地 + 远端） |
| 业务长时间中断 | 高 | 中 | 变更窗口 + 回退预案 |
| 版本不兼容 | 中 | 低 | 提前在测试环境验证 |
| 接线错误 | 中 | 中 | LLDP 核对 + 标签 |
| 回退失败 | 高 | 低 | 回退方案提前演练 |

### 15_4_2 回退方案模板
```plain
## 变更回退方案

### 1. 回退触发条件
- 条件一：核心业务在 T+30 分钟内未恢复
- 条件二：出现计划外的业务影响（如其他区域受影响）
- 条件三：设备出现异常（反复重启、配置丢失）

### 2. 回退步骤（精确到命令）
步骤 1：恢复原线缆连接（保留在原位置，5 分钟内完成）
步骤 2：在新设备上执行 undo 相关配置 / 或直接下电
步骤 3：旧设备加电并确认配置（原配置已保留）
步骤 4：验证核心业务恢复

### 3. 回退验证
- ping 网关
- 业务系统登录测试
- 关键用户确认

### 4. 回退后动作
- 记录问题、重新评估方案
- 重新预约窗口
```

### 15_4_3 变更操作纪律
1. **变更前必备份**：`save` + TFTP 导出。
2. **单点修改**：一次改一处，改完立即验证。
3. **不跳过验证**：每个关键步骤后跑验收命令。
4. **保留物理回退能力**：旧线缆、旧设备先不拆。
5. **变更留痕**：截图或保存命令输出，作为交付证据。
6. **双人复核**：关键操作一人操作、一人复核。

---

## 15_5 面试汇报与技术方案表达
### 15_5_1 技术面试的评分逻辑
| 维度 | 考察点 | 表现方式 |
| --- | --- | --- |
| 技术深度 | 是否理解原理与边界 | 能说清"为什么这样选"与"代价是什么" |
| 方案能力 | 是否能做取舍 | 给出 2 个备选方案并比较 |
| 表达能力 | 是否讲得清 | 结构化表达：背景 → 需求 → 方案 → 理由 → 风险 |
| 应变能力 | 被追问时的反应 | 承认不知道的部分，但给出排查思路 |
| 项目经验 | 是否真做过 | 能说出具体的坑与解决办法 |

### 15_5_2 方案汇报的"黄金结构"
```plain
1. 背景与需求（1 分钟）
   客户是谁、网络规模、业务特点、核心诉求

2. 约束条件（1 分钟）
   预算、工期、现有设备、业务中断容忍度、团队运维能力

3. 方案设计（3~5 分钟）
   拓扑 + 关键技术选型（每项说清"为什么选它"）

4. 备选方案与取舍（2 分钟）
   方案 A vs 方案 B，各自的失效边界与适用场景

5. 风险与应对（1~2 分钟）
   单点风险、割接风险、回退方案

6. 验收标准（1 分钟）
   用什么命令、什么方法证明方案达标
```

### 15_5_3 常见追问与应答要点
| 追问 | 应答要点 |
| --- | --- |
| 为什么用 IRF 不用 M-LAG？ | 园区网允许分钟级维护窗口，IRF 更简单、运维成本低；若客户要求零中断则改 M-LAG |
| 为什么 Trunk 不允许 VLAN 1？ | 避免广播域泄漏与 VLAN 跳跃攻击，等保检查项 |
| STP 为什么默认关闭？ | H3C 默认关闭，必须手工开启；不开启时二层冗余会形成环路 |
| VRRP 为什么要 track 上行口？ | 避免主设备上行断了但仍占 Master，导致流量黑洞 |
| 割接失败怎么办？ | 说清触发条件与回退步骤，强调保留物理回退能力 |

### 📌 案例手记：30 分钟面试，讲技术还是讲故事？
某次 IE 面试，候选人把 OSPF 的 LSA 类型倒背如流，但被问到"如果让你重新设计这个网络，你会改哪里"时卡住了。

反例与正例：

+ **反例**：罗列技术点（"我们用了 MSTP、VRRP、OSPF、BFD 等多种技术"）——听起来像配置清单。
+ **正例**：讲决策链（"客户是医院，业务中断容忍度极低，所以核心选了 M-LAG 而不是 IRF，因为 IRF 升级需要重启；代价是配置复杂度上升，我们通过标准模板来控制"）——体现方案能力。

**结论**：**面试不是考背书，是考"你能不能为决策负责"。** 每个技术选型都要能说出理由、代价与替代方案。

---

## 15_6 交付文档清单
### 必交付文档
| 文档 | 内容 | 用途 |
| --- | --- | --- |
| 需求调研表 | 现状、需求、约束 | 项目基线 |
| 技术方案 | 拓扑、设计、选型理由 | 评审与实施依据 |
| 实施计划 | 步骤、时间、人员分工 | 割接执行 |
| 规划表 | VLAN、IP、端口、设备命名 | 实施与运维 |
| 配置脚本 | 逐设备的完整配置 | 实施与备份 |
| 验收报告 | 每项的验证命令与结果 | 客户签字 |
| 回退方案 | 触发条件与步骤 | 风险控制 |
| 设备台账 | 型号、序列号、维保、位置 | 运维移交 |
| 运维手册 | 巡检项、常见故障处理 | 日常运维 |
| 培训材料 | 拓扑说明、关键操作 | 客户赋能 |

### 验收报告模板
```plain
## 项目验收报告

### 一、项目概况
项目名称 / 实施时间 / 参与方 / 实施范围

### 二、验收项与结果
| 序号 | 验收项 | 验收方法 | 预期结果 | 实际结果 | 是否通过 |
| --- | --- | --- | --- | --- | --- |
| 1 | VLAN 互通 | ping 测试 | 跨 VLAN 通 | 通 | 是 |
| 2 | 上网 | 访问公网 | 成功 | 成功 | 是 |
| 3 | 冗余切换 | 断开主链路 | 30 秒内恢复 | 12 秒 | 是 |

### 三、遗留问题
（问题描述、影响、计划解决时间）

### 四、附件
- 拓扑图
- 配置脚本
- 命令输出记录
- 培训签到表
```

---

## 15_7 全流程验收清单（本板块总结）
| 阶段 | 验收项 | 达标标准 |
| --- | --- | --- |
| 设计 | 规划表完整 | VLAN、IP、端口、命名全部明确 |
| 实施 | 配置与规划一致 | `display` 输出与规划表逐项吻合 |
| 验证 | 每项配置有验证 | 每个验收项有命令 + 结果记录 |
| 割接 | 有回退方案 | 触发条件明确、步骤可操作 |
| 交付 | 文档齐全 | 十类文档齐备 |
| 表达 | 能讲清方案 | 黄金结构 6 段完整，能应对追问 |
| 沉淀 | 笔记完成 | 用四段式模板记录，含踩坑与边界 |

### 收官建议
```plain
学完 15 个板块后，做三件事检验成果：

1. 不看文档，40 分钟内配完中小企业单核心组网（15_1）
2. 人为注入 3 个故障，30 分钟内定位并写出排错报告（14_5）
3. 用 10 分钟向"客户"讲清楚你的方案与理由（15_5）

三件事都能做到，说明你已经从"会配命令"走到"能解决问题、能讲清方案"。
```