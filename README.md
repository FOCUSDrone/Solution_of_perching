# Solution_of_perching
```
.
├── README.md                    # 项目说明文档
├── sh_utils
│   └── pub_triger.sh           # 触发着陆规划的脚本
└── src                         # 源代码目录
    ├── odom_vis                # 可视化相关包
    │   ├── odom_visualization  # 无人机和平台可视化包
    │   └── pose_utils          # 姿态变换工具包
    ├── planning                # 规划包（主要节点）
    ├── traj_opt                # 轨迹优化包
    └── vis_utils               # 可视化工具包


.
├── README.md
├── sh_utils
│   └── pub_triger.sh
└── src
    ├── odom_vis
    │   ├── odom_visualization
    │   │   ├── CMakeLists.txt
    │   │   ├── Makefile
    │   │   ├── bin
    │   │   │   ├── odom_visualization
    │   │   │   └── odom_visualization_vicon45
    │   │   ├── launch
    │   │   │   ├── real_vis.launch
    │   │   │   ├── sim_vis.launch
    │   │   │   └── vins_vis.launch
    │   │   ├── mainpage.dox
    │   │   ├── meshes
    │   │   │   ├── f250.dae
    │   │   │   └── hummingbird.mesh
    │   │   ├── package.xml
    │   │   └── src
    │   │       ├── odom_visualization.cpp
    │   │       └── odom_visualization_plate.cpp
    │   └── pose_utils
    │       ├── CMakeLists.txt
    │       ├── Makefile
    │       ├── include
    │       │   └── pose_utils.h
    │       ├── package.xml
    │       └── src
    │           └── pose_utils.cpp
    ├── planning
    │   ├── CMakeLists.txt
    │   ├── config
    │   │   └── rviz_sim.rviz
    │   ├── launch
    │   │   └── perching.launch
    │   ├── nodelet_plugin.xml
    │   ├── package.xml
    │   └── src
    │       └── planning_nodelet.cpp
    ├── traj_opt
    │   ├── CMakeLists.txt
    │   ├── include
    │   │   └── traj_opt
    │   │       ├── lbfgs_raw.hpp
    │   │       ├── minco.hpp
    │   │       ├── poly_traj_utils.hpp
    │   │       ├── root_finder.hpp
    │   │       └── traj_opt.h
    │   ├── package.xml
    │   └── src
    │       └── traj_opt_perching.cc
    └── vis_utils
        ├── CMakeLists.txt
        ├── include
        │   └── vis_utils
        │       └── vis_utils.hpp
        └── package.xml


```
```
traj_opt (轨迹优化包)
功能: 负责计算最优轨迹，包含核心优化算法
关键文件:

include/traj_opt/traj_opt.h: 轨迹优化接口
include/traj_opt/minco.hpp: MINCO轨迹生成算法
include/traj_opt/poly_traj_utils.hpp: 多项式轨迹工具
include/traj_opt/root_finder.hpp: 多项式根查找算法
include/traj_opt/lbfgs_raw.hpp: L-BFGS优化算法
src/traj_opt_perching.cc: 着陆轨迹优化实现
```
```
planning (规划节点包)
功能: 协调整个规划过程，处理触发和状态管理
关键文件:

src/planning_nodelet.cpp: 主规划节点实现
launch/perching.launch: 主要启动文件
config/rviz_sim.rviz: RViz配置文件
```
```
vis_utils (可视化工具包)
功能: 提供通用可视化功能
关键文件:

include/vis_utils/vis_utils.hpp: 可视化工具类

```
```
odom_visualization (里程计可视化包)
功能: 可视化无人机和着陆平台的状态
关键文件:

src/odom_visualization.cpp: 无人机可视化实现
src/odom_visualization_plate.cpp: 着陆平台可视化实现
launch/*.launch: 不同场景的可视化配置
meshes/: 3D模型文件
```
```
pose_utils (姿态工具包)
功能: 提供姿态变换和旋转表示
关键文件:

include/pose_utils.h: 姿态变换函数声明
src/pose_utils.cpp: 姿态变换实现
```
## 已有组件
- ✅ 轨迹规划算法: traj_opt包提供完整的轨迹优化
- ✅ 可视化工具: vis_utils和odom_visualization提供丰富的可视化
- ✅ 参数配置: perching.launch中有详细的参数配置
- ✅ 姿态处理: pose_utils提供必要的姿态变换功能
## 缺失组件（需要自行实现）
- ❌ 无人机动力学模型: 缺少特定机架的动力学模型
- ❌ 控制器: 缺少轨迹跟踪控制器
- ❌ 仿真环境: 缺少Gazebo或其他仿真环境集成
- ❌ 硬件接口: 缺少与实际硬件通信的接口
# 实现步骤
## 创建无人机模型:
- 在odom_visualization/meshes/中添加新机架的3D模型
- 为Gazebo创建URDF/SDF模型
## 实现控制器:
- 创建新包your_controller
- 实现订阅规划轨迹和发布控制命令的节点
## 集成仿真环境:
- 创建Gazebo启动文件
- 配置物理参数和碰撞属性
## 参数调整:
- 根据新机架物理特性修改perching.launch中的参数
















