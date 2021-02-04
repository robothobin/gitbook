# **Plantuml**

流程图神器：VS code + plantuml + java

##  时序图

```
@startuml
 
title 时序图
 
== 鉴权阶段 ==
 
Alice -> Bob: 请求
Bob -> Alice: 应答
 
== 数据上传 ==
 
Alice -> Bob: 上传数据
note left: 这是显示在左边的备注
 
Bob --> Canny: 转交数据
... 不超过 5 秒钟 ...
Canny --> Bob: 状态返回
note right: 这是显示在右边的备注
 
Bob -> Alice: 状态返回
 
== 状态显示 ==
 
Alice -> Alice: 给自己发消息
 
@enduml
```

TIPS:

* 文件类型： test.puml
* 开始、结束： @startuml, @enduml
* title 给时序图命名
* 实线 ->    虚线-->
* 每个时序（箭头）用冒号添加注释。如"Alice -> Bob: 请求"
* note添加备注，note left / note right
* == XX ==分割时序图
* ... XX ...表示延迟
* 自己给自己发消息， Alice -> Alice