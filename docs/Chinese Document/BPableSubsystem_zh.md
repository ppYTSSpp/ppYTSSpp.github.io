---
sort: 1
---

# 可蓝图化的子系统

## 插件简介

本插件提供了三个可蓝图继承的子系统：

BPable_GameInstanceSubsystem

BPable_LocalPlayerSubsystem

BPable_WorldSubsystem

![可蓝图继承的子系统](../resource/BPableSubsystem/屏幕截图 2022-09-02 171703.jpg)

> 图中Get到的BPable子系统的这种用法**非法**，关于该插件的使用方法在下文。上图仅仅时展示作用

用户直接通过蓝图继承这三个类就可以获得蓝图子系统。

## 快速启用

> 这里以BPable_Subsystem为例

- 打开项目的插件设置

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 175348.jpg)



- 确保BlueprintableSubsystem插件启用

![](../resource/BPableSubsystem/屏幕截图 2022-09-02 180005.jpg)

- 在内容浏览器中创建蓝图类，并选取BPable_GameInstanceSubsystem为父类
- 创建成功后打开你创建的游戏实例子系统蓝图类进行编辑
- 在其他蓝图类中使用Get Subsystem通用节点调用你创建的蓝图子系统

## 蓝图子系统相关接口

### 游戏实例子系统蓝图类

- 可实现的接口

### 本地玩家子系统蓝图类

- 可实现的接口

### 场景子系统蓝图类

- 可实现的接口
- 当前版本存在问题