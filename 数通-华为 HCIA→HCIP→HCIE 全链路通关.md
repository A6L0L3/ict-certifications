# 华为数通 HCIA→HCIP→HCIE 全链路通关知识库
> **一句话定位**：这不是一份"知识点罗列"，而是一条**能走完的路**——从第一次登录交换机，到在 480 分钟的实验考场里完成设计、部署、排错与论述。
> 本知识库以华为数通（Datacom）方向为主线，覆盖 **HCIA→HCIP→HCIE** 三级认证全链路，所有配置均基于 **VRP 系统**（S 系列交换机 / AR 系列路由器 / CloudEngine 数据中心交换机），命令可直接粘贴到 eNSP 或真机执行。

---

## 一、这份知识库解决什么问题
学数通的人，通常卡在四个地方：

| 痛点 | 本知识库的做法 |
| --- | --- |
| **不知道考什么、学到哪算够** | 板块0 给出三级能力模型、考试科目与权重、各阶段里程碑自检表 |
| **知识点学完就忘、不会用** | 每个板块配"案例小故事 + 完整配置 + 验证命令 + 建议亲手做一次的实验" |
| **配置背了一堆，出故障还是抓瞎** | 板块17 给出 20 个高频真实案例，按"现象 → 排查命令 → 根因 → 处理"四段式组织 |
| **考试有分数，工作没章法** | 每个板块都配"场景笔记法"——记什么、怎么验、三板斧是什么 |

**核心设计原则**：每个板块都能独立成篇，也都能串成一条线。你可以从头读到尾，也可以带着一个故障现象直接翻到对应板块。

---

## 二、三级能力分水岭（先看这个，再决定投入）
| 级别 | 能力定位 | 一句话标准 |
| --- | --- | --- |
| **HCIA** | 中小型网络的配置与基础运维 | **会配**——照着需求把命令敲出来，单技术点正确即可 |
| **HCIP** | 跨场景方案理解 + 单领域规划设计部署 | **会设计**——知道为什么这么配，能处理多技术叠加与互通约束 |
| **HCIE** | 复杂网络设计、部署、调优、排错 | **会取舍与救火**——8 小时内完成设计—部署—排错闭环，并说清"为什么选 A 不选 B" |

> 一句话记住三者的差别：**HCIA 关心"通不通"，HCIP 关心"为什么通"，HCIE 关心"断了怎么最快恢复，以及当初为什么这么设计"。**

---

## 三、知识库总地图（20 个板块）
```latex
┌─────────────────────────────────────────────────────────────────┐
│  导航层                                                          │
│   板块0  学习路径与认证通关地图                                    │
├─────────────────────────────────────────────────────────────────┤
│  HCIA 地基（能通）                                               │
│   板块1  VRP 系统管理与设备基础                                    │
│   板块2  以太网交换与 VLAN 技术                                    │
│   板块3  生成树与二层环路防护                                      │
│   板块4  链路聚合、堆叠与集群                                      │
│   板块5  三层交换、VLAN 间路由与 DHCP 服务                         │
│   板块6  IP 路由基础、静态路由与连通性检测                          │
├─────────────────────────────────────────────────────────────────┤
│  HCIP 主力（能控）                                               │
│   板块7  RIP 与 OSPF 路由技术                                     │
│   板块8  IS-IS 与 BGP 路由技术                                    │
│   板块9  MPLS、MPLS L3VPN 与 EVPN                                │
│   板块10 VXLAN 与园区网络虚拟化                                    │
│   板块11 ACL、NAT 与流量过滤                                      │
│   板块12 接入安全与用户管理                                        │
│   板块13 网络可靠性与快速收敛                                      │
│   板块14 QoS 与流量管理                                           │
├─────────────────────────────────────────────────────────────────┤
│  HCIE 冲刺（能救）                                               │
│   板块15 组播与 IPv6 技术                                         │
│   板块16 网络自动化与智能运维                                      │
│   板块17 故障排查方法论与案例库                                    │
│   板块18 HCIE 实验冲刺与综合组网                                   │
├─────────────────────────────────────────────────────────────────┤
│  常备手边                                                        │
│   板块19 附录：命令速查、设备命名与实验清单                         │
└─────────────────────────────────────────────────────────────────┘
```

### 板块速查表
| 板块 | 标题 | 级别 | 核心命题 | 前置 |
| --- | --- | --- | --- | --- |
| 板块0 | 学习路径与认证通关地图 | 全级别 | 考什么、怎么学、练什么、到哪算达标 | 无 |
| 板块1 | VRP 系统管理与设备基础 | HCIA | 设备怎么登录、配置怎么管理、远程怎么运维 | 0 |
| 板块2 | 以太网交换与 VLAN 技术 | HCIA→HCIP | 报文的 VLAN Tag 在整个转发过程中被怎么处理 | 1 |
| 板块3 | 生成树与二层环路防护 | HCIA→HCIP | 有冗余就必然有环，如何既冗余又无环 | 2 |
| 板块4 | 链路聚合、堆叠与集群 | HCIA→HCIE | 多链路变一条、多台设备变一台 | 3 |
| 板块5 | 三层交换、VLAN 间路由与 DHCP | HCIA→HCIP | 不同 VLAN 怎么通信、网关放哪、地址怎么下发 | 2 |
| 板块6 | IP 路由基础、静态路由与连通性 | HCIA→HCIP | 设备凭什么决定报文从哪个口出去 | 5 |
| 板块7 | RIP 与 OSPF 路由技术 | HCIA→HCIE | 链路状态协议如何建邻居、算路由、做汇总 | 6 |
| 板块8 | IS-IS 与 BGP 路由技术 | HCIP→HCIE | AS 之间怎么传路由、怎么精细控制选路 | 7 |
| 板块9 | MPLS、MPLS L3VPN 与 EVPN | HCIP→HCIE | 标签怎么转发、地址重叠怎么解决 | 8 |
| 板块10 | VXLAN 与园区网络虚拟化 | HCIP→HCIE | 大二层怎么跨三层、网关放集中还是分布 | 9 |
| 板块11 | ACL、NAT 与流量过滤 | HCIA→HCIE | 谁能访问谁、内网怎么出网 | 6 |
| 板块12 | 接入安全与用户管理 | HCIP→HCIE | 接上网线的是不是"该接的人、该接的设备" | 2、5 |
| 板块13 | 网络可靠性与快速收敛 | HCIP→HCIE | 断了怎么不断业务、切换要多久 | 4、5 |
| 板块14 | QoS 与流量管理 | HCIP→HCIE | 拥塞时让谁先过 | 11 |
| 板块15 | 组播与 IPv6 技术 | HCIP→HCIE | 一份数据只发给想看的人；IPv6 怎么过渡 | 6、7 |
| 板块16 | 网络自动化与智能运维 | HCIP→HCIE | 让机器替你敲命令、替你发现问题 | 1 |
| 板块17 | 故障排查方法论与案例库 | 全级别（HCIE 核心） | 看到现象能不能立刻想到那三四个原因 | 全部 |
| 板块18 | HCIE 实验冲刺与综合组网 | HCIE | 480 分钟怎么分配、论述题怎么写 | 全部 |
| 板块19 | 附录：命令速查、设备命名与实验清单 | 全级别 | 不翻整库就能查到命令与默认参数 | 无 |

---

## 四、怎么读这份知识库（四条路线）
### 路线 A：零基础从头通关（推荐新手）
```latex
板块0（通读一遍，建立全局观）
  → 板块1 → 2 → 3 → 4 → 5 → 6        （HCIA 地基，约 4–8 周）
  → 板块7 → 8 → 11 → 12 → 13 → 14     （HCIP 主力，约 3–6 个月）
  → 板块9 → 10 → 15 → 16              （HCIE 进阶）
  → 板块17 → 18                       （冲刺与实战）
  板块19 全程常备手边
```

### 路线 B：有基础，直奔 HCIP
```latex
板块0 只看 0_1（认证体系）与 0_6（级别 × 知识点映射）
  → 快速过 板块1–6（查漏补缺，重点看每节末尾的"考点与易错点"）
  → 精读 板块7（OSPF）与 板块8（BGP）        ← HCIP 的两大权重
  → 板块11–14（安全、可靠性、QoS）
  → 板块17（排错方法论）
```

### 路线 C：HCIE 冲刺（已有 HCIP 基础）
```latex
板块9（MPLS/VPN）→ 板块10（VXLAN）  ← 实验里承载网占 25%、园区占 20%
  → 板块16（自动化，笔试 17%）
  → 板块17（排错，独立 15 分，性价比最高）
  → 板块18（480 分钟节奏 + 论述题框架）
```

### 路线 D：带着故障来查（运维现场）
```latex
第1步 上不了网 / 网慢        → 板块17 的"分层排错速查表" + 案例 1/2/3
第2步 邻居起不来             → 板块7（OSPF 八项检查）或 板块8（BGP 状态机）
第3步 私接设备 / 拿到假地址  → 板块12（DHCP Snooping + IPSG）
第4步 主备不切换             → 板块13（VRRP 排错 + BFD）
第5步 VPN 不通              → 板块9（黄金五步排查法）
第6步 组播收不到流           → 板块15（RPF 检查）
```

---

## 五、每个板块的统一结构（读到哪、找什么）
为避免"翻遍全文找不到想要的东西"，全部 20 个板块采用同一套骨架：

```latex
第2步 技术小节       X_1、X_2、X_3……（二级编号，逐层递进）
第3步 案例小故事     真实场景还原：现象 → 排查 → 根因 → 处理
第4步 落地配置       可直接粘贴的完整配置片段（含地址规划表）
第5步 验证与排错     display 命令 + 输出解读 + 排错清单
第6步 场景笔记与验证 本板块要沉淀的笔记 / 验证三板斧 / 建议亲手做一次的实验
第7步 考点与易错点   表格化的"易错点 → 正确认知"
```

> **二级编号规则**：一级用 `X_1 / X_2 / X_3`，二级用 `X_1.1 / X_1.2`。例如 `8_3.1` = 板块8 第 3 节第 1 小节。全库统一，方便引用与检索。

---

## 六、学习方法：三条支线要并行
技术学习不能只堆知识点，必须三条腿走路：

| 支线 | 内容 | 产出物 | 时间占比 |
| --- | --- | --- | --- |
| **理论线** | 协议原理、报文结构、状态机 | 思维导图 / 自己的笔记 | 30% |
| **实验线** | 拓扑搭建、配置、抓包、排错 | 实验报告 / 配置模板库 | 50% |
| **题感线** | 真题/模拟题、拖拽题、填空 | 错题本（记录"为什么会选错"） | 20% |

**两条硬提醒：**

1. 华为考试中**填空、拖拽题占比不低**，考的是命令与参数的精确记忆（如 `preference` 默认值、`ospf cost` 取值范围）。建议单独建一份"纯记忆卡片"，考前集中过，板块19 的 19_7 默认参数表就是现成的底稿。
2. **实验报告数量比实验数量更重要**。每做完一个实验，按"需求 → 地址规划 → 关键配置 → 验证输出 → 遇到的坑 → 三问复盘"写一份 10 分钟的记录——它是你考前唯一能快速回顾的东西。

---

## 七、考试与证书要点（速记版）
| 项目 | 要点 |
| --- | --- |
| HCIA-Datacom | H12-811，笔试 90 min，600/1000 通过 |
| HCIP-Datacom | H12-821（核心，必修）+ 一门选修（如 H12-831），两门无先后顺序 |
| HCIE-Datacom | H12-891 笔试 + H12-892 实验（480 min，80/100 通过） |
| 笔试有效期 | **18 个月**——HCIE 笔试通过后须在此期限内通过实验 |
| 证书有效期 | **3 年**，自发放日起算，无宽限期 |
| 重认证 | 失效前通过同级或更高级任意一门考试即可刷新 3 年；也可走继续教育学分 |

> ⚠️ 考试代码、费用考点政策会随版本调整，**报名前务必以华为人才在线与 Pearson VUE 预约页面的最新公告为准**。

**HCIE 实验的三段式结构**：Design（设计）→ Deploy（部署）→ Troubleshoot（排错）。其中排错已升级为独立计分模块（基础故障题 5 分 + 进阶故障题 10 分 = 15 分），总时长 480 分钟、总分 100 分、合格线 80 分不变。

> **排错是全场性价比最高的分数**：15 分只需 45 分钟。详见板块17 与板块18。

---

## 八、关于插图与排版
+ 全部拓扑与原理图采用 **ASCII 文本拓扑**（内嵌在 ```text 代码块中），不依赖任何外部图片服务，在GitHub 中都能原样渲染，永不失效；
+ 全文为**纯 Markdown**，不含 HTML 标签，不含外部引用标记；
+ 所有命令块可直接复制粘贴到 eNSP 或真机执行。

---

## 九、最后一句
这份知识库的价值，不在于你读了几遍，而在于**你亲手敲过多少条命令、踩过多少个坑、写过多少份实验报告**。

**建议从板块0 开始，今天就搭起第一台设备。**

# 板块0 · 学习路径与认证通关地图
> 定位：先把"考什么、怎么学、练什么、到哪一步算达标"讲清楚，再进入技术细节。本板块是整份知识库的导航层与备考总纲，第一次打开请通读一遍，之后按需回查。
> 本知识库以**华为数通（Datacom）方向**为主线，覆盖 HCIA→HCIP→HCIE 全链路，所有配置均基于 VRP 系统（S 系列交换机 / AR 系列路由器 / CloudEngine 数据中心交换机），命令可直接粘贴到 eNSP 或真机执行。

## 0_1 华为认证体系全景
### 0_1.1 三级能力模型
| 级别 | 全称 | 能力定位 | 典型岗位 |
| --- | --- | --- | --- |
| **HCIA** | Huawei Certified ICT Associate（工程师级） | 掌握数通基础知识，能完成中小型网络的**配置与基础运维** | 网络运维工程师、桌面运维、售前助理 |
| **HCIP** | Huawei Certified ICT Professional（高级工程师级） | 具备跨场景方案理解与**单领域规划设计 + 部署**能力 | 网络工程师、项目实施工程师、甲方网络主管 |
| **HCIE** | Huawei Certified ICT Expert（专家级） | 具备**复杂网络设计、部署、调优、排错**的端到端能力 | 网络架构师、高级交付专家、技术经理 |

能力差异的**分水岭**只有三件事，记住这三句，你就知道每个阶段该练什么：

1. **HCIA 会配**：照着需求把命令敲出来，单技术点正确即可；
2. **HCIP 会设计**：知道为什么这么配，能处理多技术叠加（OSPF + BGP + MPLS + VRRP + QoS）与互通约束；
3. **HCIE 会取舍与救火**：在 8 小时实验里完成设计—部署—排错闭环，并且能说清"为什么选 A 不选 B"。

> **现场故事**：一次园区网割接，两位工程师都把 OSPF 配通了。甲方临时要求"监控流量不能走办公链路"，A 工程师愣住——他只会配，不会改属性；B 工程师十分钟用 route-policy 加 community 搞定。这就是 HCIA 与 HCIP 的分水岭：不是会不会敲命令，而是**需求变了你还敢不敢动手**。

### 0_1.2 数通方向考试科目与费用（现行版本）
| 级别 | 科目 | 考试代码 | 形式 | 时长 | 通过分/总分 | 费用 | 语言 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| HCIA-Datacom | HCIA-Datacom V1.0 | **H12-811** | 笔试 | 90 min | 600/1000 | 200 USD | 中/英 |
| HCIP-Datacom | Core Technology（**必修**） | **H12-821** | 笔试 | 90 min | 600/1000 | 300 USD | 中/英 |
| HCIP-Datacom | Advanced Routing & Switching（**选修**） | **H12-831** | 笔试 | 90 min | 600/1000 | 180 USD | 中/英 |
| HCIE-Datacom | 笔试 | **H12-891** | 笔试 | 90 min | 600/1000 | 300 USD | 中/英 |
| HCIE-Datacom | 实验（Lab） | **H12-892** | 操作 + 论述 | 480 min | 80/100 | 8000 CNY（海外约 1200 USD） | 中/英 |

**关键规则（踩坑率极高，务必记住）：**

+ **笔试成绩有效期 18 个月**：HCIE 笔试通过后，必须在 18 个月内通过实验考试，否则笔试作废需重考；
+ **HCIP 需两门**：H12-821（核心）+ 一门选修，两门**无先后顺序**，只要在成绩有效期内都通过即可取证；
+ **证书有效期 3 年**，自证书发放日起算，**无宽限期**，过期不能"续"，只能重新考全部科目；
+ **重认证**：在失效前通过同级别任意一门考试、或更高级别任意一门考试，即可刷新 3 年；另可通过官方继续教育学分（课程进度 ≥90% + 结课考试）以学代考；
+ **旧版选修科目已退市**：HCIP-Datacom 旧版四门细分方向（WAN 规划部署 H12-861、SD-WAN 规划部署 H12-871、企业网络方案设计 H12-851、网络自动化开发 H12-881）已进入退市流程，新版方向统一归并到 **H12-831（高级路由交换）**，一门覆盖原四科，考点范围显著扩大；已持有旧版证书在有效期内**仍然有效，无需重考**。手上有旧版考券的，务必在官方公布的停止考试交付（EOS）时间前考掉，过期作废且不退款。

> ⚠️ 考试代码、费用考点政策会随版本调整，报名前以华为人才在线（e.huawei.com/cn/talent）与 Pearson VUE 预约页面为准。

### 0_1.3 HCIE-Datacom 笔试知识点权重
| 知识模块 | 笔试占比 | 实验占比 |
| --- | --- | --- |
| 高级路由交换技术 | 37% | 40% |
| 园区网络规划与部署 | 23% | 20% |
| 承载网（Bearer WAN）规划与部署 | 15% | 25% |
| 网络自动化 | 17% | 10% |
| WAN 互联规划与部署 | 8% | 5% |

**这张表直接决定你的时间投入比例。** 很多人把 90% 时间花在路由交换，结果在承载网（MPLS/SR/承载网方案）和自动化上丢分——实验里承载网权重高达 25%，是仅次于路由交换的第二大块。

### 0_1.4 HCIP-Datacom 两门科目的知识点权重
**H12-821（核心技术，必考）：**

| 知识模块 | 占比 |
| --- | --- |
| **BGP 核心知识** | **17%** |
| **OSPF 核心知识** | **16%** |
| 路由和流量控制 | 10% |
| 组播基础 | 9% |
| 网络安全基础 | 9% |
| 交换技术基础 | 7% |
| 其他（IP 基础、以太网、广域网等） | 约 32% |

**H12-831（高级路由交换，选考）：**

| 知识模块 | 占比 |
| --- | --- |
| **IPv6 路由** | **20%** |
| **MPLS 技术** | **19%** |
| **IGP 高级特性** | **17%** |
| BGP 高级特性 | 10% |
| 以太网高级技术、网络运维、故障排除、网络割接等 | 约 34% |

> 💡 **三条从权重表读出来的备考结论**：  
第1步 **BGP 是 HCIP 的第一权重**（821 占 17%），比 OSPF 还高，别只顾着啃 OSPF；  
第2步 **H12-831 的核心是 IPv6 + MPLS + IGP 高级特性，合计 56%**，几乎决定这门课的成败——本知识库的板块5/7/8/9/15 正是按这个权重铺的；  
第3步 **新版 831 明显偏向"排错 + 割接 + 运维"**，纯背命令的备考方式已经不够用了，必须能读懂现象、定位根因。

### 0_1.5 HCIE 实验考试的三段式结构
```latex
┌──────────────────────────────────────────────────────────────┐
│  H12-892 Lab（480 分钟 / 8 小时）                              │
├──────────────┬──────────────┬────────────────────────────────┤
│  Design 设计  │ Deploy 部署   │ Troubleshoot 排错               │
│  读需求→画拓扑 │ 真机/仿真环境 │ 预置故障 + 动态场景故障          │
│  →选技术选型   │ 完成完整配置  │ ★ 单独 15 分：基础题 5 分        │
│  →写规划文档   │ →逐项验证     │             + 进阶题 10 分      │
└──────────────┴──────────────┴────────────────────────────────┘
```

**新版实验的排错模块要点：**

+ **分值构成**：1 道基础故障题（**5 分**）+ 1 道进阶故障题（**10 分**），合计 **15 分**；
+ **总时长仍为 480 分钟、总分仍 100 分、合格线仍 80 分**——排错这 15 分必须拿到，否则部署部分要补 15 分回来；
+ **考核形式**：预置故障 + 动态场景故障，考的是应急响应与根因定位，不是配置背诵；
+ 具体执行时间与题型细节以官方最新公告为准。

高分要点：**部署部分边配边验**（每完成一个技术点立刻 `display` 验证），不要攒到最后；**排错部分先恢复业务再找根因**，先拿分再解释。

---

## 0_2 学习路径总览
### 0_2.1 一条主线：从"能通"到"能控"到"能救"
```latex
第 1 阶段 · 能通（HCIA，约 4–8 周）
  网络模型 → 交换/VLAN → 三层路由 → 基础服务(DHCP/NAT) → 基础安全
        ↓
第 2 阶段 · 能控（HCIP，约 3–6 个月）
  STP/MSTP → Eth-Trunk/堆叠 → OSPF多区域/IS-IS → BGP与路由策略
  → MPLS/VPN → 组播 → QoS → 可靠性(VRRP/BFD) → 园区网方案
        ↓
第 3 阶段 · 能救（HCIE，约 6–12 个月）
  VXLAN/EVPN → 承载网 → SDN/自动化(Python/NETCONF) → 大型综合实验
  → 限时排错训练 → 论述题写作训练
```

### 0_2.2 三条并行的学习支线
技术学习不能只堆知识点，必须三条腿走路：

| 支线 | 内容 | 产出物 | 时间占比 |
| --- | --- | --- | --- |
| **理论线** | 协议原理、报文结构、状态机 | 思维导图 / 自己的笔记 | 30% |
| **实验线** | eNSP 拓扑搭建、配置、抓包、排错 | 实验报告 / 配置模板库 | 50% |
| **题感线** | 真题/模拟题、拖拽题、填空 | 错题本（记录"为什么会选错"） | 20% |

> **特别提醒**：华为考试中填空、拖拽题占比不低，这类题考的是**命令与参数的精确记忆**（例如 `preference` 默认值、`ospf cost` 取值范围）。建议单独建一份"纯记忆卡片"，考前集中过（板块19 的默认参数速记表就是现成素材）。

### 0_2.3 各阶段里程碑自检
| 阶段 | 达标标志（自检清单） |
| --- | --- |
| **HCIA** | 第1步 独立搭建 2 台交换机 + 2 台路由器的园区网；第2步 熟练配置 VLAN/Trunk/VLANIF/静态路由/单区域 OSPF/ACL/NAT/DHCP；第3步 能用 `ping`/`tracert`/`display` 定位"某台 PC 上不了网" |
| **HCIP** | 第1步 独立完成 MSTP + VRRP + Eth-Trunk + OSPF 多区域 + BGP 的综合组网；第2步 能配 MPLS L3VPN 并解释标签转发过程；第3步 看得懂路由表和 LSA/LSP；第4步 能写一份 3 页的实施方案 |
| **HCIE** | 第1步 8 小时内完成 VXLAN + BGP EVPN + MPLS 综合实验；第2步 面对 5 个预设故障能在 30 分钟内恢复业务；第3步 论述题能做到"结论先行 + 原理支撑 + 对比取舍" |

**怎么用这张表**：每学完一个板块回来打勾，勾不满就不往下走。HCIA 阶段最容易出现的自欺欺人是"我看懂了"——请把"看懂"替换成"我能从零敲出来并让 PC ping 通"。

---

## 0_3 新手入门顺序
### 0_3.1 前 30 天：打地基（每天 1.5–2 小时）
| 周次 | 主题 | 必做实验 |
| --- | --- | --- |
| 第 1 周 | OSI/TCP-IP 模型、IP 编址与子网划分、VRP 命令行 | eNSP 装好，起 1 台 AR2220，练熟 `?`、Tab 补全、`display` 系列命令 |
| 第 2 周 | 交换机工作原理（MAC 学习/泛洪/转发）、VLAN、Access/Trunk/Hybrid | 单交换机 3 VLAN 划分 + 跨交换机 Trunk 互通 |
| 第 3 周 | VLANIF 三层交换、静态路由、默认路由、浮动静态路由 | 三层交换机实现 VLAN 间路由 + 两台路由器静态路由互通 |
| 第 4 周 | STP/RSTP、Eth-Trunk、Telnet/SSH 管理 | 三交换机环形拓扑跑 RSTP，观察根桥选举与阻塞端口 |

**第 1 周最容易忽视的一件事**：先把 eNSP 的**设备启动失败（错误代码 40）**解决掉，否则后面每个实验都在跟环境打架。方案见 0_4。

### 0_3.2 第 31–90 天：进入路由世界
| 周次 | 主题 | 必做实验 |
| --- | --- | --- |
| 第 5–6 周 | RIP（理解距离矢量）→ OSPF 单区域 | OSPF 单区域 3 台路由器，观察邻居状态机 `display ospf peer brief` |
| 第 7–8 周 | OSPF 多区域、LSA 类型、DR/BDR、虚链路、路由汇总 | 多区域组网 + `display ospf lsdb` 逐类 LSA 解读 |
| 第 9 周 | ACL、NAT（Easy IP/NAPT/静态 NAT）、DHCP/DHCP Relay | PC 通过 NAT 访问"外网"，ACL 限制网段互访 |
| 第 10 周 | VRRP、BFD、链路聚合、DHCP Snooping/端口安全 | 双上行 VRRP 主备切换，拔线观察切换时间 |
| 第 11–12 周 | 综合实验（园区网）+ 错题复盘 | 见板块18 综合实验 |

### 0_3.3 常见"新手死循环"及破解
| 死循环 | 表现 | 破解方法 |
| --- | --- | --- |
| 只看视频不敲命令 | 看得懂、配不出来 | 视频暂停率 ≥50%，每段看完立刻复现 |
| 只敲命令不看原理 | 换个拓扑就懵 | 每个协议配完后抓一次包，看报文长什么样 |
| 做完实验不保存 | 下次重头再来 | 每个实验导出配置 + 拓扑文件，建自己的"实验仓库" |
| 遇到报错就重做 | 排错能力永远为零 | 强制自己 30 分钟内靠 `display`/`debugging` 定位，不许重开 |

---

## 0_4 实验环境搭建
### 0_4.1 三条路线对比
| 方案 | 适用人群 | 优点 | 缺点 |
| --- | --- | --- | --- |
| **eNSP（传统版）** | HCIA/HCIP 考生 | 免费、运行真实 VRP、资料最多 | 官方已停止更新；Win11 新机易报"错误 40"；不支持部分新特性 |
| **eNSP Pro** | 需要新特性（M-LAG、高级 VXLAN）的 HCIE 考生 | 持续维护、支持更多新设备与协议、Web 界面 | 官方仅对认证级合作伙伴开放下载权限，个人普通账号获取困难 |
| **真机 / 线上机架（Rack）** | HCIE 冲刺 | 手感、延迟、报错与考场一致 | 有成本，需按小时预约 |

> 现实建议：**HCIA/HCIP 阶段用传统 eNSP 完全够用**；HCIE 冲刺阶段如果自学，优先找机构的线上机架；**不要为了 eNSP Pro 的下载权限浪费备考时间**。

**eNSP Pro 的权限门槛（先看清规则再决定要不要折腾）：**

| 项目 | 官方说明 |
| --- | --- |
| **开放对象** | 仅面向认证级伙伴：ASP（授权服务伙伴）、服务伙伴/业务运营伙伴、销售伙伴（**不含**注册销售伙伴） |
| **不开放对象** | 注册销售伙伴、人才联盟伙伴、咨询与规划伙伴、**普通注册用户**、产品客户等 |
| **License** | 不需要 License；有权限即可下载安装 |
| **获取方式** | 公司先在 e+Partner 完成认证 → 个人账号关联公司升级为合作伙伴账号 → 在"技术支持 > 软件下载 > 培训与认证服务"下载 |
| **访问方式** | 浏览器（推荐 Chrome）访问 `https://[设备IP]:8443`，使用 Uniportal 账号登录 |

### 0_4.2 eNSP 稳定安装清单（踩坑总结版）
安装顺序**不可颠倒**，版本**不可随意升级**：

```latex
1. WinPcap 4.1.3        （不要用 Npcap 替代，eNSP 依赖 WinPcap）
2. Wireshark 3.x        （安装时若弹 Npcap 选项，取消勾选）
3. VirtualBox 5.2.44    （★ 必须 5.2.x；6.x/7.x 会导致 AR 设备报错 40）
4. eNSP V100R003C00     （最后装，安装路径不要有中文与空格）
```

装完后的关键收尾动作：

1. 对 `eNSP.exe`、`eNSP_Client.exe` 右键 → 属性 → 兼容性 → 勾选**以管理员身份运行**（Win11 可再勾"以兼容模式运行 Windows 8"，部分机器需 Win7 模式，二选一试）；
2. 关闭或放行 Windows 防火墙与杀软，否则虚拟网卡被拦截；
3. 以管理员身份首次启动 → 菜单**工具 → 选项 → 工具设置**，核对 VirtualBox / Wireshark 路径是否被正确识别；
4. 新建拓扑，拖入一台 AR2220 启动，能进 `#` 提示符即环境 OK。

> **Win11 新版本特例**：部分新版本存在兼容性缺陷（如 24H2 早期内部版本），需先升级系统到较新的内部版本（可搜对应离线更新包），否则 AR 设备必然启动失败。**环境搞不定不要硬扛，先换一台老机器或虚拟机跑 eNSP，把时间花在技术上。**

### 0_4.3 实验工程化管理（强烈建议）
```latex
D:\eNSP-Lab\
├── 01-VLAN-Trunk\
│   ├── topology.topo          # eNSP 拓扑文件
│   ├── 需求与规划.md           # 先写需求再动手
│   ├── config\SW1.cfg SW2.cfg  # 每设备导出配置
│   └── 验证记录.md             # display 关键输出 + 结论
├── 02-OSPF-MultiArea\
├── 03-BGP-RoutePolicy\
├── ...（按技术点顺序递增编号）\
└── 99-Troubleshooting\        # 排错专用，考前只看这里
```

> 目录编号建议：**按技术点顺序递增**，不要按日期。日期会乱，技术顺序不会。排错目录单独留一个 `99-`，考前只翻它。

每条记录至少包含：**需求 → 地址规划表 → 完整配置 → 验证命令输出 → 遇到的坑**。这份仓库在 HCIE 冲刺时就是你的排错案例库。

---

## 0_5 学习方法论
### 0_5.1 协议学习的"四问法"
每学一个新协议，强制回答四个问题，答不上来就是没学会：

1. **它解决什么问题？**（没有它之前网络怎么了）
2. **它靠什么报文/表项工作？**（Hello？LSA？Update？绑定表？）
3. **状态怎么迁移？**（Down → Init → 2-Way → Full，卡在哪一步意味着什么）
4. **它和谁的边界在哪？**（和谁配合、和谁冲突、什么时候不该用它）

举例套用 OSPF：解决"距离矢量收敛慢、有环路"的问题 → 靠 Hello/DD/LSR/LSU/LSAck 五类报文 + LSDB → 邻居状态机七态 → 与 BGP 的边界是"IGP 管 AS 内部可达，BGP 管 AS 间策略"。

### 0_5.2 抓包是理解协议的最短路径
eNSP 支持在链路上右键"开始抓包"直接调起 Wireshark。**必抓的 8 个包**：

| 场景 | 抓什么 | 看什么 |
| --- | --- | --- |
| VLAN | Trunk 链路上的以太帧 | 802.1Q Tag 字段、VLAN ID、PRI |
| STP | 交换机互联口 | BPDU 的 Root ID / Port Role / Flags |
| ARP | 同网段主机互通 | 请求广播、应答单播、免费 ARP |
| DHCP | PC 获取地址 | Discover/Offer/Request/Ack 四步 |
| OSPF | 广播链路 | 224.0.0.5、DR 选举、LSA 泛洪 |
| BGP | EBGP 直连 | Open/Update/Keepalive/Notification |
| MPLS | P/PE 之间 | 标签栈、Label/PHP |
| VXLAN | Underlay 链路 | VNI、UDP 4789、外层 IP |

### 0_5.3 命令记忆的三个技巧
1. **视图归类法**：把命令按视图记（系统视图 / 接口视图 / 协议视图），避免"知道命令但不知道在哪敲"；
2. **对比记忆法**：`display` 系列与 `debug` 系列成对记（`display ospf peer` ↔ `debugging ospf event`）；
3. **参数关联法**：记住默认值的"量级"（OSPF 参考带宽默认 100 Mbps、VRRP 优先级默认 100、STP 优先级默认 32768、BGP Local_Pref 默认 100、静态路由优先级 60），考试填空/选择直接秒。

---

## 0_6 认证级别 × 知识点映射表
> **本节导读**：同一门技术，在 HCIA / HCIP / HCIE 的要求深度完全不同。这张表帮你判断「这个知识点要学到什么程度才够」。

| 知识领域 | HCIA | HCIP | HCIE |
| --- | --- | --- | --- |
| VRP/设备管理 | ★★★ 会用 | ★★ 熟练 | ★ 自动化批配 |
| VLAN/Trunk/Hybrid | ★★★ | ★★ | ★（叠加 VXLAN） |
| STP/RSTP/MSTP | ★★ 基础 | ★★★ 设计与调优 | ★★ 与堆叠/Eth-Trunk 取舍 |
| 静态/默认/浮动路由 | ★★★ | ★★ | ★ |
| RIP | ★★ | ★ 了解 | — |
| OSPF | ★★ 单区域 | ★★★ 多区域/高级特性 | ★★★ 优化与排错 |
| IS-IS | — | ★★★ | ★★★（承载网主力） |
| BGP | ★ 概念 | ★★★ | ★★★ 策略/RR/EVPN |
| 路由策略（Route-Policy/IP-Prefix） | — | ★★★ | ★★★ |
| MPLS/LDP/L3VPN | — | ★★★ | ★★★ |
| EVPN/VXLAN | — | ★★ | ★★★ |
| 组播 IGMP/PIM | — | ★★ | ★★ |
| IPv6/OSPFv3/BGP4+ | ★ 基础 | ★★ | ★★★ |
| QoS | ★ 概念 | ★★ | ★★★（含 HQoS） |
| 安全（ACL/AAA/802.1X/防攻击） | ★★ | ★★★ | ★★★ |
| 可靠性（VRRP/BFD/堆叠） | ★★ | ★★★ | ★★★ |
| 网络自动化 | — | ★ | ★★★（Python/NETCONF/YANG） |
| 园区网/承载网方案设计 | — | ★★ | ★★★ |
| 网络迁移与割接 | — | ★ | ★★ |

**用法**：★ 少不代表不重要，而是"在这个级别你该投入多少精力"。比如 VRP 在 HCIA 是三星，因为开局全靠它；到 HCIE 只剩一星，因为你要把它交给 Python 批量处理。

---

## 0_7 备考节奏与证书维护
### 0_7.1 报考流程（笔试）
```latex
注册华为账号（Uniportal）→ 绑定 Pearson VUE 账号
→ 选择科目（H12-811 / H12-821 / H12-831 / H12-891）与考点城市
→ 支付考试费 → 携带本人有效身份证件原件到考点现场考试
```

+ 三个级别之间**可跨级报考**，不要求必须先考 HCIA；
+ 但知识是累积的，零基础直接冲 HCIE 通过率极低；
+ HCIE 实验考试需在笔试通过后**至少 5 天**才能预约，考场集中在北京、成都、杭州、深圳、安顺等城市（以预约页面为准）。

### 0_7.2 时间规划模板（在职备考，按周推进不写死日期）
| 阶段 | 周期 | 每周投入 | 重点 |
| --- | --- | --- | --- |
| HCIA | 6–8 周 | 8–10 h | 理论 3 : 实验 5 : 刷题 2 |
| HCIP（两门） | 4–6 个月 | 10–12 h | 每门分开备考，先 821 后 831 |
| HCIE 笔试 | 3–4 个月 | 12–15 h | 全栈知识 + 论述素材积累 |
| HCIE 实验 | 3–5 个月 | 15–20 h | 每天一个技术模块 + 每周一次 4 小时模拟考 |

**三级备考的节奏差异：**

+ **HCIA**：一周一个技术域，周末做综合小实验，第 6 周开始刷题库，错题回看配置；
+ **HCIP**：先啃 821 的 BGP + OSPF（占 33%），再上 831 的 IPv6 + MPLS + IGP 高级特性（占 56%）；每门考前留 2 周纯刷题；
+ **HCIE 笔试**：按权重表分配时间，自动化（17%）和承载网（15%）不要跳过；
+ **HCIE 实验**：速度是硬指标，用板块18 的"速度训练目标"表量化自己（例如 MPLS L3VPN 单域合格线 30 分钟）。

### 0_7.3 证书维护清单
+ 证书有效期：**3 年**，从发放日起算，**过期无宽限期**；
+ 到期前 3–6 个月启动重认证规划；
+ 重认证方式：第1步 通过同级或更高级任意一门考试；第2步 官方继续教育学分（课程进度 ≥90% + 结课考试）；
+ HCIP 仅支持**同技术方向**重认证（Datacom 不能拿 Security 续）；HCIE 支持跨方向组合规则，具体以官方最新政策为准。

---

## 0_8 场景笔记法：怎么记、怎么验
这一节是全知识库的"使用说明书"。后面每个板块都有独立的「场景笔记与验证」小节，格式统一，照抄即可。

### 0_8.1 一次实验的标准记录模板
每次做完实验，按下面六段写 10 分钟，比重做三遍都值钱：

```latex
【实验名】OSPF 多区域 + 特殊区域
【需求一句话】分支区域路由表只保留一条默认路由，减少 LSDB
【拓扑】（贴 ASCII 拓扑或截图）
【地址规划表】设备/接口/VLAN/IP/掩码/网关 → 表格
【关键配置】只贴核心 10~20 行，不要整份粘贴
【验证输出】display 命令 + 关键字段（贴 5~10 行，标红星）
【遇到的坑】现象 → 原因 → 解法（一句话即可）
【三问复盘】
  第1步 这条命令不加会怎样？（反向验证）
  第2步 换个拓扑我还认得出来吗？（迁移能力）
  第3步 如果考试只给现象不给需求，我第一步敲什么？（排错反射）
```

### 0_8.2 三类笔记的区别
| 笔记类型 | 记什么 | 什么时候看 |
| --- | --- | --- |
| **原理笔记**（思维导图） | 协议解决什么问题、报文/表项、状态机 | 学新协议当天 + 考前一周 |
| **配置模板库** | 可直接粘贴的标准配置（带注释） | 做实验/割接时直接抄 |
| **错题/坑本** | 现象 → 根因 → 一条命令 | 考前三天集中过 |

> **坑本是最值钱的资产**。HCIE 实验的排错题，本质上就是别人给你埋坑——你埋过挖过的坑越多，15 分拿得越稳。

### 0_8.3 验证的三板斧
任何技术点配完，按顺序做三件事，形成肌肉记忆：

```latex
第1步 看状态：display xxx peer / brief / interface   → 邻居/端口/会话起来没？
第2步 看表项：display xxx routing-table / lsdb / mac-address → 表项学到了没？
第3步 打流量：ping / ping -a 源地址 / tracert        → 数据真的过去了没？
```

**验证的三条纪律：**

1. **边配边验**，不要攒到最后（考试时最后发现问题就没时间改）；
2. **验证要带源**：`ping -a 192.168.10.1 8.8.8.8`，否则你测的是设备自己而不是业务；
3. **验收要留证据**：关键 `display` 输出截图或存文本，写进实验记录。

### 0_8.4 关于本知识库的插图
文档中的拓扑与原理图一律采用 **ASCII 文本拓扑**（内嵌在代码块中），不依赖任何外部图片服务，复制到任意 Markdown 编辑器或实验报告中都不会失效：

```latex
        ┌──────────┐
        │   Core   │
        │  SW-Core │
        └────┬─────┘
       GE0/0/1  GE0/0/2
        ┌────┴─────┐
   ┌────┴───┐  ┌───┴────┐
   │ SW-ACC1│  │ SW-ACC2│
   └────┬───┘  └───┬────┘
     PC1(VLAN10) PC2(VLAN20)
```

---

## 0_9 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | 认为必须逐级考 | **可跨级报考**，零基础直冲 HCIE 只是通过率极低，不是不允许 |
| 2 | HCIP 只要考一门 | **必须 H12-821 + 一门选修**，两门都过才取证 |
| 3 | 笔试有效期记成 3 年 | 笔试成绩 **18 个月**，证书 **3 年**，两个数字别混 |
| 4 | 证书过期还能续 | **无宽限期**，过期只能重考全部科目 |
| 5 | HCIE 实验只考配置 | 现在是 Design + Deploy + **Troubleshoot（15 分）** 三段 |
| 6 | 只学路由交换 | 实验里承载网占 25%、自动化占 10%，权重表决定时间分配 |
| 7 | 环境折腾一周 | eNSP 装不上立刻换方案（老机器/虚拟机/线上机架），别陷在环境里 |
| 8 | 笔记只抄配置 | 没有"现象 → 根因 → 命令"的坑本，等于没做过实验 |

---

# 板块1 · VRP 系统管理与设备基础
> 定位：一切配置的起点。HCIA 阶段要"敲得顺"，HCIP 阶段要"管得住"，HCIE 阶段要"能批量、能自动化"。本板块把设备登录、文件系统、配置管理、远程运维、日志审计这条线一次打通。
> 适用设备：S2700/S3700/S5700/S6700/S7700/S9700/CloudEngine、AR 系列路由器；系统：VRP V200R / CloudEngine V100R。

## 1_1 VRP 体系结构与命令行视图
### 1_1.1 VRP 是什么
VRP（Versatile Routing Platform，通用路由平台）是华为数通设备的操作系统内核，负责三个平面：

+ **转发平面**：报文的高速转发（由转发引擎/ASIC 完成，不消耗 CPU）；
+ **控制平面**：路由协议计算、表项维护（消耗 CPU）；
+ **管理平面**：命令行、网管、日志、文件管理。

**理解"三平面分离"直接决定你的排错思路**：转发不通看表项，协议不通看邻居，管理不了看服务与 ACL。

> **现场故事**：某园区核心 CPU 长期 70%，运维以为是路由太多。实际 `display cpu-usage task` 一看，是大量网管 SNMP 轮询 + 日志刷屏打满管理平面，转发平面 ASIC 闲得很。加了日志级别过滤与轮询间隔调整后 CPU 降到 18%。**先分清是哪个平面出问题，能省掉一半排查时间。**

### 1_1.2 命令行视图树（必须形成肌肉记忆）
```latex
<Huawei>                     用户视图（只读监控、ping、save、reboot）
  │  system-view
  ▼
[Huawei]                     系统视图（全局配置）
  │
  ├── [Huawei-GigabitEthernet0/0/1]     接口视图
  ├── [Huawei-Vlanif10]                 VLANIF 三层接口视图
  ├── [Huawei-vlan10]                   VLAN 视图
  ├── [Huawei-ospf-1]                   OSPF 进程视图
  │     └── [Huawei-ospf-1-area-0.0.0.0]  OSPF 区域视图
  ├── [Huawei-bgp]                      BGP 视图
  │     └── [Huawei-bgp-af-ipv4]         BGP 地址族视图
  ├── [Huawei-aaa]                      AAA 视图
  ├── [Huawei-ui-vty0-4]                VTY 用户界面视图
  ├── [Huawei-Eth-Trunk1]               Eth-Trunk 视图
  └── [Huawei-port-group-x]             端口组视图
```

**高频快捷操作：**

| 操作 | 快捷键/命令 | 说明 |
| --- | --- | --- |
| 命令帮助 | `?` | 查看当前视图可用命令 |
| 参数帮助 | `ping ?` | 查看该命令的参数 |
| 补全 | `Tab` | 自动补全命令或参数 |
| 简写 | `dis cu` / `int g0/0/1` | VRP 支持唯一前缀简写 |
| 返回上级 | `quit` | 逐层退出 |
| 直接回用户视图 | `return` 或 `Ctrl+Z` | 从任意视图返回 |
| 中止长输出 | `Ctrl+C` | 停止 `display` 刷屏 |
| 过滤输出 | `display cu | include vlan` | 管道过滤，支持 `include`/`exclude`/`begin`/`section` |

### 1_1.3 命令等级（命令分级保护）
| 级别 | 名称 | 权限 |
| --- | --- | --- |
| 0 | 参观级 | `ping`、`tracert`、`display` 等诊断命令 |
| 1 | 监控级 | 更多 display、debugging 关闭类 |
| 2 | 配置级 | 业务配置命令 |
| 3–15 | 管理级 | 文件系统、用户管理、命令级别修改、重启 |

生产环境做法：**给运维账号 level 2，给管理员 level 3，绝不默认全部给 15**。

```latex
[SW] command-privilege level 3 view system display      # 调整命令级别示例
[SW-aaa] local-user ops privilege level 2               # 用户级别控制
```

---

## 1_2 首次登录与初始配置
### 1_2.1 Console 连接参数（背下来）
| 参数 | 值 |
| --- | --- |
| 波特率 | 9600 |
| 数据位 | 8 |
| 停止位 | 1 |
| 校验位 | 无 |
| 流控 | 无 |

Console 口是**最后的救命通道**，远程服务无论怎么配崩，Console 都能进。**割接现场必须随身带 Console 线 + USB 转串口**——这是老工程师和新手最明显的区别之一。

### 1_2.2 开局标准配置模板（可直接粘贴）
```latex
<Huawei> system-view
[Huawei] sysname SW-Office-A

# —— 时间与时区（日志时间戳准不准全看它）——
[SW-Office-A] clock timezone BJ add 08:00:00
[SW-Office-A] clock datetime 14:30:00 2026-08-14

# —— 特权密码（进入系统视图的二次保护）——
[SW-Office-A] super password cipher Huawei@123

# —— 管理 VLAN 与 IP ——
[SW-Office-A] vlan 10
[SW-Office-A-vlan10] description MGMT-VLAN
[SW-Office-A-vlan10] quit
[SW-Office-A] interface Vlanif 10
[SW-Office-A-Vlanif10] ip address 192.168.1.1 24
[SW-Office-A-Vlanif10] quit

# —— 默认网关（跨网段管理必配）——
[SW-Office-A] ip route-static 0.0.0.0 0 192.168.1.254

# —— 保存 ——
[SW-Office-A] return
<SW-Office-A> save
```

> 💡 密码策略：华为默认要求密码包含**大写字母、小写字母、数字、特殊符号**的组合，且不能与账号名相似。生产环境建议 12 位以上并定期更换。

### 1_2.3 开局必做的 8 项加固动作
```latex
1. 修改默认账号与密码，删除无用账号
2. 关闭不用的服务：undo telnet server enable / undo http server enable
3. 配置 SSH + ACL 限制可管理源地址
4. 配置 console 口密码与超时锁定
5. 开启日志服务器（info-center loghost）与 NTP
6. 关闭未使用端口：shutdown
7. 配置 banner 登录警示信息
8. save 并导出配置备份
```

对应配置：

```latex
[SW] header login information "WARNING: Authorized Access Only!"
[SW] user-interface console 0
[SW-ui-console0] authentication-mode password
[SW-ui-console0] set authentication password cipher Console@123
[SW-ui-console0] idle-timeout 5 0            # 5 分钟无操作自动断开
[SW-ui-console0] quit

[SW] ntp-service unicast-server 192.168.1.200   # 时间同步
[SW] undo telnet server enable                   # 关闭明文 Telnet 服务
[SW] stelnet server enable                       # 开启 SSH
```

> ⚠️ **NTP 不是可选项**：没有时间同步的日志，在排错时等于废纸——你无法把交换机的告警和防火墙、服务器的日志对齐时间线。

---

## 1_3 配置文件与文件系统管理
### 1_3.1 两套配置：current vs saved
这是新手最常踩的坑：**改完就走，断电配置全丢**。

| 概念 | 说明 | 查看命令 |
| --- | --- | --- |
| **当前配置**（current-configuration） | 运行在内存中的配置，断电丢失 | `display current-configuration` |
| **保存配置**（saved-configuration） | 保存在 Flash 中的 `vrpcfg.zip`，下次启动加载 | `display saved-configuration` |

```latex
<SW> save                      # 内存 → Flash（★ 改完必做）
<SW> reset saved-configuration # 清空 Flash 配置（★ 必须在用户视图 < > 下执行）
<SW> reboot                    # 重启（会提示保存）
<SW> compare configuration     # 对比当前配置与下次启动配置差异
```

> ⚠️ `reset saved-configuration` 在**系统视图 **`[ ]`** 下执行会直接报错**，必须回到 `< >` 用户视图。这是 HCIA 高频考点。

### 1_3.2 配置文件备份到服务器（运维标配）
```latex
# 方式一：FTP 上传
<SW> ftp 192.168.1.100
[ftp] put vrpcfg.zip SW-Office-A_20260814.zip
[ftp] quit

# 方式二：TFTP（更简单，无需账号）
<SW> tftp 192.168.1.100 put vrpcfg.zip backup.cfg

# 方式三：指定下次启动文件（用于版本回退）
<SW> startup saved-configuration flash:/backup.cfg
<SW> display startup                 # 查看启动文件与系统软件
```

### 1_3.3 文件与系统软件管理
```latex
<SW> dir flash:                                   # 列出 Flash 文件
<SW> delete flash:/old.cfg                        # 删除文件
<SW> undelete                                     # 恢复误删
<SW> reset recycle-bin                            # 清空回收站释放空间
<SW> display startup                              # 查看启动配置/系统软件/补丁
<SW> startup system-software flash:/S5700-V200R019C10.cc   # 指定下次启动系统软件
<SW> display patch-information                    # 查看补丁
```

**割接铁律**：升级前必须 `save` + 导出配置 + 记录当前版本（`display version`）+ 确认双主控/双电源状态，否则升级失败无法回退。

### 1_3.4 配置回滚与批量导入
```latex
[SW] rollback configuration to 50        # 回滚到配置历史中的第 50 步（需先开启）
[SW] configuration commit                # 提交确认（两阶段生效机制）
```

VRP 支持**配置回退点**机制，配合 `display configuration commit list` 查看历史提交点。做大变更前先建立回退点，是割接的保险带。

---

## 1_4 接口基础与批量配置
### 1_4.1 以太网接口配置模板
```latex
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] description "Uplink-to-Core-GE1/0/1"   # 描述是运维的命根子
[SW-GigabitEthernet0/0/1] duplex full      # 全双工
[SW-GigabitEthernet0/0/1] speed 1000       # 1000M（对接老设备才手工指定，默认 auto）
[SW-GigabitEthernet0/0/1] flow-control     # 开启流控（慎用，可能造成队头阻塞）
[SW-GigabitEthernet0/0/1] mdi auto         # 网线自适应（auto/across/normal）
[SW-GigabitEthernet0/0/1] undo shutdown    # 激活端口
```

> ⚠️ **双工与速率手工指定的风险**：两端不一致（一端 auto、一端强制 100M 全双工）会导致"一端全双工、一端半双工"，表现为**大量 late collision、CRC 错误、网速极慢但能 ping 通**。正确做法：**要么两端都 auto，要么两端都手工一致**。

### 1_4.2 端口批量配置：port-group（效率神器）
```latex
# 临时端口组（不保存端口组定义）
[SW] port-group group-member gigabitethernet 0/0/1 to gigabitethernet 0/0/24
[SW-port-group] port link-type access
[SW-port-group] port default vlan 100
[SW-port-group] quit

# 永久端口组（可重复使用）
[SW] port-group office-ports
[SW-port-group-office-ports] group-member gigabitethernet 0/0/1 to 0/0/24
[SW-port-group-office-ports] port link-type access
[SW-port-group-office-ports] port default vlan 100
```

### 1_4.3 接口常见诊断命令
```latex
[SW] display interface g0/0/1                  # 单端口详细（看错包、双工、速率）
[SW] display interface brief                   # 全端口摘要（PHY/Protocol 状态）
[SW] display interface description             # 端口描述一览（交接神器）
[SW] display transceiver interface g0/0/1      # 光模块信息
[SW] reset counters interface g0/0/1           # 清空统计（排错前先清，便于观察增量）
```

**端口状态判读：**

| 显示 | 含义 | 处理 |
| --- | --- | --- |
| `up / up` | 正常 | — |
| `down / down` | 物理层不通 | 查线缆、模块、对端 |
| `up / down` | 协议层问题 | 查双工/速率/封装/VLAN |
| `*down / down` | 管理员 shutdown | `undo shutdown` |

---

## 1_5 日志、信息中心与监控
### 1_5.1 info-center 配置
```latex
[SW] info-center enable
# 批量配置时先关提示，避免刷屏打断输入
[SW] undo info-center enable
# 配置完成后务必恢复，保证审计可追溯
[SW] info-center enable

# 日志上送 syslog 服务器（生产必配）
[SW] info-center loghost 192.168.1.200
[SW] info-center source default channel 2 log level warning

# 日志缓冲区查看
[SW] display logbuffer
[SW] display trapbuffer
```

### 1_5.2 一键故障信息收集（现场救命命令）
```latex
<SW> display diagnostic-information
# 或保存到文件再导出
<SW> display diagnostic-information > flash:/diag.txt
```

这条命令会采集配置、状态、统计、日志等全量信息。**报障给华为 400 时，对方第一句就是要这个。**

### 1_5.3 健康度巡检命令组
```latex
[SW] display version            # 版本与运行时长（看有没有意外重启）
[SW] display device             # 单板/成员状态
[SW] display cpu-usage          # CPU（>70% 需关注）
[SW] display cpu-usage task     # 定位占 CPU 的进程
[SW] display memory             # 内存
[SW] display environment        # 温度
[SW] display power              # 电源
[SW] display fan                # 风扇
[SW] display health             # 健康度总览（部分型号支持）
[SW] display clock              # 系统时间（日志时间戳准不准，先看它）
[SW] display ntp-service status # NTP 同步状态（时间错了日志就没法对）
[SW] display users              # 当前在线用户（有没有陌生登录）
[SW] display cpu-defend statistics   # 上送 CPU 的报文统计（攻击排查）
```

> **踢除可疑登录**：`free user-interface vty 0`（在用户视图下执行）。发现陌生会话时，先 `display users` 确认来源，再踢除并立即改密码。

**巡检频率建议**：核心设备每日自动采集一次（`display` 输出落库），人工深度巡检每季度一次。

---

## 1_6 远程管理：Telnet 与 SSH
### 1_6.1 Telnet（仅测试环境使用）
```latex
[SW] telnet server enable
[SW] user-interface vty 0 4
[SW-ui-vty0-4] authentication-mode password
[SW-ui-vty0-4] set authentication password cipher Telnet@123
[SW-ui-vty0-4] user privilege level 15
```

> Telnet 明文传输，密码可被抓包还原。**生产环境一律禁用。**

### 1_6.2 SSH（Stelnet）完整配置（生产标准）
```latex
# 第1步 生成 RSA 密钥对（首次启用 SSH 前必做，否则服务端起不来）
[SW] rsa local-key-pair create
# 提示输入密钥长度，填 2048（低于 1024 客户端会拒绝）

# 第2步 开启 SSH 服务端
[SW] stelnet server enable

# 第3步 创建本地用户（AAA 视图）
[SW] aaa
[SW-aaa] local-user netadmin password cipher Admin@2026
[SW-aaa] local-user netadmin privilege level 15
[SW-aaa] local-user netadmin service-type ssh
[SW-aaa] quit

# 第4步 创建 SSH 用户并绑定认证方式
[SW] ssh user netadmin authentication-type password
[SW] ssh user netadmin service-type stelnet

# 第5步 VTY 接口限定协议为 SSH
[SW] user-interface vty 0 4
[SW-ui-vty0-4] authentication-mode aaa
[SW-ui-vty0-4] protocol inbound ssh
[SW-ui-vty0-4] idle-timeout 10 0

# 第6步 配套 ACL（只允许网管网段登录）
[SW] acl 2000
[SW-acl-basic-2000] rule permit source 192.168.99.0 0.0.0.255
[SW-acl-basic-2000] rule deny source any
[SW-acl-basic-2000] quit
[SW] user-interface vty 0 4
[SW-ui-vty0-4] acl 2000 inbound
```

### 1_6.3 对比速记
| 维度 | Telnet | SSH（Stelnet） |
| --- | --- | --- |
| 端口 | 23 | 22 |
| 传输 | 明文 | 加密 |
| 服务端命令 | `telnet server enable` | `stelnet server enable` + `rsa local-key-pair create` |
| VTY 协议 | `protocol inbound telnet`（或 all） | `protocol inbound ssh` |
| 生产建议 | 关闭 | 开启 + ACL 限制源 |

---

## 1_7 典型落地案例：新交换机开局全流程
### 1_7.1 需求
一台新 S5700 接入交换机上架，要求：办公 VLAN 100、监控 VLAN 200、上行 Trunk 放行两个 VLAN、管理 IP 192.168.99.11/24 网关 .254、只能网管网段 SSH 登录、未用端口关闭。

### 1_7.2 地址与端口规划表
| 项目 | 规划 |
| --- | --- |
| 管理 VLAN / IP | VLAN 99 / 192.168.99.11 /24，网关 192.168.99.254 |
| 办公 | VLAN 100，端口 GE0/0/1–10 |
| 监控 | VLAN 200，端口 GE0/0/11–20 |
| 上行 | GE0/0/24，Trunk 放行 99/100/200 |
| 未用 | GE0/0/21–23、GE0/0/25–28 关闭 |

### 1_7.3 完整配置
```latex
<Huawei> system-view
[Huawei] sysname ACC-Office-01
[ACC-Office-01] vlan batch 99 100 200

# 办公端口
[ACC-Office-01] port-group pg-office
[ACC-Office-01-port-group-pg-office] group-member gigabitethernet 0/0/1 to 0/0/10
[ACC-Office-01-port-group-pg-office] port link-type access
[ACC-Office-01-port-group-pg-office] port default vlan 100
[ACC-Office-01-port-group-pg-office] stp edged-port enable
[ACC-Office-01-port-group-pg-office] quit

# 监控端口
[ACC-Office-01] port-group pg-cctv
[ACC-Office-01-port-group-pg-cctv] group-member gigabitethernet 0/0/11 to 0/0/20
[ACC-Office-01-port-group-pg-cctv] port link-type access
[ACC-Office-01-port-group-pg-cctv] port default vlan 200
[ACC-Office-01-port-group-pg-cctv] stp edged-port enable
[ACC-Office-01-port-group-pg-cctv] quit

# 上行 Trunk
[ACC-Office-01] interface gigabitethernet 0/0/24
[ACC-Office-01-GigabitEthernet0/0/24] port link-type trunk
[ACC-Office-01-GigabitEthernet0/0/24] port trunk allow-pass vlan 99 100 200
[ACC-Office-01-GigabitEthernet0/0/24] undo port trunk allow-pass vlan 1
[ACC-Office-01-GigabitEthernet0/0/24] quit

# 管理 IP + 网关
[ACC-Office-01] interface Vlanif 99
[ACC-Office-01-Vlanif99] ip address 192.168.99.11 24
[ACC-Office-01-Vlanif99] quit
[ACC-Office-01] ip route-static 0.0.0.0 0 192.168.99.254

# 关闭未用端口
[ACC-Office-01] port-group pg-unused
[ACC-Office-01-port-group-pg-unused] group-member gigabitethernet 0/0/21 to 0/0/23
[ACC-Office-01-port-group-pg-unused] shutdown
[ACC-Office-01-port-group-pg-unused] quit
```

SSH 与加固部分按 1_6.2 与 1_2.3 追加，最后 `save`。

### 1_7.4 验收测试清单
| # | 验收项 | 命令 | 合格标准 |
| --- | --- | --- | --- |
| 1 | 端口归属正确 | `display port vlan` | 1–10 在 VLAN 100，11–20 在 VLAN 200 |
| 2 | 上行放行正确 | `display interface g0/0/24 trunk` | allow-pass 含 99/100/200，无 VLAN 1 |
| 3 | 管理 IP 可管 | `display ip interface brief` | Vlanif99 up/up |
| 4 | 跨网段可管 | `ping 192.168.99.254` | 通 |
| 5 | SSH 可登录 | 从网管机 ssh | 成功；从非网管网段应失败 |
| 6 | Telnet 已关 | `display telnet server status` | 关闭 |
| 7 | 配置已存 | `display saved-configuration` | 与当前一致 |
| 8 | 未用口已关 | `display interface brief` | 21–23 为 *down |

---

## 1_8 排错清单：设备"管不上 / 配不进 / 存不下"
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 可能原因 | 定位命令 | 处理 |
| --- | --- | --- | --- |
| **SSH 连不上** | 未生成 RSA 密钥 | `display ssh server status` | `rsa local-key-pair create` |
| SSH 连不上 | VTY 未限定/未开 SSH | `display ssh server` | `protocol inbound ssh` + `stelnet server enable` |
| SSH 连不上 | ACL 拦了源 | `display acl 2000`（看计数） | 放行网管网段 |
| SSH 连不上 | 用户服务类型错 | `display local-user` | `service-type ssh` |
| **Telnet 能连 SSH 不能** | 服务端/协议不匹配 | `display ssh server status` | 补齐 SSH 全套配置 |
| **配不进系统视图** | 用户级别低 | `display local-user username X` | 提权到 3 以上 |
| 命令敲了不生效 | 视图不对 | 看提示符 `[SW-xxx]` | 回对应视图 |
| **存不下配置** | 在 `[ ]` 视图执行 reset/save 参数错 | 看提示符 | `return` 到 `< >` 再 `save` |
| 配置保存后重启丢失 | 指定了错误的启动文件 | `display startup` | 重新 `save` 并核对 startup |
| Flash 空间不足 | 回收站/老版本堆积 | `dir flash:` | `reset recycle-bin`、删除老版本 |
| 管理 IP ping 不通 | VLANIF 无 UP 端口 | `display ip interface brief` | 该 VLAN 需有活跃端口 |

> **排错顺序建议**：先看"能不能到"（ping 管理 IP）→ 再看"服务起没起"（`display ssh server status`）→ 最后看"谁被拦了"（ACL 计数）。

---

## 1_9 场景笔记与验证
### 1_9.1 本板块要记的三类笔记
| 笔记 | 记什么 | 示例 |
| --- | --- | --- |
| **开局模板** | 一套能直接粘贴的模板（命名/时间/VLAN/管理 IP/SSH/加固） | 存成 `开局模板.cfg`，新设备改 5 处即可 |
| **验收清单** | 8 项验收表，每次开局逐条打勾 | 见 1_7.4 |
| **坑本** | `reset saved-configuration` 必须在用户视图；SSH 必须先建密钥 | 一句话 + 一条命令 |

### 1_9.2 验证三板斧（本板块版）
```latex
第1步 看状态：display ip interface brief / display interface brief
第2步 看表项：display saved-configuration（存没存）、display startup（启动文件对不对）
第3步 打流量：ping 网关 / 从网管机 ssh 登录（真连一次，别只看配置）
```

### 1_9.3 一个值得养成的小习惯
**每次 **`save`** 前先 **`compare configuration`，看一眼"我这次到底改了什么"。这个动作能避免 90% 的"我明明没改这个怎么坏了"。

---

## 1_10 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | `reset saved-configuration` 在 `[ ]` 下执行 | 必须在**用户视图 **`< >` 下执行，否则报错 |
| 2 | 改完配置不保存 | 当前配置在内存，断电丢失，`save`** 是肌肉记忆** |
| 3 | SSH 配完连不上 | 漏了 `rsa local-key-pair create`（第一步就漏，最常见） |
| 4 | 认为 level 15 是标配 | 生产应分级：运维 2、管理员 3 |
| 5 | Console 不配密码 | Console 是最后通道，但也要配密码与 idle-timeout |
| 6 | 手工指定双工速率 | 两端必须一致，否则产生 late collision/CRC，能 ping 通但极慢 |
| 7 | 端口不写 description | 三个月后你自己都认不出这根线去哪 |
| 8 | 日志不配 NTP | 时间对不齐，跨设备排错无法关联 |

---

# 板块2 · 以太网交换与 VLAN 技术
> 定位：交换是园区网的骨骼。HCIA 要求"会划分、能互通"，HCIP 要求"会规划、懂 Tag 走向"，HCIE 要求"能把它放进 VXLAN/虚拟化架构里做设计取舍"。
> 核心命题只有一个：**一个报文从某端口进、从某端口出，它的 VLAN Tag 在整个过程中被怎么处理？** 把这个问题想明白，Access/Trunk/Hybrid/QinQ 全部通吃。

## 2_1 以太网交换基础
### 2_1.1 交换机转发三动作
| 动作 | 触发条件 | 说明 |
| --- | --- | --- |
| **泛洪（Flooding）** | 目的 MAC 不在 MAC 表中 | 从同 VLAN 的其他所有端口发出 |
| **转发（Forwarding）** | 目的 MAC 在表中且端口明确 | 单播点到点 |
| **丢弃（Discarding）** | 目的 MAC 对应端口 = 接收端口；或策略拒绝 | 不转发 |

### 2_1.2 MAC 地址表学习机制
```latex
1. 交换机从端口 X 收到帧 → 读取源 MAC → 写入 MAC 表（MAC ↔ 端口 ↔ VLAN）
2. 查目的 MAC：
   ├─ 表中有 → 从对应端口单播转发
   ├─ 表中无 → 在同 VLAN 内泛洪（组播/广播同样泛洪）
   └─ 对应端口=入端口 → 丢弃
3. 表项老化时间默认 300 秒，超时删除
```

MAC 表管理命令：

```latex
[SW] display mac-address                                    # 查看 MAC 表
[SW] display mac-address dynamic                            # 动态表项
[SW] display mac-address vlan 10                            # 按 VLAN 过滤
[SW] display mac-address interface g0/0/1                   # 按端口过滤
[SW] display mac-address aging-time                         # 老化时间
[SW] mac-address timer aging 300                            # 修改老化时间
[SW] mac-address timer no-aging                             # 不老化（静态网络）
[SW] mac-address static 0000-0012-0034 gigabitethernet 1/0/1 vlan 10   # 静态绑定
[SW] mac-address blackhole 0000-0012-0035 vlan 10           # 黑洞 MAC（丢弃匹配报文）
[SW] mac-address flapping detection                         # MAC 漂移检测（查环路）
[SW] display mac-address flapping record                    # 查看漂移记录
```

> 🚨 **MAC 地址漂移 = 二层环路的最强信号**。当同一 MAC 在两个端口间反复出现，说明存在环路或有人伪造 MAC。生产环境务必开启漂移检测：

```latex
[SW] mac-address flapping detection
[SW] interface g0/0/1
[SW-GigabitEthernet0/0/1] mac-address flapping trigger error-down
```

### 2_1.3 以太网帧格式与 802.1Q Tag
```latex
标准以太帧（Ethernet II）
┌──────────┬──────────┬────────┬────────┬─────┬──────┐
│ 目的MAC 6B│ 源MAC 6B  │ TPID 2B │ PCP/DEI│数据  │ FCS  │
└──────────┴──────────┴────────┴────────┴─────┴──────┘
                       0x8100   │VID 12b│

802.1Q Tag 字段（4 字节）：
┌─────────────┬───┬───┬──────────────────┐
│ TPID 16bit  │PRI│CFI│  VID 12bit       │
│ (0x8100)    │3b │1b │ (1~4094)         │
└─────────────┴───┴───┴──────────────────┘
```

| 字段 | 含义 |
| --- | --- |
| TPID | Tag Protocol Identifier，固定 0x8100（QinQ 可改 0x8200/0x88A8） |
| PRI（802.1p） | 3 bit 优先级，0–7，用于 QoS |
| CFI/DEI | 规范格式指示位，以太网中固定 0 |
| VID | VLAN ID，12 bit，可用范围 **1–4094**（0 与 4095 保留） |

**帧长考点**：标准以太帧 64–1518 字节；带 802.1Q Tag 的帧最大 **1522** 字节；支持巨帧（Jumbo Frame）可到 9000+ 字节，需**全程设备一致**，否则分片/丢弃。

---

## 2_2 VLAN 原理与规划
### 2_2.1 VLAN 解决什么问题
+ **隔离广播域**：ARP 广播不再全网泛滥，抑制广播风暴；
+ **提升安全**：不同部门二层隔离，跨 VLAN 必须走三层（可加 ACL）；
+ **简化管理**：按业务而非物理位置组网，工位调整不改线。

### 2_2.2 VLAN ID 划分
| 范围 | 用途 |
| --- | --- |
| 0、4095 | 系统保留，不可用 |
| **1** | 默认 VLAN，**所有端口默认属于 VLAN 1**（生产建议：清空 VLAN 1 的业务端口） |
| 2–1001 | 普通 VLAN，日常使用 |
| 1002–1005 | 传统保留（FDDI/Token Ring 兼容） |
| 1006–4094 | 扩展 VLAN |

### 2_2.3 VLAN 规划最佳实践
```latex
按业务 + 按安全等级双维度划分，VLAN ID 与网段绑定，形成可读的映射关系：

VLAN 10  办公有线    192.168.10.0/24    安全等级：中
VLAN 20  办公无线    192.168.20.0/24    安全等级：中
VLAN 30  视频监控    192.168.30.0/24    安全等级：高（禁止互访、禁止上外网）
VLAN 40  IP 电话     192.168.40.0/24    安全等级：中（需 QoS 优先）
VLAN 50  访客        192.168.50.0/24    安全等级：低（仅 Internet）
VLAN 99  设备管理    192.168.99.0/24    安全等级：最高（仅网管可达）
VLAN 100 上行互联    10.0.0.0/30        三层链路
```

规划原则：

1. **一个 VLAN 一个网段**，第三位 octet 与 VLAN ID 对齐，排错时一眼看穿；
2. **管理 VLAN 独立**，不与业务混用；
3. **预留扩展段**，避免后期 VLAN ID 断号；
4. **语音/视频单独 VLAN**，便于打 QoS 标记；
5. **Trunk 上禁止放行 VLAN 1**，且修剪不必要的 VLAN（`port trunk allow-pass` 精确指定，不用 `all`）。

### 2_2.4 VLAN 创建
```latex
# 单个创建
[SW] vlan 100
[SW-vlan100] description Sales-Dept
[SW-vlan100] quit

# 批量创建（推荐）
[SW] vlan batch 10 20 30 40          # 不连续
[SW] vlan batch 10 to 100            # 连续

# 查看
[SW] display vlan
[SW] display vlan 10
[SW] display vlan summary
```

---

## 2_3 端口类型深度解析
### 2_3.1 三种链路类型
| 类型 | Tag 处理 | 典型场景 |
| --- | --- | --- |
| **Access** | 收：无 Tag 打上 PVID；有 Tag 且与 PVID 一致则收，否则丢弃。发：**剥离 Tag** | PC、打印机、摄像头、AP（非隧道模式） |
| **Trunk** | 收：无 Tag 打 PVID；有 Tag 且允许通过则收。发：**PVID 相同剥离，其他保留 Tag** | 交换机互联、交换机-路由器、交换机-服务器（多 VLAN） |
| **Hybrid** | 可**逐 VLAN 指定** tagged 或 untagged，收发都灵活 | VoIP + 数据共口、虚拟机接入、特殊组网 |

### 2_3.2 收发行为对照表（考试高频）
**Access 端口：**

| 方向 | 帧状态 | 处理 |
| --- | --- | --- |
| 收 | 无 Tag | 打上 PVID |
| 收 | 有 Tag 且 VID = PVID | 接收 |
| 收 | 有 Tag 且 VID ≠ PVID | **丢弃** |
| 发 | — | **剥离 Tag** 后发送 |

**Trunk 端口：**

| 方向 | 帧状态 | 处理 |
| --- | --- | --- |
| 收 | 无 Tag | 打上 **PVID**（默认 VLAN 1） |
| 收 | 有 Tag 且 VID ∈ allow-pass | 接收 |
| 收 | 有 Tag 且 VID ∉ allow-pass | **丢弃** |
| 发 | VID = PVID | **剥离 Tag** |
| 发 | VID ≠ PVID 且在允许列表 | 保留 Tag |

**Hybrid 端口：**

| 方向 | 处理 |
| --- | --- |
| 收 无 Tag | 打 PVID，若 PVID 在 tagged/untagged 列表中则接收，否则丢弃 |
| 收 有 Tag | VID 在列表中则接收，否则丢弃 |
| 发 | 按该 VLAN 配置的 **tagged/untagged** 决定保留或剥离 |

### 2_3.3 Access/Trunk 配置
```latex
# Access
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] port link-type access
[SW-GigabitEthernet0/0/1] port default vlan 100

# Trunk
[SW] interface gigabitethernet 0/0/24
[SW-GigabitEthernet0/0/24] port link-type trunk
[SW-GigabitEthernet0/0/24] port trunk allow-pass vlan 10 20 30     # 精确放行，推荐
[SW-GigabitEthernet0/0/24] port trunk pvid vlan 99                 # 修改 PVID（谨慎！）
[SW-GigabitEthernet0/0/24] undo port trunk allow-pass vlan 1       # 去掉默认 VLAN 1
```

> ⚠️ **Trunk 两端 PVID 不一致的后果**：一端收到对端"剥离 Tag 发出的无标记帧"时，会按本端 PVID 打标，导致 VLAN 错位（本该 VLAN 10 的流量跑到 VLAN 99）。**两端 PVID 必须一致**，或干脆两边都改成同一个无业务 VLAN。
> ⚠️ Access 改 Trunk 失败处理：端口上若已配 `port default vlan`，需先清除：

```latex
[SW-GigabitEthernet0/0/24] undo port default vlan
[SW-GigabitEthernet0/0/24] port link-type trunk
```

### 2_3.4 Hybrid 配置
```latex
[SW] interface gigabitethernet 0/0/5
[SW-GigabitEthernet0/0/5] port link-type hybrid
[SW-GigabitEthernet0/0/5] port hybrid pvid vlan 10           # 无标记帧归属 VLAN 10
[SW-GigabitEthernet0/0/5] port hybrid vlan 10 20 untagged    # VLAN 10/20 发出时剥离 Tag
[SW-GigabitEthernet0/0/5] port hybrid vlan 100 tagged        # VLAN 100 发出时保留 Tag
```

**Hybrid 经典场景：语音 + 数据共口**——IP 电话串在 PC 前面，PC 的数据帧无标记进 VLAN 10（untagged），电话的语音帧带 VLAN 40 标记（tagged），一个物理口承载两个业务。

### 2_3.5 端口 VLAN 验证命令
```latex
[SW] display port vlan                      # 端口与 VLAN 归属总表（最常用）
[SW] display port vlan g0/0/1               # 单端口
[SW] display vlan 10                        # VLAN 内有哪些端口
[SW] display interface g0/0/24 trunk        # Trunk 详情（allow-pass、PVID）
```

---

## 2_4 跨交换机 VLAN 通信（Trunk 实战）
### 2_4.1 典型拓扑
```latex
   PC1(VLAN10)                PC2(VLAN20)              PC3(VLAN10)
   192.168.10.1              192.168.20.1              192.168.10.2
        │ E1/0/5                  │ E1/0/10                  │ E1/0/20
        │ access                  │ access                   │ access
   ┌────┴─────────────────────────┴──────┐          ┌─────────┴───────┐
   │            SW1                      │          │      SW2        │
   │        VLAN 10 / 20                 │  Trunk   │   VLAN 10 / 20  │
   │                              E1/0/24├──────────┤E1/0/24          │
   └─────────────────────────────────────┘          └─────────────────┘
                    allow-pass vlan 10 20（两端一致）
```

### 2_4.2 完整配置（两端对称）
```latex
# ================= SW1 =================
[SW1] vlan batch 10 20
[SW1] interface ethernet 1/0/5
[SW1-Ethernet1/0/5] port link-type access
[SW1-Ethernet1/0/5] port default vlan 10
[SW1-Ethernet1/0/5] quit

[SW1] interface ethernet 1/0/10
[SW1-Ethernet1/0/10] port link-type access
[SW1-Ethernet1/0/10] port default vlan 20
[SW1-Ethernet1/0/10] quit

[SW1] interface ethernet 1/0/24
[SW1-Ethernet1/0/24] port link-type trunk
[SW1-Ethernet1/0/24] port trunk allow-pass vlan 10 20
[SW1-Ethernet1/0/24] undo port trunk allow-pass vlan 1
[SW1-Ethernet1/0/24] quit

# ================= SW2 =================
[SW2] vlan batch 10 20
[SW2] interface ethernet 1/0/20
[SW2-Ethernet1/0/20] port link-type access
[SW2-Ethernet1/0/20] port default vlan 10
[SW2-Ethernet1/0/20] quit

[SW2] interface ethernet 1/0/24
[SW2-Ethernet1/0/24] port link-type trunk
[SW2-Ethernet1/0/24] port trunk allow-pass vlan 10 20
[SW2-Ethernet1/0/24] undo port trunk allow-pass vlan 1
[SW2-Ethernet1/0/24] quit
```

### 2_4.3 验证与测试
```latex
[SW1] display interface e1/0/24 trunk
# 关键看：Trunk VLAN Allowed（10, 20）、PVID（两端一致）

# 终端侧
PC1（VLAN 10，192.168.10.1/24）→ ping 192.168.10.2（PC3，跨交换机同 VLAN）→ 通
PC1 → ping 192.168.20.1（PC2，不同 VLAN）→ 不通（二层隔离，需三层）
```

### 2_4.4 Trunk 故障排查表
| 现象 | 原因 | 处理 |
| --- | --- | --- |
| 同 VLAN 跨设备不通 | 一端漏 allow-pass | 两端 `display interface xxx trunk` 对比 |
| 部分 VLAN 通部分不通 | allow-pass 列表不一致 | 统一放行列表 |
| Trunk 口配不上 | 端口残留 `port default vlan` | `undo port default vlan` 再改类型 |
| VLAN 错位（流量跑到别的 VLAN） | 两端 PVID 不一致 | 统一 PVID 或改为无业务 VLAN |
| 全网莫名互通 | Trunk 放行了 VLAN 1 / 用了 all | 精确放行 + `undo port trunk allow-pass vlan 1` |

---

## 2_5 端口组与批量操作
### 2_5.1 端口组的两种形态
```latex
# 第1步 临时端口组（不留存定义，一次性批量）
[SW] port-group group-member gigabitethernet 0/0/1 to 0/0/24
[SW-port-group] port link-type access
[SW-port-group] port default vlan 100

# 第2步 永久端口组（可重复使用，推荐生产用）
[SW] port-group pg-office
[SW-port-group-pg-office] group-member gigabitethernet 0/0/1 to 0/0/24
[SW-port-group-pg-office] port link-type access
[SW-port-group-pg-office] port default vlan 100
```

### 2_5.2 在 VLAN 视图下批量加端口
```latex
[SW] vlan 10
[SW-vlan10] port gigabitethernet 0/0/1 to 0/0/29
```

### 2_5.3 端口限速（qos lr）
```latex
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] qos lr outbound cir 2000 cbs 20000   # 出方向限速 2 Mbps
```

---

## 2_6 VLAN 间路由（三层交换）
不同 VLAN 之间通信必须过三层设备，主流做法是三层交换机上的 **VLANIF 接口**作网关。详细的转发流程、配置与验收见**板块5**（三层交换与 DHCP 服务），此处只需记住结论：

+ **二层交换机**只能在同一广播域内转发；
+ **VLANIF** 是三层逻辑接口，需要该 VLAN 内有 UP 的物理端口才会 UP；
+ 三层交换机首包上 CPU 建表，后续报文由 ASIC 硬件转发（"一次路由，多次交换"）。

---

## 2_7 MUX VLAN（同 VLAN 内二层隔离）
### 2_7.1 应用场景
酒店、校园网、出租办公：所有用户都在一个网段，但要求**用户之间不能互访，只能访问服务器/网关**。传统做法要给每个用户一个 VLAN + 一个网段，地址浪费；MUX VLAN 用一个主 VLAN 解决。

| 角色 | 说明 |
| --- | --- |
| **Principal VLAN**（主 VLAN） | 可以与所有从 VLAN 通信 |
| **Separate VLAN**（隔离型从 VLAN） | 内部完全隔离，只能与主 VLAN 通信 |
| **Group VLAN**（互通型从 VLAN） | 内部可互通，也可与主 VLAN 通信 |

### 2_7.2 配置
```latex
[SW] vlan 100
[SW-vlan100] mux-vlan                              # 设为主 VLAN
[SW-vlan100] subordinate separate 200              # 隔离型从 VLAN
[SW-vlan100] subordinate group 300                 # 互通型从 VLAN
[SW-vlan100] quit

[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] port link-type access
[SW-GigabitEthernet0/0/1] port default vlan 200
[SW-GigabitEthernet0/0/1] port mux-vlan enable     # ★ 接口必须开启
```

---

## 2_8 QinQ 双层 VLAN（运营商/大型园区）
### 2_8.1 原理
在用户 VLAN Tag（内层）外面再打一层运营商 VLAN Tag（外层），把 4094 个 VLAN 扩展成 4094 × 4094，解决运营商承接多客户时的 VLAN 资源不足问题。

```latex
原始帧 → [用户 C-Tag (VID 10)] → [运营商 S-Tag (VID 1000)] → 数据
        内层（客户自主管理）      外层（运营商统一管理）
```

### 2_8.2 基本 QinQ 配置（端口固定打外层 Tag）
```latex
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] port link-type dot1q-tunnel
[SW-GigabitEthernet0/0/1] port default vlan 1000     # 固定外层 Tag
```

### 2_8.3 灵活 QinQ（按内层 VLAN 打不同外层 Tag）
```latex
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] port link-type hybrid
[SW-GigabitEthernet0/0/1] port hybrid untagged vlan 1000 1010
[SW-GigabitEthernet0/0/1] qinq vlan-translation enable
[SW-GigabitEthernet0/0/1] port vlan-stacking vlan 10 to 20 stack-vlan 1000
[SW-GigabitEthernet0/0/1] port vlan-stacking vlan 30 to 40 stack-vlan 1010
```

> QinQ 场景要同步把接口 MTU 调大（多 4 字节 Tag），否则大包被丢。

---

## 2_9 GVRP：VLAN 自动注册
GVRP（GARP VLAN Registration Protocol）让交换机之间自动同步 VLAN 信息，减少手工创建。

```latex
[SW] gvrp                                          # 全局开启
[SW] interface gigabitethernet 0/0/24
[SW-GigabitEthernet0/0/24] port link-type trunk
[SW-GigabitEthernet0/0/24] port trunk allow-pass vlan all
[SW-GigabitEthernet0/0/24] gvrp                    # 接口开启
```

> **现实提醒**：GVRP 只同步 VLAN 的存在，不同步端口归属；而且自动注册容易把不该有的 VLAN 扩散出去。**生产环境多数关闭 GVRP，用手工规划 + 网管批量下发**。考试层面要记住它的作用与配置命令即可。

---

## 2_10 典型落地案例：单交换机多业务 VLAN 划分
### 2_10.1 需求
一台接入交换机承载三类业务：办公（VLAN 10，1–10 口）、监控（VLAN 20，11–20 口）、语音 + 数据共口（VLAN 40 语音 tagged + VLAN 10 数据 untagged，21–22 口），上行 Trunk 放行 10/20/40。

### 2_10.2 配置
```latex
[SW] vlan batch 10 20 40

# 办公
[SW] port-group pg-office
[SW-port-group-pg-office] group-member gigabitethernet 0/0/1 to 0/0/10
[SW-port-group-pg-office] port link-type access
[SW-port-group-pg-office] port default vlan 10
[SW-port-group-pg-office] stp edged-port enable

# 监控
[SW] port-group pg-cctv
[SW-port-group-pg-cctv] group-member gigabitethernet 0/0/11 to 0/0/20
[SW-port-group-pg-cctv] port link-type access
[SW-port-group-pg-cctv] port default vlan 20
[SW-port-group-pg-cctv] stp edged-port enable

# 语音 + 数据（Hybrid）
[SW] interface gigabitethernet 0/0/21
[SW-GigabitEthernet0/0/21] port link-type hybrid
[SW-GigabitEthernet0/0/21] port hybrid pvid vlan 10
[SW-GigabitEthernet0/0/21] port hybrid vlan 10 untagged
[SW-GigabitEthernet0/0/21] port hybrid vlan 40 tagged

# 上行
[SW] interface gigabitethernet 0/0/24
[SW-GigabitEthernet0/0/24] port link-type trunk
[SW-GigabitEthernet0/0/24] port trunk allow-pass vlan 10 20 40
[SW-GigabitEthernet0/0/24] undo port trunk allow-pass vlan 1
```

### 2_10.3 验收
| 验收项 | 命令 | 合格标准 |
| --- | --- | --- |
| 端口归属 | `display port vlan` | 1–10→10，11–20→20，21→hybrid 10/40 |
| 上行放行 | `display interface g0/0/24 trunk` | 含 10/20/40，无 VLAN 1 |
| 同 VLAN 互通 | PC1 ping PC2（均 VLAN 10） | 通 |
| 异 VLAN 隔离 | PC1 ping PC3（VLAN 20） | 不通（未开三层） |
| MAC 学习 | `display mac-address vlan 10` | 能看到 PC 的 MAC |

---

## 2_11 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 排查命令 | 常见根因 |
| --- | --- | --- |
| 同 VLAN 两台 PC 不通 | `display port vlan`、`display mac-address` | 端口 VLAN 归属错；或一端 Access 一端 Trunk |
| 跨设备同 VLAN 不通 | 两端 `display interface xxx trunk` | allow-pass 漏配 / PVID 不一致 |
| VLANIF 起不来 | `display ip interface brief` | 该 VLAN 内无任何 UP 端口 |
| 新建 VLAN 没生效 | `display vlan summary` | 忘了批量创建或端口未加入 |
| 全网广播风暴 | `display mac-address flapping record` | 环路（见板块3） |
| 语音电话拿不到语音 VLAN | `display port vlan` | Hybrid 未 tagged VLAN 40 |

> **现场故事**：某客户报"监控有一半摄像头掉线"。现场一看，接入交换机上行 Trunk 只放行了 VLAN 10 20，而新装的摄像头划到了 VLAN 30。**一句 **`port trunk allow-pass vlan 30`** 解决**，但排查花了两小时——因为大家都在查摄像头本身和网线。教训：跨设备不通，**第一时间对比两端 Trunk 放行列表**，这是性价比最高的第一刀。

---

## 2_12 场景笔记与验证
### 2_12.1 本板块要沉淀的笔记
| 笔记类型 | 内容 |
| --- | --- |
| **Tag 走向图** | 自己画一张 Access/Trunk/Hybrid 的收发表（收无 Tag/收有 Tag/发），考试前默画一遍 |
| **VLAN 规划模板** | 业务—VLAN ID—网段—安全等级四列表格，新项目直接套 |
| **坑本** | Trunk 两端 PVID 不一致、Access 改 Trunk 要先 undo default vlan、Hybrid 忘 tagged 语音 VLAN |

### 2_12.2 验证三板斧（本板块版）
```latex
第1步 看状态：display port vlan / display vlan 10        端口在哪个 VLAN？
第2步 看表项：display mac-address vlan 10                MAC 学到了吗？在哪个口？
第3步 打流量：同 VLAN PC 互 ping（通）；跨 VLAN 互 ping（不通才对）
```

**加一刀**：`display interface g0/0/24 trunk` 看 PVID 与 allow-pass——跨设备问题 80% 出在这里。

### 2_12.3 抓包验证（强烈建议做一次）
在 Trunk 链路上抓包，亲眼看到：

+ 带 Tag 的帧（0x8100 + VID）在交换机之间穿梭；
+ 从 Access 口出去的帧（PC 侧）没有 Tag。

这一眼，抵得上背十遍收发表。

---

## 2_13 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | Trunk 发所有 VLAN 都带 Tag | **PVID 那个 VLAN 发出时剥离 Tag** |
| 2 | Access 口能收带 Tag 的帧 | 只有 **VID = PVID** 才收，否则丢弃 |
| 3 | Hybrid 是"高级 Trunk" | 它是**逐 VLAN 决定 tagged/untagged**，收发都灵活 |
| 4 | VLAN 1 无害 | 默认所有端口都在 VLAN 1，生产必须清掉并禁止 Trunk 放行 |
| 5 | VLANIF 建了就 UP | 需要该 VLAN 内有 **UP 的物理端口** |
| 6 | 802.1Q 帧最大 1518 | 带 Tag 后最大 **1522** 字节 |
| 7 | 端口改类型失败是设备 bug | 先 `undo port default vlan`（Access）或清原有配置 |
| 8 | MUX VLAN 从 VLAN 之间能通 | Separate 型**完全隔离**，只能与主 VLAN 通 |

---

# 板块3 · 生成树与二层环路防护
> 定位：环路是二层网络的头号杀手——一个没配 STP 的环路能在 30 秒内打满 CPU、冲垮全网。本板块从"为什么要有 STP"讲到"MSTP 多实例负载均衡设计与防护三件套"，并给出可直接复用的园区网模板。
> 能力要求：HCIA 会开、会看；HCIP 会设计根桥与实例映射、会配保护；HCIE 能在大型园区里做 STP 与堆叠/Eth-Trunk 的方案取舍。

## 3_1 为什么需要生成树
### 3_1.1 二层环路的三大灾难
| 灾难 | 成因 | 表现 |
| --- | --- | --- |
| **广播风暴** | 广播帧在环路中无限循环 | 全网带宽被占满，CPU 飙高，业务全断 |
| **MAC 地址表震荡** | 同一 MAC 从不同端口反复学到 | MAC 表反复刷新，转发错乱 |
| **帧重复** | 同一单播帧多次到达 | 上层协议异常（TCP 重传、应用报错） |

> **现场故事**：会议室员工把网线两端插到同一台交换机的两个口，30 秒内整层楼断网。运维赶到时，交换机 CPU 98%，指示灯狂闪，所有 PC 打不开任何页面。拔掉那根线的瞬间，全网恢复。**防御手段就两条：STP + 边缘端口/BPDU 保护**——这一条配置价值等于一次全楼业务中断。

### 3_1.2 STP 的核心思想
**逻辑上阻塞某些端口，把有环的物理拓扑修剪成无环的树形拓扑**，同时保留冗余链路——主链路断了，阻塞端口自动打开，实现冗余。

```latex
物理拓扑（有环）              逻辑拓扑（STP 修剪后）

   SW1 ───── SW2                SW1 ══════ SW2
    │  ╲     ╱  │                  │          │
    │    ╲ ╱    │                  │          │
    │    ╱ ╲    │                  │          │
    │  ╱     ╲  │                  │          │
   SW3 ───── SW4                SW3 ══════ SW4
                                   ×一条链路被阻塞（逻辑断开，物理仍在）
```

### 3_1.3 三个选举过程（必须按顺序理解）
```latex
第1步 选根桥（Root Bridge）
   → 全网唯一的树根，比较 桥ID（优先级 + MAC），越小越优
   → 优先级默认 32768，步长 4096

第2步 选根端口（Root Port，每台非根交换机一个）
   → 到根桥路径开销最小的端口

第3步 选指定端口（Designated Port，每条链路一个）
   → 链路两端中到根桥更优的那个端口
   → 剩下的端口 = 阻塞端口（Alternate/Backup）
```

**端口开销标准（cost）对照：**

| 链路速率 | IEEE 802.1D-1998 | IEEE 802.1t（华为默认推荐） |
| --- | --- | --- |
| 10 Mbps | 100 | 2,000,000 |
| 100 Mbps | 19 | 200,000 |
| 1 Gbps | 4 | 20,000 |
| 10 Gbps | 2 | 2,000 |
| 40 Gbps | 1 | 500 |

> 华为默认使用 802.1t 标准，可用 `stp pathcost-standard { dot1d-1998 | dot1t | legacy }` 切换。**同一网络内所有设备必须一致**，否则路径计算失真。

---

## 3_2 STP / RSTP / MSTP 三代对比
> **本节导读**：三代协议的差异，本质上都围绕同一件事——**收敛能有多快、冗余能不能用起来**。看表时抓住这两条主线就不会乱。

| 特性 | STP（802.1D） | RSTP（802.1w） | MSTP（802.1s） |
| --- | --- | --- | --- |
| 收敛时间 | 30–50 秒 | **1–2 秒** | 1–2 秒 |
| 端口角色 | Root/Designated/Block | + **Alternate/Backup** | 同 RSTP（按实例） |
| 端口状态 | Disabled/Blocking/Listening/Learning/Forwarding（5 种） | Discarding/Learning/Forwarding（3 种） | 同 RSTP |
| 负载均衡 | 不支持 | 不支持（所有 VLAN 一棵树） | **支持（多实例多棵树）** |
| VLAN 感知 | 不感知 | 不感知 | **感知（VLAN → 实例映射）** |
| 华为命令 | `stp mode stp` | `stp mode rstp` | `stp mode mstp`（默认） |

**为什么 RSTP 快？** 关键在于**Proposal/Agreement 握手机制**与**边缘端口**概念：点到点链路可逐段快速协商进入转发，不必等 2 个 Forward Delay（各 15 秒）。

**RSTP 端口角色补充：**

| 角色 | 含义 |
| --- | --- |
| Root Port | 去往根桥最优的端口 |
| Designated Port | 每条网段向下游转发 BPDU 的端口 |
| **Alternate Port** | 根端口的备份（从别的交换机听到更优 BPDU） |
| **Backup Port** | 指定端口的备份（本交换机的另一个端口收到自己发的 BPDU） |

---

## 3_3 STP/RSTP 配置
### 3_3.1 基础配置
```latex
[SW] stp enable                            # 开启 STP（华为默认开启）
[SW] stp mode rstp                         # 切换为 RSTP（推荐）
[SW] stp priority 8192                     # 设置桥优先级（4096 的倍数）
[SW] stp root primary                      # 强制成为主根桥（等价于 priority 0）
[SW] stp root secondary                    # 设为备份根桥（等价于 priority 4096）
[SW] stp pathcost-standard dot1t           # 统一开销标准
[SW] stp timer forward-delay 1500          # 转发延迟（厘秒，谨慎修改）
[SW] stp bridge-diameter 5                 # 网络直径（影响 Hello/Max Age 自动计算）
```

### 3_3.2 端口级配置
```latex
[SW] interface ethernet 0/0/1
[SW-Ethernet0/0/1] stp cost 200                  # 手工指定路径开销（影响选路）
[SW-Ethernet0/0/1] stp port priority 16          # 端口优先级（16 的倍数）
[SW-Ethernet0/0/1] stp edged-port enable         # 边缘端口（接终端，跳过 30 秒等待）
[SW-Ethernet0/0/1] stp point-to-point force-true # 强制点到点模式
```

### 3_3.3 边缘端口（必配！）
接 PC、打印机、摄像头、服务器的端口**必须配边缘端口**，否则：

+ PC 开机后要等 **30 秒**才能上网（Listening + Learning）；
+ 用户频繁报"开机后一会儿才能上网"的诡异故障。

```latex
# 单端口
[SW-GigabitEthernet0/0/1] stp edged-port enable

# 全局：所有端口默认按边缘端口处理（配合 BPDU 保护）
[SW] stp edged-port default
```

> ⚠️ 开了 `stp edged-port default` 后，**交换机互联口必须显式关闭边缘端口**，否则可能造成临时环路：

```latex
[SW-GigabitEthernet0/0/24] stp edged-port disable
```

---

## 3_4 STP 保护机制（生产环境四件套）
### 3_4.1 BPDU 保护（防私接交换机）
```latex
[SW] stp bpdu-protection
```

作用：边缘端口**一旦收到 BPDU 立即 shutdown**，防止用户私接交换机形成环路。

恢复：

```latex
[SW] display stp abnormal-port                       # 查看被关闭端口
[SW] interface g0/0/5
[SW-GigabitEthernet0/0/5] undo shutdown              # 手工恢复
# 或配置自动恢复
[SW] error-down auto-recovery cause bpdu-protection interval 300
```

### 3_4.2 根保护（防根桥被抢占）
```latex
[SW] interface g0/0/24
[SW-GigabitEthernet0/0/24] stp root-protection
```

作用：在指定端口上启用，**一旦收到更优 BPDU，该端口进入 Discarding**，保护根桥地位不被新接入设备篡夺。配置在**根桥的所有指定端口**上。

### 3_4.3 环路保护（防单向链路导致环路）
```latex
[SW] interface g0/0/1
[SW-GigabitEthernet0/0/1] stp loop-protection
```

作用：根端口/Alternate 端口**收不到 BPDU 时**，进入 Discarding 并持续检测，避免光纤单向故障导致"收不到 BPDU 却以为链路正常"而形成环路。

### 3_4.4 TC 保护（防 Topology Change 攻击）
```latex
[SW] stp tc-protection
[SW] stp tc-protection threshold 5        # 单位时间内最多处理 5 次 TC BPDU
```

作用：恶意/故障设备不断发 TC BPDU 会导致**全网 MAC 表被反复清空**（表现为周期性丢包）。TC 保护限制单位时间内的 TC 处理次数。

### 3_4.5 保护机制对照表
| 保护 | 配置位置 | 触发条件 | 动作 |
| --- | --- | --- | --- |
| BPDU 保护 | 全局 | 边缘端口收到 BPDU | 端口 error-down |
| 根保护 | 指定端口 | 收到更优 BPDU | 端口 Discarding（可自恢复） |
| 环路保护 | 根端口/Alternate | 收不到 BPDU | 端口 Discarding |
| TC 保护 | 全局 | TC BPDU 超阈值 | 限流处理 |

---

## 3_5 MSTP 多实例设计
### 3_5.1 为什么需要 MSTP
RSTP 的缺陷：**所有 VLAN 共用一棵树**，被阻塞的链路完全空闲，带宽浪费一半。

MSTP 的解决思路：**把 VLAN 分组映射到不同实例（Instance），每个实例独立计算一棵树**，不同实例阻塞不同链路，实现负载分担。

```latex
实例 1（VLAN 10-20）：树 A，阻塞 SW3-SW4 之间链路
实例 2（VLAN 30-40）：树 B，阻塞 SW1-SW2 之间链路
→ 两条上行链路都被利用起来
```

### 3_5.2 MSTP 域名三要素（必须全同）
MSTP 是一个"域"的概念，只有三要素完全一致的设备才认为在同一域内：

1. **域名**（Region Name）
2. **修订级别**（Revision Level）
3. **VLAN → 实例的映射表**

> 三要素只要有一个不同，两台交换机就被认为在不同域，MSTP 退化为按域间 CIST 计算，负载均衡设计失效。**这是 MSTP 排错的头号原因。**

### 3_5.3 MSTP 配置
```latex
[SW] stp mode mstp
[SW] stp region-configuration
[SW-mst-region] region-name CAMPUS-1
[SW-mst-region] revision-level 1
[SW-mst-region] instance 1 vlan 10 to 20
[SW-mst-region] instance 2 vlan 30 to 40
[SW-mst-region] active region-configuration        # ★ 必须激活，否则不生效！
[SW-mst-region] quit

# 实例优先级（实现不同实例的不同根桥）
[SW] stp instance 1 priority 4096                  # 本交换机是实例 1 的主根
[SW] stp instance 2 priority 8192                  # 实例 2 的备份根
```

> ⚠️ `active region-configuration` **漏配是 MSTP 配置最高频的失误**。配完 `display stp region-configuration` 看到的 Region name 仍是空或默认值。

### 3_5.4 MSTP 验证
```latex
[SW] display stp brief                        # 各实例端口角色与状态
[SW] display stp region-configuration         # 三要素（★ 全网必须一致）
[SW] display stp instance 1                   # 实例 1 的详细信息
[SW] display stp root                         # 根桥信息
[SW] display stp abnormal-port                # 异常端口
```

---

## 3_6 典型落地案例：园区网 MSTP + 负载分担
### 3_6.1 拓扑
```latex
              ┌────────────┐          ┌────────────┐
              │  Core-1    │══════════│  Core-2    │
              │实例1主/实例2备│          │实例2主/实例1备│
              └──────┬─────┘          └─────┬──────┘
                     │  GE0/0/1           GE0/0/1
                     └──────────┬──────────┘
                                │
                          ┌─────┴─────┐
                          │   ACC-1   │
                          └─────┬─────┘
                          终端（VLAN 10-40）
```

### 3_6.2 设计目标
+ 实例 1（VLAN 10–20）主根在 Core-1，阻塞 Core-2 方向；
+ 实例 2（VLAN 30–40）主根在 Core-2，阻塞 Core-1 方向；
+ 两条上行链路都被用起来；任一 Core 故障，另一个实例自动接管的全部流量。

### 3_6.3 完整配置
```latex
# ============ 三台设备相同的域配置 ============
[SW] stp mode mstp
[SW] stp region-configuration
[SW-mst-region] region-name CAMPUS-1
[SW-mst-region] revision-level 1
[SW-mst-region] instance 1 vlan 10 to 20
[SW-mst-region] instance 2 vlan 30 to 40
[SW-mst-region] active region-configuration
[SW-mst-region] quit

# ============ Core-1 ============
[Core-1] stp instance 1 priority 4096
[Core-1] stp instance 2 priority 8192

# ============ Core-2 ============
[Core-2] stp instance 1 priority 8192
[Core-2] stp instance 2 priority 4096

# ============ 保护（三台都配）============
[SW] stp bpdu-protection
[SW] interface gigabitethernet 0/0/24
[SW-GigabitEthernet0/0/24] stp root-protection       # 上行口开根保护

# 用户口：边缘端口
[SW] port-group pg-user
[SW-port-group-pg-user] group-member gigabitethernet 0/0/1 to 0/0/20
[SW-port-group-pg-user] stp edged-port enable

# 上行口：关闭边缘端口（若开了全局 default）
[SW-GigabitEthernet0/0/24] stp edged-port disable
```

### 3_6.4 测试与验收
```latex
# 第1步 域配置一致性（三台设备输出必须完全一致）
display stp region-configuration

# 第2步 检查两台核心各自成为不同实例的根
display stp brief        # Core-1 上实例 1 端口全为 DESI/ROOT；实例 2 有一个阻塞口

# 第3步 模拟故障：断开 Core-1 上行，观察实例 1 切换
#    预期：1–2 秒内实例 1 流量切到 Core-2

# 第4步 拔插 PC 网线，验证即插即用（边缘端口生效，无需等 30 秒）
```

**验收判定表：**

| 验收项 | 命令 | 合格标准 |
| --- | --- | --- |
| 域三要素一致 | `display stp region-configuration`（三台） | 域名/修订级别/映射表完全一致 |
| 实例主根正确 | `display stp instance 1/2` | Core-1 是实例 1 根，Core-2 是实例 2 根 |
| 阻塞口位置正确 | `display stp brief` | 每个实例各有一个阻塞口，且分布在不同链路 |
| 收敛时间 | 断开主链路后 ping | 丢包 ≤2 秒 |
| 边缘端口生效 | PC 开机即 ping | 立刻通，无 30 秒等待 |
| BPDU 保护生效 | 用户口接一台交换机 | 端口 error-down |

---

## 3_7 二层环路的其他防护手段
### 3_7.1 Loop Detection（环路检测，华为增强特性）
不依赖 STP 的轻量环路检测，周期性发送检测报文，发现本端口发出的报文又从其他端口回来即判定环路。

```latex
[SW] loop-detection enable
[SW] interface gigabitethernet 0/0/5
[SW-GigabitEthernet0/0/5] loop-detection enable
[SW-GigabitEthernet0/0/5] loop-detection action shutdown
```

### 3_7.2 风暴控制（广播/组播/未知单播抑制）
```latex
[SW] interface gigabitethernet 0/0/5
[SW-GigabitEthernet0/0/5] broadcast-suppression 5        # 广播抑制到端口带宽 5%
[SW-GigabitEthernet0/0/5] multicast-suppression 10
[SW-GigabitEthernet0/0/5] unicast-suppression 5
[SW-GigabitEthernet0/0/5] storm-control broadcast min-rate 100 max-rate 500    # 部分型号写法（kbps）
[SW-GigabitEthernet0/0/5] storm-control action block                            # 超限时阻断（也可配 shutdown）
```

> 不同平台的命令写法有两种：`broadcast-suppression`（按端口带宽百分比）与 `storm-control`（按速率 kbps + 动作）。**记住"百分比"和"速率"这两个维度就够了**，上设备时用 `?` 确认具体写法。

> 风暴控制是"止损"手段：环路已经发生时，它把广播流量压到可控范围，保住 CPU 和其他端口的业务。

### 3_7.3 端口隔离（同 VLAN 内互访隔离）
```latex
[SW] port-isolate mode l2
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] port-isolate enable group 1
```

适用于宾馆/宿舍场景：同 VLAN 内端口互相不能通信，但都能访问上行口。

---

## 3_8 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 可能原因 | 定位命令 | 处理 |
| --- | --- | --- | --- |
| 全网变慢、CPU 高 | 二层环路 | `display mac-address flapping record`、`display cpu-usage task` | 找漂移端口 shutdown；根治配 BPDU 保护 |
| PC 开机 30 秒才能上网 | 未配边缘端口 | `display stp interface g0/0/1` | `stp edged-port enable` |
| 两条上行只有一条在用（RSTP） | RSTP 单树，正常现象 | `display stp brief` | 改用 MSTP 多实例 |
| MSTP 负载分担不生效 | 域名三要素不一致 / 漏激活 | `display stp region-configuration`（每台对比） | 统一三要素 + `active region-configuration` |
| 用户私接交换机后端口被关 | BPDU 保护生效（正常） | `display stp abnormal-port` | 移除私接设备后 `undo shutdown` |
| 根桥被新设备抢占 | 未配根保护 | `display stp root` | 在根桥指定端口配 `stp root-protection` |
| 周期性丢包 | TC 攻击 | `display stp tc-protection` | `stp tc-protection threshold 5` |
| 阻塞口该转发却 Discarding | 环路保护/根保护触发 | `display stp brief`、`display logbuffer` | 检查是否有单向链路 |

---

## 3_9 场景笔记与验证
### 3_9.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **选举三步图** | 根桥 → 根端口 → 指定端口，每步比较什么（自己画一遍） |
| **MSTP 域三要素卡** | 域名 / 修订级别 / 实例映射，考前一分钟能默出来 |
| **保护四件套对照表** | 配置位置、触发条件、动作（见 3_4.5） |
| **坑本** | 漏 `active region-configuration`；`stp edged-port default` 后互联口没关；全局改了 cost 标准但只有一台 |

### 3_9.2 验证三板斧（本板块版）
```latex
第1步 看状态：display stp brief              端口角色 ROOT/DESI/ALTE，状态 FWD/DIS
第2步 看表项：display stp region-configuration（域一致）、display stp root（根是谁）
第3步 打流量：断开主链路，ping -t 看丢几个包（收敛时间实测）
```

### 3_9.3 强烈建议做一次的破坏性实验
在 eNSP 里**故意造一个环路**（一根线两端插同一交换机），观察：

1. 多少秒后 CPU 打满、ping 全丢；
2. `display mac-address flapping record` 的记录长什么样；
3. 加上 `stp bpdu-protection` + 边缘端口后再造一次，看端口是否被自动 shutdown。

**亲手见过一次环路长什么样，考场上遇到排错题心里就有底。**

---

## 3_10 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | STP 要手工开启 | 华为**默认开启**，模式为 MSTP |
| 2 | 优先级越小越优记反 | 桥 ID、优先级、cost 都是**越小越优**；端口优先级也越小越优 |
| 3 | 2-Way 一定是故障 | 广播网络中 **DROther 之间 2-Way 是正常的**（OSPF 同理） |
| 4 | MSTP 配完就生效 | 必须 `active region-configuration` |
| 5 | 边缘端口配了就安全 | 边缘端口**必须配合 BPDU 保护**，否则收到 BPDU 会退出边缘状态形成环路风险 |
| 6 | 开了 `stp edged-port default` 万事大吉 | 互联口必须 `stp edged-port disable` |
| 7 | 根保护配在所有端口 | 只在**根桥的指定端口**配 |
| 8 | RSTP 支持负载分担 | 只有 **MSTP** 支持（多实例） |

---

# 板块4 · 链路聚合、堆叠与集群
> 定位：把"多条物理链路"变成"一条逻辑链路"，把"多台物理设备"变成"一台逻辑设备"。这是园区网从"能跑"走向"高可靠、无环路、易管理"的关键一跃。
> 技术树：**Eth-Trunk（带宽叠加）→ iStack/CSS（设备虚拟化）→ MAD（防分裂）→ M-LAG（跨设备链路聚合，新一代方案）**。HCIA 掌握前两个，HCIP 要求能做方案设计，HCIE 要能对比三者的适用边界。

## 4_1 链路聚合 Eth-Trunk
### 4_1.1 解决什么问题
| 问题 | Eth-Trunk 的解决 |
| --- | --- |
| 上行带宽不足（1G 不够用） | 多链路捆绑，带宽线性叠加（2×1G = 2G） |
| 单链路故障导致业务中断 | 成员链路互为备份，断一条业务不中断 |
| STP 把冗余链路阻塞了，带宽浪费 | 逻辑上是一条链路，**STP 不会阻塞**，全链路转发 |

### 4_1.2 两种模式
| 模式 | 协商 | 命令 | 特点 | 适用 |
| --- | --- | --- | --- | --- |
| **手工模式**（manual load-balance） | 不协商 | `mode manual load-balance`（默认） | 配置简单，但不检测错连/单通 | 设备不支持 LACP 时 |
| **LACP 静态模式**（推荐） | LACP 协议协商 | `mode lacp-static` | 主动检测链路状态，支持活动/备份链路、抢占 | 生产环境首选 |

> LACP 通过交换 **LACPDU** 协商：双方的系统优先级 + MAC 决定**主动端**，主动端决定哪些链路是"活动链路"（Selected），其余为备份（Unselected）。

### 4_1.3 负载分担方式
```latex
[SW-Eth-Trunk1] load-balance src-dst-mac
```

| 模式 | 哈希因子 | 适用场景 |
| --- | --- | --- |
| `src-mac` | 源 MAC | 单台服务器对多客户端 |
| `dst-mac` | 目的 MAC | 多客户端访问单服务器 |
| `src-dst-mac`（默认） | 源+目的 MAC | 通用二层场景 |
| `src-ip` / `dst-ip` | 源/目的 IP | 三层场景 |
| `src-dst-ip` | 源+目的 IP | **三层/网关场景推荐** |
| `src-dst-ip-l4port` | IP + 四层端口 | 流量最均匀（多会话场景） |

> ⚠️ **负载均衡的真相**：Eth-Trunk 是**基于流（Flow）的哈希分担，不是逐包轮询**。一条大象流（如大文件备份）永远只会走一条成员链路，单流带宽不会超过单链路带宽。所以"2G 聚合口传一个大文件最快只有 1G"是**正常的，不是故障**——这个知识点面试和考试都爱考。

### 4_1.4 LACP 模式配置（推荐）
```latex
[SW] interface eth-trunk 1
[SW-Eth-Trunk1] mode lacp-static
[SW-Eth-Trunk1] trunkport gigabitethernet 0/0/1 to 0/0/2
[SW-Eth-Trunk1] max active-linknumber 2         # 最大活动链路数
[SW-Eth-Trunk1] lacp preempt enable             # 开启抢占（活动链路恢复后抢占回位）
[SW-Eth-Trunk1] lacp preempt delay 10           # 抢占延迟 10 秒（避免震荡）
[SW-Eth-Trunk1] lacp timeout fast               # 快速检测（1s，默认 slow 90s/3s）
[SW-Eth-Trunk1] port link-type trunk
[SW-Eth-Trunk1] port trunk allow-pass vlan 10 20 30
[SW-Eth-Trunk1] load-balance src-dst-ip
[SW-Eth-Trunk1] quit

# 主动端选举（可选，让性能高的设备做主动端）
[SW] lacp priority 100                          # 值越小越优先成为主动端
```

> **活动链路数 vs 备份链路**的典型用法：4 条成员链路配 `max active-linknumber 2`，则 2 条工作、2 条备份，实现"带宽可控 + 冗余"。

### 4_1.5 手工模式配置
```latex
[SW] interface eth-trunk 1
[SW-Eth-Trunk1] trunkport gigabitethernet 0/0/3 to 0/0/5
[SW-Eth-Trunk1] port link-type trunk
[SW-Eth-Trunk1] port trunk allow-pass vlan 10 20 30
[SW-Eth-Trunk1] load-balance src-dst-mac
```

### 4_1.6 验证与输出解读
```latex
[SW] display eth-trunk 1                        # 聚合口总览
[SW] display eth-trunk 1 verbose                # 详细信息
[SW] display lacp statistics eth-trunk 1        # LACP 报文统计
[SW] display trunkmembership eth-trunk 1        # 成员端口列表
[SW] display interface eth-trunk 1              # 聚合口接口信息（带宽、流量）
```

```latex
Eth-Trunk1's state information is:
WorkingMode: STATIC                   ← LACP 静态模式
Least Active-linknumber: 1
Max Active-linknumber: 2              ← 最大活动链路
Operate status: up
--------------------------------------------------------------------------------
ActorPortName          Status   PortType PortPri PortNo PortKey PortState Weight
GigabitEthernet0/0/1   Selected 1GE     32768   2      305     10111100  1
GigabitEthernet0/0/2   Selected 1GE     32768   3      305     10111100  1
GigabitEthernet0/0/3   Unselect 1GE     32768   4      305     10100000  1
```

+ `Selected` = 活动链路，参与转发；`Unselect` = 备份或异常链路；
+ 两端 `PortKey` 必须一致，否则无法聚合；
+ 若某个端口一直 Unselect，检查两端配置是否一致（速率/双工/VLAN/模式）。

### 4_1.7 Eth-Trunk 故障排查
| 现象 | 原因 | 处理 |
| --- | --- | --- |
| 成员口 Unselect | 两端配置不一致（VLAN/速率/双工/模式） | 逐项对齐 |
| 聚合口 down | 成员口全部 down 或手工 shutdown | 查物理链路 |
| 流量只走一条链路 | 哈希因子选择不当（如只有一对 MAC/IP 通信） | 改 `src-dst-ip-l4port` 或增加流量种类 |
| LACP 协商失败 | 一端 lacp-static 一端 manual | 统一模式 |
| 误接其他设备 | 手工模式不检测错连 | 改用 LACP 模式 |

> **Eth-Trunk 配置铁律：先把配置做在 Eth-Trunk 逻辑口上，再把物理口加进去。** 反过来（先在物理口配 VLAN 再加组）会报配置冲突。

---

## 4_2 堆叠 iStack（盒式交换机）
### 4_2.1 堆叠解决什么问题
| 痛点（多交换机独立） | 堆叠后的改善 |
| --- | --- |
| N 台设备 N 份配置、N 个管理 IP | **一台逻辑设备**：一份配置、一个 IP、一个 MAC |
| 设备间链路要靠 STP 阻塞 | 跨设备 Eth-Trunk，**无环路、全链路负载分担** |
| 主备靠 VRRP，切换慢且复杂 | 堆叠内毫秒级切换，无需 VRRP |
| 扩容要重新规划网络 | 新设备加入即自动同步配置 |

### 4_2.2 角色与选举
| 角色 | 数量 | 职责 |
| --- | --- | --- |
| **Master** | 唯一 | 管理整个堆叠系统，同步配置给所有成员 |
| **Standby** | 唯一 | Master 的备份，Master 故障毫秒级接管 |
| **Slave** | 多台 | 业务转发，听 Master 调度 |

**选举规则（依次比较）：**

```latex
第1步 已上电运行的设备 优先于 刚启动的设备
第2步 堆叠优先级高者（默认 100，可配 1–255，越大越优）
第3步 MAC 地址小者
```

### 4_2.3 堆叠规划要点
| 项目 | 建议 |
| --- | --- |
| 成员数量 | 盒式最多 9 台（实际推荐 ≤4，太多增加分裂风险） |
| 拓扑 | **环形**优于链形（环形断一条链路不分裂） |
| 堆叠口接线 | 本端 `stack-port n/1` 必须对接对端 `stack-port m/2`（交叉互联） |
| 版本 | **所有成员系统软件版本必须完全一致** |
| 必配 | **MAD 多主检测**（不配 = 埋雷） |

### 4_2.4 三台环形堆叠配置示例
```latex
   SW0 ══════════ SW1
    ║               ║
    ╚═══════════════╝
        SW2（环形闭合）
每台的 stack-port n/1 接下一台的 stack-port m/2
```

```latex
# ========== SW0（规划为 Master） ==========
[SW0] sysname SW0
[SW0] stack slot 0 priority 200                            # 最高优先级
[SW0] interface stack-port 0/1
[SW0-Stack-Port0/1] port member-group interface gigabitethernet 0/0/27
[SW0-Stack-Port0/1] port member-group interface gigabitethernet 0/0/28
[SW0-Stack-Port0/1] quit

# ========== SW1 ==========
[SW1] stack slot 0 renumber 1                              # 改堆叠 ID（重启生效）
[SW1] stack slot 0 priority 150
[SW1] interface stack-port 1/1
[SW1-Stack-Port1/1] port member-group interface gigabitethernet 0/0/27
[SW1-Stack-Port1/1] port member-group interface gigabitethernet 0/0/28
[SW1-Stack-Port1/1] quit

# ========== SW2 ==========
[SW2] stack slot 0 renumber 2
[SW2] stack slot 0 priority 100
[SW2] interface stack-port 2/1
[SW2-Stack-Port2/1] port member-group interface gigabitethernet 0/0/27
[SW2-Stack-Port2/1] port member-group interface gigabitethernet 0/0/28
[SW2-Stack-Port2/1] quit
```

配置完成后**保存 → 断电 → 按规划接好堆叠线 → 再上电**（先上 Master）。启动后端口编号变为 `GigabitEthernet0/0/1`（槽位号/子卡号/端口号）。

### 4_2.5 堆叠验证
```latex
[SW0] display stack                        # 堆叠拓扑与成员
[SW0] display stack topology               # 环形/链形连接关系
[SW0] display stack peers                  # 邻居信息
[SW0] display device                       # 成员设备状态
[SW0] display stack channel all            # 堆叠链路带宽与状态
```

---

## 4_3 集群 CSS（框式交换机）
### 4_3.1 与 iStack 的区别
| 对比 | iStack | CSS |
| --- | --- | --- |
| 适用设备 | 盒式（S5700/S6700 等） | 框式（S7700/S9700/CE12800 等） |
| 成员数 | 最多 9 台 | 一般 2 台（部分型号支持更多） |
| 本质 | 设备虚拟化 | 设备虚拟化（控制平面合一） |

### 4_3.2 配置要点
```latex
# ================= DeviceA =================
[DeviceA] css enable
[DeviceA] set css mode lpu                     # 业务口集群模式（或用主控板集群口）
[DeviceA] set css id 1
[DeviceA] set css priority 150                 # 值大者优先为主
[DeviceA] interface css-port 1
[DeviceA-css-port1] port interface xgigabitethernet 1/0/1 to 1/0/2 enable
[DeviceA-css-port1] quit
[DeviceA] quit
<DeviceA> save
<DeviceA> reboot                               # 重启后集群生效

# ================= DeviceB =================
[DeviceB] css enable
[DeviceB] set css mode lpu                     # 模式必须与 DeviceA 一致
[DeviceB] set css id 2                         # 成员 ID 唯一（1 已给 DeviceA）
[DeviceB] set css priority 100                 # 优先级低于 DeviceA → 成为备
[DeviceB] interface css-port 1
[DeviceB-css-port1] port interface xgigabitethernet 1/0/1 to 1/0/2 enable
[DeviceB-css-port1] quit
[DeviceB] quit
<DeviceB> save
<DeviceB> reboot
```

> ⚠️ **CSS 与 iStack 的共同铁律**：第1步 两端**模式、版本必须一致**；第2步 成员 ID 唯一；第3步 **保存后断电接线再上电**（先上主）；第4步 集群同样必须配 MAD，否则分裂即双主。

### 4_3.3 集群验证
```latex
[DeviceA] display css status
[DeviceA] display css channel
[DeviceA] display device
```

---

## 4_4 MAD 多主检测（堆叠/集群必配）
### 4_4.1 为什么必须有 MAD
堆叠链路全部中断后，两台成员都会认为自己是 Master，变成**两台配置相同的独立设备**：相同 IP、相同网关、相同 MAC → **ARP 混乱、网络大乱**。MAD 就是检测并抑制这种情况的机制：检测到分裂后，**保留一台（状态正常的），把其余成员的业务端口关闭**。

### 4_4.2 三种 MAD 方式
| 方式 | 原理 | 适用 |
| --- | --- | --- |
| **直连检测（direct）** | 成员间用普通网线直连，互发 MAD 报文 | 两台设备距离近（同机柜） |
| **代理检测（relay）** | 通过一台普通交换机中转 MAD 报文 | 设备分散、直连不便 |
| **LACP MAD** | 借 Eth-Trunk 链路传 MAD 报文 | 已有跨设备 Eth-Trunk 场景 |

### 4_4.3 直连检测配置
```latex
[SW0] interface gigabitethernet 0/0/5
[SW0-GigabitEthernet0/0/5] mad detect mode direct
[SW1] interface gigabitethernet 1/0/5
[SW1-GigabitEthernet1/0/5] mad detect mode direct
```

### 4_4.4 代理检测配置
```latex
# 堆叠系统侧
[SW0] interface eth-trunk 1
[SW0-Eth-Trunk1] mad detect mode relay

# 代理交换机侧（普通交换机即可，开启代理功能）
[Proxy] interface eth-trunk 1
[Proxy-Eth-Trunk1] mad relay
```

### 4_4.5 MAD 故障恢复
```latex
[SW0] display mad verbose                  # 查看 MAD 状态
# 堆叠链路恢复后：
[SW0] mad restore                          # 恢复被 MAD 关闭的业务端口
```

> **现场故事**：某医院核心堆叠，堆叠线被保洁拔掉一根（链形堆叠），两台成员分裂成双主，全院 HIS 系统中断 20 分钟。复盘发现：**没配 MAD**。后来补了直连检测 + 环形堆叠，再拔一根线业务零感知。**MAD 不是可选项，是堆叠的保险丝。**

---

## 4_5 跨设备链路聚合与 M-LAG
### 4_5.1 传统方案的困境
| 方案 | 困境 |
| --- | --- |
| 堆叠 | 控制平面合一，**升级要整机重启**（或依赖平滑升级），软件 Bug 可能同时影响两台；有分裂风险 |
| 独立双机 + VRRP | 上行链路有一半被 STP 阻塞，带宽浪费；切换秒级 |

### 4_5.2 M-LAG（跨设备链路聚合）
**两台独立交换机虚拟成一台**，对外呈现为一个聚合组，下联设备正常做 LACP 聚合即可——**既无 STP 阻塞，又保持控制平面独立**（可逐台升级）。

| 关键概念 | 说明 |
| --- | --- |
| **DFS Group** | 动态交换服务组，两台设备之间同步 MAC/ARP 表项 |
| **Peer-Link** | 两台设备之间的互联链路，承载同步流量与故障时的流量绕行 |
| **M-LAG 接口** | 绑定了 DFS Group 的 Eth-Trunk，下联设备正常聚合 |

### 4_5.3 八维度对比：堆叠 vs M-LAG（论述题素材）
| 维度 | 堆叠/CSS | M-LAG |
| --- | --- | --- |
| **控制平面** | 统一（一台逻辑设备） | 独立（两台独立设备） |
| **管理** | 一份配置，简单 | 两台配置，需保证一致性 |
| **升级** | 需平滑升级机制 | **可逐台升级，风险低** |
| **故障域** | 较大（软件 Bug 可能影响整机） | 较小 |
| **分裂风险** | 有，需 MAD | 无（本来就是两台） |
| **成本/复杂度** | 低 | 中 |
| **成员扩展性** | 盒式最多 9 台 | 一般 2 台 |
| **适用场景** | 中小园区、运维能力一般的团队 | 大型园区/数据中心、要求升级不中断 |

**选型结论（可直接套用于论述题）：**

+ **中小园区、团队规模小、追求运维简单** → 堆叠/CSS（一份配置、一个 IP 管到底）；
+ **大型园区、数据中心、要求升级零中断、故障域最小化** → M-LAG；
+ 若已上控制器（iMaster NCE）或有自动化运维能力，M-LAG 的"两份配置"劣势可通过自动化消除。

### 4_5.4 M-LAG 关键配置骨架（CloudEngine）
```latex
# ============ SW-A ============
[SW-A] dfs-group 1
[SW-A-dfs-group-1] source ip 10.1.1.1
[SW-A-dfs-group-1] quit

[SW-A] interface eth-trunk 0                        # Peer-Link
[SW-A-Eth-Trunk0] trunkport 100ge 1/0/1 to 1/0/2
[SW-A-Eth-Trunk0] mode lacp-static
[SW-A-Eth-Trunk0] peer-link 1
[SW-A-Eth-Trunk0] quit

[SW-A] interface eth-trunk 10                       # 下联聚合口
[SW-A-Eth-Trunk10] mode lacp-static
[SW-A-Eth-Trunk10] dfs-group 1 m-lag 1
[SW-A-Eth-Trunk10] trunkport 10ge 1/0/5
[SW-A-Eth-Trunk10] quit

# ============ SW-B（镜像配置，source ip 不同） ============
# dfs-group 1 / peer-link 1 / m-lag 1 编号保持一致
```

---

## 4_6 典型落地案例：园区核心双机 + 接入堆叠
### 6_6.1 拓扑
```latex
              ┌────────────┐          ┌────────────┐
              │  Core-1    │══════════│  Core-2    │
              │  (CSS)     │ Eth-Trunk│            │
              └──────┬─────┘          └─────┬──────┘
                     │                      │
                     └──────────┬───────────┘
                                │ 跨设备 Eth-Trunk
                          ┌─────┴─────┐
                          │  ACC 堆叠  │（SW0/SW1 环形）
                          └─────┬─────┘
                             终端
```

### 4_6.2 配置要点
```latex
# 跨设备 Eth-Trunk：成员口分布在堆叠的不同成员上
[ACC] interface eth-trunk 1
[ACC-Eth-Trunk1] mode lacp-static
[ACC-Eth-Trunk1] trunkport gigabitethernet 0/0/27     # SW0 上的口
[ACC-Eth-Trunk1] trunkport gigabitethernet 1/0/27     # SW1 上的口
[ACC-Eth-Trunk1] port link-type trunk
[ACC-Eth-Trunk1] port trunk allow-pass vlan 10 20 30
[ACC-Eth-Trunk1] load-balance src-dst-ip
```

### 4_6.3 验收测试
```latex
# 第1步 聚合状态
display eth-trunk 1              # 两个成员口都 Selected

# 第2步 断链测试
#    拔掉一条成员线 → ping 不丢包或丢 1 个包

# 第3步 断设备测试
#    关闭 SW1 → SW0 接管，ping 丢包 ≤1 秒

# 第4步 MAD 验证（模拟堆叠分裂）
#    拔掉全部堆叠线 → MAD 生效，一台保留、另一台业务口被关
#    恢复堆叠线 → mad restore
```

---

## 4_7 方案选型对比（论述题素材）
> **本节导读**：这一节是论述题的弹药库。记住一个原则——**没有最优方案，只有最匹配约束的方案**，答题时要先说需求再说选型。

| 需求 | 推荐方案 | 理由 |
| --- | --- | --- |
| 接入层多台交换机统一管理 | iStack 堆叠 | 一份配置、跨设备 Eth-Trunk 无环路 |
| 核心层要求极致可靠、可逐台升级 | M-LAG（或 CSS + 平滑升级） | 控制平面独立，故障域小 |
| 上行带宽不够、又要冗余 | Eth-Trunk（LACP） | 带宽叠加 + 链路备份，STP 不阻塞 |
| 预算有限、运维人力少 | 堆叠 | 管理简单，成本低 |
| 数据中心、服务器双上行 | M-LAG | 服务器侧标准 LACP，无需厂商私有驱动 |

---

## 4_8 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 原因 | 定位/处理 |
| --- | --- | --- |
| 成员口一直 Unselect | 两端模式/VLAN/速率不一致 | `display eth-trunk 1 verbose` 逐项对齐 |
| LACP 协商不起来 | 一端 manual 一端 lacp-static | 统一为 `mode lacp-static` |
| 聚合口只有一条链路跑流量 | 哈希因子不合适或流量单一 | 改 `src-dst-ip-l4port`；用多流测试 |
| 堆叠成员没起来 | 版本不一致 / 堆叠口接错 | `display stack`；统一版本、检查交叉接线 |
| 堆叠后端口编号变了 | 正常现象（槽位号变化） | 重新核对配置中的接口编号 |
| 堆叠分裂网络大乱 | **未配 MAD** | 配 MAD；恢复后 `mad restore` |
| MAD 误关闭业务口 | 堆叠链路闪断 | 修复堆叠链路后 `mad restore` |
| M-LAG 两端表项不一致 | Peer-Link 故障或 DFS 未建 | `display dfs-group 1` |

---

## 4_9 场景笔记与验证
### 4_9.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **聚合模式对照卡** | 手工 vs LACP：协商、检测、是否支持活动/备份 |
| **堆叠上线 SOP** | 规划 ID/优先级 → 配堆叠口 → 保存 → 断电 → 接线 → 上电 → 验证 → 配 MAD |
| **M-LAG 三件套** | dfs-group + peer-link + m-lag 接口绑定（编号两端一致） |
| **坑本** | 先配物理口再加组会冲突；堆叠版本必须一致；MAD 不配等于埋雷 |

### 4_9.2 验证三板斧（本板块版）
```latex
第1步 看状态：display eth-trunk 1 / display stack / display css status
第2步 看表项：display trunkmembership eth-trunk 1（成员对不对）
第3步 打流量：断一条成员线 ping -t（应不丢或丢 1 包）；断一台成员设备（应秒级恢复）
```

### 4_9.3 值得记录的两个数据
+ **Eth-Trunk 断链是否丢包**：LACP fast 模式通常不丢或丢 1 包；slow 模式可能丢几秒；
+ **堆叠主备切换时间**：实测通常是毫秒到秒级，写进你的实验记录，论述题里引用自己的实测数据会显得非常专业。

---

## 4_10 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | 2G 聚合口单流能跑 2G | **不能**，单流走一条成员链路，这是基于流哈希 |
| 2 | Eth-Trunk 会被 STP 阻塞 | 逻辑上一条链路，STP 不阻塞成员链路 |
| 3 | 配置顺序无所谓 | **先配逻辑口，再加物理口**，否则冲突报错 |
| 4 | 堆叠成员版本可不同 | 必须**完全一致** |
| 5 | 堆叠优先级越大越优 | 是的（默认 100，与 STP 相反，注意区分） |
| 6 | 堆叠不需要 MAD | **必须配**，否则分裂即双主 |
| 7 | M-LAG 是堆叠的升级版 | 是另一种思路：控制平面独立，可逐台升级 |
| 8 | 环形堆叠可随意断一根线 | 环形断一根不分裂；链形断一根即分裂 |

---

# 板块5 · 三层交换、VLAN 间路由与 DHCP 服务
> 定位：把二层网络"打通"成可通信的网络。HCIA 要求会配 VLANIF 与 DHCP；HCIP 要求理解三层转发流程、能做网关冗余设计（与 VRRP 配合）；HCIE 要求能在园区虚拟化（VXLAN）场景中重新审视网关位置（集中式 vs 分布式）。
> 核心问题：**不同 VLAN 的主机怎么通信？网关该放哪里？地址怎么自动下发？**

## 5_1 三层交换原理
### 5_1.1 为什么二层交换机做不到
二层交换机只能在同一广播域内转发。不同 VLAN = 不同广播域 = 不同网段，跨网段通信必须依靠**三层设备（路由器或三层交换机）**做路由。

### 5_1.2 三种实现 VLAN 间路由的方式
| 方式 | 原理 | 优点 | 缺点 | 现状 |
| --- | --- | --- | --- | --- |
| **VLANIF（三层交换）** ★推荐 | 三层交换机上为每个 VLAN 创建虚拟三层接口 | 性能高（硬件转发）、配置简单、可扩展 | 需要三层交换机 | **园区网主流** |
| **单臂路由** | 路由器一个物理口划子接口（dot1q 终结） | 节省路由器端口 | 带宽瓶颈、单点 | 小型/临时组网 |
| **三层物理口互联** | 每个 VLAN 占一个路由器物理口 | 简单直观 | 极耗端口 | 基本淘汰 |

### 5_1.3 三层交换转发流程（"一次路由，多次交换"）
```latex
第1步 PC1(192.168.10.1) 判断目的 IP 192.168.20.1 与自己不同网段
   → 发 ARP 请求网关 192.168.10.254 的 MAC
第2步 交换机用 Vlanif10 的 MAC 回应（网关代理 ARP）
第3步 PC1 发出帧：目的 MAC = 网关MAC，VLAN 10，目的 IP = 192.168.20.1
第4步 交换机查三层转发表 → 目的网段 192.168.20.0/24 是直连 VLAN 20
第5步 无 PC2 的 ARP 项 → 交换机在 VLAN 20 内发 ARP 请求 PC2
第6步 收到应答后，交换机【重写二层帧头】：
   源 MAC = Vlanif20 的 MAC，目的 MAC = PC2 的 MAC，VLAN 10 → VLAN 20
第7步 从 VLAN 20 的端口转发出去
第8步 同时生成硬件三层转发表项，后续同流的报文【不再上 CPU】，直接硬件转发
```

> 关键点：三层交换**不是"路由一次就结束了"**，而是首个报文上 CPU 建表，后续报文由 ASIC 硬件按表转发，这就是它能达到线速的原因。

### 5_1.4 三层交换机 vs 路由器
| 维度 | 三层交换机 | 路由器 |
| --- | --- | --- |
| 转发方式 | 硬件 ASIC 转发为主 | CPU/NP 转发 |
| 接口类型 | 以太网为主 | 以太网/串口/POS/E1 等丰富 |
| 路由协议 | 支持（OSPF/BGP/IS-IS） | 支持（更完整） |
| 高级特性 | 相对有限 | NAT/IPSec/QoS/隧道更全面 |
| 典型位置 | **园区网汇聚/核心（内网网关）** | **出口/广域网边界** |

---

## 5_2 VLANIF 配置实战
### 5_2.1 拓扑与规划
```latex
   PC1                                              PC2
 192.168.10.1/24                              192.168.20.1/24
 网关 .10.254                                  网关 .20.254
 VLAN 10                                       VLAN 20
   │ access                                       │ access
   │ E1/0/20                                      │ E1/0/21
┌──┴──────────────────────────────────────────────┴──┐
│                 SW1（三层交换机，核心）               │
│   ┌──────────────────┐   ┌──────────────────┐      │
│   │    Vlanif 10     │   │    Vlanif 20     │      │
│   │ 192.168.10.254/24│   │ 192.168.20.254/24│      │
│   └────────┬─────────┘   └─────────┬────────┘      │
│            └───────────┬───────────┘               │
│              ┌─────────┴─────────┐                 │
│              │  三层转发引擎（ASIC）│  ← 直连路由自动生成│
│              └───────────────────┘                 │
│                        │ E1/0/24                   │
└────────────────────────┼───────────────────────────┘
                         │ Trunk（allow-pass 10 20）
                    ┌────┴────┐
                    │  SW2    │ 二层接入交换机
                    └────┬────┘
                         │ E1/0/5 access vlan 10
                    ┌────┴────┐
                    │  PC3    │ 192.168.10.2/24
                    └─────────┘
```

| 项目 | 规划 |
| --- | --- |
| VLAN 10 | 办公，192.168.10.0/24，网关 192.168.10.254（Vlanif10） |
| VLAN 20 | 监控，192.168.20.0/24，网关 192.168.20.254（Vlanif20） |
| SW1 | 三层交换机（核心），承担网关 |
| SW2 | 二层接入交换机，上联 Trunk |
| 互联 | SW1-E1/0/24 ↔ SW2-E1/0/24，Trunk 放行 VLAN 10/20 |

### 5_2.2 完整配置
**SW1（三层交换机）：**

```latex
<Huawei> system-view
[Huawei] sysname SW1
[SW1] vlan batch 10 20

# 接入端口
[SW1] interface ethernet 1/0/20
[SW1-Ethernet1/0/20] port link-type access
[SW1-Ethernet1/0/20] port default vlan 10
[SW1-Ethernet1/0/20] stp edged-port enable
[SW1-Ethernet1/0/20] quit

[SW1] interface ethernet 1/0/21
[SW1-Ethernet1/0/21] port link-type access
[SW1-Ethernet1/0/21] port default vlan 20
[SW1-Ethernet1/0/21] stp edged-port enable
[SW1-Ethernet1/0/21] quit

# 上联/下联 Trunk
[SW1] interface ethernet 1/0/24
[SW1-Ethernet1/0/24] port link-type trunk
[SW1-Ethernet1/0/24] port trunk allow-pass vlan 10 20
[SW1-Ethernet1/0/24] undo port trunk allow-pass vlan 1
[SW1-Ethernet1/0/24] quit

# ★ 关键：VLANIF 三层网关接口
[SW1] interface Vlanif 10
[SW1-Vlanif10] ip address 192.168.10.254 24
[SW1-Vlanif10] description Office-Gateway
[SW1-Vlanif10] quit

[SW1] interface Vlanif 20
[SW1-Vlanif20] ip address 192.168.20.254 24
[SW1-Vlanif20] description CCTV-Gateway
[SW1-Vlanif20] quit
```

**SW2（二层交换机）：**

```latex
[Huawei] sysname SW2
[SW2] vlan batch 10 20
[SW2] interface ethernet 1/0/5
[SW2-Ethernet1/0/5] port link-type access
[SW2-Ethernet1/0/5] port default vlan 10
[SW2-Ethernet1/0/5] stp edged-port enable
[SW2-Ethernet1/0/5] quit

[SW2] interface ethernet 1/0/24
[SW2-Ethernet1/0/24] port link-type trunk
[SW2-Ethernet1/0/24] port trunk allow-pass vlan 10 20
[SW2-Ethernet1/0/24] undo port trunk allow-pass vlan 1
[SW2-Ethernet1/0/24] quit
```

### 5_2.3 验证
```latex
[SW1] display ip interface brief                  # Vlanif10/20 是否 UP
[SW1] display ip routing-table                    # 应看到两条直连路由（Direct）
[SW1] display vlan                                # VLAN 与端口
[SW1] display arp                                 # PC 上线后能看到 ARP 表项
```

```latex
# 终端侧
PC1> ping 192.168.10.254         # 通：网关可达
PC1> ping 192.168.20.254         # 通：跨网段到对端网关
PC1> ping 192.168.20.1           # 通：VLAN 间通信成功 ★
PC1> tracert 192.168.20.1        # 应只有一跳（192.168.10.254 → 192.168.20.1）
```

> 🚨 **VLANIF 无法 UP 的常见原因**：该 VLAN 在交换机上**没有任何 UP 的物理端口**（Access 或 Trunk 放行）。VLANIF 是"逻辑接口"，需要 VLAN 内有活跃端口才会 UP。

---

## 5_3 单臂路由（路由器子接口）
### 5_3.1 场景
没有三层交换机时的临时方案：路由器一个物理口划多个子接口，每个子接口终结一个 VLAN。

### 5_3.2 配置
```latex
# ============ 路由器 ============
[Router] interface gigabitethernet 0/0/1.10
[Router-GigabitEthernet0/0/1.10] dot1q termination vid 10
[Router-GigabitEthernet0/0/1.10] ip address 192.168.10.254 24
[Router-GigabitEthernet0/0/1.10] arp broadcast enable      # ★ 最容易漏！
[Router-GigabitEthernet0/0/1.10] quit

[Router] interface gigabitethernet 0/0/1.20
[Router-GigabitEthernet0/0/1.20] dot1q termination vid 20
[Router-GigabitEthernet0/0/1.20] ip address 192.168.20.254 24
[Router-GigabitEthernet0/0/1.20] arp broadcast enable
[Router-GigabitEthernet0/0/1.20] quit

# ============ 交换机 ============
[SW] interface gigabitethernet 0/0/24
[SW-GigabitEthernet0/0/24] port link-type trunk
[SW-GigabitEthernet0/0/24] port trunk allow-pass vlan 10 20
```

> ⚠️ 终结子接口（dot1q termination）默认**不发 ARP 广播**，不配 `arp broadcast enable` 会导致 PC ping 不通网关——这是 HCIA 实验的经典失分点。

### 5_3.3 三层交换机上的等价形式
三层交换机用 VLANIF 天然等价，不需要子接口，也不需要 `arp broadcast enable`。

---

## 5_4 DHCP 服务
### 5_4.1 DHCP 工作流程（四步）
```latex
第1步 Discover  客户端广播："谁能给我个地址？"
第2步 Offer     服务器回应："给你 192.168.10.10，网关是 .254"
第3步 Request   客户端广播确认："我要这个地址"
第4步 Ack       服务器确认："成交，租期 1 天"
```

### 5_4.2 交换机作为 DHCP Server（全局地址池）
```latex
[SW] dhcp enable

[SW] ip pool VLAN10
[SW-ip-pool-VLAN10] gateway-list 192.168.10.254
[SW-ip-pool-VLAN10] network 192.168.10.0 mask 255.255.255.0
[SW-ip-pool-VLAN10] dns-list 8.8.8.8 114.114.114.114
[SW-ip-pool-VLAN10] excluded-ip-address 192.168.10.200 192.168.10.253
[SW-ip-pool-VLAN10] lease day 1                     # 租期 1 天（默认）
[SW-ip-pool-VLAN10] quit

[SW] interface Vlanif 10
[SW-Vlanif10] dhcp select global                    # 接口下启用全局池模式
```

**接口池（更简单，网关即接口 IP）：**

```latex
[SW] interface Vlanif 20
[SW-Vlanif20] dhcp select interface
[SW-Vlanif20] dhcp server dns-list 8.8.8.8
[SW-Vlanif20] dhcp server excluded-ip-address 192.168.20.240 192.168.20.253
```

> 接口池适合小型网络（网关地址自动作为网关）；**生产推荐全局池**，便于统一管理与排除地址段。

### 5_4.3 DHCP Relay（中继）
当 DHCP 服务器在另一网段（如服务器区）时，网关接口做中继：

```latex
[SW] dhcp enable
[SW] interface Vlanif 30
[SW-Vlanif30] dhcp select relay
[SW-Vlanif30] dhcp relay server-ip 192.168.99.100
```

> 中继原理：网关把客户端广播的 Discover 单播转发给服务器，并把服务器的回应带回客户端网段。**服务器上必须有回程路由**（否则 Offer 回不来）。

### 5_4.4 DHCP 验证命令
```latex
[SW] display ip pool                                  # 地址池总览
[SW] display ip pool interface Vlanif10 used          # 已分配地址
[SW] display ip pool name VLAN10                      # 指定池详情
[SW] display dhcp server statistics
[SW] display dhcp relay all                           # 中继状态
```

**终端侧验证：**

```latex
PC> ipconfig /release
PC> ipconfig /renew
PC> ipconfig            # 看是否拿到 IP、掩码、网关、DNS
```

---

## 5_5 DHCP Snooping（防私接 DHCP 服务器）
### 5_5.1 威胁场景
员工自带小路由器接入网口，路由器默认开 DHCP → 其他同事拿到**假网关**（如 192.168.1.1）→ 上不了网，甚至流量被中间人劫持。

### 5_5.2 工作机制与配置
```latex
第1步 交换机在 VLAN 内开启 Snooping，端口分为 Trusted / Untrusted
第2步 Untrusted 端口【丢弃】服务器方向的报文（Offer/Ack）
第3步 Trusted 端口正常转发服务器报文
第4步 交换机监听完整的 DHCP 交互，生成【绑定表】：IP + MAC + VLAN + 端口 + 租期
```

```latex
[SW] dhcp enable
[SW] dhcp snooping enable ipv4

[SW] vlan 10
[SW-vlan10] dhcp snooping enable
[SW-vlan10] dhcp snooping trusted interface gigabitethernet 0/0/1    # 上行口=信任
[SW-vlan10] quit

[SW] interface gigabitethernet 0/0/2
[SW-GigabitEthernet0/0/2] dhcp snooping enable
[SW-GigabitEthernet0/0/2] dhcp snooping check dhcp-chaddr enable     # 防 CHADDR 伪造
[SW-GigabitEthernet0/0/2] dhcp snooping check dhcp-giaddr enable     # 防 GIADDR 欺骗
[SW-GigabitEthernet0/0/2] dhcp snooping user-bind max-number 20
[SW-GigabitEthernet0/0/2] dhcp snooping rate-limit 10                # 防饿死攻击
```

### 5_5.3 静态绑定表与 IPSG 联动
```latex
[SW] user-bind static ip-address 192.168.10.100 mac-address 0001-0002-0003 interface gigabitethernet 0/0/5 vlan 10
[SW] display dhcp snooping user-bind all

# IPSG 联动（在用户口开启源 IP+MAC 检查）
[SW] interface gigabitethernet 0/0/5
[SW-GigabitEthernet0/0/5] ip source check user-bind enable
```

> 绑定表的价值：不仅防私接 DHCP，还是 **IPSG 和 DAI 的数据源**——有了它，私改 IP 和 ARP 欺骗都能防（详见板块12）。

---

## 5_6 网关冗余设计（与 VRRP 配合）
### 5_6.1 三种网关部署模式
| 模式 | 网关位置 | 特点 |
| --- | --- | --- |
| **核心集中网关** | 核心交换机 VLANIF | 管理简单，主流；核心需冗余（堆叠或 VRRP） |
| **汇聚分布网关** | 汇聚层 VLANIF | 转发路径短，配置分散 |
| **VRRP 双机网关** | 两台核心各配 VRRP | 真冗余，配合 MSTP 做负载分担 |

### 5_6.2 典型：核心双机 + VRRP
```latex
# Core-1（VLAN 10 的 Master）
[Core-1] interface Vlanif 10
[Core-1-Vlanif10] ip address 192.168.10.252 24
[Core-1-Vlanif10] vrrp vrid 10 virtual-ip 192.168.10.254
[Core-1-Vlanif10] vrrp vrid 10 priority 120

# Core-2（Backup）
[Core-2] interface Vlanif 10
[Core-2-Vlanif10] ip address 192.168.10.253 24
[Core-2-Vlanif10] vrrp vrid 10 virtual-ip 192.168.10.254
[Core-2-Vlanif10] vrrp vrid 10 priority 100
```

终端网关填 **192.168.10.254**（虚拟 IP）。详细原理、track 与 BFD 联动见**板块13**。

---

## 5_7 综合案例：中小企业园区网（VLANIF + DHCP + Snooping）
### 5_7.1 需求与规划
| 项目 | 规划 |
| --- | --- |
| VLAN 10 办公 | 192.168.10.0/24，网关 .254，DHCP 自动分配 |
| VLAN 20 监控 | 192.168.20.0/24，网关 .254，DHCP（排除 .200–.253 给固定摄像头） |
| VLAN 99 管理 | 192.168.99.0/24 |
| 网关位置 | Core 三层交换机；监控不能访问办公（ACL，见板块11） |
| 安全 | 全网开 DHCP Snooping，上行口信任 |

### 5_7.2 Core 配置要点
```latex
[Core] dhcp enable
[Core] ip pool POOL-10
[Core-ip-pool-POOL-10] gateway-list 192.168.10.254
[Core-ip-pool-POOL-10] network 192.168.10.0 mask 24
[Core-ip-pool-POOL-10] dns-list 8.8.8.8
[Core-ip-pool-POOL-10] excluded-ip-address 192.168.10.201 192.168.10.253
[Core-ip-pool-POOL-10] quit

[Core] vlan batch 10 20 99
[Core] interface Vlanif 10
[Core-Vlanif10] ip address 192.168.10.254 24
[Core-Vlanif10] dhcp select global
[Core-Vlanif10] quit

[Core] interface Vlanif 20
[Core-Vlanif20] ip address 192.168.20.254 24
[Core-Vlanif20] dhcp select global
[Core-Vlanif20] quit

# 下联 Trunk
[Core] interface gigabitethernet 0/0/1
[Core-GigabitEthernet0/0/1] port link-type trunk
[Core-GigabitEthernet0/0/1] port trunk allow-pass vlan 10 20 99
[Core-GigabitEthernet0/0/1] undo port trunk allow-pass vlan 1
```

### 5_7.3 接入交换机配置
```latex
[ACC] vlan batch 10 20 99
[ACC] port-group pg-office
[ACC-port-group-pg-office] group-member gigabitethernet 0/0/1 to 0/0/10
[ACC-port-group-pg-office] port link-type access
[ACC-port-group-pg-office] port default vlan 10
[ACC-port-group-pg-office] stp edged-port enable

[ACC] interface gigabitethernet 0/0/24
[ACC-GigabitEthernet0/0/24] port link-type trunk
[ACC-GigabitEthernet0/0/24] port trunk allow-pass vlan 10 20 99

# ===== DHCP Snooping =====
[ACC] dhcp snooping enable ipv4
[ACC] vlan 10
[ACC-vlan10] dhcp snooping enable
[ACC-vlan10] dhcp snooping trusted interface gigabitethernet 0/0/24    # 上行信任
[ACC-vlan10] quit
```

### 5_7.4 验收测试
```latex
# 第1步 地址获取：PC 设为 DHCP 自动获取 → ipconfig 看到 192.168.10.x
# 第2步 地址池状态
[Core] display ip pool name POOL-10 used
# 第3步 绑定表
[ACC] display dhcp snooping user-bind all
# 第4步 安全验证：模拟私接 DHCP 服务器（在用户口接一台开 DHCP 的小路由器）
#    预期：假服务器不生效，交换机日志有告警
# 第5步 跨 VLAN 通信：办公 PC 能 ping 通监控网关（除非配了 ACL 禁止）
```

---

## 5_8 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 原因 | 定位/处理 |
| --- | --- | --- |
| **VLANIF 起不来** | 该 VLAN 内无 UP 端口 | `display vlan 10` 查端口；接入设备上线或 Trunk 放行 |
| 同 VLAN 通跨 VLAN 不通 | 网关没配 / 网关 IP 错 / 终端网关填错 | `display ip interface brief`；终端 `ipconfig` |
| PC 拿到 169.254.x.x | DHCP 请求没到服务器 | 检查 `dhcp enable`、接口 `dhcp select`、VLAN 放行 |
| DHCP 中继不生效 | 服务器无回程路由 | 在服务器侧查路由；`display dhcp relay` |
| 拿到假网关 | **私接 DHCP 服务器** | 开 Snooping，上行口设为 trusted |
| 单臂路由 ping 不通网关 | 子接口漏 `arp broadcast enable` | 补配 |
| 部分终端拿不到地址 | 地址池耗尽 / 排除段过多 | `display ip pool name X`（看 Used/Idle） |
| 终端改静态 IP 后能上网（不该允许） | 未开 IPSG | 配 `ip source check user-bind enable` |

---

## 5_9 场景笔记与验证
### 5_9.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **三层转发八步图** | 自己画一遍 PC1 → PC2 的 MAC/IP 变化（哪层变、哪层不变） |
| **DHCP 配置模板** | 全局池 + 排除段 + DNS + 租期，存成模板 |
| **Snooping 部署 SOP** | 全局开 → VLAN 开 → 上行信任 → 用户口开检查 → 配 IPSG |
| **坑本** | VLANIF 无 UP 端口不 UP；单臂路由漏 arp broadcast enable；中继忘了回程路由 |

### 5_9.2 验证三板斧（本板块版）
```latex
第1步 看状态：display ip interface brief（VLANIF up/up 才算数）
第2步 看表项：display ip routing-table（两条直连路由）、display arp（学到 PC MAC 没）
第3步 打流量：ping 网关 → ping 其他 VLAN 网关 → ping 其他 VLAN 的 PC（三步递进）
```

**DHCP 专项验证：**

```latex
display ip pool name POOL-10 used        # 已分配列表（看 MAC 与租期）
display dhcp snooping user-bind all      # 绑定表（IPSG/DAI 的数据源）
```

### 5_9.3 一个能记很久的小实验
在 eNSP 里用一台路由器模拟"私接的 DHCP 服务器"，不开 Snooping 时观察 PC 拿到假地址；开 Snooping 后再看——**这一次的对比，会让你永远记住为什么要配 Snooping。**

---

## 5_10 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | 有 VLANIF 就能通 | 需要该 VLAN 内有 **UP 的物理端口** |
| 2 | 跨 VLAN 通信改 VLAN Tag 就行 | 三层转发 **IP 头不变**，只重写二层帧头 |
| 3 | 单臂路由只需配子接口 | 必须 `arp broadcast enable` |
| 4 | DHCP 只需 `dhcp enable` | 接口还要 `dhcp select global/interface/relay` |
| 5 | 中继只要本机配就行 | **服务器必须有回程路由** |
| 6 | Snooping 开了就完事 | 必须指定 **trusted 上行口**，否则全网拿不到地址 |
| 7 | Snooping 只能防私接 DHCP | 它生成绑定表，是 **IPSG/DAI** 的基础 |
| 8 | 网关填核心的真实 IP | 有 VRRP 时应填**虚拟 IP** |

---

# 板块6 · IP 路由基础、静态路由与连通性检测
> 定位：路由是数通的灵魂，静态路由是理解路由表的起点。HCIA 要会配、会看路由表；HCIP 要懂递归查找、负载分担、浮动路由与 BFD 联动；HCIE 要能在大型网络里判断"该用静态还是动态""为什么这条路没走通"。
> 核心问题：**一个目的 IP 来了，设备凭什么决定从哪个口发出去？**

## 6_1 路由表结构与查表原则
### 6_1.1 路由表字段解读
```latex
[Router] display ip routing-table

Route Flags: R - relay, D - download to fib
------------------------------------------------------------------------------
Routing Tables: Public
         Destinations : 8        Routes : 8

Destination/Mask    Proto   Pre  Cost      Flags NextHop         Interface
    0.0.0.0/0       Static  60   0          RD   192.168.12.1    Ethernet2/0
  192.168.3.0/24    Direct  0    0           D   192.168.3.1     Ethernet1/0
  192.168.3.1/32    Direct  0    0           D   127.0.0.1       Ethernet1/0
  192.168.5.0/24    Direct  0    0           D   192.168.5.1     Ethernet2/0
  192.168.10.0/24   OSPF    10   2           D   192.168.5.2     Ethernet2/0
  192.168.20.0/24   RIP     100  1           D   192.168.5.3     Ethernet2/0
```

| 字段 | 含义 |
| --- | --- |
| Destination/Mask | 目的网段与掩码 |
| **Proto** | 路由来源（Direct/Static/RIP/OSPF/IS-IS/BGP） |
| **Pre（Preference）** | 路由协议优先级，越小越优 |
| Cost | 路由开销（度量值） |
| Flags | R = 迭代路由，D = 已下发 FIB（可转发） |
| NextHop | 下一跳 IP |
| Interface | 出接口 |

### 6_1.2 最长匹配原则（最重要的一条）
> **路由器按"掩码最长"的路由转发，而不是按优先级、也不是按配置顺序。**

举例：目的 IP = 192.168.1.5，路由表中有：

```latex
192.168.1.0/24   → 下一跳 A
192.168.1.0/25   → 下一跳 B
0.0.0.0/0        → 下一跳 C
```

结果：匹配 `/25`（掩码最长，范围最精确） → 走下一跳 B。

### 6_1.3 路由优选三步走
```latex
Step 1：最长匹配（先按掩码长度筛，长的优先）
Step 2：同掩码下，比 优先级 Pre（越小越优）
Step 3：Pre 相同，比 Cost（越小越优）
        Cost 也相同 → 形成等价路由（负载分担）
```

### 6_1.4 常见协议默认优先级（背下来）
| 路由来源 | 华为默认 Pre |
| --- | --- |
| 直连（Direct） | **0** |
| OSPF 内部 | **10** |
| IS-IS | **15** |
| 静态（Static） | **60** |
| RIP | **100** |
| OSPF ASE（外部引入） | **150** |
| OSPF NSSA | 150 |
| IBGP | **255** |
| EBGP | **255** |

> 记忆锚点：直连 0 → OSPF 10 → IS-IS 15 → 静态 60 → RIP 100 → 外部 150 → BGP 255。**优先级越小越可信。**
> ⚠️ 注意：OSPF 内部路由第10步优于静态路由（60），这意味着**配了静态备份路由时，OSPF 学来的路由会"抢在前面"**——浮动静态路由必须把 preference 调到大于 60 才生效（见 6_2.3）。

### 6_1.5 路由迭代（递归查找）
当下一跳不是直连地址时，路由器需要**再查一次路由表**找到去往该下一跳的路径，这个过程叫迭代。

```latex
ip route-static 10.10.10.0 24 172.16.1.1
而 172.16.1.1 又需要通过直连路由到达 → 迭代
```

迭代失败则路由不生效（`display ip routing-table` 中看不到，或 Flags 无 D）。排查用：

```latex
[Router] display ip routing-table 10.10.10.0 verbose
```

---

## 6_2 静态路由配置
### 6_2.1 三种写法
```latex
# 第1步 指定下一跳（最常用，以太网环境推荐）
[Router] ip route-static 192.168.3.0 255.255.255.0 192.168.12.1

# 第2步 指定出接口（点到点链路，如串口/PPP）
[Router] ip route-static 192.168.3.0 24 Serial 1/0/0

# 第3步 出接口 + 下一跳（最严谨，避免 ARP 解析问题）
[Router] ip route-static 192.168.3.0 24 GigabitEthernet 0/0/1 192.168.12.1
```

> ⚠️ **以太网环境只写出接口的风险**：路由器会认为目标网段是"直连"，对每个目的 IP 直接发 ARP 请求，若对端未开启代理 ARP，则**不通**。所以**广播型链路（以太网）必须写下一跳**，点到点链路可只写出接口。

### 6_2.2 默认路由
```latex
[Router] ip route-static 0.0.0.0 0.0.0.0 192.168.12.1
```

用途：出口路由器 / 接入交换机（管理流量）/"不知道去哪就走这里"。

> 层级越低（接入层），越适合用默认路由；只有在**出口唯一（单宿主）**时才用默认路由，多出口要做策略路由或动态路由。

### 6_2.3 浮动静态路由（主备切换）
```latex
# 主链路（下一跳 12.1，默认 preference 60）
[Router] ip route-static 192.168.3.0 255.255.255.0 192.168.12.1

# 备份链路（下一跳 12.2，preference 100 → 优先级更低，主路由存在时被"隐藏"）
[Router] ip route-static 192.168.3.0 255.255.255.0 192.168.12.2 preference 100
```

**工作机制**：两条路由掩码相同，比较 Pre → 60 的优先生效写入路由表；当主链路 down（出接口失效）时，60 的路由消失，100 的路由"浮上来"。

> 🚨 **浮动静态路由的经典陷阱**：如果主链路是**以太网且下一跳可达性不随链路 down 而消失**（例如经过一台交换机再连对端，本端接口仍 UP），静态路由不会消失，备份永远不生效！  
**解决方案**：第1步 配 BFD/NQA 联动检测；第2步 用出接口形式；第3步 改用动态路由。

### 6_2.4 等价路由（负载分担）
```latex
[Router] ip route-static 192.168.3.0 24 192.168.12.1
[Router] ip route-static 192.168.3.0 24 192.168.12.2
# 两条 Pre 与 Cost 都相同 → 等价路由，流量分担
```

验证：

```latex
[Router] display ip routing-table 192.168.3.0
# 应看到两条 NextHop
```

等价路由默认按**逐流**分担（源目的 IP 哈希），可切换为逐包（不推荐，会导致乱序）：

```latex
[Router] ip load-balance packet        # 逐包（慎用！会造成 TCP 乱序重传）
```

### 6_2.5 黑洞路由（防环 & 汇总防环）
```latex
[Router] ip route-static 10.0.0.0 8 NULL 0
```

用途：

1. **路由汇总后的防环**（做汇总的路由器必须有一条指向 NULL0 的汇总路由，否则可能环路）；
2. **过滤特定流量**（把恶意网段指向黑洞）；
3. **BGP 发布汇总路由时的锚点**。

### 6_2.6 接口 IP 配置（静态路由的前提）
```latex
[Router] interface ethernet 1/0
[Router-Ethernet1/0] ip address 192.168.3.100 255.255.255.0
[Router-Ethernet1/0] undo shutdown

# 交换机上需要先把二层口变三层口
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] undo portswitch
[SW-GigabitEthernet0/0/1] ip address 10.0.0.1 30
```

---

## 6_3 静态路由与 BFD / NQA 联动
### 6_3.1 为什么需要联动
静态路由**没有邻居检测机制**，链路中间断了（如经过光纤收发器、交换机）而本端接口仍 UP 时，静态路由不会消失，流量被黑洞吞掉。BFD/NQA 提供**毫秒级/秒级的主动探测**。

> **现场故事**：某企业主备专线，主链路中间一段运营商光缆被挖断，但两端路由器接口都还 UP，静态路由纹丝不动，业务断了 4 小时没人知道为什么"看起来都是绿的"。后来加了 BFD 联动，主路一断 300 ms 切到备份。**这就是"感知故障"和"看见接口 UP"的区别。**

### 6_3.2 静态路由绑定 BFD
```latex
# 第1步 配置 BFD 会话（两端都配）
[SW-A] bfd
[SW-A-bfd] quit
[SW-A] bfd atob bind peer-ip 10.1.1.2 source-ip 10.1.1.1
[SW-A-bfd-session-atob] discriminator local 10
[SW-A-bfd-session-atob] discriminator remote 20
[SW-A-bfd-session-atob] commit                 # ★ 必须 commit 才生效
[SW-A-bfd-session-atob] quit

# 对端（local/remote 交叉）
[SW-B] bfd btoa bind peer-ip 10.1.1.1 source-ip 10.1.1.2
[SW-B-bfd-session-btoa] discriminator local 20
[SW-B-bfd-session-btoa] discriminator remote 10
[SW-B-bfd-session-btoa] commit

# 第2步 静态路由绑定 BFD 会话
[SW-A] ip route-static 192.168.20.0 24 10.1.1.2 track bfd-session atob

# 第3步 验证
[SW-A] display bfd session all
```

### 6_3.3 NQA 联动（支持更丰富的探测类型）
```latex
[SW-A] nqa test-instance admin link1
[SW-A-nqa-admin-link1] test-type icmp
[SW-A-nqa-admin-link1] destination-address ipv4 10.1.1.2
[SW-A-nqa-admin-link1] frequency 5
[SW-A-nqa-admin-link1] start now

[SW-A] ip route-static 0.0.0.0 0 10.1.1.2 track nqa admin link1
```

> **BFD vs NQA**：BFD 用于毫秒级链路/邻居检测（与路由协议联动）；NQA 可以做 ICMP/TCP/HTTP/DNS 等更丰富的探测（适合探测"对端业务是否真的活着"）。

---

## 6_4 连通性测试与调试工具
### 6_4.1 ping 高级用法（排错利器）
```latex
ping 192.168.1.1                      # 基本
ping -a 192.168.10.1 8.8.8.8          # 指定源地址（★ 排错必用，否则测的是设备自己）
ping -c 10 192.168.1.1                # 指定次数
ping -s 1500 192.168.1.1              # 指定包大小（测 MTU）
ping -f -s 1472 192.168.1.1           # 不分片 + 大包（精确定位 MTU 问题）
ping -t 5000 192.168.1.1              # 超时时间
```

> ★ **排错第一条就该用 **`ping -a 源地址`。很多人"能 ping 通"是因为用了设备自身接口地址，而业务源地址根本不通。

### 6_4.2 tracert
```latex
tracert 192.168.20.1                  # 看路径与断在哪一跳
tracert -a 192.168.10.1 8.8.8.8       # 指定源
```

**判读技巧：**

| 现象 | 含义 |
| --- | --- |
| 某一跳开始全是 `*` | 故障点在该跳或之后（也可能是该跳禁 ICMP） |
| 跳数来回震荡 | 存在**路由环路** |
| 第一跳就是网关但第二跳出不去 | 网关回程或上行问题 |

### 6_4.3 debugging（慎用！生产环境有风险）
```latex
<SW> debugging ospf event
<SW> terminal debugging
<SW> terminal monitor
# 用完务必关闭
<SW> undo debugging all
```

> ⚠️ `debugging` 消耗 CPU，可能把设备打瘫。**生产环境必须先确认 CPU 余量，用完立刻关。** 考试和实验中可以放心用，它是理解协议的最快方式。

---

## 6_5 综合案例：三站点企业网络（静态路由 + 浮动备份）
### 6_5.1 拓扑与需求
```latex
        总部 R1 ────────── 分支 R2
          │  ╲               │
          │    ╲             │
          │      ╲           │
          │        ╲         │
        分支 R3 ─────────────┘（备份链路，优先级低）

需求：
第1步 三站点内网互通
第2步 R1↔R2 走主链路；主链路断后经 R3 绕行
第3步 使用浮动静态路由实现主备
```

### 6_5.2 地址规划
| 链路 | 网段 | 本端 | 对端 |
| --- | --- | --- | --- |
| R1–R2 | 10.0.12.0/30 | R1 .1 | R2 .2 |
| R1–R3 | 10.0.13.0/30 | R1 .1 | R3 .2 |
| R2–R3 | 10.0.23.0/30 | R2 .1 | R3 .2 |
| R1 内网 | 192.168.1.0/24 | — | — |
| R2 内网 | 192.168.2.0/24 | — | — |
| R3 内网 | 192.168.3.0/24 | — | — |

### 6_5.3 关键配置（以 R2 为例）
```latex
[R2] ip route-static 192.168.1.0 24 10.0.12.1                      # 主：去总部
[R2] ip route-static 192.168.1.0 24 10.0.23.2 preference 100       # 备：经 R3 绕行
[R2] ip route-static 192.168.3.0 24 10.0.23.2
```

### 6_5.4 验收
```latex
# 第1步 路由表检查（以 R2 为例）
[R2] display ip routing-table 192.168.1.0
#    应只看到 preference 60 的主路由（备份路由被隐藏）

# 第2步 连通性
[R2] ping -a 192.168.2.1 192.168.1.1      # 通

# 第3步 主备切换测试
#    shutdown R2 的 10.0.12.0 接口 → 再查路由表
[R2] display ip routing-table 192.168.1.0
#    应看到 preference 100 的备份路由浮现，ping 仍通（路径变了）

# 第4步 恢复
#    undo shutdown → 主路由回来，备份再次隐藏
```

---

## 6_6 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 可能原因 | 定位命令 | 处理 |
| --- | --- | --- | --- |
| 路由表里根本没有这条路由 | 没配 / 下一跳不可达（迭代失败） | `display ip routing-table x.x.x.x verbose` | 补配或先解决下一跳可达 |
| 路由存在但 ping 不通 | 对端无回程路由（**单向通**） | 两端 `display ip routing-table` | 补回程路由 |
| 配了备份路由但不生效 | 主路由没消失（接口仍 UP） | `display ip routing-table` | 配 BFD/NQA 联动 |
| 有两条路但只走一条 | Pre 不同（正常）或等价未形成 | `display ip routing-table x.x.x.x` | 想负载分担就让 Pre 与 Cost 相同 |
| 走的路径不是我以为的 | 最长匹配命中了别的路由 | `display ip routing-table x.x.x.x` | 检查是否有更精确的路由 |
| 能 ping 通网关 ping 不通外网 | 无默认路由或 NAT 问题 | `display ip routing-table 0.0.0.0` | 补默认路由（见板块11 NAT） |
| 大包不通小包通 | MTU/MSS 问题 | `ping -f -s 1472` | 调整 MTU 或 `tcp adjust-mss` |
| tracert 在某跳循环 | 路由环路 | `tracert` | 检查环路上的路由/汇总黑洞 |

> **单向通是最高频的静态路由故障**：A 能 ping 通 B，B ping 不通 A——**永远先查对端有没有回来的路由**。

---

## 6_7 场景笔记与验证
### 6_7.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **优先级数轴** | 直连 0 → OSPF 10 → IS-IS 15 → 静态 60 → RIP 100 → 外部 150 → BGP 255（贴在桌上） |
| **静态路由写法卡** | 以太网写下一跳，点到点可写出接口，严谨写法"出接口 + 下一跳" |
| **主备切换 SOP** | 配主/备 → 查路由表（只有主）→ shutdown 主接口 → 查路由表（备浮现）→ ping 验证 |
| **坑本** | 浮动路由不生效（接口仍 UP）；单向通（无回程）；ping 不指定源（测错对象） |

### 6_7.2 验证三板斧（本板块版）
```latex
第1步 看状态：display ip interface brief（接口 up/up，IP 对不对）
第2步 看表项：display ip routing-table x.x.x.x（有没有、走哪条、Pre 多少）
第3步 打流量：ping -a 源地址 目的地址（★ 必须带源）；tracert 看路径
```

### 6_7.3 建议做一次的分层验证实验
三台路由器串联，故意做三件事并观察：

1. 删掉中间路由器的回程路由 → 体会"单向通"；
2. 主链路中间接一台交换机后拔线 → 体会"接口 UP 但路不通"（浮动路由不生效）；
3. 加上 BFD 后再拔 → 体会"毫秒级切换"。

**这三个现象记住了，静态路由排错就过关了。**

---

## 6_8 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | 先比优先级再比掩码 | **先最长匹配**，再比 Pre，再比 Cost |
| 2 | 数字大的优先级高 | **Pre 越小越优**（直连 0 最可信） |
| 3 | 静态路由 preference 默认 100 | 默认 **60**（RIP 才是 100） |
| 4 | 以太网静态路由可只写出接口 | 会导致对每个目的 IP 发 ARP，**必须写下一跳** |
| 5 | 浮动路由配了就一定会切 | 主路由不消失就不会切，需 **BFD/NQA** 或出接口形式 |
| 6 | 两条静态路由自动负载分担 | 需 Pre 与 Cost **都相同**才形成等价 |
| 7 | ping 通就是业务通 | 要 `ping -a 业务源地址` 才算数 |
| 8 | 大包小包一起测 | MTU 问题只在**大包**暴露，用 `ping -s` 测 |

---

# 板块7 · RIP 与 OSPF 路由技术
> 定位：OSPF 是 HCIP/HCIE 的第一主力协议，实验考试必考。本板块从 RIP 的"距离矢量直觉"切入，重点铺开 OSPF 的邻居状态机、LSA、区域设计、高级特性与排错。
> HCIE 实验里 OSPF 相关占比极高：**多区域设计、LSA 过滤与汇总、虚链路、认证、外部路由引入、快速收敛**——这些必须形成肌肉记忆。

## 7_1 RIP：理解距离矢量的最短路径
### 7_1.1 特点与适用
| 项目 | 说明 |
| --- | --- |
| 类型 | 距离矢量（Distance Vector） |
| 度量 | **跳数**（Hop Count），最大 15，16 为不可达 |
| 优先级 | 100 |
| 版本 | RIPv1（有类）/ RIPv2（无类，支持 VLSM、组播 224.0.0.9、认证） |
| 定时器 | Update 30s / Invalid 180s / Holddown 180s / Flush 240s |
| 适用 | 小型网络、教学理解；生产环境基本被 OSPF 取代 |

> RIP 的现实价值不在用，而在**帮你建立"距离矢量"的直觉**：我只告诉邻居"我能到哪、几跳"，不告诉它全网长什么样。理解了它的笨，才懂 OSPF 为什么聪明。

### 7_1.2 配置
```latex
# ============ R1 ============
[R1] interface ethernet 1/0
[R1-Ethernet1/0] ip address 192.168.3.1 24
[R1] interface ethernet 2/0
[R1-Ethernet2/0] ip address 192.168.5.1 24

[R1] rip 1
[R1-rip-1] version 2                     # RIPv2（支持 VLSM 与认证）
[R1-rip-1] network 192.168.3.0
[R1-rip-1] network 192.168.5.0
[R1-rip-1] undo summary                  # ★ 关闭自动汇总（避免不连续子网问题）

# ============ R2 ============
[R2] rip 1
[R2-rip-1] version 2
[R2-rip-1] network 192.168.4.0
[R2-rip-1] network 192.168.5.0
[R2-rip-1] undo summary
```

> ★ RIP 的 `network` 命令写**主类网段**，且只写自己直连的网段。

### 7_1.3 验证与关键参数
```latex
[R1] display rip                        # RIP 进程状态
[R1] display rip 1 database             # RIP 数据库
[R1] display rip 1 interface            # 参与 RIP 的接口
[R1] display ip routing-table protocol rip
```

**RIP 防环机制（必须记住四条）：**

| 机制 | 说明 |
| --- | --- |
| **水平分割（Split Horizon）** | 从某接口学到的路由，不再从该接口发回去 |
| **毒性逆转（Poison Reverse）** | 从某接口学到的路由，以跳数 16 发回去（比水平分割更彻底） |
| **抑制计时器（Hold-down）** | 路由失效后一段时间内不接受更差的路由 |
| **触发更新（Triggered Update）** | 拓扑变化立即发更新，不等 30 秒 |

> 帧中继/多点网络中水平分割会导致"分支之间学不到路由"，解法：关闭水平分割（`undo rip split-horizon`）或改用点到点子接口。

**RIPv2 认证：**

```latex
[R1] interface ethernet 2/0
[R1-Ethernet2/0] rip authentication-mode md5 usual cipher Huawei@123
```

---

## 7_2 OSPF 基础
### 7_2.1 OSPF vs RIP 核心差异
| 维度 | RIP | OSPF |
| --- | --- | --- |
| 类型 | 距离矢量（传闻路由） | **链路状态**（全网拓扑都清楚） |
| 度量 | 跳数（最大 15） | **Cost = 参考带宽 / 接口带宽** |
| 收敛 | 分钟级 | **秒级** |
| 环路 | 依赖防环机制 | **算法本身无环**（SPF） |
| 适用 | 小型 | 中小型到超大型 |

### 7_2.2 基础配置与 Router ID
```latex
[SW] ospf 1 router-id 1.1.1.1                # 手动指定 Router ID（★ 生产必须）
[SW-ospf-1] area 0
[SW-ospf-1-area-0.0.0.0] network 192.168.10.0 0.0.0.255
[SW-ospf-1-area-0.0.0.0] network 192.168.20.0 0.0.0.255
```

**Router ID 规则**：第1步 手动配置优先；第2步 否则取最大的 Loopback 接口 IP；第3步 否则取最大的物理接口 IP。Router ID **必须全网唯一**，冲突会导致邻居起不来、路由计算混乱。修改后需重启进程：

```latex
<SW> reset ospf 1 process
```

### 7_2.3 通配符掩码（Wildcard Mask）
OSPF 的 `network` 命令用的是**反掩码**（0 = 必须匹配，1 = 不关心）：

```latex
network 192.168.10.0 0.0.0.255      # 匹配 192.168.10.0/24
network 192.168.10.1 0.0.0.0        # 精确匹配单个接口 IP（推荐写法！）
network 0.0.0.0 255.255.255.255     # 匹配所有接口
```

> 推荐使用 `network 接口IP 0.0.0.0` 的精确写法，避免误把其他接口宣告进 OSPF。

**接口使能方式（更直观，推荐）：**

```latex
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] ospf enable 1 area 0
```

### 7_2.4 Cost 计算
```latex
Cost = 参考带宽（默认 100 Mbps） / 接口带宽（Mbps），最小为 1

100M 以太网 → 100/100 = 1
10M 以太网  → 100/10  = 10
1000M       → 100/1000 = 0.1 → 取 1（不足 1 按 1 算）
```

> 🚨 **千兆/万兆网络必须修改参考带宽**，否则 GE、10GE、40GE 的 cost 全是 1，SPF 无法选出最优路径。**且全网所有 OSPF 路由器必须一致**：

```latex
[SW-ospf-1] bandwidth-reference 100000       # 单位 Mbps，建议设为网络中最大带宽
```

手工改接口 cost：

```latex
[SW] interface gigabitethernet 0/0/3
[SW-GigabitEthernet0/0/3] ospf cost 100
```

---

## 7_3 OSPF 邻居建立
### 7_3.1 五类报文
| 报文 | 作用 |
| --- | --- |
| **Hello** | 发现/维持邻居，选举 DR/BDR |
| **DD（Database Description）** | 描述 LSDB 摘要（目录） |
| **LSR（Link State Request）** | 请求缺失的 LSA 详情 |
| **LSU（Link State Update）** | 发送 LSA 详情 |
| **LSAck** | 确认收到 |

### 7_3.2 七种邻居状态机（必背）
```latex
Down → Init → 2-Way → ExStart → Exchange → Loading → Full
```

| 状态 | 含义 | 卡住意味着 |
| --- | --- | --- |
| **Down** | 未收到 Hello | 链路不通接口未宣告 |
| **Init** | 收到对端 Hello，但对方没列出我的 RID | 单向链路、ACL 拦截 |
| **2-Way** | 双向确认（双方 Hello 都含对方 RID） | 正常（DROther 之间就停在这） |
| **ExStart** | 协商主从（Master/Slave）与 DD 序列号 | **MTU 不匹配** |
| **Exchange** | 交换 DD 摘要 | 大包被丢弃（MTU） |
| **Loading** | 发 LSR 请求缺失 LSA | LSA 请求无响应 |
| **Full** | LSDB 同步完成 | ★ 正常终态 |

> **DROther 之间停在 2-Way 是正常的**（只有 DR/BDR 与 DROther 之间才会到 Full）。看到 2-Way 先判断是不是广播网络中的 DROther 关系。

### 7_3.3 DR/BDR 选举
```latex
第1步 比较接口优先级（0–255，默认 1，0 = 不参与选举）
第2步 优先级相同，比较 Router ID，越大越优
第3步 DR/BDR 一旦选定，非抢占（新设备优先级更高也不会抢，除非重启进程）
```

```latex
[SW-GigabitEthernet0/0/1] ospf dr-priority 100
```

### 7_3.4 网络类型
| 类型 | Hello/Dead | DR 选举 | 典型链路 |
| --- | --- | --- | --- |
| **Broadcast**（默认以太网） | 10s / 40s | 选举 | 以太网 |
| **P2P** | 10s / 40s | 不选举 | 串行链路、专线 |
| **NBMA** | 30s / 120s | 选举（需手工指定 peer） | 帧中继、ATM |
| **P2MP** | 30s / 120s | 不选举 | 部分无线/专网 |

```latex
[SW-GigabitEthernet0/0/1] ospf network-type p2p
```

> ⚠️ **网络类型不匹配**时，即使 Hello 时间碰巧一致能建邻，**路由也会算错**（因为对链路的描述方式不同）。这是最隐蔽的坑之一。

### 7_3.5 邻居建立失败排查清单
| # | 原因 | 现象 | 定位命令 |
| --- | --- | --- | --- |
| 1 | Router ID 冲突 | 邻居反复震荡 | `display ospf brief` |
| 2 | 区域 ID 不一致 | 起不来 | `display ospf interface` |
| 3 | 认证类型/密码不一致 | 起不来 | `display ospf error` |
| 4 | Hello/Dead 时间不一致 | 起不来 | `display ospf interface` |
| 5 | 网络类型不匹配 | 能建邻但路由错 | `display ospf interface` |
| 6 | **MTU 不匹配** | 卡 ExStart/Exchange | `display ospf error` |
| 7 | 接口未宣告 / network 掩码写错 | 一直 Down | `display ospf interface` |
| 8 | 掩码不一致（广播网） | 卡 2-Way 或起不来 | `display ip interface brief` |
| 9 | ACL 拦了 224.0.0.5 | 起不来 | `display acl` |
| 10 | 区域类型不一致（Stub 标志位） | 起不来 | `display ospf brief` |
| 11 | 静默接口 | 不收发 Hello | `display ospf interface` |

> **第一刀永远是 **`display ospf error` ——它会直接告诉你哪类报文出错、错在哪个字段，比逐项对比配置快十倍。

---

## 7_4 OSPF 区域与 LSA
### 7_4.1 区域设计原则
```latex
┌─────────────────────────────────────────┐
│            Area 0（骨干区域）              │
│   所有非骨干区域必须直接/逻辑连到 Area 0    │
└────┬──────────┬──────────┬──────────────┘
     │          │          │
   Area 10    Area 20    Area 30
   （分支A）   （分支B）   （DMZ）
```

规则：

1. **所有非骨干区域必须与 Area 0 相连**；
2. Area 0 必须是连续的；
3. ABR（区域边界路由器）连接多个区域，至少有一个接口在 Area 0；
4. ASBR（自治系统边界路由器）引入外部路由。

### 7_4.2 常用 LSA 类型（考试必考）
| LSA | 名称 | 产生者 | 传播范围 | 作用 |
| --- | --- | --- | --- | --- |
| **Type 1** | Router LSA | 每台路由器 | 本区域内 | 描述自身链路状态 |
| **Type 2** | Network LSA | DR | 本区域内 | 描述广播网段的链路 |
| **Type 3** | Summary LSA | ABR | 区域间 | 区域间路由（网段汇总） |
| **Type 4** | ASBR Summary | ABR | 区域间 | 如何到达 ASBR |
| **Type 5** | AS External | ASBR | 全网（除特殊区域） | 外部路由 |
| **Type 7** | NSSA External | ASBR in NSSA | NSSA 内 | NSSA 外部路由（出区域时转 Type 5） |

```latex
[SW] display ospf lsdb                       # LSDB 总览
[SW] display ospf lsdb router                # Type 1
[SW] display ospf lsdb network               # Type 2
[SW] display ospf lsdb summary               # Type 3
[SW] display ospf lsdb asbr                  # Type 4
[SW] display ospf lsdb ase                   # Type 5
[SW] display ospf lsdb nssa                  # Type 7
```

**OSPF 全景验证命令（一张表过完整个协议）：**

```latex
[SW] display ospf brief              # 进程概要（Router ID、区域数、实例）
[SW] display ospf peer               # 邻居详情（状态机停在哪一步）
[SW] display ospf peer brief         # 邻居摘要
[SW] display ospf interface          # 接口的开销/网络类型/DR/BDR/定时器
[SW] display ospf routing            # OSPF 学到的路由（与全局路由表对比看是否被过滤）
[SW] display ospf error              # ★ 邻居起不来时的第一命令
[SW] display ospf vlink              # 虚链路状态
```

### 7_4.3 特殊区域（减少 LSA、缩小 LSDB）
| 区域类型 | 允许的 LSA | 禁止 | 默认路由 | 适用 |
| --- | --- | --- | --- | --- |
| **普通区域** | 1/2/3/4/5 | — | 需手工下发 | 通用 |
| **Stub** | 1/2/3 | 4/5 | ABR 自动下发 Type 3 默认路由 | 分支，无需外部路由 |
| **Totally Stub** | 1/2 + 默认 | 3/4/5 | ABR 自动下发 | 分支，路由最简 |
| **NSSA** | 1/2/3/7 | 4/5（可引入外部路由为 Type 7） | 需手工下发 | 分支有外部路由需引入 |
| **Totally NSSA** | 1/2 + 默认 + 7 | 3/4/5 | ABR 自动下发 | 引入外部 + 最简路由表 |

```latex
# Stub（区域内所有路由器都要配）
[SW-ospf-1-area-0.0.0.10] stub

# Totally Stub（只在 ABR 上配）
[ABR-ospf-1-area-0.0.0.10] stub no-summary

# NSSA
[SW-ospf-1-area-0.0.0.20] nssa
[ABR-ospf-1-area-0.0.0.20] nssa no-summary                  # Totally NSSA
[ABR-ospf-1-area-0.0.0.20] nssa default-route-advertise     # 下发默认路由
```

> ⚠️ **同一区域内所有路由器的区域类型必须一致**，否则邻居无法建立（Hello 报文中的区域类型标志位不匹配）。

### 7_4.4 路由汇总
```latex
# ABR 汇总（区域间路由）
[ABR-ospf-1] area 10
[ABR-ospf-1-area-0.0.0.10] abr-summary 192.168.0.0 255.255.240.0

# ASBR 汇总（外部路由）
[ASBR-ospf-1] asbr-summary 172.16.0.0 255.255.240.0
```

作用：减小 LSDB 与路由表，**提高稳定性**（明细路由震荡不再影响其他区域）。

---

## 7_5 OSPF 高级特性
### 7_5.1 认证
```latex
# 区域认证（MD5）
[SW-ospf-1] area 0
[SW-ospf-1-area-0.0.0.0] authentication-mode md5 1 cipher Huawei@123

# 接口认证（优先级高于区域认证，两端接口配）
[SW-GigabitEthernet0/0/1] ospf authentication-mode md5 1 cipher Huawei@123
```

### 7_5.2 静默接口（不收发 Hello）
```latex
[SW-ospf-1] silent-interface Vlanif10        # 接终端的网段不参与 OSPF
```

用途：接口已宣告进 OSPF 但不希望向终端发 Hello（安全 + 省资源）。

### 7_5.3 路由引入与过滤
```latex
# 引入直连/静态/其他协议
[SW-ospf-1] import-route static
[SW-ospf-1] import-route direct
[SW-ospf-1] import-route bgp

# 引入时打标记与开销
[SW-ospf-1] import-route static type 1 cost 100 tag 100

# 用 IP-Prefix + 策略过滤
[SW] ip ip-prefix PL-NO-CCTV index 10 deny 192.168.30.0 24
[SW] ip ip-prefix PL-NO-CCTV index 20 permit 0.0.0.0 0 less-equal 32
[SW-ospf-1] filter-policy ip-prefix PL-NO-CCTV import

# 过滤 Type 3 LSA 进入某区域
[ABR-ospf-1-area-0.0.0.10] filter ip-prefix PL-XXX import
```

### 7_5.4 下发默认路由
```latex
[SW-ospf-1] default-route-advertise always            # 强制下发（无论本机有无默认路由）
[SW-ospf-1] default-route-advertise                   # 本机存在默认路由才下发（推荐）
[SW-ospf-1] default-route-advertise type 1 cost 10    # 带开销与类型
```

### 7_5.5 快速收敛
```latex
# BFD 联动（毫秒级检测）
[SW-ospf-1] bfd all-interfaces enable

# SPF 智能定时器（避免频繁计算）
[SW-ospf-1] spf-schedule-interval millisecond 50

# LSA 生成/接收延迟
[SW-ospf-1] lsa-generation-interval 1
[SW-ospf-1] lsa-arrival-interval 1

# 快速重路由 FRR（LFA 备份路径，切换 <50ms）
[SW-ospf-1] frr
[SW-ospf-1-frr] loop-free-alternate
```

### 7_5.6 虚链路（Virtual Link）
场景：某区域无法物理直连 Area 0（如两家公司合并，中间隔着一个非骨干区域）。

```latex
[ABR1-ospf-1] area 10
[ABR1-ospf-1-area-0.0.0.10] vlink-peer 3.3.3.3        # 对端 ABR 的 Router ID
```

> 虚链路是"补丁"手段，能不用就不用。考场上要会配、要能说出它的代价（增加复杂度、虚链路不能穿越 Stub 区域）。

---

## 7_6 综合配置案例：多区域 + 特殊区域 + 汇总
### 7_6.1 规划
```latex
                 Internet
                    │
              ┌─────┴─────┐
              │   R-Exit  │  Area 0
              └─────┬─────┘
              10.0.0.0/30
                    │
              ┌─────┴─────┐
              │  Core-ABR │  Area 0 / Area 10 / Area 20
              └──┬─────┬──┘
        10.0.10.0/30  10.0.20.0/30
            │             │
        ┌───┴───┐     ┌───┴───┐
        │  AGG1 │     │  AGG2 │   Area 10（普通）/ Area 20（NSSA）
        └───────┘     └───────┘
```

### 7_6.2 关键配置
```latex
# ============ Core-ABR ============
[Core] ospf 1 router-id 1.1.1.1
[Core-ospf-1] area 0
[Core-ospf-1-area-0.0.0.0] network 10.0.0.0 0.0.0.3
[Core-ospf-1] area 10
[Core-ospf-1-area-0.0.0.10] network 10.0.10.0 0.0.0.3
[Core-ospf-1-area-0.0.0.10] abr-summary 192.168.0.0 255.255.240.0
[Core-ospf-1] area 20
[Core-ospf-1-area-0.0.0.20] network 10.0.20.0 0.0.0.3
[Core-ospf-1-area-0.0.0.20] nssa no-summary                  # Totally NSSA

# 出口默认路由下发
[Core-ospf-1] default-route-advertise

# ============ AGG2（NSSA 区域）============
[AGG2] ospf 1 router-id 3.3.3.3
[AGG2-ospf-1] area 20
[AGG2-ospf-1-area-0.0.0.20] network 10.0.20.0 0.0.0.3
[AGG2-ospf-1-area-0.0.0.20] nssa
[AGG2-ospf-1] import-route static type 2                     # 引入为 Type 7
```

### 7_6.3 验证
```latex
[Core] display ospf peer brief             # 邻居（Full 才算数）
[Core] display ospf lsdb                   # 各类 LSA
[Core] display ospf routing                # OSPF 路由
[Core] display ip routing-table protocol ospf
[AGG2] display ospf lsdb nssa              # NSSA 区域应有 Type 7
[AGG2] display ip routing-table            # Totally NSSA 应只有一条默认路由 + 直连
```

---

## 7_7 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 排查命令 | 常见根因 |
| --- | --- | --- |
| 邻居起不来 | `display ospf error` | 区域 ID/认证/Hello 时间/MTU/网络类型 |
| 卡在 ExStart | `display ospf error` | **MTU 不匹配** |
| 卡在 2-Way | `display ospf peer` | 广播网 DROther 之间正常；或都配了 priority 0 |
| 邻居有但学不到路由 | `display ospf lsdb`、`display ospf routing` | filter-policy 过滤 / 网络类型不匹配 |
| 有路由但不通 | `display ip routing-table`、`display fib` | 被更优来源（静态/BGP）抢了；或下一跳不可达 |
| 路由表比预期大 | `display ospf lsdb` | 未做汇总 / 未配特殊区域 |
| 外部路由学不到 | `display ospf lsdb ase` | Stub 区域内禁止 Type 5 |
| 邻居反复震荡 | `display logbuffer` | Router ID 冲突 / 链路质量差 |

---

## 7_8 场景笔记与验证
### 7_8.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **七态状态机卡点表** | Down/Init/2-Way/ExStart/Exchange/Loading/Full 各自"卡住意味着什么" |
| **LSA 类型卡** | 1/2/3/4/5/7 的产生者、范围、作用（考前一分钟能默） |
| **特殊区域对照表** | 允许哪些 LSA、谁下发默认路由 |
| **坑本** | 掩码写成正掩码；忘记 bandwidth-reference；Stub 区域两端类型不一致；静默接口配错 |

### 7_8.2 验证三板斧（本板块版）
```latex
第1步 看状态：display ospf peer brief           邻居 Full？Role 对不对（DR/BDR/DROther）
第2步 看表项：display ospf lsdb（LSA 齐不齐）、display ospf routing（算出来没）
第3步 打流量：ping -a 源 目的 + tracert（路径对不对）
```

**加两刀：**

```latex
display ospf interface             # Hello/Dead、网络类型、cost、DR 优先级
display ospf error                 # 邻居起不来时的第一刀
```

### 7_8.3 建议做的两个破坏性实验
1. **改一端 MTU 为 9000** → 观察邻居卡在 ExStart，然后 `display ospf error` 看报错字段；
2. **一端改网络类型为 P2P** → 观察邻居能 Full 但路由条目异常。

这两个坑亲手踩过，考场上遇到"邻居起不来"类排错题就有直觉了。

---

## 7_9 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | network 用正掩码 | 必须用**反掩码**（wildcard） |
| 2 | Router ID 自动选就行 | 生产**必须手工指定**且全网唯一 |
| 3 | 千兆链路 cost 各不相同 | 默认参考带宽 100 Mbps，GE 以上都是 1，**必须改 bandwidth-reference** |
| 4 | 2-Way 是故障 | 广播网 DROther 之间 **2-Way 正常** |
| 5 | DR 优先级高的会自动抢 | **非抢占**，需重启进程 |
| 6 | Stub 区域只在一端配 | **区域内所有路由器都要配**（Totally Stub 只在 ABR） |
| 7 | MTU 只影响大包 | MTU 不匹配会让邻居**卡在 ExStart** |
| 8 | 改了 Router ID 立即生效 | 需 `reset ospf process` |
| 9 | SPF 越频繁越好 | 需配智能定时器，否则路由震荡拖垮 CPU |
| 10 | 静态备份路由 preference 配 50 | 50 < 60 会抢在静态前面失效；**浮动静态要 >60** |

---

# 板块8 · IS-IS 与 BGP 路由技术
> 定位：IS-IS 是承载网与大型园区 IGP 的主力，BGP 是 AS 之间与业务承载的核心。HCIE 实验几乎必考 BGP + 路由策略 + 反射器。
> 学习顺序建议：**先吃透 BGP 的选路规则与属性，再练路由策略（Route-Policy、IP-Prefix、Community）**——这才是 HCIE 实验里真正的得分点。

## 8_1 IS-IS 基础
### 8_1.1 IS-IS vs OSPF 选型
| 维度 | OSPF | IS-IS |
| --- | --- | --- |
| 承载协议 | IP（协议号 89） | 直接封装在数据链路层（更中立，天然支持 IPv6） |
| 区域划分 | **基于接口**（ABR 在区域内） | **基于路由器**（一台路由器整体属于一个区域） |
| 扩展性 | 好 | **更好**（TLV 结构，易扩展，运营商首选） |
| 收敛 | 快 | 更快（PRC 部分路由计算） |
| 典型应用 | 园区网、企业网 | **运营商骨干、大型数据中心、承载网** |

### 8_1.2 NET 地址（IS-IS 的身份证）
```latex
NET 格式：Area ID (1-13字节) + System ID (6字节) + SEL (1字节，固定 00)

示例：49.0001.0000.0000.0001.00
      └─49.0001──┘ └─0000.0000.0001─┘ └00┘
        Area ID        System ID        SEL
```

**System ID 规划惯例**：由 Router ID 或 Loopback IP 转换而来，把 IP 每段补足 3 位后按 4 位分组：

```latex
Loopback 10.1.1.1  →  010.001.001.001  →  0100.0100.1001
NET 示例：49.0001.0100.0100.1001.00
```

### 8_1.3 IS-IS 配置
```latex
[Router] isis 1
[Router-isis-1] network-entity 49.0001.0000.0000.0001.00
[Router-isis-1] is-level level-2              # level-1 / level-2 / level-1-2（默认）
[Router-isis-1] cost-style wide               # ★ 宽度量（支持大 Cost 与 TE，强烈建议）
[Router-isis-1] quit

[Router] interface gigabitethernet 0/0/1
[Router-GigabitEthernet0/0/1] ip address 10.0.12.1 30
[Router-GigabitEthernet0/0/1] isis enable 1
[Router-GigabitEthernet0/0/1] isis circuit-type p2p     # P2P 链路建议改（避免 DIS 选举）
[Router-GigabitEthernet0/0/1] isis cost 10

[Router] interface loopback 0
[Router-LoopBack0] ip address 10.1.1.1 32
[Router-LoopBack0] isis enable 1
```

### 8_1.4 路由器级别与区域
| 级别 | 含义 | 类比 OSPF |
| --- | --- | --- |
| **Level-1** | 区域内路由，类似 Stub | 区域内 |
| **Level-2** | 骨干区域路由 | 骨干区域 |
| **Level-1-2**（默认） | 同时参与，类似 ABR | ABR |

```latex
L1 区域：类似 OSPF 的 Totally Stubby Area
        L1 路由器只知道本区域，通过最近的 L1-2 路由器（发 ATT 位）产生默认路由出去
L2 区域：骨干，由所有 L2 与 L1-2 路由器组成（不需要"物理连续"，比 OSPF 灵活）
```

### 8_1.5 验证
```latex
[Router] display isis peer                    # 邻居
[Router] display isis brief                   # 概要
[Router] display isis lsdb                    # LSDB
[Router] display isis route                   # IS-IS 路由
[Router] display isis interface               # 接口
[Router] display isis error                   # 错误统计
[Router] display ip routing-table protocol isis
```

### 8_1.6 IS-IS 高级特性
```latex
# 路由渗透（L2 → L1，让 L1 区域学到明细路由，避免次优路径）
[Router-isis-1] import-route isis level-2 into level-1

# 认证
[Router-isis-1] area-authentication-mode md5 cipher Isis@Area
[Router-isis-1] domain-authentication-mode md5 cipher Isis@Domain
[Router-GigabitEthernet0/0/1] isis authentication-mode md5 cipher Isis@Link

# 快速收敛
[Router-isis-1] bfd all-interfaces enable
[Router-isis-1] timer lsp-generation 1 50 50
[Router-isis-1] flash-flood 15

# 路由汇总
[Router-isis-1] summary 10.1.0.0 255.255.0.0 level-2

# 开销
[Router-isis-1] auto-cost enable              # 自动按带宽算 cost
[Router-isis-1] bandwidth-reference 100000
```

---

## 8_2 BGP 基础
### 8_2.1 BGP 是什么
+ **外部网关协议（EGP）**，用于 AS（自治系统）之间交换路由；
+ 基于 **TCP 179**，可靠的单播连接；
+ **不计算最短路径，只传递路由 + 丰富的属性**（路径矢量）；
+ 核心价值：**策略控制能力极强**（这才是它存在的理由）。

### 8_2.2 IBGP vs EBGP
| 维度 | EBGP | IBGP |
| --- | --- | --- |
| 位置 | 不同 AS 之间 | 同一 AS 内部 |
| 默认 TTL | 1（直连） | 255 |
| 下一跳 | 会改为自己 | **默认不改**（需 `next-hop-local`） |
| 防环 | AS_Path | **水平分割**（从 IBGP 学到的不再转发给 IBGP 邻居） |
| 管理距离 | 255 | 255 |

> **IBGP 水平分割的后果**：AS 内部所有 IBGP 路由器必须**全互联**（n(n-1)/2 条连接），规模一大就爆炸。解法：**路由反射器（Route Reflector）** 或 **联盟（Confederation）**。

### 8_2.3 基本配置
```latex
# ============ EBGP ============
[SwitchA] bgp 65008
[SwitchA-bgp] router-id 10.1.1.1
[SwitchA-bgp] peer 10.3.1.1 as-number 65009                     # 对端 AS 号
[SwitchA-bgp] ipv4-family unicast
[SwitchA-bgp-af-ipv4] network 10.8.1.0 255.255.255.0             # 发布网段（必须精确存在于路由表）
[SwitchA-bgp-af-ipv4] peer 10.3.1.1 enable
[SwitchA-bgp-af-ipv4] quit

# ============ IBGP + next-hop-local ============
[SwitchB] bgp 65009
[SwitchB-bgp] router-id 10.2.2.2
[SwitchB-bgp] peer 10.5.5.5 as-number 65009                     # 同 AS = IBGP
[SwitchB-bgp] peer 10.5.5.5 connect-interface LoopBack 0        # 用 Loopback 建邻（更稳）
[SwitchB-bgp] ipv4-family unicast
[SwitchB-bgp-af-ipv4] peer 10.5.5.5 enable
[SwitchB-bgp-af-ipv4] peer 10.5.5.5 next-hop-local              # ★ IBGP 必配
```

> ⚠️ **BGP **`network`** 命令的严格性**：要求该网段**精确存在于 IP 路由表中**（掩码完全匹配），否则不会发布。这与 OSPF 的 network 完全不同，是新手高频踩坑点。

### 8_2.4 BGP 对等体状态机
```latex
Idle → Connect → Active → OpenSent → OpenConfirm → Established
```

| 卡在 | 常见原因 |
| --- | --- |
| **Idle** | 无去往 peer 的路由 / 配错 AS / 被 ACL 拦 |
| **Active** | TCP 连接失败（对端未配、端口不通TTL 不够） |
| **Established** | ★ 正常 |

```latex
[Router] display bgp peer                 # 看 State
[Router] display bgp peer verbose         # 详细信息
```

**非直连 EBGP 需改 TTL：**

```latex
[Router-bgp] peer 10.3.1.1 ebgp-max-hop 2       # 默认 TTL=1，跨一跳需改大
```

**用 Loopback 建 EBGP：**

```latex
[Router-bgp] peer 3.3.3.3 as-number 65009
[Router-bgp] peer 3.3.3.3 connect-interface LoopBack 0
[Router-bgp] peer 3.3.3.3 ebgp-max-hop 2
[Router] ip route-static 3.3.3.3 32 10.0.12.2    # 必须有到 peer Loopback 的路由
```

### 8_2.5 BGP 报文类型
| 报文 | 作用 |
| --- | --- |
| Open | 建立连接，协商参数（版本、AS、Hold Time、能力） |
| Update | 发布/撤销路由 |
| Keepalive | 保活（默认 60s，Hold 180s） |
| Notification | 报错并断开 |
| Route-Refresh | 请求重发路由 |

---

## 8_3 BGP 选路规则（核心中的核心）
### 8_3.1 选路原则：11 步顺序（华为官方口径）
> ⚠️ **先记住两个前提**：
> + `Preferred-Value` 是华为私有属性，只在**本设备**有效，不会传给任何对等体——它是"强制本机选路"的最后手段；
> + **下一跳不可达的路由根本不参与选路**（连比较的资格都没有），这是最常被忽略的前置条件。

华为设备按以下顺序**依次比较**，前一步比出结果就停止：

| 步 | 比较项 | 优选 | 作用域 / 备注 |
| --- | --- | --- | --- |
| **0** | **下一跳可达性** | 可达者入选 | **前置条件**，不可达直接淘汰 |
| **1** | **Preferred-Value**（PrefVal） | **最大** | 华为私有，**仅本设备有效**，默认 0 |
| **2** | **Local_Preference** | **最大** | AS 内传播，默认 100 |
| **3** | **本地始发优先级** | 手动聚合 > 自动聚合 > `network` > `import-route` > 从对等体学习 | 逐级比较 |
| **4** | **AS_Path** | **最短** | AS_Path 为空时优选空的 |
| **5** | **Origin** | **IGP(i) > EGP(e) > Incomplete(?)** | — |
| **6** | **MED** | **最小** | 默认 0；**只在来自同一 AS 的路由之间比** |
| **7** | **对等体类型** | **EBGP > IBGP > LocalCross > RemoteCross** | VPN 场景特有 |
| **8** | **到下一跳的 IGP Metric** | **最小** | 即"最近的下一跳" |
| **9** | **Cluster_List** | **最短** | 路由反射器场景 |
| **10** | **Router ID** | **最小** | 若携带 Originator_ID，则改比 Originator_ID 且不再比 RID |
| **11** | **对等体 IP 地址** | **最小** | 最终 tie-breaker |

**记忆口诀（第 1–8 步，考试要求能默写）：**

```latex
一私（PrefVal）二本（Local_Pref）三始发（聚合>network>import）
四短（AS_Path）五源（Origin）六 MED（小）
七类（EBGP>IBGP）八近（IGP Metric 小）
九簇（Cluster 短）十 ID（RID 小）十一对端 IP 小
```

**等价负载分担的成立条件（易考）：**

```latex
第 1 ~ 第 8 步中所有需要比较的属性完全相同，才会形成 BGP 等价路由。
即：PrefVal、Local_Pref、始发方式、AS_Path（长度与内容）、Origin、MED、对等体类型、IGP Metric 全部一致。

[Router-bgp-af-ipv4] maximum load-balancing 2          # 允许 2 条等价
[Router-bgp-af-ipv4] maximum load-balancing eibgp 2    # EBGP/IBGP 混合负载分担
```

> 实验里调选路最常用的三个手段：**Local_Preference（控制出 AS 流量）**、**MED（控制入 AS 流量）**、**AS_Path Prepend（粗粒度影响入向）**。PrefVal 只在单机救急时用，因为它不传播。

### 8_3.2 关键属性速查
| 属性 | 作用域 | 默认 | 方向 | 用途 |
| --- | --- | --- | --- | --- |
| **Preferred-Value** | 本设备（华为私有） | 0 | 越大越优 | 本机强制选路 |
| **Local_Preference** | AS 内传播 | 100 | 越大越优 | 控制**出 AS** 流量 |
| **MED** | 相邻 AS 间 | 0 | 越小越优 | 控制**入 AS** 流量 |
| **AS_Path** | 全局 | — | 越短越优 | 防环 + 选路 |
| **Origin** | 全局 | — | i > e > ? | 路由来源 |
| **Community** | 自定义 | — | 标记 | 批量策略 |
| **Next_Hop** | — | — | 必须可达 | 转发依据 |

---

## 8_4 路由策略三件套
> **这是 HCIE 实验的必考核心**：所有"改属性、控选路、过滤路由"的需求，都要靠它们实现。

### 8_4.1 IP-Prefix（精确匹配路由）
```latex
[Router] ip ip-prefix PL-A index 10 permit 192.168.1.0 24
[Router] ip ip-prefix PL-B index 10 permit 10.0.0.0 8 greater-equal 16 less-equal 24
[Router] ip ip-prefix PL-DEFAULT index 10 permit 0.0.0.0 0
[Router] ip ip-prefix PL-ALL index 10 permit 0.0.0.0 0 less-equal 32
```

匹配规则：先按 index 从小到大匹配，命中即停止；末尾隐含 deny all。

```latex
greater-equal 16 less-equal 24   # 掩码长度在 16~24 之间
greater-equal 24                 # 掩码 ≥24
less-equal 8                     # 掩码 ≤8
```

### 8_4.2 Route-Policy（策略核心）
```latex
[Router] route-policy RP-SET-LP permit node 10
[Router-route-policy] if-match ip-prefix PL-A
[Router-route-policy] apply local-preference 300
[Router-route-policy] quit

[Router] route-policy RP-SET-LP permit node 20          # ★ 放空节点放行其余路由
[Router-route-policy] apply local-preference 100
[Router-route-policy] quit
```

> ⚠️ **Route-Policy 末尾隐含 deny all**。如果不写第二个 permit 节点，未匹配 PL-A 的路由会被**全部拒掉**——这是生产事故的经典原因。

### 8_4.3 Community（团体属性）
```latex
# 打团体属性
[Router] route-policy RP-COMM permit node 10
[Router-route-policy] apply community 65001:100

# 按团体属性匹配
[Router] ip community-filter 1 permit 65001:100
[Router] route-policy RP-MATCH permit node 10
[Router-route-policy] if-match community-filter 1

# 发布时携带团体属性（★ 必须配，否则不传递）
[Router-bgp-af-ipv4] peer 10.1.1.2 advertise-community

# 公认团体属性
no-export          # 不通告给 EBGP 对等体
no-advertise       # 不通告给任何对等体
internet           # 默认，可通告给所有
local-as           # 只在联盟内传播
```

### 8_4.4 AS_Path Filter
```latex
[Router] ip as-path-filter 1 permit ^65009$           # 起源于 AS 65009
[Router] ip as-path-filter 2 permit _65010_           # 经过 AS 65010
[Router] ip as-path-filter 3 deny ^$                  # 拒绝本地始发（空 AS_Path）
[Router] ip as-path-filter 3 permit .*                # 允许其余
```

### 8_4.5 应用策略
```latex
# 对某个 peer 应用出/入方向策略
[Router-bgp-af-ipv4] peer 10.1.1.2 route-policy RP-SET-LP import
[Router-bgp-af-ipv4] peer 10.1.1.2 route-policy RP-SET-MED export

# —— 其他常用 apply 动作 ——
[Router-route-policy] apply preferred-value 100      # 华为私有，仅本机有效，越大越优
[Router-route-policy] apply origin igp               # 修改 Origin（igp > egp > incomplete）
[Router-route-policy] apply community 100:1          # 打团体属性
[Router-route-policy] apply local-preference 200
[Router-route-policy] apply as-path 65001 additive   # AS_Path 追加（影响入向）
[Router-route-policy] if-match route-type internal   # 匹配路由类型（内部/外部）

# 引入路由时应用
[Router-bgp] import-route ospf 1 route-policy RP-OSPF-IN

# 全局对引入路由过滤
[Router-bgp] filter-policy ip-prefix PL-XXX export
```

---

## 8_5 路由反射器与联盟
### 8_5.1 路由反射器（Route Reflector）
解决 IBGP 全互联问题：RR 从 Client 学到的路由可以反射给其他 Client 和 Non-Client，从而打破水平分割。

```latex
# ================= RR 上 =================
[RR] bgp 65009
[RR-bgp] peer 10.2.2.2 as-number 65009
[RR-bgp] peer 10.2.2.2 connect-interface LoopBack 0
[RR-bgp] ipv4-family unicast
[RR-bgp-af-ipv4] peer 10.2.2.2 enable
[RR-bgp-af-ipv4] peer 10.2.2.2 reflect-client          # ★ 指定为 Client
[RR-bgp-af-ipv4] peer 10.2.2.2 next-hop-local

# Client 上：只需与 RR 建邻（普通 IBGP 配置）
```

**防环机制：**

| 属性 | 作用 |
| --- | --- |
| **Cluster_List** | 记录经过的 RR 集群，RR 收到含自己 Cluster ID 的路由则丢弃 |
| **Originator_ID** | 记录始发者的 Router ID，始发者收到自己始发的路由则丢弃 |

> 生产建议：**RR 双机冗余**（两台 RR 相同 Cluster ID），Client 同时与两台 RR 建邻。

### 8_5.2 联盟（Confederation）
把一个大 AS 划分成若干个子 AS（用私有 AS 号 64512–65535），子 AS 内全互联，子 AS 之间用类 EBGP 连接。

```latex
[Router] bgp 65001                                  # 子 AS 号
[Router-bgp] confederation id 100                   # 对外呈现的联盟 ID
[Router-bgp] confederation peer-as 65002 65003      # 其他子 AS
```

> **RR vs 联盟**：RR 简单、改动小，是主流；联盟需要改 AS 号规划，适合超大规模或多园区合并场景。论述题里回答"优先 RR，超大规模再考虑联盟"通常不会错。

---

## 8_6 路由聚合
```latex
# 自动聚合（按主类聚合，不推荐）
[Router-bgp] summary automatic

# 手工聚合（推荐）
[Router-bgp] aggregate 172.16.0.0 255.255.240.0 detail-suppressed     # 抑制明细
[Router-bgp] aggregate 172.16.0.0 255.255.240.0 as-set                # 保留 AS_Path 防环
[Router-bgp] aggregate 172.16.0.0 255.255.240.0 attribute-policy RP-AGG  # 聚合后打属性
```

> **做汇总必须配一条指向 NULL0 的黑洞路由**（见板块6），否则明细路由消失时可能产生环路。

---

## 8_7 综合案例：企业双出口 BGP + 路由策略
### 8_7.1 需求
```latex
企业 AS 65001，双出口：
  ISP-A（AS 100）：主用，带宽大
  ISP-B（AS 200）：备份，带宽小
目标：
  第1步 出方向：访问 ISP-A 的网段走 ISP-A（LP 高），其余默认走 ISP-A，ISP-B 备份
  第2步 入方向：让外部流量优先从 ISP-A 进来（MED 小）
```

### 8_7.2 关键配置
```latex
[Router] bgp 65001
[Router-bgp] peer 100.1.1.1 as-number 100            # ISP-A
[Router-bgp] peer 200.1.1.1 as-number 200            # ISP-B

# 汇总路由锚点（配合黑洞路由）
[Router] ip route-static 172.16.0.0 16 NULL 0
[Router-bgp] network 172.16.0.0 16

# ===== 前缀列表：定义 ISP 网段 =====
[Router] ip ip-prefix PL-ISP-A index 10 permit 100.100.0.0 16
[Router] ip ip-prefix PL-ISP-B index 10 permit 200.200.0.0 16

# ===== 入方向策略（控制"出去"的流量）=====
[Router] route-policy RP-IN-A permit node 10
[Router-route-policy] if-match ip-prefix PL-ISP-A
[Router-route-policy] apply local-preference 300       # ISP-A 网段 LP 最高
[Router] route-policy RP-IN-A permit node 20
[Router-route-policy] apply local-preference 200       # 其余 LP 200（主用）

[Router] route-policy RP-IN-B permit node 10
[Router-route-policy] if-match ip-prefix PL-ISP-B
[Router-route-policy] apply local-preference 300
[Router] route-policy RP-IN-B permit node 20
[Router-route-policy] apply local-preference 100       # 低于 A，作为备份

# ===== 出方向策略（控制"进来"的流量）=====
[Router] route-policy RP-OUT-A permit node 10
[Router-route-policy] apply med 100                    # MED 低，优先
[Router] route-policy RP-OUT-B permit node 10
[Router-route-policy] apply med 200                    # MED 高，备份
[Router-route-policy] apply as-path 65001 65001 additive   # 追加 AS_Path 更保险

# ===== 应用 =====
[Router-bgp-af-ipv4] peer 100.1.1.1 route-policy RP-IN-A import
[Router-bgp-af-ipv4] peer 100.1.1.1 route-policy RP-OUT-A export
[Router-bgp-af-ipv4] peer 200.1.1.1 route-policy RP-IN-B import
[Router-bgp-af-ipv4] peer 200.1.1.1 route-policy RP-OUT-B export
```

### 8_7.3 验证
```latex
[Router] display bgp routing-table                  # 看 *> 标记的优选路由
[Router] display bgp routing-table 100.100.1.0      # 看某条路由的属性（LP/MED/AS_Path）
[Router] display bgp peer                           # Established
[Router] display ip routing-table protocol bgp      # 进路由表了没
```

> **验证要点**：`display bgp routing-table` 中带 `*` 表示有效（下一跳可达），带 `>` 表示优选。**只有 **`>`** 的才会进 IP 路由表、才会转发**——看到 `*` 没有 `>` 就要查下一跳。

---

## 8_8 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 原因 | 定位/处理 |
| --- | --- | --- |
| **BGP 邻居 Idle** | 无去往 peer 的路由（最常见） | `display ip routing-table peer地址`；补 IGP/静态 |
| 邻居 Active | TCP 不通 / TTL 不够 / 对端未配 | `display bgp peer`；非直连要 `ebgp-max-hop` |
| 邻居 Established 但无路由 | 没 network / 没 import / 地址族未 enable | `display bgp peer verbose`（看地址族） |
| 学到路由但不可用（无 `>`） | **下一跳不可达**（IBGP 未配 next-hop-local） | `peer x.x.x.x next-hop-local` |
| 路由发了但对端收不到 | 出方向 route-policy 过滤 / 末尾隐含 deny | 检查 route-policy 节点 |
| 发了路由但掩码对不上 | BGP network 要求**精确匹配**路由表 | 补一条精确路由或聚合 |
| 选路不符合预期 | LP/MED/AS_Path 优先级理解有误 | 按顺序逐步 `display bgp routing-table x.x.x.x` |
| Peer 卡 Active | TCP 建不起来 | `display tcp status`（看 179 端口连接状态） |
| 路由震荡 | 链路或接口不稳定 | `display bgp routing-table flap-info`（衰减统计） |
| 策略没生效 | 节点未命中 / 未应用 | `display route-policy` + `display ip ip-prefix` |
| 路由反射后部分设备收不到 | RR 未配 reflect-client / Cluster 冲突 | `display bgp peer verbose` |
| 汇总后产生环路 | 缺 NULL0 黑洞路由 | 补 `ip route-static x.x.x.x NULL 0` |

---

## 8_9 场景笔记与验证
### 8_9.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **选路 11 步口诀卡** | "一私二本三始发，四短五源六 MED，七类八近九簇十 ID 十一 IP" |
| **属性方向卡** | Local_Pref 控制出 AS（入方向改），MED 控制入 AS（出方向改） |
| **策略三件套模板** | ip-prefix 定义 → route-policy 匹配+改属性 → peer 上应用（别忘了 permit 空节点） |
| **坑本** | IBGP 漏 next-hop-local；route-policy 末尾隐含 deny；network 掩码不精确；非直连 EBGP 忘 ebgp-max-hop |

### 8_9.2 验证三板斧（本板块版）
```latex
第1步 看状态：display bgp peer（Established？）
第2步 看表项：display bgp routing-table（有没有 * 和 >）、display bgp routing-table x.x.x.x（属性对不对）
第3步 打流量：ping -a 源 目的 + tracert（实际走哪条路，验证策略是否生效）
```

**加一刀**：`display ip routing-table protocol bgp` ——BGP 表里有不等于进了全局路由表，只有最优路由才会下发。

### 8_9.3 值得做的策略实验
搭一个双出口拓扑，然后依次验证：

1. 只改 LP，看出方向流量切换；
2. 只改 MED，看入方向（用对端的 `display bgp routing-table` 观察）；
3. 用 AS_Path Prepend 再验证一次，对比三者的生效范围。

**做完这三步，论述题里"如何控制出入流量"就有自己的话可说了。**

---

## 8_10 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | IS-IS 区域也按接口划分 | IS-IS **按路由器**划分，一台设备整体属于一个区域 |
| 2 | BGP 也会算最短路径 | BGP **不算路**，只按属性做策略选路 |
| 3 | IBGP 不需要 next-hop-local | **必配**，否则下一跳不可达，路由不可用 |
| 4 | network 能发布任意网段 | 必须**精确存在于路由表**（掩码完全匹配） |
| 5 | route-policy 不匹配就放行 | **末尾隐含 deny all**，必须补 permit 节点 |
| 6 | Local_Pref 控制入方向 | LP 控制**出 AS**；MED 控制**入 AS**（方向别搞反） |
| 7 | MED 全网通用 | 默认**只在来自同一 AS 的路由之间比较** |
| 8 | RR 会改变 AS_Path | RR 不改变 AS_Path，用 **Cluster_List/Originator_ID** 防环 |
| 9 | 非直连 EBGP 直连建邻就行 | 默认 TTL=1，需 `ebgp-max-hop` |
| 10 | 汇总路由不需要配套措施 | 必须配 **NULL0 黑洞路由**防环 |

---

# 板块9 · MPLS、MPLS L3VPN 与 EVPN
> 定位：承载网与大型企业专线的核心技术，HCIE 笔试承载网模块占 15%、实验占 25%。也是 HCIE-Datacom 里"最抽象但最有规律"的一块——把标签转发过程想通了，配置就是固定套路。
> 学习路线：**MPLS 基本概念 → LDP 标签分发 → 单域 L3VPN → 跨域 Option A/B/C → EVPN**。

## 9_1 MPLS 基础
### 9_1.1 为什么需要 MPLS
| 传统 IP 转发的问题 | MPLS 的解决 |
| --- | --- |
| 每跳都要查路由表（最长匹配，慢） | **标签交换**（精确匹配，快） |
| 无法做流量工程（只能走 IGP 最短路径） | 可指定显式路径（MPLS TE） |
| 无法实现地址重叠的 VPN | **VPN 实例隔离**（地址可重叠） |
| QoS 与业务绑定困难 | 标签可携带 EXP（QoS）信息 |

### 9_1.2 核心概念
| 术语 | 含义 |
| --- | --- |
| **LSR** | 标签交换路由器（运行 MPLS 的路由器） |
| **LER** | 边缘 LSR，负责**压入（Push）**和**弹出（Pop）**标签 |
| **LSP** | 标签交换路径（单向！双向通信需要两条 LSP） |
| **FEC** | 转发等价类（具有相同转发处理方式的一组报文） |
| **Label** | 20 bit 标签，范围 0–2^20-1 |
| **Ingress / Transit / Egress** | LSP 的入口 / 中间 / 出口 |

### 9_1.3 标签结构（32 bit）
```latex
┌───────────────┬─────────┬───┬─────────┐
│  Label 20bit  │ EXP 3bit│S 1│ TTL 8bit│
└───────────────┴─────────┴───┴─────────┘
    标签值        QoS     栈底  防环
```

+ **S（Bottom of Stack）**：1 = 栈底（VPN 场景会有两层标签）；
+ **EXP**：用于 QoS（现称 TC）；
+ **特殊标签**：
    - `0`：IPv4 显式空标签（Explicit NULL）——**保留 EXP 用于 QoS**
    - `3`：隐式空标签（Implicit NULL）——**倒数第二跳弹出 PHP**
    - `1`：Router Alert；`2`：IPv6 显式空标签

### 9_1.4 标签操作三动作
```latex
Push（压入）：Ingress 收到 IP 报文，查 FIB 发现有标签 → 压入标签
Swap（交换）：Transit 收到标签报文，查 LFIB → 用出标签替换入标签
Pop （弹出）：Egress（或倒数第二跳）移除标签，还原 IP 报文
```

### 9_1.5 PHP（倒数第二跳弹出）
**为什么需要**：如果让 Egress 自己弹出标签，它要先查标签表再查 IP 路由表，两次查表。让倒数第二跳（P 路由器）直接弹出（用隐式空标签 3 通知），Egress 收到的是纯 IP 报文，直接查 IP 路由表即可，**省一次查表**。

```latex
Ingress ────── P ────── Egress
  压入标签100      收到3号标签→弹出      收到纯IP报文
  发送[100|IP]  →  发送[IP]         →  查IP路由表
```

---

## 9_2 MPLS 与 LDP 配置
### 9_2.1 基本配置骨架
```latex
# ============ 全局：配置 LSR ID 与使能 MPLS/LDP ============
[Router] mpls lsr-id 1.1.1.1                 # ★ 必须是真实存在且路由可达的 Loopback 地址
[Router] mpls
[Router-mpls] quit
[Router] mpls ldp
[Router-mpls-ldp] quit

# ============ 接口：使能 MPLS 与 LDP ============
[Router] interface gigabitethernet 0/0/1
[Router-GigabitEthernet0/0/1] ip address 10.0.12.1 30
[Router-GigabitEthernet0/0/1] mpls
[Router-GigabitEthernet0/0/1] mpls ldp

[Router] interface loopback 0
[Router-LoopBack0] ip address 1.1.1.1 32
```

> ⚠️ **LSR ID 配置后不能随便改**，修改需 `undo mpls` 全部重来。它必须是设备上一个**已配置且路由可达**的地址（通常用 Loopback0）。

### 9_2.2 LDP 会话与标签分发
```latex
第1步 邻居发现：UDP 646 组播 Hello（224.0.0.2）
第2步 建立 TCP 会话（646），传输地址大的一方为主动方
第3步 会话建立（Initialization + KeepAlive）
第4步 标签分发：下游为上游的 FEC 分配标签（DU 下游自主方式，华为默认）
```

验证：

```latex
[Router] display mpls ldp session                  # LDP 会话（应为 Operational）
[Router] display mpls ldp peer
[Router] display mpls lsp                          # 标签转发表
[Router] display mpls lsp verbose
[Router] display mpls interface                    # 使能 MPLS 的接口
[Router] display fib 2.2.2.2                       # 查看 FIB（是否有 Tunnel ID）
```

### 9_2.3 静态 LSP（无需 LDP，小规模场景）
```latex
# Ingress
[Ingress] static-lsp ingress LSP-A destination 3.3.3.3 32 nexthop 10.0.12.2 out-label 100

# Transit
[Transit] static-lsp transit LSP-A incoming-interface g0/0/0 in-label 100 nexthop 10.0.23.3 out-label 200

# Egress
[Egress] static-lsp egress LSP-A incoming-interface g0/0/1 in-label 200
```

### 9_2.4 MPLS 排错与 MTU 陷阱
| 现象 | 原因 | 处理 |
| --- | --- | --- |
| LDP 会话起不来 | LSR ID 不可达 / 未路由可达 | 用 IGP 通告 Loopback |
| 会话 Down | 传输地址不可达 | 检查 IGP 是否通告接口网段 |
| 有会话但无 LSP | 接口未 `mpls ldp` | 逐接口检查 |
| LSP 不完整 | 中间节点未使能 MPLS | 逐跳 `display mpls interface` |
| 能建 LSP 但不通 | **MTU 不够**（标签增加 4 字节） | 增大 MPLS MTU |

> **MTU 陷阱**：MPLS 每加一层标签增加 4 字节，VPN 场景加 8 字节。若接口 MTU 为 1500，加标签后 1508 会被丢弃。解决：`mpls mtu 1508` 或把接口 MTU 调大到 1530/9000。

---

## 9_3 MPLS L3VPN
### 9_3.1 三大角色
| 角色 | 全称 | 职责 |
| --- | --- | --- |
| **CE** | Customer Edge | 用户侧设备，**不感知 VPN**，与 PE 跑普通路由 |
| **PE** | Provider Edge | 运营商边缘，**维护 VPN 实例、打两层标签** |
| **P** | Provider | 运营商核心，**只做标签交换，不感知 VPN 路由** |

### 9_3.2 地址重叠问题与 RD/RT
+ **RD（Route Distinguisher）**：64 bit，加在 IPv4 地址前构成 **VPNv4 地址（96 bit）**，解决**地址重叠**（不同客户用同样网段）；
+ **RT（Route Target）**：BGP 扩展团体属性，控制**路由导入导出**（决定哪些站点能互通）。

```latex
RD: 100:1（格式 AS:NN 或 IP:NN）
VPNv4 地址 = RD(8字节) + IPv4(4字节)

RT 导入导出规则：
  本端 Export RT = 对端 Import RT  →  路由可被学习（互通成立）
```

**VPN 拓扑控制三例：**

| 需求 | RT 设计 |
| --- | --- |
| 全互通（Full Mesh） | 所有站点 Export 100:1，Import 100:1 |
| 完全隔离 | 各站点 Export/Import 各自独立 RT |
| Hub-Spoke（分支只能与总部互通） | 分支 Export 200:1 / Import 100:1；总部 Export 100:1 / Import 200:1 |

### 9_3.3 两层标签
```latex
PE1 发出的报文：[ 外层标签(LDP) | 内层标签(MP-BGP 分配) | IP 报文 ]
                 ↑ 用于到达 PE2    ↑ 用于标识属于哪个 VPN 实例

P 路由器： 只 swap 外层标签
PE2：      外层已在倒数第二跳弹出 → 收到 [内层标签 | IP] → 按内层标签查 VPN 实例转发表
```

> **记住这条规律：外层走 tunnel（到对端 PE），内层分 VPN（到哪个客户的哪个口）。**

### 9_3.4 完整配置（单域 L3VPN）
拓扑：

```latex
   CE1 ── PE1 ── P ── PE2 ── CE2
  (Site A)              (Site B)
```

**Step 1：运营商骨干 IGP（OSPF 示例）**

```latex
[PE1] ospf 1 router-id 1.1.1.1
[PE1-ospf-1] area 0
[PE1-ospf-1-area-0.0.0.0] network 1.1.1.1 0.0.0.0
[PE1-ospf-1-area-0.0.0.0] network 10.0.12.0 0.0.0.3
```

**Step 2：MPLS + LDP**（见 9_2.1，三台设备都配）

**Step 3：PE 上创建 VPN 实例**

```latex
[PE1] ip vpn-instance VPN-A
[PE1-vpn-instance-VPN-A] route-distinguisher 100:1
[PE1-vpn-instance-VPN-A] vpn-target 100:1 export-extcommunity
[PE1-vpn-instance-VPN-A] vpn-target 100:1 import-extcommunity
```

**Step 4：PE 与 CE 互联接口绑定 VPN 实例**

```latex
[PE1] interface gigabitethernet 0/0/1
[PE1-GigabitEthernet0/0/1] ip binding vpn-instance VPN-A
[PE1-GigabitEthernet0/0/1] ip address 10.1.1.1 30       # ★ 绑定后需重配 IP
```

> ⚠️ **接口绑定 VPN 实例后会清空原 IP 配置**，必须重新配地址。这是实验中最常见的"明明配了却不通"。

**Step 5：PE-CE 之间的路由（三种方式）**

```latex
# 方式一：静态（简单）
[PE1] ip route-static vpn-instance VPN-A 172.16.1.0 24 10.1.1.2

# 方式二：OSPF（PE 上的 OSPF 进程需绑定 VPN 实例）
[PE1] ospf 2 vpn-instance VPN-A
[PE1-ospf-2] area 0
[PE1-ospf-2-area-0.0.0.0] network 10.1.1.0 0.0.0.3

# 方式三：EBGP
[PE1] bgp 100
[PE1-bgp] ipv4-family vpn-instance VPN-A
[PE1-bgp-VPN-A] peer 10.1.1.2 as-number 65001
```

**Step 6：PE 之间 MP-BGP（传 VPNv4 路由）**

```latex
[PE1] bgp 100
[PE1-bgp] peer 3.3.3.3 as-number 100                    # 对端 PE 的 Loopback
[PE1-bgp] peer 3.3.3.3 connect-interface LoopBack 0
[PE1-bgp] ipv4-family vpnv4
[PE1-bgp-af-vpnv4] peer 3.3.3.3 enable

# 把 VPN 实例里的路由引入 BGP（静态场景）
[PE1-bgp] ipv4-family vpn-instance VPN-A
[PE1-bgp-VPN-A] network 172.16.1.0 24

# OSPF 场景（BGP 与 OSPF 互引）
[PE1-bgp-VPN-A] import-route ospf 2
[PE1-ospf-2] import-route bgp
```

### 9_3.5 验证命令（逐层排查的黄金顺序）
```latex
第1步 display mpls ldp session                              # LDP 会话 Operational？
第2步 display bgp vpnv4 all peer                            # MP-BGP Established？
第3步 display bgp vpnv4 vpn-instance VPN-A routing-table    # 学到对端私网路由没？
第4步 display ip routing-table vpn-instance VPN-A           # 进 VPN 路由表没？
第5步 ping -vpn-instance VPN-A 172.16.2.1                   # ★ 必须带 -vpn-instance
```

> ★ **第 第5步 步是最经典的错误**：直接 `ping 172.16.2.1` 会在公网路由表里查，必然失败。**PE 上 ping 私网必须带 **`-vpn-instance`**。**

### 9_3.6 L3VPN 排错表
| 现象 | 原因 | 处理 |
| --- | --- | --- |
| LDP 会话起不来 | LSR ID 不可达 | IGP 通告 Loopback |
| MP-BGP 邻居起不来 | vpnv4 地址族未 enable / 无路由 | 检查 `peer x.x.x.x enable` |
| 有邻居但学不到 VPN 路由 | **RT 不匹配** | 检查两端 export/import RT |
| 学到了路由但不通 | ping 没带 `-vpn-instance` | 加上参数 |
| 接口 IP 配不上 | 绑定 VPN 实例后 IP 被清 | 重新配 IP |
| 有路由但转发丢包 | MTU（两层标签 8 字节） | 调大 MPLS MTU |
| 学到路由但下一跳不可达 | 骨干网 LSP 不完整 | `display mpls lsp` 逐跳查 |

### 9_3.7 OSPF 与 BGP 互引的 Sham Link 问题
**场景**：客户两个站点之间除了 MPLS 专线，还有一条**后门链路（backdoor）**。PE-CE 跑 OSPF 时，经 MPLS 传过去的路由在 CE 看来是 **Type 3（区域间）**，而后门链路学到的是 **Type 1/2（区域内）** → **OSPF 优先走区域内路由**，流量全走后门，专线白买。

**解法**：在两台 PE 之间建立 **Sham Link**（伪连接），让经 MPLS 传递的路由以 Type 1（区域内）形式出现：

```latex
[PE1] ospf 2 vpn-instance VPN-A
[PE1-ospf-2] area 0
[PE1-ospf-2-area-0.0.0.0] sham-link 1.1.1.1 3.3.3.3     # 源/目为两端 PE 的 Loopback
```

> Sham Link 是 HCIE 高频论述/排考点：**当客户有后门链路且要求走 MPLS 主路时，必须配 sham-link**（或用 route-policy 调开销）。

---

## 9_4 跨域 VPN（Inter-AS）
### 9_4.1 三种方案对比
| 方案 | 做法 | 优点 | 缺点 | 适用 |
| --- | --- | --- | --- | --- |
| **Option A** | ASBR 之间每个 VPN 一个子接口，像 PE-CE 一样对接 | 简单、隔离性好 | 每个 VPN 一个接口，**扩展性差** | VPN 数量少 |
| **Option B** | ASBR 之间用 MP-EBGP 传 VPNv4 路由 | 一条链路承载所有 VPN | ASBR 要维护 VPNv4 路由，压力大 | 中等规模 |
| **Option C** | PE 之间直接建多跳 MP-EBGP，ASBR 只传带标签路由 | 扩展性最好 | 配置复杂 | 大规模跨域 |

### 9_4.2 Option A 关键配置
```latex
# ASBR1 上为每个 VPN 建一个子接口，绑定 VPN 实例，像 PE-CE 一样对接
[ASBR1] interface gigabitethernet 0/0/1.10
[ASBR1-GigabitEthernet0/0/1.10] ip binding vpn-instance VPN-A
[ASBR1-GigabitEthernet0/0/1.10] ip address 10.100.1.1 30

# 与对端 ASBR 跑 EBGP（在 VPN 实例地址族下）
[ASBR1-bgp] ipv4-family vpn-instance VPN-A
[ASBR1-bgp-VPN-A] peer 10.100.1.2 as-number 200
```

### 9_4.3 Option B 关键配置
```latex
# 关键：ASBR 需要为 EBGP 下一跳分配标签（标签路由能力）
[ASBR1-bgp] ipv4-family vpnv4
[ASBR1-bgp-af-vpnv4] peer 10.100.1.2 enable
[ASBR1-bgp-af-vpnv4] peer 10.100.1.2 label-route-capability
[ASBR1] interface gigabitethernet 0/0/1
[ASBR1-GigabitEthernet0/0/1] mpls
```

---

## 9_5 EVPN（Ethernet VPN）
### 9_5.1 为什么需要 EVPN
传统 VPN 的问题：

| 传统方案 | 局限 |
| --- | --- |
| MPLS L3VPN | 只能传三层路由，无法承载二层 MAC 学习 |
| VPLS | 靠数据面泛洪学 MAC，广播多、收敛慢、无法做多活 |
| 裸纤/VLL | 点对点，无法多点互联 |

EVPN 的思路：**用 BGP 做控制面来通告 MAC/IP 路由**，把"二层可达信息"当作路由来传递——既支持二层互通，也支持三层互通，还能做多活和快速收敛。

### 9_5.2 EVPN 路由类型
| 类型 | 名称 | 作用 |
| --- | --- | --- |
| **Type 1** | Ethernet Auto-Discovery | 以太自动发现（多活场景，防环路、快速收敛） |
| **Type 2** | MAC/IP Advertisement | **通告主机 MAC、IP、所在 VNI（核心）** |
| **Type 3** | Inclusive Multicast | 通告 VTEP 属于哪个 VNI → 自动建 BUM 隧道 |
| **Type 4** | Ethernet Segment | 以太段路由（多活场景下 DF 选举） |
| **Type 5** | IP Prefix | 通告外部 IP 前缀（与外部网络互通） |

### 9_5.3 EVPN 配置骨架（BGP EVPN 地址族）
```latex
[PE] bgp 100
[PE-bgp] peer 3.3.3.3 as-number 100
[PE-bgp] peer 3.3.3.3 connect-interface LoopBack 0
[PE-bgp] l2vpn-family evpn
[PE-bgp-af-evpn] peer 3.3.3.3 enable
[PE-bgp-af-evpn] undo policy vpn-target        # ★ RR 场景必配：不对 RT 做过滤，否则路由被丢弃

[PE] display bgp evpn all routing-table
```

> ⚠️ `undo policy vpn-target`** 是 EVPN RR 的经典坑**：BGP EVPN 默认按 RT 过滤路由，而路由反射器自身往往没有配置对应的 VPN 实例（即没有 RT），结果收到的路由全被丢掉。作为 RR 时务必关掉这个过滤。

---

## 9_6 综合实验：企业 MPLS L3VPN 专线
### 9_6.1 需求
```latex
两个客户（VPN-A 与 VPN-B）通过同一张 MPLS 骨干网互联：
第1步 VPN-A 的 Site1（172.16.1.0/24）与 Site2（172.16.2.0/24）互通
第2步 VPN-B 的 Site1（192.168.1.0/24）与 Site2（192.168.2.0/24）互通
第3步 两个 VPN 之间完全隔离
第4步 允许两个 VPN 使用重叠地址（验证 RD 的作用）
```

### 9_6.2 关键配置汇总
```latex
# ============ VPN 实例（两个客户，RT 不同即可隔离）============
[PE1] ip vpn-instance VPN-A
[PE1-vpn-instance-VPN-A] route-distinguisher 100:1
[PE1-vpn-instance-VPN-A] vpn-target 100:1 both
[PE1] ip vpn-instance VPN-B
[PE1-vpn-instance-VPN-B] route-distinguisher 100:2
[PE1-vpn-instance-VPN-B] vpn-target 100:2 both

# ============ CE 接口绑定 ============
[PE1] interface gigabitethernet 0/0/1
[PE1-GigabitEthernet0/0/1] ip binding vpn-instance VPN-A
[PE1-GigabitEthernet0/0/1] ip address 10.1.1.1 30

# ============ PE-CE EBGP ============
[PE1-bgp] ipv4-family vpn-instance VPN-A
[PE1-bgp-VPN-A] peer 10.1.1.2 as-number 65001

# ============ PE 之间 MP-BGP ============
[PE1-bgp] ipv4-family vpnv4
[PE1-bgp-af-vpnv4] peer 3.3.3.3 enable
```

### 9_6.3 验收步骤
```latex
# PE 侧
[PE1] display mpls ldp session                            # Operational
[PE1] display bgp vpnv4 all peer                          # Established
[PE1] display bgp vpnv4 vpn-instance VPN-A routing-table  # 有对端私网路由
[PE1] ping -vpn-instance VPN-A 172.16.2.1                 # 通

# CE 侧
[CE1] ping 172.16.2.1                                     # 通
# 隔离验证：VPN-A 的 CE 应 ping 不通 VPN-B 的网段
[CE1] ping 192.168.2.1                                    # 不通（符合预期）
```

---

### 9_6.5 案例：两个客户都叫 192.168.1.0，怎么和平共处
> 某运营商给两家连锁客户开 MPLS 专线，巧合的是两家内网都用了 `192.168.1.0/24`。放在传统路由网络里，这根本没法做——路由表会打架，A 客户的流量会窜到 B 客户那边去。
> 工程师一开始想让客户改地址，被客户一口回绝："门店几百台设备，改地址等于停业一周。"
> 最后用 MPLS L3VPN 解决，三步：  
第1步 两家各建一个 VPN 实例，配不同的 **RD**（A 用 100:1，B 用 200:1）——地址重叠问题就此解决，VPNv4 地址 = RD + IPv4，全局唯一；  
第2步 配 **RT** 控制互通：A 的 Export RT = A 的 Import RT，B 同理，**两边互不匹配**——隔离达成；  
第3步 PE 与 CE 之间跑 EBGP，把客户路由收进各自的实例路由表。
> 验收时最关键的一步是**反向验证**：在 A 客户的 CE 上 `ping` B 客户的网段，必须**不通**。很多人只测"通"，忘了测"不通"——而 VPN 业务里，"该不通的不通"和"该通的通"同样重要。
> 半年后总部要统一看两家的监控数据，只改了一行：在总部站点同时 Import 两家的 RT。**业务拓扑的调整，最后是靠 RT 的加减法完成的**，这就是 MPLS VPN 最值钱的地方。

## 9_7 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 第一刀 | 第二刀 |
| --- | --- | --- |
| LDP 会话起不来 | `display mpls ldp session` | `ping -a 1.1.1.1 3.3.3.3`（LSR ID 可达？） |
| LSP 不完整 | `display mpls lsp` | `display mpls interface`（逐跳看使能） |
| MP-BGP 起不来 | `display bgp vpnv4 all peer` | 检查 vpnv4 地址族是否 enable |
| 学不到 VPN 路由 | `display bgp vpnv4 vpn-instance X routing-table` | 检查 **RT 是否匹配** |
| 有路由 ping 不通 | `ping -vpn-instance X 目的` | 检查接口是否绑定 VPN 实例、IP 是否重配 |
| 大包不通 | `ping -s 1500 -vpn-instance X 目的` | 调 MPLS MTU |
| 流量走后门链路 | `display ospf routing`（看 LSA 类型） | 配 **sham-link** |

---

## 9_8 场景笔记与验证
### 9_8.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **标签转发图** | 画一遍 PE1→P→PE2 的标签变化（外层 swap、内层不变、PHP） |
| **RT 互通判据** | 本端 Export = 对端 Import 才互通（Hub-Spoke 怎么配） |
| **五步验证顺序卡** | LDP 会话 → MP-BGP → VPNv4 路由 → VPN 路由表 → 带实例 ping |
| **坑本** | 绑定 VPN 实例后 IP 被清；ping 忘带 -vpn-instance；RT 不匹配；MTU 少 8 字节 |

### 9_8.2 验证三板斧（本板块版）
```latex
第1步 看状态：display mpls ldp session / display bgp vpnv4 all peer
第2步 看表项：display mpls lsp（标签表）、display bgp vpnv4 vpn-instance X routing-table
第3步 打流量：ping -vpn-instance VPN-A 172.16.2.1  ← ★ 考试最容易忘的参数
```

### 9_8.3 值得做一次的标签观察实验
在 eNSP 里搭三台路由器跑 MPLS，然后在 P 与 PE2 之间的链路**抓包**，看以太网帧里的标签字段：

+ Ingress 侧：能看到 `[Label|IP]`；
+ PHP 之后（倒数第二跳弹出）：抓到的已经是纯 IP 包。

**亲眼看过标签，MPLS 就不再抽象。**

---

## 9_9 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | LSP 是双向的 | **单向**，双向通信需要两条 LSP |
| 2 | Egress 自己弹标签 | 倒数第二跳弹出（PHP，隐式空标签 3） |
| 3 | RD 控制互通 | **RD 解决地址重叠**，**RT 控制互通** |
| 4 | 接口绑定 VPN 实例不影响 IP | 会**清空原 IP**，必须重配 |
| 5 | PE 上 ping 私网直接 ping | 必须 `ping -vpn-instance X` |
| 6 | 两层标签作用相同 | 外层到对端 PE，内层标识 VPN 实例 |
| 7 | MTU 不用管 | 每标签 +4 字节，VPN 场景 +8，需调 MPLS MTU |
| 8 | 后门链路问题不用管 | 走后门是 OSPF 选路规则决定的，需 **sham-link** |
| 9 | 跨域 Option A 最常用 | A 最简单但扩展性最差；大规模用 B/C |
| 10 | EVPN 只是 VXLAN 的控制面 | EVPN 是**通用控制面**，同时服务 VXLAN 与 MPLS 两种数据面 |

---

# 板块10 · VXLAN 与园区网络虚拟化
> 定位：HCIE-Datacom 园区模块的核心（笔试 23%、实验 20%）。VXLAN 把"大二层"从数据中心带到了园区网，配合 BGP EVPN 实现"一张网承载多业务、用户位置无关"。
> 先理解一个根本转变：**传统园区靠 VLAN 隔离业务、靠 VLANIF 做网关；VXLAN 园区靠 VNI 隔离业务、靠 BD（Bridge Domain）做二层域、靠 Anycast Gateway 做分布式网关。**

## 10_1 VXLAN 基础
### 10_1.1 为什么需要 VXLAN
| 传统 VLAN 的问题 | VXLAN 的解决 |
| --- | --- |
| VLAN ID 只有 4094 个 | VNI 有 **2^24（1600 万+）** |
| 二层域受物理位置限制（不能跨三层） | **Overlay 隧道**，跨三层建二层 |
| STP 阻塞链路，带宽浪费 | Underlay 全三层转发，无 STP |
| 虚拟机迁移要求同二层域，受限 | 迁移后 IP/MAC 不变，位置无关 |
| 园区多业务隔离难 | 一网多用（业务随行） |

### 10_1.2 VXLAN 报文封装
```latex
┌──────────────────────────────────────────────────────────┐
│ 外层以太头 │ 外层IP头 │ UDP头 │ VXLAN头 │ 原始以太帧 │ FCS │
└───────────┴──────────┴───────┴─────────┴────────────┴────┘
                         目的端口 4789   VNI 24bit
                         （源端口哈希，用于 ECMP 负载分担）
```

| 字段 | 说明 |
| --- | --- |
| 外层 IP | VTEP 的 IP（Underlay 可达） |
| UDP 目的端口 | **4789**（IANA 标准；早期部分实现用 8472） |
| UDP 源端口 | 由内层报文哈希生成 → **保证 ECMP 负载分担** |
| VXLAN 头 | 8 字节，含 24 bit **VNI** 与标志位 |
| 原始帧 | 完整的二层帧（含 VLAN Tag，可选） |

> **MTU 提醒**：VXLAN 封装增加约 50 字节（外层以太 14 + 外层 IP 20 + UDP 8 + VXLAN 8）。Underlay 网络 MTU 建议 ≥1550，或设置 **MTU 9000（巨帧）**，否则大包被丢弃。

### 10_1.3 关键组件
| 术语 | 全称 | 作用 |
| --- | --- | --- |
| **VTEP** | VXLAN Tunnel End Point | VXLAN 隧道端点，负责封装/解封装 |
| **VNI** | VXLAN Network Identifier | 24 bit 网络标识（类似 VLAN ID） |
| **BD** | Bridge Domain | 二层广播域，**VNI 与 BD 一一对应（1:1 绑定）** |
| **VAP** | Virtual Access Point | 虚拟接入点，把业务流量引入 BD |
| **NVE** | Network Virtualization Edge | 逻辑接口（通常是 `Nve 1`），隧道的载体 |
| **Underlay** | 底层 IP 网络 | 跑 IGP（OSPF/IS-IS）+ BGP，提供 VTEP 可达 |
| **Overlay** | 叠加网络 | VXLAN 隧道 |

### 10_1.4 网关部署方式
| 方式 | 位置 | 优点 | 缺点 | 适用 |
| --- | --- | --- | --- | --- |
| **集中式网关** | 网关在 Spine/Core（一台设备） | 配置简单、策略集中 | **流量绕行**、单点风险 | 小规模、南北向流量为主 |
| **分布式网关**（推荐） | 网关在每个 Leaf（VBDIF） | **最优转发路径**、无绕行 | 配置复杂 | 数据中心/园区主流 |

**分布式网关的关键：Anycast Gateway** —— 所有 Leaf 上的网关 IP 和 MAC **完全相同**，主机无论迁移到哪台 Leaf，网关都不变，无需重新获取 ARP。

---

## 10_2 VXLAN 静态隧道（手工方式）
适合小规模或理解原理，无需 BGP EVPN。

### 10_2.1 配置流程
```latex
第1步 创建 BD 并绑定 VNI
第2步 创建 VAP（子接口或 VLAN 方式）把业务流量引入 BD
第3步 创建 NVE 接口，指定源 VTEP IP
第4步 配置头端复制列表（peer-list）
```

### 10_2.2 完整配置（两台 Leaf 建立 VXLAN 隧道）
```latex
# ================= LEAF1 =================
[LEAF1] bridge-domain 10
[LEAF1-bd10] vxlan vni 10                              # BD 与 VNI 绑定
[LEAF1-bd10] quit

# 业务接入（子接口方式，dot1q 终结）
[LEAF1] interface gigabitethernet 0/0/1.10 mode l2
[LEAF1-GigabitEthernet0/0/1.10] encapsulation dot1q vid 10
[LEAF1-GigabitEthernet0/0/1.10] bridge-domain 10
[LEAF1-GigabitEthernet0/0/1.10] quit

# 或用 VLAN 方式（更简单）
[LEAF1] vlan 10
[LEAF1] bridge-domain 10
[LEAF1-bd10] l2 binding vlan 10

# NVE 接口与头端复制
[LEAF1] interface Nve 1
[LEAF1-Nve1] source 1.1.1.1                            # 源 VTEP IP（Loopback）
[LEAF1-Nve1] vni 10 head-end peer-list 2.2.2.2         # 指定远端 VTEP

# ================= LEAF2（镜像配置）=================
[LEAF2] bridge-domain 10
[LEAF2-bd10] vxlan vni 10
[LEAF2-bd10] l2 binding vlan 10
[LEAF2] interface Nve 1
[LEAF2-Nve1] source 2.2.2.2
[LEAF2-Nve1] vni 10 head-end peer-list 1.1.1.1
```

### 10_2.3 验证
```latex
[LEAF1] display vxlan vni                    # VNI 与 BD 映射
[LEAF1] display vxlan tunnel                 # 隧道状态（应为 up）
[LEAF1] display bridge-domain                 # BD 信息
[LEAF1] display vxlan peer                    # 远端 VTEP 列表
[LEAF1] display mac-address bridge-domain 10  # BD 内的 MAC 表
```

> **静态方式的局限**：每次新增 Leaf 都要在所有 Leaf 上改 peer-list，规模一大就不可维护。生产环境一律用 **BGP EVPN** 自动发现。

---

## 10_3 VXLAN + BGP EVPN（生产标准）
### 10_3.1 为什么需要 EVPN 做控制面
| 静态 VXLAN | BGP EVPN |
| --- | --- |
| 隧道需手工指定 peer | **自动发现 VTEP**，新增设备自动建立隧道 |
| MAC 靠数据面泛洪学习 | **控制面通告 MAC/IP**（Type 2 路由） |
| BUM 流量靠头端复制（手工） | **自动建立 BUM 隧道**（Type 3 路由） |
| 无法做 ARP 抑制 | **ARP 抑制**（本地代答，减少广播） |
| 规模受限 | 支持大规模组网 |

### 10_3.2 EVPN 路由类型（VXLAN 场景）
| 类型 | 在 VXLAN 中的作用 |
| --- | --- |
| **Type 2（MAC/IP）** | 通告主机 MAC、IP、所在 VNI（**核心**） |
| **Type 3（Inclusive Multicast）** | 通告 VTEP 属于哪个 VNI → 自动建 BUM 隧道 |
| **Type 5（IP Prefix）** | 通告外部 IP 前缀（用于 VXLAN 与外部网络互通） |

### 10_3.3 集中式网关配置（Spine 做网关）
**Underlay（所有设备跑 IGP，通告 Loopback）：**

```latex
[Spine] ospf 1 router-id 100.1.1.1
[Spine-ospf-1] area 0
[Spine-ospf-1-area-0.0.0.0] network 100.1.1.1 0.0.0.0
[Spine-ospf-1-area-0.0.0.0] network 10.0.11.0 0.0.0.3
```

**BGP EVPN 邻居（Spine 作为 RR，Leaf 作为 Client）：**

```latex
# ============ Spine（RR） ============
[Spine] bgp 100
[Spine-bgp] peer 1.1.1.1 as-number 100
[Spine-bgp] peer 1.1.1.1 connect-interface LoopBack 0
[Spine-bgp] l2vpn-family evpn
[Spine-bgp-af-evpn] peer 1.1.1.1 enable
[Spine-bgp-af-evpn] peer 1.1.1.1 reflect-client          # RR
[Spine-bgp-af-evpn] peer 2.2.2.2 enable
[Spine-bgp-af-evpn] peer 2.2.2.2 reflect-client

# ============ Leaf1（Client） ============
[Leaf1] bgp 100
[Leaf1-bgp] peer 100.1.1.1 as-number 100
[Leaf1-bgp] peer 100.1.1.1 connect-interface LoopBack 0
[Leaf1-bgp] l2vpn-family evpn
[Leaf1-bgp-af-evpn] policy vpn-target
[Leaf1-bgp-af-evpn] peer 100.1.1.1 enable
```

**EVPN 实例与 VXLAN 绑定：**

```latex
[Leaf1] evpn vpn-instance EVPN-10 bd-mode              # bd-mode：绑定到 BD
[Leaf1-evpn-instance-EVPN-10] route-distinguisher 1:10
[Leaf1-evpn-instance-EVPN-10] vpn-target 10:10 export-extcommunity
[Leaf1-evpn-instance-EVPN-10] vpn-target 10:10 import-extcommunity
[Leaf1-evpn-instance-EVPN-10] quit

[Leaf1] bridge-domain 10
[Leaf1-bd10] vxlan vni 10
[Leaf1-bd10] evpn binding vpn-instance EVPN-10         # BD 与 EVPN 实例绑定

[Leaf1] interface Nve 1
[Leaf1-Nve1] source 1.1.1.1
[Leaf1-Nve1] vni 10 head-end peer-list protocol bgp    # ★ 由 BGP 自动发现
```

### 10_3.4 分布式网关（Anycast）配置
```latex
# 所有 Leaf 上配置【相同的】VBDIF 网关 IP 与 MAC
[Leaf1] interface Vbdif 10
[Leaf1-Vbdif10] ip address 192.168.10.254 24
[Leaf1-Vbdif10] mac-address 0000-5e00-0101              # ★ 两端必须一致
[Leaf1-Vbdif10] arp distribute-gateway enable           # ★ 分布式网关（本地代答）
[Leaf1-Vbdif10] vxlan anycast-gateway enable            # ★ Anycast 网关

# Leaf2 上完全相同的配置（IP、MAC 一致）
```

> **分布式网关三件套**：**相同 IP + 相同 MAC + **`arp distribute-gateway enable`。缺一个就出现"主机迁移后不通"或"ARP 代答异常"。

### 10_3.5 三层 VXLAN 网关与外部互通
```latex
# 在 Vbdif 上跑 OSPF/静态，与外部网络互通
[Leaf1] ospf 1
[Leaf1-ospf-1] area 0
[Leaf1-ospf-1-area-0.0.0.0] network 192.168.10.0 0.0.0.255
```

---

## 10_4 三层网关：集中式 vs 分布式（选型必考）
> **本节导读**：网关放哪里，是 VXLAN 方案设计里最关键的一个决定。判断依据只有一条——**流量是不是要绕路**。

| 维度 | 集中式网关 | 分布式网关 |
| --- | --- | --- |
| 网关位置 | Spine/核心一台 | 每台 Leaf（VBDIF） |
| 转发路径 | **次优**（跨 Leaf 流量要绕行到 Spine） | **最优**（本地 Leaf 三层转发） |
| 单点风险 | 有（网关设备故障影响全网） | 无（Anycast，本地即可转发） |
| 配置复杂度 | 低 | 中（三件套 + EVPN 配置） |
| ARP 表项压力 | 集中在网关 | 分散在各 Leaf |
| 适用 | 小规模、南北向流量为主（上网为主） | 数据中心/中大型园区、东西向流量多 |

**集中式网关的两个硬伤（论述题必答）：**

1. **流量绕行**：同网段跨 Leaf 的两台服务器互访，也要把流量送到 Spine 再回来，浪费带宽、增加时延；
2. **单点风险 + 表项瓶颈**：所有终端的 ARP/MAC 表项集中在一台设备上，规模一大就撑不住。

**结论框架**：

```latex
小规模园区 / 南北向为主 / 运维能力有限    → 集中式（简单可控）
中大型园区 / 数据中心 / 东西向流量大       → 分布式（Anycast）
```

---

## 10_5 园区网络虚拟化（CloudCampus）
### 10_5.1 传统园区 vs 虚拟化园区
| 维度 | 传统园区 | 虚拟化园区（CloudCampus） |
| --- | --- | --- |
| 业务隔离 | VLAN + ACL | **VNI + 安全组** |
| 用户策略 | 绑定 VLAN/IP/端口 | **绑定用户身份**（业务随行） |
| 网关 | 核心集中 | 分布式 Anycast |
| 移动性 | 换位置可能换 VLAN | **位置无关**，策略随人走 |
| 运维 | 逐台命令行 | 控制器（iMaster NCE）统一编排 |

### 10_5.2 典型架构
```latex
┌─────────────────────────────────────────┐
│         iMaster NCE（控制器/编排层）       │
│   自动化部署 / 业务编排 / 智能运维          │
└───────────────────┬─────────────────────┘
                    │ NETCONF/YANG、Telemetry
        ┌───────────┴───────────┐
   ┌────┴────┐             ┌────┴────┐
   │  Core   │             │  Core   │   Underlay：OSPF/IS-IS
   └────┬────┘             └────┬────┘   Overlay：VXLAN/BGP EVPN
        └──────────┬────────────┘
              ┌────┴────┐
              │  Leaf   │  VXLAN 接入 + Anycast 网关
              └────┬────┘
              终端（有线/无线/物联）
```

### 10_5.3 业务随行（Free Mobility）
**核心思想**：策略不再绑定 IP/VLAN/端口，而是绑定**用户身份（安全组）**。用户无论走到哪栋楼、哪个端口、用有线还是无线，权限不变。

```latex
传统：用户 → VLAN 10 → IP 段 → ACL（换楼就换 VLAN，策略要重配）
随行：用户 → 安全组（如"研发组"）→ 策略随行（换位置策略不变）
```

**价值**：终端移动频繁、无线占比高的园区，运维工作量大幅下降。

### 10_5.4 用户接入控制（NAC）
VXLAN 园区里，用户接入先认证（802.1X/Portal/MAC），认证通过后由控制器下发**授权结果**（VLAN/VNI、安全组、ACL），实现"认证—授权—策略"闭环（详见板块12）。

---

## 10_6 验证与排错
### 10_6.1 验证命令清单
```latex
[Leaf] display vxlan vni                     # VNI 与 BD 映射
[Leaf] display vxlan tunnel                  # 隧道状态（up？）
[Leaf] display vxlan peer                    # 远端 VTEP 列表
[Leaf] display bgp evpn all routing-table    # EVPN 路由
[Leaf] display bgp evpn routing-table mac    # MAC/IP 路由（Type 2）
[Leaf] display mac-address bridge-domain 10  # BD 内 MAC 表
[Leaf] display arp interface Vbdif 10        # 网关 ARP
[Leaf] display nve 1 interface               # NVE 接口状态
```

### 10_6.2 排错清单
| 现象 | 排查 | 常见根因 |
| --- | --- | --- |
| 隧道起不来 | `display vxlan tunnel`、`ping` VTEP 地址 | Underlay 不可达（IGP 没通告 Loopback） |
| 隧道 up 但业务不通 | `display vxlan vni`（两端 VNI 一致？） | VNI 不一致 |
| 学不到对端 MAC | `display bgp evpn routing-table mac` | **RT 不匹配** / EVPN 实例未绑定 BD |
| EVPN 邻居起不来 | `display bgp evpn peer` | l2vpn-family 未 enable |
| 大包不通小包通 | `ping -s 1500` | **MTU**（VXLAN 开销 50 字节） |
| 分布式网关迁移后不通 | 对比两端 Vbdif 配置 | IP/MAC 不一致或缺 `arp distribute-gateway enable` |
| BUM 流量不通 | `display vxlan peer` | Type 3 路由未学到 / 头端复制列表为空 |

---

## 10_7 方案设计要点（论述题素材）
### 10_7.1 园区网是否上 VXLAN？
```latex
判断依据：
  - 终端规模 >1000、业务多、移动性强 → 引入
  - 有控制器（iMaster NCE）与自动化运维能力 → 引入
  - 小规模固定办公 → 传统 VLAN 方案更经济

引入后的收益：业务随行、位置无关、大二层、策略集中
引入的代价：设备要求高、运维复杂度上升、MTU 需重新规划
```

### 10_7.2 Underlay 设计要点
| 要点 | 建议 |
| --- | --- |
| IGP 选择 | 园区用 OSPF，大型/承载网用 IS-IS |
| 通告范围 | 只需通告 Loopback（VTEP 地址）与互联网段 |
| 可靠性 | 与 BFD 联动，IGP 快速收敛 |
| MTU | 建议全网 9000（巨帧），或至少 ≥1550 |
| 负载分担 | Underlay 全三层，天然 ECMP，无 STP 阻塞 |

### 10_7.3 可靠性设计
```latex
第1步 网关冗余：Anycast 分布式网关（天然多活，无需 VRRP）
第2步 链路冗余：Leaf 双上行 + Underlay ECMP
第3步 设备冗余：Leaf 成对部署（M-LAG 或堆叠，见板块4）
第4步 控制面冗余：双 RR（Spine 双机做 RR）
第5步 逃生机制：控制器故障时，已有转发表项继续生效（本地转发不中断）
```

---

### 10_7.4 案例：虚拟机迁到另一栋楼，业务没断
> 某企业的财务系统跑在 A 楼机房的虚拟机上，某天 A 楼电力改造需要把 VM 迁到 B 楼。传统方案下这是件麻烦事：跨楼 = 跨三层 = IP 网段必须换，换 IP 就要改应用配置、改防火墙策略、改 DNS，财务系统还得停机。
> 上了 VXLAN 之后，这件事变成了一次 **vMotion**：
> + A 楼和 B 楼的 Leaf 都在同一个 VXLAN 网络里，VNI 一致，二层域跨三层打通；
> + VM 迁过去后 **IP、MAC、网关全部不变**，因为网关是 **Anycast Gateway**——B 楼 Leaf 上的 VBDIF 地址和 A 楼完全一样；
> + 迁移过程中 ARP 表项由 BGP EVPN 的 Type 2 路由通告更新，其他 Leaf 几秒内就学到新的位置。
> 业务侧感知：一次 ping 丢包，全程无中断。
> 后来复盘时，运维负责人说了一句话很到位：**"以前我们规划网络是按机房画的，现在按业务画的。"** 这正是 VXLAN 园区网的核心价值——把"用户在哪栋楼"和"用户能访问什么"解耦。

## 10_8 场景笔记与验证
### 10_8.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **封装图** | 画一遍 VXLAN 报文结构，标出 50 字节开销与 4789 端口 |
| **组件映射卡** | BD ↔ VNI（1:1）、VTEP ↔ NVE、VAP 引入业务 |
| **分布式网关三件套** | 相同 IP + 相同 MAC + arp distribute-gateway enable |
| **坑本** | VNI 两端不一致；MTU 没调；EVPN 实例忘了绑定 BD；peer-list protocol bgp 写成静态 |

### 10_8.2 验证三板斧（本板块版）
```latex
第1步 看状态：display vxlan tunnel（up？）、display bgp evpn peer（Established？）
第2步 看表项：display bgp evpn routing-table mac（学到对端主机 MAC 没）
第3步 打流量：同 BD 两台主机互 ping；再用 ping -s 1500 测 MTU
```

### 10_8.3 建议做一次的迁移实验
在分布式网关环境下，把一台主机从 Leaf1 挪到 Leaf2（改接入端口即可），观察：

+ 主机 IP 与网关**不变**；
+ `display mac-address bridge-domain 10` 里 MAC 的位置从 Leaf1 变到 Leaf2；
+ ping 不中断或只丢 1 个包。

**这个实验能让你真正理解"位置无关"四个字的分量。**

---

## 10_9 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | VXLAN 是二层技术 | 它同时支持**二层（L2 VXLAN）与三层（L3 VXLAN 网关）** |
| 2 | VNI 与 VLAN 一一对应 | **VNI 与 BD 一一对应**，BD 再通过 VAP 绑定 VLAN 或子接口 |
| 3 | UDP 端口是 8472 | 标准 **4789** |
| 4 | VXLAN 开销可忽略 | 约 **50 字节**，Underlay MTU 必须调大 |
| 5 | 生产用静态隧道 | 生产用 **BGP EVPN**（自动发现 + ARP 抑制） |
| 6 | 分布式网关只要 IP 相同 | 还要 **MAC 相同** + `arp distribute-gateway enable` |
| 7 | 集中式网关没有缺点 | 有**绕行 + 单点**两个硬伤，论述题常考 |
| 8 | 隧道 up 就等于业务通 | 还要查 VNI 一致、RT 匹配、MTU、MAC 学习 |

---

# 板块11 · ACL、NAT 与流量过滤
> 定位：网络安全的第一道闸门，也是 HCIE 实验里"限制互访""控制出口"的直接手段。HCIA 会写基本 ACL 就够了，HCIP 要求能用高级 ACL 做精细化控制，HCIE 要求能结合安全组、策略路由做整体访问控制设计。
> 一句话原则：**ACL 是自上而下匹配、命中即停、末尾隐含 deny all**。

## 11_1 ACL 基础
### 11_1.1 ACL 分类与编号
| 类型 | 编号范围 | 匹配维度 | 典型用途 |
| --- | --- | --- | --- |
| **基本 ACL** | 2000–2999 | 仅**源 IP**、分片、时间段 | 简单来源控制、VTY 限制 |
| **高级 ACL** | 3000–3999 | 源/目的 IP、协议、**端口**、优先级、时间段 | 精细访问控制（主力） |
| **二层 ACL** | 4000–4999 | **源/目的 MAC**、802.1p、以太类型 | 二层过滤 |
| **用户自定义 ACL** | 5000–5999 | 报文偏移位置自定义匹配 | 特殊报文 |
| **用户 ACL** | 6000–6999 | 用户/用户组（配合 NAC） | 业务随行场景 |

> 也可用**命名 ACL**：`acl name OFFICE-NET basic`，可读性强，推荐在生产中使用。

### 11_1.2 规则匹配机制（核心）
```latex
第1步 从 rule ID 最小（序号最小）的规则开始，自上而下匹配
第2步 命中第一条匹配的规则后【立即执行动作并停止】
第3步 所有规则都不匹配 → 执行隐含的【deny all】
```

> 因此：**精确（范围小）的规则放在前面，宽泛（范围大）的规则放在后面**。顺序写错 = 策略完全失效。

**Rule ID 步长**：默认步长为 5（rule 5、10、15...），便于中间插入新规则：

```latex
[SW] step 10                                # 修改步长
[SW-acl-adv-3001] rule 12 deny ip source ...   # 可在 10 和 20 之间插入
```

### 11_1.3 通配符掩码（Wildcard）
```latex
0 = 必须精确匹配      1 = 不关心

192.168.1.0  0.0.0.255      # 匹配 192.168.1.0/24 全部主机
192.168.1.1  0.0.0.0        # 仅匹配 192.168.1.1（可写成 source 192.168.1.1 0）
0.0.0.0      255.255.255.255  # 匹配任意（= any）
192.168.0.0  0.0.255.255    # 匹配 192.168.0.0/16
```

**特殊的奇偶/范围匹配（考试偶尔考）：**

```latex
192.168.1.0 0.0.0.254       # 匹配偶数地址（最后一位为偶数）
192.168.1.1 0.0.0.254       # 匹配奇数地址
```

---

## 11_2 基本 ACL
### 11_2.1 配置与应用
```latex
[Router] acl number 2001
[Router-acl-basic-2001] rule 5 deny source 192.168.1.0 0.0.0.255
[Router-acl-basic-2001] rule 10 permit source 192.168.3.0 0.0.0.255
[Router-acl-basic-2001] quit
```

**典型应用：限制 VTY 登录源**

```latex
[SW] acl 2000
[SW-acl-basic-2000] rule permit source 192.168.100.200 0
[SW-acl-basic-2000] rule deny source any
[SW-acl-basic-2000] quit

[SW] user-interface vty 0 4
[SW-ui-vty0-4] acl 2000 inbound
```

**接口应用：**

```latex
[Router] interface GigabitEthernet 0/0/1
[Router-GigabitEthernet0/0/1] traffic-filter inbound acl 2001
```

> ⚠️ **部署位置原则**：**基本 ACL 应尽量靠近目的端**（因为只看源 IP，靠近源端会把该源的所有流量都过滤掉，可能误伤）；**高级 ACL 应尽量靠近源端**（匹配维度多，可精确控制）。

---

## 11_3 高级 ACL
### 11_3.1 配置示例
```latex
# 拒绝 VLAN 10 访问 VLAN 20 的 FTP 服务
[Switch] acl number 3001
[Switch-acl-adv-3001] rule deny tcp source 10.1.1.0 0.0.0.255 destination 10.1.2.0 0.0.0.255 destination-port eq ftp
[Switch-acl-adv-3001] rule permit ip source any destination any
[Switch-acl-adv-3001] quit

[Switch] interface Vlanif 10
[Switch-Vlanif10] traffic-filter inbound acl 3001
```

### 11_3.2 常用操作符与端口
| 操作符 | 含义 |
| --- | --- |
| `eq` | 等于 |
| `gt` | 大于 |
| `lt` | 小于 |
| `neq` | 不等于 |
| `range` | 范围 |

```latex
destination-port eq 80                 # HTTP
destination-port eq 21                 # FTP 控制
destination-port eq 22                 # SSH
destination-port eq 23                 # Telnet
destination-port eq 443                # HTTPS
destination-port eq 3389               # RDP
destination-port range 20 21           # FTP 数据+控制
protocol icmp                          # ICMP（可用 icmp-type 细分）
protocol ip / tcp / udp / gre / esp
```

**拒绝 ping 但允许其他：**

```latex
[Router-acl-adv-3100] rule deny icmp source 192.168.1.0 0.0.0.255 destination any icmp-type echo
[Router-acl-adv-3100] rule permit ip
```

### 11_3.3 时间段 ACL（time-range）
```latex
[SW] time-range WORKTIME 08:00 to 18:00 working-day
[SW] acl 3001
[SW-acl-adv-3001] rule deny ip source 192.168.10.0 0.0.0.255 destination any time-range WORKTIME
[SW-acl-adv-3001] rule permit ip
```

用途：上班时间禁止访问视频网站、限制 P2P 等。

### 11_3.4 二层 ACL
```latex
# 匹配 802.1p 优先级为 6 的报文（典型用于语音）
[Switch] acl number 4000
[Switch-acl-L2-4000] rule permit 8021p 6

# 匹配特定 MAC
[Switch] acl 4001
[Switch-acl-L2-4001] rule deny source-mac 0001-0002-0003 ffff-ffff-ffff
```

---

## 11_4 流量过滤与策略路由
### 11_4.1 traffic-filter vs traffic-policy
| 机制 | 作用 | 特点 |
| --- | --- | --- |
| **traffic-filter** | 纯过滤（permit/deny） | 简单直接 |
| **traffic-policy**（MQC） | 过滤 + 改属性（重标记、限速、重定向） | 功能强，用于 QoS（见板块14） |
| **策略路由 PBR** | 改变转发路径（不走路由表） | 用于多出口分流 |

### 11_4.2 策略路由（PBR）
场景：内网有两条出口（教育网/公网），希望特定网段走特定出口。

```latex
# 第1步 定义 ACL 匹配流量
[Router] acl 3001
[Router-acl-adv-3001] rule permit ip source 192.168.10.0 0.0.0.255
[Router-acl-adv-3001] quit

# 第2步 定义流分类
[Router] traffic classifier C-EDU
[Router-classifier-C-EDU] if-match acl 3001

# 第3步 定义流行为（重定向下一跳）
[Router] traffic behavior B-EDU
[Router-behavior-B-EDU] redirect ip-nexthop 202.1.1.1

# 第4步 定义策略
[Router] traffic policy P-PBR
[Router-trafficpolicy-P-PBR] classifier C-EDU behavior B-EDU

# 第5步 应用到入接口（策略路由只能用在入方向）
[Router] interface gigabitethernet 0/0/0
[Router-GigabitEthernet0/0/0] traffic-policy P-PBR inbound
```

> 策略路由的优先级**高于路由表**。验证：`display traffic-policy applied-record`。

### 11_4.3 ACL 管理与查看
```latex
[SW] display acl 3001                             # 查看规则及【匹配计数】
[SW] display acl all
[SW] display traffic-filter applied-record         # 查看应用位置
[SW] display traffic-policy applied-record
[SW] reset acl counter 3001                        # 清空计数（便于观察新流量）
[SW] undo acl number 3001                          # 删除整个 ACL
```

> ★ **匹配计数（Matched）是排错的利器**：配置了 ACL 但不确定是否命中，看计数是否增长。**计数不增长 = 流量没走到这条规则**（方向或位置错了）。

### 11_4.4 ACL 应用逻辑示意
```latex
                    报文进入接口（inbound）
                            │
                            ▼
                  ┌───────────────────┐
                  │   rule 5  匹配？   │──是──▶ 【deny】丢弃 ──▶ 结束
                  └─────────┬─────────┘             或
                            │否                   【permit】放行 ──▶ 结束
                            ▼
                  ┌───────────────────┐
                  │  rule 10 匹配？    │──是──▶ 执行动作 ──▶ 结束（★ 不再往下）
                  └─────────┬─────────┘
                            │否
                            ▼
                  ┌───────────────────┐
                  │  rule 15 匹配？    │──是──▶ 执行动作 ──▶ 结束
                  └─────────┬─────────┘
                            │否
                            ▼
                  ┌───────────────────┐
                  │ 后续 rule 依次匹配 │──是──▶ 执行动作 ──▶ 结束
                  └─────────┬─────────┘
                            │否（所有规则都不匹配）
                            ▼
                  ┌───────────────────┐
                  │ 隐含 rule deny all │──▶ 【全部丢弃】
                  └───────────────────┘
                      ↑ 华为 ACL 末尾自动附加，配置文件中看不到
```

---

## 11_5 NAT 地址转换
### 11_5.1 NAT 类型
| 类型 | 原理 | 适用场景 |
| --- | --- | --- |
| **静态 NAT** | 一对一固定映射 | 内网服务器对外提供固定公网地址 |
| **NAPT（PAT）** | 多对一 + 端口复用（地址池） | 多用户共享一批公网地址上网 |
| **Easy IP** | 多对一，直接用出接口地址 | **中小企业/家用出口最常用**（无固定公网地址池） |
| **NAT Server** | 端口映射（公网端口 → 内网服务器端口） | 内网 Web/邮件服务器对外发布 |

### 11_5.2 配置
```latex
# ============ 第1步 静态 NAT ============
[Router] nat static global 202.1.1.10 inside 192.168.1.10
[Router] interface gigabitethernet 0/0/1
[Router-GigabitEthernet0/0/1] nat static enable

# ============ 第2步 NAPT（地址池）============
[Router] nat address-group 1 202.1.1.10 202.1.1.20
[Router] acl 2000
[Router-acl-basic-2000] rule permit source 192.168.1.0 0.0.0.255
[Router] interface gigabitethernet 0/0/1
[Router-GigabitEthernet0/0/1] nat outbound 2000 address-group 1

# 只做地址转换、不做端口复用（no-pat）：一个私网地址占一个公网地址
[Router-GigabitEthernet0/0/1] nat outbound 2000 address-group 1 no-pat

# ============ 第3步 Easy IP（最常用）============
[Router] interface gigabitethernet 0/0/1
[Router-GigabitEthernet0/0/1] nat outbound 2000

# ============ 第4步 NAT Server（发布内网服务器）============
[Router-GigabitEthernet0/0/1] nat server protocol tcp global 202.1.1.10 80 inside 192.168.1.100 80
```

### 11_5.3 NAT 验证
```latex
[Router] display nat session                  # 会话表（★ 有没有转换？）
[Router] display nat outbound                 # 出方向 NAT 配置
[Router] display nat server                   # NAT Server 映射
[Router] display nat statistics               # 统计
```

### 11_5.4 NAT ALG 与特殊协议
FTP 这类协议的**数据连接端口是在控制报文里动态协商的**，NAT 设备看不懂就转不了，需要 ALG（应用层网关）：

```latex
[Router] nat alg ftp enable
[Router] nat alg dns enable
[Router] nat alg sip enable
[Router] nat alg rtsp enable
```

> **典型故障**：FTP 能登录但列不出目录（被动模式）→ **ALG 未开**或防火墙未放行被动端口范围。

### 11_5.5 NAT 排错
| 现象 | 原因 | 处理 |
| --- | --- | --- |
| 内网不能上网 | ACL 未 permit 内网网段 | `display acl 2000`（看计数） |
| ACL 有 permit 仍不通 | ACL 规则**顺序错误**（deny 在前） | 调整 rule ID |
| 会话表无记录 | 流量没到 NAT 接口 | 检查路由、接口方向（outbound） |
| FTP 能登录列不出目录 | **ALG 未开** | `nat alg ftp enable` |
| 外网访问不了内网服务器 | NAT Server 未配或端口错 | `display nat server` |
| 部分网站打不开 | MTU/MSS 问题（PPPoE） | `tcp adjust-mss 1452` |

---

## 11_6 综合案例：企业出口（NAT + ACL 互访控制）
### 11_6.1 需求与规划
| 项目 | 规划 |
| --- | --- |
| 内网网段 | 办公 192.168.10.0/24、无线 192.168.20.0/24、监控 192.168.30.0/24 |
| 出口 | 公网地址 202.1.1.1/30，对端 202.1.1.2 |
| 需求第1步 | 全网通过 Easy IP 上网 |
| 需求第2步 | **监控网段禁止访问办公与无线** |
| 需求第3步 | 上班时间（8:00–18:00）办公网禁止访问某视频网段 |

### 11_6.2 完整配置
```latex
# ============ 接口与路由 ============
[Router] interface gigabitethernet 0/0/0              # 内网口
[Router-GigabitEthernet0/0/0] ip address 192.168.1.1 24
[Router] interface gigabitethernet 0/0/1               # 公网口
[Router-GigabitEthernet0/0/1] ip address 202.1.1.1 30
[Router] ip route-static 0.0.0.0 0 202.1.1.2
[Router] ip route-static 192.168.10.0 24 192.168.1.2   # 回程到内网三层交换机
[Router] ip route-static 192.168.20.0 24 192.168.1.2
[Router] ip route-static 192.168.30.0 24 192.168.1.2

# ============ ACL 2000：定义允许 NAT 的源 ============
[Router] acl 2000
[Router-acl-basic-2000] rule permit source 192.168.10.0 0.0.0.255
[Router-acl-basic-2000] rule permit source 192.168.20.0 0.0.0.255
[Router-acl-basic-2000] quit

# ============ Easy IP ============
[Router-GigabitEthernet0/0/1] nat outbound 2000

# ============ 高级 ACL：监控不能访问办公/无线 ============
[Router] acl 3001
[Router-acl-adv-3001] rule deny ip source 192.168.30.0 0.0.0.255 destination 192.168.10.0 0.0.0.255
[Router-acl-adv-3001] rule deny ip source 192.168.30.0 0.0.0.255 destination 192.168.20.0 0.0.0.255
[Router-acl-adv-3001] rule permit ip
[Router-acl-adv-3001] quit

[Router] interface gigabitethernet 0/0/0
[Router-GigabitEthernet0/0/0] traffic-filter inbound acl 3001   # 靠近源端

# ============ 时间段限制 ============
[Router] time-range WORKTIME 08:00 to 18:00 working-day
[Router] acl 3002
[Router-acl-adv-3002] rule deny ip source 192.168.10.0 0.0.0.255 destination 10.10.10.0 0.0.0.255 time-range WORKTIME
[Router-acl-adv-3002] rule permit ip
```

### 11_6.3 验收
```latex
# 设备侧
[Router] display nat session                 # 有内网 IP → 公网 IP 的转换记录
[Router] display acl 3001                    # deny 规则的匹配计数在增长（说明生效）

# 终端侧
办公 PC：ping 8.8.8.8                        # 通
监控 PC：ping 192.168.10.1                   # 不通（符合需求第2步）
监控 PC：ping 8.8.8.8                        # 通（不能访问办公但能上网）
```

---

## 11_7 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 排查 | 常见根因 |
| --- | --- | --- |
| ACL 配了没效果 | `display acl 3001`（看计数） | 计数不增 = 应用位置/方向错；计数增但动作不符 = 规则顺序错 |
| 配了 ACL 全网不通 | 检查是否漏了 `permit ip` | **末尾隐含 deny all** |
| 只想拦一部分结果全拦了 | 规则顺序 | 精确规则要放前面 |
| NAT 后不能上网 | `display nat session` | ACL 未 permit 源；或缺默认路由/回程路由 |
| NAT Server 外网访问不到 | `display nat server` | 端口/协议写错；或公网口未开 |
| 同一接口同方向两个 filter | `display traffic-filter applied-record` | **后配覆盖先配**，只生效一个 |
| 策略路由不生效 | `display traffic-policy applied-record` | PBR 只能应用在**入方向** |

---

## 11_8 场景笔记与验证
### 11_8.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **匹配机制卡** | 自上而下、命中即停、末尾隐含 deny（三条背死） |
| **通配符练习** | 0.0.0.255 / 0.0.255.255 / 0.0.0.254（奇偶）能秒判 |
| **NAT 类型对照** | 静态 / NAPT / Easy IP / NAT Server 的写法与场景 |
| **坑本** | 忘写 permit ip；ACL 应用方向反了；PBR 配在出方向；FTP 忘了 ALG |

### 11_8.2 验证三板斧（本板块版）
```latex
第1步 看配置：display acl 3001（规则对不对）
第2步 看计数：display acl 3001（Matched 有没有涨）← ★ 最关键
第3步 打流量：从被控端 ping / 访问应用（被拦 = 不通；通过 = 通）
```

**NAT 专项：**

```latex
display nat session        # 有会话 = 转换成功；无会话 = 流量没到或 ACL 没匹配
```

### 11_8.3 一个值得养成的习惯
配完 ACL 先 `reset acl counter 3001` **清零计数**，再打一次测试流量，然后看计数。这样能 100% 确认"这条规则到底有没有命中"，而不是靠猜。

---

## 11_9 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | ACL 末尾默认放行 | **末尾隐含 deny all**，必须显式写 permit |
| 2 | 规则顺序无所谓 | 自上而下、命中即停，**精确规则在前** |
| 3 | 通配符就是子网掩码反码 | 概念相似但用途不同，0 = 精确匹配，1 = 不关心 |
| 4 | 基本 ACL 靠近源端 | 基本 ACL **靠近目的端**；高级 ACL 靠近源端 |
| 5 | 同接口可配多个 filter | 同方向**后配覆盖先配** |
| 6 | PBR 可配出方向 | 策略路由只能应用在**入方向** |
| 7 | NAT 只需配 nat outbound | 还要 ACL 指定源 + 回程路由 |
| 8 | FTP 问题都是权限问题 | **ALG 未开**是被动模式失败的头号原因 |
| 9 | NAT Server 与 outbound 冲突 | 可共存；Server 用于入方向发布服务 |

---

# 板块12 · 接入安全与用户管理
> 定位：网络安全的"最后一百米"。核心命题是：**如何确保接上网线的是"该接的人、该接的设备"**。HCIP 要求掌握端口安全、DHCP Snooping、IPSG 等交换机安全特性；HCIE 要求能设计完整的 NAC（网络准入控制）方案。
> 攻击面清单：私接设备、私接 DHCP 服务器、MAC 泛洪、ARP 欺骗、IP 伪造、非法接入、管理面攻击。

## 12_1 接入安全威胁全景
> **本节导读**：先看清对手。接入层的攻击手段其实就那么几类，防御技术也是一一对应的——把这张表记住，后面的章节都是它的展开。

| 威胁 | 攻击方式 | 防御技术 | 章节 |
| --- | --- | --- | --- |
| 私接交换机/Hub | 造成环路、广播风暴 | **BPDU 保护、端口安全、Loop Detection** | 12_2 / 板块3 |
| 私接 DHCP 服务器 | 下发错误网关/DNS（中间人） | **DHCP Snooping** | 12_3 |
| MAC 泛洪（CAM Table Overflow） | 伪造大量 MAC 塞满表，交换机变 Hub | **端口安全（限制 MAC 数）** | 12_2 |
| DHCP 饿死攻击 | 伪造大量 CHADDR 耗尽地址池 | **Snooping + CHADDR 检查 + 限速** | 12_3 |
| ARP 欺骗 | 伪造网关 ARP 应答，劫持流量 | **DAI、ARP 防欺骗** | 12_4 |
| IP 伪造 | 冒用他人 IP 绕过策略 | **IPSG** | 12_5 |
| 非法终端接入 | 员工私带电脑入网 | **802.1X / Portal / MAC 认证（NAC）** | 12_6 |
| 管理面攻击 | 暴力破解 SSH、未授权访问 | **AAA + ACL + 命令分级** | 12_7 |

> **现场故事**：某单位早上全员上不了网，网关能 ping 通，DNS 也正常。抓包发现大家拿到的网关是 192.168.1.1——而真正的网关是 192.168.10.254。**有人在工位上接了个家用路由器**。当天下午全网开了 DHCP Snooping，问题再没出现过。这类故障的特点是"现象诡异、原因简单"，而 Snooping 就是那两行配置。

---

## 12_2 端口安全（Port Security）
### 12_2.1 原理与 MAC 类型
把端口与 MAC 地址绑定，限制该端口允许学习的 MAC 数量与具体地址，超限即触发保护动作。

| 类型 | 学习方式 | 是否保存配置 | 重启后 |
| --- | --- | --- | --- |
| **安全动态 MAC** | 动态学习 | 否 | 丢失 |
| **安全静态 MAC** | 手工配置 | 是 | 保留 |
| **Sticky MAC（粘性）** | 动态学习并**自动转为静态** | 是 | **保留**（最实用） |

### 12_2.2 配置
```latex
[SW] port-security enable                          # 全局开启

[SW] interface ethernet 1/0/1
[SW-Ethernet1/0/1] port-security enable
[SW-Ethernet1/0/1] port-security max-mac-num 2     # 最大 MAC 数
[SW-Ethernet1/0/1] port-security port-mode autolearn
[SW-Ethernet1/0/1] port-security mac-address sticky      # 粘性 MAC
[SW-Ethernet1/0/1] port-security protect-action shutdown
[SW-Ethernet1/0/1] quit

[SW] port-security timer disableport 30            # 临时关闭时长 30 秒
```

### 12_2.3 保护动作（protect-action）
| 动作 | 行为 | 适用 |
| --- | --- | --- |
| **protect** | 丢弃非法报文，不告警 | 隐蔽处理 |
| **restrict** | 丢弃 + **告警（trap/log）** | 推荐（可审计） |
| **shutdown** | 直接关闭端口 | 最严格 |

### 12_2.4 验证
```latex
[SW] display port-security                    # 全局状态
[SW] display port-security interface e1/0/1  # 端口详情
[SW] display mac-address security             # 安全 MAC 表
```

### 12_2.5 场景建议
| 场景 | 配置 |
| --- | --- |
| PC 固定工位 | sticky MAC + max 2（PC + IP 电话） |
| 会议室 | max 10（临时多人），不做 sticky |
| 打印机/摄像头 | 静态 security MAC |
| 接 AP 的端口 | **不要开端口安全**（无线用户 MAC 太多） |

> ⚠️ 接 AP 或下联交换机的端口**绝不能**限制 MAC 数量，否则大量合法终端被误杀。

---

## 12_3 DHCP Snooping 详解
### 12_3.1 工作机制
```latex
第1步 交换机在 VLAN 内开启 Snooping，端口分为 Trusted / Untrusted
第2步 Untrusted 端口【丢弃】服务器方向的报文（Offer/Ack）
第3步 Trusted 端口正常转发服务器报文
第4步 交换机监听完整的 DHCP 交互，生成【绑定表】：IP + MAC + VLAN + 端口 + 租期
```

### 12_3.2 完整配置
```latex
[SW] dhcp enable
[SW] dhcp snooping enable ipv4

[SW] vlan 10
[SW-vlan10] dhcp snooping enable
[SW-vlan10] dhcp snooping trusted interface gigabitethernet 0/0/1       # 上行口=信任
[SW-vlan10] quit

[SW] interface gigabitethernet 0/0/2
[SW-GigabitEthernet0/0/2] dhcp snooping enable
[SW-GigabitEthernet0/0/2] dhcp snooping check dhcp-giaddr enable        # 防 GIADDR 欺骗
[SW-GigabitEthernet0/0/2] dhcp snooping check dhcp-chaddr enable        # 防 CHADDR 伪造
[SW-GigabitEthernet0/0/2] dhcp snooping check dhcp-request enable
[SW-GigabitEthernet0/0/2] dhcp snooping user-bind max-number 20
[SW-GigabitEthernet0/0/2] quit

[SW] arp dhcp-snooping-detect enable              # ARP 与 Snooping 联动
```

### 12_3.3 防 DHCP 饿死攻击（限速）
```latex
[SW] interface gigabitethernet 0/0/2
[SW-GigabitEthernet0/0/2] dhcp snooping rate-limit enable
[SW-GigabitEthernet0/0/2] dhcp snooping rate-limit 10            # 每秒最多 10 个 DHCP 报文
[SW-GigabitEthernet0/0/2] dhcp snooping rate-limit alarm enable
```

### 12_3.4 静态绑定表（重要服务器/固定终端）
```latex
[SW] user-bind static ip-address 192.168.10.100 mac-address 0001-0002-0003 interface gigabitethernet 0/0/5 vlan 10
[SW] display dhcp snooping user-bind all
```

> 静态绑定表的价值：IPSG/DAI 可依赖它工作；且**即使终端不用 DHCP（手工配 IP）也能被保护**。

---

## 12_4 ARP 安全
### 12_4.1 ARP 欺骗原理与危害
```latex
攻击者（192.168.1.100，MAC: AA）不断发送伪造 ARP 应答：
  "192.168.1.1（网关）的 MAC 是 AA"
→ 其他主机的 ARP 表被污染 → 流量全部经攻击者中转 → 窃取/篡改数据
```

### 12_4.2 防御手段
**第1步 DAI（动态 ARP 检测，最有效）：**

```latex
[SW] dhcp snooping enable ipv4
[SW] vlan 10
[SW-vlan10] dhcp snooping enable
[SW-vlan10] arp anti-attack check user-bind enable        # 基于绑定表检查 ARP 报文
[SW-vlan10] arp anti-attack check user-bind alarm enable
```

原理：收到 ARP 报文时，与 **Snooping 绑定表 / 静态 user-bind 表**比对，IP + MAC + 端口/VLAN 不匹配则丢弃。

**第2步 ARP 报文限速：**

```latex
[SW-GigabitEthernet0/0/2] arp anti-attack rate-limit enable
[SW-GigabitEthernet0/0/2] arp anti-attack rate-limit 50           # 每秒 50 个 ARP 报文
```

**第3步 网关 ARP 防欺骗（在网关上做）：**

```latex
[SW] arp anti-attack gateway-duplicate enable             # 检测网关地址冲突
[SW] arp gratuitous-arp send enable                       # 主动发免费 ARP（刷新全网）
```

**第4步 ARP 表项固化：**

```latex
[SW] arp anti-attack entry-check fixed-mac enable         # 固定 MAC 模式
[SW] arp anti-attack entry-check fixed-all enable         # 完全固定
[SW] arp anti-attack entry-check send-ack enable          # 发送确认后才更新
```

**第5步 静态 ARP 绑定（小规模关键设备）：**

```latex
[SW] arp static 192.168.10.100 0001-0002-0003
```

### 12_4.3 验证
```latex
[SW] display arp anti-attack configuration
[SW] display arp anti-attack statistics
[SW] display arp
[SW] display arp anti-attack gateway-duplicate item
```

---

## 12_5 IPSG（IP Source Guard）
### 12_5.1 原理与配置
基于绑定表（DHCP Snooping 或静态 user-bind）检查报文的**源 IP / 源 MAC / VLAN / 入端口**，全部匹配才放行。

```latex
# 方式一：接口下（依赖 DHCP Snooping 绑定表）
[SW] interface gigabitethernet 0/0/2
[SW-GigabitEthernet0/0/2] ip source check user-bind enable

# 方式二：VLAN 下批量
[SW] vlan 10
[SW-vlan10] ip source check user-bind enable

# 检查项（可选组合，越严越安全也越容易误伤）
[SW-GigabitEthernet0/0/2] ip source check user-bind check-item ip-address mac-address
```

### 12_5.2 园区网标准配置组合（推荐落地顺序）
华为官方《小型园区配置示例》给出的落地顺序是：**先开 DHCP Snooping，再开 IPSG**，两者是依赖关系而非并列关系。

```latex
配置逻辑链：
  终端私接小路由器开 DHCP
        ↓ 危害
  合法用户拿到假地址 → 上不了网
        ↓ 对策第1步
  DHCP Snooping（信任合法上行口，抑制非法 DHCP 服务器）
        ↓ 同时生成绑定表
        ↓ 对策第2步
  IPSG（防止用户私改 IP 后攻击网络）
```

官方推荐的匹配项组合是：**IP + MAC + VLAN 三项**（兼顾安全性与兼容性，不建议默认加接口，否则终端换端口就断网）。

```latex
# 第1步 全局开启
[SW] dhcp snooping enable ipv4
# 第2步 指定信任端口（连接合法 DHCP 服务器 / 上行的端口）
[SW] vlan 10
[SW-vlan10] dhcp snooping trusted interface Eth-Trunk1
# 第3步 连接 DHCP 服务器与终端的接口都使能 Snooping
# 第4步 开启 IPSG（IP + MAC + VLAN 三项检查）
[SW-vlan10] ip source check user-bind enable
[SW-vlan10] ip source check user-bind check-item ip-address mac-address vlan
```

### 12_5.3 排错
| 现象 | 原因 | 处理 |
| --- | --- | --- |
| 开了 IPSG 后终端断网 | 无绑定表项（终端静态 IP 且未配静态绑定） | 配 `user-bind static` 或改用 DHCP |
| 部分终端能上部分不能 | 绑定表项缺失或过期 | `display dhcp snooping user-bind all` |
| 换了端口就上不了网 | 检查项包含了 interface | 去掉 interface 检查项 |
| 合法用户被误杀 | 绑定表项与实际不符（换了网卡） | 清除旧表项，重新获取地址 |

---

## 12_6 NAC 网络准入控制
### 12_6.1 三种认证方式
| 方式 | 原理 | 优点 | 缺点 | 适用 |
| --- | --- | --- | --- | --- |
| **802.1X** | 客户端 + 交换机端口认证（EAPoL） | 安全性高、认证在接入层 | 需装客户端（现代 OS 多内置） | **办公有线内网** |
| **Portal** | 浏览器弹出认证页面 | 无需客户端，体验好 | 认证在三层（先拿地址再认证） | 访客、无线 |
| **MAC 认证** | 以 MAC 作为用户名密码 | 零安装 | MAC 可伪造，安全性低 | 打印机、摄像头等哑终端 |

**组合建议**：办公网 **802.1X 为主 + MAC 认证兜底**（哑终端）；访客网用 Portal。

### 12_6.2 802.1X 配置（本地认证示例）
```latex
# 第1步 全局开启 802.1X
[SW] dot1x enable

# 第2步 配置 AAA 域与用户
[SW] aaa
[SW-aaa] local-user user1 password cipher User1@2026
[SW-aaa] local-user user1 service-type 8021x
[SW-aaa] quit

# 第3步 接口下开启
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] dot1x enable
[SW-GigabitEthernet0/0/1] dot1x max-user 2
```

### 12_6.3 802.1X + RADIUS（生产标准）
```latex
[SW] radius-server template RD1
[SW-radius-RD1] radius-server shared-key cipher Radius@Key
[SW-radius-RD1] radius-server authentication 192.168.99.100 1812
[SW-radius-RD1] radius-server accounting 192.168.99.100 1813
[SW-radius-RD1] quit

[SW] aaa
[SW-aaa] authentication-scheme AUTH-RD
[SW-aaa-authen-AUTH-RD] authentication-mode radius
[SW-aaa] domain default
[SW-aaa-domain-default] authentication-scheme AUTH-RD
[SW-aaa-domain-default] radius-server RD1
```

> RADIUS 端口：**1812（认证）/ 1813（计费）**；HWTACACS 端口 **49**。

### 12_6.4 授权结果（下发 VLAN/ACL）
服务器下发属性使终端进入指定 VLAN 或应用 ACL（实现"不同人不同权限"）：

```latex
# RADIUS 服务器下发属性（示例）
Tunnel-Type = VLAN(13)
Tunnel-Medium-Type = IEEE-802(6)
Tunnel-Private-Group-ID = 100        # 下发 VLAN 100
Filter-Id = ACL-NAME                  # 下发 ACL
```

### 12_6.5 验证与排错
```latex
[SW] display dot1x                       # 全局状态
[SW] display dot1x interface g0/0/1      # 接口状态
[SW] display dot1x statistics            # 统计
[SW] display access-user                 # 在线用户
```

| 现象 | 排查 |
| --- | --- |
| 认证一直失败 | 检查共享密钥、RADIUS 可达、用户名域（@domain） |
| 能认证但拿不到地址 | 检查下发的 VLAN 是否存在DHCP 是否可达 |
| 哑终端通不过 | 配 MAC 认证兜底，或开启免认证 VLAN（受限权限） |

**先于终端验证服务器连通性（强烈推荐）：**

```latex
<SW> test-aaa user001 Huawei@123 radius-template RD1
# 返回成功说明 RADIUS 服务器、共享密钥、账号本身都没问题
# 若失败，问题在"设备↔服务器"，而不是终端——这一步能省掉一半排查时间
```

**端口因安全特性被 error-down 后的自动恢复：**

```latex
[SW] error-down auto-recovery cause bpdu-protection interval 300     # BPDU 保护 5 分钟后自动恢复
[SW] error-down auto-recovery cause port-security interval 300       # 端口安全
[SW] error-down auto-recovery cause dhcp-snooping-error interval 300 # DHCP Snooping 超限
[SW] display error-down recovery                                     # 查看自动恢复配置
```

---

## 12_7 AAA 与设备管理安全
### 12_7.1 AAA 三要素
| 要素 | 作用 |
| --- | --- |
| **认证（Authentication）** | 你是谁 |
| **授权（Authorization）** | 你能干什么 |
| **计费（Accounting）** | 你干了什么 |

### 12_7.2 配置（HWTACACS+ / RADIUS）
```latex
# HWTACACS 模板（华为私有，命令级授权更细）
[SW] hwtacacs-server template TC1
[SW-hwtacacs-TC1] hwtacacs-server authentication 192.168.99.200 49
[SW-hwtacacs-TC1] hwtacacs-server authorization 192.168.99.200 49
[SW-hwtacacs-TC1] hwtacacs-server shared-key cipher Tacacs@Key
[SW-hwtacacs-TC1] quit

[SW] aaa
[SW-aaa] authentication-scheme AUTH-TC
[SW-aaa-authen-AUTH-TC] authentication-mode hwtacacs local    # ★ 服务器挂了用本地兜底
[SW-aaa] domain default_admin
[SW-aaa-domain-default_admin] authentication-scheme AUTH-TC
[SW-aaa-domain-default_admin] hwtacacs-server TC1
```

> ⚠️ **一定要配本地兜底**（`hwtacacs local` 或 `radius local`），否则 AAA 服务器一挂，全网设备都登不上。

### 12_7.3 加固清单（可直接作为检查表）
```latex
□ 修改默认账号密码，删除无用账号
□ 关闭 Telnet / HTTP，只留 SSH（stelnet server enable）
□ VTY 限定 SSH + ACL 限制源（acl 2000 inbound）
□ VTY 配置 idle-timeout
□ Console 口配密码与超时
□ 用户分级（运维 level 2，管理员 level 3）
□ 开启 AAA 集中认证 + 本地兜底
□ 配置日志服务器（info-center loghost）与 NTP
□ 关闭未用端口（shutdown）
□ 配置登录 banner 警示信息
□ 定期备份配置（FTP/TFTP/自动化脚本）
```

---

## 12_8 综合案例：办公网接入安全加固
### 12_8.1 需求
办公 VLAN 10 接入交换机：防私接 DHCP、防私改 IP、防 ARP 欺骗、限制每端口 2 个 MAC、哑终端用 MAC 认证。

### 12_8.2 完整配置
```latex
# ============ 全局基础安全 ============
[SW] dhcp enable
[SW] dhcp snooping enable ipv4
[SW] port-security enable
[SW] dot1x enable
[SW] stp bpdu-protection

# ============ VLAN 级安全 ============
[SW] vlan 10
[SW-vlan10] dhcp snooping enable
[SW-vlan10] dhcp snooping trusted interface gigabitethernet 0/0/24     # 上行信任
[SW-vlan10] arp anti-attack check user-bind enable                     # DAI
[SW-vlan10] ip source check user-bind enable                           # IPSG
[SW-vlan10] ip source check user-bind check-item ip-address mac-address vlan
[SW-vlan10] quit

# ============ 用户端口 ============
[SW] interface gigabitethernet 0/0/5
[SW-GigabitEthernet0/0/5] port link-type access
[SW-GigabitEthernet0/0/5] port default vlan 10
[SW-GigabitEthernet0/0/5] stp edged-port enable
# 端口安全
[SW-GigabitEthernet0/0/5] port-security enable
[SW-GigabitEthernet0/0/5] port-security max-mac-num 2
[SW-GigabitEthernet0/0/5] port-security mac-address sticky
[SW-GigabitEthernet0/0/5] port-security protect-action restrict
# DHCP Snooping 检查
[SW-GigabitEthernet0/0/5] dhcp snooping check dhcp-chaddr enable
[SW-GigabitEthernet0/0/5] dhcp snooping rate-limit 10
# ARP 限速
[SW-GigabitEthernet0/0/5] arp anti-attack rate-limit enable
[SW-GigabitEthernet0/0/5] arp anti-attack rate-limit 50
# 802.1X（哑终端走 MAC 认证兜底）
[SW-GigabitEthernet0/0/5] dot1x enable
[SW-GigabitEthernet0/0/5] dot1x mac-bypass

# ============ 上行口 ============
[SW] interface gigabitethernet 0/0/24
[SW-GigabitEthernet0/0/24] port link-type trunk
[SW-GigabitEthernet0/0/24] port trunk allow-pass vlan 10 99
[SW-GigabitEthernet0/0/24] undo port trunk allow-pass vlan 1
[SW-GigabitEthernet0/0/24] stp edged-port disable
```

### 12_8.3 验证
```latex
[SW] display dhcp snooping user-bind all        # 绑定表（有记录）
[SW] display port-security interface g0/0/5     # 端口安全状态
[SW] display arp anti-attack statistics         # DAI 统计（有无丢弃）
[SW] display dot1x interface g0/0/5             # 认证状态
[SW] display access-user                        # 在线用户

# 攻击模拟验证：
# 第1步 在用户口接一台开 DHCP 的小路由器 → 其他终端仍拿到正确地址（Snooping 生效）
# 第2步 手工把 PC 改成别人的 IP → 上不了网（IPSG 生效）
# 第3步 伪造 ARP 应答 → 被丢弃，DAI 计数增长
```

---

## 12_9 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 排查 | 常见根因 |
| --- | --- | --- |
| 开了 Snooping 全网拿不到地址 | `display dhcp snooping` | **上行口没设为 trusted** |
| 开了 IPSG 后部分终端断网 | `display dhcp snooping user-bind all` | 静态 IP 终端无绑定表项 |
| DAI 误伤合法用户 | `display arp anti-attack statistics` | 绑定表过期/不匹配（换了网卡） |
| 端口安全误杀 | `display port-security interface` | 接了 AP 或 Hub（MAC 超数） |
| 802.1X 认证失败 | `display dot1x statistics` | 共享密钥错、域配置错、服务器不可达 |
| AAA 服务器挂了登不上设备 | — | **没配本地兜底**（`radius local`） |
| 换了端口就上不了网 | 检查 IPSG 检查项 | 检查项含 interface |

---

## 12_10 场景笔记与验证
### 12_10.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **攻击—防御对照表** | 8 种攻击对应什么技术（见 12_1） |
| **三件套依赖图** | DHCP Snooping → 绑定表 → IPSG / DAI（先有表才有防） |
| **认证方式选型卡** | 802.1X（办公）/ Portal（访客）/ MAC（哑终端） |
| **坑本** | 上行口忘配 trusted；IPSG 导致静态 IP 终端断网；AAA 没配本地兜底 |

### 12_10.2 验证三板斧（本板块版）
```latex
第1步 看配置：display dhcp snooping / display port-security / display dot1x
第2步 看表项：display dhcp snooping user-bind all（绑定表有没有、对不对）
第3步 打流量 + 攻击模拟：私接 DHCP（应无效）、改 IP（应断网）、伪造 ARP（应被丢）
```

### 12_10.3 建议做一次的攻防实验
在 eNSP 或真机上，按顺序做三个"攻击"：

1. 接一台开 DHCP 的路由器 → 观察开/不开 Snooping 的差别；
2. 把 PC 改成别人的 IP → 观察开/不开 IPSG 的差别；
3. 用工具发伪造 ARP → 观察开/不开 DAI 的差别。

**这三组对比做完，接入安全就从"背配置"变成了"我见过它真的起作用"。**

---

## 12_11 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | Snooping 开了就安全 | 必须指定 **trusted 上行口**，否则全网拿不到地址 |
| 2 | IPSG 可独立工作 | 依赖 **Snooping 绑定表或静态 user-bind** |
| 3 | 端口安全越严越好 | 接 AP/Hub 的**不能开**，否则误杀一片 |
| 4 | Sticky MAC 不保存 | 会**自动转静态**并保存，重启保留 |
| 5 | DAI 只看 IP | 比对 **IP+MAC+VLAN+接口**四维 |
| 6 | AAA 只配服务器就行 | 必须配 **local 兜底** |
| 7 | 802.1X 只适合办公网 | 哑终端要用 **MAC 认证兜底**（mac-bypass） |
| 8 | RADIUS 端口 1812 | 认证 1812，**计费 1813**；HWTACACS 是 49 |

---

# 板块13 · 网络可靠性与快速收敛
> 定位：让网络"断而不知"。HCIP 要求掌握 VRRP、BFD、链路备份；HCIE 要求能设计端到端的可靠性方案并量化切换时间（亚秒级 vs 秒级）。
> 可靠性 = **冗余（有备份）+ 检测（能发现故障）+ 切换（切得够快）** 三件事缺一不可。

## 13_1 可靠性技术全景
> **本节导读**：可靠性 = **冗余 + 检测 + 切换**，三件事缺一不可。看这张表时注意两件事：每一层解决的是哪一类故障，以及切换要多久。

| 层次 | 技术 | 保护对象 | 典型切换时间 |
| --- | --- | --- | --- |
| **设备级** | 堆叠 iStack / CSS / M-LAG | 整机故障 | 毫秒–秒级 |
| **链路级** | Eth-Trunk、接口备份 | 单链路故障 | 毫秒级（Eth-Trunk 无感知） |
| **网关级** | **VRRP** | 网关单点 | 默认 3 秒+，配 BFD 可 <1 秒 |
| **检测级** | **BFD / NQA / DLDP** | 故障发现 | 毫秒–秒级 |
| **路由级** | 路由协议收敛（OSPF+BFD/IS-IS+BFD/BGP） | 路径故障 | <1 秒（带 BFD） |
| **转发级** | **FRR（LFA/TE FRR）** | 链路/节点故障 | <50 ms |
| **业务级** | 双机热备、会话同步（防火墙） | 业务中断 | 秒级 |

> 设计可靠性方案时，按这张表**逐层回答"这一层谁来兜底"**，论述题直接就有骨架。

---

## 13_2 VRRP 虚拟路由冗余
### 13_2.1 原理
```latex
多台路由器组成一个 VRRP 组，共享一个【虚拟 IP】（终端的网关）
  ├─ Master：承担实际转发，周期性发送 VRRP 通告（默认 1 秒）
  └─ Backup：监听通告，Master 超时（3×通告间隔 + 偏移）后接管
```

+ **协议号 112**，目的组播地址 **224.0.0.18**，虚拟 MAC 格式：**00-00-5E-00-01-{VRID}**（如 VRID 1 → 00-00-5E-00-01-01）；
+ 优先级范围 0–255，默认 **100**，**越大越优**；
+ 优先级 **255** 保留给"IP 地址拥有者"（虚拟 IP = 真实接口 IP 的设备）。

### 13_2.2 基础配置
```latex
# ================= Master（SW1）=================
[SW1] interface Vlanif 10
[SW1-Vlanif10] ip address 192.168.10.1 24
[SW1-Vlanif10] vrrp vrid 1 virtual-ip 192.168.10.254
[SW1-Vlanif10] vrrp vrid 1 priority 120                      # 高于默认 100 → Master
[SW1-Vlanif10] vrrp vrid 1 preempt-mode timer delay 20       # 抢占延迟 20 秒（避免震荡）
[SW1-Vlanif10] vrrp vrid 1 timer advertise 1                 # 通告间隔 1 秒

# ================= Backup（SW2）=================
[SW2] interface Vlanif 10
[SW2-Vlanif10] ip address 192.168.10.2 24
[SW2-Vlanif10] vrrp vrid 1 virtual-ip 192.168.10.254
[SW2-Vlanif10] vrrp vrid 1 priority 100                      # 默认，可不配
```

### 13_2.3 上行链路跟踪（关键！）
**问题场景**：SW1 是 Master，但 SW1 的上行链路断了——SW1 仍是 Master，流量到 SW1 后无路可走 → **黑洞**。

解决：**跟踪上行接口，链路 down 时自动降低优先级**。

```latex
[SW1-Vlanif10] vrrp vrid 1 track interface gigabitethernet 0/0/24 reduced 30
# 上行口 down → 优先级 120-30 = 90 < 100 → SW2 抢占成为 Master
```

> ⚠️ **未配 track 是 VRRP 最高频的故障**："主设备没问题，业务却全断了"。

### 13_2.4 负载分担（双主模式）
创建两个 VRRP 组，奇数 VLAN 主在 SW1，偶数 VLAN 主在 SW2：

```latex
# SW1
[SW1-Vlanif10] vrrp vrid 10 virtual-ip 192.168.10.254
[SW1-Vlanif10] vrrp vrid 10 priority 120                    # VLAN 10 的 Master
[SW1-Vlanif20] vrrp vrid 20 virtual-ip 192.168.20.254
[SW1-Vlanif20] vrrp vrid 20 priority 100                    # VLAN 20 的 Backup

# SW2（相反）
[SW2-Vlanif20] vrrp vrid 20 virtual-ip 192.168.20.254
[SW2-Vlanif20] vrrp vrid 20 priority 120
```

> 注意：**VRID 与 VLAN 一一对应**，不同 VLAN 用不同 VRID 区分。

### 13_2.5 VRRP 与 BFD 联动（亚秒切换）
```latex
[SW1] bfd
[SW1] bfd vrrp-to-sw2 bind peer-ip 192.168.10.2 source-ip 192.168.10.1
[SW1-bfd-session-vrrp-to-sw2] discriminator local 10
[SW1-bfd-session-vrrp-to-sw2] discriminator remote 20
[SW1-bfd-session-vrrp-to-sw2] min-tx-interval 100
[SW1-bfd-session-vrrp-to-sw2] min-rx-interval 100
[SW1-bfd-session-vrrp-to-sw2] commit
[SW1-bfd-session-vrrp-to-sw2] quit

[SW1] interface Vlanif 10
[SW1-Vlanif10] vrrp vrid 1 track bfd-session 10 reduced 30
```

> 默认 VRRP 检测时间约 3 秒；配 BFD（100 ms × 3）后可压到 **300 ms 以内**。

### 13_2.6 验证
```latex
[SW1] display vrrp                     # 详细状态
[SW1] display vrrp brief               # 摘要（★ 看 State 是 Master 还是 Backup）
[SW1] display vrrp statistics
```

输出要点：

```latex
Vlanif10 | Virtual Router 10
  State : Master
  Virtual IP : 192.168.10.254
  Master IP : 192.168.10.1
  PriorityRun : 120          ← 运行优先级
  PriorityConfig : 120       ← 配置优先级
  Preempt : YES   Delay Time : 20
  TimerRun : 1
  Track IF : GigabitEthernet0/0/24   Priority reduced : 30
```

### 13_2.7 VRRP 排错
| 现象 | 原因 | 处理 |
| --- | --- | --- |
| 两台都是 Master | 三层不通（VRRP 报文收不到）/ 虚拟 IP 不一致 / VRID 不一致 | `ping` 互连接口；核对 vrid 与 virtual-ip |
| 两台都是 Backup | 配置错误或认证不一致 | 检查配置 |
| 主切换慢 | 未配 BFD | 配 BFD 联动 |
| **Master 上行断了不切换** | **未配 track** | 补 `vrrp vrid x track interface` |
| 频繁主备震荡 | 链路质量差 / 未配抢占延迟 | 配 `preempt-mode timer delay` |
| 虚拟 IP ping 不通 | 虚拟 IP 被占用 | 确保虚拟 IP 未被其他设备使用 |

---

## 13_3 BFD 双向转发检测
### 13_3.1 原理与价值
BFD 提供**统一的、毫秒级的链路/邻居故障检测**，被静态路由、OSPF、IS-IS、BGP、VRRP、MPLS 等联动调用。

```latex
工作机制：两端周期性互发 BFD 控制报文
          连续 detect-multiplier 个报文未收到 → 判定 Down

检测时间 = min-rx-interval × detect-multiplier
默认：1000ms × 3 = 3 秒
最快可配：3.3ms × 3 ≈ 10ms（需设备支持）
```

### 13_3.2 会话建立方式
| 方式 | 特点 | 配置要点 |
| --- | --- | --- |
| **静态 BFD（手工指定标识符）** | 稳定可控 | 需配 local/remote discriminator 并 `commit` |
| **动态 BFD（auto）** | 由协议自动创建 | 协议下 `bfd all-interfaces enable` |
| **BFD Echo（单臂）** | 单端即可，对端无需支持 BFD | 需 `bfd echo-source-ip` |

### 13_3.3 静态 BFD 配置
```latex
# ============ 本端 ============
[SW-A] bfd
[SW-A] bfd to-swB bind peer-ip 10.1.1.2 source-ip 10.1.1.1
[SW-A-bfd-session-to-swB] discriminator local 10
[SW-A-bfd-session-to-swB] discriminator remote 20
[SW-A-bfd-session-to-swB] min-tx-interval 100
[SW-A-bfd-session-to-swB] min-rx-interval 100
[SW-A-bfd-session-to-swB] detect-multiplier 3
[SW-A-bfd-session-to-swB] commit                 # ★ 必须
[SW-A-bfd-session-to-swB] quit

# ============ 对端（local/remote 交叉） ============
[SW-B] bfd to-swA bind peer-ip 10.1.1.1 source-ip 10.1.1.2
[SW-B-bfd-session-to-swA] discriminator local 20
[SW-B-bfd-session-to-swA] discriminator remote 10
[SW-B-bfd-session-to-swA] commit
```

### 13_3.4 BFD 与各协议联动
```latex
# 静态路由
[SW-A] ip route-static 0.0.0.0 0 10.1.1.2 track bfd-session to-swB

# OSPF
[SW-ospf-1] bfd all-interfaces enable

# IS-IS
[SW-isis-1] bfd all-interfaces enable

# BGP
[SW-bgp] peer 10.1.1.2 bfd enable

# VRRP
[SW-Vlanif10] vrrp vrid 1 track bfd-session 10 reduced 30

# MPLS LSP（检测 LSP 连通性）
[SW] bfd lsp-tunnel bind mpls-te tunnel Tunnel0/0/1        # 静态绑定 TE 隧道
[SW] bfd lsp-tunnel bind ldp-lsp peer-ip 3.3.3.3           # 绑定 LDP LSP
[SW-bfd-lsp-session] discriminator local 30
[SW-bfd-lsp-session] discriminator remote 40
[SW-bfd-lsp-session] min-tx-interval 100
[SW-bfd-lsp-session] min-rx-interval 100
[SW-bfd-lsp-session] process-pst                            # ★ 允许 BFD 联动触发上层切换
[SW-bfd-lsp-session] commit
[SW-bfd-lsp-session] quit
```

### 13_3.5 验证与排错
```latex
[SW] display bfd session all                  # 会话状态（Up/Down）
[SW] display bfd session verbose
[SW] display bfd statistics
```

| 现象 | 原因 | 处理 |
| --- | --- | --- |
| 会话一直 Down | 未 `commit` | 补 `commit` |
| 会话 Down | local/remote discriminator 配反 | 两端交叉核对 |
| 会话 Down | 源/目 IP 不可达 | 先 `ping -a 源 目` |
| 联动不生效 | 路由未绑定 bfd-session | 检查 track 配置 |

---

## 13_4 其他可靠性技术
### 13_4.1 DLDP（单向链路检测）
**场景**：光纤收发接反或单根光纤断裂 → 本端能收、对端收不到 → 二层协议认为链路正常 → 产生单向流量黑洞。DLDP 专门检测这类"单向链路"。

```latex
[SW] dldp enable
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] dldp enable
[SW-GigabitEthernet0/0/1] dldp interval 10        # 检测间隔
[SW] display dldp
```

### 13_4.2 接口备份
主接口故障时，备份接口顶上（常用于专线 + 4G/拨号备份）。

```latex
[SW] interface gigabitethernet 0/0/1               # 主接口
[SW-GigabitEthernet0/0/1] standby interface gigabitethernet 0/0/2
[SW-GigabitEthernet0/0/1] standby timer delay 10 10
```

### 13_4.3 智能链路（Smart Link，双上行快速切换）
双上行场景（接入交换机上联两台汇聚），Smart Link 提供**毫秒级**主备切换，比 STP 快得多。

```latex
[SW] smart-link group 1
[SW-smlk-group1] port gigabitethernet 0/0/1 master
[SW-smlk-group1] port gigabitethernet 0/0/2 slave
[SW-smlk-group1] flush send control-vlan 10        # 发 Flush 报文刷新上游 MAC
[SW-smlk-group1] quit
[SW] display smart-link group 1
```

### 13_4.4 FRR 快速重路由（IP FRR / LFA）
IGP 预先计算一条**无环备份下一跳**，故障时在路由重新收敛之前就切过去，实现 <50 ms 切换。

```latex
# OSPF IP FRR（自动计算无环备份下一跳，切换 <50ms）
[SW-ospf-1] frr
[SW-ospf-1-frr] loop-free-alternate

# 验证
[SW] display ospf routing                    # 看是否有备份下一跳（Backup NextHop）
```

> **FRR 与 BFD 的分工**：FRR 解决"**我**这跳故障立刻绕行"（本地保护，<50 ms）；BFD + 路由收敛解决"全网重新算路"（秒级到亚秒级）。两者互补，不是替代。

---

## 13_5 综合案例：园区网端到端可靠性设计
### 13_5.1 目标
```latex
双核心 + 双上行接入，要求：
第1步 单台核心故障：业务不中断
第2步 单条上行链路故障：毫秒级感知
第3步 上行出口中断：网关自动切换（不发生黑洞）
第4步 收敛可量化（有测试方法与目标值）
```

### 13_5.2 分层可靠性设计
| 层次 | 方案 | 目标切换时间 |
| --- | --- | --- |
| 设备级 | 核心双机（堆叠或 M-LAG） | 毫秒–秒级 |
| 链路级 | 接入双上行 Eth-Trunk / Smart Link | <50 ms（Smart Link） |
| 网关级 | VRRP + track 上行 + BFD 联动 | <1 秒 |
| 路由级 | OSPF + BFD 联动 | <1 秒 |
| 出口级 | 双出口 + NQA 探测 + 浮动路由 | 秒级 |
| 转发级 | OSPF FRR（LFA） | <50 ms |

### 13_5.3 关键配置片段
```latex
# 网关：VRRP + track 上行口 + BFD
[Core1-Vlanif10] vrrp vrid 10 virtual-ip 192.168.10.254
[Core1-Vlanif10] vrrp vrid 10 priority 120
[Core1-Vlanif10] vrrp vrid 10 track interface gigabitethernet 0/0/23 reduced 30
[Core1-Vlanif10] vrrp vrid 10 track bfd-session 10 reduced 30

# 路由：OSPF + BFD
[Core1-ospf-1] bfd all-interfaces enable
[Core1-ospf-1] frr
[Core1-ospf-1-frr] loop-free-alternate

# 出口：上行浮动路由 + BFD
[Core1] ip route-static 0.0.0.0 0 172.16.100.2 track bfd-session to-exit
[Core1] ip route-static 0.0.0.0 0 172.16.200.2 preference 100
```

### 13_5.4 切换时间测试方案
```latex
第1步 基准：ping -t 持续打流（Windows）或 ping -c 1000（设备侧）
第2步 断链路：shutdown 某条成员链路 → 记录丢包个数（×1s = 大概切换时间）
第3步 断设备：重启某台核心 → 记录丢包
第4步 断上行：shutdown 主上行 → 观察 VRRP 是否切换（display vrrp brief）
第5步 恢复：undo shutdown → 观察是否回切（抢占延迟是否生效）
```

**判定标准参考：**

| 场景 | 合格 | 优秀 |
| --- | --- | --- |
| 链路故障（Eth-Trunk 成员） | 丢 ≤1 包 | 不丢包 |
| 设备故障（VRRP + BFD） | <1 秒 | <300 ms |
| 路由收敛（OSPF + BFD） | <1 秒 | <500 ms |
| FRR 本地保护 | <50 ms | <50 ms |

> 把这些**实测数字写进实验记录**，论述题里引用自己的数据，说服力远超"很快""秒级"这类空话。

---

## 13_6 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 排查 | 常见根因 |
| --- | --- | --- |
| VRRP 双主 | `display vrrp brief`（两端） | 三层不通 / VRID 或虚拟 IP 不一致 |
| 主备不切换 | `display vrrp`（看 Track） | **未配 track** |
| 切换后仍黑洞 | 检查上行口与路由 | track 减的优先级不够（降到仍最高） |
| 切换太慢 | 是否配 BFD | 默认 3 秒，配 BFD 可 <1 秒 |
| 频繁震荡 | `display logbuffer` | 未配抢占延迟 / 链路质量差 |
| BFD 会话 Down | `display bfd session all` | 漏 `commit` / discriminator 配反 |
| 联动不生效 | 检查绑定 | 路由没 track bfd-session |
| 单向链路业务异常 | `display dldp` | 未开 DLDP |

---

## 13_7 场景笔记与验证
### 13_7.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **五层可靠性骨架** | 设备/链路/网关/路由/出口各由谁兜底 |
| **VRRP 参数卡** | 优先级默认 100、组播 224.0.0.18、虚拟 MAC 00-00-5E-00-01-{VRID} |
| **BFD 参数卡** | 检测时间 = min-rx-interval × detect-multiplier，默认 1000ms×3 |
| **坑本** | VRRP 未配 track；BFD 漏 commit；两端 discriminator 没交叉；抢占延迟忘配 |

### 13_7.2 验证三板斧（本板块版）
```latex
第1步 看状态：display vrrp brief（Master/Backup）、display bfd session all（Up）
第2步 看配置：display vrrp（Track 项在不在）、display current-configuration | include bfd
第3步 打流量：ping -t 持续打流 + 制造故障，数丢包个数
```

### 13_7.3 必须亲手做一次的测试
**"断一根线，数丢几个包"**。这个动作把抽象的"可靠性"变成了数字。把每次测得的丢包数记在实验记录里，考前翻一遍，论述题就有料。

---

## 13_8 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | VRRP 优先级越小越优 | **越大越优**（默认 100），与 STP cost 相反 |
| 2 | VRRP 上行断了会自动切 | **不会**，必须配 `track` |
| 3 | 抢占立即生效 | 配 `preempt-mode timer delay` 可防震荡（生产建议配） |
| 4 | BFD 配完就生效 | 静态 BFD 必须 `commit` |
| 5 | BFD 两端配置相同 | local/remote discriminator 必须**交叉** |
| 6 | FRR 和 BFD 二选一 | **互补**：FRR 本地 <50 ms，BFD 驱动全网收敛 |
| 7 | 堆叠不需要 VRRP | 堆叠内部无需 VRRP；但**跨堆叠/U 型组网仍需要** |
| 8 | 可靠性只靠设备双机 | 冗余 + 检测 + 切换**三件事缺一不可** |

---

# 板块14 · QoS 与流量管理
> 定位：网络拥塞时"让谁先过"的艺术。HCIP 要求掌握 MQC 模型与常见队列机制；HCIE 要求能设计端到端 QoS 方案（分类/标记/限速/拥塞管理/拥塞避免）并计算带宽参数。
> 核心模型：**分类（Classifier）→ 行为（Behavior）→ 策略（Policy）→ 应用（Apply）**，华为称为 MQC（模块化 QoS 命令行）。

## 14_1 QoS 基础
### 14_1.1 网络质量的四个指标
| 指标 | 含义 | 典型要求 |
| --- | --- | --- |
| **带宽** | 单位时间传输量 | 语音 64–128 kbps/路 |
| **时延** | 端到端传输时间 | 语音 <150 ms，视频 <400 ms |
| **抖动** | 时延变化 | 语音 <30 ms |
| **丢包率** | 丢失比例 | 语音 <1% |

### 14_1.2 四种 QoS 服务模型
| 模型 | 原理 | 是否需预留资源 | 应用 |
| --- | --- | --- | --- |
| **Best-Effort** | 尽力而为，不做任何保证 | 否 | 默认 |
| **IntServ** | 每条流预留资源（RSVP） | 是 | 扩展性差，基本不用 |
| **DiffServ**（主流） | **按类区分服务**，每类统一处理 | 否（按类调度） | 现网主流 |

### 14_1.3 QoS 处理流程
```latex
报文进入 → 分类/标记 → 流量监管(CAR)/整形(Shaping) → 拥塞避免(WRED) → 拥塞管理(队列调度) → 发出
            ↑               ↑                          ↑                    ↑
         打优先级        限速/丢包                 拥塞前丢包            拥塞时排队
```

### 14_1.4 优先级映射（必须掌握）
**二层 802.1p（CoS，3 bit，0–7）：**

| 值 | 业务 | 队列 |
| --- | --- | --- |
| 0 | BE（尽力而为，默认） | 0 |
| 1 | AF1 | 1 |
| 2 | AF2 | 2 |
| 3 | AF3 | 3 |
| 4 | AF4 | 4 |
| 5 | **EF（语音）** | 5 |
| 6 | CS6（路由协议） | 6 |
| 7 | CS7 | 7 |

**三层 DSCP（6 bit，0–63）常见取值：**

| DSCP 名称 | 值 | 业务 |
| --- | --- | --- |
| **EF** | 46 | **语音**（低时延低丢包） |
| **AF41/AF42/AF43** | 34/36/38 | 视频会议 |
| **AF31/AF32/AF33** | 26/28/30 | 关键业务 |
| **AF21/AF22/AF23** | 18/20/22 | 普通业务 |
| **AF11/AF12/AF13** | 10/12/14 | 批量业务 |
| **BE（CS0）** | 0 | 尽力而为 |

> **记忆技巧**：`AFxy` 中 x = 类别（越大越重要），y = 丢弃概率（越大越先丢）。

**信任模式配置：**

```latex
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] trust dscp              # 信任 DSCP（推荐三层网络）
[SW-GigabitEthernet0/0/1] trust 8021p             # 信任 802.1p（二层网络）
[SW-GigabitEthernet0/0/1] trust upstream default  # 信任上行设备
```

> ⚠️ 接入交换机**默认不信任**终端报文的优先级（会全部置 0）。接 IP 电话的端口需要 `trust 8021p` 或 `trust dscp`，否则语音优先级被抹掉——**这是语音质量差却查不出原因的经典陷阱**。

---

## 14_2 MQC 配置模型
### 14_2.1 四步流程
```latex
第1步 traffic classifier   定义"哪些报文"（分类）
第2步 traffic behavior     定义"怎么处理"（行为）
第3步 qos policy           把第1步和第2步绑定（策略）
第4步 qos apply policy     应用到接口/全局（应用）
```

### 14_2.2 完整配置示例
```latex
# ================= 第1步 分类器 =================
[SW] traffic classifier VOICE
[SW-classifier-VOICE] if-match dscp ef                     # 匹配语音（DSCP 46）
[SW] traffic classifier VIDEO
[SW-classifier-VIDEO] if-match dscp af41                   # 匹配视频（DSCP 34）
[SW] traffic classifier DATA
[SW-classifier-DATA] if-match acl 3001                     # 也可匹配 ACL

# ================= 第2步 流行为 =================
[SW] traffic behavior BE-VOICE
[SW-behavior-BE-VOICE] queue llq                           # 低时延队列（优先转发）
[SW] traffic behavior BE-VIDEO
[SW-behavior-BE-VIDEO] queue af bandwidth pct 30           # 保证 30% 带宽
[SW] traffic behavior BE-DATA
[SW-behavior-BE-DATA] car cir 1024 cbs 2048                # 限速 1 Mbps

# ================= 第3步 策略 =================
[SW] qos policy QOS-CAMPUS
[SW-qos-policy-QOS-CAMPUS] classifier VOICE behavior BE-VOICE
[SW-qos-policy-QOS-CAMPUS] classifier VIDEO behavior BE-VIDEO
[SW-qos-policy-QOS-CAMPUS] classifier DATA behavior BE-DATA

# ================= 第4步 应用 =================
[SW] interface gigabitethernet 0/0/1
[SW-GigabitEthernet0/0/1] qos apply policy QOS-CAMPUS inbound
```

### 14_2.3 分类器匹配条件汇总
```latex
if-match acl 3001                    # 匹配 ACL
if-match dscp ef / af41 / 46         # 匹配 DSCP
if-match 8021p 5                     # 匹配 802.1p
if-match ip-precedence 5             # 匹配 IP 优先级
if-match vlan-id 10                  # 匹配 VLAN
if-match source-mac 0001-0002-0003   # 匹配源 MAC
if-match any                         # 匹配所有（用于默认类）
if-match protocol ip / ipv6
if-match l2-protocol arp
```

> 一个 classifier 中多条 `if-match` 时，默认**与（AND）关系**；可用 `if-match operator or` 改为"或"。

### 14_2.4 验证
```latex
[SW] display qos policy interface g0/0/1          # 接口上的策略与统计（★）
[SW] display traffic classifier user-defined
[SW] display traffic behavior user-defined
[SW] display qos policy user-defined
[SW] display qos queue statistics interface g0/0/1   # 各队列统计
```

---

## 14_3 限速：CAR 与流量整形
### 14_3.1 三种限速机制对比
| 机制 | 方向 | 超限时动作 | 是否缓存 | 应用 |
| --- | --- | --- | --- | --- |
| **CAR（监管）** | 入/出 | **直接丢弃** | 否 | 接入限速、运营商对用户限速 |
| **流量整形（Shaping）** | 出 | **缓存后匀速发送** | 是（队列） | 出口带宽适配（如 1G 口接 100M 专线） |
| **接口限速（qos lr）** | 出 | 丢弃 | 否 | 端口整体限速 |

### 14_3.2 令牌桶参数
```latex
CIR（Committed Information Rate）    承诺信息速率（kbps）
CBS（Committed Burst Size）          承诺突发尺寸（byte）
PIR（Peak Information Rate）         峰值信息速率（kbps）
PBS（Peak Burst Size）               峰值突发尺寸（byte）
```

**双令牌桶三色标记：**

```latex
        CIR/CBS 桶        PIR/PBS 桶        结果
报文 ≤  CIR          有令牌              —          绿色（pass）
CIR < 报文 ≤ PIR     无令牌            有令牌        黄色（pass，可能被优先丢弃）
报文 > PIR           无令牌            无令牌        红色（丢弃）
```

### 14_3.3 配置
```latex
# 第1步 接口限速（出方向 2 Mbps）
[SW-GigabitEthernet0/0/2] qos lr outbound cir 2000 cbs 20000

# 第2步 CAR（在流行为中）
[SW] traffic behavior BE-LIMIT
[SW-behavior-BE-LIMIT] car cir 1024 cbs 2048 pbs 4096 green pass yellow pass red discard

# 第3步 流量整形（出接口适配上游带宽）
[SW-GigabitEthernet0/0/24] qos queue 0 shaping cir 100000
```

**CBS 经验取值：**

```latex
CBS ≈ CIR(kbps) × 1000 / 8 × 突发时长(秒)
示例：CIR = 2000 kbps，允许 100ms 突发
     CBS = 2000 × 1000 / 8 × 0.1 = 25000 byte
```

---

## 14_4 拥塞管理与拥塞避免
### 14_4.1 队列调度机制
| 机制 | 原理 | 特点 |
| --- | --- | --- |
| **FIFO** | 先进先出 | 无差别，拥塞时谁先到谁先走 |
| **PQ（严格优先级）** | 高优先级队列清空才轮到低优先级 | 低优先级可能"饿死" |
| **WRR（加权轮询）** | 按权重轮流调度 | 无法保证时延 |
| **DRR** | 按字节数加权轮询 | 更公平 |
| **WFQ** | 按流加权公平 | 自动按流分配 |
| **PQ+WFQ/WRR 混合**（推荐） | 语音用 PQ，其余用 WRR | **兼顾时延与公平** |
| **LLQ（低时延队列）** | PQ + 限速（防饿死） | **语音最佳选择** |

### 14_4.2 队列配置
```latex
[SW] qos queue-profile CAMPUS-Q
[SW-qos-queue-profile-CAMPUS-Q] queue 5 weight 20            # WRR 权重
[SW-qos-queue-profile-CAMPUS-Q] queue 5 pq                   # 或配置为严格优先级
[SW-qos-queue-profile-CAMPUS-Q] queue 5 length 100           # 队列长度
[SW] interface gigabitethernet 0/0/24
[SW-GigabitEthernet0/0/24] qos queue-profile CAMPUS-Q
```

### 14_4.3 拥塞避免（WRED）
**为什么需要**：TCP 全局同步——多个 TCP 流同时丢包 → 同时降速 → 同时回升，带宽利用率锯齿状波动。WRED 通过**随机早期丢弃**让不同流在不同时刻丢包，避免同步。

```latex
[SW] drop-profile DP-AF
[SW-drop-profile-DP-AF] wred dscp
[SW-drop-profile-DP-AF] dscp af21 low-limit 30 high-limit 80 discard-percentage 10
[SW] qos queue-profile CAMPUS-Q
[SW-qos-queue-profile-CAMPUS-Q] queue 2 drop-profile DP-AF
```

> **关键点**：WRED 只对**TCP 有效**（UDP 不降速）。语音（UDP）应放在 LLQ，而不是靠 WRED。

---

## 14_5 典型场景：企业 QoS 方案设计
### 14_5.1 业务分级
| 业务 | 标记 | 队列 | 保障方式 |
| --- | --- | --- | --- |
| 语音 | **EF（46）** | 5 | **LLQ**（优先 + 限速） |
| 视频会议 | AF41（34） | 4 | AF 保证 30% 带宽 |
| 关键业务（ERP/生产） | AF31（26） | 3 | AF 保证 20% 带宽 |
| 普通办公 | AF21第18步 | 2 | WRR + WRED |
| 批量/下载 | BE（0） | 0 | **CAR 限速**（防止吃满带宽） |

### 14_5.2 完整配置
```latex
# ============ 分类器 ============
[SW] traffic classifier C-VOICE
[SW-classifier-C-VOICE] if-match dscp ef
[SW] traffic classifier C-VIDEO
[SW-classifier-C-VIDEO] if-match dscp af41
[SW] traffic classifier C-KEY
[SW-classifier-C-KEY] if-match dscp af31
[SW] traffic classifier C-BULK
[SW-classifier-C-BULK] if-match acl 3001

# ============ 行为 ============
[SW] traffic behavior B-VOICE
[SW-behavior-B-VOICE] queue llq bandwidth pct 10
[SW] traffic behavior B-VIDEO
[SW-behavior-B-VIDEO] queue af bandwidth pct 30
[SW] traffic behavior B-KEY
[SW-behavior-B-KEY] queue af bandwidth pct 20
[SW] traffic behavior B-BULK
[SW-behavior-B-BULK] car cir 2048 cbs 4096

# ============ 策略 ============
[SW] qos policy P-CAMPUS
[SW-qos-policy-P-CAMPUS] classifier C-VOICE behavior B-VOICE
[SW-qos-policy-P-CAMPUS] classifier C-VIDEO behavior B-VIDEO
[SW-qos-policy-P-CAMPUS] classifier C-KEY behavior B-KEY
[SW-qos-policy-P-CAMPUS] classifier C-BULK behavior B-BULK

# ============ 应用（上行口出方向，拥塞发生地）============
[SW] interface gigabitethernet 0/0/24
[SW-GigabitEthernet0/0/24] qos apply policy P-CAMPUS outbound
```

### 14_5.3 接入侧标记（如果终端不可信）
```latex
# 接 IP 电话的端口：按 VLAN 打标记（语音 VLAN 40）
[SW] traffic classifier C-MARK-VOICE
[SW-classifier-C-MARK-VOICE] if-match vlan-id 40
[SW] traffic behavior B-MARK-VOICE
[SW-behavior-B-MARK-VOICE] remark dscp ef
[SW] qos policy P-MARK
[SW-qos-policy-P-MARK] classifier C-MARK-VOICE behavior B-MARK-VOICE
[SW-GigabitEthernet0/0/1] qos apply policy P-MARK inbound
```

### 14_5.4 验证与测试
```latex
[SW] display qos policy interface g0/0/24         # 看各分类的匹配计数
[SW] display qos queue statistics interface g0/0/24   # 各队列的丢包/通过统计
```

**效果测试方法：**

| 方法 | 做法 |
| --- | --- |
| 拥塞模拟 | 用大流量工具（iperf）打满上行，同时打语音电话，观察是否清晰 |
| 计数验证 | 看 VOICE 分类器的 Matched 计数是否增长（说明分类生效） |
| 丢包验证 | 拥塞时看 BE 队列有丢包、LLQ 队列**无丢包** |

---

### 14_5.5 案例：视频会议一卡，全公司都知道
> 某公司每天上午 10 点开全员视频会议，一到点画面就卡成 PPT，IT 被投诉了大半年。带宽从 100M 升到 500M，还是卡。
> 现场抓包 + 看队列统计，真相是：**不是带宽不够，是排队错了**。
> 会议流量和同事们的下载、备份、云同步挤在同一个队列里（默认 BE 队列，FIFO）。10 点整几百人同时开视频，正好撞上早间备份任务的大象流，队列一拥塞，语音视频这类**对时延敏感的小包**就在大包后面排队——几百毫秒的排队时延，画面自然就卡了。
> 三步改造：  
第1步 **分类**：视频终端的流量打 DSCP AF41（或在接入侧按 VLAN 重标记）；  
第2步 **调度**：视频进 AF 队列保证 30% 带宽，语音进 **LLQ**（低时延队列）优先转发；  
第3步 **限制**：给备份/下载类流量配 CAR 限速，别让它无限吃带宽。
> 改造后带宽还是 500M，画面再没卡过。
> 这个案例说明一件事：**QoS 不是"加带宽"，是"排队排得对"**。带宽决定能跑多快，QoS 决定谁先跑。

## 14_6 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 排查 | 常见根因 |
| --- | --- | --- |
| QoS 配了没效果 | `display qos policy interface`（看计数） | 应用方向错（应在**出方向**）/ 策略未应用到拥塞点 |
| 语音优先级被抹掉 | 检查接入端口 trust | 未配 `trust 8021p/dscp` |
| 语音卡顿但带宽够 | 检查队列 | 语音没进 LLQ，和普通数据抢同一个队列 |
| 限速不生效 | 检查 car 参数单位 | CIR 单位是 **kbps** |
| 低优先级业务完全不通 | 检查是否用了纯 PQ | 高优先级队列吃满带宽 → 低优先级**饿死**，应配 LLQ/WRR |
| TCP 吞吐上不去 | 是否缺 WRED | 全局同步导致锯齿，配 WRED 改善 |
| 匹配计数不涨 | 分类器条件写错 | dscp 值与报文实际标记不符（先抓包确认） |

---

## 14_7 场景笔记与验证
### 14_7.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **DSCP 速查卡** | EF 46（语音）、AF41 34（视频）、AF31 26（关键业务）、BE 0 |
| **MQC 四步模板** | classifier → behavior → policy → apply（存成模板） |
| **机制选型卡** | 语音 LLQ、关键业务 AF、批量 CAR、出口整形、TCP 用 WRED |
| **坑本** | 策略应用在入方向（应在出方向）；CAR 单位 kbps；接入侧忘配 trust |

### 14_7.2 验证三板斧（本板块版）
```latex
第1步 看配置：display qos policy interface g0/0/24（策略在不在方向对不对）
第2步 看计数：同一命令里的 Matched（分类命中了吗）
第3步 打流量：制造拥塞（大流量打满），看队列统计中 LLQ 是否零丢包
```

### 14_7.3 建议做一次的 QoS 效果实验
用两台 PC + iperf 打满链路（模拟拥塞），对比：

1. **不做 QoS**：语音/视频卡顿，ping 时延飙到几百 ms；
2. **做了 QoS（语音 LLQ）**：ping 时延仍稳定在几 ms。

**亲手测过一次，你就知道 QoS 不是玄学。**

---

## 14_8 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | QoS 是提速技术 | 它是**拥塞时的调度策略**，不增加带宽 |
| 2 | 策略配在入方向 | 拥塞发生在**出方向**，调度策略应应用在出接口 |
| 3 | 接入侧不用管标记 | 默认**不信任终端优先级**，需 `trust` 或接入侧 remark |
| 4 | 语音用纯 PQ 最好 | 纯 PQ 会让低优先级**饿死**，应用 **LLQ**（PQ + 限速） |
| 5 | CAR 会缓存报文 | CAR 直接丢；**整形**才缓存 |
| 6 | WRED 对所有流量有效 | 只对 **TCP 有效**（UDP 不会因丢包降速） |
| 7 | CAR 单位 Mbps | 单位是 **kbps** |
| 8 | DSCP AF41 值记不住 | AF41 = **34**（AF4x：x=1→34, 2→36, 3→38） |

---

# 板块15 · 组播与 IPv6 技术
> 定位：组播是视频、会议、金融行情的刚需，IPv6 是必经之路。HCIP 要求掌握 IGMP Snooping 与 PIM 基础；HCIE 要求能设计园区组播方案（SSM/ASM、RP 部署）与 IPv6 过渡方案（双栈/隧道/翻译）。
> 组播的核心命题只有一句：**一份数据，只发给"想看的人"，且每条链路只传一份。**  
IPv6 的核心命题也只有一句：**地址够用了，但过渡期的共存问题才是真正的考题。**

## 15_1 组播基础
### 15_1.1 三种通信方式
| 方式 | 地址范围 | 特点 |
| --- | --- | --- |
| 单播 | A/B/C 类 | 一对一，N 个接收者 = N 份流量 |
| **广播** | 255.255.255.255 / 子网广播 | 一对所有，**无法跨三层** |
| **组播** | 224.0.0.0 – 239.255.255.255 | **一对一组接收者**，每条链路只传一份 |

组播的价值用一句话说清：**100 个人看同一路 4 Mbps 视频，单播要占 400 Mbps，组播只占 4 Mbps。**

```latex
                    单播（Unicast）                     组播（Multicast）
              每来一个接收者复制一份                    沿途只复制一次

   源 ────▶ R1 ────▶ R2 ──┬──▶ 接收者1              源 ────▶ R1 ────▶ R2 ──┬──▶ 接收者1
                          ├──▶ 接收者2                                    ├──▶ 接收者2
                          └──▶ 接收者3                                    └──▶ 接收者3
          链路流量 = 3 份                                    链路流量 = 1 份
```

### 15_1.2 组播地址空间
| 范围 | 用途 |
| --- | --- |
| 224.0.0.0–224.0.0.255 | **永久组播地址（协议保留）**，TTL=1，路由器不转发 |
| 224.0.1.0–231.255.255.255 | 用户组播地址（ASM） |
| 232.0.0.0–232.255.255.255 | **SSM 专用**（源特定组播） |
| 233.0.0.0–238.255.255.255 | GLOP 地址 |
| 239.0.0.0–239.255.255.255 | **私有组播地址（管理域内）**，企业自用首选 |

**必须背下来的保留地址：**

| 地址 | 用途 |
| --- | --- |
| 224.0.0.1 | 所有主机 |
| 224.0.0.2 | 所有路由器 |
| 224.0.0.5 | 所有 OSPF 路由器 |
| 224.0.0.6 | OSPF DR/BDR |
| 224.0.0.9 | RIPv2 |
| 224.0.0.13 | PIM |
| 224.0.0.18 | VRRP |
| 224.0.0.22 | IGMPv3 |

> 排错冷知识：如果你在某条链路上抓到大量 224.0.0.5 / 224.0.0.18 的报文，说明 OSPF 或 VRRP 正在工作；如果抓到 224.0.0.2 但有设备不响应，先查路由器是不是被 ACL 拦了组播。

### 15_1.3 组播 MAC 映射与"32 对 1"陷阱
```latex
IPv4 组播 MAC = 01-00-5E-0（高 25 位固定） + IP 地址低 23 位

例：224.1.1.1
  IP 低 23 位 = 000 0001 . 0000 0001 . 0000 0001
  MAC        = 01-00-5E-01-01-01
```

映射缺陷：IPv4 组播地址有 **28 位可变**，MAC 只映射了 **23 位**，高 5 位丢失 → **32 个组播 IP 映射到同一个 MAC**。

```latex
224.1.1.1  ┐
225.1.1.1  ├─ 全部映射到 01-00-5E-01-01-01
226.1.1.1  │
  ...      │
239.1.1.1  ┘
```

> ⚠️ 这就是"两个组播频道同时开，画面互相干扰/解码失败"的根源。规划组播业务时，**务必让同一网络中同时使用的组播地址低 23 位互不相同**（例如一个用 239.1.1.1，另一个改用 239.1.1.33）。

### 15_1.4 分发树：SPT vs RPT
| 类型 | 全称 | 结构 | 适用 |
| --- | --- | --- | --- |
| **SPT（最短路径树）** | Shortest Path Tree | 以**源**为根 | 源少、流量大 |
| **RPT（共享树）** | Rendezvous Point Tree | 以 **RP** 为根 | 源多、流量小（ASM 模式） |

```latex
        RPT（共享树，先到 RP 再转）          SPT（最短路径树，直奔源）

         [RP]                                 源 ───────────▶ 接收者
        ╱  │  ╲                               │              ▲
      ╱    │    ╲                             └──▶ 接收者 ────┘
   源1   源2    接收者                        各自走单播最短路径
   （所有源都先汇到 RP）
```

PIM-SM 的实际行为是：**先走 RPT 找到源，再按需切换到 SPT**（RPT→SPT 切换），兼顾了收敛与效率。

---

## 15_2 IGMP（主机 ↔ 路由器）
### 15_2.1 三个版本
| 版本 | 加入 | 离开 | 特定源 | 说明 |
| --- | --- | --- | --- | --- |
| **IGMPv1** | 加入报文 | 静默离开（超时） | 不支持 | 基本淘汰 |
| **IGMPv2**（最常用） | 加入报文 | **Leave 报文**（快速离开） | 不支持 | 主流 |
| **IGMPv3** | 加入报文 | Leave | **支持（SSM 必需）** | 源特定组播 |

### 15_2.2 配置与查询器
```latex
[SW] multicast routing-enable                      # 全局开启组播路由（三层设备）
[SW] interface Vlanif 10
[SW-Vlanif10] igmp enable
[SW-Vlanif10] igmp version 2                       # 指定版本（默认 v2）
[SW-Vlanif10] igmp host-tracking                   # 记录主机成员（可选）
[SW-Vlanif10] quit
```

**查询器（Querier）选举**：同网段多台路由器时，**IP 地址最小者**成为查询器，负责周期性发 Query 维护组成员。

```latex
[SW-Vlanif10] igmp querier-timeout 255             # 查询器失效超时
```

> ⚠️ 如果网段里一台三层设备都没开 IGMP，也没有 Snooping 查询器，那么 IGMP Snooping 的"路由器端口"永远学不到，二层组播转发表为空，组播会退化成广播泛洪——这是"开了 Snooping 却没效果"的头号原因。

### 15_2.3 验证
```latex
[SW] display igmp interface Vlanif 10              # 接口 IGMP 状态与版本
[SW] display igmp group                            # 组播组成员（★ 看谁在收看）
[SW] display igmp routing-table                    # IGMP 路由表
```

---

## 15_3 IGMP Snooping（二层交换机必配）
### 15_3.1 为什么需要
二层交换机默认把组播当广播泛洪 → 所有端口都收到视频流，带宽被吃光，会议室的摄像头把整个接入层拖垮。

IGMP Snooping 让交换机**偷听 IGMP 报文**，建立"组播 MAC ↔ 端口"表，只把组播转发给**真正有接收者的端口**。

```latex
未开 Snooping：              开了 Snooping：
  组播流 ──▶ 交换机 ──▶ 所有端口        组播流 ──▶ 交换机 ──▶ 仅成员端口
             （泛洪，浪费带宽）                      （精准投递）
```

### 15_3.2 配置
```latex
[SW] igmp-snooping enable                          # 全局开启
[SW] vlan 10
[SW-vlan10] igmp-snooping enable
[SW-vlan10] igmp-snooping querier enable           # 无三层设备时，交换机充当查询器
[SW-vlan10] igmp-snooping report-suppression       # 报告抑制（减少报文）
[SW-vlan10] quit

# 静态路由器端口（连接组播路由器的口必须正确识别）
[SW] interface gigabitethernet 0/0/24
[SW-GigabitEthernet0/0/24] igmp-snooping static-router-port vlan 10
```

### 15_3.3 验证
```latex
[SW] display igmp-snooping                             # 全局配置
[SW] display igmp-snooping vlan 10                     # VLAN 级
[SW] display l2-multicast forwarding-table vlan 10     # ★ 二层组播转发表
[SW] display igmp-snooping port-info                   # 端口角色
[SW] display igmp-snooping router-port vlan 10         # 路由器端口
```

> 排查要点：若二层组播转发表为空，按此顺序查 → 第1步 该 VLAN 是否开了 Snooping；第2步 是否有查询器（决定路由器端口能否学到）；第3步 接收者是否真的发了 IGMP Report。

---

## 15_4 PIM（路由器 ↔ 路由器）
### 15_4.1 三种模式选型
| 模式 | 全称 | 特点 | 适用 |
| --- | --- | --- | --- |
| **PIM-DM** | Dense Mode | 推（Push）：先泛洪再剪枝 | 接收者密集，小型网络 |
| **PIM-SM** | Sparse Mode | 拉（Pull）：显式加入，需要 RP | **主流**（接收者分散） |
| **PIM-SSM** | Source-Specific | 指定源，无需 RP（配合 IGMPv3） | 视频直播、单点源 |

> 选型口诀：**源固定、接收者只订阅不发布 → 直接用 SSM**，省掉 RP 这一整套复杂度；**源不固定（如多人会议）→ PIM-SM + RP**。

### 15_4.2 PIM-SM + 静态 RP 配置
```latex
# ============ 所有组播路由器 ============
[Router] multicast routing-enable
[Router] pim
[Router-pim] static-rp 2.2.2.2                     # 静态 RP 地址（全网必须一致）
[Router-pim] quit

# 在所有组播网络接口上使能 PIM-SM
[Router] interface gigabitethernet 0/0/1
[Router-GigabitEthernet0/0/1] pim sm
[Router-GigabitEthernet0/0/1] quit

# 接收者侧接口开 IGMP
[Router] interface gigabitethernet 0/0/2
[Router-GigabitEthernet0/0/2] pim sm
[Router-GigabitEthernet0/0/2] igmp enable
[Router-GigabitEthernet0/0/2] quit
```

> ⚠️ **静态 RP 的铁律**：全网每一台组播路由器的 `static-rp` 地址必须完全一致。只要有一台写错或漏配，该设备就无法建立 RPT，表现为"有的网段收得到，有的网段收不到"。

### 15_4.3 BSR 动态 RP（规模化推荐）
```latex
# C-BSR（候选自举路由器）
[Router-pim] c-bsr gigabitethernet 0/0/1 hash-length 30 priority 10

# C-RP（候选汇聚点）
[Router-pim] c-rp gigabitethernet 0/0/1 group-policy 2000 priority 10
[Router] acl 2000
[Router-acl-basic-2000] rule permit source 239.0.0.0 0.255.255.255
```

BSR 的好处：RP 信息由协议自动扩散，新增设备不用逐台改 `static-rp`，还能配 C-BSR/C-RP 冗余。

### 15_4.4 PIM-SSM 配置（单点源直播首选）
```latex
[Router] pim
[Router-pim] ssm-policy 2001                        # 指定 SSM 组范围
[Router-pim] quit
[Router] acl 2001
[Router-acl-basic-2001] rule permit source 232.0.0.0 0.255.255.255
[Router-acl-basic-2001] quit

# 接收者侧接口必须 IGMPv3
[Router-GigabitEthernet0/0/2] igmp version 3
```

### 15_4.5 验证与 RPF（组播排错的核心）
```latex
[Router] display pim interface                      # 使能 PIM 的接口
[Router] display pim neighbor                       # PIM 邻居（★ 先看这个）
[Router] display pim routing-table                  # 组播路由表（(S,G) 与 (*,G)）
[Router] display pim rp-info                        # RP 信息
[Router] display pim bsr-info                       # BSR 信息
[Router] display multicast routing-table
[Router] display multicast rpf-info 10.1.1.1        # ★ RPF 检查
```

**RPF（反向路径转发）检查**：路由器收到组播报文后，查"去往源的单播路由"，若**接收接口 ≠ RPF 接口则直接丢弃**。这是组播防环的核心，也是"配置全对却收不到流"的第一嫌疑。

```latex
          接收接口 g0/0/1
  源 ─────────────────────▶ 路由器
                              │
              RPF 检查：去往源的单播路由出接口是 g0/0/2
              → 接口不一致 → 丢弃（组播静默失败）
```

### 15_4.6 组播排错表
| 现象 | 原因 | 处理 |
| --- | --- | --- |
| 接收者收不到流 | IGMP 未加入 / 无 Snooping 表 | `display igmp group` |
| 有 (*,G) 无 (S,G) | RP 到源的注册失败 | 查 RP 与源侧 DR |
| PIM 邻居起不来 | 接口未 `pim sm` / 单播路由不通 | 查接口与 IGP |
| 组播断断续续 | **RPF 失败** / 环路 | `display multicast rpf-info` |
| 二层泛洪 | Snooping 未开或路由器端口识别错 | 配静态 router-port |
| 换频道要等很久 | IGMPv2 离开延迟 / 组播表老化 | 调 `igmp` 快速离开或缩短老化 |

---

## 15_5 IPv6 基础
### 15_5.1 地址格式与简写规则
```latex
IPv6 地址：128 bit，8 段，每段 4 个十六进制数

2001:0db8:0000:0000:0000:ff00:0042:8329
      │    └────┬─────┘    │
      │         │          └── 接口 ID（后 64 位）
      │         └── 可压缩为 ::
      └── 全球路由前缀（前 64 位）
```

**两条简写规则（必考）：**

1. 每段前导 0 可省略：`0db8` → `db8`、`0042` → `42`；
2. 连续的一段或多段全 0 可用 `::` 代替，但**全地址中只能出现一次**。

```latex
2001:0db8:0000:0000:0000:0000:0000:0001   →  2001:db8::1
fe80:0000:0000:0000:020c:29ff:fe1a:3b4c   →  fe80::20c:29ff:fe1a:3b4c
0000:0000:0000:0000:0000:0000:0000:0001   →  ::1（环回）
0000:0000:0000:0000:0000:0000:0000:0000   →  ::（未指定地址）
```

### 15_5.2 地址类型
| 类型 | 地址/前缀 | 说明 |
| --- | --- | --- |
| **全球单播** | 2000::/3 | 相当于 IPv4 公网地址 |
| **链路本地** | FE80::/10 | **自动生成**，仅本链路有效，必须记住它 |
| **唯一本地** | FC00::/7 | 相当于 IPv4 私网地址（10/8、192.168/16） |
| 环回 | ::1 | 本机 |
| 未指定 | :: | 尚未获取地址（如 DHCPv6 请求源） |
| **组播** | FF00::/8 | 替代广播，**IPv6 无广播** |
| 任播 | 单播地址空间 | 多个节点共用一个地址，路由到最近者 |

**组播中的两个特殊地址：**

```latex
FF02::1   链路本地范围的所有节点
FF02::2   链路本地范围的所有路由器
FF02::1:FFxx:xxxx  被请求节点组播地址（Solicited-Node，由单播地址后 24 位映射）
```

### 15_5.3 相对 IPv4 的关键改进
| 改进 | 说明 |
| --- | --- |
| 地址空间 | 128 bit，近乎无限，不再需要 NAT 缓解地址短缺 |
| 报头简化 | 固定 40 字节基本头，去掉校验和与分片字段，转发更快 |
| 扩展头 | 用链式扩展头实现可选功能，扩展性好 |
| 无广播 | 广播被组播彻底取代，消除广播风暴隐患 |
| 即插即用 | 支持 SLAAC（无状态自动配置），主机可自行生成地址 |
| 内置安全 | IPsec 原生支持 |
| NDP | 用 ICMPv6 邻居发现替代 ARP，安全性与功能性更强 |

### 15_5.4 NDP（邻居发现，替代 ARP）
NDP 用 **ICMPv6** 报文完成 IPv4 中 ARP、路由器发现、重定向三件事：

| 报文 | 类型 | 作用 |
| --- | --- | --- |
| **NS（Neighbor Solicitation）** | ICMPv6 135 | 请求对方的链路层地址（≈ ARP 请求） |
| **NA（Neighbor Advertisement）** | ICMPv6 136 | 回应自己的链路层地址（≈ ARP 应答） |
| **RS（Router Solicitation）** | ICMPv6 133 | 主机主动请求路由器发 RA |
| **RA（Router Advertisement）** | ICMPv6 134 | 路由器通告前缀，主机据此自动配置地址 |

```latex
[SW] display ipv6 neighbors                    # 查看 IPv6 邻居表（≈ display arp）
[SW] display ipv6 interface Vlanif 10          # 接口 IPv6 信息
[SW] display ipv6 routing-table                # IPv6 路由表
```

**DAD（重复地址检测）**：主机配置地址前先用 NS 探测该地址是否被占用，没有人应答才正式启用——这是 IPv6"即插即用"不撞地址的关键。

### 15_5.5 地址配置
```latex
[SW] ipv6                                       # 全局使能 IPv6（★ 第一步，别漏）
[SW] interface Vlanif 10
[SW-Vlanif10] ipv6 enable                       # 接口使能（会自动生成链路本地地址）
[SW-Vlanif10] ipv6 address 2001:db8:10::1 64    # 手工配置全球单播地址
[SW-Vlanif10] ipv6 address 2001:db8:10:: 64 eui-64    # EUI-64（用 MAC 生成接口 ID）
[SW-Vlanif10] ipv6 address auto link-local      # 自动生成链路本地地址
[SW-Vlanif10] quit
```

**RA 相关（无状态自动配置）：**

```latex
[SW-Vlanif10] undo ipv6 nd ra halt              # 允许发 RA（默认抑制）
[SW-Vlanif10] ipv6 nd ra prefix 2001:db8:10:: 64 2592000 604800
```

> ⚠️ **最常见的低级失误**：只配了 `ipv6 address` 却忘了全局 `ipv6`，系统直接提示不支持；或者配了地址但 `display ipv6 interface` 显示只有链路本地地址——八成是全局没开。

---

## 15_6 IPv6 路由协议
### 15_6.1 静态路由
```latex
[Router] ipv6 route-static 2001:db8:20:: 64 2001:db8:12::2
[Router] ipv6 route-static :: 0 2001:db8:12::2                 # IPv6 默认路由
[Router] ipv6 route-static 2001:db8:20:: 64 2001:db8:12::2 preference 100   # 浮动
```

### 15_6.2 OSPFv3
```latex
[Router] ospfv3 1
[Router-ospfv3-1] router-id 1.1.1.1             # ★ OSPFv3 仍需手工指定 Router ID
[Router-ospfv3-1] quit

[Router] interface gigabitethernet 0/0/1
[Router-GigabitEthernet0/0/1] ipv6 enable
[Router-GigabitEthernet0/0/1] ipv6 address 2001:db8:12::1 64
[Router-GigabitEthernet0/0/1] ospfv3 1 area 0   # ★ 在接口下使能，不在进程下 network
[Router-GigabitEthernet0/0/1] quit
```

> 与 OSPFv2 最大的两个区别：第1步 **在接口下使能**（不用 network 命令）；第2步 Router ID 仍是 **IPv4 格式**，且必须手工配（否则可能因无 IPv4 地址而无法启动）。

```latex
[Router] display ospfv3 peer
[Router] display ospfv3 routing
[Router] display ospfv3 lsdb
```

### 15_6.3 IS-IS for IPv6
```latex
[Router] isis 1
[Router-isis-1] network-entity 49.0001.0000.0000.0001.00
[Router-isis-1] ipv6 enable topology standard   # ★ 使能 IPv6 拓扑（默认是 IPv4 单拓扑）
[Router-isis-1] quit

[Router] interface gigabitethernet 0/0/1
[Router-GigabitEthernet0/0/1] ipv6 enable
[Router-GigabitEthernet0/0/1] ipv6 address 2001:db8:12::1 64
[Router-GigabitEthernet0/0/1] isis ipv6 enable 1
[Router-GigabitEthernet0/0/1] quit
```

### 15_6.4 BGP4+（MP-BGP for IPv6）
```latex
[Router] bgp 100
[Router-bgp] router-id 1.1.1.1
[Router-bgp] peer 2001:db8:12::2 as-number 200
[Router-bgp] ipv6-family unicast                # ★ 必须进 IPv6 地址族
[Router-bgp-af-ipv6] peer 2001:db8:12::2 enable
[Router-bgp-af-ipv6] network 2001:db8:100:: 64
[Router-bgp-af-ipv6] quit
```

```latex
[Router] display bgp ipv6 peer
[Router] display bgp ipv6 routing-table
[Router] display ipv6 routing-table protocol bgp
```

> 知识点联动：BGP4+ 的本质是 **MP-BGP 多协议扩展**，它复用 TCP 179 会话，通过地址族区分 IPv4/IPv6/VPNv4/EVPN——理解了板块8的 MP-BGP，这里只是换个地址族。

---

## 15_7 IPv6 过渡技术
### 15_7.1 三条路线
| 策略 | 代表技术 | 思路 | 适用场景 |
| --- | --- | --- | --- |
| **双栈** | IPv4 + IPv6 同时跑 | 终端与网络同时支持两种协议 | **首选**，改造目标态 |
| **隧道** | GRE、6to4、ISATAP | IPv6 报文封装在 IPv4 里穿越 | 孤岛互联、过渡期 |
| **翻译** | NAT64 / DNS64 | IPv6 与 IPv4 互译 | 纯 IPv6 终端访问 IPv4 资源 |

### 15_7.2 双栈（最简单、最推荐）
```latex
[SW] ipv6
[SW] interface Vlanif 10
[SW-Vlanif10] ip address 192.168.10.254 24
[SW-Vlanif10] ipv6 enable
[SW-Vlanif10] ipv6 address 2001:db8:10::1 64
[SW-Vlanif10] undo ipv6 nd ra halt
```

终端同时拿到 IPv4 与 IPv6 地址，**优先用 IPv6，回落 IPv4**。

### 15_7.3 GRE 隧道（IPv6 over IPv4）
```latex
[Router] interface tunnel 0/0/1
[Router-Tunnel0/0/1] tunnel-protocol gre
[Router-Tunnel0/0/1] source gigabitethernet 0/0/1      # 或指定 IPv4 源地址
[Router-Tunnel0/0/1] destination 202.100.1.2           # 对端 IPv4 地址
[Router-Tunnel0/0/1] ipv6 enable
[Router-Tunnel0/0/1] ipv6 address 2001:db8:ffff::1 64
[Router-Tunnel0/0/1] quit
```

### 15_7.4 6to4 自动隧道
```latex
[Router] interface tunnel 0/0/2
[Router-Tunnel0/0/2] tunnel-protocol ipv6-ipv4 6to4
[Router-Tunnel0/0/2] source 202.100.1.1
[Router-Tunnel0/0/2] ipv6 enable
[Router-Tunnel0/0/2] ipv6 address 2002:ca64:101::1 64   # 2002: + IPv4 的十六进制
[Router-Tunnel0/0/2] quit
[Router] ipv6 route-static 2002:: 16 tunnel 0/0/2       # 汇聚路由指向隧道
```

6to4 地址的特点：**前缀固定为 2002::/16，后 32 位由隧道源 IPv4 地址转换而来**（202.100.1.1 → ca64:0101）。

### 15_7.5 NAT64（IPv6 单栈访问 IPv4）
```latex
[Router] nat64 enable
[Router] interface gigabitethernet 0/0/2               # 连接 IPv6 网络的接口
[Router-GigabitEthernet0/0/2] nat64 enable
[Router-GigabitEthernet0/0/2] quit
[Router] nat64 prefix 64:ff9b:: 96                     # 公认 NAT64 前缀
```

> 现实中 NAT64 常与 **DNS64** 配合使用：DNS64 把解析到的 IPv4 地址合成一个 `64:ff9b::/96` 前缀的 IPv6 地址，终端以为对方是 IPv6，实际由 NAT64 网关做转换。

---

## 15_8 案例：监控组播改造与园区 IPv6 双栈
### 15_8.1 案例小故事
> 某园区新上了 200 路 4 Mbps 高清监控，架构组一开始没想太多，全部走单播：客户端一多，核心到汇聚的万兆链路直接打满，画面全是马赛克，保安部投诉"不如原来的模拟摄像头"。
> 排错时抓包一看：同一路摄像头的流，在核心上行口出现了 **30 份完全一样的 UDP 报文**——30 个客户端在看同一路画面，单播老老实实复制了 30 次。
> 改造三步走：第1步 摄像头与平台改用组播推流（239.x 私有组）；第2步 全网二层开 IGMP Snooping，三层跑 PIM-SM（RP 放在核心）；第3步 汇聚与核心之间开启三层组播，客户端侧 IGMPv2 加入。  
改造后同一条链路上每组只传 1 份，带宽从 800 Mbps 直降到 4 Mbps，马赛克消失。
> 半年后园区做 IPv6 改造，又遇到新问题：新办公区是 IPv6 单栈，访问不到的老业务系统（纯 IPv4）。最后用 **双栈 + NAT64/DNS64** 兜底，新业务走 IPv6，老业务由网关翻译。

### 15_8.2 需求与规划
| 项目 | 规划 |
| --- | --- |
| 监控组播组 | 239.10.1.0 – 239.10.1.255（私有组，低 23 位互不相同） |
| RP | 核心交换机 Loopback0：10.0.0.254 |
| 组播模式 | PIM-SM（静态 RP），接收者侧 IGMPv2 |
| 二层 | 全网 VLAN 开 IGMP Snooping |
| IPv6 前缀 | 2001:db8:10::/64（办公）、2001:db8:20::/64（监控） |
| IPv6 网关 | 与 IPv4 网关同一台核心，双栈 |

### 15_8.3 关键配置
```latex
# ================= 核心（RP） =================
[Core] multicast routing-enable
[Core] pim
[Core-pim] static-rp 10.0.0.254
[Core-pim] quit
[Core] interface LoopBack 0
[Core-LoopBack0] ip address 10.0.0.254 32
[Core-LoopBack0] pim sm
[Core-LoopBack0] quit
[Core] interface Vlanif 30
[Core-Vlanif30] pim sm                          # 组播源侧
[Core-Vlanif30] quit
[Core] interface Vlanif 10
[Core-Vlanif10] pim sm
[Core-Vlanif10] igmp enable                     # 接收者侧
[Core-Vlanif10] igmp version 2
[Core-Vlanif10] quit

# ================= 接入交换机（二层） =================
[ACC] igmp-snooping enable
[ACC] vlan 10
[ACC-vlan10] igmp-snooping enable
[ACC-vlan10] quit
[ACC] interface gigabitethernet 0/0/24
[ACC-GigabitEthernet0/0/24] igmp-snooping static-router-port vlan 10

# ================= IPv6 双栈网关 =================
[Core] ipv6
[Core] interface Vlanif 10
[Core-Vlanif10] ipv6 enable
[Core-Vlanif10] ipv6 address 2001:db8:10::1 64
[Core-Vlanif10] undo ipv6 nd ra halt
[Core-Vlanif10] quit
```

### 15_8.4 验收
```latex
# 第1步 组播源是否在 RP 注册
[Core] display pim rp-info
[Core] display pim routing-table                # 应看到 (*,G) 与 (S,G) 表项

# 第2步 接收者是否加入
[Core] display igmp group                       # 应看到客户端 IP 与组地址

# 第3步 二层有没有精准转发（关键：不是泛洪）
[ACC] display l2-multicast forwarding-table vlan 10

# 第4步 RPF 是否通过
[Core] display multicast rpf-info 10.10.30.5    # 源（摄像头）的 RPF 接口

# 第5步 IPv6 连通性
[Core] display ipv6 neighbors
[Core] ping ipv6 2001:db8:10::100
```

---

## 15_9 场景笔记与验证
### 15_9.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **组播地址卡** | 232/8 = SSM，239/8 = 私有，224.0.0.x = 协议保留（背 8 个常用） |
| **MAC 映射卡** | 01-00-5E-0 + 低 23 位；32 对 1 陷阱与规避方法 |
| **协议分层卡** | 主机↔路由器 = IGMP；二层交换机 = Snooping；路由器↔路由器 = PIM |
| **RPF 卡** | "接收接口 = 去往源的单播出接口"，否则丢弃 |
| **IPv6 简写规则** | 前导 0 省略 + `::` 只能出现一次 |
| **IPv6 地址类型卡** | 2000::/3 全球、FE80::/10 链路本地、FF00::/8 组播 |
| **坑本** | 忘了全局 `ipv6`；OSPFv3 在接口下使能；IS-IS 忘了 `ipv6 enable topology` |

### 15_9.2 验证三板斧（本板块版）
```latex
第1步 看成员：display igmp group（有人加入吗？加的是哪个组？）
第2步 看树：  display pim routing-table（有 (*,G) 吗？有 (S,G) 吗？）
第3步 看 RPF：display multicast rpf-info 源IP（RPF 接口是不是你以为的那个口？）
```

### 15_9.3 建议做一次的组播实验
用 eNSP 搭 2 台路由器 + 2 台交换机，跑 PIM-SM + IGMP Snooping，然后**故意制造两种故障**各练一次：

1. 把 RP 地址在一台路由器上写错 → 观察 `display pim routing-table` 只剩 (*,G) 而无 (S,G)；
2. 在接收者侧加一条指向错误接口的静态路由 → 触发 RPF 失败，`display multicast rpf-info` 显示接口不匹配，流量静默丢弃。

**亲手把这两个故障复现一遍，组播排错就再也不会抓瞎。**

---

## 15_10 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | 组播地址属于某一台主机 | 组播地址标识的是**一组接收者**，不是主机 |
| 2 | 224.0.0.x 可以跨网段 | 该段为协议保留，**TTL=1，路由器不转发** |
| 3 | 组播 MAC 一一对应 IP | 低 23 位映射，**32 个 IP 共用一个 MAC** |
| 4 | IGMP Snooping 自己会发查询 | 无三层设备时需配 `igmp-snooping querier enable` |
| 5 | PIM-SM 不需要 RP | SM 必须有 RP（静态或 BSR），**SSM 才不需要** |
| 6 | 静态 RP 只配一台就行 | **所有**组播路由器都要配且一致 |
| 7 | 组播不通先查 PIM | 先查 **RPF** 与单播路由是否通 |
| 8 | IPv6 可以写多个 `::` | 全地址中 `::` **只能出现一次** |
| 9 | IPv6 也有广播 | IPv6 **无广播**，全部用组播 |
| 10 | OSPFv3 用 network 宣告 | **在接口下 **`ospfv3 1 area 0` 使能 |
| 11 | IS-IS 开了就支持 IPv6 | 需 `ipv6 enable topology standard`（或 ipv6 topology） |
| 12 | 过渡技术越新越好 | **双栈是目标态**，隧道与翻译是过渡手段 |

---

# 板块16 · 网络自动化与智能运维
> 定位：HCIE 笔试权重高、实验占比持续上升的新增模块。不会写几行 Python、看不懂 YANG、没听过 Telemetry，HCIE 拿不到高分，项目上也只能停留在"人肉运维"阶段。
> 学习目标：**能读能改 NETCONF/YANG 报文结构、能用 Python 批量下配置、能做配置合规检查与自动备份、理解 Telemetry 与传统 SNMP 的代际差异。**
> 一句话价值：**把"重复 100 遍的操作"变成"跑一次脚本"，把"出事才发现"变成"秒级感知"。**

## 16_1 网络自动化全景
### 16_1.1 为什么需要自动化
| 传统运维痛点 | 自动化解决 |
| --- | --- |
| 100 台设备改一个 ACL，手工敲 100 遍 | **批量下发**，分钟级完成 |
| 配置漂移（设备间配置不一致）无人知晓 | **自动巡检 + 合规比对** |
| 故障靠人肉查，MTTR 长 | **Telemetry 秒级感知 + 自动告警** |
| 割接靠记忆，易遗漏 | **脚本化编排，可回滚** |
| 新人上手慢 | 脚本即 SOP |

### 16_1.2 自动化技术栈
```latex
┌──────────────────────────────────────────────┐
│  编排层：Ansible / Python 脚本 / iMaster NCE  │
├──────────────────────────────────────────────┤
│  API 层：NETCONF / RESTful / gRPC / Telemetry │
├──────────────────────────────────────────────┤
│  数据层：YANG 模型（配置/状态数据建模）         │
├──────────────────────────────────────────────┤
│  传输层：SSH / TLS / TCP                       │
├──────────────────────────────────────────────┤
│  设备层：VRP / CloudEngine                     │
└──────────────────────────────────────────────┘
```

| 技术 | 用途 | 特点 |
| --- | --- | --- |
| **NETCONF** | 配置下发与查询 | 基于 XML，事务性，支持回滚 |
| **YANG** | 数据建模语言 | 定义配置/状态数据的结构 |
| **RESTCONF** | RESTful 风格配置 | HTTP + JSON/XML |
| **Telemetry** | 实时数据采集 | **推模式**（设备主动上报），秒级/亚秒级 |
| **SNMP** | 传统监控 | **拉模式**（网管轮询），分钟级 |
| **gRPC/gNMI** | 新一代接口 | 高效，流式 |
| **OPS** | 设备内嵌 Python 运行环境 | 在设备上跑脚本响应事件 |

> 记忆锚点：**NETCONF 管配置，Telemetry 管监控，YANG 是它们共同的"数据字典"。**

---

## 16_2 NETCONF 与 YANG
### 16_2.1 NETCONF 核心概念
```latex
NETCONF = 基于 XML 的网络配置协议，运行在 SSH 之上（默认端口 830）

三个配置库（Datastore）：
  ┌─ [running]     当前运行配置
  ├─ [candidate]   候选配置（编辑后需 commit 才生效）
  └─ [startup]     启动配置
```

> 三个配置库的写法在实际报文里是 running / candidate / startup（XML 元素名）。**生产环境建议在 candidate 上编辑再 commit**，这样一旦配错可以 `discard-changes` 整体丢弃，不必逐条 undo。

### 16_2.2 设备侧使能 NETCONF
```latex
[SW] netconf
[SW-netconf] protocol inbound ssh port 830
[SW-netconf] idle-timeout 10
[SW-netconf] quit

[SW] ssh server netconf                        # 使能 SSH 的 NETCONF 子系统
[SW] aaa
[SW-aaa] local-user netconf-user password cipher Netconf@123
[SW-aaa] local-user netconf-user service-type ssh
[SW-aaa] local-user netconf-user privilege level 3
[SW-aaa] quit
[SW] ssh user netconf-user authentication-type password
[SW] ssh user netconf-user service-type snetconf        # ★ 注意是 snetconf
[SW] save
```

验证：

```latex
[SW] display netconf session                   # 当前 NETCONF 会话
[SW] display netconf capability                # 设备支持的 YANG 能力集
[SW] display netconf statistics
```

### 16_2.3 NETCONF 报文结构
**查询接口配置（get-config）：**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rpc message-id="101" xmlns="urn:ietf:params:xml:ns:netconf:base:1.0">
  <get-config>
    <source>
      <running/>
    </source>
    <filter type="subtree">
      <ifm xmlns="urn:huawei:yang:huawei-ifm">
        <interfaces>
          <interface>
            <ifName>GigabitEthernet0/0/1</ifName>
          </interface>
        </interfaces>
      </ifm>
    </filter>
  </get-config>
</rpc>

```

**修改配置（edit-config）：**

```xml
<rpc message-id="102" xmlns="urn:ietf:params:xml:ns:netconf:base:1.0">
  <edit-config>
    <target>
      <running/>
    </target>
    <config>
      <ifm xmlns="urn:huawei:yang:huawei-ifm">
        <interfaces>
          <interface>
            <ifName>GigabitEthernet0/0/1</ifName>
            <ifDescr>Configured-By-NETCONF</ifDescr>
            <ifAdminStatus>up</ifAdminStatus>
          </interface>
        </interfaces>
      </ifm>
    </config>
  </edit-config>
</rpc>

```

**常用操作：**

| 操作 | 作用 |
| --- | --- |
| `get` | 获取配置 + 状态数据 |
| `get-config` | 只获取配置数据 |
| `edit-config` | 修改配置（merge/replace/create/delete） |
| `copy-config` | 配置库之间复制 |
| `delete-config` | 删除配置库 |
| `lock` / `unlock` | 加锁防冲突 |
| `commit` | 提交候选配置 |
| `discard-changes` | 丢弃未提交的修改 |
| `close-session` / `kill-session` | 关闭会话 |

> 考试常考 `edit-config` 的 **merge 与 replace 区别**：merge 是增量合并（保留未涉及的配置），replace 是整段替换（未提及的配置被删除）。生产环境用 replace 前必须三思。

### 16_2.4 YANG 模型基础
```latex
module huawei-ifm {
  namespace "urn:huawei:yang:huawei-ifm";
  prefix ifm;

  container ifm {
    container interfaces {
      list interface {
        key "ifName";
        leaf ifName        { type string; }
        leaf ifDescr       { type string; }
        leaf ifAdminStatus { type enumeration { enum up; enum down; } }
      }
    }
  }
}
```

**YANG 关键字：**

| 关键字 | 含义 |
| --- | --- |
| `module` | 模块（顶层） |
| `namespace` | 命名空间（唯一标识） |
| `container` | 容器（分组） |
| `list` | 列表（可多个实例，需 key） |
| `leaf` | 叶子节点（单个值） |
| `leaf-list` | 叶子列表（多个值） |
| `type` | 数据类型 |
| `config true/false` | 是否可配置（false = 只读状态数据） |

> 查看设备 YANG 能力：`display netconf capability`，或用 `get` 获取 `netconf-state` 信息。写 NETCONF 脚本前先查能力集，能省掉一半"报文被拒"的调试时间。

---

## 16_3 Python 自动化实战
### 16_3.1 环境准备
```bash
pip install paramiko netmiko ncclient textfsm
```

| 库 | 用途 |
| --- | --- |
| `paramiko` | SSH 底层库 |
| `netmiko` | 多厂商 SSH 封装（推荐） |
| `ncclient` | NETCONF 客户端 |
| `textfsm` | 解析 CLI 输出为结构化数据 |

**设备侧的配合设置（脚本能跑通的前提）：**

```latex
[SW] screen-length 0 temporary             # ★ 关闭分页，否则长输出被 "--More--" 截断
[SW] user-interface vty 0 4
[SW-ui-vty0-4] screen-length 0             # VTY 下永久关闭分页
[SW-ui-vty0-4] idle-timeout 15 0
[SW-ui-vty0-4] quit
```

> ⚠️ **忘记 **`screen-length 0`** 是自动化脚本"卡住不动"的最常见原因**：脚本等待命令结束，设备却在等用户按空格。表现为连接超时、输出只有前几屏。

### 16_3.2 示例一：SSH 批量执行命令与备份（netmiko）
```python
from netmiko import ConnectHandler
import datetime
import os

devices = [
    {"host": "192.168.99.11", "name": "ACC-01"},
    {"host": "192.168.99.12", "name": "ACC-02"},
    {"host": "192.168.99.13", "name": "ACC-03"},
]

commands = [
    "display version",
    "display interface brief",
    "display stp brief",
    "display cpu-usage",
]

os.makedirs("backup", exist_ok=True)

for dev in devices:
    conn = {
        "device_type": "huawei",          # netmiko 支持 huawei / huawei_vrp
        "host": dev["host"],
        "username": "netadmin",
        "password": "Admin@2026",
        "port": 22,
    }
    print(f"===== 正在采集 {dev['name']} ({dev['host']}) =====")
    try:
        net = ConnectHandler(**conn)
        net.enable()
        output = ""
        for cmd in commands:
            output += f"\n---- {cmd} ----\n"
            output += net.send_command(cmd, expect_string=r"[>\]]", read_timeout=60)
        ts = datetime.datetime.now().strftime("%Y%m%d_%H%M%S")
        with open(f"backup/{dev['name']}_{ts}.txt", "w", encoding="utf-8") as f:
            f.write(output)
        # 自动保存配置
        net.send_command("save", expect_string=r"\[Y/N\]")
        net.send_command("Y", expect_string=r"[>\]]")
        net.disconnect()
        print(f"  [OK] {dev['name']} 采集完成")
    except Exception as e:
        print(f"  [FAIL] {dev['name']}: {e}")
```

### 16_3.3 示例二：批量下发配置（带回滚）
```python
from netmiko import ConnectHandler
import os

config_commands = [
    "vlan 100",
    "description Auto-Created-VLAN",
    "interface GigabitEthernet0/0/1",
    "port link-type access",
    "port default vlan 100",
    "stp edged-port enable",
]

def push_config(host, username, password, commands):
    os.makedirs("rollback", exist_ok=True)
    net = ConnectHandler(device_type="huawei", host=host,
                         username=username, password=password)
    # 先备份当前配置（回滚的底线）
    before = net.send_command("display current-configuration", read_timeout=90)
    with open(f"rollback/{host}_before.cfg", "w", encoding="utf-8") as f:
        f.write(before)
    try:
        net.enable()
        out = net.send_config_set(commands)
        net.send_command("save", expect_string=r"\[Y/N\]")
        net.send_command("Y", expect_string=r"[>\]]")
        print(f"[OK] {host}\n{out}")
    except Exception as e:
        print(f"[FAIL] {host}: {e}，请检查 rollback/{host}_before.cfg 手动回滚")
    finally:
        net.disconnect()

push_config("192.168.99.11", "netadmin", "Admin@2026", config_commands)
```

> ★ **下发的三条铁律**：第1步 先备份再改；第2步 先在一台上试跑，验证无误再批量；第3步 每批之间留观察窗口，别一口气推完全网。

### 16_3.4 示例三：配置合规检查
```python
from netmiko import ConnectHandler
import re

# 合规基线：必须包含的安全配置
baseline = {
    "SSH 服务":      r"stelnet server enable",
    "VTY 限定 SSH":  r"protocol inbound ssh",
    "日志服务器":     r"info-center loghost",
    "STP BPDU 保护": r"stp bpdu-protection",
    "NTP":          r"ntp-service",
}

def compliance_check(host, user, pwd):
    net = ConnectHandler(device_type="huawei", host=host, username=user, password=pwd)
    cfg = net.send_command("display current-configuration", read_timeout=90)
    net.disconnect()

    print(f"\n===== 合规检查：{host} =====")
    result = []
    for item, pattern in baseline.items():
        hit = re.search(pattern, cfg) is not None
        result.append((item, "PASS" if hit else "FAIL"))
        print(f"  [{'PASS' if hit else 'FAIL'}] {item}")
    return result

compliance_check("192.168.99.11", "netadmin", "Admin@2026")
```

### 16_3.5 示例四：NETCONF（ncclient）
```python
from ncclient import manager

host = "192.168.99.11"

# 查询接口信息
get_filter = """
<filter type="subtree">
  <ifm xmlns="urn:huawei:yang:huawei-ifm">
    <interfaces>
      <interface>
        <ifName>GigabitEthernet0/0/1</ifName>
      </interface>
    </interfaces>
  </ifm>
</filter>
"""

with manager.connect(host=host, port=830, username="netconf-user",
                     password="Netconf@123", hostkey_verify=False,
                     device_params={"name": "huawei"}) as m:
    print(m.get_config(source="running", filter=get_filter))

    # 修改接口描述
    edit_cfg = """
<config>
  <ifm xmlns="urn:huawei:yang:huawei-ifm">
    <interfaces>
      <interface>
        <ifName>GigabitEthernet0/0/1</ifName>
        <ifDescr>Configured-By-NETCONF</ifDescr>
      </interface>
    </interfaces>
  </ifm>
</config>
"""
    print(m.edit_config(target="running", config=edit_cfg))
    m.commit()
```

### 16_3.6 解析 CLI 输出（TextFSM 思路）
没有现成模板时，用正则也能快速提取字段：

```python
import re

raw = """
GigabitEthernet0/0/1   up    up     192.168.10.1
GigabitEthernet0/0/2   down  down   --
"""

pattern = re.compile(r"^(\S+)\s+(\S+)\s+(\S+)\s+(\S+)?", re.M)
for m in pattern.finditer(raw):
    ifname, phy, proto, ip = m.groups()
    print(f"接口={ifname:22} 物理={phy:6} 协议={proto:6} IP={ip}")
```

> 实战建议：小规模用正则，规模上来后改用 **TextFSM 模板**或直接用 NETCONF/YANG 拿结构化数据——**能拿结构化数据就别解析文本**，这是自动化稳定性的分水岭。

---

## 16_4 Telemetry 与智能运维
### 16_4.1 SNMP vs Telemetry（代际差异，必考）
| 维度 | SNMP | Telemetry |
| --- | --- | --- |
| 模式 | **拉**（网管轮询） | **推**（设备主动上报） |
| 周期 | 分钟级 | **秒级 / 亚秒级** |
| 数据粒度 | 粗（计数器） | 细（接口、队列、流表等） |
| 编码 | BER | **GPB / JSON** |
| 扩展性 | 差（MIB 定义） | 好（YANG 定义） |
| 大规模 | 轮询压力大 | 适合大规模 |

```latex
SNMP（拉模式）：                    Telemetry（推模式）：

 网管 ──轮询请求──▶ 设备             设备 ──订阅数据──▶ 采集器
 网管 ◀──响应────  设备             （设备按周期主动推，网管只负责收）
 ↑ 设备越多，轮询越慢                ↑ 万台设备也能秒级感知
```

### 16_4.2 Telemetry 静态订阅
```latex
[SW] telemetry
[SW-telemetry] destination-group DEST1
[SW-telemetry-destination-group-DEST1] ipv4-address 192.168.1.100 port 10001 protocol grpc
[SW-telemetry-destination-group-DEST1] quit
[SW-telemetry] sensor-group SENSOR1
[SW-telemetry-sensor-group-SENSOR1] sensor-path huawei-ifm:ifm/interfaces/interface
[SW-telemetry-sensor-group-SENSOR1] quit
[SW-telemetry] subscription SUB1
[SW-telemetry-subscription-SUB1] sensor-group SENSOR1 sample-interval 10000
[SW-telemetry-subscription-SUB1] destination-group DEST1
[SW-telemetry-subscription-SUB1] quit
```

**三要素记忆法**：`sensor-group`（采什么）→ `destination-group`（发给谁）→ `subscription`（多久发一次）。

### 16_4.3 gRPC 与采集器
+ **gRPC**：Google 开源的高性能 RPC 框架，Telemetry 主流承载协议；
+ **采集器**：接收并解析 GPB 编码的数据（如 Prometheus + 自研解析器、华为 iMaster NCE）；
+ 典型链路：设备（gRPC 推）→ 采集器（解码）→ 时序库（存储）→ 看板（可视化告警）。

### 16_4.4 iMaster NCE（控制器）
| 能力 | 说明 |
| --- | --- |
| 网络自动化 | 配置模板、批量下发、业务编排 |
| 智能运维 | Telemetry 采集、故障智能定界、健康度评估 |
| 业务随行 | 与园区 VXLAN/策略联动，实现用户策略随行 |
| 开放 API | 北向 RESTful 接口，可对接自有运维平台 |

---

## 16_5 OPS（设备内嵌脚本）
OPS 让**脚本跑在设备上**，直接响应设备事件（接口 down、CPU 超阈值、日志关键字）。

```python
# interface_down.py
def ops_condition(_ops):
    # 监听接口 down 事件
    ret, desp = _ops.cli.subscribe("evt", "IFNET/2/LINKDOWN", True, True, False, 10)
    return 0

def ops_execute(_ops):
    # 事件触发后自动执行：打印日志并采集信息
    _ops.cli.execute("display interface brief")
    _ops.syslog("Interface down detected, auto collected info")
    return 0
```

```latex
[SW] ops
[SW-ops] script-assistant python interface_down.py
[SW-ops] quit
[SW] display ops script
```

> OPS 的价值：**不等人**。半夜接口 flapping，脚本立刻把现场信息抓下来并上送日志，第二天早上你面对的是一份完整的证据，而不是一句"好像断过"。

---

## 16_6 自动化落地路线（从零到一）
### 16_6.1 开局配置模板（Jinja2 示例）
```python
from jinja2 import Template

tpl = Template("""sysname {{ hostname }}
vlan batch {{ vlans | join(' ') }}
#
interface Vlanif{{ mgmt_vlan }}
 ip address {{ mgmt_ip }} {{ mgmt_mask }}
#
{% for p in access_ports %}
interface GigabitEthernet0/0/{{ p }}
 port link-type access
 port default vlan {{ data_vlan }}
 stp edged-port enable
{% endfor %}
""")

print(tpl.render(
    hostname="ACC-01",
    vlans=[10, 20, 99],
    mgmt_vlan=99,
    mgmt_ip="192.168.99.11",
    mgmt_mask="24",
    access_ports=range(1, 25),
    data_vlan=10,
))
```

**落地路线四步：**

```latex
第1步 脚本化备份      → 先把"配置备份"这件事自动化（风险最低，收益立竿见影）
第2步 脚本化巡检      → CPU/内存/接口错包/邻居状态，每天自动跑一次
第3步 模板化开局      → 新设备上线直接渲染模板，杜绝手工敲错
第4步 编排化变更      → 变更脚本化 + 自动回滚 + 变更窗口控制
```

### 16_6.2 自动化安全风控（必须遵守）
| 风险 | 控制措施 |
| --- | --- |
| 账号泄露 | 专用自动化账号，最小权限（level 2–3），密码走密钥库不硬编码 |
| 误操作扩散 | 先单机验证 → 小批量 → 全网；每批留观察窗口 |
| 无回滚 | 变更前强制备份，脚本内置回滚路径 |
| 并发压垮设备 | 限制并发连接数（建议 ≤ 10） |
| 审计缺失 | 记录每次变更的时间、人、设备、命令、结果 |

---

## 16_7 案例：一次自动化巡检救下的割接
> 某园区准备做核心设备升级，割接窗口只有凌晨 3 小时。团队提前跑了一次自动化合规巡检脚本，结果在 40 台接入交换机里揪出 **3 台没有配 **`stp bpdu-protection`**、2 台 NTP 指向了错误地址、1 台 VTY 还开着 Telnet**。
> 这几台设备如果原样进入割接，最可能的结果是：新核心上线后 STP 收敛异常，会议室环路一起，整层楼断网；日志时间戳错乱让事后复盘变成一锅粥。
> 脚本 20 分钟跑完，问题 1 小时内修完，割接按计划完成。**这就是自动化的意义：不是炫技，是把"人肉看不过来的细节"变成"机器每次都会看的清单"。**

---

## 16_8 排错清单
> **本节导读**：遇到问题时按这张表逐条对照——先按现象归类，再跑「第一刀」命令缩小范围，最后才动手改配置。

| 现象 | 原因 | 处理 |
| --- | --- | --- |
| SSH 登录失败 | 服务未开 / 账号未配 service-type ssh / VTY 协议不对 | 查 `stelnet server enable`、`ssh user`、`protocol inbound ssh` |
| NETCONF 连不上 | 未 `ssh server netconf` / 端口非 830 / 服务类型不是 snetconf | 逐项核对三处配置 |
| NETCONF 报文被拒 | namespace 或节点名不匹配 | `display netconf capability` 核对能力集 |
| edit-config 后配置被清空 | 用了 `replace` 而非 `merge` | 改用 merge |
| Telemetry 无数据 | sensor-path 错误 / 目的地址端口不通 | 查 subscription 状态与采集器监听 |
| 脚本执行到一半卡住 | 命令回显匹配不到 expect_string | 调大 read_timeout 或修正匹配串 |
| 批量下发部分失败 | 单台异常未捕获导致整体中断 | 逐台 try/except，记录失败清单继续跑 |

---

## 16_9 场景笔记与验证
### 16_9.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **技术栈卡** | NETCONF 配、Telemetry 监、YANG 建模、gRPC 传输 |
| **端口卡** | SSH 22、NETCONF 830、SNMP 161、Telemetry 自定义（常用 10001） |
| **三个配置库** | running / candidate / startup，candidate 需 commit |
| **edit-config 卡** | merge 增量、replace 整段替换（危险） |
| **Telemetry 三要素** | sensor-group → destination-group → subscription |
| **坑本** | 服务类型写成 `netconf` 而非 `snetconf`；忘了 commit；批量脚本没 try/except |

### 16_9.2 验证三板斧（本板块版）
```latex
第1步 看会话：display netconf session（NETCONF 建起来了吗？）
第2步 看能力：display netconf capability（YANG 路径写对了吗？）
第3步 看订阅：display telemetry subscription（数据推出去了吗？）
```

### 16_9.3 建议做一次的自动化实验
1. 在 eNSP 或真机上开启 NETCONF，用 ncclient 完成一次 **查询 → 修改 → 提交 → 回滚** 全过程；
2. 写一个合规检查脚本，对 3 台设备跑一遍，故意在其中一台删掉 `stp bpdu-protection`，验证脚本能否抓出来；
3. 把"每天备份配置"写成定时任务，跑一周，看备份文件是否按预期生成。

---

## 16_10 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | 自动化等于写脚本 | 核心是**标准化 + 可回滚 + 可审计** |
| 2 | NETCONF 用 TCP 22 | 默认 **830**（走 SSH 之上） |
| 3 | `edit-config` 默认 replace | 默认是 **merge**，replace 才是危险操作 |
| 4 | candidate 配置改完即生效 | 需 `commit` 才生效 |
| 5 | SSH 用户服务类型写 netconf | 正确是 `snetconf` |
| 6 | Telemetry 也是拉模式 | 是**推模式**，设备主动上报 |
| 7 | SNMP 与 Telemetry 二选一 | 过渡期**共存**，SNMP 存量设备仍依赖 |
| 8 | YANG 只能用于 NETCONF | 也用于 RESTCONF、gNMI 与 Telemetry 建模 |
| 9 | 脚本敢直接全网推 | **先单机、再小批、后全网**，每批留观察窗口 |
| 10 | OPS 脚本和运维脚本一样 | OPS **跑在设备内**，直接响应设备事件 |

---

# 板块17 · 故障排查方法论与案例库
> 定位：HCIE-Datacom 实验的**故障排查已升级为独立计分模块**（基础故障题 5 分 + 进阶故障题 10 分，合计 15 分），采用预置故障与动态场景故障两种形式，限时恢复业务。本板块同时也是真实运维中最值钱的能力。
> 为什么排错值得单独花时间：**15 分，却只需要 45 分钟**——这是整场实验里性价比最高的分数。但排错考的从来不是背命令，而是"看到现象，脑子里能不能立刻蹦出那三四个可能的原因，并且知道先用哪条命令砍掉一半可能性"。
> 记住：**排错不是猜，是"缩小范围"的过程。每一条命令都应该砍掉一半的可能性。**

## 17_1 排错方法论
### 17_1.1 五种思路与适用场景
| 方法 | 思路 | 适用 |
| --- | --- | --- |
| **自底向上**（推荐） | 物理层 → 数据链路层 → 网络层 → 传输层 → 应用层 | 大多数网络故障 |
| **自顶向下** | 应用 → 传输 → 网络 → 链路 → 物理 | 应用异常但底层"看起来正常" |
| **分而治之**（最快） | 在中间点测试，定位在哪一半，再二分 | 大型网络、跨站点故障 |
| **对比法** | 与正常设备/正常时段对比 | 配置漂移、间歇性故障 |
| **替换法** | 换线/换模块/换端口/换设备 | 疑似硬件故障 |

### 17_1.2 五步标准流程
```latex
第1步 收集信息：故障现象、影响范围、发生时间、变更历史（★ 80% 的故障与变更有关）
第2步 定位范围：全網 / 单网段 / 单设备 / 单用户？
第3步 分层测试：物理 → 二层 → 三层 → 应用
第4步 制定方案：先恢复业务，再根治（★ 考试/生产都先拿分）
第5步 验证与复盘：确认恢复、记录根因、输出报告
```

> ★ 第一问永远是：**"故障前改过什么？"** 割接、升级、插线、换设备、策略调整……变更是故障的最大来源。

### 17_1.3 分而治之的实操
```latex
拓扑：PC ── ACC ── AGG ── CORE ── FW ── Internet
故障：PC 上不了网

Step 1：PC ping 自己的网关        → 不通，问题在 PC–AGG 之间
Step 2：在 AGG 上 ping CORE 接口   → 通，问题缩小到 PC–ACC 或 ACC–AGG
Step 3：在 ACC 上 ping AGG         → 通，问题在 PC–ACC（接入段）
Step 4：换端口/换线测试           → 定位到具体故障点
```

要点：**每测一次就把可能性砍掉一半**，三步之内必然定位到具体网段。

### 17_1.4 排错工具箱
| 工具 | 命令 | 用途 |
| --- | --- | --- |
| **连通性** | `ping`、`ping -a 源`、`ping -s 大小` | 通不通回程、MTU |
| **路径** | `tracert` | 断在哪一跳、有没有环路 |
| **接口** | `display interface brief` | UP/DOWN、速率、错包 |
| **二层** | `display mac-address`、`display port vlan` | MAC 学习、VLAN 归属 |
| **三层** | `display ip routing-table`、`display fib` | 路由是否存在是否下发 |
| **ARP** | `display arp` | 下一跳 MAC 是否解析 |
| **协议** | `display ospf peer`、`display bgp peer` | 邻居状态 |
| **表项** | `display acl`、`display nat session` | 策略是否命中 |
| **日志** | `display logbuffer`、`display trapbuffer` | 历史告警 |
| **诊断** | `display diagnostic-information` | 一键全量采集 |
| **抓包** | `capture-packet` / Wireshark | 报文级分析 |
| **设备健康** | `display device` / `display cpu-usage` / `display memory` | 硬件与资源 |
| **地址池** | `display ip pool` / `display ip pool name X used` | DHCP 分配情况 |
| **绑定表** | `display dhcp snooping` / `display dhcp snooping user-bind all` | 安全绑定表 |
| **策略应用** | `display traffic-filter applied-record` / `display traffic-policy applied-record` | 策略挂在哪 |
| **大包测试** | `ping -s 1500 -f` | 不分片大包，测 MTU |

**设备内抓包（不接镜像也能抓）：**

```latex
<SW> capture-packet interface GigabitEthernet 0/0/1 acl 3000 destination terminal
<SW> capture-packet interface GigabitEthernet 0/0/1 acl 3000 destination file flash:/cap.cap
```

---

## 17_2 分层排错速查表
### 17_2.1 物理层
| 现象 | 检查 | 命令 |
| --- | --- | --- |
| 端口 down | 线缆、模块、对端、shutdown | `display interface brief`、`display transceiver` |
| 频繁 up/down | 光模块不兼容、光衰、网线质量 | `display interface`（看 error）、`display logbuffer` |
| 光口不通 | 收发光功率、波长、单模/多模 | `display transceiver interface` |
| CRC 错包 | 双工/速率不匹配、电磁干扰 | `display interface`（Input errors） |

**光模块判读：**

```latex
<SW> display transceiver interface GigabitEthernet 0/0/1 verbose
  Rx Power:  -5.23 dBm      正常范围：一般 -3 ~ -15 dBm
  Tx Power:  -3.15 dBm
  若 Rx < -20 dBm → 光衰过大（光纤弯折/接头脏/距离超限）
  若 Rx 显示 N/A 或 -40 dBm → 对端未发光或光纤断
```

### 17_2.2 数据链路层
| 现象 | 检查 | 命令 |
| --- | --- | --- |
| 同 VLAN 不通 | 端口 VLAN 归属、Trunk 放行、STP 阻塞 | `display port vlan`、`display stp brief` |
| MAC 学不到 | 端口 down、VLAN 错、MAC 表满 | `display mac-address` |
| **MAC 漂移** | **环路** | `display mac-address flapping record` |
| 全网慢 | 广播风暴、环路 | `display cpu-usage`、`display interface`（广播包速率） |
| Eth-Trunk 异常 | 成员状态、两端配置 | `display eth-trunk` |

### 17_2.3 网络层
| 现象 | 检查 | 命令 |
| --- | --- | --- |
| 跨网段不通 | 网关、路由、VLANIF 状态 | `display ip routing-table`、`display ip interface brief` |
| **单向通** | **对端无回程路由** | 两端 `display ip routing-table` |
| 路由不存在 | 协议邻居、宣告、策略过滤 | `display ospf peer`、`display bgp peer` |
| 路由存在但不通 | 下一跳不可达、ARP 失败、ACL | `display arp`、`display fib` |
| OSPF 邻居起不来 | Hello 参数、区域、认证、MTU、Router ID | `display ospf error` |

### 17_2.4 应用层
| 现象 | 检查 |
| --- | --- |
| 能 ping 通但打不开网页 | DNS、HTTP 代理、防火墙 |
| 网页能开但慢 | MTU/MSS、DNS 解析慢、带宽拥塞 |
| 部分网站打不开 | MTU（PPPoE）、DNS 污染、策略拦截 |
| FTP 能登录列不出目录 | **ALG 未开**、被动模式端口未放行 |

---

## 17_3 高频案例库（20 例）
### 案例 1：全网突然变慢、CPU 飙高
**现象**：所有用户上网卡顿，`display cpu-usage` 达 90%+。

**排查：**

```latex
[SW] display cpu-usage task                    # 看哪个进程占 CPU
[SW] display mac-address flapping record       # 查 MAC 漂移 → 环路
[SW] display interface | include broadcast     # 广播包速率异常
[SW] display stp brief                         # 是否有该阻塞却未阻塞的端口
```

**根因**：有人把网线两端插到同一台交换机的两个口，形成环路。

**处理：**

```latex
# 应急：shutdown 疑似端口
[SW] interface g0/0/5
[SW-GigabitEthernet0/0/5] shutdown

# 根治：边缘端口 + BPDU 保护
[SW] stp bpdu-protection
[SW] port-group pg-user
[SW-port-group-pg-user] stp edged-port enable
```

---

### 案例 2：PC 开机后 30 秒才能上网
**现象**：插上网线后要等半分钟才能通信。

**根因**：接入端口未配**边缘端口**，STP 要经历 Listening(15s) + Learning(15s)。

**处理：**

```latex
[SW] interface g0/0/1
[SW-GigabitEthernet0/0/1] stp edged-port enable
# 或全局（互联口需 undo）
[SW] stp edged-port default
```

---

### 案例 3：Trunk 上部分 VLAN 不通
**现象**：VLAN 10 通VLAN 20 不通。

**排查：**

```latex
[SW1] display interface g0/0/24 trunk          # 看 allow-pass 列表
[SW2] display interface g0/0/24 trunk          # 两端对比
```

**根因**：两端 `port trunk allow-pass` 列表不一致（一端漏了 VLAN 20）。

**处理**：两端统一放行列表。

---

### 案例 4：VLAN 间不通（VLANIF down）
**现象**：PC ping 不通其他 VLAN 的网关。

**排查：**

```latex
[SW] display ip interface brief                # Vlanif20 是 *down* (physically down)
[SW] display vlan 20                           # VLAN 20 内无任何 UP 端口
```

**根因**：VLANIF 需要该 VLAN 内有 **UP 的物理端口**才会 UP。该 VLAN 的接入设备全关机。

**处理**：接入设备上线，或将 Trunk 口放行该 VLAN。

---

### 案例 5：单臂路由 PC ping 不通网关
**根因**：子接口漏配 `arp broadcast enable`，终结子接口不发 ARP 广播。

**处理：**

```latex
[Router-GigabitEthernet0/0/1.10] arp broadcast enable
```

---

### 案例 6：OSPF 邻居卡在 ExStart
**根因**：**MTU 不匹配**（一端 1500，一端 9000），DD 报文无法通过 MTU 检查。

**处理：**

```latex
# 方案一：统一 MTU
[SW-GigabitEthernet0/0/1] mtu 1500

# 方案二：忽略 MTU 检查（临时）
[SW-GigabitEthernet0/0/1] ospf mtu-enable
```

---

### 案例 7：OSPF 邻居卡在 2-Way
**排查：** `display ospf peer`，若两台都是 DROther，2-Way 是正常的。

**结论**：广播网络中 **DROther 之间就是 2-Way**，不是故障。只有 DR/BDR 与 DROther 才到 Full。

---

### 案例 8：OSPF 学到了路由但不通
**排查：**

```latex
[SW] display ospf routing                      # OSPF 有路由
[SW] display ip routing-table                  # 全局路由表却没有
```

**根因**：存在更优来源的路由（如静态 Pre 60 优于 OSPF 外部 150），或路由被 `filter-policy` 过滤。

---

### 案例 9：BGP 邻居 Idle
**根因**：无去往 peer 地址的路由（最常见）。

**处理：**

```latex
[Router] display ip routing-table 3.3.3.3      # 无路由 → 补 IGP 通告或静态路由
```

---

### 案例 10：IBGP 学到路由但"不可用"
**现象**：`display bgp routing-table` 中路由没有 `>` 标记，只有 `*`。

**根因**：下一跳不可达（IBGP 默认不改下一跳）。

**处理：**

```latex
[Router-bgp-af-ipv4] peer 10.5.5.5 next-hop-local
```

---

### 案例 11：能 ping 通 IP 但打不开网页
**排查**：`ping 8.8.8.8` 通`ping www.xxx.com` 不通 → **DNS 问题**。

**处理**：检查 DHCP 下发的 DNS、终端 DNS 配置、DNS 服务器可达性。

---

### 案例 12：能上 QQ 但不能开网页
**根因**：QQ 走 IP 直连，网页依赖 DNS → 典型的 **DNS 解析失败或劫持**。

**处理**：换 DNS、检查出口是否有 DNS 拦截、`nslookup` 验证解析结果。

---

### 案例 13：NAT 配置正确但内网不能上网
**排查清单：**

```latex
第1步 终端网关是否指向做 NAT 的设备
第2步 NAT 设备是否有到公网的默认路由
第3步 公网侧是否有回程路由（尤其多出口）
第4步 ACL 是否匹配了内网网段
第5步 运营商线路本身是否可达
```

---

### 案例 14：私接路由器导致全网断网
**现象**：部分用户拿到 192.168.1.x 的"假地址"，上不了网。

**根因**：有人把自己家的小路由器 LAN 口接到了办公网，其 DHCP 服务器抢答。

**处理：**

```latex
[SW] dhcp enable
[SW] dhcp snooping enable ipv4
[SW] vlan 10
[SW-vlan10] dhcp snooping enable
[SW-vlan10] dhcp snooping trusted interface gigabitethernet 0/0/1    # 上行口信任
```

---

### 案例 15：VRRP 双主
**现象**：两台设备 `display vrrp brief` 都显示 Master。

**根因**：**三层不通**（VRRP 报文收不到）、虚拟 IP 不一致、VRID 不一致、认证不一致。

**处理**：`ping` 互连接口；逐项核对 vrid、virtual-ip、认证配置。

---

### 案例 16：主设备宕机但 VRRP 不切换（或切换后仍黑洞）
**根因**：第1步 未配 BFD 导致检测慢；第2步 主设备**上行链路断了但仍是 Master**，未配 track。

**处理：**

```latex
[SW1-Vlanif10] vrrp vrid 1 track interface gigabitethernet 0/0/24 reduced 30
[SW1-Vlanif10] vrrp vrid 1 track bfd-session 10 reduced 30
```

---

### 案例 17：堆叠分裂后网络大乱
**现象**：堆叠链路中断后，两台设备都认为自己是 Master，IP/MAC 冲突，全网瘫痪。

**根因**：**未配 MAD 多主检测**。

**处理：**

```latex
[SW] mad detect mode direct                    # 直连检测
# 或
[SW] mad detect mode relay                     # 代理检测
[SW] mad restore                               # 链路恢复后恢复堆叠
```

---

### 案例 18：MSTP 负载分担不生效
**现象**：配了 instance 1/2，但流量仍全走一条上行。

**根因**（按概率排序）：

1. **漏配 **`active region-configuration`；
2. 各交换机 region-name / revision-level / VLAN 映射**三要素不一致**；
3. 两端实例优先级配成了同一台设备当根。

**排查：** `display stp region-configuration` 逐台对比，输出必须完全一致。

---

### 案例 19：MPLS L3VPN 配置齐全但 ping 不通
**排查顺序（黄金五步）：**

```latex
第1步 display mpls ldp session          → LDP 会话是否 Operational
第2步 display mpls lsp                  → LSP 是否完整（Ingress/Transit/Egress 都有）
第3步 display bgp vpnv4 all peer        → MP-BGP 邻居是否 Established
第4步 display bgp vpnv4 routing-table   → 是否收到对端 VPNv4 路由
第5步 检查 RT：本端 Export RT = 对端 Import RT ？
```

**最高频根因**：**RT 不匹配**（Export/Import 写反或漏配），或 PE-CE 之间路由没进来。

---

### 案例 20：VXLAN 隧道 up 但业务不通
**排查：**

```latex
[LEAF] display vxlan vni            # VNI 与 BD 映射两端是否一致
[LEAF] display vxlan tunnel         # 隧道状态
[LEAF] display vxlan peer           # 远端 VTEP 列表
[LEAF] display mac-address bridge-domain 10    # MAC 是否学到
```

**常见根因**：

1. 两端 **VNI/BD 不一致**；
2. Underlay **MTU 不足**（VXLAN 封装增加 50 字节，大包被丢）；
3. 业务流量未正确引入 BD（VAP 绑定错）；
4. EVPN 的 RT 不匹配，MAC/IP 路由未通告。

---

## 17_4 排错命令速查（按症状索引）
| 症状 | 第一条命令 | 第二条命令 |
| --- | --- | --- |
| 上不了网 | `display ip interface brief` | `display ip routing-table` |
| 同网段不通 | `display port vlan` | `display mac-address` |
| 全网慢/CPU 高 | `display cpu-usage task` | `display mac-address flapping record` |
| 邻居起不来（OSPF） | `display ospf error` | `display ospf peer` |
| 邻居起不来（BGP） | `display bgp peer` | `display ip routing-table peer地址` |
| 路由学不到 | `display ip routing-table protocol xxx` | `display xxx peer` |
| 有路由不通 | `display fib` | `display arp` |
| 策略不生效 | `display acl 3001`（看计数） | `display traffic-policy applied-record` |
| VPN 不通 | `display mpls lsp` | `display bgp vpnv4 routing-table` |
| 组播收不到 | `display igmp group` | `display multicast rpf-info 源IP` |
| 网关不通 | `display vrrp brief` | `ping 虚拟IP` |
| 设备管不上 | `display ssh server status` | `display acl`（VTY 是否限了源） |

---

## 17_5 故障信息收集与报告
### 17_5.1 现场一键采集
```latex
<SW> display diagnostic-information
# 或保存到文件再导出
<SW> display diagnostic-information > flash:/diag.txt
<SW> tftp 192.168.1.100 put flash:/diag.txt diag.txt
```

### 17_5.2 故障报告模板（可直接套用）
```latex
【故障报告】

一、故障概述
   发生时间：2026-xx-xx xx:xx（发现时间 / 恢复时间）
   影响范围：xx 栋 x 层 / xx 业务 / xx 个用户
   故障等级：P1/P2/P3

二、故障现象
   （用户视角描述，例如：办公网大面积掉线，ping 网关丢包 60%）

三、变更历史
   故障前 24 小时内是否有变更：有 / 无
   变更内容：（割接、升级、策略调整等）

四、排查过程（按时间线，每条命令 + 结论）
   1. display cpu-usage → CPU 92%，任务 xxx 占比最高
   2. display mac-address flapping record → MAC xxxx 在 G0/0/5 与 G0/0/9 间漂移
   3. 定位：二层环路

五、根因分析
   （一句话说清：什么导致了什么）

六、处理措施
   应急：（shutdown 端口，业务 xx 分钟内恢复）
   根治：（配置 BPDU 保护 + 边缘端口，纳入基线）

七、改进项
   1. 全网补齐 stp bpdu-protection（责任人与完成时间）
   2. 接入端口批量下发边缘端口
   3. 纳入巡检脚本，每周检查一次
```

---

## 17_6 HCIE 实验排错专项技巧
### 17_6.1 限时排错策略（45 分钟拿 15 分）
```latex
第1步 前 3 分钟：通读故障描述，标出"预期行为"与"实际行为"的差
第2步 前 10 分钟：跑一遍分层速查（物理 → 二层 → 三层 → 策略）
第3步 10–25 分钟：定位根因，【先把业务恢复】（哪怕用临时方案）
第4步 25–35 分钟：验证业务恢复，补齐正式修复
第5步 35–45 分钟：记录根因与处理过程（论述/报告要写）
```

> ★ **黄金法则：先恢复业务，再找根因。** 考试和生产的评分逻辑一样——业务通了才给分，解释得再漂亮，业务不通也是 0。

### 17_6.2 常见预设故障点清单
| 层级 | 高频预设故障 |
| --- | --- |
| 接口 | 端口被 shutdown、速率/双工不匹配、MTU 不一致 |
| 二层 | VLAN 未创建、Trunk 未放行、PVID 不一致、STP 阻塞 |
| 三层 | IP 配错/掩码错、静态路由下一跳错、VLANIF 未 UP |
| 路由 | Router ID 冲突、区域号错、认证不一致、network 宣告漏 |
| BGP | peer AS 号错、未 `next-hop-local`、无到 peer 的路由 |
| 策略 | ACL 顺序错、route-policy 节点漏 permit、前缀列表掩码错 |
| 可靠性 | VRRP 缺 track、BFD 未 commit、Eth-Trunk 成员配置不一致 |
| 安全 | 端口安全超限、IPSG 绑定表缺失、VTY 被 ACL 拦 |

### 17_6.3 排错自检清单（每个故障点都过一遍）
```latex
□ 接口是否 up？（物理与协议双 up）
□ IP 与掩码是否正确？
□ VLAN 是否创建并放行？
□ 路由表中是否有目标网段的路由？
□ 下一跳是否可达？
□ ARP 是否解析成功？
□ 协议邻居状态是否正常？
□ ACL/策略是否命中？（看计数）
□ 是否有更优路由把流量引走？
□ 回程路由是否存在？（单向通的头号原因）
□ MTU 是否一致？
□ 最近做过什么变更？
```

---

## 17_7 案例：一次"不可能"的单向通
> 客户报障："A 区能访问 B 区服务器，B 区却访问不了 A 区。"现场所有人都觉得不可能——同一条链路，怎么会单向？
> 按分而治之的思路：  
第1步 在 A 区网关 ping B 区 → 通；  
第2步 在 B 区网关 ping A 区 → 不通；  
第3步 `display ip routing-table` 在 B 区网关上一看——**根本没有去往 A 区网段的路由**，只有一条默认路由指向了防火墙，而防火墙上 A 区方向的回程策略被上一次变更误删了。
> 结论：所谓"单向通"，本质是**回程路由缺失**。数据包去的时候好好的，回来时找不到路，就被丢在了半路。
> 修复只花 3 分钟，但定位花了 40 分钟——**如果一开局就想到"单向通 = 查回程"，3 分钟就够了**。这就是方法论的价值：它不让你更聪明，它让你不遗漏。

---

## 17_8 场景笔记与验证
### 17_8.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **分层速查卡** | 物理 → 二层 → 三层 → 应用，每层 3 条命令 |
| **症状反查表** | 见 17_4，按症状查第一条命令 |
| **单向通定律** | 单向通 = 回程路由缺失 |
| **环路信号** | MAC 漂移 + CPU 高 + 广播包飙升 = 环路三件套 |
| **坑本** | VLANIF 需活跃端口才 UP；OSPF 2-Way 可能是正常；DROther 之间不到 Full |

### 17_8.2 验证三板斧（排错版）
```latex
第1步 定范围：ping 网关 → ping 对端网关 → ping 对端主机（断在哪一跳）
第2步 看表项：路由表有没有 → FIB 有没有 → ARP 有没有（三层三查）
第3步 看计数：ACL/策略的 Matched 是否增长（策略到底命中了没）
```

### 17_8.3 建议做一次的排错训练
在 eNSP 里**给自己埋 5 个故障**（让同学来埋更好），限时 30 分钟定位并恢复：

1. 把 Trunk 的 allow-pass 去掉一个 VLAN；
2. 把 OSPF 一端的认证删掉；
3. 把浮动静态路由的 preference 改小（让备份抢主）；
4. 在 VTY 下挂一个限制源的 ACL，把自己挡在门外；
5. 把 VRRP 的 track 删掉，模拟上行断了不切换。

**能亲手把故障造出来，就能在考场上把它认出来。**

---

## 17_9 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | 排错靠经验猜 | 靠**缩小范围**，每条命令砍掉一半可能性 |
| 2 | 先找根因再恢复 | **先恢复业务，再根治**（考试先拿分） |
| 3 | 单向通很罕见 | 非常常见，**查回程路由** |
| 4 | ping 通就等于没问题 | 还要查 **MTU、丢包、时延**（大包丢是典型 MTU 问题） |
| 5 | 路由表有路由就能通 | 还需 **FIB 下发 + 下一跳可达 + ARP 解析成功** |
| 6 | OSPF 2-Way 是故障 | 广播网中 **DROther 之间 2-Way 正常** |
| 7 | MAC 漂移一定是攻击 | 多数是**环路**或虚拟机迁移 |
| 8 | VLANIF 配了 IP 就 UP | 需该 VLAN 内有 **UP 的物理端口** |
| 9 | 配置对了就该通 | 还要查**策略命中计数**与对端回程 |
| 10 | 排错不需要记录 | 故障报告是**复盘与免责**的唯一凭据 |

---

# 板块18 · HCIE 实验冲刺与综合组网
> 定位：H12-892 实验考试（480 分钟）的实战演练手册。本板块提供**完整的综合组网实验**与**论述题答题框架**，是把前 17 个板块串起来的收口环节。
> 实验考试结构：**Design（设计）→ Deploy（部署）→ Troubleshoot（排错）**。排错已成为独立计分模块（**基础故障题 5 分 + 进阶故障题 10 分 = 15 分**），采用**预置故障**与**动态场景故障**两种形式，重点考察应急响应与根因定位——不是背配置，而是"看到现象能不能立刻想到那三四个可能的原因"。

## 18_1 实验考试全流程拆解
### 18_1.1 480 分钟时间分配建议
| 阶段 | 时长 | 任务 | 产出 |
| --- | --- | --- | --- |
| **读题与规划** | 30 min | 通读全部需求，画拓扑，填地址规划表 | 规划文档（草稿） |
| **基础配置** | 60 min | 设备命名、接口 IP、VLAN、IGP | 全网 Underlay 通 |
| **核心业务部署** | 180 min | MPLS/VPN、BGP、VXLAN、组播、可靠性、QoS | 各技术点逐项验证 |
| **验证与自查** | 60 min | 按需求逐条 `display` 验证，补漏 | 验收记录 |
| **排错专项** | **45 min** | 定位并处理预设故障（**15 分**） | 业务恢复 |
| **论述题** | 60 min | 写方案说明与技术选型理由 | 论述答案 |
| **缓冲与检查** | 45 min | 保存配置、复查 | — |

> 📌 **排错模块的分值口径**：**1 道基础故障题 5 分 + 1 道进阶故障题 10 分 = 15 分**；总时长 480 分钟、总分 100 分、合格线 80 分均不变。
> 这意味着**一道进阶故障题的 10 分，相当于部署环节一整个技术点的分值**。排错的得分性价比是全场最高的——建议用 45 分钟稳拿这 15 分，而不是花 90 分钟在部署里抠无关紧要的细节。

**关键提醒：**

+ 实验**提交后不可撤回**，配置错了只能覆盖；
+ **边配边验**，不要攒到最后（最后发现问题没时间改）；
+ 每完成一个大模块立刻 `save`。

### 18_1.2 答题优先级原则
```latex
第1步 先做"地基"：接口 IP、IGP（后面所有业务都依赖它）
第2步 再做"主干"：MPLS/BGP/VPN（分值高）
第3步 再做"增强"：可靠性、QoS、安全、组播
第4步 最后"锦上添花"：优化类、可选需求
第5步 排错题：先恢复业务，再写原因
```

### 18_1.3 论述题评分要点
| 评分维度 | 说明 |
| --- | --- |
| **结论明确** | 第一句就给出选择，不要模棱两可 |
| **原理支撑** | 说清技术机制，不是背命令 |
| **对比分析** | 给出备选方案及不选的理由 |
| **场景结合** | 联系题目给出的业务背景 |
| **完整性** | 覆盖部署、可靠性、安全、运维多个维度 |

---

## 18_2 综合实验一：大型企业园区网（完整可练）
### 18_2.1 需求描述
```latex
第1步 网络结构：核心层（2 台）+ 汇聚层（2 台）+ 接入层（若干）
第2步 业务 VLAN：办公 10、无线 20、监控 30、语音 40、管理 99
第3步 核心层做网关（VLANIF），双机 VRRP 负载分担
第4步 汇聚与核心之间跑 OSPF Area 0
第5步 接入层 MSTP 负载分担（奇数/偶数 VLAN 分别走不同汇聚）
第6步 核心双机 Eth-Trunk 互联，接入双上行 Eth-Trunk
第7步 出口路由器做 NAT（Easy IP）+ 默认路由下发
第8步 监控网段禁止访问办公网段
第9步 语音流量优先转发（QoS）
第10步 全网开启 SSH 管理，日志上送网管服务器
```

### 18_2.2 拓扑
```latex
                        Internet
                            │
                     ┌──────┴──────┐
                     │   R-Exit    │  (NAT + 默认路由)
                     └──────┬──────┘
                    172.16.100.0/30
                            │
        ┌───────────────────┴───────────────────┐
        │                                       │
   ┌────┴────┐    Eth-Trunk1（跨框聚合）    ┌────┴────┐
   │ Core-1  │═════════════════════════════│ Core-2  │
   │ (CSS)   │                             │         │
   └────┬────┘                             └────┬────┘
        │  GE0/0/1                         GE0/0/1
        │  10.0.11.0/30                    10.0.12.0/30
   ┌────┴────┐                             ┌────┴────┐
   │  AGG-1  │════════ 10.0.99.0/30 ═══════│  AGG-2  │
   └────┬────┘                             └────┬────┘
        │                                       │
        └───────────────┬───────────────────────┘
                        │
                 ┌──────┴──────┐
                 │   ACC-1     │  (iStack 堆叠)
                 └──────┬──────┘
                   终端（VLAN 10/20/30/40）
```

### 18_2.3 地址规划表
| 项目 | 网段 | Core-1 | Core-2 | 说明 |
| --- | --- | --- | --- | --- |
| 上行 R-Exit | 172.16.100.0/30 | .1 | .2 | 与出口互联 |
| Core-AGG1 | 10.0.11.0/30 | .1 | — | — |
| Core-AGG2 | 10.0.12.0/30 | .1 | — | — |
| AGG 互联 | 10.0.99.0/30 | — | — | AGG1 .1 / AGG2 .2 |
| 管理网段 | 192.168.99.0/24 | .252 | .253 | 网关 .254 |
| VLAN 10 办公 | 192.168.10.0/24 | .252 | .253 | 网关 .254（VRRP） |
| VLAN 20 无线 | 192.168.20.0/24 | .252 | .253 | 网关 .254 |
| VLAN 30 监控 | 192.168.30.0/24 | .252 | .253 | 网关 .254 |
| VLAN 40 语音 | 192.168.40.0/24 | .252 | .253 | 网关 .254 |

**VRRP 主备规划（负载分担）：**

| VLAN | VRID | Master | Backup |
| --- | --- | --- | --- |
| 10 | 10 | Core-1 | Core-2 |
| 20 | 20 | Core-2 | Core-1 |
| 30 | 30 | Core-1 | Core-2 |
| 40 | 40 | Core-2 | Core-1 |
| 99 | 99 | Core-1 | Core-2 |

> 设计要点：**VRID 与 VLAN ID 对齐**，奇数 VLAN 主在 Core-1、偶数 VLAN 主在 Core-2，两台核心都不闲置——这既是负载分担，也是论述题里"为什么选 VRRP 而不选堆叠"的答题素材。

### 18_2.4 配置实现
#### Step 1：Core-1 基础与网关
```latex
<Huawei> system-view
[Huawei] sysname Core-1
[Core-1] vlan batch 10 20 30 40 99

# 上行口（三层）
[Core-1] interface gigabitethernet 0/0/23
[Core-1-GigabitEthernet0/0/23] undo portswitch
[Core-1-GigabitEthernet0/0/23] ip address 172.16.100.1 30
[Core-1-GigabitEthernet0/0/23] quit

# 下联 AGG-1（三层）
[Core-1] interface gigabitethernet 0/0/1
[Core-1-GigabitEthernet0/0/1] undo portswitch
[Core-1-GigabitEthernet0/0/1] ip address 10.0.11.1 30
[Core-1-GigabitEthernet0/0/1] quit

# 核心互联 Eth-Trunk（跨框）
[Core-1] interface eth-trunk 1
[Core-1-Eth-Trunk1] mode lacp-static
[Core-1-Eth-Trunk1] trunkport gigabitethernet 0/0/21
[Core-1-Eth-Trunk1] trunkport gigabitethernet 0/0/22
[Core-1-Eth-Trunk1] port link-type trunk
[Core-1-Eth-Trunk1] port trunk allow-pass vlan 10 20 30 40 99
[Core-1-Eth-Trunk1] load-balance src-dst-ip
[Core-1-Eth-Trunk1] quit

# ===== VLANIF 网关 + VRRP =====
[Core-1] interface Vlanif 10
[Core-1-Vlanif10] ip address 192.168.10.252 24
[Core-1-Vlanif10] vrrp vrid 10 virtual-ip 192.168.10.254
[Core-1-Vlanif10] vrrp vrid 10 priority 120
[Core-1-Vlanif10] vrrp vrid 10 preempt-mode timer delay 20
[Core-1-Vlanif10] vrrp vrid 10 track interface gigabitethernet 0/0/23 reduced 30
[Core-1-Vlanif10] quit

[Core-1] interface Vlanif 20
[Core-1-Vlanif20] ip address 192.168.20.252 24
[Core-1-Vlanif20] vrrp vrid 20 virtual-ip 192.168.20.254
[Core-1-Vlanif20] vrrp vrid 20 priority 100
[Core-1-Vlanif20] quit

[Core-1] interface Vlanif 30
[Core-1-Vlanif30] ip address 192.168.30.252 24
[Core-1-Vlanif30] vrrp vrid 30 virtual-ip 192.168.30.254
[Core-1-Vlanif30] vrrp vrid 30 priority 120
[Core-1-Vlanif30] quit

[Core-1] interface Vlanif 40
[Core-1-Vlanif40] ip address 192.168.40.252 24
[Core-1-Vlanif40] vrrp vrid 40 virtual-ip 192.168.40.254
[Core-1-Vlanif40] vrrp vrid 40 priority 100
[Core-1-Vlanif40] quit
```

#### Step 2：Core OSPF 与默认路由下发
```latex
[Core-1] ospf 1 router-id 1.1.1.1
[Core-1-ospf-1] area 0
[Core-1-ospf-1-area-0.0.0.0] network 10.0.11.0 0.0.0.3
[Core-1-ospf-1-area-0.0.0.0] network 192.168.10.0 0.0.0.255
[Core-1-ospf-1-area-0.0.0.0] network 192.168.20.0 0.0.0.255
[Core-1-ospf-1-area-0.0.0.0] network 192.168.30.0 0.0.0.255
[Core-1-ospf-1-area-0.0.0.0] network 192.168.40.0 0.0.0.255
[Core-1-ospf-1-area-0.0.0.0] quit
[Core-1-ospf-1] default-route-advertise always          # 向内网下发默认路由
[Core-1-ospf-1] quit
[Core-1] ip route-static 0.0.0.0 0 172.16.100.2         # 指向出口路由器
```

#### Step 3：汇聚与接入（MSTP + Eth-Trunk）
```latex
# ===== AGG-1 =====
[AGG-1] vlan batch 10 20 30 40 99
[AGG-1] stp mode mstp
[AGG-1] stp region-configuration
[AGG-1-mst-region] region-name CAMPUS
[AGG-1-mst-region] revision-level 1
[AGG-1-mst-region] instance 1 vlan 10 30          # 奇数 VLAN
[AGG-1-mst-region] instance 2 vlan 20 40          # 偶数 VLAN
[AGG-1-mst-region] active region-configuration    # ★ 必须激活
[AGG-1-mst-region] quit
[AGG-1] stp instance 1 priority 4096              # 实例 1 的主根
[AGG-1] stp instance 2 priority 8192

# 上联 Core-1（三层）
[AGG-1] interface gigabitethernet 0/0/24
[AGG-1-GigabitEthernet0/0/24] undo portswitch
[AGG-1-GigabitEthernet0/0/24] ip address 10.0.11.2 30
[AGG-1-GigabitEthernet0/0/24] quit

# 下联 ACC（Trunk）
[AGG-1] interface gigabitethernet 0/0/1
[AGG-1-GigabitEthernet0/0/1] port link-type trunk
[AGG-1-GigabitEthernet0/0/1] port trunk allow-pass vlan 10 20 30 40 99
[AGG-1-GigabitEthernet0/0/1] undo port trunk allow-pass vlan 1
[AGG-1-GigabitEthernet0/0/1] quit

# ===== ACC-1（堆叠）=====
[ACC-1] stp mode mstp
[ACC-1] stp region-configuration
[ACC-1-mst-region] region-name CAMPUS             # ★ 三要素必须与汇聚完全一致
[ACC-1-mst-region] revision-level 1
[ACC-1-mst-region] instance 1 vlan 10 30
[ACC-1-mst-region] instance 2 vlan 20 40
[ACC-1-mst-region] active region-configuration
[ACC-1-mst-region] quit

# 双上行 Eth-Trunk
[ACC-1] interface eth-trunk 1
[ACC-1-Eth-Trunk1] mode lacp-static
[ACC-1-Eth-Trunk1] trunkport gigabitethernet 1/0/1
[ACC-1-Eth-Trunk1] trunkport gigabitethernet 2/0/1
[ACC-1-Eth-Trunk1] port link-type trunk
[ACC-1-Eth-Trunk1] port trunk allow-pass vlan 10 20 30 40 99
[ACC-1-Eth-Trunk1] quit

# 用户端口（Hybrid：数据 untagged + 语音 tagged）
[ACC-1] interface gigabitethernet 1/0/5
[ACC-1-GigabitEthernet1/0/5] port link-type hybrid
[ACC-1-GigabitEthernet1/0/5] port hybrid pvid vlan 10
[ACC-1-GigabitEthernet1/0/5] port hybrid vlan 10 untagged
[ACC-1-GigabitEthernet1/0/5] port hybrid vlan 40 tagged
[ACC-1-GigabitEthernet1/0/5] stp edged-port enable
[ACC-1-GigabitEthernet1/0/5] quit
```

#### Step 4：出口 NAT 与互访控制
```latex
[R-Exit] acl 2000
[R-Exit-acl-basic-2000] rule permit source 192.168.0.0 0.0.255.255
[R-Exit-acl-basic-2000] quit
[R-Exit] interface gigabitethernet 0/0/0
[R-Exit-GigabitEthernet0/0/0] nat outbound 2000        # Easy IP
[R-Exit-GigabitEthernet0/0/0] quit

# 监控网段（30）禁止访问办公网段第10步
[R-Exit] acl 3001
[R-Exit-acl-adv-3001] rule deny ip source 192.168.30.0 0.0.0.255 destination 192.168.10.0 0.0.0.255
[R-Exit-acl-adv-3001] rule permit ip
[R-Exit-acl-adv-3001] quit
```

### 18_2.5 验收清单
```latex
第1步 display vrrp brief            → 奇数 VLAN 主在 Core-1，偶数 VLAN 主在 Core-2
第2步 display ospf peer             → 核心与汇聚邻居 Full
第3步 display eth-trunk 1           → 成员口均 Selected
第4步 display stp brief             → 实例 1/2 阻塞不同端口（负载分担生效）
第5步 display nat session           → 内网访问外网有会话生成
第6步 display acl 3001              → 监控访问被拒时计数增长
第7步 终端 ping 网关 → ping 外网 → tracert 看路径是否最优
第8步 模拟核心故障：shutdown Core-1 上行，验证 VRRP 切换与业务恢复
```

---

## 18_3 综合实验二：MPLS L3VPN + BGP 骨干
### 18_3.1 需求
```latex
第1步 运营商/大型企业网骨干：PE1 — P — PE2，IGP 用 IS-IS
第2步 骨干网跑 MPLS + LDP
第3步 承载两个客户 VPN：VPN-A（可互通）、VPN-B（完全隔离）
第4步 PE 与 CE 之间用 EBGP 对接
第5步 PE 之间建立 MP-BGP（VPNv4）邻居
```

### 18_3.2 关键配置要点
```latex
# ============ 骨干 IGP（IS-IS） ============
[PE1] isis 1
[PE1-isis-1] network-entity 49.0001.0000.0000.0001.00
[PE1-isis-1] is-level level-2
[PE1-isis-1] cost-style wide
[PE1-isis-1] quit
[PE1] interface gigabitethernet 0/0/0
[PE1-GigabitEthernet0/0/0] isis enable 1
[PE1-GigabitEthernet0/0/0] quit
[PE1] interface loopback 0
[PE1-LoopBack0] isis enable 1
[PE1-LoopBack0] quit

# ============ MPLS/LDP ============
[PE1] mpls lsr-id 1.1.1.1
[PE1] mpls
[PE1-mpls] quit
[PE1] mpls ldp
[PE1-mpls-ldp] quit
[PE1] interface gigabitethernet 0/0/0
[PE1-GigabitEthernet0/0/0] mpls
[PE1-GigabitEthernet0/0/0] mpls ldp
[PE1-GigabitEthernet0/0/0] quit

# ============ VPN 实例（两个客户） ============
[PE1] ip vpn-instance VPN-A
[PE1-vpn-instance-VPN-A] route-distinguisher 100:1
[PE1-vpn-instance-VPN-A] vpn-target 100:1 export-extcommunity
[PE1-vpn-instance-VPN-A] vpn-target 100:1 import-extcommunity
[PE1-vpn-instance-VPN-A] quit

[PE1] ip vpn-instance VPN-B
[PE1-vpn-instance-VPN-B] route-distinguisher 200:1
[PE1-vpn-instance-VPN-B] vpn-target 200:1 export-extcommunity
[PE1-vpn-instance-VPN-B] vpn-target 200:1 import-extcommunity
[PE1-vpn-instance-VPN-B] quit

# ============ CE 接口绑定 ============
[PE1] interface gigabitethernet 0/0/1
[PE1-GigabitEthernet0/0/1] ip binding vpn-instance VPN-A
[PE1-GigabitEthernet0/0/1] ip address 10.1.11.1 24
[PE1-GigabitEthernet0/0/1] quit

# ============ PE-CE 之间 EBGP ============
[PE1] bgp 100
[PE1-bgp] ipv4-family vpn-instance VPN-A
[PE1-bgp-VPN-A] peer 10.1.11.2 as-number 65001
[PE1-bgp-VPN-A] quit

# ============ PE 之间 MP-BGP ============
[PE1] bgp 100
[PE1-bgp] peer 3.3.3.3 as-number 100
[PE1-bgp] peer 3.3.3.3 connect-interface LoopBack 0
[PE1-bgp] ipv4-family vpnv4
[PE1-bgp-af-vpnv4] peer 3.3.3.3 enable
[PE1-bgp-af-vpnv4] quit
```

### 18_3.3 验收
```latex
[PE1] display mpls ldp session               # Operational
[PE1] display mpls lsp                       # 到 3.3.3.3 的 LSP 完整
[PE1] display bgp vpnv4 all peer             # Established
[PE1] display bgp vpnv4 vpn-instance VPN-A routing-table    # 学到对端 CE 路由
[PE1] ping -vpn-instance VPN-A 10.2.11.2     # ★ 带 VPN 实例 ping

# 隔离验证：VPN-A 的 CE 应 ping 不通 VPN-B 的网段
```

> ★ **必记命令**：`ping -vpn-instance VPN-A x.x.x.x`。普通 ping 走的是全局路由表，永远测不通 VPN 业务——这是 VPN 排错时最高频的"假故障"。

---

## 18_4 论述题答题框架（可套用模板）
### 18_4.1 通用六段式
```latex
第1步 结论：     第一句给出选型（例："本方案核心层采用 CSS 集群 + Eth-Trunk，而非堆叠"）
第2步 需求回扣： 题目中的哪些约束决定了这个选择（规模、可靠性要求、业务类型）
第3步 方案说明： 怎么部署（拓扑、协议、关键参数）
第4步 对比取舍： 备选方案是什么，为什么不选（★ 这一段最拉分）
第5步 风险与应对：单点、收敛时间、割接风险，以及 mitigation
第6步 运维视角： 如何监控、如何扩容、如何排错
```

**答题时间控制**：论述题 60 分钟内写 2–3 道，每道控制在 15–20 分钟，**结论段必须先写**（即使后面没写完，结论也在）。

### 18_4.2 常见论述题与答题要点
| 论述题 | 答题要点 |
| --- | --- |
| **堆叠 vs M-LAG** | 堆叠：配置简单、一台逻辑设备，但升级需整机重启、控制面耦合；M-LAG：两台独立控制面、可独立升级、可靠性更高，但配置复杂、需 peer-link。结论：核心层追求独立升级选 M-LAG，接入层追求易管理选堆叠 |
| **OSPF vs IS-IS** | OSPF：区域基于接口、企业网主流、资料多；IS-IS：TLV 扩展性好、基于路由器分区域、收敛快、运营商首选。结论：大型骨干/承载网选 IS-IS，园区网选 OSPF |
| **集中式 vs 分布式网关（VXLAN）** | 集中式：配置简单策略集中，但流量绕行、单点风险；分布式（Anycast）：路径最优、无绕行，但配置复杂。结论：规模大、东西向流量多必须分布式 |
| **MPLS L3VPN 跨域 Option A/B/C** | A：简单、ASBR 之间按 VPN 建子接口，扩展性差；B：ASBR 之间 MP-BGP 传标签路由，主流；C：PE 之间直接建多跳 EBGP，控制面复杂但转发最优 |
| **静态 vs 动态路由** | 静态：可控、无开销，但无故障感知；动态：自动收敛，但有资源开销。结论：小型/边缘用静态（配 BFD/NQA 联动），核心用动态 |
| **园区网要不要上 VXLAN** | 看规模与业务随行需求：多业务隔离、用户位置无关、终端规模大 → 上；传统固定工位、规模小 → VLAN + VLANIF 足够 |

---

## 18_5 实验冲刺训练计划
### 18_5.1 每日训练模板（考前 2 个月）
```latex
工作日（每天 2 小时）：
  19:00–19:30  背命令/默认参数（纯记忆卡片）
  19:30–21:00  搭一个技术点实验（OSPF/BGP/MPLS/VXLAN 轮换）

周末（每天 6 小时）：
  上午  完整综合实验一遍（计时，模拟 480 分钟压缩到 4 小时）
  下午  排错专项（让同伴埋故障，限时 45 分钟）
  晚上  论述题 2 道（手写，不用复制粘贴）
```

### 18_5.2 速度训练目标
| 项目 | 目标时间 | 说明 |
| --- | --- | --- |
| 设备开局（命名/VLAN/接口 IP） | ≤ 15 min/台 | 模板化，肌肉记忆 |
| OSPF 多区域打通 | ≤ 20 min | 含验证 |
| BGP + 路由策略 | ≤ 30 min | 含 IP-Prefix + Route-Policy |
| MPLS L3VPN 单域 | ≤ 40 min | 含 LDP、VPN 实例、MP-BGP |
| 排错（单故障） | ≤ 10 min | 含恢复与记录 |

> 速度的本质是**模板化**：把每类配置写成自己的"标准片段库"，考试时是"调取 + 微调"，而不是"现场组织语言"。

### 18_5.3 常见失误清单（考前必查）
```latex
□ 忘记 save（每完成一个模块就存一次）
□ MSTP 忘记 active region-configuration
□ 子接口忘记 arp broadcast enable
□ IBGP 忘记 next-hop-local
□ BGP network 的网段与路由表掩码不完全匹配
□ VRRP 忘记配 track（上行断了不切换）
□ BFD 会话忘记 commit
□ Eth-Trunk 先配物理口再加组（顺序反了会冲突）
□ VXLAN 两端 VNI/BD 不一致
□ 未考虑 MTU（MPLS +4 字节/层，VXLAN +50 字节）
□ 改完配置没验证就往下做
□ 排错时一头扎进根因，忘了先恢复业务
```

---

## 18_6 案例：480 分钟里最贵的那 20 分钟
> 一位考生第一次考 HCIE 实验，部署部分做得很顺，到 6 小时结束时只剩 15 分钟，论述题还没动笔。结果部署拿了 55 分，论述 0 分，总分 55，差 25 分。
> 第二次他改了策略：**进场先花 30 分钟规划，每完成一个模块立刻 save + 验证，论述题在第 4 小时就开始写**（边做边写，把方案说明穿插在技术点之间）。最后留了 50 分钟做排错与复查，顺利通过。
> 两次的差别不在技术，而在**节奏**。480 分钟里最贵的不是最后那 20 分钟，而是**没有规划就开敲的头 60 分钟**——它会在第 5 小时以"返工"的形式加倍还回来。

---

## 18_7 场景笔记与验证
### 18_7.1 本板块要沉淀的笔记
| 笔记 | 内容 |
| --- | --- |
| **时间分配卡** | 规划 30 / 基础 60 / 部署 180 / 验证 60 / 排错 45 / 论述 60 / 缓冲 45 |
| **优先级卡** | 地基 → 主干 → 增强 → 优化 → 排错（先恢复后根治） |
| **论述六段式** | 结论 → 需求 → 方案 → 对比取舍 → 风险 → 运维 |
| **模板库** | 开局、OSPF、BGP/策略、MPLS VPN、VRRP、VXLAN 各一份标准片段 |
| **失误清单** | 见 18_5.3，考前一天逐条过 |

### 18_7.2 验证三板斧（实验版）
```latex
第1步 每配完一个技术点立刻 display 验证（不要攒到最后）
第2步 每完成一个模块立刻 save（防止提交不可撤回造成返工）
第3步 排错先恢复业务（ping 通）再补正式修复与根因说明
```

### 18_7.3 建议做一次的模拟
按真实节奏做一次 **4 小时压缩版综合实验**（园区网或 MPLS 骨干二选一），全程计时、不查资料、边配边验，结束后按 18_5.3 的失误清单给自己打分。

**能连续两次在压缩时间内跑通，考场的 480 分钟就会显得很宽裕。**

---

## 18_8 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | 部署越快越好 | **边配边验**才是真快，返工才是真慢 |
| 2 | 论述题最后写 | 应**穿插写**，至少保证结论段完成 |
| 3 | 排错要找到根因才算完 | **先恢复业务**，根因写在报告里 |
| 4 | save 一次就够 | **每个模块**完成后都存一次 |
| 5 | 部署完再统一验证 | 攒到最后等于没时间改 |
| 6 | 论述题写越长越好 | 评分看**结论 + 对比取舍 + 场景结合**，不是字数 |
| 7 | 排错 15 分不如部署 | 排错**单位时间得分最高**，45 分钟拿 15 分 |
| 8 | 模板背下来就够 | 要能**按题目约束裁剪**，生搬硬套会答偏 |

---

> **下一步**：拿着这份知识库，走进考场 —— 然后回头把你的经验补进这份笔记里。

# 板块19 · 附录：命令速查、设备命名与实验清单
> 定位：考前速查手册 + 日常运维备查表。建议**单独打印**放在手边，考前最后几天反复过。
> 使用说明：所有命令以 **VRP V200R 系列（S 系列交换机 / AR 系列路由器）**为准；CloudEngine 数据中心交换机（CE 系列）部分命令一致，但接口命名为 `10GE 1/0/1`、`100GE 1/0/1` 格式。

## 19_1 通用命令速查
### 19_1.1 视图与基础操作
| 功能 | 命令 |
| --- | --- |
| 进入系统视图 | `system-view` |
| 返回上级视图 | `quit` |
| 返回用户视图 | `return` / `Ctrl+Z` |
| 设备命名 | `sysname SW-01` |
| 查看当前配置 | `display current-configuration` |
| 查看保存配置 | `display saved-configuration` |
| 保存配置 | `save` |
| 清除保存配置（**用户视图**） | `reset saved-configuration` |
| 重启 | `reboot` |
| 查看版本 | `display version` |
| 查看硬件 | `display device` |
| 设置时区 | `clock timezone BJ add 08:00:00` |
| 设置时间 | `clock datetime 14:30:00 2026-08-14` |
| NTP | `ntp-service unicast-server x.x.x.x` |
| 帮助 | `?` / `Tab` 补全 |
| 过滤输出 | `| include` / `| exclude` / `| begin` / `| section` |
| 查看在线用户 | `display users` |
| 踢掉某个登录 | `free user-interface vty 0` |
| 关闭分页（脚本必需） | `screen-length 0 temporary` |

### 19_1.2 接口与链路
| 功能 | 命令 |
| --- | --- |
| 端口描述 | `description "Uplink-to-Core"` |
| 全双工 | `duplex full` |
| 速率 | `speed 1000` |
| 流控 | `flow-control` |
| 网线自适应 | `mdi auto` |
| 激活端口 | `undo shutdown` |
| 端口信息 | `display interface g0/0/1` |
| 端口摘要 | `display interface brief` |
| 端口描述一览 | `display interface description` |
| 光模块信息 | `display transceiver interface g0/0/1` |
| 清空统计 | `reset counters interface g0/0/1` |
| 二层口转三层口 | `undo portswitch` |
| 配置 IP | `ip address 192.168.1.1 24` |
| 接口摘要（三层） | `display ip interface brief` |
| MTU | `mtu 9000` |
| TCP MSS | `tcp adjust-mss 1452` |

### 19_1.3 端口组（批量操作）
| 功能 | 命令 |
| --- | --- |
| 临时端口组 | `port-group group-member g0/0/1 to 0/0/24` |
| 永久端口组 | `port-group pg-office` → `group-member g0/0/1 to 0/0/24` |
| VLAN 视图加端口 | `[SW-vlan10] port g0/0/1 to 0/0/29` |
| 端口限速 | `qos lr outbound cir 2000 cbs 20000` |

### 19_1.4 系统健康与日志
| 功能 | 命令 |
| --- | --- |
| 系统时间 | `display clock` |
| CPU | `display cpu-usage` / `display cpu-usage task` |
| 内存 | `display memory` |
| 温度 | `display environment` |
| 电源/风扇 | `display power` / `display fan` |
| 日志缓冲 | `display logbuffer` |
| 告警缓冲 | `display trapbuffer` |
| 日志服务器 | `info-center loghost 192.168.1.200` |
| 关闭/恢复提示 | `info-center source DS channel 0 log state off/on` |
| 一键诊断 | `display diagnostic-information` |
| CPU 防御统计 | `display cpu-defend statistics` |
| NTP 状态 | `display ntp-service status` / `display ntp-service sessions` |
| LLDP 邻居 | `lldp enable` + `display lldp neighbor brief` |

---

## 19_2 二层技术命令速查
### 19_2.1 VLAN
| 功能 | 命令 |
| --- | --- |
| 创建 VLAN | `vlan 10` / `vlan batch 10 20 30` / `vlan batch 10 to 100` |
| VLAN 描述 | `[SW-vlan10] description Office` |
| Access 口 | `port link-type access` + `port default vlan 10` |
| Trunk 口 | `port link-type trunk` + `port trunk allow-pass vlan 10 20` |
| Trunk PVID | `port trunk pvid vlan 99` |
| Hybrid PVID | `port hybrid pvid vlan 10` |
| Hybrid untagged | `port hybrid vlan 10 20 untagged` |
| Hybrid tagged | `port hybrid vlan 40 tagged` |
| 查看 VLAN | `display vlan` / `display vlan 10` |
| 端口 VLAN | `display port vlan` |
| Trunk 详情 | `display interface g0/0/24 trunk` |
| MUX VLAN | `mux-vlan` + `subordinate separate/group` |
| QinQ | `qinq vid 1000` + `raw-vlan-id inbound 10` |
| GVRP | `gvrp`（全局 + 接口） |

### 19_2.2 MAC 地址表
| 功能 | 命令 |
| --- | --- |
| 查看 MAC | `display mac-address` |
| 静态 MAC | `mac-address static xxxx-xxxx-xxxx g1/0/1 vlan 10` |
| 黑洞 MAC | `mac-address blackhole xxxx-xxxx-xxxx vlan 10` |
| 老化时间 | `mac-address timer aging 300` |
| 不老化 | `mac-address timer no-aging` |
| **MAC 漂移检测** | `mac-address flapping detection` |
| 漂移记录 | `display mac-address flapping record` |

### 19_2.3 STP
| 功能 | 命令 |
| --- | --- |
| 开启 STP | `stp enable`（默认开启，模式 mstp） |
| 切换模式 | `stp mode stp / rstp / mstp` |
| 桥优先级 | `stp priority 8192` |
| 主/备根 | `stp root primary` / `stp root secondary` |
| 实例优先级 | `stp instance 1 priority 4096` |
| 端口开销 | `stp cost 200` |
| 边缘端口 | `stp edged-port enable`（全局 `stp edged-port default`） |
| BPDU 保护 | `stp bpdu-protection` |
| 根保护 | `stp root-protection` |
| 环路保护 | `stp loop-protection` |
| TC 保护 | `stp tc-protection` |
| 开销标准 | `stp pathcost-standard dot1t` |
| 自动恢复 | `error-down auto-recovery cause bpdu-protection interval 300` |
| MSTP 域 | `stp region-configuration` → `region-name` / `revision-level` / `instance x vlan y` |
| **激活域配置** | `active region-configuration` |
| 查看 | `display stp brief` / `display stp root` / `display stp region-configuration` |
| TC 统计 | `display stp tc-bpdu statistics` |
| 风暴控制 | `storm-control broadcast min-rate 100 max-rate 500` + `storm-control action block` |
| 广播抑制 | `broadcast-suppression 5`（按百分比） |

### 19_2.4 Eth-Trunk / 堆叠
| 功能 | 命令 |
| --- | --- |
| 创建聚合口 | `interface eth-trunk 1` |
| LACP 模式 | `mode lacp-static` |
| 加入成员 | `trunkport g0/0/1 to 0/0/2` |
| 最大活动链路 | `max active-linknumber 2` |
| 抢占 | `lacp preempt enable` + `lacp preempt delay 10` |
| 负载均衡 | `load-balance src-dst-ip` |
| 查看 | `display eth-trunk 1` / `display eth-trunk verbose` / `display lacp statistics eth-trunk 1` |
| 堆叠优先级 | `stack slot 0 priority 200` |
| 改堆叠 ID | `stack slot 0 renumber 1`（重启生效） |
| 堆叠口 | `interface stack-port 0/1` + `port member-group interface g0/0/27` |
| 集群 | `css` + `css member 1` + `css priority 150` |
| MAD 直连 | `mad detect mode direct` |
| MAD 中继 | `mad detect mode relay` |
| MAD 恢复 | `mad restore` |
| 查看 | `display stack` / `display css status` / `display mad verbose` |
| M-LAG（CE） | `dfs-group 1` + `peer-link 1` + `dfs-group 1 m-lag 1` |
| M-LAG 查看 | `display dfs-group 1 m-lag` / `display dfs-group 1 node 1` |

---

## 19_3 三层与路由命令速查
### 19_3.1 三层接口与路由表
| 功能 | 命令 |
| --- | --- |
| 创建 VLANIF | `interface Vlanif 10` + `ip address x.x.x.x 24` |
| 子接口 | `interface g0/0/1.10` + `dot1q termination vid 10` |
| **子接口 ARP 广播** | `arp broadcast enable`（★ 常漏） |
| 静态路由 | `ip route-static 目的 掩码 下一跳` |
| 默认路由 | `ip route-static 0.0.0.0 0 x.x.x.x` |
| 浮动路由 | `ip route-static ... preference 100` |
| 黑洞路由 | `ip route-static 10.0.0.0 8 NULL 0` |
| 查看路由表 | `display ip routing-table` |
| 指定路由 | `display ip routing-table 192.168.1.0` |
| 协议路由 | `display ip routing-table protocol ospf` |
| FIB | `display fib` |
| ARP 表 | `display arp` |
| 静态 ARP | `arp static 192.168.1.1 xxxx-xxxx-xxxx` |
| 二层口转三层 | `undo portswitch` |
| 查看端口 VLAN | `display port vlan` / `display interface brief` |
| 查看单接口配置 | `display current-configuration interface g0/0/1` |

### 19_3.2 RIP
| 功能 | 命令 |
| --- | --- |
| 启用 | `rip 1` + `version 2` + `network 192.168.1.0` |
| 关闭汇总 | `undo summary` |
| 认证 | `rip authentication-mode md5 usual cipher xxx` |
| 查看 | `display rip` / `display rip 1 database` |

### 19_3.3 OSPF
| 功能 | 命令 |
| --- | --- |
| 启用 | `ospf 1 router-id 1.1.1.1` |
| 区域宣告 | `area 0` + `network 192.168.1.0 0.0.0.255` |
| 接口使能 | `[接口] ospf enable 1 area 0` |
| 参考带宽 | `bandwidth-reference 100000` |
| 接口开销 | `ospf cost 100` |
| 网络类型 | `ospf network-type p2p` |
| 定时器 | `ospf timer hello 1` / `ospf timer dead 4` |
| DR 优先级 | `ospf dr-priority 100` |
| 区域认证 | `authentication-mode md5 1 cipher xxx` |
| 接口认证 | `ospf authentication-mode md5 1 cipher xxx` |
| 静默接口 | `silent-interface Vlanif10` |
| 引入路由 | `import-route static / direct / bgp` |
| 下发默认路由 | `default-route-advertise always` |
| ABR 汇总 | `abr-summary 192.168.0.0 255.255.240.0` |
| ASBR 汇总 | `asbr-summary 172.16.0.0 255.255.240.0` |
| Stub | `stub` / `stub no-summary` |
| NSSA | `nssa` / `nssa no-summary` |
| 虚链路 | `vlink-peer 3.3.3.3` |
| BFD | `bfd all-interfaces enable` |
| 忽略 MTU 检查 | `ospf mtu-enable`（接口下） |
| 查看 | `display ospf peer` / `display ospf peer brief` / `display ospf error` / `display ospf routing` |
| 接口/LSDB | `display ospf interface` / `display ospf lsdb` |
| 虚链路查看 | `display ospf vlink` |
| 取消静默 | `undo silent-interface Vlanif10` |

### 19_3.4 IS-IS
| 功能 | 命令 |
| --- | --- |
| 启用 | `isis 1` + `network-entity 49.0001.0000.0000.0001.00` |
| 级别 | `is-level level-2` |
| 宽度量 | `cost-style wide` |
| 接口使能 | `isis enable 1` |
| 链路类型 | `isis circuit-type p2p` |
| 开销 | `isis cost 10` / `auto-cost enable` |
| 路由渗透 | `import-route isis level-2 into level-1` |
| 认证 | `area-authentication-mode md5` / `domain-authentication-mode md5` |
| 查看 | `display isis peer` / `display isis lsdb` / `display isis route` |

### 19_3.5 BGP
| 功能 | 命令 |
| --- | --- |
| 启用 | `bgp 65001` + `router-id 1.1.1.1` |
| 建邻 | `peer 10.1.1.2 as-number 65002` |
| 换源接口 | `peer x.x.x.x connect-interface LoopBack 0` |
| 发布路由 | `network 10.1.1.0 255.255.255.0`（★ 须与路由表精确匹配） |
| IBGP 改下一跳 | `peer x.x.x.x next-hop-local` |
| 非直连 EBGP | `peer x.x.x.x ebgp-max-hop 2` |
| 路由反射器 | `peer x.x.x.x reflect-client` |
| 团体属性 | `peer x.x.x.x advertise-community` |
| 引入 | `import-route direct / static / ospf 1` |
| 聚合 | `aggregate 10.1.0.0 255.255.0.0 detail-suppressed` |
| 首选值（华为私有） | `peer x.x.x.x preferred-value 100`（越大越优，仅本机有效） |
| 发布团体属性 | `peer x.x.x.x advertise-community`（★ 不配则不传递） |
| 联盟 | `confederation id 65001` + `confederation peer-as 65002` |
| 路由衰减查看 | `display bgp routing-table flap-info` |
| TCP 连接查看 | `display tcp status`（BGP 卡 Active 时查） |
| 查看 | `display bgp peer` / `display bgp routing-table` / `display bgp vpnv4 all routing-table` |

### 19_3.6 路由策略工具
| 功能 | 命令 |
| --- | --- |
| 前缀列表 | `ip ip-prefix PL-1 index 10 permit 10.1.0.0 16` |
| 策略 | `route-policy RP-1 permit node 10` + `if-match ip-prefix PL-1` + `apply cost 100` |
| 团体过滤 | `ip community-filter 1 permit 100:1` |
| AS_Path 过滤 | `ip as-path-filter 1 permit ^65001$` |
| 应用（peer） | `peer x.x.x.x route-policy RP-1 export` |
| 应用（引入） | `import-route ospf 1 route-policy RP-1` |
| 过滤策略 | `filter-policy ip-prefix PL-1 export` |
| 匹配路由类型 | `if-match route-type internal/external` |
| 修改 Origin | `apply origin igp/incomplete` |
| 策略查看 | `display route-policy` / `display ip ip-prefix` |

---

## 19_4 业务与安全命令速查
### 19_4.1 DHCP
| 功能 | 命令 |
| --- | --- |
| 开启服务 | `dhcp enable` |
| 全局地址池 | `ip pool POOL-10` → `network 192.168.10.0 mask 24` |
| 网关 | `gateway-list 192.168.10.254` |
| DNS | `dns-list 114.114.114.114` |
| 租期 | `lease day 1 hour 0 minute 0` |
| 排除地址 | `excluded-ip-address 192.168.10.1 192.168.10.10` |
| 静态绑定 | `static-bind ip-address x.x.x.x mac-address xxxx-xxxx-xxxx` |
| 接口地址池 | `[Vlanif10] dhcp select interface`（用接口网段做池，小型场景） |
| 接口启用 | `[Vlanif10] dhcp select global` |
| 中继 | `[Vlanif10] dhcp select relay` + `dhcp relay server-ip 192.168.1.100` |
| 查看 | `display ip pool` / `display ip pool name POOL-10 used` |

### 19_4.2 ACL / NAT / 策略路由
| 功能 | 命令 |
| --- | --- |
| 基本 ACL | `acl 2000` + `rule 5 permit source 192.168.1.0 0.0.0.255` |
| 高级 ACL | `acl 3000` + `rule deny tcp source x destination y destination-port eq 80` |
| 二层 ACL | `acl 4000` + `rule permit 8021p 6` |
| 应用过滤 | `[接口] traffic-filter inbound acl 3000` |
| 查看 ACL | `display acl 3000` / `display acl all` / `display traffic-filter applied-record` |
| 时间段 | `time-range WORKTIME 08:00 to 18:00 working-day` |
| NAPT（地址池） | `nat address-group 1 202.1.1.10 202.1.1.20` + `nat outbound 2000 address-group 1` |
| No-PAT（只换地址） | `nat outbound 2000 address-group 1 no-pat` |
| Easy IP | `[接口] nat outbound 2000` |
| NAT Server | `nat server protocol tcp global x 80 inside y 80` |
| NAT ALG | `nat alg ftp enable` |
| 查看会话 | `display nat session` |
| PBR 分类 | `traffic classifier` + `if-match acl 3001` |
| PBR 行为 | `traffic behavior` + `redirect ip-nexthop 202.1.1.1` |
| PBR 应用 | `[接口] traffic-policy P-PBR inbound` |

### 19_4.3 安全特性
| 功能 | 命令 |
| --- | --- |
| 端口安全 | `port-security enable` + `port-security max-mac-num 2` |
| 粘性 MAC | `port-security mac-address sticky` |
| DHCP Snooping | `dhcp snooping enable ipv4` + VLAN 下 `dhcp snooping enable` |
| 信任端口 | `dhcp snooping trusted interface g0/0/1` |
| DAI | `arp anti-attack check user-bind enable` |
| IPSG | `ip source check user-bind enable` |
| 静态绑定表 | `user-bind static ip-address x mac-address x interface g0/0/5 vlan 10` |
| 802.1X | `dot1x enable`（全局 + 接口） |
| AAA 域 | `aaa` → `domain default` → `authentication-scheme` |
| 本地用户 | `local-user admin password cipher xxx privilege level 3` |
| SSH 服务 | `stelnet server enable` + `ssh user admin service-type stelnet` |
| ARP 限速 | `arp anti-attack rate-limit 50` |
| 网关地址冲突检测 | `arp anti-attack gateway-duplicate enable` |
| 端口隔离 | `port isolate`（同 VLAN 内二层隔离） |
| 静态安全 MAC | `mac-address security xxxx-xxxx-xxxx vlan 1` |
| 端口安全动作 | `port-security protect-action restrict` |
| RADIUS 服务器 | `radius-server authentication 192.168.99.100 1812`（模板视图下） |
| 认证连通性测试 | `test-aaa user001 pwd radius-template RD1` |
| 在线用户 | `display access-user` |
| error-down 自动恢复 | `error-down auto-recovery cause bpdu-protection interval 300` |
| VTY 限定 | `[ui-vty] protocol inbound ssh` + `acl 2000 inbound` |

### 19_4.4 可靠性
| 功能 | 命令 |
| --- | --- |
| VRRP 组 | `vrrp vrid 1 virtual-ip 192.168.1.254` |
| 优先级 | `vrrp vrid 1 priority 120` |
| 抢占延迟 | `vrrp vrid 1 preempt-mode timer delay 20` |
| 跟踪接口 | `vrrp vrid 1 track interface g0/0/24 reduced 30` |
| 跟踪 BFD | `vrrp vrid 1 track bfd-session 10 reduced 30` |
| 查看 | `display vrrp brief` |
| BFD 会话 | `bfd name bind peer-ip x source-ip y` + `discriminator local/remote` + `commit` |
| BFD 联动 | `ip route-static ... track bfd-session name` |
| 协议 BFD | `[ospf-1] bfd all-interfaces enable` |
| 查看 BFD | `display bfd session all` |
| 接口备份 | `[主接口] standby interface g0/0/2` |
| Smart Link | `smart-link group 1` + `port g0/0/1 master` |
| FRR | `[ospf-1] frr` + `loop-free-alternate` |
| DLDP | `dldp enable` + `dldp work-mode enhance`（全局 + 接口） |
| NQA 探测 | `nqa test-instance admin icmp` → `test-type icmp` → `start now` |

### 19_4.5 QoS
| 功能 | 命令 |
| --- | --- |
| 分类器 | `traffic classifier VOICE` + `if-match dscp ef` |
| 行为 | `traffic behavior BE-VOICE` + `queue llq` |
| 策略 | `qos policy P1` + `classifier VOICE behavior BE-VOICE` |
| 应用 | `[接口] qos apply policy P1 outbound` |
| 限速 | `car cir 1024 cbs 2048` |
| 接口限速 | `qos lr outbound cir 2000` |
| 整形 | `qos queue 0 shaping cir 100000` |
| LLQ 带宽 | `queue llq bandwidth pct 10` |
| 队列长度 | `queue length 100` / `[接口] qos queue 5 length 100` |
| WRED 阈值 | `color green low-limit 30 high-limit 80` |
| 重标记 | `remark dscp ef` |
| 队列模板 | `qos queue-profile` + `queue 5 pq` / `queue 5 weight 20` |
| 信任 | `trust dscp` / `trust 8021p` |
| 查看 | `display qos policy interface g0/0/1` |

### 19_4.6 MPLS / VPN / VXLAN
| 功能 | 命令 |
| --- | --- |
| LSR ID | `mpls lsr-id 1.1.1.1` |
| 使能 MPLS/LDP | `mpls` + `mpls ldp` |
| 接口使能 | `[接口] mpls` + `mpls ldp` |
| 查看 LSP | `display mpls lsp` / `display mpls ldp session` |
| VPN 实例 | `ip vpn-instance VPN-A` + `route-distinguisher 100:1` |
| RT | `vpn-target 100:1 export-extcommunity` / `import-extcommunity` |
| 接口绑定 | `[接口] ip binding vpn-instance VPN-A` |
| MP-BGP | `ipv4-family vpnv4` + `peer x.x.x.x enable` |
| 带实例 ping | `ping -vpn-instance VPN-A 10.1.1.2` |
| BD | `bridge-domain 10` + `vxlan vni 10` |
| NVE | `interface Nve 1` + `source 1.1.1.1` + `vni 10 head-end peer-list 2.2.2.2` |
| EVPN 实例 | `evpn vpn-instance E1 bd-mode` + `evpn binding vpn-instance E1` |
| EVPN 地址族 | `l2vpn-family evpn` + `peer x enable` |
| EVPN 关 RT 过滤（RR） | `undo policy vpn-target` |
| 头端复制（EVPN 方式） | `vni 10 head-end peer-list protocol bgp` |
| 查看 | `display vxlan vni` / `display vxlan tunnel` / `display bgp evpn peer` / `display bgp evpn all routing-table` |

### 19_4.7 组播 / IPv6
| 功能 | 命令 |
| --- | --- |
| 组播路由 | `multicast routing-enable` |
| PIM | `pim` + `static-rp 2.2.2.2` + 接口 `pim sm` |
| IGMP | `[接口] igmp enable` + `igmp version 2` |
| SSM 范围 | `ssm-policy 2001` + ACL 放行 232.0.0.0/8 |
| BSR/C-RP | `c-bsr g0/0/1` / `c-rp g0/0/1` |
| Snooping | `igmp-snooping enable` + `igmp-snooping querier enable` + VLAN 下使能 |
| 绑定表 | `display dhcp snooping user-bind all` |
| 组播查看 | `display pim neighbor` / `display igmp group` / `display multicast rpf-info` |
| IPv6 使能 | `ipv6`（全局）+ `ipv6 enable`（接口） |
| IPv6 地址 | `ipv6 address 2001:db8:1::1 64` |
| IPv6 静态 | `ipv6 route-static :: 0 2001:db8:12::2` |
| OSPFv3 | `ospfv3 1` + 接口 `ospfv3 1 area 0` |
| BGP4+ | `ipv6-family unicast` + `peer x enable` |
| RA 放行 | `undo ipv6 nd ra halt` |
| 查看 | `display ipv6 routing-table` / `display ipv6 neighbors` |

### 19_4.8 自动化
| 功能 | 命令 |
| --- | --- |
| NETCONF | `netconf` + `protocol inbound ssh port 830` |
| SSH 子系统 | `ssh server netconf` |
| 生成 RSA 密钥 | `rsa local-key-pair create`（首次启用 SSH 必做） |
| SSH 用户类型 | `ssh user x service-type snetconf` |
| 查看会话 | `display netconf session` / `display netconf capability` |
| Telemetry | `telemetry` → `sensor-group` / `destination-group` / `subscription` |
| OPS | `ops` + `script-assistant python xxx.py` |
| 查看 | `display telemetry subscription` / `display ops script` |

---

## 19_5 华为设备命名规则
### 19_5.1 交换机型号解读
```latex
以 S5731-S24T4X 为例：

  S 5 7 3 1 - S 2 4 T 4 X
  │ │ │ │ │   │ │ │ │ │ │
  │ │ │ │ │   │ │ │ │ │ └── X：万兆上行（10GE）
  │ │ │ │ │   │ │ │ │ └──── 4：4 个万兆口
  │ │ │ │ │   │ │ │ └────── T：电口（双绞线）
  │ │ │ │ │   │ │ └──────── 24：24 个下行口
  │ │ │ │ │   │ └────────── 子系列（S = Standard）
  │ │ │ │ │   └──────────── 系列后缀
  │ │ │ │ └──────────────── 产品代次
  │ │ │ └────────────────── 7：高端（越大越高）
  │ │ └──────────────────── 7 系列
  │ └────────────────────── 5：交换机
  └──────────────────────── S：Switch
```

### 19_5.2 软件版本后缀
| 后缀 | 含义 |
| --- | --- |
| `V200R019C10` | V200 = 平台版本，R019 = 主版本，C10 = 次版本 |
| `C00SPCxxx` | 补丁版本 |
| `V100R006` | CloudEngine 系列常见版本线 |

### 19_5.3 上行端口类型后缀
| 后缀 | 含义 |
| --- | --- |
| `T` | 电口（RJ45） |
| `P` | 光口（SFP） |
| `X` | 万兆（SFP+） |
| `Q` | 40GE |
| `C` | 100GE |

### 19_5.4 常见系列定位
| 系列 | 定位 |
| --- | --- |
| S1700 / S2700 | 入门级二层接入 |
| S3700 / S5700 | 园区接入/汇聚主力（考试最常接触） |
| S6700 / S7700 | 汇聚/核心，支持堆叠与高级特性 |
| S9700 / S12700 | 核心/园区核心，框式 |
| CloudEngine（CE） | 数据中心交换机 |
| AR 系列（AR1200/2200/3200） | 路由器，企业分支与出口 |

### 19_5.5 接口编号规则
```latex
盒式：GigabitEthernet 0/0/1      →  槽位0/子卡0/端口号1
框式：GigabitEthernet 1/0/1      →  槽位1/子卡0/端口号1
堆叠：GigabitEthernet 1/0/1      →  成员1（堆叠 ID）/子卡/端口
CE：  10GE 1/0/1                 →  10GE 接口，槽位1/子卡0/端口1
```

> 排错冷知识：堆叠后端口编号变成 `x/0/y`，**x 就是堆叠 ID**。看到 `2/0/5` 报障，第一反应是"这是堆叠成员 2 上的 5 号口"，而不是"第 2 槽位"。

---

## 19_6 实验清单（从入门到 HCIE）
### 19_6.1 HCIA 阶段（15 个必做实验）
```latex
 1. eNSP 安装与第一个拓扑（两台设备 ping 通）
 2. 交换机开局（命名/时间/管理 IP/保存）
 3. Console 与 Telnet 登录配置
 4. SSH 登录 + ACL 限制源
 5. 单交换机 VLAN 划分与 Access 口
 6. 跨交换机 Trunk 配置与验证
 7. Hybrid 口（语音 + 数据共口）
 8. port-group 批量配置
 9. VLANIF 三层互通（两个 VLAN 互 ping）
10. 单臂路由（子接口 + arp broadcast enable）
11. 静态路由 + 默认路由（三网段互通）
12. 浮动静态路由（主备切换验证）
13. 基本 ACL 限制 VTY 登录源
14. 高级 ACL 限制网段互访
15. Easy IP 出网（NAT）
```

### 19_6.2 HCIP 阶段（15 个进阶实验）
```latex
 1. STP/RSTP/MSTP 配置与根桥控制
 2. MSTP 多实例负载分担（含 active region-configuration）
 3. STP 保护四件套（BPDU/根/环路/TC）
 4. Eth-Trunk 手工与 LACP 模式
 5. iStack 堆叠（含 MAD 多主检测）
 6. DHCP 全局池 + 中继 + Snooping
 7. VRRP 主备 + 负载分担 + track
 8. BFD 与静态路由/VRRP 联动
 9. OSPF 单区域 → 多区域
10. OSPF 特殊区域（Stub/NSSA）与汇总
11. OSPF 认证、虚链路、快速收敛
12. IS-IS 基础与路由渗透
13. BGP EBGP/IBGP + next-hop-local
14. BGP 路由策略（IP-Prefix + Route-Policy + Community）
15. 路由反射器 / 联盟
```

### 19_6.3 HCIE 阶段（10 个高阶实验）
```latex
 1. MPLS + LDP 基础与 LSP 验证
 2. MPLS L3VPN 单域（RD/RT/两层标签）
 3. 跨域 VPN Option A / B
 4. EVPN 基础（BGP EVPN 地址族）
 5. VXLAN 静态隧道
 6. VXLAN + BGP EVPN 集中式网关
 7. VXLAN 分布式 Anycast 网关
 8. 组播（IGMP Snooping + PIM-SM + RP）
 9. 端到端 QoS（MQC + LLQ + 限速 + 队列）
10. Python 批量备份 + 合规检查脚本
```

### 19_6.4 综合模拟实验（考前必练）
```latex
A. 大型企业园区网（VLAN + MSTP + Eth-Trunk + VRRP + OSPF + NAT + ACL + QoS）
B. MPLS 骨干网 + 双客户 L3VPN（IS-IS + LDP + MP-BGP + 路由策略）
C. 限时排错（同伴埋 5 个故障，45 分钟内恢复并记录）
D. 论述题 3 道（六段式手写，每题 20 分钟）
```

> 练习原则：**每个实验都要写一份自己的实验报告**（拓扑 + 需求 + 配置 + 验证 + 踩坑）。报告数量比实验数量更重要——它是你考前唯一能快速回顾的东西。

---

## 19_7 默认参数速记表（考试填空/选择高频）
> **本节导读**：这张表是填空与选择题的高频来源，也是现网排错时判断「配置有没有被人改过」的基准线。建议单独打印，考前反复过。

| 项目 | 默认值 |
| --- | --- |
| STP 桥优先级 | **32768**（步长 4096） |
| STP 模式（华为） | **MSTP** |
| STP Forward Delay | 15 秒（Listening + Learning 共 30 秒） |
| MAC 老化时间 | **300 秒** |
| VLAN 可用范围 | **1–4094**（0 与 4095 保留） |
| 802.1Q Tag 长度 | 4 字节（帧长上限 1522） |
| 路由优先级 | 直连 0 / OSPF 10 / IS-IS 15 / 静态 60 / RIP 100 / OSPF ASE 150 / BGP 255 |
| OSPF 参考带宽 | 100 Mbps |
| OSPF Hello / Dead | 广播网 10s / 40s，P2P 10s / 40s |
| OSPF Router ID | 手工 > 最大 Loopback > 最大物理口 |
| BGP 端口 / Hold Time | TCP 179 / Keepalive 60s，Hold 180s |
| BGP Local_Preference | 100 |
| VRRP 优先级 | **100**（255 保留给 IP 拥有者） |
| VRRP 通告间隔 | 1 秒 |
| VRRP 虚拟 MAC | 00-00-5E-00-01-{VRID} |
| VRRP 组播地址 | 224.0.0.18（协议号 112） |
| LACP 超时 | slow 90s（可配 fast 1s） |
| Eth-Trunk 负载均衡 | src-dst-mac |
| DHCP 租期 | 1 天 |
| ACL 步长 | 5 |
| BFD 默认检测 | 1000ms × 3 |
| SSH 端口 / NETCONF 端口 | 22 / **830** |
| 组播 SSM 范围 | 232.0.0.0/8 |
| 组播私有范围 | 239.0.0.0/8 |
| VXLAN UDP 端口 | **4789** |
| VXLAN 封装开销 | 50 字节 |
| MPLS 标签 | 20 bit，PHP 隐式空标签 = **3** |
| Console 波特率 | **9600** |

---

## 19_8 认证与考试速查
### 19_8.1 考试科目一览
| 级别 | 科目 | 考试代码 | 形式 | 时长 | 通过分/总分 | 费用 |
| --- | --- | --- | --- | --- | --- | --- |
| HCIA-Datacom | HCIA-Datacom V1.0 | **H12-811** | 笔试 | 90 min | 600/1000 | 200 USD |
| HCIP-Datacom | Core Technology（**必修**） | **H12-821** | 笔试 | 90 min | 600/1000 | 300 USD |
| HCIP-Datacom | Advanced Routing & Switching（**选修**） | **H12-831** | 笔试 | 90 min | 600/1000 | 180 USD |
| HCIE-Datacom | 笔试 | **H12-891** | 笔试 | 90 min | 600/1000 | 300 USD |
| HCIE-Datacom | 实验（Lab） | **H12-892** | 操作 + 论述 | 480 min | 80/100 | 8000 CNY |

### 19_8.2 关键规则（必记，踩坑率极高）
```latex
第1步 笔试成绩有效期 18 个月：HCIE 笔试通过后须在 18 个月内通过实验，否则笔试作废
第2步 HCIP 需两门：H12-821（核心）+ 一门选修；无先后顺序，有效期内都通过即可取证
第3步 证书有效期 3 年，自证书发放日起算，无宽限期；过期不能续，只能重考全部科目
第4步 重认证：失效前通过同级别或更高级别任意一门考试，即可刷新 3 年
第5步 另可通过官方继续教育学分（课程进度 ≥90% + 结课考试）以学代考
第6步 HCIP 旧版细分方向（WAN/SD-WAN/方案设计/自动化开发）已进入退市流程，
   新版统一归并到 H12-831；若持有旧版考券，务必在官方通知的截止日期前考掉
第7步 已持有的旧版证书在有效期内仍然有效，无需重考
```

> ⚠️ 考试代码、费用考点政策会随版本调整，**报名前务必以华为人才在线（e.huawei.com/cn/talent）与 Pearson VUE 预约页面的最新公告为准**。

### 19_8.3 HCIE 笔试知识点权重
| 知识模块 | 笔试占比 | 实验占比 |
| --- | --- | --- |
| 高级路由交换技术 | 37% | 40% |
| 园区网络规划与部署 | 23% | 20% |
| 承载网规划与部署 | 15% | 25% |
| 网络自动化 | 17% | 10% |
| WAN 互联规划与部署 | 8% | 5% |

### 19_8.4 HCIP 两门科目权重
**H12-821（核心技术，必考）：** BGP 17% · OSPF 16% · 路由和流量控制 10% · 组播基础 9% · 网络安全基础 9% · 交换技术基础 7% · 其他约 32%

**H12-831（高级路由交换，选考）：** IPv6 路由 20% · MPLS 19% · IGP 高级特性 17% · BGP 高级特性 10% · 以太网高级技术/运维/排错/割接等约 34%

> 三条从权重表读出来的结论：  
第1步 **BGP 是 HCIP 第一权重**，比 OSPF 还高，别只顾着啃 OSPF；  
第2步 **H12-831 的核心是 IPv6 + MPLS + IGP 高级特性（合计 56%）**；  
第3步 新版 831 明显偏向**排错 + 割接 + 运维**，纯背命令已经不够用。

---

## 19_9 速查手册的正确用法
### 19_9.1 三种用法
| 场景 | 用法 |
| --- | --- |
| **考前 3 天** | 只过 19_7 默认参数表 + 19_8 权重表（填空与选择题的性价比最高） |
| **做实验时** | 卡住时按技术域查 19_1–19_4，**查完立刻关掉手册自己敲一遍** |
| **运维现场** | 用 19_1.4 健康巡检组 + 19_4 各业务查看命令，先采集再动手 |

### 19_9.2 把速查表变成自己的
```latex
第1步 打印 19_7 默认参数表，贴在显示器边（每天看 3 分钟，一周就记住了）
第2步 把 19_6 实验清单做成打勾表，做完一个划一个（进度可视化）
第3步 建一份"我踩过的坑"，每次实验失败都往里加一条（考前只看这份）
```

### 19_9.3 验证三板斧（速查版）
```latex
第1步 查参数：不确定的默认值，先查 19_7 再下判断
第2步 查命令：按技术域定位到 19_1–19_4，复制粘贴到设备前先读一遍
第3步 查进度：对照 19_6 清单，看自己卡在哪一个实验
```

---

## 19_10 考点与易错点
> **本节导读**：下面这些是考试和现网都高频踩的坑，每一条都对应一个「想当然」的错误认知。考前过一遍，比多刷两套题管用。

| # | 易错点 | 正确认知 |
| --- | --- | --- |
| 1 | 速查表用来背 | 它是**索引**，真正记住靠反复实验 |
| 2 | 默认参数不重要 | 填空/选择题**高频考点**，性价比最高 |
| 3 | 命令记住就行 | 要记住**在哪查**（技术域索引），而不是全部背下来 |
| 4 | 考试代码不会变 | 政策会随版本调整，**以官方最新公告为准** |
| 5 | 实验清单做一遍就够 | 至少做到**能脱离文档独立完成**才算过关 |
| 6 | 设备型号随便选 | 不同系列支持的特性不同（如堆叠、M-LAG），选型前先查规格 |

---

> **全库收官**：到这里，你已经走完 HCIA→HCIP→HCIE 的全链路。  
最后一句建议：**把每一份实验报告保存好，它会比任何证书都更真实地记录你的能力。**
