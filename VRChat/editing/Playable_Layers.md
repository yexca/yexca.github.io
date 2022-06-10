## 一、Playable Layers

在 SDK3 的 Avatar Descriptor 一共有五个层，分别为

- Base 或称Locomotion层，控制模型的蹲姿，趴姿等
- Additive Base层的附加，例如制作呼吸动画
- Gesture 手势层，手势动作制作，或者用于“空闲动画”，例如摇摆尾巴、拍打翅膀或移动耳朵
- Action 动作层，例如MMD舞蹈放此层
- FX 控制物品的开关，手势表情也在此层

此外，还有附加的三个层，分别为（此部分如需了解请看“[参考资料](三、参考资料)”部分）

- T-Pose
- IK Pose
- Sitting Pose

因能力有限，仅谈谈一些简单的改模

### 为模型添加“Base”，“Action”和“FX”默认控制器

如果是“SDK2转SDK3”或“MMD模型”，在“VRC Avatar Descriptor”的“Playable Layers”里点击“Customize”，然后在对应层后面点“Default 图层名”

如果是SDK3模型，可能已经有了对应层，可以将没有的加入

然后在“Assets\VRCSDK\Examples3\Animation\Controllers”可找到所有的默认控制器

- Base vrc_AvatarV3LocomotionLayer.controller
- Action vrc_AvatarV3ActionLayer.controller
- FX vrc_AvatarV3HandsLayer.controller

找到后点击并按“CTRL+D”即可克隆相同文件，可按“F2”重命名，然后可将这些文件拖入模型所在文件夹并新建一个文件夹存放。

再将文件拖入“VRC Avatar Descriptor”的“Playable Layers”对应位置即可。

## 二、数值与菜单

### 1）创建数值与菜单

可以在模型文件下新建一个文件夹用来存放数值与菜单

在“Assets”里右击，依次选择“创建-VRChat-Avatars-Expression Parameters” ，并重命名为“数值”

右击，依次选择“创建-VRChat-Avatars-Expression Menu” ，并重命名为“主菜单”

### 2）为模型添加数值与菜单

如果是“SDK2转SDK3”或“MMD模型”，在“VRC Avatar Descriptor”的“Expression”里点击“Customize”，然后将刚创建的“菜单”拖入“Menu”，“数值”拖入“Parameters”

如果是SDK3模型，可能已经有了数值和菜单，如没有参考上述操作

### 了解更多？

[浅析数值-动画器-菜单 – vrchat教程 (yexca.xyz)](https://vrchat.yexca.xyz/?p=119)

## 三、参考资料

[Playable Layers (vrchat.com)](https://docs.vrchat.com/docs/playable-layers)