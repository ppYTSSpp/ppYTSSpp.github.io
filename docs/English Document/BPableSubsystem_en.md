---
sort: 1
---

# BlueprintableSubsystem v0.7

- Translated by lpl

## The Profile of Plugin

This plugin provides six subsystems that can be inherited from blueprints：

BPable_GameInstanceSubsystem

BPable_LocalPlayerSubsystem

BPable_WorldSubsystem

BPable_TickableGameInstanceSubsystem

BPable_TickableLocalPlayerSubsystem

BPable_TickableWorldSubsystem

![可蓝图继承的子系统](../resource/BPableSubsystem/屏幕截图 2022-09-02 171703.jpg)

> This method of using  the BPable subsystem that you get in this figure is **illegal**, the proper usage of this plugin is explained down below. The picture above is only for demonstration

Users can obtain the blueprint subsystem by inheriting these base classes directly from the blueprint.

## Step-by-step usage guide

> Take BPable_GameInstanceSubsystem as an example

- Open the project's plugin Settings

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103246.jpg)

- Ensure that the BlueprintableSubsystem plugin is enabled

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103325.jpg)

- Create the blueprint class in the Content browser and select BPable_GameInstanceSubsystem as the parent class

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103359.jpg)

- Then open the blueprint class of the GameInstanceSubsystem you created and edit it

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103438.jpg)

- Call the blueprint Subsystem you created using the Get Subsystem general node in other blueprint classes

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103525.jpg)

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 220633.jpg)

## About BlueprintableSubsystem

###  Usage

In my Blueprint on the left side of the Blueprint class edit window click to override the corresponding function

![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103541.jpg)

### BPable_GameInstanceSubsystem

- Life time

  Follow its' Outer,which is also called UGameInstance.

- Interface

  | Name                  | Graphic                                                      | Explain                                                      |
  | --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | Initialize            | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103614.jpg) | A event called after this subsystem created                  |
  | WorldBeginPlay        | ![](../resource/BPableSubsystem/屏幕截图 2022-09-24 211903.jpg) | 此World开始执行BeginPlay时调用的事件                         |
  | WorldBeginTearDown    | ![](../resource/BPableSubsystem/屏幕截图 2022-09-24 211913.jpg) | 此World开始执行TearDown时调用的事件                          |
  | Deinitialize          | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103627.jpg) | A event called before this subsystem was destoryed           |
  | ShouldCreateSubsystem | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103638.jpg) | A function called before this subsystem created<br/> the Implementation of it is not necessary<br/>If implement this function,return true to create this subsystem,return false not to create this subsystem |

- Function

  | Name            | Graphic                                                      | Explain                                                      |
  | --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | GetGameInstance | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103659.jpg) | Get the Outer, or UGameInstance, of the game instance subsystem |

  

---

### BPable_LocalPlayerSubsystem

- Life time

  Follow its' Outer,which is also called ULocalPlayer.

- Interface

  | Name                  | Graphic                                                      | Explain                                                      |
  | --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | Initialize            | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103614.jpg) | A event called after this subsystem created                  |
  | WorldBeginPlay        | ![](../resource/BPableSubsystem/屏幕截图 2022-09-24 211903.jpg) | 此World开始执行BeginPlay时调用的事件                         |
  | WorldBeginTearDown    | ![](../resource/BPableSubsystem/屏幕截图 2022-09-24 211913.jpg) | 此World开始执行TearDown时调用的事件                          |
  | Deinitialize          | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103627.jpg) | A event called before this subsystem was destoryed           |
  | ShouldCreateSubsystem | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103638.jpg) | A function called before this subsystem created<br/> the Implementation of it is not necessary<br/>If implement this function,return true to create this subsystem,return false not to create this subsystem |

- Function

  | Name                     | Graphic                                                      | Explain                                                      |
  | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | GetLocalPlayerController | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103755.jpg) | Get the APlayerController Corresponding to ULocalPlayer from the Outer(ULocalPlayer) of local player's sub system ,  return null when implementing Initialize |

