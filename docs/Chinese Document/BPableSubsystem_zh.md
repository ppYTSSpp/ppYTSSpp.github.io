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

> 这里以BPable_GameInstanceSubsystem为例

- 打开项目的插件设置

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 175348.jpg)



- 确保BlueprintableSubsystem插件启用![](../resource/BPableSubsystem/屏幕截图 2022-09-02 180005.jpg)

- 在内容浏览器中创建蓝图类，并选取BPable_GameInstanceSubsystem为父类

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 214111.jpg)

- 创建成功后打开你创建的游戏实例子系统蓝图类进行编辑

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 220403.jpg)

- 在其他蓝图类中使用Get Subsystem通用节点调用你创建的蓝图子系统

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 220615.jpg)

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 220633.jpg)

## 蓝图子系统相关接口

### 游戏实例子系统蓝图类

|         名称          |                             图示                             |                             解释                             |
| :-------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|      Initialize       | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221009.jpg) |                   此子系统创建后调用的事件                   |
|     Deinitialize      | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221033.jpg) |               此子系统被GC标记销毁前调用的事件               |
| ShouldCreateSubsystem | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221053.jpg) | 此子系统创建前调用的函数，用于判断是否要创建该子系统单例。  可以不实现，不实现该接口时默认为创建。<br>实现时，若返回值为false则不创建，若返回值为true则创建。请留意 |
|    GetGameInstance    | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221152.jpg) |      获取游戏实例子系统的Outer，即游戏实例UGameInstance      |

---

### 本地玩家子系统蓝图类

|           名称           |                             图示                             |                             解释                             |
| :----------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|        Initialize        | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221009.jpg) |                   此子系统创建后调用的事件                   |
|       Deinitialize       | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221033.jpg) |               此子系统被GC标记销毁前调用的事件               |
|  ShouldCreateSubsystem   | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221053.jpg) | 此子系统创建前调用的函数，用于判断是否要创建该子系统单例。  可以不实现，不实现该接口时默认为创建。<br>实现时，若返回值为false则不创建，若返回值为true则创建。请留意 |
| GetLocalPlayerController | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 222223.jpg) | 通过本子玩家子系统的Outer，即ULocalPlayer，获取ULocalPlayer对应的APlayerController。 |

---

### 场景子系统蓝图类

|         名称          |                             图示                             |                             解释                             |
| :-------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|      Initialize       | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221009.jpg) |                   此子系统创建后调用的事件                   |
|    PostInitialize     | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 222639.jpg) |       此所有UWorldSubsystem调用Initialize后调用的事件        |
|    WorldBeginPlay     | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 222658.jpg) | 此当World准备好开始Gameplay、Gamemode转换到正确状态前和调用所有的Actor的Beginplay前调用的事 |
|     Deinitialize      | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221033.jpg) |               此子系统被GC标记销毁前调用的事件               |
| ShouldCreateSubsystem | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221053.jpg) | 此子系统创建前调用的函数，用于判断是否要创建该子系统单例。  可以不实现，不实现该接口时默认为创建。<br>实现时，若返回值为false则不创建，若返回值为true则创建。请留意 |

- 当前版本存在问题

  当你创建该子系统的蓝图类时，当退出编辑器时，编辑器会报错并崩溃。

  但正常执行游戏时并不会出现问题（暂时未发现）