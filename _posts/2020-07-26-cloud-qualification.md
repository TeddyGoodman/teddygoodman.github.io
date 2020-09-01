---
title: cloud-qualification 
author: Teddy
date: 2020-07-26 13:30:07 +0800
categories: [体系结构-应用, 云计算]
tags: [CloudComputing]
---

# 云认证

>  学习&考试准备

* 学习路径
  1. 云计算基础
  2. **云服务器产品**
  3. **云网络产品**
  4. CDN加速产品
  5. 云存储产品
  6. 数据库产品
  7. 安全产品
  8. 视频与通信服务

# I. 云计算基础

## 1.1 数据中心

### 1.1.1 EDC

* TCO = CapEx + OpeEx + OppCost
* TVO = IT带来的业务价值与收益

| L4   | 业务应用层 *各种应用系统*                                    |
| ---- | ------------------------------------------------------------ |
| L3   | 应用支撑层 *中间件、消息、开发环境、API* / 数据分析层 *数据库* |
| L2   | IT基础设施 *服务器、网络、存储、安全*                        |
| L1   | 机房设施层 *电源、机柜*                                      |
| L0   | 楼宇系统层 *机房、传输*                                      |

* 中心等级、云DC在T3级以上，并行维护+99.982%+1.6H年宕机时间

* IDC资源出租，托管型、租用型，成本低，上线块，标准化，电信级可靠、运维管理；
  * 托管，企业要购买硬件+管理维护+业务
  * 租用，运营商要硬件投入、电力公园、管理维护

### 1.1.2 云计算

* **按需服务，按量付费的服务模式，按需可配置的计算资源共享池**
* 2006 Google CEO提出云计算 Cloud Computing

* 独立自建 > 部分租用 > 按需使用
* 成本低，上线时间很快，运维管理简单、弹性扩展、范围L0-L4，自主公有云、私有云

## 1.2 核心特征

### 1.2.1 模型

| 公有云               | 私有云       | 混合云           | 行业云       |
| -------------------- | ------------ | ---------------- | ------------ |
| 服务目录             |              | 服务生命周期管理 | 运维管理系统 |
| SaaS 软件即服务      | 服务编排调度 | 服务生命周期管理 | 运维管理系统 |
| PaaS 平台即服务      | 服务编排调度 | 服务生命周期管理 | 运维管理系统 |
| IaaS  基础设施即服务 | 服务编排调度 | 服务生命周期管理 | 运维管理系统 |
| 虚拟基础设施         |              |                  | 运维管理系统 |
| 物理基础设施         |              |                  | 运维管理系统 |

* 资源池化  *提升利用率/可用性*
* 弹性扩展  *业务需求/成本均衡*
* 按需服务  *资源/时间*
* 泛网络访问  *随时随地/高质量*
* 服务可度量 *服务计费/精细化运营*

---

### 1.2.2 服务模式

* 服务使用/应用层/中间层/基础设施
* 租户维护如下

| Iaas                   | PaaS            | SaaS     |
| ---------------------- | --------------- | -------- |
| 服务使用/应用层/中间层 | 服务使用/应用层 | 服务使用 |

#### 技术架构

* SaaS

| 应用层 |      |      |      |      |
| ------ | ---- | ---- | ---- | ---- |
| Portal | CRM  | ERP  | OA   | 其他 |

* PaaS

| 中间层     |          |          |          |          |
| ---------- | -------- | -------- | -------- | -------- |
|            | 访问控制 | 负载均衡 | 开发工具 | 服务总线 |
| **中间件** |          |          |          |          |
| **数据库** |          |          |          |          |

* IaaS

| 基础架构层 |            |            |            |              |
| ---------- | ---------- | ---------- | ---------- | ------------ |
|            | 计算资源池 | 存储资源池 | 网络资源池 | 其他资源池   |
| **虚拟化** |            |            |            |              |
|            | 主机       | 存储       | 网络       | 其他基础设施 |

* **管理层**

