# Unreal Engine5
[TOC]
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
