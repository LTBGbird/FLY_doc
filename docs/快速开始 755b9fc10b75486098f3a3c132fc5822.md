# 快速开始

## 准备工作

### 自主飞行平台

- 飞机本体 x 1
- 满电4s电池 x 1
- mini-HDMI线 x 1
- 显卡欺骗器 x 1

### **自行准备**

- 路由器 x 1
- 计算机（地面站） x 1
- 显示器 x 1
- type-C 拓展坞 x 1
- 鼠标 x 1
- 键盘 x 1

### 若第一次使用

- 提前在地面站上安装NoMachine （飞机上已经安装好，只需地面站上安装即可）
    - windows下载链接：[https://downloads.nomachine.com/windows/?id=3](https://downloads.nomachine.com/windows/?id=3)
    - Linux下载链接：[https://downloads.nomachine.com/linux/?id=1](https://downloads.nomachine.com/linux/?id=1)
- 若第一次使用，请先将飞机机载电脑连接至路由器
    - 先连接mini HDMI线至显示器，插入type-C拓展坞连接键盘和鼠标。

    ![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled.png)

    - 在ubuntu系统界面，将机载计算机连上路由器的WiFi，记录飞机设备ip。可以在终端输入指令查看ip

    ```bash
    ifconifg
    ```

    ![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%201.png)


## 操作手须知

### 遥控器说明

<aside>
💡 遥控器须知务必仔细掌握，涉及应急处理。

</aside>

<aside>
💡 部署飞行应有2人在场，1人操控地面站，1人手持遥控器，具有一定的四旋翼无人机飞行经验，应对可能的意外突发情况。

</aside>

| 7通道（第一优先级） | 上：电机使能    下：急停 |
| --- | --- |
| 5通道（第二优先级） | 上：遥控器手动控制姿态   下：接入px4_ctrl  |
| 6通道（第三优先级） | 上：接入px4_ctrl跟踪轨迹    下：接入px4_ctrl遥控器控制位置 |

![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%202.png)

### 在飞行时遇到紧急情况？

- 定位崩溃
    - 体现在飞机姿态剧烈变化，严重失控
    - 处理措施：**拨下7通道，紧急停桨**
- 定位未崩溃，轨迹跟踪异常
    - 体现在飞机姿态基本稳定，严重失控
    - 处理措施：**拨下7通道，紧急停桨**

## 简单自主飞行部署

- 检查周围环境是否安全，如是否可能对行人、车辆造成安全隐患。禁止在可能造成安全隐患的场景进行飞行测试。
- 将配套4s电池置于在飞机底座和电池基座之间，并用扎带固定牢固

![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%203.png)

- 将飞机摆放在可以安全起飞的位置。为安全起见，机头朝前，机尾朝地面站。

![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%204.png)

- 使用笔记本，将其连上相同路由器WiFi，通过NoMachine连接到飞机计算机的远程桌面。（用户名与密码即为nv）

![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%205.png)

![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%206.png)

- 将遥控器调整至自主起飞前对应档位
    - 7通道：最上
    - 5通道：操作手端
    - 6通道：最下

![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%202.png)

- 打开Terminator，按 Alt+A 在所有窗口广播指令

    ```bash
    cd pn_ws/ego_lidar_ws
    ```

    进入自主飞行工作空间，输入指令

    ```bash
    source devel/setup.zsh
    ```

    ![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%207.png)

- 第一个终端启动mavros的ros节点，输入指令

    ```bash
    px4_run
    ```

    ![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%208.png)

    看到终端内有以下输出内容为正常启动px4


![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%209.png)

- 第二个终端启动自主飞行的一系列程序，输入指令

    ```bash
    ego_run
    ```


![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%2010.png)

![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%2011.png)

所有程序启动完毕大约用时大约15秒左右，

- 第三个终端启动可视化程序rviz，输入指令

    ```bash
    	visualize
    ```


![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%2012.png)

![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%2013.png)

- 确定一切准备就绪：
    - 遥控器油门置于中位
    - 四周安全，不存在人身财产安全隐患
    - 可视化程序rviz中**可视化地图实时刷新**、**飞机姿态现实正常**

- 输入飞机起飞指令

    ```bash
    takeoff
    ```

    可见飞机自动起飞，悬停于约离地1.2m高度处。

    ![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%2014.png)

- 在rviz中，使用3D Nav Goal在画面中设置目标点

    ![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%2015.png)

    在当前设置中，设置目标点仅获取 $(x,y)$ 信息，不获取高度、偏航角信息。

- 飞机根据当前所感知环境，进行实时在线自主规划，想目标的移动，红色轨迹为所规划轨迹。

    ![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%2016.png)

    ![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%2017.png)

- 在需要降落飞机时，在空闲终端输入降落指令

    ```bash
    land
    ```

    飞机自主下降，在降落到最低位置后，安全起见将7通道下拨，油门置于中位，使飞机电机下电。

    <aside>
    💡 为安全起见，降落后下次起飞在急停模式下将所有程序Ctrl+C关闭干净，重新执行部署起飞流程：遥控器置于合适挡位→启动程序。

    </aside>

    ![Untitled](%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B%20755b9fc10b75486098f3a3c132fc5822/Untitled%2018.png)


## 指定途径点轨迹规划

<aside>
💡 请注意，世界坐标系原点位于飞机启动ego_run程序时位置，前 x 左 y 上 z 。

</aside>

- 使用code打开 ~/pn_ws/lidar_ego_ws/src 文件夹
- 编辑参数文件 ~/pn_ws/lidar_ego_ws/src/planner\plan_manage\launch\run_in_exp.launch
- 修改位于39行参数 flight_type 为 2，使得使用全局途径点规划轨迹
- 修改位于42行参数 point_num 为 期望经过途径点个数
- 依次修改对应途径点坐标

    ```bash
    <arg name="point0_x" value="16.0" />
    <arg name="point0_y" value="0.0" />
    <arg name="point0_z" value="1.2" />
    ```

- 起飞步骤和部署飞行部分相同，使用 Rviz 的 2D Nav Goal 任意选点触发规划执行。
