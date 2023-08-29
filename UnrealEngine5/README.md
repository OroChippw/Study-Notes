# Unreal Engine5
[TOC]

## 基本概念
### 
### AActor（Actor）
  Actor是所有在游戏世界中存在的物体的基类，所有可以被放进场景中的物体都是Actor。派生自Actor的类自带前缀A，所以又称为AActor，它是虚幻引擎中的核心概念之一，可以用来创建角色、道具、敌人、特效等。AActor 有位置、旋转、缩放、碰撞体、事件响应等属性和功能。
```
BeginPlay函数：在加载场景生成Actor以及游戏中生成Actor的时候调用的函数
Tick函数：只有继承自Actor的类以及挂载在Actor上继承自ActorComponent的类才会Tick
```
### APawn
  APawn是代表可以在游戏世界中移动的角色或控制的对象的基类。它继承自 AActor，并具有更多的移动和输入控制功能，适用于玩家角色和NPC等。
###  ACharacter
  ACharacter 是继承自 APawn 的一个基类，用于定义具有动画、角色控制和状态的角色。它包含了一些常见的角色功能，如动画蓝图、状态机等。
### Mesh
### Socket
  插槽是在骨骼模型Mesh上定义的位置，可以用于在模型上附加其他物体、粒子效果、武器等。
### Unreal Property System (Reflection)
  UE中的反射机制使其在C++基础上添加了诸多功能，例如：网络行为（多人游戏）、内存管理
#### UENUM
#### UCLASS
#### USTRUCT
#### UFUNCTION
* BlueprintCallable只是把函数交给蓝图使得蓝图可以调用。
* BlueprintImplementableEvent则是只在C++中声明或者调用函数，而函数的具体实现交给蓝图。
* BlueprintNativeEvent则可以在C++中实现，只不过要在末尾添加上后缀_Implementation在蓝图中，我们可以选择要不要重写这个函数。

## Object Type
### World Static
  适用于所有不用移动的Actor，最好的例子就是Static Mesh Actors
### World Dynamic
  适用于所有因动画或者代码影响而移动的Actor，如电梯和门
## Collision Response
### Collision Channels
* Ignore：不和任何其他物理体产生交互
* Overlap：
* ：
* ：
* ：
* ：
* ：
* ：
### Object Types
### Reactions
### Instigator
  在 Unreal Engine 中，Instigator 是一个用于标识造成某个事件或行为发生的源头的对象。在游戏中，当某个角色或物体触发了一个事件，通常会将这个角色或物体称为 "Instigator"，因为它是事件的触发者。
  例如，在射击游戏中，如果一个玩家角色开枪，那么这个玩家角色就是造成子弹发射事件的 "Instigator"。在伤害计算中，你可以使用 Instigator 来确定造成伤害的来源，从而做出适当的伤害处理。
### Attention
当开启Simulate Physics时候，Collision Presets会变成PhysicsActor
## UE5 C++
### Unreal Build Tool & Unreal Header Tool
  Unreal Build Tool 和 Unreal Header Tool是虚幻引擎的编译工具，用于生成各种generated.h文件以将C++的代码暴露给蓝图，同时通过在.Build.cs文件中的定义加载编译时所需要用到的相应模块或插件。
配置编译时的选项。

### UE类命名前缀
  UE提供了在构建过程中生成代码的工具，如果要使用这些工具必须符合一些固定的类命名规则，如果类的命名与规则不符，将触发警告或错误。具体类的前缀命名规则如以下说明：  
* 派生自 Actor 的类前缀为 A，比如 AController。eg.ACharactor(Class)
* 派生自 Object 的类前缀为 U，比如 UComponent。
* 派生自 SWidget（Slate UI）的类前缀为 S，比如 SButton
* Enums 的前缀为 E，比如 EFortificationType。eg.EDirection(Enum)
* Interface 类的前缀通常为 I，比如 IAbilitySystemInterface。
* Template 类的前缀为 T，比如 TArray。
* 其余类的前缀均为字母 F ，比如 FVector。eg.FHitResult(Struct)


### Attention
  关于报错Error: #include found after .generated.h file - the .generated.h file should always be the last #include in a header，名字中带有.generated.h的文件一定要放在include里面最后一行引入
## IDE配置问题
### 热编译
  5.0版本的热编译会把蓝图的设置重置成为默认值

### Live Coding 

## UE5 Blueprint
###  Compent
  Capsule Compent：用以实现处理角色、物体或角色控制器的碰撞检测和响应的碰撞体组件
  Arrow Component：仅用于显示方向
  Mesh：3D网格模型，通常用于表示与碰撞体实际形状相匹配的外观，用于在游戏世界中显示碰撞体的外观。
  Character Movement：通过大量的变量实现复杂物理运动
#### SpringArm

### 重力加速度