| 云计算管理 |          |          |          |          |          |          |         |      |
| ---------- | -------- | -------- | -------- | -------- | -------- | -------- | ------- | ---- |
|            | 帐号管理 | 配置管理 | 计费管理 | 安全管理 | 流程管理 | 运维管理 | SLA监控 | API  |

### 1.2.3 部署方式

* 公、私、混、行业

* 公、私区别
  * 多租户、不同组织；同组织、单租户
  * 使用权属于客户、所有权属于服务商；使用权、所有权都属于客户
  * 成本低；成本高
  * 运维较简单；较为复杂
  * 较低的自主可控；较高的自主可控
* 混合
  * 公+私，核心为私，非核心为公
  * 多云统一，多云网关统一管理多个服务商的云服务，高质量议价权、多灾备
* 行业
  * 针对行业或者互联网产品深度优化；

## 1.3 关键技术

### 1.3.1 计算虚拟化

* 虚拟化前，单一OS，软件和硬件强耦合，利用率低，扩展性和容错性差
* 裸金属架构，虚拟化层运行在硬件上，提供CPU和内存资源池、VM、软硬解耦，故障迁移、弹性扩展
* 分类
  * 全虚拟化，OS直接运行在虚拟化层上
    * ESXi
      * User App
      * GuestOS
      * 虚拟化层，OS特权指令通过BT转换执行
      * 硬件
    * KVM
      * User App
      * GusetOS
      * 虚拟化层，OS特权指令切换到根模式执行
      * 硬件
  * 半虚拟化，OS需要修改安装额外的驱动
    * Xen
      * User APP
      * PV GuestOS
      * 虚拟化，OS特权指令超级调用Hypercall
      * 硬件
* 对比
  * KVM
    * 全虚拟化
    * KVM内核完成CPU和内存虚拟化
    * QEMU完成磁盘和网络的虚拟化
    * Linux进程进行虚拟化调度和管理
  * Xen
    * 全/半
    * Xen内核完成CPU、内存
    * Dom0完成磁盘和网络
    * Dom0完成虚拟化调度和管理
  * ESXi
    * 全
    * ESXi内核完成CPU、内存
    * 虚拟化内核完成磁盘和网络IO
    * 虚拟化内核完成虚拟化调度和管理
* KVM
  * VM是Linux进程，有进程管理模块进行管理
  * KVM内核负责CPU和内存虚拟化，QEMU负责I/O虚拟化
  * 硬件支持Intel-VT，AMD-V
* KVM优势
  * 高性能
  * 易扩展
  * 易管理

### 1.3.2 分布式数据存储 ServerSAN

* 原理
  * 将server上分散的本地盘整合为资源池
  * 读写元
    * 承接应用IO
  * 控制元
    * Hash算法确保I/O分布到各个节点
  * 存储元
    * 负责写入数据到存储块
* 优势
  * 高性价比，普通盘高性能
  * 易扩展，线性增删节点
  * 高可靠：保存3副本，快速修改和迁移

### 1.3.3 网络虚拟化 SDN

| 应用层   |             |                        | 业务应用                  |
| -------- | ----------- | ---------------------- | ------------------------- |
| 控制层   | SDN控制软件 | 网络服务               | ^API                      |
| 基础设施 | 网络设备    | 路由器、交换机、防火墙 | ^控制数据接口（OpenFlow） |

* DSN/NFV
  * SDN software define network 
    * 核心
      * 控制面和数据面分离
      * 通用路由器和交换机
      * 控制面可编程
    * 场景
      * 数据中心网络
    * 优点
      * 处理OSI 2-3层（链路，网络），优化交换机、路由器、无线
  * NFV network function virtulization
    * 核心
      * 功能和硬件解耦
      * 商业化硬件替代专用
      * 数据面可编程
    * 场景
      * 运营商基础网络
    * 优点
      * 处理4-7层（传输、会话、表示、应用），优化网络功能、LB、FW、WAN

### 1.3.4 OpenStack

