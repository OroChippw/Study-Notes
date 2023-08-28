# Unreal Engine5
[TOC]

## 基本概念
## Base
### AActor（Actor）
  Actor是所有在游戏世界中存在的物体的基类。派生自Actor的类自带前缀A，所以又称为AActor，它是虚幻引擎中的核心概念之一，可以用来创建角色、道具、敌人、特效等。AActor 有位置、旋转、缩放、碰撞体、事件响应等属性和功能。
### APawn
  APawn是代表可以在游戏世界中移动的角色或控制的对象的基类。它继承自 AActor，并具有更多的移动和输入控制功能，适用于玩家角色和NPC等。
###  ACharacter
  ACharacter 是继承自 APawn 的一个基类，用于定义具有动画、角色控制和状态的角色。它包含了一些常见的角色功能，如动画蓝图、状态机等。
### Mesh
### Socket
  插槽是在骨骼模型Mesh上定义的位置，可以用于在模型上附加其他物体、粒子效果、武器等。
## Object Type
### WorldStatic
  适用于所有不用移动的Actor，最好的例子就是Static Mesh Actors
### WorldDynamic
  适用于所有因动画或者代码影响而移动的Actor，如电梯和门
## Collision Response
* Ignore：不和任何其他物理体产生交互
* Overlap：
* ：
* ：
* ：
* ：
* ：
* ：
## UE5 C++
### UE类命名前缀
  UE提供了在构建过程中生成代码的工具，如果要使用这些工具必须符合一些固定的类命名规则，如果类的命名与规则不符，将触发警告或错误。具体类的前缀命名规则如以下说明：  
* 派生自 Actor 的类前缀为 A，比如 AController。eg.ACharactor(Class)
* 派生自 Object 的类前缀为 U，比如 UComponent。
* 派生自 SWidget（Slate UI）的类前缀为 S，比如 SButton
* Enums 的前缀为 E，比如 EFortificationType。eg.EDirection(Enum)
* Interface 类的前缀通常为 I，比如 IAbilitySystemInterface。
* Template 类的前缀为 T，比如 TArray。
* 其余类的前缀均为字母 F ，比如 FVector。eg.FHitResult(Struct)

## IDE配置问题
### 热编译

### Live Coding 

## UE5 Blueprint
###  Compent
  Capsule Compent：用以实现处理角色、物体或角色控制器的碰撞检测和响应的碰撞体组件
  Arrow Component：仅用于显示方向
  Mesh：3D网格模型，通常用于表示与碰撞体实际形状相匹配的外观，用于在游戏世界中显示碰撞体的外观。
  Character Movement：通过大量的变量实现复杂物理运动
#### SpringArm

### 重力加速度
