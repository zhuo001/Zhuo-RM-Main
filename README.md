# 卓-RoboMaster 哨兵机器人项目

![RoboMaster](https://img.shields.io/badge/RoboMaster-Sentry-red)
![Status](https://img.shields.io/badge/Status-In%20Development-yellow)
![License](https://img.shields.io/badge/License-MIT-blue)

## 项目简介

这是一个基于RoboMaster规则的哨兵机器人项目，旨在实现自主巡逻、目标检测、自动瞄准与跟踪等功能。本项目的视觉子系统以“人形目标识别与跟踪”为核心，采用 YOLOv8 进行人形检测，并结合 Berxel 3D 相机的深度信息进行距离估计与多目标跟踪。

## 项目架构

本项目采用模块化设计，各个子系统独立开发和维护：

### 子项目列表

| 子项目 | 描述 | 仓库链接 | 状态 |
|--------|------|----------|------|
| **Zhuo-RM-vision** | 视觉检测系统 | [🔗 Zhuo-RM-vision](https://github.com/zhuo001/Zhuo-RM-vision) | ✅ 开发中 |
| **Zhuo-RM-control** | 运动控制系统 | 🔜 即将推出 | ⏳ 规划中 |
| **Zhuo-RM-decision** | 决策系统 | 🔜 即将推出 | ⏳ 规划中 |
| **Zhuo-RM-hardware** | 硬件设计 | 🔜 即将推出 | ⏳ 规划中 |

## 功能特性

### 已实现功能 ✅
- [x] 3D 相机集成（Berxel 相机）
- [x] 人形目标检测（YOLOv8）
- [x] 深度信息获取与距离估计
- [x] 实时图像处理

### 开发中功能 🚧
- [ ] 自动瞄准系统
- [ ] 云台控制
- [ ] 底盘移动控制
- [ ] 自主导航
- [ ] 人形目标识别与多目标跟踪（持续优化）

### 规划中功能 📋
- [ ] 多机协同
- [ ] 路径规划
- [ ] 弹道预测
- [ ] 能量机关识别

## 技术栈

### 视觉系统
- **相机**: Berxel 3D Camera
- **检测模型**: Ultralytics YOLOv8
- **图像处理**: OpenCV
- **开发语言**: Python, C++

### 控制系统
- **框架**: ROS2 Humble
- **通信协议**: DDS

## 快速开始

### 环境要求
- Ubuntu 22.04 LTS
- ROS2 Humble
- Python 3.10+
- CUDA 11.8+（可选，用于 GPU 加速）

### 安装步骤

1. **克隆主仓库**

```bash
git clone https://github.com/zhuo001/Zhuo-RM-Main.git
cd Zhuo-RM-Main
```

2. **克隆视觉子项目**

```bash
# 视觉系统
git clone https://github.com/zhuo001/Zhuo-RM-vision.git
```

3. **准备视觉模块**

- 下载或训练 YOLOv8 权重（例如 `yolov8n.pt`）。
- 进入 `Zhuo-RM-vision`，按照该仓库 README 安装依赖并编译 C++ 扩展（Berxel SDK 封装）。

```bash
cd Zhuo-RM-vision
# 安装 Python 依赖（示例）
python3 -m pip install -r requirements.txt
# 如果包含 C++ 扩展
python3 setup.py build_ext --inplace
```

4. **运行视觉节点（示例）**

```bash
# 启动 ROS2 环境（在工作空间根目录）
source install/setup.bash
# 启动视觉检测节点（示例名称）
ros2 run vision person_detector
```

## 项目结构

```
Zhuo-RM-Main/
├── README.md                 # 本文件
├── docs/                     # 项目文档
│   ├── architecture.md       # 系统架构
│   ├── hardware.md           # 硬件设计
│   └── api.md                # API 文档
├── Zhuo-RM-vision/          # 视觉系统（子模块）
├── Zhuo-RM-control/         # 控制系统（子模块）
├── Zhuo-RM-decision/        # 决策系统（子模块）
└── Zhuo-RM-hardware/        # 硬件设计（子模块）
```

## 贡献指南

欢迎贡献代码！请遵循以下步骤：

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

## 开发路线图

### Phase 1: 基础功能 (当前阶段)
- [x] 视觉系统基础框架
- [ ] 控制系统基础框架
- [ ] 系统集成测试

### Phase 2: 核心功能
- [ ] 自动瞄准
- [ ] 自主导航
- [ ] 人形目标识别与跟踪

### Phase 3: 高级功能
- [ ] 多机协同
- [ ] 战术决策
- [ ] 能量优化

## 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 联系方式

- **项目维护者**: Zhuo-Skadi
- **GitHub**: [@zhuo001](https://github.com/zhuo001)

## 致谢

感谢以下项目提供的支持：
- ROS2
- YOLOv8
- OpenCV
- Berxel SDK

---

⭐ 如果这个项目对你有帮助，请给个星标支持一下！
