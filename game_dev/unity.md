# Unity

## questions
- what is draw calls
- how to measure framerates

## game challenges
- 超级坦克大战
- block breaker
  - revive the block breaker game
- tower defense
  - reverse engineer the bought package and build a TD game
- rocket booster
- tetris
- racing
- pong
- snake
- flappy bird
- t-rex runner
- 别踩白块儿
- 微信飞机大战
- 扫雷游戏
- 打地鼠游戏
- 青蛙过河游戏
- 激光圈
- 超级马里奥 (super mario)
- 吃豆人
- 宝石迷阵
- 植物大战僵尸
- 塔防游戏
- 找Asset Store上面的完整工程，找自己感兴趣的开始复刻

## Unity Learning Pathway
- 数学知识
  - 向量，欧拉角，四元数，矩阵，
  - 向量的加减法点乘差乘
  - 空间解析几何
  - 线性代数
  - 数学分析微积分部分
  - 数值逼近解法
- 物理知识
  - 刚体力学
  - 运动学定律
  - 数理方程
- C#语言基础
  - 基本数据类型, 语法，委托与事件
  - 常用设计模式，单例模式
  - 泛型, 线程, 网络编程
- 引擎系统
  - 渲染
  - 物理和碰撞
  - AI和寻路
  - 音频
  - 动画
  - 加载和IO
  - 文件系统
  - 内存管理
  - 多线程架构
- 游戏逻辑
  - HUD，UI，FSM
  - 具体全局玩法流程逻辑
  - 技能系统
  - 武器，伤害，升级，装备
- 工具
  - 流程化插件
  - 编辑器功能
  - 便利性需求
  - 自动化构建版本工具
- 熟悉Unity的界面
- 熟悉Unity的工程结构内置目录区分
- 理解场景里面的坐标系统
  - 输入系统，向量概念
  - 世界坐标 vs 局部坐标
  - 移动，缩放，旋转
- 创建场景的一些基本概念
  - 游戏对象，组件，脚本
  - 层次视图，项目视图及属性视图
- 资源管理
  - 模型，网格，材质，贴图，动画，数据表，配置表
  - 编辑器扩展，AssetBundle
- 脚本的生命周期
  - Mono Behaviour 的生命周期	
    - Start,UpDate
  - 预制体，时间，Tag，Layer
- 界面
  - UGUI, Lua，NGUI
- 高级组件
  - 摄像机
  - 灯光
  - 地形
  - 渲染
  - 粒子系统
  - 内存管理
  - 图形学
    - Shader
    - 渲染管道
	- 物理系统
	- 动画系统
  - AI
    - 行为树
  - 角色动画控制
    - 动画系统
    - 导航系统
  - 网络通信

## feature based challenges
- 如何显示一个图片/精灵
- 精灵的显示如何分清楚哪个先渲染哪个后渲染（渲染层次）
- 如何播放帧动画
- 如何控制两个物体碰撞
- 两个物体碰撞时候销毁其中一个同时生成一个物体播放帧动画特效然后播放完成之后销毁
- 如何播放音乐音效
- 背景层滚动效果怎么做
- 每次播放特效都生成一个物体然后销毁是不是有点浪费内存，可不可以一次生成多个重复利用（引入了对象池）
- 如何处理存档（数据持久化）
- 存档时候如果 A 写入存档还没结束时候 B 又写入存档会不会出问题（引入了文件系统使用单例）

## data structures in games

堆栈的应用：在处理菜单时候比如进入设置菜单时候把新菜单压栈操作，返回时候出栈销毁即可。在游戏场景进入到一个房间时候可以把当前游戏场景暂停然后把新的房间场景压栈。

队列的应用：在一些需要缓冲输入时候（比如格斗游戏）可以使用队列来控制输入操作。在一些技能系统比如一回合有8个体力槽玩家来组合攻击。在制作回放系统时候也可以使用队列来制作。

树的应用：基本是当你需要面对分支而且每个分支都有分支时候需要考虑。典型的比如剧情或者对话树，在节点下有很多子物体，子物体又可以有很多子物体时候也是它的应用场景。

图的应用：在可视化流程控制，有限状态机和导航系统都可以找到它的影子

## Concepts
- Actors
- Controllers
- Characters
- Game Modes
- Game States
- Levels
- Collisions
- Animation sequences
- Static meshes
- Skeletel meshes
- rigid body
- collision detection

# unity packages
- odin
- playmaker

## books
* 游戏编程算法与技巧
* 游戏编程模式
* 游戏引擎架构
* realtime rendering 3rd
* Fundations of physically based modelling

## game design
- 龙与地下城城主手册
- 战旗类经典的资料

## people
- 叶劲峰 