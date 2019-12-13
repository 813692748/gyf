# unreal4学习笔记

# 一、获取Actor

```c++
#include "GameFramework/Actor.h"
AActor* owner = GetOwner(); //可以设置为私有变量，并在构造函数中初始化
```

## 二、旋转Actor

```c++
FRotator NewRotator = FRotator(0, -90, 0);  
owner->SetActorRotation(NewRotator);
```

## 三、获取世界属性

```c++
#include "Engine/World.h"

//获取默认玩家对象
AActor* DefaultPawn = GetWorld()->GetFirstPlayerController()->GetPawn();

//获取世界时间
time = GetWorld()->GetTimeSeconds();
```

## 四、触发

```c++
//.h
#include "Engine/TriggerVolume.h"
#include "Engine/World.h"
UPROPERTY(EditAnywhere)  //设置为编辑器可见
ATriggerVolume* triggervolume;

//.cpp
this->DefaultPawn = GetWorld()->GetFirstPlayerController()->GetPawn();
if (triggervolume->IsOverlappingActor(this->DefaultPawn))
{}
```

## 五、日志输出

```c++
UE_LOG(LogTemp, Warning, TEXT("%s Begin..."), *(this->owner->GetName()));
```
## 六、新建游戏模式

![](C:\Users\M\Desktop\unreal_data\设置主角.png)

## 七、将Actor转换为蓝图类

![](C:\Users\M\Desktop\unreal_data\Actor.png)

## 八、获取视野向量

```c++
FVector point0; //坐标
FRotator viewRotator; //角度
GetWorld()->GetFirstPlayerController()->GetPlayerViewPoint(point0, viewRotator); 
//通过引用获取视野向量

FVector point1 = point + viewRotator.Vector() * 100; //视野1m远的点
```

## 九、画调试辅助线

```c++
#include "DrawDebugHelpers.h"
DrawDebugLine(GetWorld(), start, end, FColor(255, 0, 0), false, 0, 0, 10);
//参数：（绘制世界，起始，终止，颜色，保留，~， ~， 厚度）
```

## 十、