---

### BPable_WorldSubsystem

- Life time

  Following its' Outer，which is also called UWorld.Only appear in Game or PIE.

- Interface

  | Name                  | Graphic                                                      | Explain                                                      |
  | --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | Initialize            | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103614.jpg) | A event called after this subsystem created                  |
  | PostInitialize        | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103855.jpg) | A event called after all UWorldSubsystem calls Initialize    |
  | WorldBeginPlay        | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103911.jpg) | A event called when world is ready to start gameplay before the game mode transitions to the correct state and call BeginPlay on all actors |
  | Deinitialize          | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103627.jpg) | A event called before this subsystem was destoryed           |
  | ShouldCreateSubsystem | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103638.jpg) | A function called before this subsystem created<br/> the Implementation of it is not necessary<br/>If implement this function,return true to create this subsystem,return false not to create this subsystem |

------



### BPable_TickableGameInstanceSubsystem

- Life Time

  Inherited from UBPable_GameInstanceSubsystem. Please view relevant contents in the parent class.

- Class defaults

  | Name                 | Explain                                         |
  | -------------------- | ----------------------------------------------- |
  | IsTickEnabled        | Whether to enable Tick                          |
  | IsTickableThenPaused | Whether to enable Tick after the game is paused |

- Interface

  Some interfaces are Inherited from UBPable_GameInstanceSubsystem. Please view relevant contents in the parent class.

  | Name | Graphic                                                      | Explain                                                |
  | ---- | ------------------------------------------------------------ | ------------------------------------------------------ |
  | Tick | ![](../resource/BPableSubsystem/屏幕截图 2022-09-16 103926.jpg) | This event is called every frame after Tick is enabled |

- Function

  Some functions are Inherited from UBPable_GameInstanceSubsystem.Please view relevant contents in the parent class.

  | Name                          | Graphic                                                      | Explain                                                 |
  | ----------------------------- | ------------------------------------------------------------ | ------------------------------------------------------- |
  | SetTickEnabled                | ![](../resource/BPableSubsystem/屏幕截图 2022-09-24 212400.jpg) | To set whether to enable Tick                           |
  | IsSubsystemTickEnabled        | ![](../resource/BPableSubsystem/屏幕截图 2022-09-24 212410.jpg) | The enabled value   when return to tick                 |
  | SetTickableWhenPaused         | ![](../resource/BPableSubsystem/屏幕截图 2022-09-24 212419.jpg) | Set whether to tick when the game pause                 |
  | IsSubsystemTickableWhenPaused | ![](../resource/BPableSubsystem/屏幕截图 2022-09-24 212428.jpg) | Report a value that wherher to tick when the game pause |

### BPable_TickableLocalPlayerSubsystem

- Life Time

  Inherited from UBPable_LocalPlayerSubsystem. Please view relevant contents in the parent class.

- Class defaults

  Tick相关的类默认值和UBPable_TickableLocalPlayerSubsystem保持一致，请前往查看

- Interface

  Some interfaces are Inherited from UBPable_LocalPlayerSubsystem. Please view relevant contents in the parent class.

  Tick相关的事件和UBPable_TickableLocalPlayerSubsystem保持一致，请前往查看

- Function

  Some functions are Inherited from UBPable_LocalPlayerSubsystem. Please view relevant contents in the parent class.

  Tick相关的函数和UBPable_TickableLocalPlayerSubsystem保持一致，请前往查看

### BPable_TickableWorldSubsystem

- Life Time

  Inherited from UBPable_WorldSubsystem. Please view relevant contents in the parent class.

- Class defaults

  Tick相关的类默认值和BPable_TickableWorldSubsystem保持一致，请前往查看

- Interface

  Some interfaces are Inherited from UBPable_WorldSubsystem. Please view relevant contents in the parent class.

  Tick相关的事件和BPable_TickableWorldSubsystem保持一致，请前往查看

- Function

  Tick相关的函数和BPable_TickableWorldSubsystem保持一致，请前往查看
