## 一、MMD模型导入Unity

[上篇文章](/VRChat/Upload/mmd_to_fbx.md)讲述了MMD模型转换为FBX，现在将MMD模型所有的文件都导入Unity

## 二、MMD模型适配

### 1）材质

点击FBX文件，右方点击”Materials-位置-使用外部材质“，然后点击应用，等待亿会

### 2）骨骼

依次点击”Rig-动画类型-人形“，点击应用，等待亿会

然后点击”配置…“进入查看骨骼

首先确定是不是T-pose，如果不是，右边划到最下方，点击”动作-强制T动作“，然后检查骨骼是否错误（一般有错误在”Head“）

检查完毕后点击”Done“

## 三、添加SDK描述文件

### 1）调整视角球

”VRC Avatar Descriptor“第一个为”View“，即我们要调整的视角球，点击”Edit“即可在Unity调整，大概放在额头前，然后回到脚本点击”Return“即可

### 2）添加”Viseme“

如果未在Blend设置请忽视(即[MMD模型转换为FBX第三步](/VRChat/Upload/mmd_to_fbx.md#三、进一步处理)未做)，请看[第四步](#四、添加动骨和碰撞)或直接上传

”VRC Avatar Descriptor“第二个为”LipSync“，”Mode“选择”Viseme Blend Shape“，左方将”Body“拖入”Face Mesh“会自动识别

### 3）添加”Eye Look“

”VRC Avatar Descriptor“第三个为”Eye Look“，点击”Enable“，将左右眼睛骨骼拖入对应位置

下方”Eyelids“的”Eyelid Type“选择”Blendshapes“，然后将”Body“拖入，即可自动识别

## 四、添加动骨和碰撞

**注意：VRChat官方指出“Dynamic bone”过段时间将会被完全移除，请学习/添加新动骨PhysBones**

添加动骨和碰撞是需要反复尝试的，而且毕竟麻烦，如果不加的话在游戏里移动模型的衣服头发不会动

### 1）动骨

在想要“动”的地方添加动骨，例如裙子，头发等，这里以裙子为例

找到裙子所在的骨骼，点击后在右方点击“添加组件”，搜索“Dynamic bone”，添加

然后将骨骼放进“Dynamic bone”的“Root”，调整四个参数

Damping  阻力
Elasticity  弹性

下面两个限制范围
Stiffness   刚度(比下面的小)
Inert      惰性的

以下参数仅供参考，具体请自行尝试最佳参数

例：裙子参数 0.6 、 0.06 、 0.2 、0.4

　　胸部参数 0.08 、 0.06 

　　头发参数 0.7 、 0.06 、 0.6 、0.85

此处参数参考：[VRchat模型之unity – 星空月零 – 博客园](https://www.cnblogs.com/raitorei/p/12008887.html)

### 2）碰撞

动骨做完后在“游戏模式”下移动模型可以看到效果（穿模），这时可通过添加碰撞解决，例如腿部碰撞

在想要添加碰撞的骨骼下方新建一个空物体（右击骨骼，点击“Create Empty”）

点击这个空物体，在右方添加组件“Dynamic bone Collider”，调整大小和高度

### 3）碰撞加入动骨

点击想放入碰撞并有动骨的骨骼(例如裙子)，将上一步创建的物体拖入右方动骨组件的碰撞器(例如腿部碰撞)即可（这样腿部的碰撞就可以和裙子动骨碰撞，从而使裙子撑起来）

此时打开“播放模式”即可看到效果

## 五、上传

上传参考[成品模型上传第四步](/VRChat/Upload/Upload.md#四、上传模型)

关于”VRC Avatar Descriptor“其他部分将在后续文章描述