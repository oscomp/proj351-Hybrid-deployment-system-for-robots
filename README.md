# proj351-Hybrid-deployment-system-for-robots
# 基于异构多核平台的机器人混合部署系统及实时优化

## **项目描述**

ROS (Robot Operating System)是一个开源、灵活的机器人软件开发框架，它提供了构建机器人应用程序的库、工具和通信基础设施。ROS的设计目标是使机器人软件开发更加模块化、可重用、可维护和可扩展。它提供了一套通用的机器人操作系统功能，包括硬件抽象、设备驱动、库和工具，以及一种用于组合和编写机器人软件的通用方法。

Hypervisor（虚拟机监控程序），也被称为虚拟机管理程序或VMM，是一种系统软件，它允许在同一台物理计算机上运行多个虚拟机（VM）。 Hypervisor在物理计算机和VM之间提供一个抽象层，它可以管理和分配物理计算机资源（如CPU、内存、存储和网络）给每个VM，同时隔离VM之间的资源，从而使每个VM看起来像一台独立的计算机。Hypervisor有两种类型：Type 1和Type 2。Type 1 Hypervisor，也被称为本地Hypervisor或裸机Hypervisor，直接安装在物理计算机上，而不需要操作系统作为中间层。

unikernel是一种轻量级操作系统架构，它的设计目标是将操作系统内核与应用程序合并为一个单一的可执行文件，从而最大程度地减少操作系统的大小和复杂性，并提高性能和安全性。该架构通常基于虚拟化技术，它可以直接在裸机上运行，也可以运行在VM中。unikernel通常被认为是面向容器和微服务的理想选择，因为它的轻量级和高性能可以提供更快的启动时间和更好的资源利用率。

基于ROS节点可拆分和Type-1 Hypervisor对虚拟机隔离的特性，将ROS中的实时任务和非实时任务区分开。使用现有的一种虚拟机监控器——Shyper将其隔离到不同的VM中，使得非实时且复杂的ROS节点运行在一个VM上；将实时任务放在其他VM上，通过Shyper资源直通的方式，让该VM独占某些资源，从而提高该系统处理实时任务的能力；甚至可以基于unikernel的高性能和Rust语言的内存和线程安全特征，将实时任务运行在一个基于Rust的unikernel架构操作系统上。通过Shyper将ROS的任务隔离到不同的VM之后，需要修改ROS底层的通信原理，配合Shyper进行优化，通过上述手段，来优化机器人的实时任务，降低时延并且提高系统的安全可靠性。

## **参考资料：**

（1）type-1 hypervisor——Shyper：https://gitee.com/openeuler/rust_shyper

（2）uniKernel参考：https://fr.wikipedia.org/wiki/Unikernel

（3）Linux下部署ROS1 melodic，参考：http://wiki.ros.org/melodic/Installation/Ubuntu。

（4）Integrating ROS and ROS2 on mixed-critical robotic systems based on embedded heterogeneous platforms：https://roscon.ros.org/2018/presentations/ROSCon2018_integratingrosandros2onmixedcriticalityroboticsystems.pdf

（5）使用Rust支持ROS runtime：https://github.com/adnanademovic/rosrust

## **所属赛道**

2025全国大学生操作系统比赛的“OS功能挑战”赛道

## **参赛要求**

- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生或研究生 
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
- 请遵循“2025全国大学生操作系统比赛”的章程和技术方案要求

## **项目导师**

韩宗成 hanzongcheng@huawei.com

## **赛题分类**

未归类的应用（如机器人、无人机等）

## **难度**

中等 ~ 高等。

## **特征：**

1. ROS应用使用Rust或C++或Python语言实现
2. 支持在真实搭载RK3588、Jetson Nano、Jetson Tx2等实体开发板的小车上运行
3. 时延低于ROS1原生环境
4. 为了兼容Shyper社区开源协议，License建议为：Mulan PSL v2

## **预期目标**

#### **注意：下面的内容是建议内容，不要求必须全部完成。选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标**

#### **注：为了避免重复造轮子，本项目既可以从头开发，也可以联系导师在其项目基础上进行进一步的开发**

1. 能够在搭载实体开发板的机器人上基于Linux系统运行ROS(ROS1, ROS2均可)，使其支持小车遥控、建图和导航等的功能。
2. 能够在搭载实体开发板的机器人上运行Shyper，使其支持启动至少两个虚拟机
3. 能够剥离机器人的实时任务，并能在不同VM上运行
4. 了解ROS1通讯原理，基于Shyper对实时支持进行优化
5. 搭建的基于 Hypervisor的ROS控制框架可以在无人车上部署，并提供实际测试结果验证对ROS框架优化的效果
6. 基于现有的unikernel，搭架ROS的运行环境，使其能够支持ROS应用（可选拓展）
7. 基于Rust自行实现一个支持网络协议栈的unikernel，并完成上述功能（可选拓展）
