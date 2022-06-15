# 动画器图层

## 一、前言

不同图层的动画可以同时发生，同一图层同时只能只能执行一个动画

权重：(0~1)，1为正常播放

遮罩：此层上使用的遮罩，可以限制动画的播放部位，例如只要播放上半身的动画，可以使用一个遮罩定义在上半身播放动画。

## 二、数值类型

在”动画器“中添加参数有四种类型

- Float 浮点数，可以理解为小数
- Int 整数型，可以理解为整数
- Bool 布尔型，只有”True“和”False“两种取值
- Trigger 触发器(好像在VRC中没用？)

下表为VRChat数值类型(一个模型的“数值”上限为“128 bits”)

| 数值类型 | 取值范围          | 存储占用 | 备注                                                         |
| -------- | ----------------- | -------- | ------------------------------------------------------------ |
|          |                   |          |                                                              |
| int      | `0` ~ `255`       | 8 bits   | Unsigned 8-bit int.                                          |
| float    | `-1.0` ~ `1.0`    | 8 bits   | Signed 8-bit [minifloat](https://en.wikipedia.org/wiki/Minifloat) |
| bool     | `True` or `False` | 1 bit    |                                                              |

**如果要做开关，动画器-参数中参数名字与类型要与VRC数值中一模一样**

## 三、逻辑

新建一个图层，可以看到三个默认状态

| 状态名称  | 简述                                 |
| --------- | ------------------------------------ |
| Entry     | 进入后默认状态                       |
| Any State | 只要条件满足，可任意跳转到过渡的状态 |
| Exit      | 退出，返回到”Entry“                  |

**颜色**

橙色：默认状态，即进入就执行的动画

灰色：可通过过渡达到条件执行的动画

## 四、动画状态

Motion：状态绑定的动画（Animation）

速度(Speed)：动画播放的速度

乘数(Multiplier)：Speed * 指定参数（float）作为运行时的播放速度

Motion Time：指定参数（float）作为动画播放时间(可使用此制作轮盘开关)

镜像(Mirror)：镜像播放，若打开”参数(Parameter)“：指定参数作（bool）为镜像的开关

周期偏移(Cycle Offset)：循环偏移，若打开”参数(Parameter)“：指定参数（float）作为偏移

#### Transition

Solo：只生成当前过渡

Mute：禁用过渡

多个出过渡时可调整位置(上下)以实现优先级(上方优先级高于下方)

## 五、过渡

#### Transition

Solo：只生成当前过渡

Mute：禁用过渡

有退出时间(Has Exit Time)：存在退出时间，即上一个状态能否完整结束(在”Settings“中修改)

Settings：（可通过数值修改，也可以通过图形修改）

- 退出时间(Exit Time)：达到过渡条件后，上一个状态还会播放时长(单位：秒)

- 固定持续时间(Fixed Duration)：
  勾选，下一项”过度持续时间(Transition Duration)“以s为单位
  取消勾选，下一项”过度持续时间(Transition Duration)“以（前一个状态的）百分数计数，1为100%、

- 过度持续时间(Transition Duration)：过渡时间

- 过度偏移(Transition Offset)：后一个状态从何处开始，值为后一个状态的百分数，1为100%。

- 中断源(nterruption Source)：可以打断状态的过渡、

  - 无(None)：不可打断
  - Current State：前一个状态开始的状态过渡可以打断正在进行的状态过渡
  - Ordered Interruption：优先级高于当前过渡才可以打断
  - Next State：从后一个状态开始的状态过渡可以打断正在进行的状态

  - Current State Then Next State || Next State Then Current State：决定哪个动画State上的过渡节点优先权更高，前者表示先看前一个State的优先级如果没有被触发，再看后一个State的优先级，后者则相反，来达到不同的融合与打断效果。

- Condition

  ：过渡条件，可从参数中选择

  - Int型参数：可选择Greater（>）、Less（<）、Equals（==）、NotEqual（!=）指定的数作为过渡条件
  - Float型参数：可选择Greater（>）、Less（<）指定的数作为过渡条件
  - Bool：可选择指定值（true or false）作为过渡条件
  - Trigger：条件为true时触发状态过渡

# 数值

过渡的条件可使用官方数值，只需要在”动画器-参数”添加类型和名字与官方数值相同的参数即可

(以下表格中文为我自己翻译，可能会有错误，仅翻译可能有用或我用过的参数)

## 一、官方数值总览

| Name(名字)                                                   | Description(描述)                                            | Type(类型)  | Sync(同步)     |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ----------- | -------------- |
| IsLocal                                                      | True if the avatar is being worn locally, false otherwise    | Bool        | None           |
| [Viseme](https://docs.vrchat.com/docs/animator-parameters#viseme-values)(口型) | [Oculus viseme index](https://developer.oculus.com/documentation/unity/audio-ovrlipsync-viseme-reference) (`0-14`). When using Jawbone/Jawflap, range is `0-100` indicating volume | Int         | Speech         |
| Voice                                                        | Microphone volume (`0.0-1.0`)                                | Float       | Speech         |
| [GestureLeft](https://docs.vrchat.com/docs/animator-parameters#gestureleft-and-gestureright-values)(左手手势) | Gesture from L hand control (0-7)                            | Int         | IK             |
| [GestureRight](https://docs.vrchat.com/docs/animator-parameters#gestureleft-and-gestureright-values)(右手手势) | Gesture from R hand control (0-7)                            | Int         | IK             |
| GestureLeftWeight                                            | Analog trigger L (0.0-1.0)†                                  | Float       | IK             |
| GestureRightWeight                                           | Analog trigger R (0.0-1.0)†                                  | Float       | IK             |
| AngularY                                                     | Angular velocity on the Y axis                               | Float       | IK             |
| VelocityX(X方向速度)                                         | Lateral move speed in m/s                                    | Float       | IK             |
| VelocityY(Y方向速度)                                         | Vertical move speed in m/s                                   | Float       | IK             |
| VelocityZ(Z方向速度)                                         | Forward move speed in m/s                                    | Float       | IK             |
| Upright(高度)                                                | How “upright” you are. 0 is prone, 1 is standing straight up | Float       | IK             |
| Grounded(地面)                                               | True if player touching ground(如果跳跃则为false)            | Bool        | IK             |
| Seated                                                       | True if player in station                                    | Bool        | IK             |
| AFK                                                          | Is player unavailable (HMD proximity sensor / End key)       | Bool        | IK             |
| Expression1 – Expression16                                   | User defined param, Int (`0`–`255`) or Float (`-1.0`–`1.0`)  | Int / Float | IK or Playable |
| [TrackingType](https://docs.vrchat.com/docs/animator-parameters#trackingtype-parameter) | See description below                                        | Int         | Playable       |
| VRMode                                                       | Returns `1` if the user is in VR, `0` if they are not        | Int         | IK             |
| MuteSelf                                                     | Returns `true` if the user has muted themselves, `false` if unmuted | Bool        | Playable       |
| InStation                                                    | Returns `true` if the user is in a station, `false` if not   | Bool        | IK             |

## 二、手势对应数值

用于制作手势触发动画

| Index (数值) | Gesture (手势)     |
| ------------ | ------------------ |
| 0            | Neutral (自然)     |
| 1            | Fist (握拳)        |
| 2            | HandOpen (张开手)  |
| 3            | fingerpoint (指)   |
| 4            | Victory (剪刀手)   |
| 5            | RockNRoll (我爱你) |
| 6            | HandGun (手枪)     |
| 7            | ThumbsUp (点赞)    |

## 三、口型对应值

口型参考：[Viseme Reference: Unity | Oculus Developers](https://developer.oculus.com/documentation/unity/audio-ovrlipsync-viseme-reference)

可用于制作说话触发动画

| Viseme Parameter | Viseme |
| ---------------- | ------ |
| 0                | `sil`  |
| 1                | `pp`   |
| 2                | `ff`   |
| 3                | `th`   |
| 4                | `dd`   |
| 5                | `kk`   |
| 6                | `ch`   |
| 7                | `ss`   |
| 8                | `nn`   |
| 9                | `rr`   |
| 10               | `aa`   |
| 11               | `e`    |
| 12               | `i`    |
| 13               | `o`    |
| 14               | `u`    |

## 四、例子(制作手势触发动画)

目标：开关打开时，右手握拳触发动画

查表知：右手手势参数为“GestureRight”，类型为“Int”；握拳时，“GestureRight”值为“1”

### 动画器

在“动画器-参数”添加一个“Int”型参数，名字为“GestureRight”

再创建一个“Bool”型参数作为开关，例“动画开关”

新建图层，权重设为1，新建空状态命名为“默认”，再创建一个空状态命名(例动画开)，将动画拖入

创建“默认-动画开”的过渡，条件为：“动画开关”为“true”；

创建“动画开-动画”的过渡，条件为：“GestureRight”等于“1”

创建“动画开-默认”的过渡，条件为：“动画开关”为“false”；

创建“动画-动画开”的过渡，条件为：“GestureRight”不等于“1”

### 菜单-数值

在“数值”文件添加“Bool”型“动画开关”

在菜单中“Add Control”，重命名，“类型”为“Toggle”,”Parameter”为“动画开关”

# 菜单

| 类型                       | 介绍                                                |
| -------------------------- | --------------------------------------------------- |
| Button(按钮)               | 值只改变一次，通常大约一秒钟                        |
| Toggle(切换)               | 点击会变为设定值，直至关闭                          |
| Sub Menu(子菜单)           | 下一级菜单，设置参数类似”Toggle”                    |
| Two Axis Puppet(双轴控制)  | 两个参数(float)控制垂直与水平(-1.0~1.0)             |
| Four Axis Puppet(四轴控制) | 四个参数(float)控制上下左右(0~1.0) 可用来制作摇尾巴 |
| Radial Puppet(百分比转盘)  | 一个参数控制，通常用来改变颜色或换衣服              |

以上为个人理解，以下为官方原文

- **Button** – Sets a parameter when clicked, then resets after the sync/reset has been sent– usually after about a second. Cannot be held down.

- **Toggle** – Sets a parameter when the toggle is on, resets when the toggle is turned off

- Sub-Menu

   – Opens another Expression Menu. Additionally it may also set a parameter when entered, if so that parameter is reset to zero when you exit that menu.

  - **Important note:** You can put sub-menus into sub-menus!

- **Two Axis Puppet** – Opens an axis puppet menu that controls two parameters depending on the joystick position. The parameters are mapped to vertical and horizontal. The float values range from -1.0 to 1.0.

- **Four Axis Puppet** – Opens an axis puppet menu that controls four parameters depending on the joystick position. The parameters are mapped in order, up, right, down, left. The float values are 0.0 to 1.0.

- **Radial Puppet** – Open a radial puppet menu that controls a single parameter, kind of like a progress bar that you can fill!