| SERVICE    | DESC           |
| ---------- | -------------- |
| Nova       | 计算           |
| Neutron    | 网络           |
| Keystone   | 认证和授权     |
| Glance     | 镜像           |
| Swift      | 对象存储服务   |
| Cinder     | 块存储服务     |
| Horizon    | 图形化管理界面 |
| Ceilometer | 监控           |
| Heat       | 编排调度       |

* 开源
* 标准
* 部署、运维、升级复杂
* 性能和扩展性差
* 容灾能力不足

### 1.3.4 VStation

* 自主研发的云计算管理平台
* 设计原则
  * 平行扩展、简洁高效、异步
  * Fail-fast、无状态、高可用
  * 共享信道（以太网）
  * 事务处理（SQL）
  * 逻辑抽离（CGI）
  * 易于追溯（git）
* 架构
  * [dispatcher] <==> **API** => 
    * [TaskCmen] **MQ**  <==> 
      * <==> 
        * [Volume / cbs]
        * [dfw]
      * **Compute Access** <==>
        * **Compute**
      * **Image Access** <==>
        * **Image**
      * **NetWork** <==>
        * **IP**
        * **VPC**
      * **Scheduler**
      * **Resource**
      * **Error**
      * **Debug**
* OpenStack vs VStation
  * 集群：千台 / 十万
  * 容灾：需开源组件支持 / 任一模块跨机房容灾
  * 运维：需开发 / 监控、可视化运维
  * 人员：百 / 十
  * 性能：不支持100台同时创建 / 支持数万台同时创建



### 1.3.5 容器

* 轻量级虚拟化，进程隔离，应用和依赖环境、配置共同打包封装，提供独立可移植的运行环境

  * | 虚拟化                 | 容器化                 |
    | :--------------------- | ---------------------- |
    | APP1 \| APP2           | APP1 \| APP2           |
    | Bins/Libs \| Bins/Libs | Bins/Libs \| Bins/Libs |
    | GuestOS \| GuestOS     | 容器引擎               |
    | 虚拟化层               | 虚拟化层/操作系统      |
    | 硬件                   | 硬件                   |



#### Docker

* 标准化，移植性强，**Build, Ship and Run Anywhere**
* 管理
  * K8S（Kubernetes）开源容器编排管理调度
* 优势
  * 轻量
  * 秒级部署
  * 易于移植
  * 弹性伸缩



### 1.3.6 大数据 & AI

* 未来互联网就是利用人工智能在云端处理大数据。---Pony Ma
* 大数据
  * 数据量大
  * 价值密度低
  * 多样化
  * 高速产生
* AI
  * 大数据
  * 算法
  * 算力
  * 边界清晰



## 1.4 行业

* 互联网：C2C / B2C
* 互联网+：B2B2C
* 产业互联网：C2B2B2C



# II. 云服务器V2.0

## 2.1 基础

### 2.1.1 地域和可用区

* **可用区 Zone**
  * 统一地域内电力和网络互相独立的物理数据中心，命名=城市 + 编号
* **地域 region**
  * 一个独立的地理去域名，命名=覆盖范围+机房所在城市
* 云：25个地域+53个可用区
* 部署多地域多可用区
  * 就近接入
  * 隔离故障
  * LB
  * HA

### 2.1.2 实例

* 实例

  * 完整的云服务器（VM），CPU、内存、磁盘、网络、OS
  * 命名=系列.机型.规格（vCPU核心数和内存大小）
  * S4.MEDIUM4

* 管理

  * 控制台或者API管理
  * 在线调整实例配置，重启生效

* 安全

  * 策略
  * 安全组
  * 登录控制

* 规格

  * | 标准型   | S1         | S2                | S3           | S4           |
    | -------- | ---------- | ----------------- | ------------ | ------------ |
    | CPU      | Intel Xeon | Xeon Broadwell V4 | Skylake 6133 | Skylake 6148 |
    | 内存     | DDR3       | DDR4              | 最新DDR4     | 最新DDR4     |
    | 内网带宽 | 10Gbps     | 10Gbps            | 10Gbps       | 25Gbps       |
    | Max规格  | 48C96G     | 56C224G           | 80C320G      | 72C228G      |

