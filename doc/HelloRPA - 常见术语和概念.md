# HelloRPA - 常见术语和概念



## 一、 文档与项目周期术语 (Documentation & Lifecycle)



在 RPA 项目的实施周期中，文档至关重要，它们定义了“机器人要做什么”以及“怎么做”。



### 1. 核心文档



| **缩写**    | **全称**                                 | **中文名称**         | **详细解释**                                                 |
| ----------- | ---------------------------------------- | -------------------- | ------------------------------------------------------------ |
| **PDD**     | **Process Design Document**              | **流程设计文档**     | **(业务视角)** 这是项目初期最重要的文档。通常由 BA（业务分析师）编写。它详细描述了业务流程的 **As-Is**（当前人工操作现状）和 **To-Be**（未来机器人操作流程）。包括每一步点击哪里、判断逻辑是什么、异常怎么处理。 |
| **SDD**     | **Solution Design Document**             | **解决方案设计文档** | **(技术视角)** 由 RPA 开发人员或架构师编写。它基于 PDD，将业务逻辑转化为技术语言。比如：使用什么变量、涉及哪些应用程序、架构图、错误处理机制、日志记录标准等。 |
| **DSD**     | Development Specification Document       | 开发规范文档         | 有时作为 SDD 的替代或补充，详细说明代码层面的规范。          |
| **ODI/PDI** | Operational / Process Design Instruction | 操作指导书           | 有时用于指代更细颗粒度的操作手册，指导机器人运维人员如何管理该流程。 |



### 2. 项目管理常用术语



- **POC (Proof of Concept - 概念验证):** 在正式立项前，先做一个小型的 demo，证明 RPA 技术能解决该业务痛点，且技术上可行。
- **ROI (Return on Investment - 投资回报率):** 企业做 RPA 最看重的指标。计算公式通常涉及：节省的工时（FTE） vs 软件许可费+开发维护成本。
- **FTE (Full-Time Equivalent - 全时当量):** 衡量节省人力的单位。1.0 FTE 代表节省了一个全职员工的工作量。
- **UAT (User Acceptance Testing - 用户验收测试):** 开发完成后，由业务人员（User）亲自测试机器人，确认机器人跑出的结果符合预期。
- **Hypercare (特护期):** 机器人上线（Go-Live）后的最初几周，开发人员需密切监控，随时准备修复潜在的 Bug。

------



## 二、 RPA 核心组件架构 (Core Components)



 `Creator`, `Runner`, `Control Room` 是 RPA 的“三驾马车”。尽管不同厂商（UiPath, Automation Anywhere, Blue Prism, 影刀等）叫法不同，但逻辑完全一致。

我们可以将其抽象为：**设计端、控制端、执行端**。



### 1. 设计端 (The Developer Tools)



- **常见叫法:** Creator (AA), Studio (UiPath), Studio (Blue Prism), Designer.
- **功能:** 这是开发人员使用的 IDE（集成开发环境）。
- **作用:**
  - 通过拖拽组件（Activities）编写流程代码。
  - 录制屏幕操作。
  - 进行本地调试（Debug）。
  - 生成发布包。



### 2. 控制端 (The Central Brain)



- **常见叫法:** Control Room (AA/Blue Prism), Orchestrator (UiPath), Console.
- **功能:** 这是一个 Web端的管理平台，是整个 RPA 架构的大脑。
- **核心作用:**
  - **部署 (Deployment):** 接收设计端发布的流程包。
  - **调度 (Scheduling):** 设定机器人什么时候干活（例如：每天凌晨 2 点运行财务报表流程）。
  - **资产管理 (Assets):** 安全地存储密码（Credential Vault）、配置项、队列数据（Queues）。
  - **监控与日志 (Monitoring & Logs):** 监控机器人是否在运行，查看运行日志，如果报错则发送警报。



### 3. 执行端 (The Robot)



- **常见叫法:** Runner / Bot Agent (AA), Robot (UiPath), Resource PC (Blue Prism).
- **功能:** 安装在具体电脑或虚拟机（VM）上的运行时环境。
- **分类 (非常重要):**
  - **Attended Robot (有人值守机器人):** 像“私人助理”。安装在员工的电脑上，由员工手动触发，机器人和人协同工作（人做判断，机器人做繁琐录入）。
  - **Unattended Robot (无人值守机器人):** 像“后台批处理工”。安装在机房的服务器/虚拟机上，由控制台（Control Room）定时触发，无需人工干预，7x24小时工作。

------



## 三、 RPA 基础架构与扩展概念



理解了三大组件后，我们来看看它们是如何连接的，以及一些进阶概念。



### 1. 典型的 RPA 部署架构



想象一个三角形关系：

> **
>
> ![Architecture Flow的图片](https://encrypted-tbn0.gstatic.com/licensed-image?q=tbn:ANd9GcSo9a3MbDQKil1Gv3pOYStusAELCm7mpm1H-JYlXOjcWcab7SQba8UkkrBO5nLhsEiK6ujqZ2EfEAgjvaR7aWWmqgeyg6VaJeMyF-yb_n0Uj6xnbLc)
>
> Getty Images
>
> 探索



**

> 1. **开发人员**在 PC 上用 **Studio (Creator)** 写好代码，点击“发布”。
> 2. 代码包上传到了服务器上的 **Control Room**。
> 3. **Control Room** 根据预设的时间表，向 **Robot (Runner)** 发送指令。
> 4. **Robot** (位于虚拟机 VDI 中) 收到指令，自动打开 Excel/SAP/浏览器开始工作，并将结果汇报给 Control Room。



### 2. 关键扩展术语



- **VDI (Virtual Desktop Infrastructure):** 虚拟桌面基础架构。企业通常不把无人值守机器人装在物理机上，而是装在 VDI 中（如 Citrix, VMware Horizon）。这容易管理且安全。
- **OCR (Optical Character Recognition):** 光学字符识别。让机器人“看懂”图片或扫描件（如发票识别）。
- **Cognitive Automation / AI-RPA:** 认知自动化。传统 RPA 只能做规则固定的事（手脚），加上 AI（NLP、机器学习）后，机器人能处理非结构化数据（如读懂邮件意图、分类文档），相当于有了“大脑”。
- **Queue (事务队列):** 一种处理大量数据的架构模式。
  - *场景:* 有 1000 个订单要处理。
  - *做法:* 调度器（Dispatcher）把 1000 个订单扔进 Control Room 的 Queue 中。然后启动 5 个机器人（Performer），每个机器人从 Queue 里拿订单处理。这能实现**负载均衡**。
- **REFramework (Robotic Enterprise Framework):** UiPath 的一种标准化开发框架，但其理念被广泛采纳。它强调**状态机**结构（初始化 $\rightarrow$ 获取数据 $\rightarrow$ 处理数据 $\rightarrow$ 结束），并内置了强大的异常处理和重试机制。



### 3. 常见技术架构类型



- **On-Premise (私有化部署):** Control Room 部署在企业自己的内网服务器上，数据最安全，但维护成本高。
- **Cloud (云部署):** 使用厂商提供的 SaaS 版 Control Room（如 UiPath Automation Cloud），企业只需安装本地 Robot 即可，开箱即用。
- **Hybrid (混合模式):** 控制端在云上，数据处理和执行端在本地，兼顾灵活性和合规性。

------



### 总结



- **PDD/SDD** 是沟通业务与技术的桥梁。
- **Creator** 是画笔，**Control Room** 是指挥塔，**Runner** 是干活的工人。
- 区分 **Attended** (人机协同) 和 **Unattended** (全自动) 是架构设计的核心。

