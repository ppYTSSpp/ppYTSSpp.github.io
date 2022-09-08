---
sort: 1
---

# BlueprintableSubsystem

The corresponding plugin version is v0.5

## Plugin Profile

This plugin provides three subsystems that can be inherited from blueprints：

BPable_GameInstanceSubsystem

BPable_LocalPlayerSubsystem

BPable_WorldSubsystem

![可蓝图继承的子系统](../resource/BPableSubsystem/屏幕截图 2022-09-02 171703.jpg)

> This use of the BPable subsystem that you Get in the figure is **illegal**, and can be used with this plug-in below. The picture above is only for demonstration

Users can obtain the blueprint subsystem by inheriting these three classes directly from the blueprint.

## Step-by-step usage guide

> Take BPable_GameInstanceSubsystem as an example

- Open the project's plugin Settings

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 175348.jpg)



- Ensure that the BlueprintableSubsystem plugin is enabled

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 180005.jpg)

- Create the blueprint class in the Content browser and select BPable_GameInstanceSubsystem as the parent class

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 214111.jpg)

- Open the blueprint class of the GameInstanceSubsystem you created and edit it

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 220403.jpg)

- Call the blueprint Subsystem you created using the Get Subsystem general node in other blueprint classes

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 220615.jpg)

  ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 220633.jpg)

## About BlueprintableSubsystem Interface

###  Usage

In my Blueprint on the left side of the Blueprint class edit window click to overload the corresponding function

![](../resource/BPableSubsystem/屏幕截图 2022-09-03 130600.jpg)

### BlueprintableGameInstanceSubsystem

|         Name          |                           Graphic                            |                           Explain                            |
| :-------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|      Initialize       | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221009.jpg) |             Called after this subsystem created              |
|     Deinitialize      | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221033.jpg) |            Called before this subsystem destoryed            |
| ShouldCreateSubsystem | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221053.jpg) | Called before this subsystem created<br> Implementation is not necessary<br>If implement this function,return true to create this subsystem,return false not to create this subsystem |
|    GetGameInstance    | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221152.jpg) | Get the Outer, or UGameInstance, of the game instance subsystem |

---

### BlueprintableLocalPlayerSubsystem

|           Name           |                           Graphic                            |                           Explain                            |
| :----------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|        Initialize        | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221009.jpg) |             Called after this subsystem created              |
|       Deinitialize       | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221033.jpg) |            Called before this subsystem destoryed            |
|  ShouldCreateSubsystem   | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221053.jpg) | Called before this subsystem created<br/> Implementation is not necessary<br/>If implement this function,return true to create this subsystem,return false not to create this subsystem |
| GetLocalPlayerController | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 222223.jpg) | Get the APlayerController for ULocalPlayer by using the Outer of the local player subsystem, ULocalPlayer. |

---

### BlueprintableWorldSubsystem

|         Name          |                           Graphic                            |                           Explain                            |
| :-------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|      Initialize       | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221009.jpg) |             Called after this subsystem created              |
|    PostInitialize     | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 222639.jpg) |      Called after all UWorldSubsystem calls Initialize       |
|    WorldBeginPlay     | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 222658.jpg) | Called when world is ready to start gameplay before the game mode transitions to the correct state and call BeginPlay on all actors |
|     Deinitialize      | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221033.jpg) |            Called before this subsystem destoryed            |
| ShouldCreateSubsystem | ![](../resource/BPableSubsystem/屏幕截图 2022-09-02 221053.jpg) | Called before this subsystem created<br/> Implementation is not necessary<br/>If implement this function,return true to create this subsystem,return false not to create this subsystem |

- Current plugin problems

  If you create a blueprint subclass for BPable_WorldSubsystem, the editor will report an error and crash when you exit the editor.

  But there will be no problems when the game is executed properly (not found yet)