* 实例类型

  * 不同配置实现不同的IO、计算、网络、存储能力
  * 选择CVM实例

* 实例族

  * 某一类实例类型集合

* 实例类型

  * | 类型 | 特点                   | 场景                                       |
    | ---- | ---------------------- | ------------------------------------------ |
    | 标准 | 均衡计算、内存和网络   | 中小Web应用、数据库、企业官网              |
    | 内存 | 大内存                 | 大量的内存操作、查找和计算、分布式内存缓存 |
    | 高IO | 高IO、高吞吐量、低时延 | NoSQL、集群化数据库、OLTP系统              |
    | 计算 | 高主频CPU、最高性价比  | 高流量Web、MMO游戏、HPC                    |

### 2.1.3 云服务器镜像

* 定义
  * 创建云服务器的模板，提供操作系统和软件配置
* 作用
  * 批量部署
  * 特定软件部署
  * 运行环境备份
* 镜像类型
  * 公有
  * 服务市场
  * 自定义
  * 共享
* 镜像优势
  * 部署时长： 3 -5 min
  * 过程：快速创建合适和云服务器
  * 安全性：测试审核、安全加固
  * 适用情况：四种镜像

### 2.1.4 云服务器存储

* 介质
  * 普通云硬盘
  * 高性能云硬盘
  * SSD云硬盘
* 场景
  * 系统盘
  * 数据盘
* 架构
  * 本地盘
  * 云硬盘
  * 对象存储

### 2.1.5

* 虚拟主机 > 独立主机 > VPS > 云服务器



### 2.2.1 CVM (Cloud Virtual Machine)

* 弹性伸缩的计算服务
  * 弹性伸缩，分钟
  * 灵活配置，CPU、内存、带宽
  * 稳定可靠，3副本
  * 管理简单，API/CLI/控制台
  * 安全网络，VPC/ACL/安全组
  * 全面防护，木马/漏洞/破解
* 业务，电商
  * 需求
    * 突发流量井喷
    * 业务保障、成本控制
  * 方案
    * 标准CVM、镜像，S2 1C1G
    * 弹性伸缩组：闲时减实例，忙时增实例

### 2.2.2 GPU

* 高速并行计算和浮点计算
* 高并行、高吞吐、低时延，科学计算性能比传统架构高50倍
* CPU：几十个核心、复杂逻辑控制单元、强大的算术逻辑单元、逻辑控制、串行运算
* GPU：数千个加速核心，众多ALU、多线程超大并行，计算密集，并行计算

* 计算型GPU
  * 深度学习：训练和推理、图像、语音识别
  * 科学计算：建模、基因组、金融
  * 视频编码：高清视频编码
* 渲染型GPU
  * 图形工作站：动画、游戏、建模
  * 非线性编辑：电源特效
* 需求
  * AI算法建模
  * 高计算能力
* 方案
  * GPU实例 Tesla M40 GDDR5 24GB
  * 缩短深度学习和训练时间
  * 避免采购昂贵硬件



### 2.2.3 FPGA (Field Programmable Gate Array)

* **现场可编程阵列**的计算服务
* FPGA 镜像在几min内部署实例，实现硬件加速
* 3种类型
  * FX2.7xlarge60  		1 14C60GB
  * FX2.14xlarge120      2 28C120GB
  * FX2.28xlarge240      4 56C240GB
* 优势
  * 硬件加速，协同执行，运行速度比CPU快20倍
  * 硬件可编程，FPGA可重复编程，自定义硬件加速
  * 产权交易平台，统一规范和安全可靠的FPGA硬件平台和服务市场
* 场景
  * 深度学习
  * 实时图像压缩处理



### 2.2.4 专用宿主机CDH CVM Dedicated Host

* 独享主机资源、搭建平台、创建主机
* 优势
  * 物理隔离
  * 资源独享
  * 安全合规
  * 灵活配置
* 场景
  * 金融业务：安全合规
  * 高性能业务：资源独享



