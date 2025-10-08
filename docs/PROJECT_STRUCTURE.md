# 项目结构说明

## 总体架构

Zhuo-RM项目采用模块化设计，每个子系统独立开发和维护，通过Git子模块进行集成。

## 子项目详细说明

### 1. Zhuo-RM-vision (视觉系统)

**仓库地址**: https://github.com/zhuo001/Zhuo-RM-vision

**功能描述**:
- Berxel 3D相机驱动集成
- YOLOv8人形目标检测
- 深度信息获取和处理
- 实时图像显示

**技术栈**:
- Python 3.10
- C++ (Berxel SDK封装)
- OpenCV
- Ultralytics YOLOv8
- NumPy

**主要文件**:
```
Zhuo-RM-vision/
├── berxel_camera.py          # 相机Python接口
├── berxel_wrapper.cpp         # SDK C++封装
├── person_detect.py           # 主检测程序
├── test_components.py         # 组件测试
└── setup.py                   # 编译配置
```

**依赖**:
- Berxel SDK
- YOLO模型文件 (yolov8n.pt)

### 2. Zhuo-RM-control (控制系统) - 规划中

**功能描述**:
- 云台控制
- 底盘移动控制
- PID控制算法
- 电机驱动

### 3. Zhuo-RM-decision (决策系统) - 规划中

**功能描述**:
- 状态机管理
- 行为树
- 路径规划
- 战术决策

### 4. Zhuo-RM-hardware (硬件设计) - 规划中

**功能描述**:
- 机械结构设计
- 电路设计
- PCB设计
- 3D打印文件

## 系统集成

### ROS2节点通信图

```
┌─────────────────┐
│  Vision Node    │ ──► /target_info
│  (检测目标)     │
└─────────────────┘
         │
         ▼
┌─────────────────┐
│  Decision Node  │ ──► /control_cmd
│  (决策控制)     │
└─────────────────┘
         │
         ▼
┌─────────────────┐
│  Control Node   │ ──► /motor_cmd
│  (电机控制)     │
└─────────────────┘
```

### 数据流

1. **视觉系统** → 检测目标位置和距离
2. **决策系统** → 根据目标信息制定策略
3. **控制系统** → 执行云台和底盘动作

## 开发规范

### 分支管理

- `main`: 主分支，稳定版本
- `develop`: 开发分支
- `feature/*`: 功能开发分支
- `hotfix/*`: 紧急修复分支

### 提交规范

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Type类型**:
- `feat`: 新功能
- `fix`: 修复bug
- `docs`: 文档更新
- `style`: 代码格式
- `refactor`: 重构
- `test`: 测试相关
- `chore`: 构建/工具相关

### 代码风格

- Python: PEP 8
- C++: Google C++ Style Guide
- ROS2: ROS2 Coding Style

## 构建和部署

### 克隆项目（含子模块）

```bash
# 克隆主仓库
git clone --recursive https://github.com/zhuo001/Zhuo-RM-Main.git

# 如果已经克隆，更新子模块
git submodule update --init --recursive
```

### 编译

```bash
# 编译ROS2工作空间
cd Zhuo-RM-Main
colcon build --symlink-install

# 编译视觉系统
cd Zhuo-RM-vision
python3 setup.py build_ext --inplace
```

### 运行

```bash
# 启动ROS2环境
source install/setup.bash

# 启动视觉节点
ros2 run vision person_detector

# 启动其他节点...
```

## 测试

### 单元测试

```bash
# Python测试
pytest

# C++测试
colcon test
```

### 集成测试

```bash
# 运行集成测试脚本
./scripts/integration_test.sh
```

## 性能指标

### 视觉系统
- 检测帧率: 30 FPS
- 检测延迟: < 50ms
- 检测精度: > 85%

### 控制系统
- 控制频率: 100 Hz
- 响应时间: < 20ms

## 故障排除

常见问题和解决方案请查看各子项目的README文件。

## 更新日志

详见各子项目的CHANGELOG.md文件。
