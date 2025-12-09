# HelloRPA

## 项目目的

RPA从业5年， 本项目用于记录及分享RPA领域相关知识。期望让感兴趣的同学可以快速了解这个领域。 



## 什么是RPA

 Robotic process automation (RPA) 即机器人流程自动化。

* Robotic 区别于物理机器人， 可以理解为软件机器人、数字员工。 在RPA的世界，你编写的RPA程序可以独立运行，并像人一样自动化的工作。
* Process 即流程， RPA机器人目的一般为进行某些流程步骤的处理。 比如ERP的操作、Excel的处理、审批流等。 具体一点，比如HR的入职流程，需要进行简历的归档、入职通知邮件的发送、ERP或E-HR系统的信息录入、社医保购买、公积金购买一套流程都可以使用RPA来完成。 
* Automation 即自动化， 区别与人工处理， RPA可以实现流程的自动化，也可以实现简单的人机交互。



关于什么是RPA， techtarget上有篇文章讲的很好，大家可以参考 [本链接](./reference/What_is_RPA.pdf)。



## RPA的特性是什么

在当下多种编程语言流行的环境下，为什么还需要RPA， 它有何过人之处？

我们首先看下哪些场景适合RPA：

* **有规则的**
* **重复的**
* **稳定不易变化的**
* **大量的**

如上述HR入离职流程即符合相关条件， 某客户有近10W员工，高峰期每天入职近千人。HR同事需要对每位入职员工走固定的流程，在邮件、纸质文档、Excel文件、EHR系统（ERP）、政府社医保公积金系统间流转完成入职流程。 HR陷入大量重复的工作中，不断的在各种系统资料中操作，而且容易出错。 



### 桥梁： 解决信息孤岛

分析入职流程， 会发现上述流程难以自动化是因为各个系统是独立的，比如企业HR系统和政府间没有API接口需要进行Excel进行数据的导入导出， 纸质文档或邮件内容需要进行数字化、结构化才能进行数据流转。

所以RPA在这个过程中就是“桥梁”的作用，可以简单理解为数据的搬运工作。 

### 低代码

商业RPA厂商都提供了集成的开发平台， 可以使用拖拉拽快速完成流程的开发。 

区别于普通编程语言，需要使用特定的开发包， 阅读晦涩难懂技术文档完成开发。 RPA一般都有统一的界面拖拉拽， 每个包封装好了最常用的组件，可以实现快速开发， 一般RPA项目开发周期都在6个月以内。

### GUI自动化 + Web自动化

区别于其他编程语言， RPA集成了GUI自动化和Web自动化， 除了逻辑处理和API调用， RPA机器人可以直接在桌面程序GUI图形界面和浏览器之上工作，完成比如输入框输入、选择、按钮点击、滚动以及界面数据提取等操作。 



## 更多内容分篇介绍



1. [HelloRPA-常见术语和概念](doc/HelloRPA-常见术语和概念.md)- 100%
2. [HelloRPA-RPA厂商](doc/HelloRPA-RPA厂商.md) - 100%
3. HelloRPA-RPA+AI - 0%
4. [HelloRPA-RPA项目管理](doc/HelloRPA-RPA项目管理.md) - 100%
5. [HelloRPA-RPA流程定义文档PDD模板](doc/HelloRPA-RPA流程定义文档PDD模板.md) - 100%

5. [HelloRPA-RPA解决方案之验证码](doc/HelloRPA-RPA解决方案之验证码.md) - 100%
6. HelloRPA-RPA解决方案之HR - 0%
7. HelloRPA-RPA解决方案之财务 - 0%



## 版权说明

本仓库内容采用 [知识共享 署名-非商业性使用 4.0 国际 许可协议 (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/deed.zh) 进行许可。

[![CC BY-NC 4.0][cc-by-nc-image]][cc-by-nc-shield]

* **允许**：自由阅读、下载、修改、分享。
* **禁止**：将本仓库内容用于商业目的（如付费培训、出版、商业转售等）。
* **条件**：转载或引用时请注明出处：[wangqichang/HelloRPA](https://github.com/wangqichang/HelloRPA)

[cc-by-nc-image]: https://licensebuttons.net/l/by-nc/4.0/88x31.png
[cc-by-nc-shield]: https://creativecommons.org/licenses/by-nc/4.0/deed.zh