### 2.2.5 黑石 CPM

* 黑石物理服务器 Cloud Physical Machine
  * 按需购买、按量付费的物理服务器租赁服务
  * 云端专用、高性能、安全隔离的物理集群
* 黑石 Stack-V，深度整合VMware
  * 混合云
  * 深度整合VMware套件，包括vSphere6.5、vSAN6.6、NSX6.3等，VMware许可
  * 通过互联网，整合云产品
* 黑石 ARM，CPM for ARM
  * 需求：移动端游戏真机测试
  * 方案：黑石ARM实例，运行android模拟器，测试
* 黑石 OpenPOWER，CPM for OpenPOWER
  * 需求：大数据处理、高并发IO，大内存、高速传输
  * 黑石OpenOPWER，高主频、并发线程多、内存带宽大、缓存大



### 2.3.1 云服务计费模式

* 购买渠道
  * 官网Portal购买，控制台
  * API购买
* 模式
  * 包年包月 PrePaid
  * 按量付费 PostPaid
  * 阶梯计价、越多越省，量越大、时间越长、单价越低
* 价格计算器
  * 产品选型配置，价格计算，直接购买，导出清单
* 包年包月
  * 一次支付一个月或多月、多年的费用
  * 退款，五天无理由
  * 场景，低成本、长期、稳定
  * 流程
    * 选购 - 订单 - 账单 - 到期处理 - 续费
  * 停服回收
    * 到期预警，前7-前1天，续费通知，自动续费不足通知
    * 欠费预警，到期当天，断网关机保留数据，系统通知
    * 资源停服，当期当天-后7天，联系客服续费恢复
    * 资源销毁，到期后8天，清除数据销毁资源，不可恢复
* 按量付费
  * 后付费，一定结算周期
  * 业务波动大，资源使用临时性、突发性
  * 流程
    * 充值 - 开通 - 冻结 - 解冻 - 账单 - 欠费 <
  * 冻结机制
    * 系统根据结算周期和历史使用情况，预估冻结一定的余额，下次结算或资源释放时解冻
    * 月结
      * 每月计算日，解冻之前的费用，并扣费
      * 再次计算冻结费用
        * 设备资源：上月底Last day实际使用云服务量 X 30 X 单价
        * 流量类资源：上月费用的X1或X1.2
      * 调整配置，先解冻，在按照新配置冻结
      * 资源释放，下月结算日3号，解冻
    * 时结/日结
      * 购买，冻结1~2个结算周期的费用
      * 调整配置，先解冻，在按照新配置单价冻结
      * 资源释放，下月结算日3号，解冻
    * 回收机制
      * 生成账单，结算周期，生成账单进行扣费，余额不足进入欠费状态；
      * 欠费保护，时：2小时，天：1天，推送欠费提醒，继续使用；冲正前，不能新开通服务
      * 欠费停服，时：24小时，天：30天，系统推送停服通知，资源被强制关停；充值后，控制台重新启动；冲正前，不能新开通服务
      * 欠费回收，超过欠费停服期，销毁回收，不可恢复；冲正前，不能新开通服务
    * 限制
      * 不支持代理商代父
      * 不支持代金券
      * 不支持5天无理由
      * 不支持切换包年包月



### 2.3.4 计费方案

* CVM 费用 = 实例费用（CPU+Mem）+ 存储费用 + 带宽费用
* 模式
  * 包年包月
    * 预付
  * 按量计费
    * 后付费，按秒，按小时
    * 阶梯：0 < T1 <= 96H <= T2 <= 360H < T3
    * 部分不支持关机不收费
* 方案
  * 包年包月
    * 元/月
    * 单价低
    * 使用一个月
    * 升配无限制，降配5次
  * 按量计费
    * 元/秒
    * 初始单价高，阶梯降价，96小时，360小时，使用15天后，单价基本接近包年包月
    * 按秒计费，按小时结算
    * 随时升降配置，无限制
* 实例购买限额
  * 包年包月150，100（新加坡1，多伦多1，硅谷1）
  * 按量付费30，20（香港1，多伦多1，硅谷1）
