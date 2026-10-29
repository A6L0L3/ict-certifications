# 锐捷数通 RGSA→RGSP→RGSE 三级认证全链路实战知识库
## README · 导览
### README_1 RGSA→RGSP→RGSE（Routing & Switching 方向）
> **全库定位**：一套把「协议原理 → RGOS 命令 → 现场验证 → 故障定位 → 备考作战」串成一条链的可落地知识库。  
全部内容为纯 Markdown 源文件，可直接用任意 Markdown 编辑器打开；所有拓扑均为内嵌 ASCII 文本图，不依赖任何外部图床。  
全库统一验收标准：**能配通能调通能排掉。**

---

### README_2 这套知识库解决什么问题
市面上的认证资料通常只解决「命令怎么写」，而锐捷认证的字母 **S 是 Solutions（解决方案）不是 Switching**——考核重心早就从"设备会不会配"迁移到了"方案能不能落地"。

本库因此确立一条贯穿始终的主线，每个技术点都必须回答三问：

```plain
         怎么配        →        怎么验        →        坏了怎么查
    （命令与参数）        （show 命令与判读）      （分层定位与回退）
```

对应到三个级别，就是本库最核心的一句话：

| 级别 | 一句话定位 | 考核重心 |
| --- | --- | --- |
| **RGSA** | 把网络**接起来、通起来** | 会不会配 |
| **RGSP** | 把网络**设计稳、冗余好、能交付** | 配得对不对 |
| **RGSE** | 把网络**规划对联得动、故障定位准** | 为什么这么配、坏了怎么修 |

> **使用铁律**：不要按考纲顺序学，要按**数据转发路径**学。一台 PC 访问外网，数据包依次经过「接入 → 汇聚 → 核心 → 出口 → 运营商」，学习顺序就照这条链路走，每学完一段就能解决一段的真实问题。

---

### README_3 认证体系速览
锐捷认证已完成品牌升级：**RCNA → RGSA、RCNP → RGSP、RCIE → RGSE**。新旧证书在有效期内同等效力，考试大纲与难度保持不变，原有教材、题库、实验手册可继续使用。

| 级别 | 英文全称 | 定位 | 考试代码 | 费用 | 有效期 |
| --- | --- | --- | --- | --- | --- |
| **RGSA** | Ruijie Global Solutions Associate | ≤100 节点中小型网络 | C8211（VUE） | 160 美元 | 3 年 |
| **RGSP** | Ruijie Global Solutions Professional | 500 节点级大中型园区网 | C8311（VUE） | 320 美元 | 3 年 |
| **RGSE** | Ruijie Global Solutions Expert | 大型复杂网络 | C8511-Written + C8511-Lab | 300 美元 + 8000 元 | 3 年 |

+ 笔试全部由 **Pearson VUE** 代理，中文闭卷，通过线 **600/1000（60%）**。
+ RGSE 需笔试 + Lab 两级，**笔试成绩 24 个月内必须通过 Lab**，否则笔试作废。
+ 官方入口：锐捷 ICT 人才教育中心、Pearson VUE 锐捷专区（详见板块1）。

---

### README_4 按级别取用建议
#### 学习顺序的总原则
```plain
按数据转发路径学，而不是按考纲顺序学：
  接入（VLAN/STP/安全）→ 汇聚（SVI/路由）→ 核心（OSPF/聚合/VSU）→ 出口（NAT/ACL）
每学完一段就能解决一段的真实问题，正反馈最强。
```

+ **RGSA 精读**：板块0 → 1 → 2 → 3 → 4 → 5 → 8（静态 + OSPF 单区域）→ 9 → 12
+ **RGSP 精读**：板块0-13 全量，重点 板块5、6、7、10、11
+ **RGSE 精读**：以板块14 为主线，回溯板块8、13，重点练故障排查与方案设计

> 12 周入门路线的**逐周排布、每周闭环动作与自检标准**见 **板块0_2** 与 **板块0_3**，本索引不重复展开。

#### 每段学习的闭环动作（缺一不可）
```plain
1. 看原理    搞懂"为什么需要这个技术"，而不是先记命令
2. 敲一遍    在模拟器或真机上实际配置，不要用眼睛学网络
3. 故意改错  改一个参数看现象，这一步决定你是"背过"还是"懂了"
4. 用 show 验 每条技术至少掌握三条验证命令
5. 记排障清单 把踩过的坑写进自己的清单，考前只看这份
```

---

### README_5 五个最容易在考场/现场翻车的点
```plain
1. 忘了 ip routing              → 三层交换机 VLAN 间不通
2. ACL 末尾隐含 deny any        → 配完全网断网
3. 静态 NAT 缺 permit-inside    → 内网访问不了自己的服务器
4. VRRP track 降级值不够        → 上联断了但不切换
5. 先配 MSTP 实例后建 VLAN      → 报 warning，实例不生效
```

记住这五条，能避开网络工程师职业生涯中相当比例的午夜故障电话。

---

### README_6 使用须知
+ **命令版本**：全部配置基于锐捷 **RGOS** 系统（RG-S2xxx/S5xxx/S6xxx 交换系列、RG-RSR 路由系列、RG-AC/RAP 无线系列）。不同软件版本命令细节存在差异，文中用「版本提示」标注；若某条命令报错，优先检查提示符所处模式，再尝试等价写法。
+ **图片说明**：全库所有拓扑均已重绘为内嵌 ASCII 文本图，在中直接可见、可复制，不依赖外部图床，导入不会丢图。
+ **可粘贴性**：所有代码块均为可直接粘贴的 RGOS 配置片段，`!` 后为注释，敲入设备时不会生效。
+ **标记语言**：全库为纯 Markdown，不含任何 HTML 标签，可完整识别导入。

## 板块0 · 学习路径与备考总纲
> **本板块解决什么问题**：在翻开第一个技术点之前，先想清楚三件事——认证考什么、学到什么程度算过关、按什么顺序学。  
对应：RGSA→RGSP→RGSE 全部级别。有了这张全局地图，后面 14 个板块的每一节都知道自己站在链条的哪一环。

---

### 0_1 先建立全局地图：认证考什么、学到什么程度
#### 命名怎么理解
锐捷认证体系已完成品牌升级：**RCNA → RGSA、RCNP → RGSP、RCIE → RGSE**。

| 字母 | 含义 | 说明 |
| --- | --- | --- |
| R | Ruijie | 锐捷 |
| G | Global | 国际化认证与全球认可 |
| S | Solutions | **解决方案导向**——不是单纯的命令堆砌 |
| A / P / E | Associate / Professional / Expert | 工程师 / 高级工程师 / 专家 |

> **关键认知**：字母 "S" 是 Solutions 而非 Switching。这意味着考核重心从"设备会不会配"向"方案能不能落地"迁移。做实验时多问自己一句"这个配置解决什么业务问题"，比多背十条命令有用。

#### 三级定位一句话概括
| 级别 | 定位 | 一句话 |
| --- | --- | --- |
| **RGSA** | ≤100 节点中小型网络 | 把网络**接起来、通起来** |
| **RGSP** | 500 节点级大中型园区网 | 把网络**设计稳、冗余好、能交付** |
| **RGSE** | 大型复杂网络 | 把网络**规划对联得动、故障定位准** |

更直白地说：

> **RGSA 考"会不会配"，RGSP 考"配得对不对"，RGSE 考"为什么这么配、坏了怎么修"。**

这句话是全库主线。每学一个技术点，都用这三问检验自己：

```plain
            ┌─────────────┐
            │  一个技术点  │
            └──────┬──────┘
         ┌─────────┼─────────┐
         ▼         ▼         ▼
      怎么配     怎么验    坏了怎么查
    （命令参数）（show判读）（分层定位）
```

#### 新旧证书的关系
**新旧证书在有效期内同等效力，考试大纲与难度保持不变。** 手上的旧版教材、题库、实验手册完全可以继续用到考完，不必重新买资料——升级改的是名字和定位，不是考纲。

> **现场故事 · 被"新版认证"吓到的小李**  
小李手里有一套 RCNP 教材，刚看到品牌升级的消息，第一反应是"完了，得重新买全套资料"，甚至想推迟考试。前辈只问了他一句："你先去把新旧考纲对比一下，看变了哪一条。" 结果一条都没变。小李按原计划复习，用旧教材 + 真机实验一次通过。  
**复盘**：认证改名是品牌行为，考纲变更才是备考行为。遇到"体系升级"类消息，第一动作永远是**对比考纲**，而不是**掏钱买书**。

---

### 0_2 零基础 12 周入门路线（按数据转发路径学）
**不要按考纲顺序学，按数据转发路径学。** 一台 PC 访问百度，数据包依次经过：

```plain
网卡 → 接入交换机（VLAN / STP / 端口安全）
     → 汇聚（三层 SVI / 路由）
     → 核心（OSPF / 聚合 / VSU）
     → 出口（NAT / ACL）
     → 运营商
```

学习顺序就照这条链路走，每学完一段就能解决一段的真实问题，正反馈最强。下面为**相对周次**排布，可按自身基础整体压缩或拉长。

```plain
第 1-2 周   协议底座      OSI/TCP-IP、IPv4 编址与 VLSM、ARP、DHCP、Windows 命令、抓包
              ↓
第 3 周     设备上手      RGOS 模式切换、配置保存与备份、文件管理、SSH 加固
              ↓
第 4-5 周   二层交换      VLAN、Access/Trunk、跨交换机同 VLAN、VLAN 间路由
              ↓
第 6 周     破环          STP/RSTP/MSTP、PortFast、BPDU Guard、RLDP
              ↓
第 7 周     冗余          链路聚合（静态/LACP）、VSU 虚拟化
              ↓
第 8 周     网关冗余      VRRP、MSTP+VRRP 联动、track、BFD
              ↓
第 9-10 周  路由          静态/浮动、RIP、OSPF 单区域与多区域、三层交换机路由
              ↓
第 11 周    出口          ACL、NAT、PPP/广域网
              ↓
第 12 周    安全与验收    端口安全、DHCP Snooping、ARP 防护、综合实验
```

#### 每周的闭环动作（缺一不可）
1. **看原理**——搞懂"为什么需要这个技术"，而不是先记命令。
2. **敲一遍**——在模拟器或真机上实际配置，不要用眼睛学网络。
3. **故意改错**——改一个参数看现象，这一步决定你是"背过"还是"懂了"。
4. **用 show 验证**——每条技术至少掌握三条验证命令。
5. **记录排障清单**——把踩过的坑写进自己的清单，考前只看这份。

> **现场故事 · "眼睛学网络"的代价**  
两位同期入职的工程师，A 把全套实验视频看了两遍，笔记抄得工工整整；B 只看了原理，剩下时间全在真机上敲，还故意把 Trunk 的 allowed VLAN 改错、把 VRRP 组号写岔，看设备怎么报错。  
三个月后园区网割接，接入层有一台交换机 VLAN 不通。A 在现场翻了半小时笔记没头绪；B 上去两条命令——`show interfaces gi0/24 switchport` 和 `show vlan`——就定位到互联口 allowed 列表漏了一个 VLAN。  
**复盘**：命令可以查，但"看到什么回显意味着什么问题"只能靠亲手敲出来。第 3 步"故意改错"是区分背书和懂行的分水岭。

---

### 0_3 三级能力对照表与 10 分钟自检法
随便挑一个能力项，能在 **10 分钟内**写出完整可粘贴的配置并说出三条验证命令，才算过关。

| 能力项 | RGSA 要求 | RGSP 要求 | RGSE 要求 |
| --- | --- | --- | --- |
| VLAN | 会建 VLAN、划 Access、配 Trunk | Super VLAN / Private VLAN / Native VLAN / Trunk 修剪 | 跨数据中心大二层（VXLAN） |
| 破环 | 知道 STP 存在会开 | MSTP 多实例规划、实例与 VLAN 映射、边缘端口优化 | 与 VRRP/路由联动的收敛调优 |
| 冗余 | 无 | 聚合（静态/LACP）、VSU、VRRP、BFD、RLDP | 跨机框 MLAG、VSU 双主机检测 |
| 路由 | 静态、默认、RIP、OSPF 单区域 | OSPF 多区域/LSA/特殊区域/汇总/认证、BGP 基础、策略路由、重分布 | BGP 高级属性、ISIS、SR、MPLS VPN |
| 出口 | ACL、静态 NAT、PAT | 多出口、策略路由、端口映射、permit-inside | 与 IPSec/GRE 联动、QoS 保障 |
| 安全 | 端口安全基本 | DHCP Snooping、IP Source Guard、ARP Check、全局绑定、AAA、802.1X | 接入准入、园区整体安全架构 |
| 无线 | 胖 AP 配置 | 瘦 AP + AC、CAPWAP、WLAN 安全、网优 | 无线网优、漫游、高密度 |
| 排障 | 常用 `show` | 分层排障、抓包、镜像 | 复杂故障定位与方案级规避 |

#### 10 分钟自检法怎么操作
```plain
第1步 计时开始，白纸手写（不翻资料）该技术的完整配置
第2步 写完后，说出三条验证命令 + 每条命令"正常应该看到什么"
第3步 再说出一个典型故障现象 → 根因 → 解决方法
第4步 三件都做到且不超过 10 分钟 → 该项过关，打勾
   任一件卡壳 → 回到对应板块重做"故意改错"环节
```

---

### 0_4 实验环境搭建：三种方案与终端连接参数
三选一即可，不必都上。**优先级：方案 A 打底 → 方案 C 补高端特性。**

#### 方案 A：锐捷官方模拟器（推荐，贴合考试）
命令与真机一致，是备考主战场。**局限**：部分高端特性（VSU、MPLS）模拟不完整，需要真机补练。

#### 方案 B：EVE-NG 加载锐捷镜像
社区常见做法。**已知限制**：虚拟 PC 往往拿不到锐捷设备的 DHCP 地址。所以 DHCP 相关实验建议改用静态 IP 验证，或改用真机 / 官方模拟器。

> 把这条限制提前记住，能省下"为什么我的 PC 一直拿 169.254"的半小时。

#### 方案 C：真机最小化环境（最贴近交付）
| 设备 | 数量 | 用途 |
| --- | --- | --- |
| RG-S2xxx 接入交换机 | 2 台 | VLAN / STP / 端口安全 / RLDP |
| RG-S5xxx 三层交换机 | 2 台 | SVI / MSTP / VRRP / 聚合 / OSPF |
| RG-RSR 路由器 | 1-2 台 | NAT / PPP / 静态路由 |
| RG-AC + RAP | 1+2 台 | WLAN 瘦 AP 组网 |
| Console 线 + USB 转串口 | 2 条 | 初始化 |

#### 终端连接标准参数
```plain
波特率  ：9600
数据位  ：8
停止位  ：1
校验位  ：无
流控    ：无
```

连接工具：SecureCRT / Xshell / MobaXterm / PuTTY 均可。

> **强烈建议开启会话日志（Session Log）**：所有实验过程自动落盘。事后复盘、写实验报告、追溯"我上周到底敲了什么"直接复用，省下的时间远超配置它的 30 秒。

---

### 0_5 三段式学习法与场景记录笔记模板
#### 三段式学习法
| 阶段 | 动作 | 产出 |
| --- | --- | --- |
| **配置前** | 画拓扑、写 IP/VLAN 规划表、写预期结果 | 一张规划表 + 一句预期（例："PC1 ping 通 PC2，且 Trunk 上抓包能看到 802.1Q 标签 VLAN 20"） |
| **配置中** | 一条命令一回车，看回显 | 出现 `%` 开头的告警必须当场搞懂，不要跳过 |
| **配置后** | 跑验收清单、`write` 保存、导出配置存档 | 配置文本 + 验证输出 |

> **★ 为什么要先写"预期结果"**：没有预期就没有判断。写不出"配通之后应该看到什么"，也就看不出"哪里没通"。这一步是新手和专业工程师最大的差别。

#### 每个实验的强制产物
```plain
实验 / 现场记录模板
──────────────────────────────────────────────
场景名称：
拓扑：            （ASCII 拓扑，可复制）
IP / VLAN 规划：
完整配置：        （可粘贴文本，从设备 show run 导出）
验证命令与输出：   （show 命令 + 关键回显，贴原始输出不要手打）
踩坑记录：        （出错现象 → 根因 → 解决方法，三栏缺一不可）
一句话原理：      （用自己的话说清这个技术解决什么问题）
──────────────────────────────────────────────
```

> "一句话原理"那一栏最容易被跳过，但它是最有价值的——考场上遇到变形题，靠的就是这个，而不是背过的命令序列。

#### 场景笔记记录法：三类场景分别记什么
| 场景类型 | 记录重点 | 复用价值 |
| --- | --- | --- |
| **实验 / 练习** | 拓扑 + 完整配置 + 三条 show 输出 | 考前 10 分钟快速过 |
| **现场交付** | 规划表 + 变更步骤 + 验收结果 + 客户签字项 | 交付文档直接复用 |
| **故障处理** | 现象时间线 + 每条排查命令的输出 + 最终根因 | 同类故障下次 5 分钟定位 |

> **现场故事 · 一份笔记省下一次通宵**  
某园区网凌晨出现"部分网段时通时断"，值班工程师是新来的。老工程师翻出去年自己的一份故障笔记，里面记着一句："ARP 表里网关 MAC 会跳变 → ARP 欺骗 → 开 address-bind + arp-check"。新工程师照着 `show arp` 连查三次，果然看到 MAC 在变，启用绑定后网络立刻恢复，全程 20 分钟。  
**复盘**：笔记不是写给领导看的作业，是写给"半年后半夜三点慌张的自己"的救命纸条。故障类笔记请务必记录**原始命令输出**，不要只写结论。

---

### 0_6 高频踩坑预判清单（先记住，省一半时间）
| 现象 | 根因 | 解决 |
| --- | --- | --- |
| `instance 1 vlan 10` 报 `%Warning: you must create vlans before configuring mst instance` | 先配实例映射，后建 VLAN | 先 `vlan range 10,20` 建 VLAN，再进 MST 配置 |
| Trunk 通了但 VLAN 不通 | 两端 allowed VLAN 不一致 / Native VLAN 不一致 | 对齐 `switchport trunk allowed vlan` 与 native vlan |
| 聚合口起不来 | 成员口速率、双工、介质不一致；光口电口混绑 | 全部成员口 `speed/duplex` 对齐；同类型介质 |
| VRRP 双 Master | 三层 SVI 之间二层不通 / VRRP 组号不一致 | 检查 Trunk 是否放通该 VLAN、组号是否相同 |
| track 生效但主备没切换 | 降级后优先级仍 ≥ 备用优先级 | 降级值必须让结果**严格小于**备用优先级 |
| 端口被 shutdown 起不来 | 端口安全 / RLDP / BPDU Guard 触发 errdisable | `show interfaces status` 确认，再 `errdisable recovery` 或 `rldp reset` |
| 配置重启后丢失 | 只在 running-config，没保存 | `write` 或 `copy running-config startup-config` |
| 三层交换机 VLAN 间不通 | 忘记开 `ip routing` | 全局 `ip routing` |
| 静态 NAT 后内网访问不了服务器 | 缺 `permit-inside` 参数 | 静态映射命令末尾加 `permit-inside` |
| ACL 配完全网断网 | 末尾隐含 `deny any` | 末尾补 `permit ip any any` |
| 拿了 169.254.x.x 地址 | DHCP 请求没到服务器 | 查 VLAN / SVI IP / 中继 |
| 双工不匹配导致"能 ping 通但很慢" | 一端 auto 一端强制 | 两端都 auto 或都强制 |

---

### 0_7 报考顺序、重认证规则与职业路径
#### 考试与重认证要点
+ 笔试全部由 **Pearson VUE** 代理，中文综合笔试，通过线 **600/1000（60%）**，证书有效期 **3 年**。
+ RGSE 需 **笔试 + Lab 实验上机**两级：笔试通过成绩保留 **24 个月**，必须在此窗口内通过 Lab，否则笔试作废。
+ 重认证：证书到期前考取当前版本同级或更高级认证即可刷新有效期，有效期自**重认证考试日**起重新计算 3 年。

#### 报考顺序建议
```plain
RGSA → 上机实操 3-6 个月 → RGSP → 项目历练 1-2 年 → RGSE 笔试 → RGSE Lab
```

> **不要跳级裸考 RGSP。** MSTP+VRRP 联动和 OSPF 多区域是纸面学不会的——你得亲眼见过双 Master、见过 track 没触发、见过次优路径，才算真的会。

#### 典型职业路径
```plain
网络运维工程师（RGSA 水平）
      ↓  独立处理接入层故障、独立完成小型网络搭建
网络工程师 / 交付工程师（RGSP 水平）
      ↓  独立交付 500 节点园区网、编写方案与验收文档
高级网络工程师 / 网络架构师（RGSE 水平）
      ↓  大型网络规划、跨厂商对接、复杂故障定界
技术专家 / 售前顾问 / 技术经理
```

---

### 0_8 速记卡 · 板块0
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | S 是 **Solutions** 不是 Switching，考的是方案落地能力 | 解决方案导向 |
| ★2 | RGSA 会不会配 / RGSP 配得对不对 / RGSE 为什么这么配 | 三级主线 |
| ★3 | 按**数据转发路径**学，不按考纲顺序学 | 接入→汇聚→核心→出口 |
| ★4 | 每个技术点三问：怎么配 → 怎么验 → 坏了怎么查 | 三问闭环 |
| ★5 | 学习闭环五步：看原理 → 敲一遍 → 故意改错 → show 验证 → 记清单 | 缺一不可 |
| ★6 | 10 分钟自检法：写配置 + 三条 show + 一个故障案例 | 过关标准 |
| ★7 | 会话日志必须开，实验记录必须写"一句话原理" | 可复用资产 |
| ★8 | 品牌升级不改考纲，旧教材继续用 | 别重复买资料 |
| ★9 | RGSE 笔试 24 个月内必须过 Lab | 先练 Lab 再考笔试 |
| ★10 | 五个翻车点：ip routing / deny any / permit-inside / track 值 / MSTP 建 VLAN 顺序 | 午夜电话终结者 |

## 板块1 · 认证体系全景与考试作战地图
> **本板块解决什么问题**：考什么、怎么报名、怎么分配考场时间。技术内容从板块2 开始，这一板块先把"作战地图"铺好——很多人技术很扎实却挂在时间分配和题干陷阱上，属于完全可以避免的损失。  
对应：RGSA→RGSP→RGSE 全部级别。

---

### 1_1 品牌升级：从 RCNA/RCNP/RCIE 到 RGSA/RGSP/RGSE
锐捷认证体系已完成全线升级，新旧名称对照如下：

| 旧称 | 新称 | 英文全称 | 中文名 |
| --- | --- | --- | --- |
| RCNA | **RGSA** | Ruijie Global Solutions Associate | 锐捷全球认证解决方案工程师 |
| RCNP | **RGSP** | Ruijie Global Solutions Professional | 锐捷全球认证解决方案高级工程师 |
| RCIE | **RGSE** | Ruijie Global Solutions Expert | 锐捷全球认证解决方案专家 |

#### 升级的三个实质变化
1. **接轨国际**——认证定位从"设备工程师"转向"解决方案工程师"，考核重心向规划、设计、实施部署能力迁移。
2. **技术扩容**——新增 SDN、Cloud、AIGC、5G 等前沿技术内容，强化技术落地。
3. **种类丰富**——在通用技术认证基础上，整合新增产品及行业解决方案专项认证。

#### 对备考者最重要的结论
> **★ 新旧证书在有效期内同等效力，考试大纲和难度保持不变。**

所以：手上的旧版教材、题库、实验手册**完全可以继续用到考完为止**。升级改的是名字和定位，不是考纲。别被"新版认证"的营销话术吓得重新买全套资料。

---

### 1_2 三级定位与能力标准
#### RGSA - Routing and Switching
+ **定位**：中小型网络（100 个节点以下）的规划、设计、实施和维护。
+ **能力标准**：能在中小型园区网络中熟练使用锐捷路由器、交换机、WLAN 设备，部署与管理 VLAN、冗余链路、动态路由、NAT、WLAN 及广域网技术，实现网络连接和基本网络安全防护。
+ **适用对象**：即将或正在从事网络工程/运维的技术人员；锐捷设备代理商工程师、服务渠道工程师；零基础入门者。

#### RGSP - Routing and Switching
+ **定位**：大、中型园区网络（500 节点级）的实施、维护与管理。
+ **能力标准**：对大中型园区网中的数通产品有较深入理解，掌握园区网常用数据通信技术原理，能熟练部署产品并正确应用技术。

> **RGSP 的隐含要求**：具备交付大部分锐捷原厂项目的能力。这是它与 RGSA 的分水岭——RGSA 是"我能配通"，RGSP 是"我能交付给客户并签验收单"。

#### RGSE - Routing and Switching
+ **定位**：大型复杂网络的规划、设计和管理。
+ **能力标准**：具备复杂复合技术的理解与应用能力，理解大型复杂网络的网络架构与应用特点，理解多种技术的联动融合应用及其实现原理（**含与常见的非锐捷设备联动**）。

> **RGSE 的分水岭**：**跨厂商、跨技术联动** + **方案设计与故障排查**。考纲明确写了"含跟常见的非锐捷设备联动"——这意味着不能只会锐捷自家命令，还得懂协议标准本身。

> **现场故事 · 只会一家命令的尴尬**  
某项目要把锐捷核心与另一厂商的汇聚对接 OSPF。工程师照着锐捷手册把 `network` 命令敲完，邻居死活起不来，卡在 ExStart。  
排查时发现：对面设备接口 MTU 是 9000，本端是 1500。OSPF 在 ExStart 阶段交换 DBD 报文时会携带 MTU，两端不一致就卡住——这是**协议标准层面的行为**，不是任何一家厂商的私有命令能绕过的。  
加上 `ip ospf mtu-ignore`（或对齐两端 MTU）后立刻 Full。  
**复盘**：RGSE 考纲写"含非锐捷设备联动"不是客套话。越往上考，越要回到 RFC 和标准协议行为本身。

---

### 1_3 考试科目、代码、费用与考试形式
#### 数通（R&S）方向
| 认证科目 | 考试平台 | 考试代码 | 目录价 | 有效期 |
| --- | --- | --- | --- | --- |
| RGSA-Routing and Switching | Pearson VUE | C8211 | 160 美元 | 3 年 |
| RGSP-Routing and Switching | Pearson VUE | C8311 | 320 美元 | 3 年 |
| RGSE-R&S Written（笔试） | Pearson VUE | C8511-Written | 300 美元 | 笔试成绩 24 个月 |
| RGSE-R&S Lab（实验） | 锐捷福州考场 / 各地移动考场 | C8511-Lab | 8000 元 | 3 年 |

#### 其他方向（供扩展参考）
| 方向 | RGSA 代码 | RGSP 代码 |
| --- | --- | --- |
| Security（安全） | R3111 | R3211 |
| Cloud Computing（云计算） | R4111 | R4211 |
| WLAN（无线） | R5111 | R5211 |
| DCN（数据中心） | — | — |
| RGSE-DCN | R2311-Written | R2311-Lab |

#### 考试形式与题型
| 级别 | 形式 | 题型 | 题量 | 时长 | 及格/满分 |
| --- | --- | --- | --- | --- | --- |
| RGSA | 中文综合笔试（闭卷） | 单选 + 多选 | 约 50 题（35 单 + 15 多） | 80 分钟 | 600 / 1000 |
| RGSP | 中文综合笔试（闭卷） | 单选 + 多选 | 约 60 题（40 单 + 20 多） | 90 分钟 | 600 / 1000 |
| RGSE 笔试 | 中文综合笔试 | 判断 + 单选 + 多选 | 60 题（10 判 + 30 单 + 20 多） | 90 分钟 | 600 / 1000 |
| RGSE Lab | 中文实验上机 | 实际操作 | — | — | 60% |

> **★ RGSE 硬性规则**：通过笔试后 **2 年内（24 个月）必须通过 Lab**，否则笔试成绩作废，需重考笔试。  
**排考建议**：先具备 Lab 水平再去考笔试，避免笔试成绩过期。不要抱着"先过了笔试再说"的心态。

---

### 1_4 考纲权重与备考优先级
#### RGSA-R&S 权重分布
| 模块 | 权重 | 板块对应 |
| --- | --- | --- |
| **WLAN** | **14%** | 板块12 |
| 静态路由 | 12% | 板块8 |
| VLAN | 10% | 板块4 |
| OSPF | 10% | 板块8 |
| 网络分层模型 | 8% | 板块2 |
| NAT | 8% | 板块9 |
| 其他 | 38% | IP 地址、Windows 命令、RGOS 管理、二层原理、生成树、路由原理、ACL、无线基础、胖瘦 AP、广域网 |

> **★ 重要提醒**：**WLAN 权重最高却最容易丢分**——因为很多人只练路由交换，把无线当"了解一下"。板块12 必须完整过一遍，这是性价比最高的一块。
> 静态路由 + VLAN + OSPF 三者合计 32%，是绝对主力，要做到闭眼能配。

#### RGSP-R&S 考纲范围
网络组网、VLAN 高级技术、网络冗余 MSTP、VRRP、BFD、网络聚合链路、VSU 网络虚拟化技术、无线局域网 WLAN 技术、环路检测 RLDP、OSPF、BGP 基础、策略路由、ACL 应用网络安全、IPv6、无线网络原理、典型组网和无线网优等部署园区网络需要掌握的技术。

#### RGSE-R&S 考纲范围
BGP 路由属性和高级特性、ISIS 原理、ISIS 应用MPLS 原理和应用SR 原理和应用IPSec 技术原理和应用组播技术原理和应用QoS 技术原理和应用IPv6 技术原理和应用EVPN VXLAN 技术原理和应用局域网规划设计和锐捷典型方案、路由规划设计和锐捷典型方案、常见故障排查与解决方案。

#### 备考优先级排序（投入产出比从高到低）
```plain
第一梯队   WLAN（权重最高且易丢分）+ 静态路由 + VLAN + OSPF
                    ↓
第二梯队   NAT + ACL + 生成树（MSTP）+ 生成树优化特性
                    ↓
第三梯队   VRRP + 聚合 + VSU + 安全特性 + IPv6 基础
                    ↓
第四梯队   BGP 高级 / ISIS / MPLS / SR / QoS / EVPN VXLAN（RGSE 主线）
```

---

### 1_5 培训与报考全流程
#### 标准流程
```plain
1. 确定方向   → R&S / Security / WLAN / Cloud Computing / DCN
        ↓
2. 参加培训   → 锐捷培训合作伙伴（RTP）授权机构，线上或线下
                RGSA：5 天（约 30-40 课时）
                RGSP：10 天
                RGSE：脱产班 + 实验冲刺
        ↓
3. 购买考试券 → 通过锐捷培训合作伙伴（RTP）或锐捷商城购买
        ↓
4. 预约考试   → Pearson VUE 考试中心预约（笔试）
                RGSE Lab 需预约锐捷福州考场或各地移动考场
        ↓
5. 参加考试   → 携带有效身份证件，提前 30 分钟到场
        ↓
6. 领取证书   → 个人中心下载电子证书；RGSE 提供水晶证书套装
        ↓
7. 证书核验   → 官方渠道输入证书编号验证有效性
```

#### 官方资源入口
| 资源 | 地址 |
| --- | --- |
| 锐捷 ICT 人才教育中心 | talent.ruijie.com.cn |
| 认证全景图 | talent.ruijie.com.cn/identification |
| Pearson VUE 锐捷专区 | pearsonvue.com（搜索 Ruijie） |
| 认证服务邮箱 | talent@ruijie.com.cn |
| 锐捷服务热线 | 4008-111-000 |

#### 报考条件
**无前置门槛，直接报名。** 在校学生、大专/本科及以上毕业生、正在从事或即将从事网络通信相关工作的人员均可报名。

> 虽然官方不设前置条件，但 RGSP 的技术前提实际是 RGSA 水平，RGSE 的前提是 RGSP 水平。跳级报考通过率极低——不是因为题目超纲，而是因为缺少实验积累导致的"理解断层"。

---

### 1_6 考场时间分配与五个高频失分点
#### RGSA（80 分钟 / 50 题）
| 阶段 | 时间 | 动作 |
| --- | --- | --- |
| 第一轮 | 0-40 min | 从头到尾做会做的题，单选题平均 40 秒/题 |
| 标记 | 40-45 min | 不确定的题目做标记跳过，不纠缠 |
| 第二轮 | 45-70 min | 回头啃标记题，多选题重点复查 |
| 检查 | 70-80 min | 检查漏选、看错"不正确/错误"类题干 |

#### RGSP / RGSE 笔试（90 分钟 / 60 题）
| 阶段 | 时间 | 动作 |
| --- | --- | --- |
| 第一轮 | 0-45 min | 快速通做，单选 40 秒、多选 60 秒 |
| 第二轮 | 45-75 min | 处理标记题；计算题（VLSM、OSPF cost、BGP 属性）单独算 |
| 检查 | 75-90 min | 多选题宁缺毋滥 |

#### 五个高频失分点
1. **题干否定词**——"下列说法**错误**的是""**不能**实现的是"。每年都有人栽在这，而且栽了还觉得自己答对了。
2. **多选题保守原则**——不确定就少选。多数评分规则下漏选得部分分、错选零分。
3. **单位陷阱**——MTU、cost、优先级、计时器的单位要看清。
4. **命令模式题**——问的是"全局模式"还是"接口模式"，选项前缀 `(config)#` / `(config-if)#` / `(config-mst)#` 要看准。
5. **反常识特性**——例如 `portfast` 开启后端口**仍会发送 BPDU**（它只是跳过状态机，不停止发 BPDU）；BPDU Guard 触发后端口进入 **err-disable** 而非简单 down。

> **现场故事 · 栽在"错误"两个字上**  
一位工程师考完 RGSP 自我感觉极好，结果差 40 分。复盘模拟题时发现：他有三道题题干写着"下列说法错误的是"，他全部按"正确的"去选，而且选的时候毫无察觉——因为选项里"正确说法"更眼熟，手就点过去了。  
**复盘**：考试不是比谁懂得多，是比谁少犯低级错。**读题时把"错误/不能/不包括"圈出来**，这一个动作的价值等于多背 20 个命令。

#### 考场作战三原则
```plain
第1步 先易后难，绝不纠缠      —— 卡住的题立刻标记跳过，时间是最稀缺资源
第2步 多选题宁缺毋滥          —— 不确定的选项不选，漏选有分、错选零分
第3步 最后 10 分钟专查否定词  —— "错误/不能/不包括/不属于"逐个回看
```

---

### 1_7 重认证规则与职业发展路径
#### 证书有效期与重认证
| 项目 | 规则 |
| --- | --- |
| 有效期 | 3 年（RGSA→RGSP→RGSE 证书本体） |
| 重认证方式 | 考取当前版本的同级或更高级认证 |
| 生效时间 | 证书有效期自**重认证考试日**起重新计算 3 年 |
| 笔试成绩 | RGSE 笔试通过后 24 个月内必须通过 Lab |

> 建议把重认证和"技术版本迭代"绑定起来做，而不是临期突击。认证内容会不定期进行更新和优化，重认证本身也是一次知识刷新。

#### 典型职业路径
```plain
网络运维工程师（RGSA）
      ↓  独立处理接入层故障、独立完成小型网络搭建
网络工程师 / 交付工程师（RGSP）
      ↓  独立交付 500 节点园区网、编写方案与验收文档
高级网络工程师 / 网络架构师（RGSE）
      ↓  大型网络规划、跨厂商对接、复杂故障定界
技术专家 / 售前顾问 / 技术经理
```

#### 备考节奏建议（相对时间，按自身情况调整）
```plain
D-90 ~ D-60   通读板块 0-3，搭好协议与设备底座，实验环境跑通
D-60 ~ D-30   主攻板块 4/5/8/9/12（权重最高的几块），每个技术点做实验
D-30 ~ D-10   板块 6/7/10/11 综合实验，做完整园区网项目
D-10 ~ D-1    只做两件事：过速记卡 + 重做自己记的踩坑清单
D-Day         按 1_6 的时间分配执行，最后 10 分钟查否定词
```

---

### 1_8 速记卡 · 板块1
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | 新旧证书同等效力，**考纲未变**，旧资料继续用 | 别重复买书 |
| ★2 | RGSA C8211 / RGSP C8311 / RGSE C8511-Written + Lab | 考试代码 |
| ★3 | 通过线统一 600/1000（60%），RGSE Lab 也是 60% | 及格线 |
| ★4 | RGSE 笔试成绩 **24 个月**内必须过 Lab | 先练 Lab 再考笔试 |
| ★5 | **WLAN 占 RGSA 权重 14% 最高**，且最容易丢分 | 性价比之王 |
| ★6 | 静态路由 + VLAN + OSPF 合计 32%，闭眼能配 | 主力模块 |
| ★7 | 多选题**宁缺毋滥**：漏选部分分、错选零分 | 保守原则 |
| ★8 | 题干"错误/不能/不包括"必须圈出来 | 否定词陷阱 |
| ★9 | 命令模式看前缀：`(config)#` / `(config-if)#` / `(config-mst)#` | 模式题 |
| ★10 | portfast 仍发 BPDU；bpduguard 触发进 err-disable | 反常识特性 |

## 板块2 · 网络协议底座：编址、ARP、DHCP 与报文分析
> **本板块解决什么问题**：建立"内功"。后面所有排障都建立在能读懂报文、能算清网段、能判断"这一层到底出了什么事"的基础上。  
对应 RGSA 考纲：网络分层模型（8%）、IP 地址、Windows 常用网络命令。这是全库的起点，也是排障时最先被调用的一层。

---

### 2_1 OSI 与 TCP/IP：用"故障现象"记住七层
考试常考的是"某一层出故障会表现成什么样"，而不是让你默写七层顺序。用下面这张表建立**"层—故障现象"**的映射：

| OSI 层 | 数据单元 | 关键协议 | 锐捷设备对应 | 典型故障现象 |
| --- | --- | --- | --- | --- |
| 应用层 | Data | HTTP/DNS/DHCP/FTP | — | 能 ping 通但打不开网页 |
| 传输层 | Segment | TCP/UDP | ACL 匹配端口 | 能 ping 通但业务端口不通 |
| 网络层 | Packet | IP/ICMP/OSPF | 三层交换机、路由器 | ping 不通无路由 |
| 数据链路层 | Frame | Ethernet/VLAN/STP/ARP | 二层交换机 | MAC 学不到VLAN 错、环路 |
| 物理层 | Bit | 双绞线/光纤 | 光模块、线缆 | 端口 down、光衰过大、CRC 错 |

#### 封装与解封装
```plain
发送方（从上往下加头）
应用数据
  ↓ 加 TCP/UDP 头
[TCP头|数据]                        Segment
  ↓ 加 IP 头
[IP头|TCP头|数据]                   Packet
  ↓ 加以太网头（源/目的 MAC）+ FCS
[以太头|IP头|TCP头|数据|FCS]        Frame
  ↓ 变成比特流上线

接收方（从下往上拆头）执行相反过程
```

#### ★ 一个必须刻进脑子里的结论
**跨网段通信时，IP 头里的源/目的 IP 全程不变；以太网头里的源/目的 MAC 每经过一个三层设备就重写一次。**

这一句话解释了：为什么需要 ARP、为什么网关必须配对为什么 traceroute 能逐跳显示、为什么二层交换机看不懂 IP。整个 ARP 和网关配置的原理基础就在这里。

```plain
PC ────── 交换机 ────── 路由器 ────── 路由器 ────── 服务器
  IP:  A ──────────────────────────────────────── B   （全程不变）
  MAC: M1 → M2    M2 → M3     M3 → M4    M4 → M5      （每跳重写）
```

**考点提示**：交换机转发看**目的 MAC**，不看 IP；路由器转发看**目的 IP**，不看 MAC。

> **现场故事 · "网关配错一位"的两小时**  
新办公楼开通，用户反映"上不了网"，但办公室内互 ping 全通。  
工程师先查交换机端口——up/up；查 VLAN——正确；查路由器——路由表有回程路由。  
最后用 `show arp` 一看，网关地址对应的 MAC 条目**根本不存在**。原因：终端 DHCP 下发的网关是 192.168.10.1，而 SVI 实际配的是 192.168.10.254。改回一致，全网通。  
**复盘**："内网能通外网不通"的第一嫌疑永远是**网关**。而判断网关有没有生效，最快的就是看 ARP 表里有没有网关 MAC——这条链路完全印证了 2_1 的那句核心结论。

---

### 2_2 IPv4 编址与 VLSM 三步法
#### 地址分类速查
| 类别 | 首字节范围 | 默认掩码 | 私有地址段 |
| --- | --- | --- | --- |
| A | 1-126 | /8 | 10.0.0.0 – 10.255.255.255 |
| B | 128-191 | /16 | 172.16.0.0 – 172.31.255.255 |
| C | 192-223 | /24 | 192.168.0.0 – 192.168.255.255 |
| D | 224-239 | 组播 | — |
| E | 240-255 | 保留 | — |

**特殊地址**：

+ `127.0.0.0/8` 本地环回
+ `169.254.0.0/16` DHCP 失败自动分配——**看到这个地址，第一反应就是 DHCP 没通**

#### VLSM 三步法
**例题**：192.168.10.0/24 分给 4 个部门，分别需 60、25、10、2 台主机。

**第一步：算主机位。** 需要主机数 n，满足 `2^h - 2 ≥ n`（减 2 是去掉网络号和广播号）。

| 部门 | 需求 | 主机位 h | 掩码 | 块大小 |
| --- | --- | --- | --- | --- |
| 研发 | 60 | 6（2^6-2=62） | /26 | 64 |
| 市场 | 25 | 5（2^5-2=30） | /27 | 32 |
| 财务 | 10 | 4（2^4-2=14） | /28 | 16 |
| 网管 | 2 | 2（2^2-2=2） | /30 | 4 |

**第二步：从大到小依次切块。** 必须降序，否则产生地址碎片。

```plain
192.168.10.0/24
├─ 研发  192.168.10.0/26    可用 .1 ~ .62      广播 .63
├─ 市场  192.168.10.64/27   可用 .65 ~ .94     广播 .95
├─ 财务  192.168.10.96/28   可用 .97 ~ .110    广播 .111
├─ 网管  192.168.10.112/30  可用 .113 ~ .114   广播 .115
└─ 剩余  192.168.10.116/30 起，留给点到点链路与后续扩展
```

**第三步：验算不重叠。** 块边界必须整除块大小（如 .64/27，64÷32=2 ✓）。

> **★ 锐捷考试注意**：锐捷 DHCP 地址池配置中，子网掩码**不支持简写为 **`/24`**，必须写全 **`255.255.255.0`。这是 RGOS 的特色限制，考选择题时常设陷阱。

#### 掩码速查表
| 掩码 | 主机位数 | 可用主机数 | 反掩码（OSPF/ACL 用） |
| --- | --- | --- | --- |
| /24 255.255.255.0 | 8 | 254 | 0.0.0.255 |
| /25 255.255.255.128 | 7 | 126 | 0.0.0.127 |
| /26 255.255.255.192 | 6 | 62 | 0.0.0.63 |
| /27 255.255.255.224 | 5 | 30 | 0.0.0.31 |
| /28 255.255.255.240 | 4 | 14 | 0.0.0.15 |
| /30 255.255.255.252 | 2 | 2 | 0.0.0.3 |
| /32 255.255.255.255 | 0 | 1（主机路由） | 0.0.0.0 |

---

### 2_3 ARP 原理与排障三板斧
#### 工作流程
```plain
主机 A(192.168.1.10) 想访问网关 192.168.1.1
  1. 查本机 ARP 缓存 → 没有
  2. 发 ARP Request（广播）："谁是 192.168.1.1？请告诉 192.168.1.10"
     二层：目的 MAC = FFFF.FFFF.FFFF
  3. 网关回复 ARP Reply（单播）："我是 192.168.1.1，MAC 是 xxxx.xxxx.xxxx"
  4. A 写入 ARP 缓存，封装单播帧发送
```

#### 免费 ARP（Gratuitous ARP）
设备主动宣告自己的 IP-MAC 映射，目的 MAC 也是广播地址。两个作用：

1. **IP 地址冲突检测**——新配地址时发一个，若有人回应说明冲突。
2. **刷新下游设备的 ARP 表**——VRRP 主备切换后，新 Master 发免费 ARP，让终端更新网关 MAC。**这是 VRRP 切换能快速生效的关键机制之一**（详见板块7）。

#### 锐捷设备上的 ARP 操作
```bash
Ruijie# show arp                              ! 查看 ARP 表
Ruijie# show arp 192.168.1.1                  ! 查看指定条目
Ruijie# clear arp-cache                       ! 清空 ARP 缓存（排障常用）
Ruijie# show arp detail                       ! 详细信息

Ruijie(config)# interface vlan 10
Ruijie(config-if-VLAN 10)# arp timeout 3600   ! 修改 ARP 老化时间（秒）
```

#### ARP 排障三板斧
| 现象 | 排查命令 | 结论 |
| --- | --- | --- |
| ARP 表里没有网关 MAC | `show arp` + 抓包看 Request 有无回应 | 二层不通 / VLAN 错 / 网关 SVI 没起来 |
| ARP 表有条目但 MAC 错 | `show arp` 对比网关真实 MAC | ARP 欺骗 / 网络中存在冒充网关 |
| 时通时断 | 多次 `show arp` 观察 MAC 是否跳变 | 典型 ARP 欺骗，需启用 ARP 防护（见板块10） |

> **★ 排障心法**：`show arp` 在 IPv4 中的地位，等同于 `show mac-address-table` 在二层、`show ip route` 在三层的地位。**任何时候怀疑"二层到三层这一段"，第一反应就是查 ARP 表。**

---

### 2_4 DHCP 原理、地址池配置与中继
#### 四步交互（DORA）
```plain
Client → Server : DHCP Discover  （广播，源 0.0.0.0）
Server → Client : DHCP Offer     （携带拟分配 IP）
Client → Server : DHCP Request   （广播，宣告接受）
Server → Client : DHCP Ack       （确认，携带租期/网关/DNS）
```

**关键点**：四步都是广播（Offer 和 Ack 在部分实现中为单播，取决于广播标志位）。因此 **DHCP 不能跨网段**——跨 VLAN 必须配 **DHCP 中继（Relay）**。

```plain
   PC（VLAN 10）                      DHCP 服务器（VLAN 100）
        │                                    ▲
        │ Discover（广播，到此为止）           │
        ▼                                    │
   ┌─────────┐    单播转发（中继）      ┌──────────┐
   │ SVI 10  │ ──────────────────────▶ │  服务器   │
   │helper   │ ◀────────────────────── │          │
   └─────────┘                         └──────────┘
   ip helper-address 10.0.0.100
```

#### 锐捷三层交换机做 DHCP 服务器（完整可粘贴）
```bash
Ruijie> enable
Ruijie# configure terminal
Ruijie(config)# hostname CORE1

! 1. 创建 VLAN 与 SVI
CORE1(config)# vlan range 10,20
CORE1(config-vlan-range)# exit
CORE1(config)# interface vlan 10
CORE1(config-if-VLAN 10)# ip address 192.168.10.1 255.255.255.0
CORE1(config-if-VLAN 10)# exit
CORE1(config)# interface vlan 20
CORE1(config-if-VLAN 20)# ip address 192.168.20.1 255.255.255.0
CORE1(config-if-VLAN 20)# exit

! 2. 排除不参与自动分配的地址（网关、服务器、预留段）
CORE1(config)# ip dhcp excluded-address 192.168.10.1 192.168.10.10
CORE1(config)# ip dhcp excluded-address 192.168.10.128 192.168.10.254
CORE1(config)# ip dhcp excluded-address 192.168.20.1 192.168.20.127

! 3. 创建地址池（注意：掩码必须写全，不支持 /24 简写）
CORE1(config)# ip dhcp pool 10
CORE1(dhcp-config)# network 192.168.10.0 255.255.255.0
CORE1(dhcp-config)# default-router 192.168.10.1
CORE1(dhcp-config)# dns-server 8.8.8.8 114.114.114.114
CORE1(dhcp-config)# lease 7                  ! 租期 7 天
CORE1(dhcp-config)# exit

CORE1(config)# ip dhcp pool 20
CORE1(dhcp-config)# network 192.168.20.0 255.255.255.0
CORE1(dhcp-config)# default-router 192.168.20.1
CORE1(dhcp-config)# dns-server 8.8.8.8 114.114.114.114
CORE1(dhcp-config)# lease 7
CORE1(dhcp-config)# exit

! 4. 保存
CORE1(config)# end
CORE1# write
```

#### DHCP 中继（跨 VLAN 场景）
```bash
! 在 SVI 接口下指向 DHCP 服务器
CORE1(config)# interface vlan 10
CORE1(config-if-VLAN 10)# ip helper-address 10.0.0.100
```

#### DHCP 验证与排障清单
```bash
CORE1# show ip dhcp binding            ! 查看已分配的地址绑定
CORE1# show ip dhcp pool               ! 查看地址池使用率
CORE1# show ip dhcp conflict           ! 查看地址冲突
CORE1# debug ip dhcp server events     ! 实时调试（生产慎用）
```

| 故障 | 排查方向 |
| --- | --- |
| PC 拿到 169.254.x.x | DHCP 请求根本没到服务器：VLAN 错 / SVI 没配 IP / 中继没配 |
| 拿到 IP 但网关不对 | 地址池 `default-router` 配错 |
| 地址池耗尽 | `show ip dhcp pool` 看使用率，缩小 lease 或扩网段 |
| 拿到私接路由器的地址 | 网络中存在非法 DHCP 服务器，需启用 DHCP Snooping（板块10） |

> **注意**：部分模拟器环境（如 EVE-NG 加载锐捷镜像）下虚拟 PC 常常无法从锐捷设备正常获取 DHCP 地址。DHCP 相关实验建议改用静态 IP 验证，或改用真机 / 官方模拟器，避免误判为配置错误。

---

### 2_5 Windows 常用网络命令与排障组合拳
#### 命令速查
| 命令 | 作用 | 典型用法 |
| --- | --- | --- |
| `ipconfig /all` | 查看 IP、掩码、网关、DNS、MAC | 第一件事，确认拿到什么地址 |
| `ipconfig /release` | 释放 DHCP 地址 | 配合 renew 重拿地址 |
| `ipconfig /renew` | 重新获取 DHCP 地址 | 改完地址池后必做 |
| `ipconfig /flushdns` | 清空 DNS 缓存 | 能 ping 通 IP 但打不开网页时试 |
| `arp -a` | 查看本机 ARP 表 | 看网关 MAC 是否存在/是否正确 |
| `arp -d *` | 清空 ARP 表 | 改网关或怀疑 ARP 欺骗时用 |
| `ping -t` | 持续 ping | 观察丢包和抖动 |
| `ping -n 100 -l 1472` | 指定次数与包大小 | 测 MTU 问题 |
| `tracert` | 逐跳追踪 | 定位断在哪一跳 |
| `pathping` | ping + tracert 结合，统计每跳丢包 | 定位间歇性丢包 |
| `nslookup` | DNS 解析测试 | 区分 DNS 问题还是网络问题 |
| `netstat -ano` | 查看连接、端口、PID | 查本机端口占用 |
| `route print` | 查看本机路由表 | 多网卡/策略路由场景 |

#### 排障组合拳（按顺序打，不要跳步）
```plain
第1步 ipconfig /all         → 有没有拿到正确 IP / 网关 / DNS？
       ↓ 没有 → 查 DHCP 与 VLAN
第2步 ping 127.0.0.1        → 本机协议栈正常吗？
       ↓
第3步 ping 网关             → 二层到三层通不通？（不通查 VLAN/ARP/端口）
       ↓
第4步 ping 外网 IP（如 8.8.8.8）→ 出口 NAT 通不通？（不通查 NAT/路由）
       ↓
第5步 nslookup 域名         → DNS 通不通？（不通查 DNS 配置）
       ↓
第6步 ping 域名             → 端到端业务通不通？
```

> **★ 这套顺序的价值**：每一步都在缩小范围。**第3步不通和第4步不通，指向的是完全不同的故障域**，跳过顺序直接乱试，是新手排障耗时最长的根本原因。

---

### 2_6 端口镜像与 Wireshark 抓包实战
#### 锐捷端口镜像配置
```bash
! 场景：把 gi0/1（接服务器）的流量镜像到 gi0/24（接抓包机）
Ruijie(config)# monitor session 1 source interface gi0/1 both
Ruijie(config)# monitor session 1 destination interface gi0/24 switch
!                                                          ↑ 关键！
Ruijie(config)# end
Ruijie# show monitor session 1
```

> **★ 高频踩坑**：目的端口必须加 `switch` 关键字，否则抓包机只能收包不能发包（表现为"抓包机连上网就断网"或抓包机无法上网）。这是锐捷的特色写法，漏掉会浪费大量时间。

#### 常用变体
```bash
! 只镜像入方向 / 出方向
Ruijie(config)# monitor session 1 source interface gi0/1 rx
Ruijie(config)# monitor session 1 source interface gi0/1 tx

! 镜像整个 VLAN
Ruijie(config)# monitor session 1 source vlan 10 rx

! 删除镜像会话
Ruijie(config)# no monitor session 1

! 远程镜像（RSPAN）思路：源交换机 → 专用 RSPAN VLAN → 目的交换机
```

#### Wireshark 过滤语法（记住这几条能覆盖 90% 场景）
```plain
ip.addr == 192.168.10.10          某主机的所有流量
ip.src == 192.168.10.10           只看源
ip.dst == 192.168.10.10           只看目的
arp                               只看 ARP
icmp                              只看 ping
tcp.port == 80                    某端口
tcp.flags.syn == 1 && tcp.flags.ack == 0   只看 SYN（建连请求）
dhcp                              只看 DHCP 四步
vlan.id == 20                     只看带 VLAN 20 标签的帧
tcp.analysis.retransmission       只看重传（判断丢包）
```

#### 抓包能回答的五个问题
| 问题 | 看什么 |
| --- | --- |
| 包到底有没有发出去？ | 源端抓包，看有没有 Request |
| 包到没到对端？ | 两端同时抓，对比序号 |
| VLAN 标签对不对？ | 看有没有 802.1Q 头，VID 是几 |
| ARP 有没有回应？ | 过滤 arp，看 Request 有无对应 Reply |
| 是丢包还是没发？ | 看有无重传（`tcp.analysis.retransmission`） |

> **现场故事 · 抓包戳破"设备坏了"的误判**  
客户报"服务器时通时断"，一口咬定是核心交换机故障，要求换设备。  
工程师在服务器侧和网关侧同时抓包，过滤 `icmp`，发现：**Request 包发出了，但只有一半有 Reply**；再过滤 `arp`，发现网关 MAC 在两次抓包中**变成了两个不同的值**。  
结论：网络中存在冒充网关的 ARP 欺骗源，与交换机硬件无关。启用 `address-bind` + `arp-check` 后恢复（详见板块10）。  
**复盘**：抓包是唯一能"看到真相"的手段。在争论"是谁的锅"之前，先把它抓下来——**有报文就有真相**。

---

### 2_7 速记卡 · 板块2
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | 跨网段：**IP 全程不变，MAC 每跳重写** | 封装核心 |
| ★2 | 交换机看**目的 MAC**，路由器看**目的 IP** | 转发依据 |
| ★3 | 看到 169.254.x.x → DHCP 没通 | 第一反应 |
| ★4 | VLSM 三步法：算主机位 → 从大到小切块 → 验整除 | 必拿分计算题 |
| ★5 | 锐捷 DHCP 池掩码**必须写全**，不支持 /24 简写 | RGOS 特色坑 |
| ★6 | 免费 ARP 两大作用：冲突检测 + **刷新网关 MAC**（VRRP 靠它） | 切换生效关键 |
| ★7 | 排障组合拳：ipconfig → 环回 → 网关 → 外网IP → DNS → 域名 | 六步缩小范围 |
| ★8 | 镜像目的端口**必须加 **`switch` | 抓包机不上网的元凶 |
| ★9 | `show arp` 是二三层之间的分界证据 | 排障第一查 |
| ★10 | ARP 表 MAC 跳变 = ARP 欺骗，上 address-bind + arp-check | 时通时断 |

## 板块3 · RGOS 设备管理与 CLI 基本功
> **本板块解决什么问题**：把所有命令放进一个"坐标系"里。命令敲错位置是现场事故的头号来源；而"配了没保存"是第二号。这一板块同时解决"怎么上手一台新设备"和"怎么安全地把设备交给别人"。  
对应 RGSA 考纲：RGOS 日常管理操作。这是后面所有实验的前置动作。

---

### 3_1 CLI 四种模式：所有命令的坐标系
锐捷 RGOS 的命令行是**分层模式结构**。命令必须敲在正确的模式下；报错时**第一眼看提示符**，八成问题都是模式不对。

```plain
Ruijie>                       用户模式       只能看少量信息，不能改配置
  │  enable
  ▼
Ruijie#                       特权模式       查看全部、保存、重启、debug
  │  configure terminal
  ▼
Ruijie(config)#               全局配置模式   影响整机的配置
  │  interface gi0/1 / vlan 10 / router ospf 1
  ▼
Ruijie(config-if)#            接口配置模式   影响单个接口
Ruijie(config-vlan)#          VLAN 配置模式  影响单个 VLAN
Ruijie(config-router)#        路由配置模式   影响某个路由进程
Ruijie(config-mst)#           MSTP 配置模式  影响生成树实例
Ruijie(config-if-range)#      接口批量模式   同时影响多个接口
Ruijie(dhcp-config)#          地址池模式     DHCP 地址池配置
Ruijie(config-line)#          线路模式       VTY / Console
```

#### 记忆口诀
+ `exit` **退一级**，`end`（或 `Ctrl+Z`）**直接回特权模式**。
+ 想改配置 → 先进 `config`；想改接口 → 必须进对应的 `interface`。
+ 提示符里的 `(config-if-XXX)` 会显示当前接口名。**敲命令前先看一眼**，防止把配置敲到错误的口上——这是现场最常见的事故来源。

#### 命令帮助与简写
```bash
Ruijie# ?                       ! 查看当前模式下所有可用命令
Ruijie# sh?                     ! 查看以 sh 开头的命令
Ruijie# show run?               ! 补全以 run 开头的参数
Ruijie# show running-config     ! 完整命令
Ruijie# sh run                  ! 等价简写（RGOS 支持唯一前缀简写）
Ruijie# show history            ! 查看历史命令
```

> **交付习惯**：写进交付文档和实验报告时用**完整命令**（便于客户审计和他人接手），敲键盘时用简写（提高效率）。考试选择题里两种都会出现，都要认得。

> **现场故事 · 敲错接口的那三分钟**  
现场要关闭一台接入交换机的 gi0/24（准备拆线），工程师在 `(config)#` 下顺手敲了 `shutdown` 然后回车，接着去拔线。  
结果整台设备失联——因为 `shutdown` 敲在别的接口模式下，关掉的是上联口。团队花了三分钟跑到弱电间用 Console 恢复。  
**复盘**：`shutdown` 这类"影响面大"的命令，敲之前必须确认两件事：**提示符里的接口名**、**这条命令的作用域**。养成"看一眼提示符再回车"的肌肉记忆，能挡掉一大类事故。

---

### 3_2 开局必做七件事与 SSH 远程加固
#### 开局七件事（可整段粘贴）
```bash
! 第1步 进入特权与全局配置
Ruijie> enable
Ruijie# configure terminal

! 第2步 设置设备名（现场第一个必改项，多设备时防止配错机）
Ruijie(config)# hostname SW-Access-3F

! 第3步 设置每日提示信息（& 为终止符，也可用任意未出现在文本中的字符）
SW-Access-3F(config)# banner motd &
Enter TEXT message. End with the character '&'.
Authorized users only. Unauthorized access is prohibited.
&

! 第4步 配置远程登录密码（level 1 普通用户级）与特权密码（level 15 最高级）
SW-Access-3F(config)# enable secret level 1 0 Ruijie@Telnet123
SW-Access-3F(config)# enable secret level 15 0 Ruijie@Enable123
!  level 1~15，15 为最高权限；末尾的 0 表示密码不加密存储
!  生产环境建议用 5（MD5 加密）或启用 service password-encryption

! 第5步 对口令做基础加密
SW-Access-3F(config)# service password-encryption

! 第6步 开启管理服务
SW-Access-3F(config)# enable service web-server        ! 开启 WEB 管理
SW-Access-3F(config)# enable service telnet-server     ! 开启 Telnet
SW-Access-3F(config)# enable service ssh-server        ! 开启 SSH（推荐）

! 第7步 关闭日志干扰（实验环境常用，生产按需要）
SW-Access-3F(config)# no logging console
SW-Access-3F(config)# end
SW-Access-3F# write
```

> **版本提示**：新版本 RGOS 中 `enable services web-server`（带 s）与 `enable service web-server` 两种写法都存在，若报错换另一种即可。  
**生产建议**：**关闭 Telnet、只开 SSH**。Telnet 明文传输密码，抓一次包密码就泄露了。

#### SSH 三件套（替代 Telnet，RGSP 安全要求）
```bash
SW(config)# enable service ssh-server
SW(config)# ip ssh version 2                 ! 强制 SSH v2
SW(config)# crypto key generate rsa          ! 生成密钥对（必需，否则 SSH 起不来）
SW(config)# username admin password Admin@123
SW(config)# username admin privilege 15      ! 直接给最高级
SW(config)# line vty 0 4
SW(config-line)# login local                 ! 使用本地用户名密码认证
SW(config-line)# transport input ssh         ! 只允许 SSH 登录
SW(config-line)# exit
```

> **★ 易漏点**：`crypto key generate rsa` 是 SSH 启用的必要条件。很多人配完 `enable service ssh-server` 发现连不上，就是漏了生成密钥。  
记忆：**开服务 → 定版本 → 生密钥**，三件缺一不可。

#### 用 ACL 限制可登录的源地址（RGSP 考点）
```bash
SW(config)# ip access-list standard 10
SW(config-std-nacl)# permit 192.168.100.0 0.0.0.255
SW(config-std-nacl)# deny any
SW(config-std-nacl)# exit
SW(config)# line vty 0 4
SW(config-line)# access-class 10 in          ! 只有网管网段能登录
```

#### 开局检查清单
```plain
□ hostname 已改，能通过名称分辨设备位置
□ 特权密码已设置且使用加密存储
□ Telnet 已关闭，SSH v2 已启用并生成 RSA 密钥
□ VTY 已用 ACL 限制源地址
□ 接口 description 已写（Uplink-to-XXX / To-XXX）
□ 管理 VLAN 与网管地址已规划
□ 时间已校准（便于日志排障）
□ 已 write 保存
```

---

### 3_3 配置保存、备份、删除与密码恢复
#### 三条保存/备份命令（必须形成肌肉记忆）
```bash
SW# write                                     ! 快速保存（等价 copy run start）
SW# copy running-config startup-config        ! 标准保存命令
SW# copy running-config tftp:                 ! 备份到 TFTP 服务器
```

#### 删除配置（恢复出厂，做实验前必做）
```bash
SW# del flash:config.text      ! 删除配置文件（交换机及 1700 系列路由器）
SW# erase startup-config       ! 删除启动配置（2500 系列路由器）
SW# del flash:vlan.dat         ! 删除 VLAN 配置信息（交换机）
SW# reload                     ! 重启生效
```

**★ 顺序很重要**：

```plain
只删 config 不 reload  → 当前运行配置仍在生效
只 reload 不删        → 配置原样回来
删 + reload 组合      → 才真正回到出厂状态
```

#### 文件与版本查看
```bash
SW# show version               ! 型号、软件版本、运行时间、序列号
SW# show clock                 ! 查看设备时间
SW# show running-config        ! 当前生效配置
SW# show startup-config        ! 下次启动加载的配置
SW# show users                 ! 查看当前登录用户
SW# dir                        ! 查看 flash 中的文件
```

> **★ 排障技巧**：对比 `show running-config` 与 `show startup-config`，能立刻知道"有没有保存"。这是现场最常见的低级错误——配了一下午，断电全没了。

#### 密码恢复思路（RGSA 了解，RGSP 要求会操作）
思路是让设备启动时**跳过配置文件加载**，进入后重新设置密码：

```plain
1. 重启设备，Console 口在启动阶段按指定组合键进入 BootLoader
   （不同型号不同，常见 Ctrl+C 或 Ctrl+B）
        ↓
2. 在 BootLoader 菜单中选择忽略配置文件启动
        ↓
3. 设备以空配置启动后，copy startup-config running-config 载入原配置
   （此时可直接进特权模式，不需要密码）
        ↓
4. 重设 enable secret，最后 write 保存
```

> **注意**：真实操作步骤以具体型号的官方配置手册为准。S2xxx / S5xxx / S6xxx / RSR 各系列进入 BootLoader 的方式不同，不能想当然。密码恢复会中断业务，必须在变更窗口内操作。

---

### 3_4 信息查看命令全集（按用途分组）
#### 设备与配置类
```bash
SW# show version                              ! 版本信息
SW# show running-config                       ! 当前生效配置
SW# show running-config interface gi0/1       ! 只看某个接口的配置
SW# show clock                                ! 设备时间
SW# show users                                ! 在线登录用户
```

#### 接口类（最常用）
```bash
SW# show interface fastethernet 0/3           ! 查看 F0/3 端口详细信息
SW# show interface serial 1/2                 ! 查看 S1/2 串口信息
SW# show interface                            ! 查看所有端口详细信息
SW# show ip interface brief                   ! 简洁汇总（最常用！一眼看全部端口 IP 与状态）
SW# show ip interface                         ! 查看所有端口三层信息
SW# show interfaces status                    ! 端口状态/VLAN/双工/速率/类型汇总
SW# show interfaces counters                  ! 端口流量与错误计数
```

#### 二层表项类
```bash
SW# show mac-address-table                    ! 查看 MAC 地址表
SW# show mac address-table vlan 10            ! 只看 VLAN 10 学到的 MAC
SW# show mac address-table interface gi0/1    ! 只看某端口学到的 MAC
SW# show mac address-table count              ! 统计 MAC 数量（判断是否泛洪/MAC 攻击）
SW# show vlan                                 ! 查看所有 VLAN 信息
SW# show vlan id 10                           ! 查看指定 VLAN
SW# show spanning-tree                        ! 生成树配置与状态
SW# show spanning-tree interface fastethernet 0/1  ! 某端口的生成树状态
```

#### 冗余与聚合类
```bash
SW# show aggregateport 1 summary              ! 查看聚合端口 AG1 的信息
SW# show lacp neighbor                        ! 查看 LACP 邻居（动态聚合排障必看）
SW# show interfaces aggregateport 1           ! 查看聚合口详细状态
SW# show running-config interface aggregateport 1  ! 查看聚合口配置
```

#### 安全与 ACL 类
```bash
SW# show port-security                        ! 查看端口安全配置
SW# show port-security address                ! 查看地址安全绑定信息
SW# show ip access-lists listname             ! 查看名为 listname 的 ACL
SW# show ip dhcp snooping binding             ! 查看 DHCP Snooping 绑定表
```

> **备考建议**：这份"查看命令清单"建议直接抄在实验手册首页。RGSA 选择题中有相当比例的"用哪条命令查看 XX"类题目，属于送分题，不该丢。

---

### 3_5 端口基本配置与接口状态判读
#### 进入端口（单个 / 批量）
```bash
SW(config)# interface fastethernet 0/3                  ! 进入单个端口 F0/3
SW(config)# interface range fa 0/1-2,0/5,0/7-9          ! 批量（逗号分隔，短横线表范围）
SW(config)# interface range gi0/1-4                     ! 千兆口批量
```

> 批量配置是交付效率的命门。接入交换机 24 个口全划 VLAN，用 `interface range` 一条命令搞定，比逐端口敲快 20 倍。

#### 端口常规参数
```bash
SW(config-if)# speed 10              ! 速率，可选 10 / 100 / 1000 / auto
SW(config-if)# duplex full           ! 双工，可选 full / half / auto
SW(config-if)# description Uplink-to-Core   ! 接口描述（现场必配，排障救命）
SW(config-if)# shutdown              ! 管理性关闭端口
SW(config-if)# no shutdown           ! 启用端口
SW(config-if)# speed auto            ! 恢复自协商
SW(config-if)# duplex auto           ! 恢复自协商
```

#### ★ 速率双工黄金规则
**两端要么都 auto，要么都强制。**

一端 auto 一端强制，会协商成"速率对双工错"。典型症状：**能 ping 通，但大文件传输极慢、CRC 错误计数暴涨**。这种"半通不通"的故障最难查，现场遇到先查双工。

#### 端口归属与模式
```bash
SW(config-if)# switchport access vlan 10     ! 将该端口划入 VLAN 10（access 模式）
SW(config-if)# switchport mode trunk         ! 设为 trunk（可选 access / trunk）
SW(config-if)# port-group 1                  ! 划入聚合端口 AG1（详见板块6）
```

#### 接口状态判读（`show ip interface brief`）
| 显示状态 | 含义 | 排查方向 |
| --- | --- | --- |
| `up / up` | 物理和协议都正常 | — |
| `down / down` | 物理层没起来 | 线缆、光模块、对端没开机、端口被 shutdown |
| `up / down` | 物理通但协议不通 | 双工/速率不匹配、封装不匹配、链路协议未 up（PPP 认证失败等） |
| `administratively down` | 被管理性关闭 | 端口下有 `shutdown`，或触发了 err-disable |
| `err-disable` | 被安全机制关闭 | 端口安全 / BPDU Guard / RLDP 触发，见板块5、10 |

#### 错误计数判读（`show interfaces counters`）
| 计数项 | 增长意味着什么 |
| --- | --- |
| CRC 错误持续增长 | 双工不匹配 / 线缆质量问题 / 光衰过大 |
| 大量 collisions | 半双工或 Hub 环境，现代网络罕见 |
| 入向丢包（drops） | 带宽拥塞或队列策略 |
| 巨帧/超短帧 | MTU 不匹配 |

> **现场故事 · "能 ping 通但传文件极慢"**  
一台监控存储服务器接入后，运维反馈"网络时好时坏，拷文件只有几百 KB/s，但 ping 延迟正常、不丢包"。  
工程师查 `show interfaces counters`，发现交换机端口的 **CRC 错误计数在几分钟内涨了几千**。再看 `show interfaces status`，本端是 `auto`，对端服务器网卡被手工固定成了 `100M/full`。  
一端 auto 一端强制 → 协商成"速率对（100M）、双工错（半双工）"。改成两端都 auto 后，速度立刻恢复正常。  
**复盘**：**"能 ping 通但慢"这类软故障，第一反应该是查错误计数，而不是查带宽。** ping 用小包，掩盖了双工问题；大文件传输才会暴露。

---

### 3_6 速记卡 · 板块3
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | 报错先看**提示符**，八成是模式不对 | 命令坐标系 |
| ★2 | `exit` 退一级，`end` / Ctrl+Z 回特权 | 模式切换 |
| ★3 | SSH 三件缺一不可：开服务 + 定版本 + `crypto key generate rsa` | 最易漏 |
| ★4 | 生产环境**关 Telnet 只开 SSH** | 明文=泄露 |
| ★5 | `write` = `copy running-config startup-config` | 保存 |
| ★6 | 恢复出厂必须"**删 + reload**"组合 | 顺序很重要 |
| ★7 | 对比 run/start 可立刻判断"有没有保存" | 排障技巧 |
| ★8 | 速率双工：**两端都 auto 或都强制** | 黄金规则 |
| ★9 | `up/down` 多为协议层问题；CRC 暴涨多为**双工不匹配** | 状态判读 |
| ★10 | `description` 现场必配，是排障时的救命信息 | 交付习惯 |

## 板块4 · 二层交换与 VLAN 体系
> **本板块解决什么问题**：把一个物理局域网按业务切成多个广播域，并搞清楚"同 VLAN 为什么能跨交换机通""不同 VLAN 为什么必须走三层"。这是园区网设计的第一块砖。  
对应 RGSA 考纲：二层交换机工作原理、VLAN（10%）；RGSP 考纲：VLAN 高级特性。

---

### 4_1 二层交换机三动作与 MAC 地址学习
交换机做转发决策，靠的是一张 **MAC 地址表**（CAM 表）。对收到的每一个帧，只可能有三种处理：

| 动作 | 触发条件 | 说明 |
| --- | --- | --- |
| **泛洪（Flood）** | 目的 MAC 不在表中，或是广播/组播地址 | 向同 VLAN 内**除入端口外**的所有端口转发 |
| **转发（Forward）** | 目的 MAC 在表中，且出端口 ≠ 入端口 | 单播精准投递 |
| **丢弃（Discard）** | 目的 MAC 在表中，但出端口 = 入端口 | 同端口回环，直接丢；也可能是 FCS 校验失败 |

#### MAC 地址学习过程
```plain
1. PC-A 发送帧：源 MAC = AAAA，目的 MAC = BBBB
2. 交换机从 gi0/1 收到，先看源 MAC：
   → 写入 MAC 表：AAAA → gi0/1，VLAN 10，老化计时器 300s（默认）
3. 再查目的 MAC BBBB：
   → 表里没有 → 向 VLAN 10 内其他所有端口泛洪
4. PC-B 回应，交换机从 gi0/5 收到源 MAC = BBBB
   → 写入 MAC 表：BBBB → gi0/5
5. 后续 A↔B 的通信变成精准单播转发，不再泛洪
```

#### ★ 核心考点
**交换机只在学习源 MAC，只查目的 MAC。**

这一句话解释了为什么会出现"单向 ping 不通"——MAC 表是双向独立学习的，A 学到 B 不代表 B 学到了 A。

#### 查表验证
```bash
SW# show mac-address-table                      ! 完整 MAC 表
SW# show mac address-table vlan 10              ! 只看某个 VLAN
SW# show mac address-table interface gi0/1      ! 只看某端口
SW# show mac address-table count                ! 统计 MAC 数量
```

> **★ MAC 表项数量异常增长**是判断 MAC 泛洪攻击（或存在环路）的重要手段。正常情况下一个接入端口应该只学到 1-3 个 MAC；如果学到几十上百个，下面一定接了交换机或者有人在攻击（防护见板块10）。

---

### 4_2 VLAN 与 802.1Q：为什么要打标签
#### VLAN 的本质
VLAN（Virtual LAN）把一个物理局域网在**逻辑上**切成多个广播域。核心价值：

+ **隔离广播域**——一个 VLAN 内的广播不会被转发到另一个 VLAN。
+ **安全**——不同部门二层隔离，互访必须走三层，可在三层做 ACL 控制。
+ **灵活**——跨物理位置的主机可以属于同一 VLAN。

#### Access 与 Trunk 的分工
| 端口类型 | 连接对象 | 帧处理 | VLAN 数量 |
| --- | --- | --- | --- |
| **Access** | PC、打印机、摄像头等终端 | 收：打上 PVID 标签   发：**剥离标签**后发出 | 1 个（PVID） |
| **Trunk** | 交换机之间、交换机与路由器/服务器 | 保留标签转发（Native VLAN 除外） | 多个（allowed 列表） |

#### 802.1Q 标签结构（抓包能看到的字段）
```plain
| 目的MAC | 源MAC | 8100 | PRI/CFI/VID | 类型 | 数据 | FCS |
                  ↑         ↑
              TPID(0x8100)  VLAN ID（12bit，范围 1-4094）
```

**PVID（Port VLAN ID）**：端口的缺省 VLAN ID。Access 口的 PVID 就是它所属的 VLAN；Trunk 口的 PVID 是 Native VLAN。

#### Trunk 为什么要保留标签
```plain
同一个 Trunk 链路上传着 VLAN 10 和 VLAN 20 两种帧
    ↓
如果不打标签，对端交换机无从判断"这个帧属于哪个 VLAN"
    ↓
打上 802.1Q 标签 → 对端按标签在正确的 VLAN 内转发
```

> **★ 一句话总结**：**Trunk 的价值就在于能封装并透传 802.1Q 标签**，让对端交换机知道"这个帧属于哪个 VLAN"。

---

### 4_3 VLAN 完整配置与 allowed 四种写法
#### 创建 VLAN（单个 / 批量）
```bash
SW(config)# vlan 10                      ! 创建单个 VLAN
SW(config-vlan)# name OFFICE             ! 命名
SW(config-vlan)# exit
SW(config)# vlan range 10,20,30          ! 批量创建（逗号分隔）
SW(config)# vlan range 10-30             ! 范围创建
SW(config-vlan-range)# exit
```

#### Access 端口
```bash
SW(config)# interface gi0/2
SW(config-if)# switchport mode access
SW(config-if)# switchport access vlan 10
SW(config-if)# description PC-Office
```

> 现场简写：`sw m a` + `sw a v 10`

#### Trunk 端口
```bash
SW(config)# interface gi0/24
SW(config-if)# switchport mode trunk
SW(config-if)# switchport trunk allowed vlan only 10,20,30
SW(config-if)# switchport trunk native vlan 999
SW(config-if)# description Uplink-to-SW2
```

#### ★ allowed 四种写法，效果完全不同（必背）
| 写法 | 含义 | 风险 |
| --- | --- | --- |
| `switchport trunk allowed vlan 10,20` | **追加**到现有列表 | 历史配置残留，可能放通预期外的 VLAN |
| `switchport trunk allowed vlan only 10,20` | **覆盖**为指定列表 | **推荐**，配置结果确定 |
| `switchport trunk allowed vlan add 30` | 在现有基础上**增加** | 需先确认现有列表 |
| `switchport trunk allowed vlan remove 30` | **移除**指定 VLAN | 用于 Trunk 修剪 |

> **★ 交付铁律**：统一用 `only`。用追加写法时，设备里残留的旧 VLAN 会莫名其妙地继续放通，排查起来非常痛苦。

#### 验证命令
```bash
SW# show vlan                                    ! VLAN 列表与端口归属
SW# show vlan id 10                              ! 单个 VLAN 详情
SW# show interfaces gi0/24 switchport            ! 端口二层模式与 trunk 详情
SW# show running-config interface gi0/24         ! 端口配置
SW# show mac address-table vlan 10               ! 该 VLAN 学到的 MAC
```

---

### 4_4 核心实验：同 VLAN 跨交换机通信
#### 网络拓扑（内嵌 ASCII）
```plain
                       Trunk (F0/12)
        ┌────────────────────────────────────┐
        │                                    │
   F0/12│                                    │F0/12
 ┌──────┴───────┐                    ┌───────┴──────┐
 │      S1      │                    │      S2      │
 │              │                    │              │
 │ VLAN 1 (默认)│                    │ VLAN 1 (默认)│
 │ VLAN 20      │                    │ VLAN 30      │
 │ VLAN 30      │                    │              │
 └──────┬───────┘                    └───────┬──────┘
        │                                    │
  F0/4~F0/7                            F0/1~F0/5
  → VLAN 20                            → VLAN 30
        │                                    │
   F0/8~F0/11                          PC1~PC5
   → VLAN 30                           (192.168.30.x)
        │
   PC4~PC7
   (192.168.20.x / 192.168.30.x)
```

**网络要求**：

+ 在 S1 中创建 VLAN 1（默认存在）、VLAN 20、VLAN 30；在 S2 中创建 VLAN 1、VLAN 30。
+ 属于**同一个 VLAN** 的计算机之间可以通信（跨交换机也算）。
+ 属于**不同 VLAN** 的计算机之间不能通信。

#### 配置 S1（逐端口版，理解原理用）
```bash
S1> enable
S1# configure terminal

! 创建 VLAN 20
S1(config)# vlan 20
S1(config-vlan)# name VLAN20
S1(config-vlan)# exit

! 创建 VLAN 30
S1(config)# vlan 30
S1(config-vlan)# name VLAN30
S1(config-vlan)# exit

! 把 F0/4~F0/7 划入 VLAN 20
S1(config)# interface f0/4
S1(config-if)# switchport access vlan 20
S1(config-if)# interface f0/5
S1(config-if)# switchport access vlan 20
S1(config-if)# interface f0/6
S1(config-if)# switchport access vlan 20
S1(config-if)# interface f0/7
S1(config-if)# switchport access vlan 20

! 把 F0/8~F0/11 划入 VLAN 30
S1(config-if)# interface f0/8
S1(config-if)# switchport access vlan 30
S1(config-if)# interface f0/9
S1(config-if)# switchport access vlan 30
S1(config-if)# interface f0/10
S1(config-if)# switchport access vlan 30
S1(config-if)# interface f0/11
S1(config-if)# switchport access vlan 30

! 把 F0/12 配置为 Trunk 模式
S1(config-if)# interface f0/12
S1(config-if)# switchport mode trunk

S1(config-if)# end
S1# show vlan
S1# copy running-config startup-config
```

#### 配置 S2（批量版，现场效率写法）
```bash
S2> enable
S2# configure terminal

! 创建 VLAN 30
S2(config)# vlan 30
S2(config-vlan)# name VLAN30
S2(config-vlan)# exit

! 把 F0/1~F0/5 划入 VLAN 30（批量配置，推荐）
S2(config)# interface range f0/1-5
S2(config-if-range)# switchport access vlan 30
S2(config-if-range)# exit

! 把 F0/12 配置为 Trunk 模式
S2(config)# interface f0/12
S2(config-if)# switchport mode trunk
S2(config-if)# end

S2# show vlan
S2# copy running-config startup-config
```

#### 配置完成后的通信矩阵
| 源 | 目的 | 结果 | 原因 |
| --- | --- | --- | --- |
| S1-VLAN30 的 PC | S2-VLAN30 的 PC | 通 | 同 VLAN，Trunk 透传 |
| S1-VLAN20 的 PC | S1-VLAN30 的 PC | 不通 | 不同 VLAN，二层隔离 |
| S1-VLAN1 的 PC | S2-VLAN1 的 PC | 通 | 同 VLAN（且是 Native VLAN） |
| S1-VLAN20 的 PC | S2-VLAN30 的 PC | 不通 | 不同 VLAN |

#### ★ 为什么互联口必须配 Trunk 而不是 Access
这是整个实验最核心的一句话：**配置 Trunk 是为了让同一 VLAN 跨交换机通信。**

推演两种选择的后果：

```plain
互联口配成 Access 且属于 VLAN X
  → 只有 VLAN X 的流量能通过，其余 VLAN 的帧在出端口时就被丢弃
  → 跨交换机的同 VLAN 通信（除 VLAN X 外）无从谈起

交换机只有 1 个 VLAN（所有端口都在默认 VLAN 1）
  → 互联口配 Access 也能通，因为不存在需要区分的第二个 VLAN
  → 这就是"简单场景两头插上就能通"的原因
```

#### 剥茧看本质：整个实验只有 4 类命令
```plain
1. 进入配置模式    enable → configure terminal
2. 创建 VLAN       vlan 20 / name VLAN20
3. 端口划入 VLAN   switchport access vlan 20
4. 互联口配 Trunk  switchport mode trunk
```

看起来几十行配置，其实就是这四步的重复。**抓住了模式，就不需要背配置。**

> **现场故事 · 一个标签引发的"网络不通"**  
分公司新接入一台交换机，接完后该楼层全部上不了网，但交换机指示灯全亮。  
工程师查了半天路由和地址，均无问题。最后 `show interfaces gi0/24 switchport` 才发现：互联口被前一位同事配成了 `switchport mode access vlan 10`，而该楼层业务在 VLAN 30。  
改成 `switchport mode trunk` + `switchport trunk allowed vlan only 10,30` 后立刻恢复。  
**复盘**：**先看端口模式，再看 IP**。所有"物理连通但业务不通"的故障，第一嫌疑都是二层链路的模式与 VLAN 放通列表。

---

### 4_5 VLAN 间路由：SVI 与单臂路由
不同 VLAN 之间要通信，必须走三层设备。两种实现方式：

#### 方式一：三层交换机 SVI（主流推荐）
```plain
   VLAN 10 ──┐
             ├── 三层交换机（SVI 网关）── 互访
   VLAN 20 ──┘
```

```bash
SW(config)# ip routing                     ! ★ 必须开启三层路由功能
SW(config)# vlan range 10,20
SW(config-vlan-range)# exit
SW(config)# interface vlan 10
SW(config-if-VLAN 10)# ip address 192.168.10.1 255.255.255.0
SW(config-if-VLAN 10)# exit
SW(config)# interface vlan 20
SW(config-if-VLAN 20)# ip address 192.168.20.1 255.255.255.0
SW(config-if-VLAN 20)# exit
```

> **★ 高频翻车点（全库五大致命点之一）**：忘记 `ip routing`。三层交换机 SVI 都配好了、IP 也通，但 VLAN 之间就是不通——十有八九是这个。  
判断方法：`show ip route`，如果只有直连网段而没有跨网段路由能力，检查 `ip routing`。

#### 方式二：单臂路由（路由器子接口）
```plain
          ┌──────────┐
          │  路由器   │
          │ gi0/0.10 │ 192.168.10.1
          │ gi0/0.20 │ 192.168.20.1
          └────┬─────┘
               │ Trunk（放通 10,20）
          ┌────┴─────┐
          │ 二层交换机 │
          └──────────┘
```

```bash
Router(config)# interface gi0/0.10
Router(config-subif)# encapsulation dot1q 10
Router(config-subif)# ip address 192.168.10.1 255.255.255.0
Router(config-subif)# exit
Router(config)# interface gi0/0.20
Router(config-subif)# encapsulation dot1q 20
Router(config-subif)# ip address 192.168.20.1 255.255.255.0
```

> **对比**：SVI 走交换芯片硬件转发，性能好，是园区网标准做法；单臂路由所有跨 VLAN 流量都要上路由器，容易成为瓶颈，只在无三层交换机时使用。

#### 验证
```bash
SW# show ip interface brief              ! 看 SVI 是否 up/up
SW# show ip route                        ! 看直连网段是否进路由表
SW# show running-config | include ip routing   ! 确认三层功能已开
```

---

### 4_6 VLAN 高级特性：Super VLAN 与 Private VLAN
#### Super VLAN（VLAN 聚合）
**解决什么问题**：每个子网都有网络号、广播号、网关号三个地址无法使用，子网划分越细浪费越多。Super VLAN 让多个 Sub VLAN **共用一个三层网段和网关**，节省 IP。

```plain
        Super VLAN 100（192.168.1.1/24，有 SVI，无物理端口）
              │
      ┌───────┼───────┐
   Sub VLAN 10    Sub VLAN 20    Sub VLAN 30
   （只有二层端口，无 SVI）
```

```bash
SW(config)# vlan 100
SW(config-vlan)# supervlan
SW(config-vlan)# exit
SW(config)# vlan range 10,20
SW(config-vlan-range)# exit
SW(config)# vlan 100
SW(config-vlan)# subvlan 10,20
SW(config-vlan)# exit
SW(config)# interface vlan 100
SW(config-if-VLAN 100)# ip address 192.168.1.1 255.255.255.0
```

**Sub VLAN 之间的互通**：默认二层隔离，需要三层互访时开启代理 ARP：

```bash
SW(config)# interface vlan 100
SW(config-if-VLAN 100)# proxy-arp          ! 开启 Sub VLAN 间三层互通
```

> **★ 性能注意事项**：Super VLAN 的广播会向**所有 Sub VLAN 复制**，Sub VLAN 数量不宜过多，否则广播流量被放大，影响整体性能。

#### Private VLAN（私有 VLAN）
**解决什么问题**：同一网段内需要二层隔离（如酒店客房、出租办公、宿舍），但又不希望划太多网段浪费地址。

| 端口类型 | 角色 | 通信规则 |
| --- | --- | --- |
| **Promiscuous（混杂口）** | 连接网关/服务器 | 可与所有端口通信 |
| **Isolated（隔离口）** | 终端 | 只能与混杂口通信，彼此隔离 |
| **Community（团体口）** | 终端 | 可与同团体口和混杂口通信 |

```plain
        网关（Promiscuous）
              │
    ┌─────────┼─────────┐
  客房A     客房B      客房C
 （Isolated，彼此不能互访，但都能上网）
```

```bash
SW(config)# vlan 100
SW(config-vlan)# private-vlan primary
SW(config-vlan)# exit
SW(config)# vlan 101
SW(config-vlan)# private-vlan isolated
SW(config-vlan)# exit
SW(config)# vlan 100
SW(config-vlan)# private-vlan association 101
SW(config-vlan)# exit

! 主机口（隔离口）
SW(config)# interface gi0/1
SW(config-if)# switchport mode private-vlan host
SW(config-if)# switchport private-vlan host-association 100 101

! 混杂口（上联网关）
SW(config)# interface gi0/24
SW(config-if)# switchport mode private-vlan promiscuous
SW(config-if)# switchport private-vlan mapping 100 101
```

#### Native VLAN 规划建议
| 建议 | 说明 |
| --- | --- |
| 不要使用 VLAN 1 承载业务 | VLAN 1 是默认 VLAN，也是多种协议的默认承载 VLAN |
| Native VLAN 改成独立 ID（如 999） | 避免 VLAN 跳跃攻击，且不承载任何业务 |
| **两端 Native VLAN 必须一致** | 不一致会导致 VLAN 流量串扰，且 STP 可能报错 |

---

### 4_7 速记卡 · 板块4
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | 交换机**只学源 MAC，只查目的 MAC** | 单向不通的根源 |
| ★2 | Access 收打标签、发**剥标签**；Trunk 保留标签 | 端口分工 |
| ★3 | 互联口配 Trunk 是为了**同 VLAN 跨交换机**通信 | 实验核心 |
| ★4 | allowed 统一用 `only` 覆盖写法 | 交付铁律 |
| ★5 | VLAN 间路由：**SVI 必须配 **`ip routing` | 五大致命点之一 |
| ★6 | 单臂路由靠子接口 `encapsulation dot1q`，易成瓶颈 | 无三层交换机时的备选 |
| ★7 | MAC 表项异常增长 → 泛洪攻击或环路 | 判读技巧 |
| ★8 | Super VLAN：多 Sub VLAN 共用网段；广播向所有 Sub 复制，**不宜过多** | 性能注意 |
| ★9 | Private VLAN：Isolated 口彼此隔离，只能与 Promiscuous 口通 | 二层隔离 |
| ★10 | Native VLAN 改独立 ID（如 999），且两端一致 | 安全与稳定 |

## 板块5 · 生成树与环路防护：STP / RSTP / MSTP / RLDP
> **本板块解决什么问题**：园区网为提高可靠性必然有冗余链路，但二层冗余就是物理环路。这一板块讲清楚"怎么在保留冗余的前提下逻辑断环"，以及"环路真的发生时用什么兜底"。  
对应 RGSA 考纲：生成树；RGSP 考纲：生成树协议原理与优化、环路检测 RLDP。

---

### 5_1 环路的三个灾难与生成树的本质
园区网为提高可靠性，必然存在冗余链路（双上联、双核心）。但**二层冗余链路 = 物理环路**，会引发三个连锁灾难：

| 灾难 | 成因 | 现象 |
| --- | --- | --- |
| **广播风暴** | 广播帧在环路中无限循环 | 交换机 CPU 100%，全网瘫痪 |
| **MAC 表震荡** | 同一 MAC 从不同端口反复学到 | MAC 表反复刷新，转发错乱 |
| **帧重复** | 同一帧从多条路径到达 | 上层协议处理异常 |

#### 生成树的作用
在保留物理冗余的前提下，通过**逻辑阻塞**某些端口，把环形拓扑修剪成无环的树形拓扑；当活动链路故障时，再自动打开被阻塞的端口恢复连通。

```plain
物理拓扑（有环）              逻辑拓扑（无环树）
   A ───── B                    A ───── B
   │       │                    │
   │       │        →           │        （D 口被阻塞）
   │       │                    │
   C ───── D                    C ───── D
                                        ✗（逻辑断开）
```

> **★ 记住**：生成树不是消除冗余，而是**在冗余和连通之间做取舍**——平时断一条路，断线时换一条路。

> **现场故事 · 一根网线放倒整层楼**  
某办公室工位不够，员工自己从墙上一个网口接了台小交换机，又把小交换机的两根线都插回了墙上相邻的两个网口——**一根线造成了物理环路**。  
三分钟内，整层楼网络瘫痪：交换机指示灯疯狂闪烁，远程登录卡顿到无法操作，ping 网关丢包 100%。  
处理过程：逐台拔掉接入交换机上"一个端口学到多个 MAC"的可疑端口，最终定位到那个工位的小交换机。拔掉后网络立刻恢复。  
**复盘**：广播风暴的特点是**来得极快、影响范围是整个 VLAN**。这类故障的标准处置是：第1步先拔线恢复业务；第2步再查 `show mac address-table count` 定位异常端口；第3步最后补上 BPDU Guard / RLDP 防复发（见 5_5、5_6）。

---

### 5_2 STP（802.1D）三步选举、端口状态与计时器
#### 三步选举
```plain
第一步：选根桥（Root Bridge）
  比较 Bridge ID = 优先级(默认32768) + MAC 地址，越小越优先
        ↓
第二步：每个非根交换机选根端口（Root Port）
  到根桥路径开销最小的端口；开销相同比上游 BID；再相同比上游端口 ID
        ↓
第三步：每条链路选指定端口（Designated Port）
  链路两端中到根桥开销更小的那个端口
        ↓
剩余端口 → 阻塞（Blocking），不转发数据
```

#### 端口状态与计时器
| 状态 | 是否转发数据 | 是否学习 MAC | 停留时长 |
| --- | --- | --- | --- |
| Blocking（阻塞） | ✗ | ✗ | 持续 20s（Max Age） |
| Listening（监听） | ✗ | ✗ | 15s（Forward Delay） |
| Learning（学习） | ✗ | ✓ | 15s（Forward Delay） |
| Forwarding（转发） | ✓ | ✓ | 正常工作 |
| Disabled（禁用） | ✗ | ✗ | 端口 down |

> **★ 关键考点**：STP 从阻塞到转发需要 **30-50 秒**（20s Max Age + 2×15s Forward Delay）。这个收敛速度对现代网络不可接受，因此有了 RSTP。

#### 路径开销标准（常用值）
| 链路速率 | 开销 |
| --- | --- |
| 10M | 100 |
| 100M | 19 |
| 1G | 4 |
| 10G | 2 |

考试常考"哪条链路会被选为根端口"，用开销累加比较即可：

```plain
例：SW-C 到根桥 SW-A
  路径一：SW-C →(1G, cost 4)→ SW-A              累计 4
  路径二：SW-C →(1G, cost 4)→ SW-B →(1G, 4)→ SW-A  累计 8
  → 选路径一，对应端口成为根端口
```

#### BPDU 关键字段
| 字段 | 作用 |
| --- | --- |
| Root ID | 当前认定的根桥 BID |
| Cost of Path | 到根桥的累计路径开销 |
| Bridge ID | 发送者的 BID |
| Port ID | 发送端口的 ID（优先级+端口号） |
| Message Age / Max Age | BPDU 存活时间 |

---

### 5_3 RSTP：把收敛从 50 秒压到 1 秒
RSTP 把状态简化为三种：**Discarding / Learning / Forwarding**，并引入三个关键机制：

| 机制 | 作用 |
| --- | --- |
| **Proposal/Agreement 握手** | 点到点链路快速进入转发，无需等待计时器 |
| **边缘端口（Edge Port）** | 接终端的端口直接进入转发，跳过侦听学习 |
| **Alternate / Backup 端口** | 预先计算好备份路径，主路径故障立即切换 |

**收敛时间**：从 30-50 秒降到 **1 秒以内**（点到点链路）。

```bash
SW(config)# spanning-tree mode rstp         ! 切换为 RSTP 模式
SW# show spanning-tree
```

#### 三种模式对比
| 模式 | 标准 | 收敛 | 实例数 | 适用 |
| --- | --- | --- | --- | --- |
| STP | 802.1D | 30-50s | 单实例 | 了解原理 |
| RSTP | 802.1w | <1s | 单实例 | 简单网络 |
| **MSTP** | 802.1s | <1s | **多实例** | **园区网主流（RGSP 核心）** |

---

### 5_4 MSTP 多实例负载分担（RGSP 核心）
#### MSTP 解决什么问题
STP/RSTP 是**单生成树**：所有 VLAN 共用一棵树，导致被阻塞的链路完全空闲，带宽浪费。

MSTP 的思路：**把多个 VLAN 映射到不同的实例（Instance），每个实例独立计算生成树**。通过让不同实例阻塞不同的链路，实现负载分担。

```plain
            ┌──────────┐                    ┌──────────┐
            │   SW-A   │═══════════════════ │   SW-B   │
            │  核心1   │                    │  核心2   │
            └────┬─────┘                    └─────┬────┘
                 │                                 │
         Gi0/1 ╲ │                                 │ ╱ Gi0/1
                ╲│                                 │╱
                 ├───────────  接入 SW-C   ─────────┤
                            Gi0/2    Gi0/2

实例 1（VLAN 10,20）：SW-A 为根 → 阻塞 SW-C 的 Gi0/2（去 SW-B）
实例 2（VLAN 30,40）：SW-B 为根 → 阻塞 SW-C 的 Gi0/1（去 SW-A）
结果：两个方向的流量各走一条链路，两条链路带宽都被利用
```

#### MSTP 配置三要素（域三要素必须一致）
同一个 MST 域（Region）内的所有交换机，以下三个参数**必须完全一致**，否则会被视为不同域，导致生成树计算异常：

| 要素 | 命令 | 说明 |
| --- | --- | --- |
| 域名 | `name ruijie` | 区分大小写 |
| 修订级别 | `revision 1` | 数值一致即可 |
| VLAN-实例映射表 | `instance 1 vlan 10,20` | 必须逐条一致 |

#### 完整 MSTP 配置（双核心负载分担）
**SW-A（核心 1）**

```bash
Ruijie> enable
Ruijie# configure terminal
Ruijie(config)# hostname SW-A

! 第一步：必须先创建 VLAN，再配实例映射（否则会报 warning）
SW-A(config)# vlan range 10,20,30,40
SW-A(config-vlan-range)# exit

! 第二步：进入 MST 配置模式，配置实例映射
SW-A(config)# spanning-tree                       ! 开启生成树（默认模式为 MSTP）
SW-A(config)# spanning-tree mst configuration
SW-A(config-mst)# name ruijie
SW-A(config-mst)# revision 1
SW-A(config-mst)# instance 1 vlan 10,20        ! VLAN 10,20 映射到实例 1
SW-A(config-mst)# instance 2 vlan 30,40        ! VLAN 30,40 映射到实例 2
SW-A(config-mst)# spanning-tree mst 1 priority 4096    ! 实例 1 的主根
SW-A(config-mst)# spanning-tree mst 2 priority 8192    ! 实例 2 的备份根
SW-A(config-mst)# exit

SW-A(config)# end
SW-A# write
```

> **★ 高频翻车点（全库五大致命点之一）**：**先配 MSTP 实例映射、后建 VLAN** 会报 `%Warning: you must create vlans before configuring mst instance`，且实例映射不生效。  
正确顺序永远是：**先 **`vlan range`** 建 VLAN → 再进 **`spanning-tree mst configuration`** 配实例**。

> **版本提示**：锐捷官方文档中 `spanning-tree mst X priority Y` 是在 `(config-mst)#` 模式下配置的；部分版本也支持在 `(config)#` 全局模式下配置。两种写法效果一致，若一种报错换另一种。

**SW-B（核心 2）**

```bash
Ruijie(config)# hostname SW-B
SW-B(config)# vlan range 10,20,30,40
SW-B(config-vlan-range)# exit
SW-B(config)# spanning-tree
SW-B(config)# spanning-tree mst configuration
SW-B(config-mst)# name ruijie
SW-B(config-mst)# revision 1
SW-B(config-mst)# instance 1 vlan 10,20
SW-B(config-mst)# instance 2 vlan 30,40
SW-B(config-mst)# spanning-tree mst 1 priority 8192    ! 与 SW-A 相反
SW-B(config-mst)# spanning-tree mst 2 priority 4096
SW-B(config-mst)# exit
SW-B(config)# end
SW-B# write
```

**SW-C（接入，只需保证域一致，不改优先级）**

```bash
SW-C(config)# vlan range 10,20,30,40
SW-C(config-vlan-range)# exit
SW-C(config)# spanning-tree
SW-C(config)# spanning-tree mst configuration
SW-C(config-mst)# name ruijie
SW-C(config-mst)# revision 1
SW-C(config-mst)# instance 1 vlan 10,20
SW-C(config-mst)# instance 2 vlan 30,40
SW-C(config-mst)# exit
SW-C(config)# end
SW-C# write
! 不配优先级，默认 32768，自然成为非根
```

#### MSTP 验证命令
```bash
SW# show spanning-tree                          ! 全局生成树状态
SW# show spanning-tree summary                  ! 摘要（看根桥是谁）
SW# show spanning-tree mst configuration        ! 查看域三要素与实例映射
SW# show spanning-tree mst 1                    ! 查看实例 1 的详细状态
SW# show spanning-tree interface gi0/1          ! 查看某端口的生成树状态
SW# clear spanning-tree detected-protocols      ! 清除 STP 检测协议状态
```

#### 优先级取值规则
**优先级必须是 4096 的倍数**，可取值范围共 16 档：0、4096、8192、12288、16384、20480、24576、28672、32768、36864、40960、45056、49152、53248、57344、61440。默认 32768。

| 优先级 | 角色 | 说明 |
| --- | --- | --- |
| 0 或 4096 | 主根桥（Primary） | 数值最小，必定当选根桥 |
| 8192 | 备份根桥（Secondary） | 主根故障后接管 |
| 32768（默认） | 普通交换机 | 不参与根桥竞争 |

---

### 5_5 生成树优化：PortFast、BPDU Guard 与保护特性
#### 问题背景
接 PC 的端口如果参与 STP 计算，PC 开机后需要等待 30-50 秒才能联网——用户体验极差，报障电话立刻就来了。

#### PortFast（边缘端口）
让端口**跳过侦听/学习状态，直接进入转发**。

```bash
SW(config)# interface range gi0/1-24
SW(config-if-range)# spanning-tree portfast
```

执行时会看到提示：

```plain
%Warning: portfast should only be enabled on ports connected to a single host.
Connecting hubs, switches, bridges to this interface when portfast is enabled,
can cause temporary loops.
```

这是正常提示，提醒你**不要把 PortFast 开在接交换机/Hub 的口上**。

> **★ 考点**：PortFast 开启后端口**仍然会发送 BPDU**。它只是跳过状态机，不停止发送 BPDU。这与 BPDU Filter 有本质区别。

#### BPDU Guard（BPDU 防护）
开启 PortFast 的端口如果收到 BPDU（说明下面接了交换机，可能造成环路），立即把端口置为 **err-disable** 状态。

```bash
SW(config)# interface range gi0/1-24
SW(config-if-range)# spanning-tree portfast
SW(config-if-range)# spanning-tree bpduguard enable
```

#### 全局开启（推荐）
```bash
SW(config)# spanning-tree portfast bpduguard default
!  自动作用于所有 PortFast 端口，新增端口自动生效
```

#### BPDU Guard 触发后的恢复
```bash
SW# show interfaces status          ! 确认端口进入 err-disable
SW(config)# errdisable recovery interval 300    ! 300 秒后自动恢复（全局）
SW(config)# errdisable recovery cause bpduguard
SW# errdisable recovery             ! 立即手动恢复（特权模式）
```

#### 其他常用优化特性
| 特性 | 命令 | 作用 |
| --- | --- | --- |
| BPDU Filter | `spanning-tree bpdufilter enable` | 端口不发送也不处理 BPDU（**慎用，会破环**） |
| Root Guard | `spanning-tree guard root` | 防止本端口成为根端口，保护根桥地位 |
| Loop Guard | `spanning-tree guard loop` | 防止单向链路导致环路 |
| 环路保护（全局） | `spanning-tree loopguard default` | 全局开启 |

> **★ BPDU Filter 的正确用法**：一般**只配在接服务器的特定端口**，或明确知道不会有环路的场景。**绝不能在上联口或可能接交换机的端口上开启**——它关闭了 BPDU 收发，等于让生成树在这个端口上"失明"，一旦物理成环就是广播风暴。

#### 保护特性选型建议
```plain
接终端的接入端口  → portfast + bpduguard（标配）
上联核心的端口    → root guard（防止新接入设备抢根）
可能单向链路的光口 → loop guard
接服务器的口      → portfast（可考虑 bpdufilter，但需评估环路风险）
```

---

### 5_6 RLDP 环路检测与部署禁忌
> **承上启下**：5_5 的 BPDU Guard 有一个致命盲区——它靠**识别 BPDU 报文**判断下联是否有交换机，而傻瓜交换机既不发 BPDU 也不转发 BPDU。于是「下联接了一台几十块钱的非网管交换机并造成环路」这个最常见的现场场景，BPDU Guard 完全无感。RLDP 就是为补上这个盲区而存在的。

#### RLDP 与 BPDU Guard 的本质区别（★ 高频考点）
| 对比项 | BPDU Guard | RLDP |
| --- | --- | --- |
| 检测对象 | BPDU 报文 | RLDP 探测报文 |
| 组播 MAC | **公有** `01-80-C2-00-00-00` | **私有** `01-d0-f8-00-00-02` |
| 傻瓜交换机行为 | **丢弃**（不转发） | **转发**（透传） |
| 能检测的场景 | 下联交换机参与 STP | **傻瓜交换机 / Hub 造成的环路** |

> **★ 关键结论**：傻瓜交换机（非网管交换机）会丢弃 BPDU，但会转发 RLDP 报文。所以当环路是由**傻瓜交换机或 Hub** 造成时，BPDU Guard 失效，**只能靠 RLDP 检测**。这是 RLDP 存在的最大意义。

#### RLDP 配置
```bash
! 全局开启
SW(config)# rldp enable

! 接口下配置检测动作
SW(config)# interface range gi0/1-24
SW(config-if-range)# rldp port loop-detect shutdown-port
!                                    ↑ 动作：检测到环路后关闭端口
SW(config-if-range)# exit

! 可选动作
!   shutdown-port   关闭端口（最常用）
!   block           阻塞端口
!   warning         仅告警不动作

! 配置自动恢复（必须配，否则端口一直关闭）
SW(config)# errdisable recovery interval 300
SW(config)# rldp reset               ! 特权模式下手动恢复被关闭的端口
```

#### ★ 部署禁忌（重要）
| 禁忌 | 说明 |
| --- | --- |
| **不要在上联口配置 loop-detect shutdown-port** | 上联口收到的 RLDP 报文可能来自上级网络，误判环路会把上联口关掉，导致整台设备脱网 |
| **AP 成员口（聚合口成员）动作受限** | 聚合组成员口不支持部分 RLDP 动作，配置会报错或无效 |
| **必须配置自动恢复** | 否则一旦触发，端口需要人工 `rldp reset` 才能恢复 |

> **部署建议**：RLDP 只配在**接终端的接入端口**上，上联口和互联口不配或只配 `warning`（仅告警）。

#### 故障日志格式
RLDP 检测到环路后会在日志中留下记录，典型格式：

```plain
%RLDP-4-LOOPDETECT: Loop detect on interface GigabitEthernet 0/5,
    the port is shutdown.
```

排查时看到 `RLDP-4-LOOPDETECT` 开头的日志，即可确认该端口发生了环路并被关闭。

#### 验证命令
```bash
SW# show rldp                        ! 查看 RLDP 全局状态
SW# show rldp interface gi0/5        ! 查看指定端口的 RLDP 状态
SW# show interfaces status           ! 看端口是否被关闭
SW# show log                         ! 查环路日志
```

> **现场故事 · 上联口被 RLDP 关掉的教训**  
某工程师为了"全面防护"，在交换机的**所有端口**（含上联口）统一配置了 `rldp port loop-detect shutdown-port`。  
上线第二天，整台接入交换机脱网。现场 Console 上去一看，日志里是 `RLDP-4-LOOPDETECT: Loop detect on interface GigabitEthernet 0/24`——上联口被关了。  
原因：上级网络中有设备也在跑 RLDP，探测报文透传下来，被本端上联口误判为环路。  
**复盘**：**安全特性不是配得越多越好，而是要配在正确的位置。** RLDP 的价值在接入侧，上联口配它就等于给自己埋了一个定时脱网开关。

---

### 5_7 速记卡 · 板块5
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | 生成树是**在冗余和连通之间取舍**，不是消除冗余 | 逻辑阻塞 |
| ★2 | STP 三步：选根桥 → 选根端口 → 选指定端口，剩余阻塞 | 选举顺序 |
| ★3 | STP 收敛 **30-50s**，RSTP/MSTP **<1s** | 计时器考点 |
| ★4 | MSTP 域三要素：域名 + revision + **VLAN-实例映射**，必须全一致 | 域一致性 |
| ★5 | **先建 VLAN，再配 MST 实例** | 五大致命点之一 |
| ★6 | 优先级必须是 **4096 的倍数**，默认 32768 | 取值规则 |
| ★7 | portfast **仍会发 BPDU**；bpduguard 触发进 **err-disable** | 反常识考点 |
| ★8 | BPDU 用公有 MAC（傻瓜交换机**丢弃**）；RLDP 用私有 MAC（**转发**） | 底层差异 |
| ★9 | 傻瓜交换机造成的环路 → BPDU Guard 失效，**只能靠 RLDP** | RLDP 存在意义 |
| ★10 | **RLDP 不要配上联口**，且必须配自动恢复 | 部署禁忌 |

## 板块6 · 链路聚合与 VSU 网络虚拟化
> **本板块解决什么问题**：解决"带宽不够"和"单点故障"两件事。聚合让多条链路同时干活且毫秒级切换；VSU 让两台物理交换机变成一台逻辑设备，从根本上简化双核心架构。  
对应 RGSP 考纲：网络聚合链路、VSU 网络虚拟化技术。

---

### 6_1 链路聚合解决什么问题（对比 STP 冗余）
核心价值两点：**增加带宽** + **提供冗余**。

与 STP 冗余的本质差异：STP 是"一主一备、备路闲置"，聚合是**所有成员链路同时转发**，带宽不浪费。

| 对比项 | STP 冗余 | 链路聚合 |
| --- | --- | --- |
| 带宽 | 主用链路带宽，备用闲置 | **所有成员链路带宽叠加** |
| 故障切换 | 秒级（依赖 STP 收敛） | **毫秒级**（成员口直接退出聚合组） |
| 配置复杂度 | 需要规划实例和优先级 | 相对简单 |
| 适用场景 | 复杂多路径 | **两设备之间的点对点互联** |
| 能否跨设备 | 能 | 不能（跨设备需 VSU / M-LAG） |

> **★ 关键认知**：聚合把多条物理链路"伪装"成一条逻辑链路，因此 **STP 看到的是一条链路，不会阻塞**——这就是聚合能同时获得带宽和冗余的根本原因。

```plain
STP 视角：                     聚合视角：
  A ═══════ B                   A ═══════ B     ← STP 只看到这一条
  A ┈┈┈┈┈┈┈ B （阻塞）           （两条成员链路同时转发）
```

---

### 6_2 AggregatePort 与两种模式、LACP 配对规则
锐捷 RGOS 中的聚合逻辑接口叫 **AggregatePort**（简称 AP），编号 1-N。注意与其他厂商区分：

| 厂商 | 逻辑接口名 |
| --- | --- |
| **锐捷** | **AggregatePort（AP）** |
| 华为 | Eth-Trunk |
| 华三 | Bridge-Aggregation |
| 思科 | Port-Channel |

#### 两种模式
| 模式 | 命令 | 协商 | 特点 |
| --- | --- | --- | --- |
| **静态聚合（手工）** | `port-group 1`（不带 mode） | 不协商 | 配置简单，对端不支持 LACP 时用；**无协议保护**，配置错误可能环路 |
| **动态聚合（LACP）** | `port-group 1 mode active/passive` | LACPDU 协商 | **推荐**；能检测错连、单向链路 |

#### LACP 两端模式配对规则
| 本端 | 对端 | 能否协商成功 |
| --- | --- | --- |
| active | active | 可以 |
| active | passive | 可以 |
| passive | active | 可以 |
| passive | passive | **不可以**（双 passive 都不主动发，协商不起来） |
| on / 不带 mode | on / 不带 mode | 可以（静态，不走 LACP） |
| on | active | **不可以**（协议不匹配） |

#### ★ 配置严格遵循三阶段
```plain
先建逻辑口  →  再纳物理口  →  后调参数
interface aggregateport 1     port-group 1 mode on/active     switchport mode trunk
                                                              load-balance
                                                              allowed vlan
```

> 顺序反了会报"已关联成员口的 AP 不允许修改二层/三层属性"。此时必须先移除成员口，改完属性再加回来。

---

### 6_3 二层静态聚合（对端不支持 LACP 时）
#### 拓扑
```plain
      ┌────────────┐   Gi0/1  ┌────────────┐
      │            ├──────────┤            │
      │   SW-1     │          │   SW-2     │
      │            ├──────────┤            │
      └────────────┘   Gi0/2  └────────────┘
              AP 1 (Trunk, VLAN 10,20)
```

#### 配置
```bash
! 步骤 1：创建 AggregatePort 逻辑接口
Ruijie(config)# interface aggregateport 1
Ruijie(config-if-AggregatePort-1)# switchport              ! 确保为二层模式（默认）
Ruijie(config-if-AggregatePort-1)# exit

! 步骤 2：把物理端口加入 AP1（静态模式，不带 mode 关键字）
Ruijie(config)# interface range gigabitethernet 0/1-2
Ruijie(config-if-range)# port-group 1
Ruijie(config-if-range)# exit

! 步骤 3：配置 AP1 为 Trunk，放通 VLAN
Ruijie(config)# interface aggregateport 1
Ruijie(config-if-AggregatePort-1)# switchport mode trunk
Ruijie(config-if-AggregatePort-1)# switchport trunk allowed vlan only 10,20
Ruijie(config-if-AggregatePort-1)# description Uplink-Bundle
Ruijie(config-if-AggregatePort-1)# exit

! 步骤 4：调整负载均衡方式
Ruijie(config)# aggregateport load-balance src-dst-ip
Ruijie(config)# end
Ruijie# write
```

> 简写形式 `port-group 1`（不带 mode）在锐捷中等价于**静态聚合**。当前主流版本建议显式写出 mode 以避免歧义，但对端不支持 LACP 时就用不带 mode 的静态写法。

---

### 6_4 二层动态聚合（LACP，核心互联推荐）
```bash
! SW-1 侧
Ruijie(config)# interface aggregateport 1
Ruijie(config-if-AggregatePort-1)# switchport mode trunk
Ruijie(config-if-AggregatePort-1)# switchport trunk allowed vlan only 10,20,30
Ruijie(config-if-AggregatePort-1)# exit
Ruijie(config)# interface range gigabitethernet 0/23-24
Ruijie(config-if-range)# port-group 1 mode active
Ruijie(config-if-range)# exit

! SW-2 侧（active 或 passive 均可）
Ruijie(config)# interface aggregateport 1
Ruijie(config-if-AggregatePort-1)# switchport mode trunk
Ruijie(config-if-AggregatePort-1)# switchport trunk allowed vlan only 10,20,30
Ruijie(config-if-AggregatePort-1)# exit
Ruijie(config)# interface range gigabitethernet 0/23-24
Ruijie(config-if-range)# port-group 1 mode active
Ruijie(config-if-range)# exit

! （可选）开启 LACP 快速检测，加快故障感知
Ruijie(config)# interface range gigabitethernet 0/23-24
Ruijie(config-if-range)# lacp rate fast
```

#### LACP 验证
```bash
Ruijie# show aggregateport 1 summary          ! 聚合口摘要（看成员口状态）
Ruijie# show lacp neighbor                    ! 查看 LACP 邻居（排障必用）
Ruijie# show interfaces aggregateport 1       ! 聚合口详细状态
Ruijie# show running-config interface aggregateport 1
```

**★ 关键看什么**：`show aggregateport 1 summary` 中成员口状态应为 **Selected**（选中）。若显示 **Unselected / Standby**，说明成员口参数不一致或超出最大活动链路数。

#### 聚合协商失败时的日志
```plain
*Dec 17 13:23:52: %LLDP-4-ERRDETECT: Link aggregation for the port
    GigabitEthernet 0/23 may not match with one for the neighbor port.
```

看到这条日志，说明两端聚合配置不匹配（模式、参数、成员口数量不一致），逐项对比即可。

---

### 6_5 三层链路聚合（核心-核心 / 核心-路由器互联）
```bash
! 步骤 1：创建三层 AP 接口并配 IP
Ruijie(config)# interface aggregateport 1
Ruijie(config-if-AggregatePort-1)# no switchport        ! 关键：关闭二层
Ruijie(config-if-AggregatePort-1)# ip address 1.1.1.1 255.255.255.0
Ruijie(config-if-AggregatePort-1)# exit

! 步骤 2：物理口先转三层，再加入聚合组
Ruijie(config)# interface range gigabitethernet 0/23-24
Ruijie(config-if-range)# no switchport                  ! 必须先转三层口
Ruijie(config-if-range)# medium-type fiber              ! 若为光口，指定介质类型
Ruijie(config-if-range)# port-group 1 mode active
Ruijie(config-if-range)# exit

! 步骤 3：三层聚合推荐用源目的 IP 哈希
Ruijie(config)# aggregateport load-balance src-dst-ip
```

> **★ 注意**：**三层聚合必须先 **`no switchport`，否则报"二层口不能加入三层聚合组"。二层聚合的写法（直接 `port-group 1`）不能照搬到三层场景。

---

### 6_6 负载均衡算法与"带宽翻倍"的错觉
#### 可选算法
```bash
Ruijie(config)# aggregateport load-balance {dst-mac | src-mac | src-dst-mac
                                           | dst-ip | src-ip | src-dst-ip}
```

| 算法 | 适用场景 | 说明 |
| --- | --- | --- |
| `src-dst-mac`（**默认**） | 通用二层场景 | 基于源/目的 MAC 哈希 |
| `src-dst-ip`（**三层互联推荐**） | 三层互联、服务器多 IP | 基于源/目的 IP 哈希，VMware ESXi 等场景必需 |
| `src-mac` / `dst-mac` | 流量模型单一时 | 只按单一 MAC 维度哈希，多服务器场景下易偏斜 |
| `src-ip` / `dst-ip` | 特殊优化 | 只按单一 IP 维度哈希，适合流量方向高度固定的场景 |

#### 全局模式 vs AP 口模式（11.x 特性）
> **★ 重要**：11.x 版本支持**对某个 AP 口单独指定负载均衡模式**。
> + 当 AP 口指定了均衡模式时，**按 AP 口指定的生效**，不受全局均衡模式影响；
> + 当 AP 口没有指定时，才采用全局负载均衡模式。

```bash
! 全局模式（影响所有未单独指定的 AP 口）
Ruijie(config)# aggregateport load-balance src-dst-ip

! AP 口模式（优先级更高）
Ruijie(config)# interface aggregateport 1
Ruijie(config-if-AggregatePort-1)# aggregateport load-balance src-dst-mac
```

这个特性在多业务场景下非常有用：核心互联用 `src-dst-ip`，服务器接入用 `src-dst-mac`，各取所需。

#### ★ 为什么"带宽翻倍"常常是错觉
**单条流（同一个五元组：源 IP + 目的 IP + 源端口 + 目的端口 + 协议）永远只走一条成员链路**，这是哈希算法的铁律。

```plain
两台服务器之间传一个文件      → 只用到 1 条链路的带宽（≠ 翻倍）
100 台 PC 同时上网           → 100 个不同源 IP，哈希分散 → 整体带宽接近叠加
```

> **重要提示**：默认设备支持的流量均衡方式为 `src-dst-mac`。不同场景中用户流量特征不同，可能并不能使流量负载均衡到成员链路上，**需要人工调整负载均衡方式**。不同型号、不同软件版本支持的平衡算法可能不同，实际支持情况需按设备版本确认。

#### 验证均衡效果
```bash
Ruijie# show interfaces gigabitethernet 0/23 counters    ! 看各成员口收发包计数
Ruijie# show interfaces gigabitethernet 0/24 counters
```

若发现某个成员口计数几乎为零而另一个满载，说明哈希算法与流量模型不匹配，换算法试试。

---

### 6_7 端口聚合的硬性约束（必背）
| 约束 | 说明 |
| --- | --- |
| **成员口属性必须一致** | 速率、双工、**介质类型**（光口/电口）必须相同 |
| **光口电口不能混绑** | 物理介质不同不允许加入同一组 |
| **千兆与万兆不能混绑** | 速率不同不允许加入同一组 |
| **二层口只能加入二层 AP** | 三层口只能加入三层 AP |
| **已关联成员口的 AP 不允许改二层/三层属性** | 需先移除成员口，改属性后再加回 |
| **通常要求连接到同一对端设备** | 跨设备聚合需 M-LAG / VSU 等高级技术 |

**违反约束的后果**：成员口被置为 Unselected，聚合组降级为部分链路工作；静态模式下更危险——两端参数不一致会直接导致丢包甚至环路。

> **现场故事 · "两条千兆为什么只有千兆"**  
客户做完双链路聚合后测速，发现总带宽仍然只有 1G，怀疑设备有问题。  
排查发现测速用的是两台服务器之间的**单个大文件传输**——这是**一条流**，按哈希只走一条成员链路，本来就不可能跑满 2G。改用多线程测速工具（多流）后，带宽立刻接近 2G。  
**复盘**：向客户交付聚合链路时，**验收方式必须提前说清楚**：单流测试必然只跑单条链路带宽，多流测试才能体现聚合效果。这个误会每年都在发生。

---

### 6_8 VSU 网络虚拟化与双主机检测
> **承上启下**：6_7 留了一个未解决的问题——聚合**不能跨设备**，所以双核心之间的两条链路无法聚合成一条。传统解法是 MSTP 破环 + VRRP 冗余，但代价是配置复杂、链路闲置、收敛慢。VSU 换了个思路：**干脆把两台物理设备变成一台逻辑设备**，跨设备聚合的障碍随之消失。

#### VSU 解决什么问题
传统双核心方案：两台核心 + MSTP 破环 + VRRP 做网关冗余，存在**配置复杂、收敛慢、带宽浪费**的问题。

```plain
传统方案                                VSU 方案
┌─────┐     ┌─────┐                    ┌─────────────────┐
│SW-A │═════│SW-B │                    │      VSU        │
│MSTP │     │MSTP │                    │  （一台逻辑设备） │
│VRRP │     │VRRP │                    │  SW-A + SW-B     │
└──┬──┘     └──┬──┘                    └────────┬────────┘
   └── 聚合/接入 ──┘                            │ 聚合（跨设备，无环）
                                                │
两台设备各自配置，          只需要配一次，两条链路都转发，
需要规划实例、优先级、track    无需 MSTP，切换毫秒级
```

| 对比项 | MSTP + VRRP | VSU |
| --- | --- | --- |
| 配置复杂度 | 高（实例、优先级、track 都要规划） | **低**（一台逻辑设备） |
| 故障切换 | 秒级 | **毫秒级（50-200ms）** |
| 带宽利用 | 需精心设计负载分担 | **天然全带宽** |
| 是否需 MSTP | 是 | **否**（逻辑上无环路） |
| 升级维护 | 可逐台升级，风险低 | 需整体考虑，风险相对高 |

#### VSU 基础配置
```bash
! ===== 主交换机（Switch 1）=====
Ruijie(config)# switch virtual domain 1
Ruijie(config-vs-domain)# switch 1
Ruijie(config-vs-domain)# switch 1 priority 200     ! 优先级高者为主，默认 100
Ruijie(config-vs-domain)# exit

! 配置 VSL（虚拟交换链路）端口
Ruijie(config)# vsl-port 1
Ruijie(config-vsl-port)# port-member interface gi0/25
Ruijie(config-vsl-port)# port-member interface gi0/26
Ruijie(config-vsl-port)# exit

! 转换为 VSU 模式
Ruijie# write memory          ! ★ 切换前必须先保存配置
Ruijie# switch convert mode virtual
!  设备重启后进入 VSU 模式

! ===== 备交换机（Switch 2）=====
Ruijie(config)# switch virtual domain 1
Ruijie(config-vs-domain)# switch 2
Ruijie(config-vs-domain)# switch 2 priority 100
Ruijie(config-vs-domain)# exit
Ruijie(config)# vsl-port 1
Ruijie(config-vsl-port)# port-member interface gi0/25
Ruijie(config-vsl-port)# port-member interface gi0/26
Ruijie(config-vsl-port)# exit
Ruijie# write memory
Ruijie# switch convert mode virtual
```

#### ★ VSU 部署要点
| 要点 | 说明 |
| --- | --- |
| **VSL 链路至少 2 条** | 单条 VSL 会成为单点故障，且 VSL 断裂是双主机故障的根源 |
| **VSU 默认优先级 100** | 优先级高者成为主（Master），另一台为备（Standby） |
| **切换前必须 **`write memory` | 转换模式会重启，未保存的配置会丢失 |
| **两台设备型号与版本需匹配** | 不同型号/版本组建 VSU 可能失败或行为异常 |
| **必须配置双主机检测** | 见下文 |

#### 双主机检测（防止 VSL 断裂后的"脑裂"）
**问题**：如果 VSL 链路全部中断，两台设备都会认为自己是主，同时以相同 IP 和 MAC 对外工作，造成网络混乱——这就是**双主机（Dual-Active）故障**。

**解决方案**：配置一条独立的检测链路（BFD 双主机检测），一旦 VSL 断裂，备机自动进入 recovery 状态（关闭业务端口），只保留主机工作。

```bash
! 配置 BFD 双主机检测（用一对独立物理口直连）
Ruijie(config)# interface gi0/27
Ruijie(config-if)# dual-active detection bfd
Ruijie(config-if)# exit

! 也可用聚合口做检测链路
Ruijie(config)# interface aggregateport 2
Ruijie(config-if-AggregatePort-2)# dual-active detection bfd
Ruijie(config-if-AggregatePort-2)# exit
```

```plain
    ┌─────────────┐   VSL（≥2条）    ┌─────────────┐
    │   Switch 1  │══════════════════│   Switch 2  │
    │  （主）      │                  │   （备）     │
    └──────┬──────┘                  └──────┬──────┘
           │   ← 双主机检测链路（BFD）  →    │
           └────────────────────────────────┘
      VSL 断裂时，靠这条链路判断谁该退出
```

#### VSU 验证
```bash
Ruijie# show switch virtual                  ! 查看 VSU 域与角色
Ruijie# show switch virtual role             ! 查看主备角色
Ruijie# show switch virtual topology         ! 查看 VSU 拓扑
Ruijie# show vsl-port                        ! 查看 VSL 链路状态
Ruijie# show dual-active                     ! 查看双主机检测状态
```

> **部署禁忌**：VSU 组建后，两台设备的配置文件合并为一台。**任何配置修改都会同时影响两台设备的逻辑状态**，因此变更窗口和回退方案要比单机更谨慎。升级时建议先确认 VSL 与双主机检测正常。

---

### 6_9 速记卡 · 板块6
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | 聚合让 STP 只看到**一条链路**，所以既不阻塞又能叠加带宽 | 根本原因 |
| ★2 | 锐捷逻辑口叫 **AggregatePort（AP）** | 与华为 Eth-Trunk 区分 |
| ★3 | 三阶段顺序：**建逻辑口 → 纳物理口 → 调参数** | 顺序不可逆 |
| ★4 | LACP 双 passive **协商不起来**；on 与 active **不匹配** | 配对规则 |
| ★5 | 三层聚合必须先 `no switchport` | 常见报错 |
| ★6 | 成员口状态要看 **Selected**；Unselected 说明参数不一致 | 判读要点 |
| ★7 | **单条流永远只走一条成员链路**——带宽翻倍是多流的叠加效果 | 哈希铁律 |
| ★8 | 光口电口不能混绑、千兆万兆不能混绑、速率双工必须一致 | 硬性约束 |
| ★9 | **VSL 链路至少 2 条**，默认优先级 100，切换前 `write memory` | VSU 部署 |
| ★10 | VSU 必须配**双主机检测（BFD）**，否则 VSL 断裂导致脑裂 | 部署红线 |

## 板块7 · 网关冗余 VRRP 与 BFD 快速检测
> **本板块解决什么问题**：终端的网关只有一个 IP，网关设备一宕机整个 VLAN 就断网。VRRP 让两台设备"共同持有"一个虚拟网关；BFD 解决"链路没 down 但实际不通"时收敛太慢的问题。  
对应 RGSP 考纲：网络冗余 VRRP、BFD。这是 RGSP 实验题的核心评分区。

---

### 7_1 VRRP 解决什么问题
终端的网关 IP 是手工配置或 DHCP 下发的一个固定地址。如果网关是某台三层交换机的 SVI 接口 IP，那么**这台设备一宕机，整个 VLAN 就断网**——即使还有另一台核心交换机在正常工作。

VRRP（Virtual Router Redundancy Protocol）的思路：

```plain
        ┌──────────────┐              ┌──────────────┐
        │    SW-A      │              │    SW-B      │
        │ VLAN10 SVI   │              │ VLAN10 SVI   │
        │ 192.168.10.2 │              │ 192.168.10.3 │
        └──────┬───────┘              └───────┬──────┘
               │        VRRP 组 10            │
               └──────────────┬───────────────┘
                              │
                    虚拟网关 192.168.10.1
                    （虚拟 MAC 0000.5E00.01XX）
                              │
                         终端 PC
                    网关填 192.168.10.1
```

+ 两台设备加入同一个 **VRRP 组**，共同"持有"一个**虚拟 IP**。
+ 终端的网关填这个虚拟 IP，**永远不用改**。
+ 组内在任一时刻只有一台设备是 **Master**（实际转发），其余是 **Backup**（待命）。
+ Master 故障 → Backup 接管 → 终端无感知（切的是 MAC 地址，靠**免费 ARP** 刷新）。

> **★ 关键机制**：VRRP 切换后终端能快速恢复，靠的是新 Master 发送**免费 ARP**（Gratuitous ARP）刷新下游设备的网关 MAC 映射。这一机制在板块2 已铺垫，此处是它的主战场。

---

### 7_2 VRRP 核心机制与虚拟 MAC 换算
#### 角色选举
| 规则 | 说明 |
| --- | --- |
| 优先级高者为 Master | **默认优先级 100**，范围 1-254 |
| 优先级相同，真实 IP 大者为 Master | 次级比较条件 |
| 优先级 255 | 若接口真实 IP 就是虚拟 IP，则该设备自动成为 Master（IP 地址拥有者） |

#### 状态机
```plain
Initialize → Backup → Master
              ↑         │
              └─────────┘  优先级变化 / 超时
```

#### 关键参数
| 参数 | 默认值 | 说明 |
| --- | --- | --- |
| 优先级（Priority） | 100 | 越大越优先 |
| 通告间隔（Advertisement Interval） | 1 秒 | Master 周期性发 VRRP 通告 |
| 抢占（Preempt） | 默认开启 | 高优先级设备恢复后是否抢回 Master |
| 虚拟 MAC | `0000.5E00.01XX` | XX 为 VRRP 组号的十六进制 |

#### ★ 虚拟 MAC 换算（常考）
```plain
VRRP 组 10 → 十六进制 0x0A → 虚拟 MAC 0000.5E00.010A
VRRP 组 20 → 十六进制 0x14 → 虚拟 MAC 0000.5E00.0114
VRRP 组 1  → 十六进制 0x01 → 虚拟 MAC 0000.5E00.0101
```

> 换算方法：把组号转成两位十六进制，拼在 `0000.5E00.01` 后面。抓包时看到这个 MAC，就知道是哪个 VRRP 组在发通告。

---

### 7_3 VRRP 基础配置与验证
```bash
! ★ 先进入 SVI，再配置 VRRP（顺序不能反！）
Ruijie(config)# interface vlan 10
Ruijie(config-if-VLAN 10)# ip address 192.168.10.2 255.255.255.0
Ruijie(config-if-VLAN 10)# vrrp 10 ip 192.168.10.1        ! 组 10，虚拟网关地址
Ruijie(config-if-VLAN 10)# vrrp 10 priority 120           ! 优先级（默认 100）
Ruijie(config-if-VLAN 10)# exit
```

**对端设备**（同一 VLAN，不同真实 IP，相同组号和虚拟 IP）：

```bash
Ruijie(config)# interface vlan 10
Ruijie(config-if-VLAN 10)# ip address 192.168.10.3 255.255.255.0
Ruijie(config-if-VLAN 10)# vrrp 10 ip 192.168.10.1
Ruijie(config-if-VLAN 10)# exit
```

> **★ 最常见的错误**：两台设备的 VRRP 组号不一致，或虚拟 IP 不一致。结果是各自为政，出现**两个 Master**。

#### 验证
```bash
Ruijie# show vrrp                       ! 查看全部 VRRP 组
Ruijie# show vrrp brief                 ! 摘要
Ruijie# show vrrp interface vlan 10     ! 指定接口
```

**★ 必看字段**：State 显示 `Master` 或 `Backup`；Priority 显示当前**生效**优先级（track 后会变）；Virtual IP 是否正确。

#### 双 Master 排查清单
| 排查项 | 命令 |
| --- | --- |
| 组号是否一致 | `show vrrp brief` 两端对比 |
| 虚拟 IP 是否一致 | `show vrrp` 看 Virtual IP 字段 |
| 二层是否通（SVI 之间能互 ping） | `ping 192.168.10.3` |
| Trunk 是否放通该 VLAN | `show interfaces trunk` |
| 是否被 ACL 阻断 VRRP 协议 | 检查是否有 ACL 拒绝 112 号协议 |

---

### 7_4 MSTP + VRRP 联动的双核心负载分担（RGSP 核心场景）
#### 为什么必须联动
VRRP 决定"流量从哪台设备出去"，MSTP 决定"二层路径走哪条链路"。两者如果不一致，会出现**流量绕行**：

```plain
如果 MSTP 实例 1 的根桥是 SW-A，但 VRRP 组 10 的 Master 是 SW-B：
  流量路径：PC → 接入交换机 →(MSTP 选路走 SW-A)→ SW-A → 再绕到 SW-B → 上行
  结果：多一跳，延迟增加，链路带宽浪费，故障域扩大
```

> **★ 这是本板块最重要的设计原则，也是 RGSP 实验题的核心评分点**：  
**让 MSTP 实例的根桥与对应 VRRP 组的 Master 是同一台设备。**

#### 拓扑
```plain
                    ┌────────┐         ┌────────┐
                    │  AR1   │         │  Internet
                    └───┬────┘         └────┬───┘
                        │                   │
        Gi0/2 (三层口)  │                   │ Gi0/2 (三层口)
                 ┌──────┴──────┐     ┌──────┴──────┐
                 │   CORE1     │═════│   CORE2     │
                 │ 核心交换 1  │ AP1 │ 核心交换 2  │
                 └──────┬──────┘     └──────┬──────┘
                    Gi0/0│                  │Gi0/0
                         └────────┬─────────┘
                                  │
                            ┌─────┴─────┐
                            │  ACC-SW   │
                            │ Gi0/3 VLAN10 │
                            │ Gi0/4 VLAN20 │
                            └───────────┘

规划：
  实例 1 = VLAN 10 → 根桥 CORE1，VRRP 组 10 Master = CORE1
  实例 2 = VLAN 20 → 根桥 CORE2，VRRP 组 20 Master = CORE2
```

#### VLAN 与 IP 规划表
| 项目 | VLAN 10（办公） | VLAN 20（监控） |
| --- | --- | --- |
| 网段 | 192.168.10.0/24 | 192.168.20.0/24 |
| 虚拟网关 | 192.168.10.1 | 192.168.20.1 |
| CORE1 SVI | 192.168.10.2 | 192.168.20.2 |
| CORE2 SVI | 192.168.10.3 | 192.168.20.3 |
| VRRP 组 | 10 | 20 |
| Master | CORE1（prio 120） | CORE2（prio 120） |
| MSTP 实例 | 1 | 2 |
| MSTP 根桥 | CORE1（prio 4096） | CORE2（prio 4096） |
| CORE1 上联口 | Gi0/2 192.168.100.2/24 | 同 |
| CORE2 上联口 | Gi0/2 192.168.100.3/24 | 同 |

#### CORE1 完整配置
```bash
Ruijie> enable
Ruijie# configure terminal
Ruijie(config)# hostname CORE1
CORE1(config)# no logging console

! ---- VLAN ----
CORE1(config)# vlan range 10,20
CORE1(config-vlan-range)# exit

! ---- 上联三层口（做 VRRP track 监控目标，必须是三层口）----
CORE1(config)# interface gi0/2
CORE1(config-if-GigabitEthernet 0/2)# no switchport
CORE1(config-if-GigabitEthernet 0/2)# ip address 192.168.100.2 255.255.255.0
CORE1(config-if-GigabitEthernet 0/2)# description To-AR1
CORE1(config-if-GigabitEthernet 0/2)# exit

! ---- 互联聚合口（核心之间）----
CORE1(config)# interface aggregateport 1
CORE1(config-if-AggregatePort-1)# switchport mode trunk
CORE1(config-if-AggregatePort-1)# switchport trunk allowed vlan only 10,20
CORE1(config-if-AggregatePort-1)# exit
CORE1(config)# interface range gi0/23-24
CORE1(config-if-range)# port-group 1 mode active
CORE1(config-if-range)# exit

! ---- 下联接入 Trunk ----
CORE1(config)# interface gi0/0
CORE1(config-if-GigabitEthernet 0/0)# switchport mode trunk
CORE1(config-if-GigabitEthernet 0/0)# switchport trunk allowed vlan only 10,20
CORE1(config-if-GigabitEthernet 0/0)# description To-ACC
CORE1(config-if-GigabitEthernet 0/0)# exit

! ---- SVI + VRRP ----
CORE1(config)# interface vlan 10
CORE1(config-if-VLAN 10)# ip address 192.168.10.2 255.255.255.0
CORE1(config-if-VLAN 10)# vrrp 10 ip 192.168.10.1
CORE1(config-if-VLAN 10)# vrrp 10 priority 120            ! VLAN10 的 Master
CORE1(config-if-VLAN 10)# vrrp 10 track gi0/2 30          ! 监控上联，故障时降 30
CORE1(config-if-VLAN 10)# exit

CORE1(config)# interface vlan 20
CORE1(config-if-VLAN 20)# ip address 192.168.20.2 255.255.255.0
CORE1(config-if-VLAN 20)# vrrp 20 ip 192.168.20.1         ! 优先级默认 100，为 Backup
CORE1(config-if-VLAN 20)# exit

! ---- MSTP ----
CORE1(config)# spanning-tree
CORE1(config)# spanning-tree mst configuration
CORE1(config-mst)# name ruijie
CORE1(config-mst)# revision 1
CORE1(config-mst)# instance 1 vlan 10
CORE1(config-mst)# instance 2 vlan 20
CORE1(config-mst)# spanning-tree mst 1 priority 4096      ! 实例 1 根桥
CORE1(config-mst)# spanning-tree mst 2 priority 8192
CORE1(config-mst)# exit
CORE1(config)# end
CORE1# write
```

#### CORE2 完整配置（对称，优先级相反）
```bash
Ruijie(config)# hostname CORE2
CORE2(config)# no logging console
CORE2(config)# vlan range 10,20
CORE2(config-vlan-range)# exit

CORE2(config)# interface gi0/2
CORE2(config-if-GigabitEthernet 0/2)# no switchport
CORE2(config-if-GigabitEthernet 0/2)# ip address 192.168.100.3 255.255.255.0
CORE2(config-if-GigabitEthernet 0/2)# description To-Internet
CORE2(config-if-GigabitEthernet 0/2)# exit

CORE2(config)# interface aggregateport 1
CORE2(config-if-AggregatePort-1)# switchport mode trunk
CORE2(config-if-AggregatePort-1)# switchport trunk allowed vlan only 10,20
CORE2(config-if-AggregatePort-1)# exit
CORE2(config)# interface range gi0/23-24
CORE2(config-if-range)# port-group 1 mode active
CORE2(config-if-range)# exit

CORE2(config)# interface gi0/0
CORE2(config-if-GigabitEthernet 0/0)# switchport mode trunk
CORE2(config-if-GigabitEthernet 0/0)# switchport trunk allowed vlan only 10,20
CORE2(config-if-GigabitEthernet 0/0)# description To-ACC
CORE2(config-if-GigabitEthernet 0/0)# exit

! ---- SVI + VRRP（与 CORE1 相反）----
CORE2(config)# interface vlan 10
CORE2(config-if-VLAN 10)# ip address 192.168.10.3 255.255.255.0
CORE2(config-if-VLAN 10)# vrrp 10 ip 192.168.10.1         ! 默认 100，为 Backup
CORE2(config-if-VLAN 10)# exit

CORE2(config)# interface vlan 20
CORE2(config-if-VLAN 20)# ip address 192.168.20.3 255.255.255.0
CORE2(config-if-VLAN 20)# vrrp 20 ip 192.168.20.1
CORE2(config-if-VLAN 20)# vrrp 20 priority 120            ! VLAN20 的 Master
CORE2(config-if-VLAN 20)# vrrp 20 track gi0/2 30
CORE2(config-if-VLAN 20)# exit

! ---- MSTP（与 CORE1 相反）----
CORE2(config)# spanning-tree
CORE2(config)# spanning-tree mst configuration
CORE2(config-mst)# name ruijie
CORE2(config-mst)# revision 1
CORE2(config-mst)# instance 1 vlan 10
CORE2(config-mst)# instance 2 vlan 20
CORE2(config-mst)# spanning-tree mst 1 priority 8192
CORE2(config-mst)# spanning-tree mst 2 priority 4096      ! 实例 2 根桥
CORE2(config-mst)# exit
CORE2(config)# end
CORE2# write
```

#### 验证清单
```bash
CORE1# show vrrp brief           ! VLAN10 应为 Master，VLAN20 应为 Backup
CORE2# show vrrp brief           ! 与 CORE1 相反
CORE1# show spanning-tree mst 1  ! 实例 1 根桥应为 CORE1
CORE2# show spanning-tree mst 2  ! 实例 2 根桥应为 CORE2
CORE1# ping 192.168.10.3         ! SVI 之间二层应通
```

---

### 7_5 track 取值规则与失效分析
#### ★ track 降级值的黄金规则
**降级后的优先级必须严格小于备用设备的优先级**，否则切换不会发生。

```plain
本例：CORE1 优先级 120，CORE2 优先级 100（默认）
track 降级 30 → 上联故障时 CORE1 优先级变为 120-30 = 90
90 < 100 → CORE2 升为 Master ✓ 切换成功
```

| 配置 | 降级后 | 是否切换 | 结论 |
| --- | --- | --- | --- |
| prio 120，track 30 | 90 | 是（90 < 100） | 正确 |
| prio 120，track 20 | 100 | **否**（100 = 100，不小于） | **错误** |
| prio 120，track 10 | 110 | **否**（110 > 100） | **错误** |
| prio 150，track 60 | 90 | 是（90 < 100） | 正确 |

> **★ 全库五大致命点之一**：**VRRP track 降级值不够 → 上联断了但不切换**。  
判断公式：`主用优先级 - 降级值 < 备用优先级`（严格小于，不能等于）。

#### track 能监控什么
| 监控对象 | 命令示例 | 检测能力 |
| --- | --- | --- |
| 接口状态（物理 down） | `vrrp 10 track gi0/2 30` | 只能检测直连接口 down |
| BFD 会话 | `vrrp 10 track bfd-session vrrp-uplink 30` | **能检测"接口 up 但对端不通"**（完整配置见 7_6） |
| 路由可达性 | `vrrp 10 track 1 30`（配合 track 对象） | 检测特定路由是否从路由表消失 |

#### 失效分析：track 只配接口会漏掉什么
```plain
场景：CORE1 上联 → 运营商光端机 → 运营商网络

情况一：CORE1 的 gi0/2 直接 down        → track 接口能检测到 ✓
情况二：gi0/2 还 up，但光端机故障/光缆断
        → track 接口检测不到 ✗
        → 流量继续发给 CORE1，然后黑洞
        → 必须靠 BFD 解决（见 7_6）
```

> **现场故事 · "主备切换了但网还是不通"**  
客户做了 VRRP + track，验收时把主用上联线拔掉，切换正常，全场鼓掌。  
结果上线三个月后，运营商侧光缆中断，CORE1 的 gi0/2 指示灯依然亮着（因为中间经过了光端机），track 没有触发，CORE1 仍是 Master，全网出网流量被送到 CORE1 后黑洞——**用户断网两小时**。  
事后整改：把 track 对象从"接口"改成 **BFD 会话**，检测真正的端到端可达性。  
**复盘**：**验收时"拔线测试"通过，不代表"真实故障"能切换。** 拔线只能模拟情况一，真实世界更多是情况二。凡是要花钱买冗余的方案，都必须做"非直连故障"的切换演练。

---

### 7_6 BFD 毫秒级检测与联动
#### BFD 解决什么问题
BFD（Bidirectional Forwarding Detection）是一个**通用的毫秒级故障检测协议**，与介质、协议无关。它解决的核心问题是：**链路没 down，但实际已经不通**。

| 检测方式 | 检测速度 | 能检测"接口 up 但对端不通" |
| --- | --- | --- |
| 接口状态 | 立即（但只在直连 down 时） | 否 |
| 路由协议 Hello（OSPF 默认 10s/40s） | 秒级到几十秒 | 部分 |
| **BFD** | **毫秒级（可配 50ms×3）** | **是** |

#### BFD 与静态路由联动
```bash
! 配置 BFD 会话（与静态路由绑定）
Ruijie(config)# interface gi0/1
Ruijie(config-if)# bfd interval 50 min_rx 50 multiplier 3
Ruijie(config-if)# exit

! 静态路由联动 BFD
Ruijie(config)# ip route 0.0.0.0 0.0.0.0 gi0/1 10.0.0.1 bfd

! 或对端 IP 方式
Ruijie(config)# ip route 0.0.0.0 0.0.0.0 10.0.0.1 track bfd-session 1
```

**参数含义**：`interval 50` 每 50ms 发一次；`min_rx 50` 期望 50ms 收到一次；`multiplier 3` 连续 3 次没收到判定故障 → **150ms 内完成故障感知**。

#### BFD 与 OSPF 联动
```bash
Ruijie(config)# interface gi0/1
Ruijie(config-if)# ip ospf bfd
Ruijie(config-if)# bfd interval 50 min_rx 50 multiplier 3
Ruijie(config-if)# exit
```

> 效果：OSPF 邻居故障检测从默认 40 秒降到 150 毫秒，收敛时间下降两个数量级。

#### BFD 与 VRRP 联动
```bash
! 创建 BFD 会话检测上行链路
Ruijie(config)# bfd-session vrrp-uplink
Ruijie(config-bfd)# bind peer-ip 192.168.100.1 interface gi0/2
Ruijie(config-bfd)# interval 50 min_rx 50 multiplier 3
Ruijie(config-bfd)# exit

! VRRP 联动该 BFD 会话
Ruijie(config)# interface vlan 10
Ruijie(config-if-VLAN 10)# vrrp 10 track bfd-session vrrp-uplink 30
```

#### BFD 验证
```bash
Ruijie# show bfd session              ! 查看所有 BFD 会话
Ruijie# show bfd session detail       ! 详细信息（含收发间隔）
Ruijie# show bfd neighbors            ! 查看 BFD 邻居
```

**★ 关键看**：State 应为 **Up**；若显示 Down/Init，检查两端参数是否匹配、中间是否有设备阻断 BFD 报文（UDP 3784/3785）。

---

### 7_7 速记卡 · 板块7
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | VRRP 两台设备共持一个**虚拟 IP**，终端网关永不改 | 网关冗余 |
| ★2 | 虚拟 MAC = `0000.5E00.01` + 组号十六进制（组10 → 010A） | 常考换算 |
| ★3 | 切换后靠**免费 ARP** 刷新终端网关 MAC | 与板块2 呼应 |
| ★4 | 组号或虚拟 IP 不一致 → **双 Master** | 最常见错误 |
| ★5 | **MSTP 根桥必须与 VRRP Master 是同一台设备** | RGSP 核心评分点 |
| ★6 | track 黄金规则：**主优先级 - 降级值 < 备用优先级**（严格小于） | 五大致命点之一 |
| ★7 | track 接口只能测**直连 down**；中间设备故障测不到 | 失效分析 |
| ★8 | BFD 解决"接口 up 但对端不通"，**毫秒级**（50ms×3） | 联动首选 |
| ★9 | BFD 可与静态路由 / OSPF / VRRP 联动 | 通用检测 |
| ★10 | 验收不能只做"拔线测试"，必须演练**非直连故障** | 交付红线 |

## 板块8 · 路由技术：静态、RIP、OSPF、BGP 与路由控制
> **本板块解决什么问题**：让数据包知道"下一跳去哪"。从一条静态路由起步，到 OSPF 多区域、BGP 属性控制，解决园区网与广域互联的可达性与路径优选问题。  
对应 RGSA 考纲：路由原理和静态路由、OSPF 基础；RGSP 考纲：OSPF 技术、BGP 技术、路由控制；RGSE：BGP 高级特性、ISIS、SR。

---

### 8_1 路由基础：最长匹配、管理距离、度量值
#### 核心动作
路由器收到一个 IP 包，做两件事：

```plain
1. 查路由表，按"最长匹配原则"找最精确的那条路由
2. 按该路由的"下一跳 / 出接口"转发出去
   若没匹配到任何路由 → 直接丢弃（注意：不是泛洪）
```

> **★ 最长匹配原则**：路由表中有 `192.168.0.0/16` 和 `192.168.10.0/24` 两条都能匹配 `192.168.10.5` 的路由时，选 **/24** 那条——掩码越长越精确，优先级越高。这与"管理距离最小优先"是两个不同维度的比较：**先比掩码长度（最长匹配），同长度才比 AD**。

#### 路由表的三大来源
| 来源 | 管理距离（AD） | 说明 |
| --- | --- | --- |
| 直连路由（Connected） | 0 | 接口配了 IP 且 up |
| 静态路由（Static） | 1 | 手工配置 |
| EBGP | 20 | 外部 BGP |
| OSPF | 110 | 链路状态协议 |
| RIP | 120 | 距离矢量协议 |
| IBGP | 200 | 内部 BGP |

> **管理距离越小越可信**。同一条目的路由从多个协议学到时，选 AD 最小的。**这是浮动静态路由的原理基础。**

#### 路由度量值（Metric）
同协议内的多条路由，比较度量值：

| 协议 | 度量依据 |
| --- | --- |
| RIP | 跳数（最大 15 跳，16 跳不可达） |
| OSPF | Cost = 参考带宽 / 接口带宽 |
| BGP | 丰富的路径属性（见 8_6 与板块14） |

#### 查看路由表
```bash
Ruijie# show ip route                    ! 完整路由表
Ruijie# show ip route ospf               ! 只看 OSPF 路由
Ruijie# show ip route static             ! 只看静态路由
Ruijie# show ip route 192.168.10.0       ! 查特定目的地的路由
Ruijie# show ip protocols                ! 查看启用的路由协议
```

---

### 8_2 静态路由、默认路由、浮动静态与等价负载分担
#### 三种写法
```bash
! 方式一：指定下一跳地址（最常用）
Ruijie(config)# ip route 172.16.1.0 255.255.255.0 172.16.2.1
!                    目标网络号      子网掩码          下一跳地址

! 方式二：指定出接口（点到点链路可用）
Ruijie(config)# ip route 172.16.1.0 255.255.255.0 serial 1/2

! 方式三：同时指定出接口和下一跳（推荐）
Ruijie(config)# ip route 172.16.1.0 255.255.255.0 gi0/1 172.16.2.1
```

> **★ 方式二的坑**：在以太网（广播型多路访问）链路上只写出接口，路由器会对每个目的地址做 ARP 解析，可能导致下一跳无法解析而失败。**以太网环境务必写下一跳 IP**。串口点到点链路可以只写出接口。

#### 默认路由
```bash
Ruijie(config)# ip route 0.0.0.0 0.0.0.0 192.168.100.1
```

#### 浮动静态路由（主备链路）
**原理**：同一目的配两条静态路由，主用路由 AD 用默认 1，备用路由手工设置更大的 AD。主用失效时备用自动浮现。

```bash
! 主用：走专线，AD = 1（默认）
Ruijie(config)# ip route 0.0.0.0 0.0.0.0 10.0.0.1

! 备用：走 4G/宽带，AD = 200（比任何动态协议都大，仅在主用失效时用）
Ruijie(config)# ip route 0.0.0.0 0.0.0.0 10.0.1.1 200
```

```bash
Ruijie# show ip route 0.0.0.0
! 正常时只显示主用那条；主用链路 down 后，备用的自动进入路由表
```

> **★ 局限**：浮动路由只能检测"直连接口 down"。如果主用链路是"接口还 up 但对端不通"（比如经过一台中间设备），浮动路由不会切换。这种情况要用 **BFD 联动**（见板块7）。

#### 等价负载分担
```bash
! 两条相同 AD、相同度量值的路由 → 流量等价分担
Ruijie(config)# ip route 0.0.0.0 0.0.0.0 10.0.0.1
Ruijie(config)# ip route 0.0.0.0 0.0.0.0 10.0.1.1
```

#### 黑洞路由（防环小技巧）
```bash
! 把汇总网段指向 null0，防止汇总路由与默认路由形成环路
Ruijie(config)# ip route 192.168.0.0 255.255.0.0 null 0
```

---

### 8_3 RIP 与 RIPv1/v2 对比
#### 配置
```bash
Ruijie(config)# router rip                  ! 开启 RIP 进程
Ruijie(config-router)# network 172.16.1.0   ! 声明本设备的直连网段（主类网络号）
Ruijie(config-router)# version 2            ! 开启 RIPv2（v1/v2 可选）
Ruijie(config-router)# no auto-summary      ! 关闭自动汇总（仅 RIPv2 支持）
Ruijie(config-router)# exit
```

#### RIPv1 与 RIPv2 对比
| 特性 | RIPv1 | RIPv2 |
| --- | --- | --- |
| 有类/无类 | 有类（不携带掩码） | **无类**（携带掩码，支持 VLSM） |
| 更新方式 | 广播 255.255.255.255 | **组播 224.0.0.9** |
| 认证 | 不支持 | 支持明文/MD5 |
| 自动汇总 | 总是开启 | 可 `no auto-summary` 关闭 |

**跳数限制**：最大 15 跳，16 跳即不可达——这决定了 RIP 只能用于小型网络。

```bash
Ruijie# show ip rip                  ! 查看 RIP 配置
Ruijie# show ip rip database         ! 查看 RIP 数据库
Ruijie# debug ip rip                 ! 调试 RIP（生产慎用）
```

> 定位：RGSA 了解原理即可，实际工程几乎不用。考试重点在 v1/v2 差异与 15 跳限制。

---

### 8_4 OSPF 基础：邻居七状态、网络类型、单区域配置
#### 基本概念
| 概念 | 说明 |
| --- | --- |
| **Router ID** | OSPF 路由器标识，必须全网唯一。选举顺序：手工指定 > Loopback 最大 IP > 物理接口最大 IP |
| **Area** | 区域，Area 0 是骨干区域，其他区域必须与 Area 0 相连 |
| **Cost** | 开销 = 参考带宽 / 接口带宽，沿路径累加 |
| **邻居（Neighbor）** | 二层/三层直连且参数匹配的路由器 |
| **邻接（Adjacency）** | 完成 LSDB 同步的邻居，真正交换路由信息 |

#### 五种报文
| 报文 | 作用 |
| --- | --- |
| Hello | 发现、建立、维护邻居关系（默认 10s 一次，Dead 40s） |
| DBD（Database Description） | 描述 LSDB 摘要 |
| LSR（Link State Request） | 请求缺少的 LSA |
| LSU（Link State Update） | 发送 LSA |
| LSAck | 确认 |

#### 邻居建立的七个状态
```plain
Down → Init → 2-Way → ExStart → Exchange → Loading → Full
                 ↑                                    ↑
            DR/BDR 选举完成                        LSDB 同步完成
```

#### ★ 必须匹配的 Hello 参数（不匹配则卡在 Init/2-Way）
| 参数 | 说明 |
| --- | --- |
| Hello/Dead 时间 | 两端必须一致 |
| Area ID | 必须在同一区域 |
| 认证类型和密钥 | 必须一致 |
| 区域类型（Stub/NSSA） | 必须一致 |
| 网络掩码（广播型网络） | 必须一致 |
| Router ID | **必须不同**（相同则邻居振荡） |
| MTU | ExStart 阶段 DBD 携带，**不一致会卡在 ExStart/Exchange** |

#### 网络类型
| 类型 | 典型链路 | 是否选 DR/BDR | Hello/Dead |
| --- | --- | --- | --- |
| Broadcast（广播） | 以太网 | 是 | 10s / 40s |
| Point-to-Point（点到点） | PPP、HDLC 专线 | 否 | 10s / 40s |
| NBMA | 帧中继、ATM | 是 | 30s / 120s |
| Point-to-Multipoint | — | 否 | 30s / 120s |

> **DR/BDR 的作用**：广播型网络中，若 n 台路由器两两建立邻接，需要 n(n-1)/2 个会话。选出 DR 后，所有路由器只与 DR/BDR 建立邻接，会话数降到 2n 量级。**★ DRother 之间停留在 2-Way 状态是正常现象，不是故障。**

#### 单区域基础配置（RGSA）
```bash
! 锐捷部分老型号（如 1762）不需要进程号
Ruijie(config)# router ospf
! 主流型号需要进程号
Ruijie(config)# router ospf 1

Ruijie(config-router)# router-id 1.1.1.1              ! 强烈建议手工指定
Ruijie(config-router)# network 192.168.1.0 0.0.0.255 area 0
!                       直连网段      反掩码(Wildcard)  区域号
Ruijie(config-router)# exit
```

**反掩码（Wildcard Mask）**：`0` 表示必须匹配，`255` 表示不关心。

| 掩码 | 反掩码 |
| --- | --- |
| /24（255.255.255.0） | 0.0.0.255 |
| /30（255.255.255.252） | 0.0.0.3 |
| /25（255.255.255.128） | 0.0.0.127 |
| /32（精确主机） | 0.0.0.0 |

> **速算**：反掩码 = 255.255.255.255 减去子网掩码。

#### 三层交换机上跑 OSPF
```bash
SW(config)# ip routing                          ! 必须开启三层路由功能
SW(config)# vlan range 10,20
SW(config-vlan-range)# exit
SW(config)# interface vlan 10
SW(config-if-VLAN 10)# ip address 192.168.10.1 255.255.255.0
SW(config-if-VLAN 10)# exit
SW(config)# interface gi0/1
SW(config-if)# no switchport
SW(config-if)# ip address 10.0.0.2 255.255.255.252
SW(config-if)# exit

SW(config)# router ospf 1
SW(config-router)# router-id 2.2.2.2
SW(config-router)# network 192.168.10.0 0.0.0.255 area 0
SW(config-router)# network 10.0.0.0 0.0.0.3 area 0
SW(config-router)# passive-interface vlan 10     ! 业务 VLAN 不向外发 Hello
SW(config-router)# exit
```

> **★ passive-interface 的作用**：VLAN 10 下接的是终端，不需要与之建立 OSPF 邻居。配置后该接口**不发 Hello 报文，但网段仍会被通告进 OSPF**。既减少协议开销，又防止有人接入一台跑 OSPF 的设备干扰网络。

#### 调整 Cost
```bash
Ruijie(config)# interface gi0/1
Ruijie(config-if)# ip ospf cost 10               ! 直接指定 cost
! 或修改参考带宽（全局，影响所有接口 cost 计算）
Ruijie(config)# router ospf 1
Ruijie(config-router)# auto-cost reference-bandwidth 10000   ! 单位 Mbps
```

#### OSPF 验证
```bash
Ruijie# show ip ospf neighbor              ! 邻居状态（看是否 Full）
Ruijie# show ip ospf interface gi0/1       ! 接口 OSPF 参数（Hello/Dead/网络类型）
Ruijie# show ip ospf database              ! LSDB
Ruijie# show ip route ospf                 ! OSPF 学到的路由
Ruijie# show ip ospf                       ! 进程信息（RID、区域）
```

> **现场故事 · 卡在 ExStart 的两个小时**  
园区网新增一台路由器与核心建立 OSPF 邻居，状态一直停在 ExStart，反复振荡。  
逐项核对 Hello/Dead、区域号、认证、掩码——全部一致。最后 `show ip ospf interface` 发现一端 MTU 1500，另一端 9000。  
OSPF 在 ExStart 阶段交换的 DBD 报文里携带接口 MTU，两端不一致就无法进入 Exchange。对齐 MTU 后立刻 Full。  
**复盘**：**邻居起不来时，按"Hello 参数 → Router ID → MTU → 网络类型"的顺序查**，MTU 是最容易被忽略的一项，尤其在对接不同厂商或启用了巨帧的环境。

---

### 8_5 OSPF 多区域、LSA、特殊区域、汇总与认证
#### 为什么要分区域
单区域规模变大后，LSDB 膨胀、SPF 计算频繁、路由震荡影响全网。分区域后：

```plain
         Area 0（骨干）
    ┌──────────┼──────────┐
   ABR        ABR        ABR
    │          │          │
 Area 10    Area 20    Area 30
```

+ 区域内路由（Intra-Area）由本区域 SPF 计算
+ 区域间路由（Inter-Area）由 ABR 传递汇总
+ **★ 所有非骨干区域必须直接与 Area 0 相连**

#### 常用 LSA 类型（必考）
| LSA | 名称 | 产生者 | 作用范围 | 说明 |
| --- | --- | --- | --- | --- |
| Type 1 | Router LSA | 每台路由器 | 本区域内 | 描述自己的链路和 cost |
| Type 2 | Network LSA | DR | 本区域内 | 描述广播型网络的成员 |
| Type 3 | Summary LSA | ABR | 区域间 | 把一个区域的路由通告到另一区域 |
| Type 4 | ASBR Summary | ABR | 区域间 | 告诉其他区域"ASBR 在哪" |
| Type 5 | AS External | ASBR | 整个 AS | 外部路由（重分布进来的） |
| Type 7 | NSSA External | ASBR（NSSA 内） | NSSA 内 | NSSA 区域的外部路由，出 NSSA 时被 ABR 转成 Type 5 |

#### 路由器角色
| 角色 | 含义 |
| --- | --- |
| **内部路由器** | 所有接口都在同一区域 |
| **ABR** | 区域边界路由器，至少一个接口在 Area 0 |
| **ASBR** | 自治系统边界路由器，把外部路由重分布进 OSPF |
| **Backbone Router** | 至少一个接口在 Area 0 |

#### 特殊区域（减少 LSA、缩小 LSDB）
| 区域类型 | 允许的 LSA | 特点 | 能否引入外部路由 |
| --- | --- | --- | --- |
| **普通区域** | 1/2/3/4/5 | 默认 | 能 |
| **Stub** | 1/2/3（+ 默认路由） | 拒绝 Type 4/5，ABR 下发默认路由 | 不能 |
| **Totally Stubby** | 1/2（+ 默认路由） | 拒绝 3/4/5，只有默认路由出区域 | 不能 |
| **NSSA** | 1/2/3/7 | 允许本区域引入外部路由（以 Type 7 存在） | 能（Type 7） |
| **Totally NSSA** | 1/2/7（+ 默认路由） | 拒绝 Type 3/4/5，保留 7 | 能（Type 7） |

```bash
! Stub 区域配置（区域内所有路由器都要配）
Ruijie(config)# router ospf 1
Ruijie(config-router)# area 10 stub

! Totally Stubby（只在 ABR 上配）
Ruijie(config-router)# area 10 stub no-summary

! NSSA
Ruijie(config-router)# area 20 nssa
! NSSA 的 ABR 上可配 no-summary 变成 Totally NSSA
Ruijie(config-router)# area 20 nssa no-summary
```

> **★ 记忆口诀**：Stub 家族的进化方向是"LSA 越来越少，默认路由兜底"。区域越大、设备越弱，越该用 Stub 家族压缩 LSDB。

#### 路由汇总
```bash
! ABR 上做区域间汇总（把 Area 10 内的多个网段汇总后通告进 Area 0）
Ruijie(config)# router ospf 1
Ruijie(config-router)# area 10 range 192.168.0.0 255.255.240.0

! ASBR 上做外部路由汇总
Ruijie(config-router)# summary-address 172.16.0.0 255.255.0.0
```

> 汇总的价值：**减少 LSDB 规模、隐藏拓扑变化**。某条明细链路抖动时，如果做了汇总，其他区域感知不到，网络更稳定。

#### 认证（三种）
```bash
! 1. 接口明文认证
Ruijie(config)# interface gi0/1
Ruijie(config-if)# ip ospf authentication
Ruijie(config-if)# ip ospf authentication-key ruijie123

! 2. 接口 MD5 认证（推荐）
Ruijie(config-if)# ip ospf authentication message-digest
Ruijie(config-if)# ip ospf message-digest-key 1 md5 ruijie123

! 3. 区域认证（整个区域统一）
Ruijie(config)# router ospf 1
Ruijie(config-router)# area 0 authentication message-digest
```

> **注意**：认证类型和密钥两端必须一致，否则邻居起不来。**MD5 认证的 key-id 也必须相同。**

#### 多区域配置示例
```bash
! ABR：接口 gi0/1 在 Area 0，接口 gi0/2 在 Area 10
Ruijie(config)# router ospf 1
Ruijie(config-router)# router-id 1.1.1.1
Ruijie(config-router)# network 10.0.0.0 0.0.0.3 area 0
Ruijie(config-router)# network 192.168.10.0 0.0.0.255 area 10
Ruijie(config-router)# area 10 range 192.168.10.0 255.255.255.0
Ruijie(config-router)# passive-interface vlan 10
Ruijie(config-router)# exit
```

---

### 8_6 BGP 基础：邻居、通告、属性与验证
#### BGP 定位
BGP 是**外部网关协议**，用于 AS 之间传递路由。与 OSPF 这类 IGP 的本质差异：

| 对比项 | OSPF/ISIS（IGP） | BGP（EGP） |
| --- | --- | --- |
| 目标 | 快速发现最短路径、自动收敛 | **可控地传递大量路由、执行策略** |
| 度量 | Cost | **丰富的路径属性** |
| 收敛 | 快（秒级） | 慢（设计如此，追求稳定） |
| 适用 | 一个机构内部 | AS 之间、大型骨干 |

#### 两种邻居
| 类型 | 说明 | 典型要求 |
| --- | --- | --- |
| **EBGP** | 不同 AS 之间 | 通常直连，TTL=1 |
| **IBGP** | 同一 AS 内部 | 常用 Loopback 建邻，需 `update-source` |

#### 基础配置
```bash
Ruijie(config)# router bgp 65001
Ruijie(config-router)# router-id 1.1.1.1

! EBGP 邻居（直连）
Ruijie(config-router)# neighbor 10.0.0.2 remote-as 65002

! IBGP 邻居（用 Loopback，推荐）
Ruijie(config-router)# neighbor 2.2.2.2 remote-as 65001
Ruijie(config-router)# neighbor 2.2.2.2 update-source loopback 0
Ruijie(config-router)# neighbor 2.2.2.2 next-hop-self

! 通告网段（★ 网段必须已存在于路由表中）
Ruijie(config-router)# network 192.168.1.0 mask 255.255.255.0
Ruijie(config-router)# exit
```

> **★ BGP network 命令的本质**：不是"在接口上启用 BGP"，而是"把路由表中已存在的某条路由放进 BGP 表"。**路由表里没有这条路由，network 就不生效**——这是新手最常踩的坑。

#### IBGP 水平分割与全互联
**规则**：从 IBGP 邻居学到的路由**不再转发给其他 IBGP 邻居**。因此 AS 内需要 **IBGP 全互联**（n 台设备需 n(n-1)/2 会话）。解决方案：**路由反射器（RR）** 或 **联盟**（详见板块14）。

#### 关键属性（入门）
| 属性 | 方向 | 说明 |
| --- | --- | --- |
| **AS_Path** | 防环 + 选路 | 记录经过的 AS 号，**越短越优**；收到含自己 AS 号的路由即丢弃 |
| **Next_Hop** | 可达性 | 下一跳地址，IBGP 中默认不变，常需 `next-hop-self` |
| **Local_Pref** | 出方向 | AS 内有效，**越大越优**；管"我怎么出去" |
| **MED** | 入方向 | 可选非传递属性：只随路由通告给相邻 AS，不会再被传到第三个 AS，**越小越优**；管"别人怎么进来" |

#### 验证
```bash
Ruijie# show ip bgp summary                  ! 邻居状态（看 State/PfxRcd）
Ruijie# show ip bgp                          ! BGP 表
Ruijie# show ip bgp 192.168.1.0              ! 某前缀的所有路径与属性
Ruijie# show ip bgp neighbors 10.0.0.2 advertised-routes
Ruijie# show ip bgp neighbors 10.0.0.2 received-routes
```

**★ 邻居状态看什么**：`show ip bgp summary` 中 State 列显示数字（收到的路由数）表示已建立；显示 `Active`/`Idle`/`Connect` 表示**未建立**，需排查：可达性（ping 通吗）、AS 号、update-source、TTL。

---

### 8_7 策略路由 PBR 与路由重分布
#### 策略路由 PBR：按"源"决定路径
**与路由表的本质区别**：路由表按"目的地址"转发；PBR 可以按"源地址、协议、端口、报文长度"等条件强制指定下一跳，**优先级高于路由表**。

```plain
场景：服务器网段 172.16.50.0/24 的流量必须绕行安全审计设备 10.0.9.2，
      其余流量仍按路由表正常转发。
```

```bash
! 1. 用 ACL 匹配需要特殊处理的流量
Ruijie(config)# ip access-list extended TO-AUDIT
Ruijie(config-ext-nacl)# permit ip 172.16.50.0 0.0.0.255 any
Ruijie(config-ext-nacl)# exit

! 2. 用 route-map 设置下一跳
Ruijie(config)# route-map PBR-AUDIT permit 10
Ruijie(config-route-map)# match ip address TO-AUDIT
Ruijie(config-route-map)# set ip next-hop 10.0.9.2
Ruijie(config-route-map)# exit

! 3. 在入接口应用（注意是流量进入设备的接口）
Ruijie(config)# interface vlan 50
Ruijie(config-if-VLAN 50)# ip policy route-map PBR-AUDIT
Ruijie(config-if-VLAN 50)# exit
```

> 多出口分流（办公走电信、访客走联通）是 PBR 的另一类典型应用，完整配置见 **板块9_5**，此处不重复。

```bash
Ruijie# show route-map                       ! 查看 route-map 及匹配计数
Ruijie# show ip policy                       ! 查看接口应用的策略
```

> **★ 注意**：PBR 应用在**流量进入设备的入接口**上，应用在出接口无效。另外，若 `set ip next-hop` 指定的下一跳不可达，PBR 会**回退到普通路由表转发**（即"策略失效但不丢包"）；只有在明确配置了"下一跳不可达则丢弃"的严格模式时，流量才会被丢弃。这个默认行为要记住——它的好处是下一跳故障时业务不会硬断，代价是流量会走回原路径、可能不符合策略预期。

#### 路由重分布（双向引入）
把一种路由协议的路由注入另一种协议。典型场景：出口路由器上静态路由 / 直连网段引入 OSPF，让内网学到默认路由。

```bash
Ruijie(config)# router ospf 1
! 把静态路由重分布进 OSPF
Ruijie(config-router)# redistribute static subnets
! 把直连网段重分布进 OSPF
Ruijie(config-router)# redistribute connected subnets
! 重分布时指定 metric 与类型
Ruijie(config-router)# redistribute static subnets metric 20 metric-type 1
! 下发默认路由（最常用）
Ruijie(config-router)# default-information originate always
```

| 参数 | 作用 |
| --- | --- |
| `subnets` | **必须加**，否则只重分布主类网络，子网不会被引入 |
| `metric` | 指定引入后的 cost |
| `metric-type 1/2` | 外部路由类型，**Type 2 为默认**（不累加内部 cost） |
| `route-map` | 过滤或设置属性，防止引入不需要的路由 |

#### 重分布的风险与防范
| 风险 | 防范 |
| --- | --- |
| **路由环路**（双点双向重分布） | 用 route-map + tag 过滤；只做单点重分布或用 `distance` 调整 |
| **次优路径** | 调整 AD 或修改 metric |
| **路由条目爆炸** | 用 route-map 只引入必要网段 |
| **引入不该引的路由** | 用 prefix-list / ACL 精确匹配 |

```bash
! 用 route-map 精确控制只引入特定网段
Ruijie(config)# ip prefix-list TO-OSPF permit 172.16.0.0/16
Ruijie(config)# route-map STATIC-TO-OSPF permit 10
Ruijie(config-route-map)# match ip address prefix-list TO-OSPF
Ruijie(config-route-map)# exit
Ruijie(config)# router ospf 1
Ruijie(config-router)# redistribute static subnets route-map STATIC-TO-OSPF
```

> **现场故事 · 一次重分布引发的路由环路**  
双核心都做了"静态 ↔ OSPF"双向重分布。某天一条外部专线 flapping（反复 up/down），结果整个网络出现间歇性丢包。  
抓包发现 ICMP 报文在两台核心之间来回转发（TTL 递减）——典型的**重分布环路**：核心 A 从 OSPF 学到路由后引入静态，核心 B 又从静态引入回 OSPF，形成环路。  
整改：只在**一台**核心上做重分布，另一台通过 OSPF 学习；并用 route-map + tag 做防环标记。  
**复盘**：**双点双向重分布是路由环路的经典温床。** 能单点就单点，必须双点时一定要用 tag 互相过滤。这条规则在 RGSE 排障题里反复出现。

---

### 8_8 速记卡 · 板块8
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | **先比掩码长度（最长匹配），同长度才比 AD** | 两个维度别混淆 |
| ★2 | 以太网静态路由**必须写下一跳 IP**，只写出接口会 ARP 失败 | 常见错误 |
| ★3 | 浮动路由靠 AD 实现主备，但**只能测直连 down** | 需 BFD 补足 |
| ★4 | RIP 最大 **15 跳**，v2 组播 224.0.0.9 | 了解级 |
| ★5 | OSPF 七状态：Down→Init→2-Way→ExStart→Exchange→Loading→Full | 必背 |
| ★6 | **DRother 之间停在 2-Way 是正常现象** | 不是故障 |
| ★7 | 邻居参数：Hello/Dead、Area ID、认证、区域类型、掩码、RID 不同、**MTU** | 排查顺序 |
| ★8 | passive-interface：不发 Hello，但网段**仍被通告** | 易错概念 |
| ★9 | Stub 家族：LSA 越来越少，**ABR 下发默认路由兜底** | 特殊区域 |
| ★10 | BGP `network` 是把**路由表中已有的路由**放进 BGP | 本质理解 |
| ★11 | PBR 应用在**入接口**，优先级高于路由表 | 应用位置 |
| ★12 | 重分布必须加 `subnets`；双点双向是环路温床 | 防范要点 |

## 板块9 · 网络出口：ACL、NAT 与广域网
> **本板块解决什么问题**：内网配通之后，最后一公里——怎么控制谁能访问谁（ACL）、怎么让私有地址上公网（NAT）、怎么对接运营商专线（广域网）。  
对应 RGSA 考纲：IP 访问控制列表（8%）、NAT、广域网基础；RGSP 考纲：出口策略设计、ACL 应用。

---

### 9_1 ACL 两大类、摆放黄金规则与通配符
#### ACL 的两大类
| 类型 | 编号范围 | 匹配依据 | 典型用途 |
| --- | --- | --- | --- |
| **标准 ACL** | 1-99、1300-1999 | **仅源 IP 地址** | 控制 VTY 登录、NAT 匹配、简单过滤 |
| **扩展 ACL** | 100-199、2000-2699 | 源 IP、目的 IP、协议、端口号 | 精细的业务访问控制（主流） |

#### ★ 摆放位置的黄金规则
**标准 ACL 放在靠近目的地，扩展 ACL 放在靠近源。**

```plain
为什么？
标准 ACL 只看源地址 → 放太靠近源，会把该源去往【所有】目的地的流量都干掉
扩展 ACL 能精确到"源+目的+端口" → 靠近源可以尽早丢包，节省骨干带宽
```

#### ACL 工作原理
```plain
1. 从上到下逐条匹配规则
2. 匹配到第一条符合的规则，立即执行 permit/deny，停止继续匹配
3. 所有规则都不匹配 → 命中末尾隐含的 deny any（全部丢弃）
```

> **★ 末尾隐含 deny any** 是 ACL 最经典的考点，也是现场"配完 ACL 全网断网"事故的头号根源（全库五大致命点之一）。写 ACL 时末尾不加 `permit ip any any`，所有未明确允许的流量都会被丢弃。

#### 通配符掩码（Wildcard Mask）
与子网掩码相反：`0` 表示**必须匹配**，`255` 表示**不关心**。

| 想匹配 | 通配符写法 | 说明 |
| --- | --- | --- |
| 单台主机 192.168.1.1 | `192.168.1.1 0.0.0.0` | 或写 `host 192.168.1.1` |
| 整个网段 192.168.1.0/24 | `192.168.1.0 0.0.0.255` | — |
| 任意地址 | `0.0.0.0 255.255.255.255` | 或写 `any` |
| 奇数地址 192.168.1.1/3/5... | `192.168.1.1 0.0.0.254` | 最后一位不关心最低位 |
| 偶数地址 192.168.1.0/2/4... | `192.168.1.0 0.0.0.254` | 通配最后一位最低位固定为 0 |

---

### 9_2 ACL 配置、应用方向与 SVI 口 in/out 机制
#### 标准 ACL 配置
```bash
! 只允许网管网段（192.168.100.0/24）登录设备
Ruijie(config)# ip access-list standard 10
Ruijie(config-std-nacl)# permit 192.168.100.0 0.0.0.255
Ruijie(config-std-nacl)# deny any
Ruijie(config-std-nacl)# exit
Ruijie(config)# line vty 0 4
Ruijie(config-line)# access-class 10 in
```

#### 扩展 ACL 配置（重点）
```bash
! 场景一：禁止办公网段访问财务服务器(172.16.1.100)的 TCP 445 端口，其余放行
Ruijie(config)# ip access-list extended 100
Ruijie(config-ext-nacl)# deny tcp 192.168.10.0 0.0.0.255 host 172.16.1.100 eq 445
Ruijie(config-ext-nacl)# permit ip any any          ! 关键：末尾放行其余流量
Ruijie(config-ext-nacl)# exit

! 场景二：只允许内网访问 Web 和 DNS，其余拒绝
Ruijie(config)# ip access-list extended 110
Ruijie(config-ext-nacl)# permit tcp 192.168.0.0 0.0.255.255 any eq 80
Ruijie(config-ext-nacl)# permit tcp 192.168.0.0 0.0.255.255 any eq 443
Ruijie(config-ext-nacl)# permit udp 192.168.0.0 0.0.255.255 any eq 53
Ruijie(config-ext-nacl)# deny ip any any
Ruijie(config-ext-nacl)# exit
```

**常用端口关键字**：`eq 80`（www）/ `eq 443`（https）/ `eq 21`（ftp）/ `eq 22`（ssh）/ `eq 23`（telnet）/ `eq 25`（smtp）/ `eq 53`（domain，UDP 为主）/ `eq 3389`（rdp）。

#### 在接口上应用 ACL
```bash
Ruijie(config)# interface vlan 10
Ruijie(config-if-VLAN 10)# ip access-group 100 in      ! in = 进方向
Ruijie(config-if-VLAN 10)# exit
```

**方向判断**：`in` 和 `out` 都以**设备（路由器/三层交换机）为中心**。

```plain
终端 ──[in]──▶ ┌────────┐ ──[out]──▶ 外网
               │  设备   │
               └────────┘
```

#### ★ 锐捷三层交换机 SVI 口的 in/out 机制（RGSP 考点）
三层交换机的 SVI 口是一个**虚拟三层接口**。"in" 方向是指流量**从该 VLAN 内的二层端口进入、经过 SVI 上三层**的方向。

```plain
物理端口 gi0/3 (VLAN 10)
     │
     │  二层交换
     ▼
┌─────────────────┐
│  SVI VLAN 10    │◀── ip access-group 100 in （流量从 VLAN10 进入三层）
└─────────────────┘
```

**易错点**：在三层交换机上控制 VLAN 间访问，ACL 应用在 **SVI 口的 in 方向**（匹配源为 VLAN 内主机）最为直观和常用。

#### ACL 的其他应用
```bash
! 用于 NAT 匹配（定义哪些地址做转换）
Ruijie(config)# ip nat inside source list 1 interface gi0/1 overload

! 用于路由过滤（route-map 中调用）
Ruijie(config-route-map)# match ip address 100

! 用于 VTY 登录限制
Ruijie(config-line)# access-class 10 in

! 用于 QoS 分类
Ruijie(config-class-map)# match access-group 100
```

#### 验证
```bash
Ruijie# show ip access-lists                 ! 查看所有 ACL
Ruijie# show ip access-lists 100             ! 查看指定 ACL（含匹配计数）
Ruijie# show running-config | include access
Ruijie# clear access-list counters           ! 清空计数器
```

> **★ 排障利器**：`show ip access-lists` 会显示每条规则的**匹配次数**。ACL 不生效时看计数器——**不增长**说明流量根本没经过这个 ACL（方向或位置错了），**增长**说明命中的是这条规则。

> **现场故事 · 一条 ACL 放倒全网**  
工程师要在核心上禁止访客网段访问内网，写好 ACL 后应用到 SVI 口，回车——**全网断网**，包括办公网。  
原因：ACL 末尾漏了 `permit ip any any`，隐含的 `deny any` 把所有未匹配流量全丢了。  
应急：Console 进设备，`no ip access-group 100 in` 摘掉 ACL，网络立刻恢复；补上 `permit ip any any` 重新应用。  
**复盘**：**写 ACL 的两条铁律**——第1步末尾必须有明确放行规则；第2步应用前先在非关键接口或用 `show ip access-lists` 计数器确认命中情况。**永远不要在没想清楚"哪些流量会被这条 ACL 拦住"之前就把它挂到生产接口上。**

---

### 9_3 NAT 四种类型与 PAT 出口配置
#### 为什么需要 NAT
IPv4 公网地址枯竭，内网普遍使用私有地址（10/8、172.16/12、192.168/16）。私有地址不能在公网上被路由，所以必须在出口做**地址转换**。

#### 四种 NAT 类型
| 类型 | 特点 | 适用场景 |
| --- | --- | --- |
| **静态 NAT** | 一对一固定映射 | 内网服务器对外发布 |
| **动态 NAT** | 地址池一对一临时映射 | 内网主机数 ≤ 公网地址数 |
| **PAT / NAT Overload** | **多对一，用端口区分** | **最常用**，整网上网 |
| **端口映射（NAT Server）** | 把公网某端口映射到内网服务器 | 对外发布 Web/邮件服务 |

#### PAT（内网共享一个公网 IP 上网）
```plain
        内网                        出口路由器                  公网
   PC1 192.168.10.10:1025  ─┐
   PC2 192.168.10.20:1026  ─┼─▶ [NAT] ─▶ 202.100.1.1:10001
   PC3 192.168.10.30:1027  ─┘         └─▶ 202.100.1.1:10002
                                       └─▶ 202.100.1.1:10003
   通过"IP + 端口号"区分不同内网主机 → 这就是 Overload 的本质
```

```bash
! 1. 定义内网地址范围（用 ACL 匹配）
Ruijie(config)# ip access-list standard 1
Ruijie(config-std-nacl)# permit 192.168.10.0 0.0.0.255
Ruijie(config-std-nacl)# permit 192.168.20.0 0.0.0.255
Ruijie(config-std-nacl)# exit

! 2. 指定内外网接口
Ruijie(config)# interface gi0/0
Ruijie(config-if)# ip address 192.168.10.1 255.255.255.0
Ruijie(config-if)# ip nat inside               ! 内网侧
Ruijie(config-if)# exit
Ruijie(config)# interface gi0/1
Ruijie(config-if)# ip address 202.100.1.1 255.255.255.248
Ruijie(config-if)# ip nat outside              ! 公网侧
Ruijie(config-if)# exit

! 3. 配置 PAT（overload 关键字是关键）
Ruijie(config)# ip nat inside source list 1 interface gi0/1 overload
Ruijie(config)# exit
Ruijie# write
```

> **★ overload 参数的重要性**：若不加 `overload`，执行的是动态一对一 IP 映射，**不会执行端口转换，不能解决公网地址不够的问题**。在网络出口做 NAT 就是为了解决公网地址不足，**必须要加 overload 参数**。

#### 动态 NAT（地址池）
```bash
! 传统写法
Ruijie(config)# ip nat pool POOL1 202.100.1.10 202.100.1.20 netmask 255.255.255.0
Ruijie(config)# ip nat inside source list 1 pool POOL1 overload
```

#### NAT 验证与排障
```bash
Ruijie# show ip nat translations             ! 查看 NAT 转换表（核心命令）
Ruijie# show ip nat statistics               ! NAT 统计
Ruijie# clear ip nat translation *           ! 清空转换表（改配置后必做）
```

| 故障 | 排查方向 |
| --- | --- |
| 内网不能上网 | `ip nat inside/outside` 是否配在正确接口；ACL 是否匹配内网网段 |
| NAT 表无条目 | ACL 没匹配到（检查网段和通配符）；接口方向反了 |
| 只做了一对一映射，多人不能同时上网 | 忘了加 `overload` |
| 部分应用异常（FTP 等） | 应用层含 IP 的协议需要 ALG 支持 |
| 改了配置不生效 | 需 `clear ip nat translation *` 清表 |
| 外网访问不了内网服务器 | 缺静态映射/端口映射；服务器网关没指向路由器 |

---

### 9_4 静态 NAT、端口映射与 permit-inside
#### 静态 NAT（服务器一对一定向发布）
```bash
! 内网 Web 服务器 192.168.10.100 固定映射到公网 202.100.1.5
Ruijie(config)# ip nat inside source static 192.168.10.100 202.100.1.5
```

#### 端口映射（最实用的服务器发布方式）
```bash
! 公网 202.100.1.1 的 TCP 80 端口 → 内网 192.168.10.100 的 80 端口
Ruijie(config)# ip nat inside source static tcp 192.168.10.100 80 202.100.1.1 80

! 公网 3389 远程桌面 → 内网 192.168.10.200 的 3389
Ruijie(config)# ip nat inside source static tcp 192.168.10.200 3389 202.100.1.1 3389

! 端口改号：公网 8080 → 内网 80（规避运营商封 80）
Ruijie(config)# ip nat inside source static tcp 192.168.10.100 80 202.100.1.1 8080
```

#### ★ permit-inside：最容易踩的坑（重要）
**问题场景**：把内网服务器静态映射成公网地址后，**内网 PC 用公网地址访问自己的服务器会不通**。

**原因**：内网 PC 访问公网地址的包到达路由器，路由器做 NAT 转换后把包发回内网服务器；服务器回应时源地址是内网地址，PC 收到一个"源地址不是我请求的地址"的包，直接丢弃——**来回路径不对称**。

```plain
内网 PC ──"访问 202.100.1.5"──▶ 路由器 ──NAT──▶ 内网服务器
   ▲                                              │
   └────── 服务器用内网地址直接回应（源地址不符）────┘
           PC 收到"不是我请求的地址"的包 → 丢弃
```

**解决办法**：在静态映射命令末尾加 `permit-inside` 参数。

```bash
! 静态一对一 + permit-inside
Ruijie(config)# ip nat inside source static 172.16.1.100 192.168.2.168 permit-inside

! 端口映射 + permit-inside
Ruijie(config)# ip nat inside source static tcp 172.16.1.100 23 192.168.2.168 23 permit-inside
```

> **★ 官方建议**：当有内网服务器静态映射成公网地址时，内网 PC 若需要通过该公网地址访问服务器，**必须配置 permit-inside 参数**。  
**在配置静态 NAT 时，建议都配置 permit-inside 参数**——不管当前是否需要，先配上，避免以后加需求时踩坑。这是全库五大致命点之一。

---

### 9_5 多出口策略与 match interface 绑定
#### 问题场景
企业有两条出口（如电信 + 联通），如果地址池没绑定出接口，会出现"**从联通口出去的包带着电信的源地址**"——被运营商直接丢弃。

#### 推荐写法（地址池与出接口绑定）
```bash
Ruijie(config)# ip nat pool nat_ruijie netmask 255.255.255.0
Ruijie(config-ipnat-pool)# address 192.168.2.10 192.168.2.11 match interface GigabitEthernet 0/1
Ruijie(config-ipnat-pool)# address 192.168.3.10 192.168.3.11 match interface GigabitEthernet 0/2
Ruijie(config-ipnat-pool)# exit
Ruijie(config)# ip nat inside source list 10 pool nat_ruijie overload
```

> **★ 多出口必用 **`match interface`：从 Gi0/1 出去的流量自动 NAT 成 192.168.2.x，从 Gi0/2 出去的自动 NAT 成 192.168.3.x。

#### 多出口 + 策略路由组合
PBR 的语法与工作原理见 **板块8_7**，这里只给多出口分流这一特定场景的完整配置。

```plain
办公网段（192.168.10.0/24）→ 走电信出口 Gi0/1，下一跳 192.168.2.1
访客网段（192.168.40.0/24）→ 走联通出口 Gi0/2，下一跳 192.168.3.1
```

```bash
! 1. ACL 匹配源
Ruijie(config)# ip access-list extended OFFICE
Ruijie(config-ext-nacl)# permit ip 192.168.10.0 0.0.0.255 any
Ruijie(config-ext-nacl)# exit
Ruijie(config)# ip access-list extended GUEST
Ruijie(config-ext-nacl)# permit ip 192.168.40.0 0.0.0.255 any
Ruijie(config-ext-nacl)# exit

! 2. route-map 用多个序号分别指定下一跳
Ruijie(config)# route-map MULTI-EXIT permit 10
Ruijie(config-route-map)# match ip address OFFICE
Ruijie(config-route-map)# set ip next-hop 192.168.2.1
Ruijie(config-route-map)# exit
Ruijie(config)# route-map MULTI-EXIT permit 20
Ruijie(config-route-map)# match ip address GUEST
Ruijie(config-route-map)# set ip next-hop 192.168.3.1
Ruijie(config-route-map)# exit

! 3. 应用到内网入接口（PBR 只对入方向生效）
Ruijie(config)# interface gi0/0
Ruijie(config-if)# ip policy route-map MULTI-EXIT
Ruijie(config-if)# exit
```

> **配合要点**：PBR 负责"选路"，`match interface` 地址池负责"选源地址"，两者必须配套——只配 PBR 不配地址池绑定，仍会出现"从联通口出去却带着电信源地址"的情况。

| 故障 | 排查方向 |
| --- | --- |
| 多出口时部分网站打不开 | 地址池未用 `match interface` 绑定出接口 |
| 策略路由不生效 | PBR 是否应用在**入接口**；下一跳是否可达 |
| 主出口故障不切换 | 静态路由未配浮动 AD，或未联动 BFD |

---

### 9_6 广域网基础：PPP、CHAP 与专线
#### 常见广域网链路类型
| 类型 | 特点 | 典型场景 |
| --- | --- | --- |
| **PPP** | 点到点，支持认证和多协议 | 专线、串口链路（RGSA 考点） |
| HDLC | 锐捷默认串口封装 | 专线 |
| 帧中继（Frame Relay） | 已逐步淘汰 | 了解 |
| MSTP 专线 / 光纤直连 | 运营商提供的二层专线 | 企业互联 |

#### PPP 协商三阶段
```plain
1. LCP（链路控制协议）协商
   建立、配置、测试数据链路：MRU、认证协议、魔术字、压缩
        ↓
2. 认证（可选）：PAP 或 CHAP
        ↓
3. NCP（网络控制协议）协商，如 IPCP 协商 IP 地址
        ↓
   链路 UP，可以传数据
```

#### PAP 与 CHAP 对比（必考）
| 对比项 | PAP | CHAP |
| --- | --- | --- |
| 认证方式 | 两次握手 | **三次握手** |
| 密码传输 | **明文** | **不传密码，只传哈希挑战值** |
| 安全性 | 低 | **高（推荐）** |
| 被认证方发起 | 是 | 主认证方发起挑战 |

```plain
CHAP 三次握手：
  主认证方 ──Challenge（随机数+主机名）──▶ 被认证方
  主认证方 ◀──Response（MD5(随机数+密码)）── 被认证方
  主认证方 ──Success / Failure──────────▶ 被认证方
```

#### PPP + CHAP 配置
```bash
! ===== 主认证方（Router A）=====
RouterA(config)# username RouterB password ruijie123     ! 对端用户名密码
RouterA(config)# interface serial 1/2
RouterA(config-if)# encapsulation ppp
RouterA(config-if)# ppp authentication chap
RouterA(config-if)# ip address 10.0.0.1 255.255.255.252
RouterA(config-if)# no shutdown

! ===== 被认证方（Router B）=====
RouterB(config)# username RouterA password ruijie123     ! 两端密码必须相同
RouterB(config)# interface serial 1/2
RouterB(config-if)# encapsulation ppp
RouterB(config-if)# ip address 10.0.0.2 255.255.255.252
RouterB(config-if)# no shutdown
```

> **★ 注意**：CHAP 认证中，两端配置的 `username` 是**对方的设备名**，而 `password` 必须**两端完全相同**。这是最容易搞错的地方。  
单向认证时，被认证方只需配置接口封装与 IP；双向认证时两端都要配 `ppp authentication chap`。

#### PPP 验证与排障
```bash
RouterA# show interfaces serial 1/2          ! 看 LCP/IPCP 是否 Open
RouterA# show ppp all                        ! PPP 会话状态
RouterA# debug ppp authentication            ! 调试认证过程（生产慎用）
```

| 现象 | 排查方向 |
| --- | --- |
| 接口 `up / down` | LCP 已通但 NCP 未通，检查 IP 地址与封装 |
| 接口 `down / down` | 物理层问题：线缆、时钟、DCE/DTE |
| 认证失败反复重协商 | 用户名/密码不匹配；一端配了认证另一端没配 |
| 两端封装不一致 | 一端 PPP 一端 HDLC，改为一致 |

> **现场故事 · 专线起来了但业务不通**  
客户开通一条点到点专线，工程师配完 IP 后 `show ip interface brief` 显示 `up/up`，但两台路由器互相 ping 不通。  
查 `show interfaces serial 1/2` 发现：**一端封装 PPP 并启用了 CHAP，另一端是默认 HDLC**。封装协议不同，链路层无法互通。  
把两端统一成 `encapsulation ppp` 并配好 CHAP 后立刻通了。  
**复盘**：`up/up` 只说明物理层和协议层都"起来了"，**不代表两端协议协商成功**。串口链路的排查顺序是：物理层（线缆/时钟/DCE）→ 封装类型 → 认证参数 → IP 地址。

---

### 9_7 速记卡 · 板块9
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | **标准 ACL 靠近目的，扩展 ACL 靠近源** | 摆放黄金规则 |
| ★2 | ACL 末尾**隐含 deny any**，必须补 `permit ip any any` | 五大致命点之一 |
| ★3 | 通配符：`0` 必须匹配，`255` 不关心 | 与掩码相反 |
| ★4 | SVI 口上控制 VLAN 间访问，用 **in 方向**最直观 | RGSP 考点 |
| ★5 | 计数器**不增长**= 位置/方向错；**增长**= 命中规则 | 排障利器 |
| ★6 | PAT 必须加 `overload`，否则只是一对一映射 | 公网地址不够 |
| ★7 | 静态 NAT 建议**都配 permit-inside**，防内网访问自己服务器不通 | 五大致命点之一 |
| ★8 | 多出口必用 `match interface` 绑定地址池与出接口 | 否则被运营商丢弃 |
| ★9 | PBR 实现多出口分流，应用在**入接口** | 与板块8 呼应 |
| ★10 | CHAP 三次握手不传密码；两端 password 必须相同、username 是对方名 | 易错点 |
| ★11 | 串口 `up/up` 不代表协议协商成功，还要查封装与认证 | 排障顺序 |

## 板块10 · 交换安全与接入控制
> **本板块解决什么问题**：园区网的安全问题大多发生在二层，因为 ARP、DHCP、STP 这些二层协议天生缺乏认证机制——**谁都能说话，且默认相信**。这一板块讲清楚每种威胁用什么技术防，以及各技术之间的依赖关系。  
对应 RGSA 考纲：端口安全（基础）；RGSP 考纲：交换安全技术（端口安全、DHCP Snooping、IP Source Guard、ARP Check、全局地址绑定、AAA、802.1X）。

---

### 10_1 二层威胁全景与两张独立的绑定表
#### 威胁与防护对照
| 威胁 | 攻击手法 | 后果 | 防护手段 |
| --- | --- | --- | --- |
| **MAC 泛洪** | 伪造大量源 MAC 打满 CAM 表 | 交换机退化为 Hub，流量被窃听 | 端口安全 |
| **私接设备** | 用户接 Hub/小交换机 | 环路、越权接入 | 端口安全 + BPDU Guard + RLDP |
| **DHCP 欺骗** | 私接路由器充当 DHCP 服务器 | 下发错误网关，中间人攻击 | DHCP Snooping |
| **IP 地址盗用** | 冒用他人 IP | 地址冲突、权限冒用 | IP Source Guard |
| **ARP 欺骗** | 伪造网关 ARP 应答 | 流量劫持、断网 | ARP Check / 全局地址绑定 |

#### ★ 两张独立的绑定表（关键澄清）
很多资料把这几项技术混为一谈，实际上锐捷的二层安全依赖**两套彼此独立的绑定表**：

```plain
【体系一：DHCP 动态环境】
  ip dhcp snooping
        │ 自动生成动态绑定表（IP + MAC + VLAN + 端口 + 租期）
        ↓
  ip verify source port-security（IP Source Guard）
        └─ 依赖 Snooping 动态绑定表，防 IP 盗用

【体系二：静态 IP 环境】
  address-bind IP MAC          ← 全局静态绑定表
        +
  address-bind uplink 上联口    ← 指定不受检查的端口
        +
  address-bind install         ← 全局启用
        ↓
  接口下 arp-check
        └─ 依赖 address-bind 静态绑定表，防 ARP 欺骗

【可选组合】
  端口安全绑定表（switchport port-security mac-address X ip-address Y）
        ↓
  接口下 arp-check
        └─ 也可作为 arp-check 的数据来源（Policy Source 显示为 port-security）
```

> **★ 这是本板块最重要的一张图**。记住：**IP Source Guard 依赖 DHCP Snooping 表；ARP Check 依赖 address-bind 表或端口安全表**。它们的依赖对象不同，不能混用。

> **现场故事 · 顺序搞反，全网不通**  
工程师想防 ARP 欺骗，直接在接入交换机所有端口上开启了 `arp-check`，却没有配任何绑定表。  
结果：所有终端立刻上不了网。因为 arp-check 需要一张"合法的 IP-MAC 对应表"来校验，没有表就意味着**所有 ARP 报文都不合法**，全部被丢。  
正确做法：先建绑定表（DHCP Snooping 动态表或 address-bind 静态表），**再**在端口上启用检查。  
**复盘**：**所有"校验类"安全特性，都必须先有"校验依据"。** 记住一句话：**先有表，后开检查。**

---

### 10_2 端口安全 Port Security
#### 能做什么
限制端口允许接入的 **MAC 地址数量**，并可把 MAC 与 IP 绑定，防 MAC 泛洪和私接设备。

#### 基础配置
```bash
Ruijie(config)# interface gi0/1
Ruijie(config-if)# switchport port-security          ! 开启端口安全功能
Ruijie(config-if)# exit
```

#### 限制最大安全地址数
```bash
Ruijie(config)# interface gi0/1
Ruijie(config-if)# switchport port-security
Ruijie(config-if)# switchport port-security maximum 1        ! 1-128
Ruijie(config-if)# switchport port-security violation shutdown
Ruijie(config-if)# exit
```

> **注意**：`maximum` 限制的是**动态学习到的安全地址**数量，**手工配置的静态安全地址绑定不受此限制**。  
拼写提醒：标准写法是 `maximum`（取值范围 1-128），不是 `maxmum`。

#### Sticky MAC（自动粘绑）
```bash
Ruijie(config)# interface gi0/1
Ruijie(config-if)# switchport port-security
Ruijie(config-if)# switchport port-security maximum 2
Ruijie(config-if)# switchport port-security mac-address sticky
!  自动把当前学到的 MAC 写入配置，免去手工抄 MAC 的麻烦
```

完整语法（带指定 MAC 和 VLAN）：

```bash
Ruijie(config-if)# switchport port-security mac-address sticky 0021.cccf.6f70 vlan 10
```

#### IP + MAC 地址绑定
```bash
Ruijie(config)# interface gi0/1
Ruijie(config-if)# switchport port-security
Ruijie(config-if)# switchport port-security mac-address 0021.cccf.6f70 ip-address 192.168.10.11
!  MAC 地址用小写，格式为 xxxx.xxxx.xxxx
```

#### 三种违例处理动作
| 动作 | 行为 | 适用场景 |
| --- | --- | --- |
| `protect` | 安全地址数满后，**丢弃**未知源地址的报文，**不告警** | 宽松，静默丢弃 |
| `restrict` | 违例时**丢弃报文并发送 Trap** | 需要告警但不停端口 |
| `shutdown` | 违例时**丢弃报文、关闭接口（err-disable）并发送 Trap** | **最常用**，最严格 |

```bash
Ruijie(config-if)# switchport port-security violation shutdown
!  全局配置自动恢复：
Ruijie(config)# errdisable recovery interval 300
Ruijie(config)# errdisable recovery cause port-security
```

#### 验证
```bash
Ruijie# show port-security                  ! 查看端口安全全局配置
Ruijie# show port-security address          ! 查看安全 MAC 地址绑定表
Ruijie# show port-security interface gi0/1  ! 查看指定端口
Ruijie# show interfaces status              ! 看端口是否被 err-disable
```

`show port-security address` 输出示例：

```plain
Vlan  Mac Address       IP Address      Type        Port   Remaining Age(mins)
----  --------------    --------------- ----------  ------ -------------------
1     00d0.0000.0001    192.168.0.1     Configured  Fa0/1  -
```

#### 端口安全的局限
端口安全是**逐端口**配置的，24 口交换机要配 24 遍。大规模部署更依赖 **DHCP Snooping + IP Source Guard**（动态自动绑定）这套体系。

---

### 10_3 DHCP Snooping：防私接 DHCP 服务器
#### 工作原理
把交换机端口分为两类：

| 端口类型 | 行为 | 配置 |
| --- | --- | --- |
| **Trust（信任）** | 允许转发 DHCP **服务器响应报文**（Offer/Ack） | `ip dhcp snooping trust` |
| **Untrust（非信任）** | **丢弃** DHCP 服务器响应报文，只放行客户端请求 | **默认**，不需配 |

```plain
                    ┌─────────────────┐
   合法 DHCP 服务器 ─┤ Gi0/24 [Trust]  │
   192.168.10.1     │                 │
                    │  接入交换机      │
   私接路由器 ───────┤ Gi0/5 [Untrust] │ ← Offer/Ack 被丢弃
                    └────────┬────────┘
                             │ Gi0/10 [Untrust] ← 只放行 DHCP 请求
                          PC（正常获取合法地址）
```

#### 配置
```bash
! 1. 全局开启 DHCP Snooping
Ruijie(config)# ip dhcp snooping

! 2. 上联口设为信任（连接合法 DHCP 服务器或中继设备的端口）
Ruijie(config)# interface range gi0/1-2
Ruijie(config-if-range)# ip dhcp snooping trust
Ruijie(config-if-range)# exit

! 3. 指定 Snooping 生效的 VLAN
Ruijie(config)# ip dhcp snooping vlan 10,20

! 4.（可选）限制 DHCP 报文速率，防 DHCP 泛洪攻击
Ruijie(config)# interface gi0/5
Ruijie(config-if)# ip dhcp snooping limit rate 10      ! 每秒最多 10 个 DHCP 报文
```

#### 绑定表
DHCP Snooping 会生成一张动态绑定表，记录 **IP + MAC + VLAN + 端口 + 租期**：

```bash
Ruijie# show ip dhcp snooping binding
! MacAddress        IpAddress      Lease(sec)  Type           VLAN  Interface
! 0021.cccf.6f70    192.168.10.11  604800      dhcp-snooping  10    Gi0/10

Ruijie# show ip dhcp snooping                 ! 查看全局配置与状态
Ruijie# clear ip dhcp snooping binding        ! 清除绑定表
```

**★ 这张表是 IP Source Guard 的数据基础。**

> **部署要点**：**上联口一定要配 trust**，否则合法 DHCP 服务器的响应也被丢弃，全网拿不到地址。这是 DHCP Snooping 最常见的配置事故。

---

### 10_4 IP Source Guard：防 IP 盗用
#### 解决的问题
用户手工把 IP 改成别人的（或改成网关地址）→ 地址冲突、越权访问。IP Source Guard 在端口上做源地址校验，不匹配绑定表的一律丢弃。

#### ★ 加不加 port-security 关键字的区别（高频考点）
```bash
Ruijie(config-if-range)# ip verify source port-security
!                                   ↑
```

| 写法 | 检查内容 |
| --- | --- |
| **加 **`port-security` | 检查 **IP 报文的二层源 MAC 地址 + IP 源 IP 地址** |
| **不加 **`port-security` | **只检查二层帧的源 MAC 地址** |

> **★ 要防"私设 IP"，必须加 **`port-security`——不加的话只校验 MAC，改 IP 是拦不住的。

#### 版本差异（重要）
| 软件版本 | 命令 |
| --- | --- |
| **10.3 及以上** | `ip verify source port-security` |
| **10.3 以前** | `ip dhcp snooping address-bind` |
| 另一种写法 | `ip verify source vlan dhcp-snooping ip-mac`（开启源 IP+MAC 检测，将 Snooping 表写入地址绑定库） |

#### 配置（基于 DHCP Snooping）
```bash
! 前提：已启用 DHCP Snooping 并生成绑定表

! 在接终端的端口上启用源校验
Ruijie(config)# interface range gi0/1-23
Ruijie(config-if-range)# ip verify source port-security
Ruijie(config-if-range)# exit
```

#### 静态绑定（静态 IP 终端）
```bash
! 为静态 IP 的打印机手工添加绑定表项
Ruijie(config)# ip source binding 0021.cccf.6f70 vlan 10 192.168.10.200 interface gi0/3
Ruijie(config)# interface gi0/3
Ruijie(config-if)# ip verify source port-security
```

#### 使用注意事项（重要）
| 注意点 | 说明 |
| --- | --- |
| 必须先启用 DHCP Snooping | 否则无绑定表，源校验会导致全部不通 |
| 端口启用后未绑定的流量被丢弃 | 已绑定终端重启后需重新获取地址，或已有静态绑定 |
| 静态 IP 终端必须手工加绑定 | 否则上不了网 |
| **不要在级联交换机端口配置** | 如果交换机下还有级联交换机，**应在接入交换机上部署**，不要配在级联口 |

> **★ 官方部署要点**：如果交换机下还有级联交换机，则不要在级联交换机端口配置 IP Source Guard，而应该在**接入交换机**上部署。

#### 验证
```bash
Ruijie# show ip source binding              ! 查看绑定表（动态 + 静态）
Ruijie# show ip verify source               ! 查看端口源校验状态
```

---

### 10_5 全局地址绑定 + ARP Check：防 ARP 欺骗
#### ARP 欺骗原理
```plain
正常：  PC ──"谁是网关 192.168.10.1？"──▶ 网关应答真实 MAC
攻击：  攻击者 PC ──"我是 192.168.10.1，MAC 是 攻击者MAC"──▶ 广播给全网
结果：  其他 PC 的 ARP 表被污染，流量全部发往攻击者 → 中间人攻击/断网
```

**网关 ARP 欺骗**危害最大：所有出网流量都经过攻击者。

#### 全局 IP+MAC 绑定 + ARP-Check（静态环境方案）
这是锐捷针对**静态 IP 环境**的标准防 ARP 欺骗方案。

```bash
Ruijie> enable
Ruijie# configure terminal

! 1. 全局 IP + MAC 绑定（逐条添加终端与网关）
Ruijie(config)# address-bind 192.168.1.1 0021.cccf.6f70
Ruijie(config)# address-bind 192.168.1.10 0021.cccf.6f71
Ruijie(config)# address-bind 192.168.1.11 0021.cccf.6f72

! 2. 指定上联口（不受检查，避免把网关/上联流量误判）
Ruijie(config)# interface gi0/24
Ruijie(config-if)# address-bind uplink
Ruijie(config-if)# exit

! 3. 全局启用绑定功能
Ruijie(config)# address-bind install

! 4. 在接终端的端口启用 ARP 检查
Ruijie(config)# interface range gi0/1-23
Ruijie(config-if-range)# arp-check
Ruijie(config-if-range)# exit

Ruijie(config)# end
Ruijie# write
```

#### 配置顺序（★ 不能颠倒）
```plain
第1步 address-bind IP MAC      建表（校验依据）
        ↓
第2步 address-bind uplink      放行上联口
        ↓
第3步 address-bind install     全局启用
        ↓
第4步 接口下 arp-check         开启检查
```

> **★ 部署禁忌**：不配 `address-bind uplink` 就把上联口纳入检查，会把网关的 ARP 报文也丢弃，导致全网不通。

#### 与端口安全绑定的组合
静态环境下也可用端口安全绑定表作为 arp-check 的数据源：

```bash
Ruijie(config)# interface gi0/1
Ruijie(config-if)# switchport port-security
Ruijie(config-if)# switchport port-security mac-address 0021.cccf.6f70 ip-address 192.168.10.11
Ruijie(config-if)# arp-check          ! 使用端口安全绑定表做校验
```

此时 `show` 输出中 Policy Source 会显示为 `port-security`。

#### 验证
```bash
Ruijie# show address-bind                    ! 查看全局绑定表
Ruijie# show address-bind statistics         ! 查看绑定统计
Ruijie# show arp-check                       ! 查看 ARP 检查状态
Ruijie# show interfaces status               ! 看是否有端口因违例被关
```

#### 三种 ARP 防护方案选型
| 方案 | 依赖表 | 适用环境 | 配置量 |
| --- | --- | --- | --- |
| **DHCP Snooping + IP Source Guard** | Snooping 动态表 | DHCP 环境 | 小（自动绑定） |
| **address-bind + arp-check** | 全局静态表 | 静态 IP 环境 | 大（逐条录入） |
| **端口安全 + arp-check** | 端口安全表 | 小规模固定终端 | 中（逐端口） |

---

### 10_6 AAA 与 802.1X 准入概览
> **承上启下**：10_2 到 10_5 解决的是「**这个端口上接的设备，它的 MAC / IP 是否合法**」，依据是绑定表，属于**设备级**校验。但在真正需要严管的环境里，问题还要再往前一步：「**这个人是谁、有没有资格接入**」。这就进入了**身份级**准入，靠 AAA 与 802.1X 解决。

#### AAA 三要素
| 要素 | 含义 | 说明 |
| --- | --- | --- |
| **Authentication（认证）** | 你是谁 | 验证身份 |
| **Authorization（授权）** | 你能干什么 | 分配权限/VLAN |
| **Accounting（计费/审计）** | 你干了什么 | 记录行为 |

#### RADIUS 配置
```bash
! 1. 配置 RADIUS 服务器
Ruijie(config)# radius-server host 192.168.100.10 key ruijie123
Ruijie(config)# radius-server timeout 5
Ruijie(config)# radius-server retransmit 3

! 2. 配置 AAA 认证方法列表
Ruijie(config)# aaa new-model
Ruijie(config)# aaa authentication login default group radius local
!                                                        ↑ RADIUS 不可用时用本地认证兜底
Ruijie(config)# aaa authentication dot1x default group radius

! 3. 应用到 VTY
Ruijie(config)# line vty 0 4
Ruijie(config-line)# login authentication default
```

> **★ 兜底很重要**：`group radius local` 中的 `local` 保证 RADIUS 服务器宕机时仍能用本地账号登录设备。漏掉它，一旦服务器故障就连不上设备了。

#### 802.1X 准入
**作用**：终端接入网络前必须通过认证，认证通过后才放行流量。适用于需要严格准入的办公网。

```plain
终端 ──── 接入交换机（认证者）──── RADIUS 服务器
  │            │                        │
  └──EAPoL────▶│◀──── RADIUS ──────────▶│
               │   认证结果（放行/拒绝/下发VLAN）
```

```bash
! 全局开启 802.1X
Ruijie(config)# dot1x authentication default
Ruijie(config)# aaa authentication dot1x default group radius

! 接口下启用
Ruijie(config)# interface gi0/1
Ruijie(config-if)# dot1x port-control auto
Ruijie(config-if)# exit
```

```bash
Ruijie# show dot1x                           ! 查看 802.1X 全局状态
Ruijie# show dot1x interface gi0/1           ! 查看端口认证状态
Ruijie# show dot1x user                      ! 查看已认证用户
```

#### 园区网安全部署推荐组合
```plain
接入交换机标准配置（可整段作为模板）：
  ✓ portfast + bpduguard        （防私接交换机造成环路）
  ✓ rldp loop-detect            （防傻瓜交换机环路）
  ✓ port-security（可选）        （限制接入 MAC 数量）
  ✓ ip dhcp snooping + trust    （防私接 DHCP 服务器）
  ✓ ip verify source port-security（防私改 IP）
  ✓ address-bind + arp-check    （防 ARP 欺骗，静态环境）
  ✓ 上联口不配 arp-check / rldp shutdown
```

---

### 10_7 速记卡 · 板块10
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | **先有绑定表，后开检查**——没有校验依据就开检查 = 全网不通 | 部署第一原则 |
| ★2 | IP Source Guard 依赖 **DHCP Snooping 表** | 体系一 |
| ★3 | ARP Check 依赖 **address-bind 表或端口安全表** | 体系二 |
| ★4 | `ip verify source` **加 port-security 才校验 IP** | 高频考点 |
| ★5 | DHCP Snooping **上联口必须配 trust** | 最常见事故 |
| ★6 | 版本差异：10.3 前用 `ip dhcp snooping address-bind` | 版本提示 |
| ★7 | IP Source Guard 要部署在**接入交换机**，不要配级联口 | 官方要点 |
| ★8 | address-bind 四步：建表 → uplink → install → arp-check | 顺序不可颠倒 |
| ★9 | 端口安全三种动作：protect / restrict / **shutdown（最常用）** | 违例处理 |
| ★10 | AAA 用 `group radius local`，**local 是断网兜底** | 运维保命 |
| ★11 | ARP 表 MAC 跳变 = ARP 欺骗 | 与板块2 呼应 |

## 板块11 · 园区网规划设计与综合实施
> **本板块解决什么问题**：把前面 0-10 板块的技术点串成一个**可交付的完整项目**。重点不在命令，而在**规划决策**和**验收流程**——这是 RGSP 与 RGSA 的真正分水岭。  
对应 RGSP 考纲：网络组网概述和规划设计、典型组网。

---

### 11_1 园区网三层架构与规模对应关系
#### 三层架构
```plain
                    ┌──────────────┐
                    │   出口区      │  路由器 / 防火墙 / 行为管理
                    └──────┬───────┘
                           │
                    ┌──────┴───────┐
                    │    核心层     │  高速转发，双机冗余
                    │  Core Layer  │  VSU / VRRP / 聚合
                    └──┬────────┬──┘
                       │        │
              ┌────────┴───┐  ┌─┴──────────┐
              │   汇聚层    │  │   汇聚层    │  策略控制，VLAN 终结
              │ Aggregation│  │ Aggregation│
              └────────┬───┘  └─┬──────────┘
                       │        │
                ┌──────┴──┐  ┌──┴──────┐
                │  接入层  │  │  接入层  │  终端接入，安全控制
                │  Access │  │  Access │  端口安全/Snooping
                └─────────┘  └─────────┘
```

| 层级 | 核心职责 | 关键设备特性 | 主要技术 |
| --- | --- | --- | --- |
| **核心层** | 高速数据交换，网络骨干 | 高背板带宽、冗余电源、模块化 | VSU、VRRP、链路聚合、OSPF Area 0 |
| **汇聚层** | VLAN 终结、策略控制、广播域边界 | 三层交换机 | SVI、ACL、QoS、路由汇总 |
| **接入层** | 终端接入、安全准入 | 高密度端口、PoE 供电 | VLAN、端口安全、DHCP Snooping、PortFast |

#### 规模与架构的对应
| 规模 | 架构 | 说明 |
| --- | --- | --- |
| 小型（<100 节点，RGSA） | **两层：核心 + 接入** | 核心兼做汇聚，单核心或双核心 |
| 中型（100-500 节点，RGSP） | **三层：核心 + 汇聚 + 接入** | 标准三层，双核心冗余 |
| 大型（>500 节点，RGSE） | **多核心 + 多汇聚 + VXLAN** | 分区分域，虚拟化叠加网络 |

> **★ 这三个数字要记住**：**RGSA 定位 ≤100 节点，RGSP 定位 500 节点级，RGSE 定位大型复杂网络**。它们对应不同的架构复杂度，也决定了考试题目的场景规模。

---

### 11_2 IP 与 VLAN 规划（项目第一步）
**规划决定了后续所有工作的复杂度。这一步偷懒，后面每一步都要还债。**

#### VLAN 规划原则
| 原则 | 说明 |
| --- | --- |
| **按业务/部门划分** | 一个部门或一类业务一个 VLAN，便于管理和策略 |
| **预留扩展空间** | VLAN ID 不要连续占满，留 20%-30% 余量 |
| **管理 VLAN 独立** | 设备网管地址用独立 VLAN（如 VLAN 100），不承载业务 |
| **Native VLAN 独立** | 改成非业务、非 VLAN 1 的 ID（如 999） |
| **VLAN ID 有规律** | 如：10-99 业务、100-199 管理、900-999 特殊用途 |

#### IP 地址规划原则
| 原则 | 说明 |
| --- | --- |
| **连续性** | 同一 VLAN 用连续网段，便于路由汇总 |
| **可汇总性** | 相邻楼宇的网段设计成能用一条汇总路由覆盖 |
| **分层分配** | 按楼宇/楼层分大块，再在块内细分 |
| **预留网关** | 每个网段的第一个或最后一个可用地址作为网关（**全网统一**） |
| **预留服务地址** | 网段前部留给服务器和网络设备 |

#### 规划表模板（项目交付必填）
| VLAN ID | 名称 | 网段 | 网关 | 用途 | 端口范围 |
| --- | --- | --- | --- | --- | --- |
| 10 | OFFICE | 192.168.10.0/24 | 192.168.10.1 | 办公有线 | ACC Gi0/1-16 |
| 20 | CAMERA | 192.168.20.0/24 | 192.168.20.1 | 视频监控 | ACC Gi0/17-24 |
| 30 | WIFI-STA | 192.168.30.0/24 | 192.168.30.1 | 无线员工 | AP |
| 40 | WIFI-GUEST | 192.168.40.0/24 | 192.168.40.1 | 无线访客 | AP |
| 100 | MGMT | 192.168.100.0/24 | 192.168.100.1 | 设备网管 | 所有设备 SVI |
| 999 | NATIVE | 不配 IP | — | Trunk 本征 VLAN | 无业务 |

**链路互联地址**（用 /30 点对点网段，节省地址）：

| 链路 | 网段 | 本端 | 对端 |
| --- | --- | --- | --- |
| CORE1 ↔ 出口 | 10.0.0.0/30 | CORE1 10.0.0.1 | 出口 10.0.0.2 |
| CORE1 ↔ CORE2 | 10.0.0.4/30 | CORE1 10.0.0.5 | CORE2 10.0.0.6 |

#### 规划阶段的五个自问
```plain
第1步 三年后终端规模会翻几倍？地址够不够？VLAN 够不够？
第2步 哪些业务之间必须隔离？隔离点放在汇聚还是核心？
第3步 网关放核心还是汇聚？广播域范围有多大？
第4步 单核心故障时的业务影响面是多少？切换时间能接受吗？
第5步 后期运维从哪个入口查？网管地址怎么规划才不至于冲突？
```

---

### 11_3 技术选型决策树
#### 双核心方案：MSTP+VRRP 还是 VSU？
| 对比项 | MSTP + VRRP | VSU |
| --- | --- | --- |
| 配置复杂度 | **高**（要规划实例、优先级、track） | **低**（一台逻辑设备） |
| 故障切换 | 秒级（依赖 VRRP + STP 收敛） | **毫秒级（50-200ms）** |
| 带宽利用 | 负载分担需精心设计 | **天然全带宽** |
| 是否需 MSTP | 是 | **否**（无环路） |
| 设备要求 | 任意三层交换机 | **必须支持 VSU 的型号** |
| 升级维护 | 可逐台升级，风险低 | 需整体考虑，风险相对高 |

**决策建议**：

```plain
设备支持 VSU 且是新建项目
    → 优先 VSU（简单、快、带宽利用率高）
设备不支持 VSU 或需要平滑升级
    → MSTP + VRRP
极小型网络（<50 节点）
    → 单核心 + 链路聚合即可
```

#### 网关位置：放在核心还是汇聚？
| 方案 | 优点 | 缺点 | 适用 |
| --- | --- | --- | --- |
| **网关在核心** | 集中管理，策略统一 | 广播域跨越汇聚，STP 范围大 | **中小型园区（推荐）** |
| **网关在汇聚** | 广播域被汇聚隔离，故障域小 | 汇聚需三层，管理点分散 | 大型园区 |

#### 路由协议选型
| 规模 | 建议 |
| --- | --- |
| 小型（<10 台三层设备） | 静态路由 + 浮动路由 即可 |
| 中型（RGSP） | **OSPF 多区域**，核心与出口跑 Area 0 |
| 大型（RGSE） | OSPF + BGP + MPLS VPN |

#### 出口方案选型
```plain
单出口         → 默认路由 + PAT
双出口（主备）  → 浮动静态路由 + BFD 联动
双出口（负载）  → PBR 分流 + match interface 地址池
有公网服务器    → 静态 NAT / 端口映射 + permit-inside
```

---

### 11_4 综合实施：中型园区网完整配置
#### 项目需求
+ 一栋 5 层办公楼，约 300 个信息点
+ 双核心冗余，核心之间链路聚合
+ 4 个业务 VLAN（办公、监控、无线员工、无线访客）+ 管理 VLAN
+ 网关冗余：VLAN 10/30 主走 CORE1，VLAN 20/40 主走 CORE2
+ 出口单线路，做 PAT
+ 接入层启用完整安全特性

#### 拓扑
```plain
                        ┌────────┐
                        │  出口   │ RSR / 防火墙
                        └───┬────┘
                     10.0.0.0/30
                            │
        ┌───────────────────┴───────────────────┐
        │                                       │
   ┌────┴─────┐                           ┌─────┴────┐
   │  CORE1   │◀═════ AP1(聚合,Trunk) ═════▶│  CORE2   │
   │ 1.1.1.1  │                            │ 2.2.2.2  │
   └────┬─────┘                           └─────┬────┘
        │  Gi0/1-2 (Trunk)                     │ Gi0/1-2 (Trunk)
        └──────────────┬──────────────────────┘
                       │
                 ┌─────┴─────┐
                 │  AGG-1    │ 汇聚
                 └─────┬─────┘
                       │ Gi0/3-6 (Trunk)
        ┌──────────────┼──────────────┐
   ┌────┴─────┐  ┌─────┴────┐   ┌─────┴────┐
   │ ACC-1F   │  │ ACC-3F   │   │ ACC-5F   │ 接入
   └──────────┘  └──────────┘   └──────────┘
```

#### 规划表
| 项目 | 值 |
| --- | --- |
| MSTP 域名 / revision | ruijie / 1 |
| 实例 1 | VLAN 10, 30 → 根桥 CORE1（prio 4096） |
| 实例 2 | VLAN 20, 40 → 根桥 CORE2（prio 4096） |
| VRRP 组 10/30 | Master = CORE1（prio 120） |
| VRRP 组 20/40 | Master = CORE2（prio 120） |
| OSPF | Area 0（核心+出口），Area 10（楼栋 VLAN） |
| 聚合 | CORE1↔CORE2 用 AP1（LACP active） |

> **★ 注意**：MSTP 实例根桥与 VRRP Master 必须在同一台设备，否则流量绕行（详见板块7）。

> **与板块7 的分工**：板块7 用"VLAN 10 + VLAN 20"的最小双 VLAN 场景讲清 MSTP+VRRP 的**原理、track 取值与 BFD 联动**，并逐步解释每一条命令为什么这么写；本板块则是**完整项目落地**——4 个业务 VLAN + 1 个管理 VLAN、增加了汇聚层、引入 OSPF 多区域与 Trunk Native VLAN 改造，配置一次给全、可直接作为交付脚本使用。**原理性说明请回看板块7，此处不再重复。**

#### CORE1 完整配置
```bash
Ruijie> enable
Ruijie# configure terminal
Ruijie(config)# hostname CORE1
CORE1(config)# no logging console

! ========== VLAN ==========
CORE1(config)# vlan range 10,20,30,40,100
CORE1(config-vlan-range)# exit
CORE1(config)# vlan 10
CORE1(config-vlan)# name OFFICE
CORE1(config-vlan)# vlan 20
CORE1(config-vlan)# name CAMERA
CORE1(config-vlan)# vlan 30
CORE1(config-vlan)# name WIFI-STA
CORE1(config-vlan)# vlan 40
CORE1(config-vlan)# name WIFI-GUEST
CORE1(config-vlan)# vlan 100
CORE1(config-vlan)# name MGMT
CORE1(config-vlan)# exit

! ========== 三层功能 ==========
CORE1(config)# ip routing

! ========== 出口互联（三层口）==========
CORE1(config)# interface gi0/24
CORE1(config-if-GigabitEthernet 0/24)# no switchport
CORE1(config-if-GigabitEthernet 0/24)# ip address 10.0.0.1 255.255.255.252
CORE1(config-if-GigabitEthernet 0/24)# description To-Internet
CORE1(config-if-GigabitEthernet 0/24)# exit

! ========== 核心互联聚合 ==========
CORE1(config)# interface aggregateport 1
CORE1(config-if-AggregatePort-1)# switchport mode trunk
CORE1(config-if-AggregatePort-1)# switchport trunk allowed vlan only 10,20,30,40,100
CORE1(config-if-AggregatePort-1)# description To-CORE2
CORE1(config-if-AggregatePort-1)# exit
CORE1(config)# interface range gi0/22-23
CORE1(config-if-range)# port-group 1 mode active
CORE1(config-if-range)# exit

! ========== 下联汇聚 Trunk ==========
CORE1(config)# interface range gi0/1-2
CORE1(config-if-range)# switchport mode trunk
CORE1(config-if-range)# switchport trunk allowed vlan only 10,20,30,40,100
CORE1(config-if-range)# switchport trunk native vlan 999
CORE1(config-if-range)# description To-AGG
CORE1(config-if-range)# exit

! ========== SVI + VRRP ==========
CORE1(config)# interface vlan 10
CORE1(config-if-VLAN 10)# ip address 192.168.10.2 255.255.255.0
CORE1(config-if-VLAN 10)# vrrp 10 ip 192.168.10.1
CORE1(config-if-VLAN 10)# vrrp 10 priority 120
CORE1(config-if-VLAN 10)# vrrp 10 track gi0/24 30
CORE1(config-if-VLAN 10)# exit

CORE1(config)# interface vlan 20
CORE1(config-if-VLAN 20)# ip address 192.168.20.2 255.255.255.0
CORE1(config-if-VLAN 20)# vrrp 20 ip 192.168.20.1
CORE1(config-if-VLAN 20)# exit

CORE1(config)# interface vlan 30
CORE1(config-if-VLAN 30)# ip address 192.168.30.2 255.255.255.0
CORE1(config-if-VLAN 30)# vrrp 30 ip 192.168.30.1
CORE1(config-if-VLAN 30)# vrrp 30 priority 120
CORE1(config-if-VLAN 30)# vrrp 30 track gi0/24 30
CORE1(config-if-VLAN 30)# exit

CORE1(config)# interface vlan 40
CORE1(config-if-VLAN 40)# ip address 192.168.40.2 255.255.255.0
CORE1(config-if-VLAN 40)# vrrp 40 ip 192.168.40.1
CORE1(config-if-VLAN 40)# exit

CORE1(config)# interface vlan 100
CORE1(config-if-VLAN 100)# ip address 192.168.100.2 255.255.255.0
CORE1(config-if-VLAN 100)# exit

! ========== MSTP ==========
CORE1(config)# spanning-tree
CORE1(config)# spanning-tree mst configuration
CORE1(config-mst)# name ruijie
CORE1(config-mst)# revision 1
CORE1(config-mst)# instance 1 vlan 10,30
CORE1(config-mst)# instance 2 vlan 20,40
CORE1(config-mst)# spanning-tree mst 1 priority 4096
CORE1(config-mst)# spanning-tree mst 2 priority 8192
CORE1(config-mst)# exit

! ========== OSPF ==========
CORE1(config)# router ospf 1
CORE1(config-router)# router-id 1.1.1.1
CORE1(config-router)# network 10.0.0.0 0.0.0.3 area 0
CORE1(config-router)# network 192.168.10.0 0.0.0.255 area 10
CORE1(config-router)# network 192.168.20.0 0.0.0.255 area 10
CORE1(config-router)# network 192.168.30.0 0.0.0.255 area 10
CORE1(config-router)# network 192.168.40.0 0.0.0.255 area 10
CORE1(config-router)# network 192.168.100.0 0.0.0.255 area 0
CORE1(config-router)# passive-interface vlan 10
CORE1(config-router)# passive-interface vlan 20
CORE1(config-router)# passive-interface vlan 30
CORE1(config-router)# passive-interface vlan 40
CORE1(config-router)# exit

! ========== 管理 ==========
CORE1(config)# enable service ssh-server
CORE1(config)# ip ssh version 2
CORE1(config)# crypto key generate rsa
CORE1(config)# username admin privilege 15 password Admin@123
CORE1(config)# line vty 0 4
CORE1(config-line)# login local
CORE1(config-line)# transport input ssh
CORE1(config-line)# exit
CORE1(config)# end
CORE1# write
```

#### CORE2 完整配置（对称部分）
```bash
Ruijie(config)# hostname CORE2
CORE2(config)# no logging console
CORE2(config)# vlan range 10,20,30,40,100,999
CORE2(config-vlan-range)# exit
CORE2(config)# ip routing

! 出口互联
CORE2(config)# interface gi0/24
CORE2(config-if-GigabitEthernet 0/24)# no switchport
CORE2(config-if-GigabitEthernet 0/24)# ip address 10.0.0.5 255.255.255.252
CORE2(config-if-GigabitEthernet 0/24)# description To-Internet-Backup
CORE2(config-if-GigabitEthernet 0/24)# exit

! 核心互联聚合（与 CORE1 对称）
CORE2(config)# interface aggregateport 1
CORE2(config-if-AggregatePort-1)# switchport mode trunk
CORE2(config-if-AggregatePort-1)# switchport trunk allowed vlan only 10,20,30,40,100
CORE2(config-if-AggregatePort-1)# exit
CORE2(config)# interface range gi0/22-23
CORE2(config-if-range)# port-group 1 mode active
CORE2(config-if-range)# exit

! 下联汇聚 Trunk
CORE2(config)# interface range gi0/1-2
CORE2(config-if-range)# switchport mode trunk
CORE2(config-if-range)# switchport trunk allowed vlan only 10,20,30,40,100
CORE2(config-if-range)# switchport trunk native vlan 999
CORE2(config-if-range)# exit

! SVI + VRRP（与 CORE1 相反：VLAN 20/40 为 Master）
CORE2(config)# interface vlan 10
CORE2(config-if-VLAN 10)# ip address 192.168.10.3 255.255.255.0
CORE2(config-if-VLAN 10)# vrrp 10 ip 192.168.10.1
CORE2(config-if-VLAN 10)# exit
CORE2(config)# interface vlan 20
CORE2(config-if-VLAN 20)# ip address 192.168.20.3 255.255.255.0
CORE2(config-if-VLAN 20)# vrrp 20 ip 192.168.20.1
CORE2(config-if-VLAN 20)# vrrp 20 priority 120
CORE2(config-if-VLAN 20)# vrrp 20 track gi0/24 30
CORE2(config-if-VLAN 20)# exit
CORE2(config)# interface vlan 30
CORE2(config-if-VLAN 30)# ip address 192.168.30.3 255.255.255.0
CORE2(config-if-VLAN 30)# vrrp 30 ip 192.168.30.1
CORE2(config-if-VLAN 30)# exit
CORE2(config)# interface vlan 40
CORE2(config-if-VLAN 40)# ip address 192.168.40.3 255.255.255.0
CORE2(config-if-VLAN 40)# vrrp 40 ip 192.168.40.1
CORE2(config-if-VLAN 40)# vrrp 40 priority 120
CORE2(config-if-VLAN 40)# vrrp 40 track gi0/24 30
CORE2(config-if-VLAN 40)# exit
CORE2(config)# interface vlan 100
CORE2(config-if-VLAN 100)# ip address 192.168.100.3 255.255.255.0
CORE2(config-if-VLAN 100)# exit

! MSTP（与 CORE1 相反）
CORE2(config)# spanning-tree
CORE2(config)# spanning-tree mst configuration
CORE2(config-mst)# name ruijie
CORE2(config-mst)# revision 1
CORE2(config-mst)# instance 1 vlan 10,30
CORE2(config-mst)# instance 2 vlan 20,40
CORE2(config-mst)# spanning-tree mst 1 priority 8192
CORE2(config-mst)# spanning-tree mst 2 priority 4096
CORE2(config-mst)# exit

! OSPF
CORE2(config)# router ospf 1
CORE2(config-router)# router-id 2.2.2.2
CORE2(config-router)# network 192.168.10.0 0.0.0.255 area 10
CORE2(config-router)# network 192.168.20.0 0.0.0.255 area 10
CORE2(config-router)# network 192.168.30.0 0.0.0.255 area 10
CORE2(config-router)# network 192.168.40.0 0.0.0.255 area 10
CORE2(config-router)# network 192.168.100.0 0.0.0.255 area 0
CORE2(config-router)# passive-interface vlan 10
CORE2(config-router)# passive-interface vlan 20
CORE2(config-router)# passive-interface vlan 30
CORE2(config-router)# passive-interface vlan 40
CORE2(config-router)# exit
CORE2(config)# end
CORE2# write
```

#### 接入交换机配置模板（可批量套用）
```bash
Ruijie(config)# hostname ACC-3F
ACC-3F(config)# vlan range 10,20,30,40,100,999
ACC-3F(config-vlan-range)# exit

! ---- 上联口 Trunk ----
ACC-3F(config)# interface range gi0/25-26
ACC-3F(config-if-range)# switchport mode trunk
ACC-3F(config-if-range)# switchport trunk allowed vlan only 10,20,30,40,100
ACC-3F(config-if-range)# switchport trunk native vlan 999
ACC-3F(config-if-range)# description Uplink-to-CORE
ACC-3F(config-if-range)# exit

! ---- 终端口：办公 VLAN 10 ----
ACC-3F(config)# interface range gi0/1-16
ACC-3F(config-if-range)# switchport mode access
ACC-3F(config-if-range)# switchport access vlan 10
ACC-3F(config-if-range)# description PC-Office
ACC-3F(config-if-range)# exit

! ---- 终端口：监控 VLAN 20 ----
ACC-3F(config)# interface range gi0/17-24
ACC-3F(config-if-range)# switchport mode access
ACC-3F(config-if-range)# switchport access vlan 20
ACC-3F(config-if-range)# description Camera
ACC-3F(config-if-range)# exit

! ---- 生成树优化（接终端口）----
ACC-3F(config)# spanning-tree
ACC-3F(config)# spanning-tree mst configuration
ACC-3F(config-mst)# name ruijie
ACC-3F(config-mst)# revision 1
ACC-3F(config-mst)# instance 1 vlan 10,30
ACC-3F(config-mst)# instance 2 vlan 20,40
ACC-3F(config-mst)# exit
ACC-3F(config)# spanning-tree portfast bpduguard default
ACC-3F(config)# interface range gi0/1-24
ACC-3F(config-if-range)# spanning-tree portfast
ACC-3F(config-if-range)# exit

! ---- 环路检测 ----
ACC-3F(config)# rldp enable
ACC-3F(config)# interface range gi0/1-24
ACC-3F(config-if-range)# rldp port loop-detect shutdown-port
ACC-3F(config-if-range)# exit
ACC-3F(config)# errdisable recovery interval 300

! ---- 安全特性 ----
ACC-3F(config)# ip dhcp snooping
ACC-3F(config)# ip dhcp snooping vlan 10,20,30,40
ACC-3F(config)# interface range gi0/25-26
ACC-3F(config-if-range)# ip dhcp snooping trust
ACC-3F(config-if-range)# exit
ACC-3F(config)# interface range gi0/1-24
ACC-3F(config-if-range)# ip verify source port-security
ACC-3F(config-if-range)# exit

! ---- 管理 ----
ACC-3F(config)# interface vlan 100
ACC-3F(config-if-VLAN 100)# ip address 192.168.100.10 255.255.255.0
ACC-3F(config-if-VLAN 100)# exit
ACC-3F(config)# ip default-gateway 192.168.100.1
ACC-3F(config)# enable service ssh-server
ACC-3F(config)# crypto key generate rsa
ACC-3F(config)# username admin privilege 15 password Admin@123
ACC-3F(config)# line vty 0 4
ACC-3F(config-line)# login local
ACC-3F(config-line)# transport input ssh
ACC-3F(config-line)# exit
ACC-3F(config)# end
ACC-3F# write
```

> **★ 部署要点回顾**：
> + 接入交换机作为二层设备，用 `ip default-gateway` 而非路由协议
> + **上联口配 trust**（DHCP Snooping），**上联口不配 rldp shutdown / arp-check**
> + `spanning-tree portfast bpduguard default` 全局开启，新增端口自动生效

---

### 11_5 验收清单（交付必跑）
#### 分层验收表
| 层次 | 验收项 | 命令 | 通过标准 |
| --- | --- | --- | --- |
| **物理层** | 端口状态 | `show ip interface brief` | 规划端口全部 up/up |
| **物理层** | 错误计数 | `show interfaces counters` | CRC 不持续增长 |
| **二层** | VLAN 划分 | `show vlan` | 端口归属与规划表一致 |
| **二层** | Trunk 放通 | `show interfaces trunk` | allowed 列表与规划一致 |
| **二层** | MAC 学习 | `show mac address-table` | 各 VLAN 能学到终端 MAC |
| **破环** | 生成树角色 | `show spanning-tree mst 1/2` | 根桥与规划一致 |
| **破环** | 边缘端口 | `show spanning-tree interface` | 终端口为 edge/forwarding |
| **冗余** | 聚合状态 | `show aggregateport 1 summary` | 成员口全部 Selected |
| **冗余** | VRRP 角色 | `show vrrp brief` | 主备与规划一致，无双 Master |
| **三层** | VLAN 间互通 | `ping` | 按策略该通的通该隔离的不通 |
| **三层** | 路由学习 | `show ip route ospf` | 路由条目完整无缺失 |
| **出口** | NAT 转换 | `show ip nat translations` | 内网地址能转成公网地址 |
| **出口** | 外网可达 | `ping 公网地址` | 通 |
| **安全** | 绑定表 | `show ip dhcp snooping binding` | 终端绑定正常生成 |
| **管理** | 远程登录 | SSH 登录 | 网管网段可登录、其他网段拒绝 |

#### 高可用性验收（必须做，不能只看配置）
```plain
□ 拔掉主用上联线     → VRRP 切换，业务中断 < 数秒
□ 关闭主核心         → 备用核心接管，全网业务恢复
□ 断开聚合一条成员链路 → 业务不中断，带宽下降但不断网
□ 断开核心互联       → 检查是否出现双 Master（VSU 场景检查双主机检测）
□ 恢复主用设备       → 抢占回主（确认抢占是否符合预期）
□ 模拟非直连故障     → BFD 联动能否触发切换（最容易漏的一项）
```

#### 交付文档清单
```plain
□ IP / VLAN 规划表
□ 网络拓扑图（含物理连接与逻辑连接）
□ 设备配置文本（每台一份，含版本信息）
□ 验收测试报告（含每条验收项的实际输出）
□ 割接方案与回退预案
□ 运维手册（常用命令、故障处理流程、联系人）
```

---

### 11_6 割接方案、回退预案与变更窗口
#### 割接前准备
```plain
第1步 备份现有配置      copy running-config tftp: （每台都要）
第2步 确认回退方案      明确"什么情况触发回退""回退需要几分钟"
第3步 准备配置脚本      提前写好，不要现场现敲
第4步 确认变更窗口      业务低峰期，提前通知用户
第5步 准备应急联系方式  运营商、设备厂商、客户接口人
第6步 检查备件          光模块、网线、Console 线
```

#### 割接执行顺序（先易后难、先边缘后核心）
```plain
1. 接入交换机   → 逐台刷配置，逐台验证
2. 汇聚层       → 配置并验证 VLAN 终结与路由
3. 核心层       → 最后改，改完立即验证 VRRP/聚合/路由
4. 出口         → 最后切换，切换后立即测外网
```

#### 回退触发条件（提前约定，现场不纠结）
| 触发条件 | 动作 |
| --- | --- |
| 割接后核心业务中断超过约定时长 | 立即回退 |
| 出现无法在 30 分钟内定位的故障 | 立即回退 |
| 出现双 Master / 路由环路等扩散性故障 | 立即回退 |
| 客户临时要求中止 | 中止并保持现状（或按预案回退） |

> **★ 割接铁律**：**回退时间必须比排查时间更短。** 如果回退需要 1 小时而排查可能只要 10 分钟，那这个回退方案就是无效的。割接前一定要实际演练一次回退动作。

> **现场故事 · 没有回退方案的通宵**  
某园区网核心割接，团队准备充分，配置脚本反复检查过。割接开始后一切顺利，直到凌晨一点发现：某业务系统的服务器网段与新规划冲突，该业务中断。  
团队决定排查，但旧配置已经在刷入新配置时被覆盖，**没有完整备份**。最后靠一台备机的旧配置文本手工恢复，折腾到早上六点。  
**复盘**：**备份和回退不是"有就行"，而是要"演练过"。** 割接清单上最该打勾的两项是：第1步每台设备的配置已备份到独立存储；第2步回退步骤实际演练过一次且记录了耗时。

---

### 11_7 速记卡 · 板块11
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | 三个数字：RGSA ≤100 节点、RGSP 500 节点级、RGSE 大型复杂 | 规模对应 |
| ★2 | 规划偷懒，后面每一步都要还债 | 项目第一步 |
| ★3 | VLAN：按业务划分、管理独立、Native 独立（如 999）、留 20-30% 余量 | 规划原则 |
| ★4 | 网关统一用网段第一个或最后一个可用地址，**全网一致** | 避免混乱 |
| ★5 | 新建 + 设备支持 → **VSU**；平滑升级 → **MSTP+VRRP** | 选型决策 |
| ★6 | 网关在核心适合中小型，在汇聚适合大型（故障域小） | 网关位置 |
| ★7 | **MSTP 根桥 = VRRP Master** 同一台设备 | 防流量绕行 |
| ★8 | 接入交换机用 `ip default-gateway`，上联口配 trust、不配 rldp shutdown | 部署要点 |
| ★9 | 验收必须做**高可用演练**，尤其是非直连故障的 BFD 切换 | 验收红线 |
| ★10 | 割接铁律：**回退时间要比排查时间短，且必须演练过** | 变更管理 |
| ★11 | 割接顺序：接入 → 汇聚 → 核心 → 出口（先边缘后核心） | 执行顺序 |

## 板块12 · WLAN 基础与锐捷无线组网
> **本板块解决什么问题**：把有线网络延伸成无线覆盖，讲清楚 802.11 的核心机制、胖瘦 AP 两种架构的配置，以及信道规划与网优的实操方法。  
对应 RGSA 考纲：无线基础、胖瘦 AP 组网（**WLAN 占 RGSA 权重最高，约 14%**）；RGSP 考纲：WLAN 原理与部署、WLAN 安全技术、典型组网和无线网优。

---

### 12_1 为什么 WLAN 在 RGSA 中权重最高
很多人备考只练路由交换，结果在 WLAN 上丢分最多。RGSA 考纲中 **WLAN 占 14%**，高于静态路由（12%）、VLAN（10%）、OSPF（10%）。

```plain
RGSA 权重分布（部分）
  WLAN        ██████████████  14%   ← 最高，却最容易被忽略
  静态路由     ████████████    12%
  VLAN        ██████████      10%
  OSPF        ██████████      10%
  网络分层模型 ████████        8%
  NAT         ████████        8%
```

而且从工程角度看：**没有无线的园区网交付是不完整的**。客户验收时第一个问的往往是"WiFi 怎么连"，而不是"OSPF 几个区域"。

> **结论**：板块12 必须完整过一遍，这是整个 RGSA 备考中性价比最高的一块。

---

### 12_2 WLAN 基础概念与 802.11 标准演进
#### 核心术语
| 术语 | 英文 | 说明 |
| --- | --- | --- |
| **AP** | Access Point | 无线接入点，把有线信号转成无线 |
| **AC** | Access Controller | 无线控制器，集中管理大量 AP |
| **STA** | Station | 无线终端（手机、笔记本） |
| **SSID** | Service Set Identifier | 无线网络名称（手机搜到的 WiFi 名） |
| **BSSID** | Basic SSID | AP 的 MAC 地址，标识一个 BSS |
| **BSS** | Basic Service Set | 一个 AP 覆盖的范围 |
| **ESS** | Extended Service Set | 多个 BSS 用同一 SSID 组成的扩展网络（漫游基础） |
| **信道** | Channel | 2.4G 有 1-13（互不重叠只有 1/6/11） |

#### 802.11 协议标准演进
| 标准 | 频段 | 最大速率 | 特点 |
| --- | --- | --- | --- |
| 802.11a | 5G | 54 Mbps | 早期，已淘汰 |
| 802.11b | 2.4G | 11 Mbps | 早期 |
| 802.11g | 2.4G | 54 Mbps | 兼容 b |
| **802.11n** | 2.4G/5G | 600 Mbps | 引入 **MIMO**、40MHz 信道绑定 |
| **802.11ac** | 5G | 6.9 Gbps | Wave1/Wave2，MU-MIMO |
| **802.11ax（Wi-Fi 6）** | 2.4G/5G | 9.6 Gbps | **OFDMA**，高密度场景 |

#### 关键概念关系图
```plain
   一个 AP 的覆盖范围 = 一个 BSS（用 BSSID = AP 的 MAC 标识）
        │
        │  多个 AP 使用同一个 SSID
        ▼
   组成 ESS → 终端在 ESS 内移动 = 漫游
```

---

### 12_3 2.4G/5G 对比与 CSMA/CA
#### 2.4G 与 5G 对比
| 对比项 | 2.4G | 5G |
| --- | --- | --- |
| 频率范围 | 2.4-2.4835 GHz | 5.15-5.85 GHz |
| 可用非重叠信道 | **仅 3 个（1/6/11）** | 20+ 个 |
| 穿墙能力 | **强**（波长长） | 弱 |
| 干扰 | **严重**（蓝牙、微波炉、邻居 WiFi） | 少 |
| 速率 | 低 | 高 |
| 适用 | 远距离、低速率 | 高密度、高速率 |

> **★ 必考点**：2.4G 互不重叠信道只有 **1、6、11**（每信道 20MHz，中心频率间隔 25MHz）。信道规划是无线网优的第一件事。

```plain
2.4G 信道分布（每信道 20MHz 宽，中心间隔 5MHz）
  信道 1  ──── 2412MHz
  信道 6  ──── 2437MHz   ← 与 1 相隔 25MHz，互不重叠
  信道 11 ──── 2462MHz   ← 与 6 相隔 25MHz，互不重叠
```

#### CSMA/CA（无线为什么不能像有线那样"先听后说"）
| 对比 | CSMA/CD（有线） | CSMA/CA（无线） |
| --- | --- | --- |
| 冲突处理 | 边发边检测，冲突后重发 | **无法检测冲突**（收发不能同时），只能提前避免 |
| 机制 | 直接发送，冲突检测 | **先发 RTS/CTS 预约信道，再发送数据** |
| 原因 | 有线可以边发边收 | 无线收发同频，发送时听不到别人 |

**简单理解**：无线环境下"自己说话时听不见别人"，所以只能在说话前先"举手申请"（RTS/CTS），得到允许再发。

```plain
CSMA/CA 流程：
  发送方 ──RTS(Request To Send)──▶ 接收方
  发送方 ◀──CTS(Clear To Send)──── 接收方
  发送方 ──────数据──────────────▶ 接收方
  发送方 ◀─────ACK─────────────── 接收方
```

#### 隐藏节点问题
```plain
   AP
   ↑        ↑
  STA-A   STA-B      （A 和 B 距离远，互相听不到，但都能连 AP）

A 在发数据时听不到 B，B 也听不到 A → 两者同时发 → 在 AP 处冲突
解决：RTS/CTS 预约机制，让 AP 统一协调
```

---

### 12_4 胖 AP（FAT AP）配置实战
#### 场景
一台胖 AP，SSID 为 `Ruijie-Office`，密码 `Office@123`，AP 自身做 DHCP 给终端。

```plain
        ┌──────────────┐
        │   互联网/上级  │
        └──────┬───────┘
               │ 网线
        ┌──────┴───────┐
        │   FAT AP     │ 192.168.1.1/24（自身 LAN 口）
        │  SSID: Office│ 自带 DHCP：192.168.1.100-200
        └──────┬───────┘
               │ 无线
         手机/笔记本
```

#### 基础配置
```bash
Ruijie> enable
Ruijie# configure terminal
Ruijie(config)# hostname FAT-AP-01

! 配置 WLAN（无线服务集）
FAT-AP-01(config)# dot11 wlan 1
FAT-AP-01(dot11-wlan-config)# ssid Ruijie-Office
FAT-AP-01(dot11-wlan-config)# vlan 10
FAT-AP-01(dot11-wlan-config)# exit

! 配置射频口（2.4G 通常为 dot11radio 1/0，5G 为 2/0，以实际型号为准）
FAT-AP-01(config)# interface dot11radio 1/0
FAT-AP-01(config-if)# channel 6                       ! 指定信道（1/6/11 选一）
FAT-AP-01(config-if)# power local 100                 ! 发射功率百分比
FAT-AP-01(config-if)# wlan-id 1                       ! 绑定 wlan 1
FAT-AP-01(config-if)# no shutdown
FAT-AP-01(config-if)# exit

! 安全：WPA2-PSK
FAT-AP-01(config)# wlansec 1
FAT-AP-01(wlansec)# security rsn enable
FAT-AP-01(wlansec)# security rsn ciphers aes enable
FAT-AP-01(wlansec)# security rsn akm psk enable
FAT-AP-01(wlansec)# security rsn akm psk set-key ascii Office@123
FAT-AP-01(wlansec)# exit

! DHCP 服务
FAT-AP-01(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.99
FAT-AP-01(config)# ip dhcp pool STA
FAT-AP-01(dhcp-config)# network 192.168.1.0 255.255.255.0
FAT-AP-01(dhcp-config)# default-router 192.168.1.1
FAT-AP-01(dhcp-config)# dns-server 114.114.114.114
FAT-AP-01(dhcp-config)# exit

! 管理地址
FAT-AP-01(config)# interface bvi 1
FAT-AP-01(config-if)# ip address 192.168.1.1 255.255.255.0
FAT-AP-01(config-if)# exit
FAT-AP-01(config)# end
FAT-AP-01# write
```

#### 验证
```bash
FAT-AP-01# show dot11 wlan 1               ! 查看 WLAN 配置
FAT-AP-01# show dot11 radio 1/0            ! 查看射频状态
FAT-AP-01# show dot11 associations all-client  ! 查看已关联的终端
FAT-AP-01# show ip dhcp binding            ! 查看终端获取的 IP
```

---

### 12_5 瘦 AP + AC 组网与 CAPWAP（RGSP 核心）
#### 两种组网架构
```plain
【胖 AP（FAT AP）】                    【瘦 AP（FIT AP）+ AC】
┌─────────┐                          ┌──────────┐
│  FAT AP │ 独立工作                  │   AC     │ 集中控制
│ 自带配置│ ← 逐台配置                 └────┬─────┘
│ 自带转发│                                │ CAPWAP 隧道
└────┬────┘                          ┌─────┼─────┐
     │ 直接转有线                     ┌──┴──┐ ┌──┴──┐ ┌──┴──┐
     ▼                              │FIT AP│ │FIT AP│ │FIT AP│
                                    └──────┘ └──────┘ └──────┘
    小型（几台 AP）                       中大型（几十到上千台）
```

| 对比项 | 胖 AP（FAT） | 瘦 AP（FIT）+ AC |
| --- | --- | --- |
| 管理方式 | 逐台独立配置 | **AC 集中管理，配置自动下发** |
| 漫游 | 支持差 | **支持，无缝漫游** |
| 规模 | 几台（家庭/小门店） | **几十到上千台** |
| 成本 | AP 单价低 | AC 有额外成本 |
| 功能 | 自带路由/NAT/DHCP | 纯接入，功能由 AC 提供 |
| 典型场景 | 家庭、SOHO、小型分支 | **企业园区、高校、医院（主流）** |

> **★ RGSA 要求两种都会配；RGSP 重点考瘦 AP + AC 架构。**

#### CAPWAP 协议
AC 与 AP 之间通过 **CAPWAP**（Control And Provisioning of Wireless Access Points）隧道通信：

| 端口 | 用途 |
| --- | --- |
| **UDP 5246** | **控制隧道**（管理报文，AC 下发配置给 AP） |
| **UDP 5247** | **数据隧道**（用户数据，取决于转发模式） |

#### 两种数据转发方式
```plain
【集中转发（隧道转发）】                【本地转发（直接转发）】
STA → AP →[CAPWAP 隧道]→ AC → 网络     STA → AP → 交换机 → 网络
                                             （AP 直接把数据丢到有线）
       数据要经过 AC                       数据不过 AC
```

| 对比项 | 集中转发 | 本地转发 |
| --- | --- | --- |
| 数据路径 | 经 AC 转发 | AP 本地直接转发 |
| AC 压力 | **大**（所有流量都过 AC） | 小 |
| 策略控制 | 集中，易管控 | 需交换机配合 |
| 适用 | 小中型、需要集中安全策略 | **大型园区（推荐）** |

```bash
! 在 wlan-config 下配置本地转发
Ruijie(config)# wlan-config 1 RuiYi-1
Ruijie(config-wlan)# tunnel local          ! 配置转发方式为本地转发
Ruijie(config-wlan)# exit
```

#### AP 上线流程
```plain
1. AP 加电，通过 DHCP 获取 IP（需在 DHCP 中下发 option 138 告知 AC 地址）
        ↓
2. AP 发 Discovery 请求，寻找 AC
        ↓
3. AC 回应 Discovery Response
        ↓
4. 建立 CAPWAP 控制隧道（UDP 5246）
        ↓
5. AP 从 AC 下载配置（版本、SSID、信道、功率）
        ↓
6. AP 进入 Run 状态，开始提供服务
```

#### DHCP Option 138（AP 发现 AC 的关键）
```bash
! 在 DHCP 服务器（通常是核心交换机）上配置
CORE(config)# ip dhcp pool AP-POOL
CORE(dhcp-config)# network 192.168.200.0 255.255.255.0
CORE(dhcp-config)# default-router 192.168.200.1
CORE(dhcp-config)# option 138 ip 192.168.100.10      ! AC 的管理 IP
CORE(dhcp-config)# exit
```

> **★ 排障要点**：AP 拿不到地址或找不到 AC，八成是 **option 138 没配或配错**。这是瘦 AP 上线失败最常见的原因。

#### AC 完整配置（多 SSID 二层组网）
```bash
Ruijie> enable
Ruijie# configure terminal
Ruijie(config)# hostname AC

! ========== 1. 创建 WLAN（SSID）==========
! ★ 注意：wlan-config 语法直接带 SSID 名，不需要再单独写 ssid 命令
AC(config)# wlan-config 1 RuiYi-Office
AC(config-wlan)# exit
AC(config)# wlan-config 2 RuiYi-Guest
AC(config-wlan)# exit

! ========== 2. 创建 AP 组并绑定 WLAN ==========
AC(config)# ap-group default
AC(config-ap-group)# interface-mapping 1 10        ! wlan 1 映射到 VLAN 10
AC(config-ap-group)# interface-mapping 2 40        ! wlan 2 映射到 VLAN 40
AC(config-ap-group)# exit

! interface-mapping 完整语法（含 ap-wlan-id）：
!   interface-mapping {wlan-id} {vlan-id} [ap-wlan-id {id}]

! ========== 3. 配置安全策略 ==========
AC(config)# wlansec 1
AC(config-wlansec)# security rsn enable
AC(config-wlansec)# security rsn ciphers aes enable
AC(config-wlansec)# security rsn akm psk enable
AC(config-wlansec)# security rsn akm psk set-key ascii Office@123
AC(config-wlansec)# exit

AC(config)# wlansec 2
AC(config-wlansec)# security rsn enable
AC(config-wlansec)# security rsn ciphers aes enable
AC(config-wlansec)# security rsn akm psk enable
AC(config-wlansec)# security rsn akm psk set-key ascii Guest@123
AC(config-wlansec)# exit

! ========== 4. 关联 AP ==========
AC(config)# ap-config all                     ! 对所有 AP 生效
AC(config-ap)# ap-group default               ! 默认关联规则
AC(config-ap)# exit

! 也可按单台 AP 配置（用 AP 名称或 MAC）
AC(config)# ap-config AP-3F-01
AC(config-ap)# ap-group default
AC(config-ap)# exit

! ========== 5. AC 管理地址与路由 ==========
AC(config)# interface vlan 100
AC(config-if-VLAN 100)# ip address 192.168.100.10 255.255.255.0
AC(config-if-VLAN 100)# exit
AC(config)# ip route 0.0.0.0 0.0.0.0 192.168.100.1

AC(config)# end
AC# write
```

#### 无线验证命令
```bash
AC# show ap-config summary              ! 查看 AP 上线情况（★ 第一查）
AC# show ap-config detail               ! AP 详细信息（版本、IP、状态）
AC# show wlan-config                    ! 查看已配置的 SSID
AC# show station summary                ! 查看在线终端
AC# show ac-config                      ! 查看 AC 配置
AC# show capwap state                   ! 查看 CAPWAP 隧道状态
```

#### AP 上线失败排查清单
| 现象 | 排查方向 |
| --- | --- |
| AP 拿不到 IP | DHCP 地址池是否够；AP 所在 VLAN 是否放通 |
| AP 有 IP 但找不到 AC | **option 138 是否配置**；AC 地址是否正确 |
| 控制隧道建不起来 | UDP 5246 是否被 ACL 阻断；AC 与 AP 之间路由是否可达 |
| AP 反复重启 | AC 与 AP 版本不匹配；供电不足（PoE 功率） |
| AP 上线但无信号 | 是否绑定了 wlan-config；射频口是否 no shutdown |

---

### 12_6 WLAN 安全：认证与加密
> **承上启下**：到 12_5 为止，AP 能上线、SSID 能搜到终端能拿到地址——无线网络「能用了」。但无线信号是**开放介质**，任何人在覆盖范围内都能收到数据帧，因此「谁能连、连上来之后数据有没有被加密」必须单独解决。

#### 安全协议演进
| 协议 | 加密 | 认证 | 安全性 | 现状 |
| --- | --- | --- | --- | --- |
| **WEP** | RC4 | 共享密钥 | **极低，几分钟可破解** | 已淘汰，禁止使用 |
| **WPA** | TKIP | PSK / 802.1X | 中（TKIP 已被攻破） | 兼容老设备时用 |
| **WPA2** | **AES-CCMP** | PSK / 802.1X | **高（当前主流）** | **推荐** |
| **WPA3** | AES-GCMP | SAE | 最高 | 新设备逐步支持 |

#### 两种认证方式
| 方式 | 说明 | 适用 |
| --- | --- | --- |
| **PSK（预共享密钥）** | 所有人共用一个密码 | 家庭、小办公、访客网络 |
| **802.1X（企业级）** | 每人独立账号，需 RADIUS 服务器 | 企业办公网（推荐） |

#### WPA2-PSK 配置（个人级）
```bash
AC(config)# wlansec 1
AC(config-wlansec)# security rsn enable
AC(config-wlansec)# security rsn ciphers aes enable
AC(config-wlansec)# security rsn akm psk enable
AC(config-wlansec)# security rsn akm psk set-key ascii Office@123
AC(config-wlansec)# exit
```

#### WPA2-802.1X 配置（企业级）
```bash
! 1. 配置 RADIUS 服务器
AC(config)# radius-server host 192.168.100.20 key ruijie123

! 2. 配置 WLAN 使用 802.1X
AC(config)# wlansec 1
AC(config-wlansec)# security rsn enable
AC(config-wlansec)# security rsn ciphers aes enable
AC(config-wlansec)# security rsn akm 802.1x enable
AC(config-wlansec)# exit
```

#### 其他安全措施
```bash
! 隐藏 SSID（不广播）
AC(config-wlan)# ssid-hide

! 终端隔离（同一 AP 下终端不能互访，常用于访客网络）
AC(config-wlan)# user-isolation

! 限制单 AP 接入终端数
AC(config-wlan)# sta-limit 30

! 启用无线入侵检测（WIDS），检测非法 AP
AC(config)# wids enable
```

#### 访客网络设计建议
```plain
访客 SSID 设计要点：
  ✓ 独立 VLAN（如 VLAN 40），与内网隔离
  ✓ 独立网段与 DHCP 池
  ✓ 开启 user-isolation（终端隔离）
  ✓ 在核心/出口用 ACL 限制只能访问外网
  ✓ 可考虑限速（QoS）
```

---

### 12_7 无线网优：信道、功率与漫游
#### 网优三步法
```plain
第一步：信道规划    相邻 AP 用非重叠信道（2.4G 只用 1/6/11）
        ↓
第二步：功率调整    降低功率，缩小蜂窝，减少同频干扰
        ↓
第三步：漫游优化    调整漫游阈值，保证移动中业务不中断
```

#### 信道规划（最重要的一步）
```plain
2.4G 蜂窝式覆盖（三信道复用）
       [AP1]           [AP2]           [AP3]
        ch1             ch6             ch11
         │               │               │
    ┌────┴────┐     ┌────┴────┐     ┌────┴────┐
    │  覆盖区  │     │  覆盖区  │     │  覆盖区  │
    └────┬────┘     └────┬────┘     └────┬────┘
        [AP4]           [AP5]           [AP6]
        ch1             ch6             ch11
```

> **★ 关键原则**：**相邻且信号有重叠的 AP 必须使用不同信道**；同一信道之间要有足够的物理隔离（或降低功率）。

```bash
! 手工指定信道（网优常用）
AC(config)# ap-config AP-3F-01
AC(config-ap)# radio 1
AC(config-ap-radio)# channel 6
AC(config-ap-radio)# power local 50           ! 功率降到 50%
AC(config-ap-radio)# exit

! 自动信道与功率（小中型网络可用）
AC(config)# ap-config all
AC(config-ap)# radio 1
AC(config-ap-radio)# channel auto
AC(config-ap-radio)# power auto
```

#### 功率调整的原则
| 场景 | 功率策略 |
| --- | --- |
| 高密度部署（会议室、教室） | **降低功率**，缩小蜂窝，提高信道复用率 |
| 大范围覆盖（仓库、厂房） | 提高功率，保证边缘信号强度 |
| 多层楼 | 降低功率，减少楼层间干扰 |

> **反直觉但重要**：**AP 功率不是越大越好。** 功率过大导致蜂窝覆盖重叠严重、同频干扰加剧，反而降低整体容量。高密度场景下"小功率多 AP"优于"大功率少 AP"。

#### 漫游优化
```plain
漫游阈值建议：
  信号强度低于 -70dBm 时触发漫游（太晚会导致卡顿）
  邻 AP 信号强于当前 AP 5-10dB 时切换（避免频繁切换/乒乓漫游）
```

```bash
! 配置漫游相关参数（不同版本命令略有差异）
AC(config)# ap-config all
AC(config-ap)# radio 1
AC(config-ap-radio)# rssi-threshold 25
AC(config-ap-radio)# exit
```

#### 常见无线问题排查
| 现象 | 可能原因 | 排查方向 |
| --- | --- | --- |
| 信号满格但网速慢 | 同频干扰、终端过多 | 查信道规划、查单 AP 终端数 |
| 某些位置信号差 | 覆盖盲区、功率不足 | 现场勘测，补 AP 或调功率 |
| 移动中掉线 | 漫游阈值不合理 | 调低 rssi-threshold |
| 能连上但拿不到 IP | DHCP 池耗尽、VLAN 错 | 查地址池、查 interface-mapping |
| 频繁掉线重连 | 信道干扰、供电不稳 | 查 PoE 供电、换信道 |
| 2.4G 慢但 5G 快 | 2.4G 干扰严重 | 引导终端使用 5G（可开双频合一） |

> **现场故事 · 会议室里的"满格却很卡"**  
客户反映大会议室无线"信号满格但视频会议卡顿"。工程师现场测速，确实只有几百 Kbps。  
排查发现：这层楼有 8 个 AP，**全部使用信道 6**，而且功率都是 100%。开会时几十人同时连入，8 个 AP 互相干扰，谁都发不出去。  
整改：改为 1/6/11 三信道错开，功率统一降到 40%，蜂窝缩小、干扰隔离。整改后实测单终端速率提升近 5 倍。  
**复盘**：**无线网优第一件事永远是信道规划，第二件是降功率。** "信号满格"只代表收到了强信号，不代表信道干净——这是无线与有线最不同的地方。

---

### 12_8 速记卡 · 板块12
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | **WLAN 占 RGSA 权重 14%，最高**且最容易丢分 | 性价比之王 |
| ★2 | 2.4G 非重叠信道只有 **1、6、11** | 必考点 |
| ★3 | 5G 信道多、速率高但**穿墙弱**；2.4G 反之 | 频段对比 |
| ★4 | CSMA/CA 用 **RTS/CTS 预约**，因为无线收发不能同时 | 与 CSMA/CD 区分 |
| ★5 | 胖 AP 独立配置；瘦 AP + AC 集中管理、**支持漫游** | 架构对比 |
| ★6 | CAPWAP：**UDP 5246 控制隧道、5247 数据隧道** | 端口号 |
| ★7 | AP 发现 AC 靠 **DHCP option 138** | 上线失败首查 |
| ★8 | `wlan-config 1 名称` **直接带 SSID 名** | 语法易错 |
| ★9 | 本地转发 `tunnel local`（大型园区推荐），集中转发数据过 AC | 转发模式 |
| ★10 | 安全用 **WPA2-AES**，禁用 WEP | 安全底线 |
| ★11 | 网优三步：**信道规划 → 降功率 → 漫游调优** | 实操顺序 |
| ★12 | 功率不是越大越好，高密度要"**小功率多 AP**" | 反直觉要点 |

## 板块13 · IPv6 与组播技术
> **本板块解决什么问题**：IPv4 地址枯竭后的地址体系（IPv6）与"一份数据发给多个接收者"的高效传输方式（组播）。两者都是 RGSP 的加分项、RGSE 的必修项。  
对应 RGSP 考纲：IPv6、组播技术原理；RGSE：IPv6 技术原理和应用组播技术原理和应用。

---

### 13_1 为什么需要 IPv6
| 驱动因素 | 说明 |
| --- | --- |
| **地址枯竭** | IPv4 仅约 43 亿地址，已分配殆尽 |
| **NAT 的副作用** | NAT 破坏了端到端模型，P2P、VoIP 等应用复杂化 |
| **物联网** | 海量设备需要海量地址 |
| **性能** | IPv6 报头简化，转发效率更高 |

#### IPv6 的三大改进
| 改进 | 说明 |
| --- | --- |
| **地址空间** | 128 位，约 3.4×10^38 个地址 |
| **简化报头** | 固定 40 字节，去掉校验和，取消分片（由端系统处理） |
| **无状态自动配置** | SLAAC，设备插上网线就能自己生成地址 |

```plain
IPv4 报头 vs IPv6 报头
IPv4：变长（20-60 字节），含校验和分片字段，路由器要做校验与分片
IPv6：固定 40 字节，无校验和（交给上层），分片由端系统用扩展头处理
      → 路由器处理更简单，转发效率更高
```

---

### 13_2 IPv6 地址格式、简写规则与地址类型
#### 书写规则
```plain
完整形式：2001:0DB8:0000:0000:0001:0000:0000:0001
         共 8 段，每段 4 个十六进制字符，用冒号分隔

规则一：前导 0 可省略
2001:DB8:0:0:1:0:0:1

规则二：连续的 0 段可用 :: 代替（★ 只能用一次）
2001:DB8::1:0:0:1    或    2001:DB8:0:0:1::1

最简形式：2001:DB8::1
```

> **★ **`::`** 在一个地址中只能出现一次**——否则无法还原出唯一地址。这是考试常考点。

#### 地址前缀表示
```plain
2001:DB8:1234::/48     类似 IPv4 的 192.168.1.0/24
/64 是最常见的前缀长度（一个子网）
```

#### 地址类型
| 类型 | 前缀 | 说明 | 对应 IPv4 |
| --- | --- | --- | --- |
| **全球单播地址** | 2000::/3 | 公网地址，全球唯一 | 公网 IP |
| **链路本地地址** | FE80::/10 | **每个接口自动生成**，只在链路内有效 | 169.254.x.x |
| **唯一本地地址（ULA）** | FC00::/7 | 私网地址 | 私有地址 |
| **组播地址** | FF00::/8 | 一对多 | 组播 |
| **任播地址** | — | 一对最近 | 无 |
| 环回地址 | ::1/128 | 本机 | 127.0.0.1 |
| 未指定地址 | ::/128 | 类似 0.0.0.0 | 0.0.0.0 |

> **★ IPv6 没有广播地址**，广播的功能由组播替代。这是 IPv6 的重要特性，也是常考对比点。

#### 关键单播地址细分
| 地址 | 作用 |
| --- | --- |
| `FE80::/10` | 链路本地，用于邻居发现、路由协议（**OSPFv3/ISIS 用此建邻居**） |
| `2001::/16` | Teredo（IPv6 隧道过渡技术） |
| `2002::/16` | 6to4 隧道 |
| `FC00::/7 ~ FDFF::/7` | 唯一本地地址（ULA），相当于私网 |

#### 常用组播地址（必记）
| 地址 | 含义 | 对应 IPv4 |
| --- | --- | --- |
| `FF02::1` | 链路内所有节点 | 广播 |
| `FF02::2` | 链路内所有路由器 | — |
| `FF02::5` | OSPFv3 所有路由器 | 224.0.0.5 |
| `FF02::6` | OSPFv3 DR/BDR | 224.0.0.6 |
| `FF02::1:FFXX:XXXX` | 请求节点组播地址（替代 ARP 广播） | — |

---

### 13_3 地址配置方式：手工、EUI-64、SLAAC、DHCPv6
#### 手工配置
```bash
Ruijie(config)# ipv6 unicast-routing              ! 开启 IPv6 单播路由（必需！）
Ruijie(config)# interface gi0/1
Ruijie(config-if)# ipv6 enable                    ! 启用 IPv6（自动生成链路本地地址）
Ruijie(config-if)# ipv6 address 2001:DB8:1::1/64
Ruijie(config-if)# no shutdown
Ruijie(config-if)# exit
```

> **★ **`ipv6 unicast-routing`** 是最容易被忘的一步**——类似于 IPv4 的 `ip routing`。不开的话，IPv6 地址配了也转发不了。

#### EUI-64 方式（根据 MAC 自动生成接口 ID）
```bash
Ruijie(config-if)# ipv6 address 2001:DB8:1::/64 eui-64
```

**EUI-64 生成规则**：把 48 位 MAC 从中间插入 `FFFE`，并把第 7 位（U/L 位）取反。

```plain
MAC:      00:21:CC:CF:6F:70
插入 FFFE: 0021:CCFF:FECF:6F70
第7位取反: 0221:CCFF:FECF:6F70
           （首字节 00000000 → 00000010 = 02H）
接口 ID:  221:CCFF:FECF:6F70
完整地址: 2001:DB8:1::221:CCFF:FECF:6F70/64
```

#### SLAAC（无状态自动配置）
设备通过接收路由器发出的 **RA（Router Advertisement）** 报文，自动获取前缀 + 自己生成接口 ID。

```bash
! 路由器侧：开启 RA 通告
Ruijie(config)# interface gi0/1
Ruijie(config-if)# ipv6 address 2001:DB8:1::1/64
Ruijie(config-if)# no ipv6 nd suppress-ra         ! 允许发送 RA（默认可能抑制）
Ruijie(config-if)# exit
```

#### DHCPv6（有状态）
```bash
! 服务端
Ruijie(config)# ipv6 dhcp pool POOL6
Ruijie(config-dhcpv6)# address prefix 2001:DB8:1::/64
Ruijie(config-dhcpv6)# dns-server 2001:4860:4860::8888
Ruijie(config-dhcpv6)# exit
Ruijie(config)# interface vlan 10
Ruijie(config-if)# ipv6 dhcp server POOL6
```

#### SLAAC 与 DHCPv6 对比
| 方式 | 分配内容 | 有无状态 | 适用 |
| --- | --- | --- | --- |
| **SLAAC** | 只给前缀，接口 ID 自己生成 | 无状态 | 简单网络，不需管理 |
| **DHCPv6** | 给完整地址 + DNS 等 | 有状态 | 需要精细管理、审计 |

#### 验证
```bash
Ruijie# show ipv6 interface brief              ! IPv6 接口摘要
Ruijie# show ipv6 interface gi0/1              ! 接口详情（含链路本地地址）
Ruijie# show ipv6 route                        ! IPv6 路由表
Ruijie# show ipv6 neighbors                    ! IPv6 邻居表（相当于 ARP 表）
Ruijie# ping ipv6 2001:DB8:1::2                ! IPv6 ping
Ruijie# show ipv6 routers                      ! 查看 RA 信息
```

> **★ 排障要点**：`show ipv6 neighbors` 在 IPv6 中的作用等同于 IPv4 的 `show arp`。IPv6 用**邻居发现协议（NDP）**替代了 ARP。

---

### 13_4 IPv6 路由：静态、OSPFv3、RIPng、MP-BGP
#### 静态路由
```bash
! 指定下一跳
Ruijie(config)# ipv6 route 2001:DB8:2::/64 2001:DB8:1::2
! 指定出接口 + 下一跳
Ruijie(config)# ipv6 route 2001:DB8:2::/64 gi0/1 2001:DB8:1::2
! 默认路由
Ruijie(config)# ipv6 route ::/0 2001:DB8:1::2
```

#### OSPFv3（IPv6 的 OSPF）
**与 OSPFv2 的关键差异（必考）**：

| 对比项 | OSPFv2（IPv4） | OSPFv3（IPv6） |
| --- | --- | --- |
| 认证 | 协议内认证 | **依赖 IPv6 扩展头（IPsec）** |
| 邻居建立 | 用接口 IP | **用链路本地地址（FE80::）** |
| network 命令 | 在进程下 network | **在接口下直接启用** |
| Router ID | 32 位 | 仍是 32 位（**需手工配置**，因为 IPv6 地址是 128 位） |

```bash
Ruijie(config)# ipv6 unicast-routing
Ruijie(config)# ipv6 router ospf 1
Ruijie(config-router)# router-id 1.1.1.1            ! 必须手工指定
Ruijie(config-router)# exit
Ruijie(config)# interface gi0/1
Ruijie(config-if)# ipv6 enable
Ruijie(config-if)# ipv6 address 2001:DB8:1::1/64
Ruijie(config-if)# ipv6 ospf 1 area 0               ! 在接口下启用
Ruijie(config-if)# exit

Ruijie# show ipv6 ospf neighbor
Ruijie# show ipv6 route ospf
```

#### RIPng（IPv6 的 RIP）
```bash
Ruijie(config)# ipv6 router rip RIPNG1
Ruijie(config-router)# exit
Ruijie(config)# interface gi0/1
Ruijie(config-if)# ipv6 rip RIPNG1 enable
```

#### MP-BGP for IPv6
```bash
Ruijie(config)# router bgp 65001
Ruijie(config-router)# neighbor 2001:DB8:1::2 remote-as 65002
Ruijie(config-router)# address-family ipv6 unicast
Ruijie(config-router-af)# neighbor 2001:DB8:1::2 activate
Ruijie(config-router-af)# network 2001:DB8:100::/48
Ruijie(config-router-af)# exit
```

> **★ 注意**：IPv6 的 BGP 需要在 `address-family ipv6 unicast` 地址族下 **activate** 邻居，默认不激活。

---

### 13_5 IPv6 过渡技术：双栈、隧道、NAT64
IPv4 到 IPv6 不可能一刀切，需要过渡技术：

| 技术 | 类型 | 说明 |
| --- | --- | --- |
| **双栈（Dual Stack）** | 共存 | 设备同时跑 IPv4 和 IPv6，**最主流、最推荐** |
| **6to4 隧道** | 隧道 | 把 IPv6 包封装在 IPv4 中传输，前缀 `2002::/16` |
| **ISATAP** | 隧道 | 站内自动隧道寻址 |
| **NAT64** | 翻译 | IPv6 网络访问 IPv4 资源 |
| **DS-Lite** | 翻译 | 运营商级过渡方案 |

#### 双栈配置（最常用）
```bash
Ruijie(config)# ip routing                       ! 开启 IPv4 路由
Ruijie(config)# ipv6 unicast-routing             ! 开启 IPv6 路由
Ruijie(config)# interface vlan 10
Ruijie(config-if)# ip address 192.168.10.1 255.255.255.0
Ruijie(config-if)# ipv6 address 2001:DB8:10::1/64
Ruijie(config-if)# exit
```

```plain
双栈终端的行为：
  同时拥有 IPv4 和 IPv6 地址
  访问 IPv4 资源走 IPv4，访问 IPv6 资源走 IPv6
  ★ 双栈不是"二选一"，而是"两条路都在，按需选择"
```

#### 手动隧道（IPv6 over IPv4）
```bash
Ruijie(config)# interface tunnel 0
Ruijie(config-if)# ipv6 address 2001:DB8:FE::1/64
Ruijie(config-if)# tunnel source 10.0.0.1
Ruijie(config-if)# tunnel destination 10.0.0.2
Ruijie(config-if)# tunnel mode ipv6ip
Ruijie(config-if)# exit
```

#### 过渡技术选型
```plain
新建网络、改造彻底        → 纯双栈（最优）
需要与 IPv4 老系统长期共存 → 双栈 + NAT64
IPv6 孤岛跨 IPv4 网络互联  → 隧道（6to4 / 手动隧道）
```

---

### 13_6 组播：IGMP、IGMP Snooping 与 PIM-SM
#### 为什么需要组播
| 方式 | 场景 | 问题 |
| --- | --- | --- |
| **单播** | 100 个用户看视频 | 服务器发 100 份相同数据，带宽浪费 100 倍 |
| **广播** | 发给所有人 | 不需要的人也被迫接收，浪费且不安全 |
| **组播** | 只发给加入组的成员 | **一份数据，按需复制，带宽只占一份** |

```plain
单播：服务器 ──▶ 用户1、用户2、用户3 ……直到用户N（共 N 份拷贝，N 个用户就是 N 倍带宽）
广播：服务器 ──▶ 所有主机（不管对方要不要，且通常止步于三层）
组播：服务器 ──▶ 组播组地址 ──▶ 只复制给加入了该组的成员（每条链路上只有 1 份数据）
```

#### 组播地址
| 范围 | 说明 |
| --- | --- |
| `224.0.0.0 - 224.0.0.255` | **保留的链路本地组播**（路由协议用，TTL=1，不转发） |
| `224.0.1.0 - 238.255.255.255` | 用户可用的组播地址 |
| `239.0.0.0 - 239.255.255.255` | **管理范围（私有）组播地址**，类似私有 IP |

常见保留地址：

| 地址 | 用途 |
| --- | --- |
| 224.0.0.1 | 所有主机 |
| 224.0.0.2 | 所有路由器 |
| 224.0.0.5 | OSPF 路由器 |
| 224.0.0.6 | OSPF DR/BDR |
| 224.0.0.9 | RIPv2 |
| 224.0.0.18 | VRRP |

#### IGMP（主机与路由器之间）
**作用**：主机通过 IGMP 告诉路由器"我要加入/离开某个组播组"。

| 版本 | 特点 |
| --- | --- |
| **IGMPv1** | 只有成员报告与查询，离开靠超时（延迟大） |
| **IGMPv2** | **增加离开报文（Leave）**，离开更及时（最常用） |
| **IGMPv3** | **支持指定源（SSM）**，可指定只接收某个源的组播 |

```bash
! 在连接组播接收者的接口上启用
Ruijie(config)# interface vlan 10
Ruijie(config-if)# ip igmp enable
Ruijie(config-if)# ip igmp version 2
Ruijie(config-if)# exit
```

#### IGMP Snooping（交换机上的二层优化）
**解决的问题**：交换机缺省把组播当作广播处理，会向 VLAN 内**所有端口**泛洪，浪费带宽。

**原理**：交换机监听 IGMP 报文，建立"组播组 → 端口"的转发表，**只把组播流量发给真正有接收者的端口**。

```plain
未开 Snooping：                    开启 Snooping：
  组播源                              组播源
    │                                   │
  ┌──┴──┐                            ┌──┴──┐
  │交换机 │                           │交换机 │
  └─┬┬┬┬┬┘                           └─┬┬┬┬┬┘
   │││││ 全部泛洪                      │││││ 只发给加入了组的端口
  A B C D E                          A B C D E
                                      ✓   ✓ （只有 A、C 加入了组）
```

```bash
! 全局开启 IGMP Snooping
Ruijie(config)# ip igmp snooping
! 指定 VLAN 生效
Ruijie(config)# ip igmp snooping vlan 10
! 配置连接组播路由器的端口（避免被误剪枝）
Ruijie(config)# interface gi0/24
Ruijie(config-if)# ip igmp snooping mrouter
```

```bash
Ruijie# show ip igmp snooping                  ! 查看全局配置
Ruijie# show ip igmp snooping groups           ! 查看组播组与成员端口
Ruijie# show ip igmp snooping mrouter          ! 查看组播路由器端口
```

#### PIM-SM（组播路由协议，三层）
**PIM 两种模式**：

| 模式 | 全称 | 特点 | 适用 |
| --- | --- | --- | --- |
| **PIM-DM** | Dense Mode | 先泛洪再剪枝（推模型） | 小型、接收者密集 |
| **PIM-SM** | Sparse Mode | **按需建立分发树**（拉模型） | **大中型网络（主流）** |

**PIM-SM 核心概念**：

| 概念 | 说明 |
| --- | --- |
| **RP（Rendezvous Point）** | 汇聚点，组播源的注册中心和接收者的汇合点 |
| **RPT（共享树）** | 以 RP 为根的树，初始使用 |
| **SPT（最短路径树）** | 以源为根的树，优化后切换（避免绕行 RP） |
| **DR** | 指定路由器，负责向 RP 注册或转发 |

```plain
PIM-SM 工作流程（简化）：
  第1步 接收者向 DR 发 IGMP 加入
  第2步 DR 向 RP 方向发送 (*, G) Join，建立 RPT
  第3步 组播源向 RP 注册（Register）
  第4步 数据沿 RPT 从 RP 流向接收者
  第5步 流量超过阈值后，接收者侧 DR 切换到 SPT（绕开 RP，走最短路径）
```

#### PIM-SM 配置
```bash
! 1. 全局开启组播路由
Ruijie(config)# ip multicast-routing

! 2. 在参与组播的接口上启用 PIM-SM
Ruijie(config)# interface vlan 10
Ruijie(config-if)# ip pim sparse-mode
Ruijie(config-if)# exit
Ruijie(config)# interface gi0/24
Ruijie(config-if)# ip pim sparse-mode
Ruijie(config-if)# exit

! 3. 配置 RP（静态方式，也可用 BSR 动态选举）
Ruijie(config)# ip pim rp-address 10.0.0.100
!  所有 PIM 路由器上的 RP 地址必须一致
```

#### 组播验证
```bash
Ruijie# show ip igmp groups                ! 查看加入的组播组
Ruijie# show ip igmp interface vlan 10     ! 接口 IGMP 状态
Ruijie# show ip pim neighbor               ! PIM 邻居
Ruijie# show ip pim rp                     ! 查看 RP 信息（★ 必查）
Ruijie# show ip mroute                     ! 组播路由表
Ruijie# show ip mfib                       ! 组播转发表
```

#### 组播排障清单
| 现象 | 排查方向 |
| --- | --- |
| 接收者收不到组播 | IGMP 是否启用；`show ip igmp groups` 有无成员 |
| 组播在全网泛洪 | IGMP Snooping 是否开启；mrouter 端口是否配置 |
| 有成员但无流量 | PIM 邻居是否建立；**RP 地址是否全网一致** |
| 组播时断时续 | SPT 切换问题；RPF 检查失败 |
| 三层通但二层不通 | 检查 Snooping 表项与 mrouter 端口 |

> **★ 排障第一查**：`show ip pim rp`——**RP 地址不一致是组播故障的头号原因**，且现象往往表现为"时有时无"，极具迷惑性。

> **现场故事 · 监控画面全黑的"RP 不一致"**  
某园区视频监控系统改造后，部分楼层的监控画面全黑，但同一 VLAN 内其他业务正常。  
排查：单播全通，组播地址规划正确，IGMP Snooping 表项也有成员端口。  
最后 `show ip pim rp` 发现：核心交换机配置的 RP 是 10.0.0.100，而其中一台汇聚交换机被前任工程师单独配成了 10.0.0.200。**两台设备的 RP 认知不一致，RPT 建不起来**。  
统一 RP 后，画面全部恢复。  
**复盘**：**所有需要"全网一致"的参数（RP、MSTP 域名、VRRP 组号、OSPF 区域号）都应该写进规划表并在验收时逐台核对。** 这类故障不会报错、不会告警，只会在业务上体现为"莫名其妙不通"。

---

### 13_7 速记卡 · 板块13
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | IPv6 地址 128 位，`::`** 只能出现一次** | 必考 |
| ★2 | **IPv6 没有广播**，广播功能由组播替代 | 与 IPv4 对比 |
| ★3 | FE80::/10 链路本地，**OSPFv3 用它建邻居** | 关键地址 |
| ★4 | `ipv6 unicast-routing` 必须开，否则配了也不转发 | 最易漏 |
| ★5 | EUI-64：MAC 中间插 FFFE + **第 7 位取反** | 生成规则 |
| ★6 | OSPFv3 认证靠 IPsec；**在接口下启用**；RID 需手工配 | 与 v2 差异 |
| ★7 | IPv6 BGP 需 `address-family ipv6 unicast` 下 **activate** | 默认不激活 |
| ★8 | `show ipv6 neighbors` = IPv6 的 `show arp` | 排障要点 |
| ★9 | 过渡首选**双栈**；IPv6 孤岛用隧道 | 选型 |
| ★10 | 组播：一份数据按需复制，**IGMP Snooping 解决二层泛洪** | 核心价值 |
| ★11 | PIM-SM 是拉模型（主流），**RP 必须全网一致** | 头号故障原因 |
| ★12 | 组播排障第一查：`show ip pim rp` | 排障顺序 |

## 板块14 · RGSE 进阶专题与故障排查方法论
> **本板块解决什么问题**：从"把网络配通"升级到"解释为什么这么走、跨域怎么规划、故障根因在哪"。这是 RGSE 的主线，也是三级认证的能力分水岭。  
对应 RGSE 考纲：BGP 路由属性和高级特性、ISIS 原理与应用MPLS 原理和应用SR 原理和应用IPSec、组播、QoS、IPv6、EVPN VXLAN、局域网/路由规划设计、常见故障排查与解决方案。  
考试结构：C8511-Written（笔试）+ C8511-Lab（实验），笔试成绩 24 个月内有效。

---

### 14_1 RGSE 的能力分水岭
| 层级 | 典型问题 | RGSE 的答案形态 |
| --- | --- | --- |
| RGSA | "怎么配通 OSPF？" | 命令序列 |
| RGSP | "园区网双核心怎么设计？" | 方案 + 配置 + 验收 |
| **RGSE** | "为什么这条路由不优选？跨域 VPN 怎么规划？故障根因在哪？" | **原理推演 + 联动分析 + 定位路径** |

#### RGSE 的三个关键特征
1. **跨技术联动**——BGP + MPLS + QoS + 组播叠加，不是单点技术。
2. **跨厂商互通**——能力标准明确包含"**含跟常见的非锐捷设备联动**"。
3. **方案与排障**——局域网规划设计、路由规划设计、常见故障排查各占相当比重。

> **★ 备考启示**：不能只会锐捷自家命令，必须懂**协议标准本身**。考题里出现"与某厂商设备对接"的场景是常态。

#### RGSE 答题的思维框架
```plain
拿到一个复杂问题时的标准动作：
  第1步 定界    —— 这是几层的问题？（物理 / 二层 / 三层 / 应用）
  第2步 定因    —— 是协议行为配置错误、还是设计缺陷？
  第3步 定责    —— 涉及哪几台设备、哪几条链路？
  第4步 定方案  —— 临时规避 + 根本解决，两者都要给
  第5步 定回退  —— 改错了怎么退回来？
```

---

### 14_2 BGP 选路 13 条与高级特性
#### BGP 选路规则（13 条，按优先级）
RGSE 必考，且是排障核心。前 8 条必须背熟：

| 序号 | 规则 | 说明 |
| --- | --- | --- |
| 1 | **Weight（权重）** | 私有属性，**本地有效，越大越优** |
| 2 | **Local_Preference** | AS 内有效，**越大越优** |
| 3 | **本地始发优先** | 本地 network/aggregate > 从邻居学来 |
| 4 | **AS_Path 长度** | **越短越优** |
| 5 | **Origin 属性** | IGP(i) < EGP(e) < Incomplete(?) |
| 6 | **MED** | **越小越优** |
| 7 | **EBGP 优于 IBGP** | 同目的优先选 EBGP 路径 |
| 8 | **到下一跳的 IGP 度量** | 越小越优（热土豆路由） |
| 9-13 | 最老 EBGP 邻居 / Router ID 小 / Cluster_List 短 / 最小邻居地址 | 兜底 |

> **记忆锚点**：Weight → Local_Pref → 本地始发 → AS_Path → Origin → MED → E/BGP → IGP Cost。  
**★ 一句话区别**：**Local_Pref 管"我怎么出去"，MED 管"别人怎么进来"。**

#### BGP 属性分类（高频考点）
| 分类 | 属性 |
| --- | --- |
| **公认必遵（Well-known Mandatory）** | AS_Path、Next_Hop、Origin |
| **公认自决（Well-known Discretionary）** | Local_Preference、Atomic_Aggregate |
| **可选可传递（Optional Transitive）** | **Community**、Aggregator |
| **可选非传递（Optional Non-transitive）** | **MED**、Originator_ID、Cluster_List |

> **★ 必考题**：MED 是"可选非传递"，**跨 AS 传递时会丢失**；Community 是"可选可传递"，可以跨 AS 携带标记。

#### 路由反射器（Route Reflector）
**解决的问题**：IBGP 水平分割（从 IBGP 邻居学到的路由不再转发给其他 IBGP 邻居），导致 AS 内需要**全互联**（n 台设备需 n(n-1)/2 个会话）。

```plain
没有 RR：              有 RR：
R1──R2                 R1──┐
│╲  │╲                  R2──┼── RR ── 反射给所有 Client
│ ╲ │ ╲                 R3──┘
R3──R4
6 条会话                3 条会话
```

```bash
! RR 上配置
Ruijie(config)# router bgp 65001
Ruijie(config-router)# neighbor 2.2.2.2 route-reflector-client
Ruijie(config-router)# neighbor 3.3.3.3 route-reflector-client
Ruijie(config-router)# exit
```

**防环机制**：`Originator_ID`（记录始发者 RID）和 `Cluster_List`（记录经过的 RR 簇）。收到携带自己 RID 的路由即丢弃。

#### BGP 联盟（Confederation）
把大 AS 拆成若干子 AS，内部用 EBGP，对外仍是一个 AS。相比 RR，配置改动大但更符合真实管理边界。

| 对比项 | 路由反射器 RR | 联盟 Confederation |
| --- | --- | --- |
| 改动范围 | 只需改 RR 本身 | 所有设备都要改配置 |
| 对外表现 | 仍是同一 AS | 仍是同一 AS |
| 防环 | Originator_ID / Cluster_List | 子 AS 号（AS_CONFED） |
| 适用 | 大多数场景（主流） | 有明确管理边界拆分需求 |

#### BGP 常用策略配置
```bash
! 用 route-map 设置 Local_Preference（控制"我怎么出去"）
Ruijie(config)# route-map SET-LP permit 10
Ruijie(config-route-map)# set local-preference 200
Ruijie(config-route-map)# exit
Ruijie(config)# router bgp 65001
Ruijie(config-router)# neighbor 10.0.0.2 route-map SET-LP in

! AS-Path 追加（影响"别人怎么进来"，让对端走别的路）
Ruijie(config)# route-map PREPEND permit 10
Ruijie(config-route-map)# set as-path prepend 65001 65001 65001
Ruijie(config-route-map)# exit
Ruijie(config-router)# neighbor 10.0.0.2 route-map PREPEND out

! Community 标记
Ruijie(config-route-map)# set community 65001:100
Ruijie(config-router)# neighbor 10.0.0.2 send-community
```

#### BGP 验证
```bash
Ruijie# show ip bgp 192.168.1.0              ! 查看该路由的所有路径与属性
Ruijie# show ip bgp summary                  ! 邻居状态
Ruijie# show ip bgp neighbors 10.0.0.2 advertised-routes   ! 我发出去的路由
Ruijie# show ip bgp neighbors 10.0.0.2 received-routes     ! 我收到的路由
Ruijie# show ip bgp community 65001:100      ! 按 community 过滤
```

> **★ 排障利器**：`show ip bgp x.x.x.x` 能列出该前缀的**所有候选路径及其属性**，配合选路规则逐条比对，就能回答"为什么选了这条而不是那条"。

> **现场故事 · "为什么流量走了贵的那条专线"**  
客户有两条专线：A 线带宽大但贵，B 线便宜。规划是主走 B、备份走 A，但实际流量一直跑在 A 线上。  
工程师查路由表，两条路由都在。用 `show ip bgp 目标网段` 一看：两条路径的前 3 条选路规则（Weight、Local_Pref、本地始发）全部相同，**第 4 条 AS_Path 长度上 A 线比 B 线短一跳**，所以 A 当选。  
解决：在 B 线邻居上用 route-map 把 Local_Preference 调高到 200（优先级高于 AS_Path），流量立刻切到 B 线。  
**复盘**：**BGP 选路是"逐条比较、先命中先赢"**。不理解 13 条顺序，就永远解释不了"为什么它选了那条"。所有 BGP 流量路径问题，最终都归结为"逐条比对选路规则"。

---

### 14_3 ISIS 原理与应用
#### 与 OSPF 的对比
| 对比项 | OSPF | ISIS |
| --- | --- | --- |
| 层级 | 基于 IP（协议号 89） | **基于数据链路层**（不依赖 IP） |
| 区域 | 基于**接口**（ABR 在设备上） | 基于**设备**（L1/L2 路由器） |
| 区域边界 | 在 ABR 上 | **在链路上** |
| 扩展性 | 良好 | **更优**（运营商骨干首选） |
| 报文 | 5 种 | 9 种（Hello/LSP/CSNP/PSNP 等） |
| 度量 | Cost（参考带宽/带宽） | **默认所有接口 Cost=10**（与带宽无关） |

#### 路由器级别
| 级别 | 作用 |
| --- | --- |
| **L1** | 区域内路由，类似 OSPF 非骨干区域 |
| **L2** | 区域间路由，组成骨干 |
| **L1/L2** | 兼具，类似 OSPF ABR（**默认**） |

#### NET 地址格式
```plain
NET = AreaID(1-13字节) . SystemID(6字节) . SEL(1字节，固定00)

示例：49.0001.0000.0000.0001.00
      └─区域──┘ └─System ID──┘ └SEL┘
```

#### 配置
```bash
Ruijie(config)# router isis 1
Ruijie(config-router)# net 49.0001.0000.0000.0001.00
Ruijie(config-router)# is-type level-2-only        ! 骨干路由器
Ruijie(config-router)# exit

Ruijie(config)# interface gi0/1
Ruijie(config-if)# ip address 10.0.0.1 255.255.255.252
Ruijie(config-if)# ip router isis 1
Ruijie(config-if)# isis circuit-type level-2-only
Ruijie(config-if)# exit
```

#### 验证
```bash
Ruijie# show isis neighbors
Ruijie# show isis database
Ruijie# show isis topology
Ruijie# show ip route isis
```

> **★ 注意**：ISIS 默认所有接口 Cost 都是 10，**与带宽无关**。要按带宽计算需手工 `isis metric` 或使用 wide metric。这是与 OSPF 最容易混淆的一点。

---

### 14_4 MPLS 与 MPLS VPN
#### MPLS 核心概念
MPLS（Multi-Protocol Label Switching）在 IP 包头前插入 **32 位标签**，路由器按标签转发，不再查 IP 路由表。

```plain
传统 IP 转发：每个路由器都要查路由表 → 慢、每跳独立决策
MPLS 转发：  入口打标签，中间只看标签 → 快、路径可预先规划（TE）
```

| 术语 | 说明 |
| --- | --- |
| **LER（Label Edge Router）** | 边缘路由器，负责压入（Push）/弹出（Pop）标签 |
| **LSR（Label Switching Router）** | 核心路由器，负责标签交换（Swap） |
| **LSP（Label Switched Path）** | 标签交换路径，**单向** |
| **FEC** | 转发等价类，同一类数据包走同一路径 |
| **LFIB** | 标签转发表 |

#### 标签操作三种
```plain
Push（压入）→ Swap（交换）→ Pop（弹出）
  入口LER       中间LSR       出口LER
```

#### MPLS VPN 三大组件
| 组件 | 作用 |
| --- | --- |
| **VRF** | 虚拟路由转发表，实现**路由隔离**（不同客户的路由互不干扰） |
| **RD（Route Distinguisher）** | 路由区分符，8 字节，把可能重叠的私网 IP 变成全局唯一的 VPNv4 地址 |
| **RT（Route Target）** | 路由目标，BGP 扩展团体属性，**控制路由导入导出** |

> **★ 一句话区分 RD 与 RT（必考）**：
> + **RD 解决"地址重叠"问题**——让 192.168.1.0/24 在 A 客户和 B 客户处变成不同的 VPNv4 前缀
> + **RT 解决"路由该给谁"问题**——拓扑控制，决定 VPN 成员关系

#### 配置示例
```bash
! ============ PE 设备 ============
! 1. 创建 VRF
PE(config)# ip vrf CUSTOMER-A
PE(config-vrf)# rd 65001:100
PE(config-vrf)# route-target both 65001:100
PE(config-vrf)# exit

! 2. 接口绑定 VRF（★ 先绑 VRF 再配 IP）
PE(config)# interface gi0/1
PE(config-if)# ip vrf forwarding CUSTOMER-A
PE(config-if)# ip address 192.168.1.1 255.255.255.0
PE(config-if)# exit

! 3. 启用 MPLS
PE(config)# mpls ip
PE(config)# interface gi0/24
PE(config-if)# mpls ip
PE(config-if)# exit

! 4. MP-BGP 传递 VPNv4 路由
PE(config)# router bgp 65001
PE(config-router)# neighbor 2.2.2.2 remote-as 65001
PE(config-router)# neighbor 2.2.2.2 update-source loopback 0
PE(config-router)# address-family vpnv4 unicast
PE(config-router-af)# neighbor 2.2.2.2 activate
PE(config-router-af)# neighbor 2.2.2.2 send-community extended
PE(config-router-af)# exit-address-family
PE(config-router)# address-family ipv4 vrf CUSTOMER-A
PE(config-router-af)# neighbor 192.168.1.2 remote-as 65010    ! CE 侧 EBGP
PE(config-router-af)# exit-address-family
```

> **★ 部署禁忌**：`ip vrf forwarding` 会**清空接口上已配置的 IP 地址**。所以顺序是：先绑定 VRF，再配 IP。反过来会导致 IP 丢失，这个坑很多人踩过。

#### 验证
```bash
PE# show ip vrf                            ! 查看 VRF 列表
PE# show ip vrf interfaces                 ! 查看绑定到 VRF 的接口
PE# show ip route vrf CUSTOMER-A           ! 查看 VRF 路由表（★ 最常用）
PE# show ip bgp vpnv4 all                  ! 查看 VPNv4 路由
PE# show mpls forwarding-table             ! 查看标签转发表
PE# show mpls ldp neighbor                 ! 查看 LDP 邻居
PE# ping vrf CUSTOMER-A 192.168.1.2        ! 带 VRF 的 ping（★ 必会）
```

> **★ 排障要点**：配了 VRF 之后，**所有针对该 VPN 的 ping / traceroute 都必须带 **`vrf 名称`** 参数**。直接用 `ping 192.168.1.2` 走的是全局路由表，会不通——这是 VRF 环境最常见的"误判为故障"。

---

### 14_5 SR（Segment Routing）概述
> **承上启下**：14_4 的 MPLS 解决了「按标签转发」，但标签要靠 LDP 或 RSVP-TE 逐跳分发，中间每台设备都得维护 LSP 状态，协议重、运维难。SR 的想法很直接：**既然路径是源端决定的，那就把路径直接写进报文头里，中间节点照着走就行**。

#### SR 的核心思想
传统 MPLS 需要 LDP/RSVP-TE 来分发标签，协议复杂。SR 的思路：**把路径信息编码进报文头部的"段列表"（Segment List），源节点指定路径，中间节点只需按段转发**。

| 对比项 | MPLS（LDP/RSVP-TE） | SR |
| --- | --- | --- |
| 标签分发 | 需要 LDP / RSVP-TE 协议 | **由 IGP（OSPF/ISIS）扩展分发** |
| 状态维护 | 中间节点需维护每条 LSP 状态 | **中间节点无需维护连接状态** |
| 路径控制 | 依赖 TE 隧道 | **源路由，段列表显式指定** |
| 与 SDN 结合 | 较弱 | **天然适配（控制器下发段列表）** |

#### 两种 SR 实现
| 实现 | 说明 |
| --- | --- |
| **SR-MPLS** | 在 MPLS 数据平面上实现，用 MPLS 标签作为 Segment（主流部署） |
| **SRv6** | 基于 IPv6，用 IPv6 扩展头（SRH）承载段列表，是演进方向 |

#### 关键概念
| 概念 | 说明 |
| --- | --- |
| **Segment（段）** | 一段指令，如"去往节点 X""走某条链路" |
| **Node SID** | 标识某个节点的段（类似 Prefix SID） |
| **Adjacency SID** | 标识某条邻接链路的段 |
| **Segment List** | 有序的段列表，构成完整路径 |
| **SRGB** | Segment Routing Global Block，全局标签块 |

```plain
示例：报文要从 A 到 D，指定路径 A → B → C → D
  传统 MPLS：需要沿途建立 LSP，每个节点维护状态
  SR：      源节点 A 压入段列表 [B, C, D]，中间节点按栈顶段逐跳转发
```

```bash
! SR 基础配置示意（ISIS SR）
Ruijie(config)# router isis 1
Ruijie(config-router)# segment-routing mpls
Ruijie(config-router)# segment-routing global-block 16000 23999
Ruijie(config-router)# exit
Ruijie(config)# interface loopback 0
Ruijie(config-if)# ip address 1.1.1.1 255.255.255.255
Ruijie(config-if)# isis prefix-sid index 1
```

```bash
Ruijie# show isis segment-routing           ! 查看 SR 状态
Ruijie# show segment-routing                ! 查看 SR 全局信息
```

---

### 14_6 IPSec 技术原理与应用
#### IPSec 体系
| 组件 | 作用 |
| --- | --- |
| **AH** | 认证头，提供完整性 + 数据源认证（**不加密**） |
| **ESP** | 封装安全载荷，提供加密 + 认证（**主流**） |
| **IKE** | 密钥交换协议，负责协商 SA（分 v1 / v2） |
| **SA** | 安全关联，双方约定的加密/认证参数集合 |

#### 两种封装模式
```plain
传输模式（Transport）：  [IP头][ESP头][数据][ESP尾]
                        保护的是上层数据，用于主机到主机

隧道模式（Tunnel）：     [新IP头][ESP头][原IP头][数据][ESP尾]
                        保护整个原始 IP 包，用于网关到网关（★ 站点互联用这个）
```

#### IKE 两个阶段
```plain
阶段一（IKE SA）：  协商加密/认证算法，建立安全通道
                    主模式（6 个报文）/ 野蛮模式（3 个报文）
        ↓
阶段二（IPSec SA）：在安全通道内协商数据加密参数
                    快速模式
        ↓
      数据传输
```

#### 站点到站点 IPSec VPN 配置
```bash
! 1. 定义兴趣流（哪些流量走 VPN）
Ruijie(config)# ip access-list extended VPN-TRAFFIC
Ruijie(config-ext-nacl)# permit ip 192.168.10.0 0.0.0.255 172.16.10.0 0.0.0.255
Ruijie(config-ext-nacl)# exit

! 2. IKE 阶段一策略
Ruijie(config)# crypto isakmp policy 10
Ruijie(config-isakmp)# encryption aes 256
Ruijie(config-isakmp)# hash sha
Ruijie(config-isakmp)# authentication pre-share
Ruijie(config-isakmp)# group 2
Ruijie(config-isakmp)# exit
Ruijie(config)# crypto isakmp key Ruijie@123 address 202.100.1.2

! 3. IPSec 阶段二变换集
Ruijie(config)# crypto ipsec transform-set TS1 esp-aes 256 esp-sha-hmac
Ruijie(config-crypto-trans)# mode tunnel
Ruijie(config-crypto-trans)# exit

! 4. 加密映射并应用到接口
Ruijie(config)# crypto map CMAP 10 ipsec-isakmp
Ruijie(config-crypto-map)# match address VPN-TRAFFIC
Ruijie(config-crypto-map)# set peer 202.100.1.2
Ruijie(config-crypto-map)# set transform-set TS1
Ruijie(config-crypto-map)# exit
Ruijie(config)# interface gi0/1
Ruijie(config-if)# crypto map CMAP
Ruijie(config-if)# exit
```

#### IPSec 验证与排障
```bash
Ruijie# show crypto isakmp sa              ! 阶段一 SA 状态
Ruijie# show crypto ipsec sa               ! 阶段二 SA 状态（看加解密包数）
Ruijie# show crypto map                    ! 查看加密映射
Ruijie# clear crypto isakmp                ! 清阶段一（改配置后）
Ruijie# clear crypto sa                    ! 清所有 SA
```

| 现象 | 排查方向 |
| --- | --- |
| 阶段一建不起来 | 两端 isakmp policy 参数（加密/hash/认证/DH 组）是否一致；预共享密钥是否一致；peer 地址是否可达 |
| 阶段一通但阶段二不通 | **兴趣流是否镜像对称**（本端 permit 源 A 目的 B，对端必须是源 B 目的 A）；变换集是否一致 |
| SA 起来了但业务不通 | 路由是否指向 VPN；是否缺少 NAT 豁免（见下） |
| 加解密包数为 0 | 流量没匹配兴趣流；路由没走 VPN 接口 |

> **★ NAT 与 IPSec 冲突（经典坑）**：如果出口同时做了 PAT，走 VPN 的流量会被 NAT 转换后不再匹配兴趣流，导致 VPN 不通。解决：在 NAT 的 ACL 中 **deny 掉 VPN 的兴趣流**，让这些地址不做 NAT。

```bash
Ruijie(config)# ip access-list extended NAT-ACL
Ruijie(config-ext-nacl)# deny ip 192.168.10.0 0.0.0.255 172.16.10.0 0.0.0.255  ! VPN 流量不做 NAT
Ruijie(config-ext-nacl)# permit ip 192.168.10.0 0.0.0.255 any
Ruijie(config-ext-nacl)# exit
```

---

### 14_7 QoS 技术原理与应用
#### QoS 解决什么问题
网络拥塞时的四种处理模型：

| 模型 | 说明 | 适用 |
| --- | --- | --- |
| **Best-Effort** | 尽力而为，不区分 | 默认 |
| **IntServ** | 资源预留（RSVP），每流预留 | 规模小，难部署 |
| **DiffServ** | **差分服务，按类区分（主流）** | **园区/骨干网** |

#### QoS 四大组件
| 组件 | 作用 |
| --- | --- |
| **分类与标记（Classification & Marking）** | 识别流量并打标记（DSCP / 802.1p / IP 优先级） |
| **拥塞管理（Queuing）** | 拥塞时决定谁先发（PQ / CQ / WFQ / CBQ） |
| **拥塞避免（Avoidance）** | 提前丢包防全局同步（RED / WRED） |
| **限速与整形（Policing & Shaping）** | 控制速率（CAR / GTS） |

#### 常用队列机制对比
| 机制 | 特点 | 适用 |
| --- | --- | --- |
| **PQ（优先队列）** | 高优先级队列绝对优先 | 语音等实时业务；**低优先级可能饿死** |
| **CQ（定制队列）** | 按比例分配带宽 | 一般业务 |
| **WFQ（加权公平）** | 按流公平分配 | 默认机制 |
| **CBWFQ / LLQ** | **类的加权公平 + 低时延队列** | **语音 + 数据混合（推荐）** |

#### DiffServ 配置示例
```bash
! 1. 分类：用 class-map 匹配流量
Ruijie(config)# class-map match-any VOICE
Ruijie(config-cmap)# match ip dscp ef
Ruijie(config-cmap)# match access-group 101           ! 也可匹配 ACL
Ruijie(config-cmap)# exit

! 2. 策略：用 policy-map 定义动作
Ruijie(config)# policy-map QOS-POLICY
Ruijie(config-pmap)# class VOICE
Ruijie(config-pmap-c)# priority 1000                  ! LLQ，保证 1000kbps
Ruijie(config-pmap-c)# exit
Ruijie(config-pmap)# class class-default
Ruijie(config-pmap-c)# bandwidth remaining percent 50
Ruijie(config-pmap-c)# exit
Ruijie(config-pmap)# exit

! 3. 应用：绑定到接口出方向
Ruijie(config)# interface gi0/1
Ruijie(config-if)# service-policy output QOS-POLICY
Ruijie(config-if)# exit
```

#### 限速配置
```bash
! 接口限速（CAR）
Ruijie(config)# interface gi0/1
Ruijie(config-if)# rate-limit output 10000000 1875000 1875000 conform-action transmit exceed-action drop
!                                  10Mbps   突发       突发

! 或用 policy-map 做限速
Ruijie(config-pmap-c)# police 10000000 conform-action transmit exceed-action drop
```

#### 常用 DSCP 值
| DSCP | 名称 | 典型业务 |
| --- | --- | --- |
| EF（46） | Expedited Forwarding | **语音（VoIP）** |
| AF41（34） | Assured Forwarding | 视频会议 |
| AF31（26） | Assured Forwarding | 关键业务应用 |
| BE（0） | Best Effort | 普通上网 |

#### 验证
```bash
Ruijie# show policy-map                      ! 查看策略配置
Ruijie# show policy-map interface gi0/1      ! ★ 查看接口策略命中情况（看包数）
Ruijie# show class-map                       ! 查看分类
Ruijie# show queue                           ! 查看队列状态
```

> **★ 排障要点**：`show policy-map interface` 会显示每个 class 的**匹配包数**。QoS 不生效时先看计数器——不增长说明流量根本没被分类到（ACL 或匹配条件错了）。

#### QoS 部署建议
```plain
第1步 尽量在靠近源的位置打标记（信任边界）
第2步 中间设备信任标记，按标记调度，不必重复分类
第3步 队列调度只在真正可能拥塞的接口上配（通常是出口/上行口）
第4步 语音用 LLQ（priority），关键业务用 CBWFQ 保证带宽
第5步 不要过度设计——QoS 配置越复杂，排障越困难
```

---

### 14_8 EVPN VXLAN 与大二层
#### 传统大二层的问题
虚拟机迁移、分布式业务要求"跨三层网络实现二层互通"。传统方案（STP + 大二层）的问题：

```plain
STP 大二层的困境：
  ✗ 阻塞链路，带宽浪费
  ✗ 收敛慢，收敛期丢包
  ✗ 广播域过大，风暴影响面大
  ✗ VLAN 只有 4094 个，云环境不够用
```

#### VXLAN 的核心思路
**VXLAN（Virtual Extensible LAN）**：把二层以太帧封装在 UDP 里，跨三层网络传输——**"二层跑在三层上"（Overlay）**。

```plain
原始以太帧 ──封装──▶ [外层IP头][UDP 4789][VXLAN头(VNI)][原始以太帧]
                                              ↑
                                        24 bit VNI，支持 1600 万个隔离域
```

| 对比项 | VLAN | VXLAN |
| --- | --- | --- |
| 标识位数 | 12 bit（4094 个） | **24 bit VNI（约 1600 万个）** |
| 跨三层 | 不支持 | **支持（Overlay）** |
| 依赖 STP | 是 | **否（Underlay 用路由，无环）** |
| 封装 | 802.1Q | **MAC-in-UDP（UDP 4789）** |

#### VXLAN 关键术语
| 术语 | 说明 |
| --- | --- |
| **VTEP** | VXLAN 隧道端点，负责封装/解封装 |
| **VNI** | VXLAN 网络标识，类似 VLAN ID 但 24 位 |
| **Underlay** | 底层 IP 承载网络（跑路由协议，无环） |
| **Overlay** | 叠加的虚拟二层网络 |
| **EVPN** | **控制平面**，用 MP-BGP 传递 MAC/IP 可达信息 |

#### 为什么需要 EVPN
```plain
早期 VXLAN：  靠组播泛洪学习 MAC（依赖 Underlay 组播，难运维）
EVPN VXLAN：  ★ 用 MP-BGP 作为控制平面传递 MAC/IP 路由
              → 无组播依赖、支持 ARP 抑制、支持主机路由（/32）精确转发
```

| EVPN 优势 | 说明 |
| --- | --- |
| **控制平面学习** | MAC 地址通过 BGP 通告，不靠数据平面泛洪 |
| **ARP 抑制** | VTEP 本地代答 ARP，减少泛洪 |
| **主机路由** | 通告 /32 主机路由，支持跨网段最优转发 |
| **多活网关** | 支持分布式任播网关，虚拟机迁移无需改网关 |

#### 配置示例（EVPN VXLAN）
```bash
! 1. Underlay：IGP 打通 VTEP 之间的 Loopback
Ruijie(config)# router ospf 1
Ruijie(config-router)# network 1.1.1.1 0.0.0.0 area 0
Ruijie(config-router)# exit

! 2. 创建 VXLAN 与 VNI 映射
Ruijie(config)# vxlan 10
Ruijie(config-vxlan)# vni 10010
Ruijie(config-vxlan)# exit

! 3. 配置 VTEP 接口
Ruijie(config)# interface overlayrouter 1
Ruijie(config-if)# vxlan 10
Ruijie(config-if)# exit

! 4. EVPN 控制平面（MP-BGP）
Ruijie(config)# router bgp 65001
Ruijie(config-router)# neighbor 2.2.2.2 remote-as 65001
Ruijie(config-router)# neighbor 2.2.2.2 update-source loopback 0
Ruijie(config-router)# address-family l2vpn evpn
Ruijie(config-router-af)# neighbor 2.2.2.2 activate
Ruijie(config-router-af)# exit-address-family
Ruijie(config-router)# exit

! 5. 配置 EVPN 实例（EVI）与 VLAN 关联
Ruijie(config)# evpn
Ruijie(config-evpn)# vni 10010 l2
Ruijie(config-evpn-vni)# rd 1.1.1.1:10010
Ruijie(config-evpn-vni)# route-target both 65001:10010
Ruijie(config-evpn-vni)# exit
```

#### 验证
```bash
Ruijie# show vxlan                            ! 查看 VXLAN 配置
Ruijie# show vxlan vni 10010                  ! 查看指定 VNI
Ruijie# show bgp l2vpn evpn summary           ! EVPN 邻居状态
Ruijie# show bgp l2vpn evpn                   ! EVPN 路由
Ruijie# show mac address-table vxlan          ! VXLAN MAC 表
Ruijie# show evpn                             ! EVPN 全局信息
```

#### 部署要点
```plain
第1步 Underlay 必须先通：VTEP 的 Loopback 之间必须路由可达
第2步 MTU 要放大：VXLAN 封装增加 50 字节左右开销，Underlay 建议 MTU ≥ 1600
第3步 EVPN 邻居必须 activate（address-family l2vpn evpn 下）
第4步 RD/RT 规划与 MPLS VPN 类似，RD 区分、RT 控制导入导出
```

---

### 14_9 故障排查四法论与综合案例
#### 排障四法
| 方法 | 含义 | 适用 |
| --- | --- | --- |
| **分层法** | 从物理层往上逐层排除 | 最通用，任何故障都能用 |
| **分段法** | 把路径切成几段，逐段测试 | 跨多跳、跨域的网络 |
| **对比法** | 拿"正常的"和"异常的"对比配置/状态 | 部分通部分不通 |
| **替换法** | 换端口、换线、换设备 | 怀疑硬件/链路问题 |

#### 分层法标准流程（自底向上）
```plain
第1步 物理层    端口 up 吗？光模块/线缆/光衰正常吗？CRC 涨吗？
     ↓  show ip interface brief / show interfaces counters
第2步 数据链路层 MAC 学到了吗？VLAN 对吗？Trunk 放通了吗？有环路吗？
     ↓  show mac address-table / show vlan / show spanning-tree
第3步 网络层    ARP 有吗？网关通吗？路由表有条目吗？
     ↓  show arp / show ip route / ping 网关
第4步 传输层    端口通吗？ACL 拦了吗？
     ↓  show ip access-lists（看计数器）/ telnet 端口测试
第5步 应用层    DNS 解析对吗？服务本身起来了吗？
     ↓  nslookup / 应用层日志
```

#### 分段法示意
```plain
PC ──第1步── 接入 ──第2步── 汇聚 ──第3步── 核心 ──第4步── 出口 ──第5步── 互联网

逐段测试：
  第1步 PC → 网关          测接入层与 SVI
  第2步 网关 → 核心互联地址  测汇聚到核心
  第3步 核心 → 出口内网口    测核心到出口
  第4步 出口 → 运营商网关    测出口链路
  第5步 出口 → 公网 DNS     测端到端
哪一段不通，故障域就锁定在哪一段
```

#### 对比法要点
```plain
适用场景：同一台交换机上 A 端口通B 端口不通
标准动作：
  第1步 对比两端端口配置    show running-config interface A / B
  第2步 对比端口状态        show interfaces status
  第3步 对比 VLAN 归属       show vlan
  第4步 对比生成树状态       show spanning-tree interface
  第5步 对比安全特性        show port-security interface
```

#### 综合案例一：全网间歇性丢包
```plain
现象：整个办公网每隔十几分钟丢包几秒，无规律，业务投诉不断

排查过程：
  第1步 分层：ping 网关也丢，说明问题在二层或三层以下
  第2步 查交换机 CPU：show cpu —— 发现周期性冲高
  第3步 查 MAC 表：show mac address-table count —— 某 VLAN MAC 数量周期性暴增
  第4步 查端口：show interfaces status —— 未发现 err-disable
  第5步 抓包：发现大量源 MAC 不断变化的帧

根因：某端口下接入了环路或 MAC 泛洪源
解决：定位该端口，启用 port-security 限制 MAC 数量 + rldp
复盘：间歇性丢包 + CPU 冲高 + MAC 数量异常 = 二层环路/泛洪三件套
```

#### 综合案例二：VRRP 切换后部分终端不通
```plain
现象：核心主备切换演练后，大部分终端正常，约 20% 终端仍无法上网

排查过程：
  第1步 查 VRRP 状态：show vrrp brief —— 新 Master 正常
  第2步 查终端 ARP：arp -a —— 发现这 20% 终端的网关 MAC 仍是【旧 Master 的 MAC】
  第3步 手动清空终端 ARP：arp -d * —— 立刻恢复

根因：部分终端未响应新 Master 的免费 ARP，ARP 缓存未刷新
解决：缩短 ARP 老化时间；或在网关侧主动发送免费 ARP
复盘：VRRP 切换依赖免费 ARP 刷新终端缓存，这是设计上的"软肋"
      → 关键业务终端建议缩短 ARP 老化时间，或在演练后主动清缓存
```

#### 综合案例三：BGP 路由振荡
```plain
现象：某条 BGP 路由反复 up/down，日志里邻居频繁重建

排查思路：
  第1步 查邻居状态：show ip bgp summary —— 状态在 Established 与 Idle 间跳变
  第2步 查可达性：ping 邻居地址 —— 时通时断（底层链路问题）
  第3步 查底层：物理链路 / MTU / 中间设备
  第4步 若底层正常，检查是否配置了 route-map 导致路由被反复撤销
  第5步 检查是否有 dampening 抑制

解决顺序：先修底层链路，再考虑启用路由阻尼（dampening）抑制振荡
复盘：BGP 是应用层协议，绝大多数"路由振荡"根因在【底层】
      → 不要一上来就调 BGP 参数，先确认 ping 邻居是否稳定
```

#### RGSE 排障答题模板
```plain
遇到一个复杂故障，按这五步组织答案：
  第1步 现象确认   —— 影响范围（哪些网段/业务）、时间规律（持续/间歇）
  第2步 信息收集   —— 拓扑、配置、日志、show 输出（不要凭猜测）
  第3步 定界       —— 用分层/分段法锁定故障域在哪一段
  第4步 定因       —— 给出根因，并说明"为什么这个根因会导致这个现象"
  第5步 解决与规避 —— 临时规避方案 + 根本解决方案 + 回退方案
```

---

### 14_10 速记卡 · 板块14
| 编号 | 一句话结论 | 关键词 |
| --- | --- | --- |
| ★1 | BGP 选路 13 条，前 8 条必背：Weight→LP→本地始发→AS_Path→Origin→MED→E/BGP→IGP Cost | 记忆锚点 |
| ★2 | **Local_Pref 管"我怎么出去"，MED 管"别人怎么进来"** | 一句话区别 |
| ★3 | MED 是**可选非传递**（跨 AS 丢失）；Community 是可选可传递 | 必考题 |
| ★4 | RR 解决 IBGP 全互联；防环靠 Originator_ID + Cluster_List | 反射器 |
| ★5 | ISIS **默认所有接口 Cost=10**，与带宽无关 | 与 OSPF 差异 |
| ★6 | **RD 解决地址重叠，RT 解决路由给谁** | MPLS VPN 必考 |
| ★7 | `ip vrf forwarding` **会清空接口 IP**，先绑 VRF 再配 IP | 部署禁忌 |
| ★8 | VRF 环境下 ping 必须带 `vrf 名称` | 最常误判 |
| ★9 | SR 把路径编码进**段列表**，中间节点无状态；SR-MPLS 主流，SRv6 是方向 | 核心思想 |
| ★10 | IPSec 阶段一对**参数与密钥**，阶段二对**兴趣流与变换集**；兴趣流必须镜像对称 | 排障要点 |
| ★11 | IPSec 与 NAT 冲突时，**在 NAT ACL 中 deny 掉 VPN 兴趣流** | 经典坑 |
| ★12 | QoS 四步：分类打标 → 队列调度 → 拥塞避免 → 限速整形；语音用 **LLQ** | 部署顺序 |
| ★13 | VXLAN = **MAC-in-UDP（UDP 4789）**，VNI 24 位；EVPN 用 **MP-BGP** 传 MAC/IP | 大二层 |
| ★14 | 排障四法：**分层、分段、对比、替换** | 方法论 |
| ★15 | 间歇丢包 + CPU 冲高 + MAC 暴增 = **二层环路/泛洪三件套** | 综合判断 |