* 云服务器计费方案
  * CVM，包年包月、按秒、按时
  * GPU，包年包月、按秒、按时
  * FPGA，内测
  * CDH，包年包月
  * CPM黑石，包年包月、按秒、按时



# III. 网络产品

### 3.1.1 私有网络VPC

* **Virtual Private Cloud**, 是用户自定义的，逻辑隔离的专属云上网络空间
  * 不同VPC完全逻辑隔离
  * SDN的方式管理VPC、实现IP地址，子网、路由表、网络ACL、流日志
  * 多种连接，弹性IP，NAT网关，VPN
* 私有网络连接
  * 每个私有网络内的服务资源内网互通
  * 不同VPC之间内网默认不通
  * 用 ”对等连接“ 和 ”云联网“ 实现同一个账户下的VPC子网互通
* VPC内部
  * 自有定义网段划分、IP、路由策略，部署云服务器、LB、云数据库
  * **对等连接和基础网络互通功能**，连接内网资源，实现同服和两地三中心容灾
  * ACL和安全组，保证网络安全性
* VPC
  * 自定义网络
    * 自定义 **网段、子网、路由策略**，部署服务
  * 灵活、高性能访问
    * **性IP、NAT网关和公网网关** 访问Internet
  * 稳定可靠的数据中心连接
    * 混合云，连接云上计算资源和本地数据中心，使用 **公网VPN** or **专线** 接入
  * 灵活互通
    * **对等连接和基础网络互通** 实现私有网络的资源互通
  * 多维度安全
    * **网络ACL和安全组** 实现端口和实例维度的资源访问控制

### 3.1.2 VPC网段

* 私有网段

  * 10.0.0.0 - 10.255.255.255 [掩码16-28]
  * 172.16.0.0 - 172.31.255.255 [掩码16-28]
  * 192.168.0.0 - 192.168.255.255 [掩码16-28]

* 子网

  * 云资源部署在子网内，CVM和CDB
  * 通过DHCP获取私有IP，不能在公网路由
  * 每个子网可用IP数量，2^n - 3 （n为主机位的位数）

* CIDR (Classless Inter-Domain Routing)

  * 支持「私有网段」中的任意一个

* 子网

  * 一个VPC至少有一个子网组成，子网的CIDR必须在VPC的CIDR内，VPC的所有云资源必须部署在子网内
  * VPC具有地域（Region）属性
  * 子网具有可用区（Zone）属性
  * 一个私有网络下的子网属于该地域的不同可用区
  * 同一VPC下各子网内资源默认互通

* 默认私有网络和子网

  * 默认私有网络和自行创建的私有网络功能完全一致
  * 默认VPC不会占用某个地域下的VPC配额，不需要默认VPC和子网可自行删除

* 子网划分

  * | <u>xxxx xxxx.</u> | <u>xxxx xxxx.</u> | <u>xxxx xxxx.</u> | <u>xxxx xxxx.</u> | xxxx xxxx. |
    | ----------------- | ----------------- | ----------------- | ----------------- | ---------- |
    | 子                | 网                | 掩                | 码 **[24]**       | 主机位     |

  * 子网划分

    * 通过设置子网的位数，来决定可用的子网数和主机IP数
      * 子网位数为m，主机位数为2^(32-m) - 3
      * 10.3.5.7/24
        * 主机数量=2^(32-24) - 3
        * 网络地址10.3.5.0，广播10.3.5.255

### 3.1.3 VPC路由表

* VPC内互通，不同VPC内网不通，通过路由表实现子网间、子网与外部的路由通信
* 路由表
  * 每个私有网络有一个默认路由，用户可以创建自定义路由表；
  * 由多条路由策略组成
  * 用于控制VPC内子网的出流量方向
  * 每个子网只能关联一个路由表，一个路由表可以关联多个子网
  * 分类
    * 默认路由表
      * 创建VPC自动生成
      * 新建子网自动关联默认路由表
      * 添加删除修改路由策略，无法删除默认路由
    * 自定义路由表
      * 可以删除
      * 为相同策略的子网，创建一个路由表，将路由协议与所有子网关联
      * 创建时关联、创建后关联
* 路由策略
  * 目的端
    * 目的网段
    * 不能为路由表所在VPC的IP段，Local路由已经表示过此VPC内网默认互通
  * 下一跳类型
    * 数据包出口，支持类型：NAT网关、云服务器等
  * 下一跳
    * 指定具体跳转的下一跳实例，ID标识
* 路由策略优先级
  * 多条策略，由高到低
    * 私有网络内流量
    * 最精确路由（最长前缀匹配，优先匹配掩码最长的路由策略并确定下一跳）
    * 公网IP



### 3.1.4 VPC 访问控制

* ACL **(Access Control List)**

  * 控制进出子网的数据流
  * 子网级别无状态的可选安全层
  * 协议和端口

* 安全组

  * 配置放通和拒绝的端口/协议
  * 有状态的包过滤功能的虚拟防火墙，用于设置云服务器的实例级别的网络访问控制
  * 安全隔离手段

* | 安全组                           | ACL                                             |
  | -------------------------------- | ----------------------------------------------- |
  | CVM实例级别的流量控制 【第一层】 | 子网级别的流量控制 【第二层】                   |
  | 放通和拒绝的端口/协议            | 放通和拒绝的端口/协议                           |
  | 有状态：返回数据被自动允许       | 无状态：返回数据必须明确规则                    |
  | 启动CVM，指定安全组，关联实例    | 自动应用到子网内的所有CVM实例，可以做备份安全层 |



### 3.1.5 弹性网卡

* **ENI [Elastic Network Interface]**
* 绑定私有网络云服务器的弹性网络接口，可以自有迁移
* 优势
  * 多网卡
  * 网络隔离
  * 灵活迁移
* 绑定多个ENI，实现HA
* 单个ENI绑定多个IP，实现单机多IP
* 多网卡
  * 创建时自动生成的网卡
  * 主持绑定多个辅助弹性网卡
  * 弹性网卡可以属于同一个VPC下的不同子网
  * 支持独立的安全组
  * 配置独立的路由和转发策略
* 灵活迁移
  * 自由地在同VPC和同可用区下的云服务器之间自由迁移
  * 绑定，保留内网IP、弹性公网IP，安全组策略
  * 迁移后无需重新配置关联关系
* 网络隔离
  * 绑定同VPC可可用区的不同子网的弹性网卡，设定独立的路由转发策略，实现隔离
  * 云服务器内设定策略，失信特定目的端的流量指向不同的网卡



### 3.2.1 网络连接

* 对等连接
  * 不同VPC之间内网互通
* 云联网
  * 不同VPC之间内网互通
  * 私有网络接入私有数据中心
* 弹性IP、NAT网关、公网网关
  * 访问公网
* VPN
  * 私有网络接入私有数据中心
* 专线
  * 私有网络接入私有数据中心
* 基础网络互通
  * 基础网络和私有网络内网通信
* 安全组和ACL
  * 多维度网络安全



### 3.2.2 公网接入

* VPC里的服务器，绑定公网IP来实现

  * 普通公网IP，CVM上申请绑定，解绑后释放，无法找回
  * 弹性公网IP，EIP
    * 关联帐号，解绑保留，重新绑定
    * 提供外网访问能力
    * EIP，独立申请，支持CVM/NAT网关实例动态绑定和解绑
    * 释放
      * 用户控制台/API释放
      * 欠费释放，余额小于0且超过2小时，免费保留24H，24+2H后释放

* 公网网关

  * 是开启了转发功能的主机
  * 通过不同子网的公网网关访问Internet
  * 做源地址转换
  * 购买是没有勾选，则购买后无法切换
  * 有公网流量转发功能，为其他云主机转发，公网IP的主机没有转发能力

* 公网网关所在子网

  * 只能转发 **非所在子网** 的路由转发请求，不能与使用网关的服务在一个子网下

* NAT网关

  * 通过IP地址转换提供Internet访问
  * SNAT，源地址转换
  * DNAT，目的地址转换
  * 网关流量、流量高级、共享带宽包

* NAT [NAT Gateway]

  * IP地址转换的网络云服务
  * 访问Internet
  * 不暴露公网
  * IP流量管理，异常流量定位
  * 海量并发
  * SNAT [Source Network Address Translation]
    * 同一公网IP访问，支持5GB
  * DNAT [Destination Network Address Translation]
    * 将内网IP、协议、端口映射成外网IP、协议、端口，是云服务器能被外网访问
  * 网关监控
    * 限制内IP和NAT带宽
  * 流量告警
    * 阈值告警
  * 共享带宽包
    * 多个IP共享公网带宽，不同流量错峰
  * 安全高仿
    * BGP做DDoS和CC防护，最高310Gbps防护
  * 自动容灾
    * 双机热备、自动容灾
    * 单机故障自动切换，业务无感知
    * 可用性高达99.99%

* 公网接入的对比

  * NAT vs 公网网关 的优势

    * 大容量
    * 双机热备高可用
    * 省成本
    * 使用约束
      * 公网网关最大100Mbps，可以购买形成出口集群
      * 通过路由表汇总配置目的端路由，转发流量可以在网关间LB
      * 公网网关不支持NAT接入
      * 专线网关、VPN网关不支持NAT接入
      * 网关子网和普通子网不能关联到同一张路由表，需要新建

    | NAT                  | 公网网关              |
    | -------------------- | --------------------- |
    | 双机热备、自动热切换 | 手动故障切换          |
    | 带宽最大5G           | 取决于与服务器带宽    |
    | 最多绑定10个弹性IP   | 1个弹性IP或普通公网IP |
    | 无限速               | 云服务器限速          |
    | 最大1000万连接       | 50万                  |
    | 不占VPC内网IP        | 内用内网IP            |
    | 不支持安全组         | 支持安全组            |



### 3.2.3 DC连接

* **Direct Connect** 专线
  * 物理专线
  * 专用通道
  * 专线网关
  * 多地域
  * 多端口协议，100Base-T,1000Base-T, 1000Base-LX, 10GBase-LR 四种端口，MSTP，SDH，OTN，DWDM多种协议
  * 双线接入
  * NAT
* VPN
  * 安全加密网络隧道
  * IKE，IPsec数据加密
  * 监控告警
    * 无需额外收费

### 3.2.4 对等连接

* 大带宽、高质量互通服务
  * 多VPC，多地域，多账户异构
  * 5GB以上



### 3.2.5 云联网

* 内网互联、全网互联、学习调度、路由自动下发



### 3.3.1 CLB

* Cloud Load Balancer



### 3.3.2 流量分发算法

* 四层负载均衡
  * TCP、UDP，端口+VIP转发
* 七层
  * HTTP和HTTPS，基于内容转发
* 算法
  * 加权轮训算法
  * 加权最小连接数算法
  * 源地址散列算法
* 公网负载均衡
* 内网负载均衡
* 流量分发
  * 接入层服务器，配置一致的Docker容器承载
* 横向扩展，Autoscaling动态伸缩组



### 3.3.4 CLB+CDN

* 通过CLB+CDN将不同的流量分发到对应集群
* 业务分离



## 3.4 网络计费

* 免费
  * 内网同地域免费，不同子网通信，同地域连接免费；
  * 普通公网IP免费
  * 帮定CVM或NAT的弹性IP
* 收费
  * 为绑定CVM和NAT的弹性IP
  * 闲置的EIP，计算到S，闲置费用 0.2 * (xs/3600)
* 公网网关本质是云服务器实例
* NAT
  * 网关费用+Internet流量费用
  * 共享带宽包，按照整体结算，出带宽产生高额费用
  * BGP线路
  * 带宽计费
    * 公网传输速率 Mbps 计费
    * 包年包月、按带宽使用时长计费
  * 流量计费，总流量GB