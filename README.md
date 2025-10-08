# 卓-RoboMaster 哨兵机器人项目

![RoboMaster](https://img.shields.io/badge/RoboMaster-Sentry-red)
![Status](https://img.shields.io/badge/Status-In%20Development-yellow)
![License](https://img.shields.io/badge/License-MIT-blue)

## 项目简介

这是一个基于RoboMaster规则的哨兵机器人项目，旨在实现自主巡逻、目标检测、自动瞄准等功能。

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
- [x] 3D相机集成（Berxel相机）
- [x] 人形目标检测（YOLOv8）
- [x] 深度信息获取
- [x] 实时图像处理

### 开发中功能 🚧
- [ ] 自动瞄准系统
- [ ] 云台控制
- [ ] 底盘移动控制
- [ ] 自主导航
- [ ] 装甲板识别

### 规划中功能 📋
- [ ] 多目标追踪
- [ ] 路径规划
- [ ] 弹道预测
- [ ] 能量机关识别

## 技术栈

### 视觉系统
- **相机**: Berxel 3D Camera
- **深度学习框架**: YOLOv8
- **图像处理**: OpenCV
- **开发语言**: Python, C++

### 控制系统
- **框架**: ROS2 Humble
- **通信协议**: DDS
- **实时性**: RT-Linux

### 硬件平台
- **主控**: 待定
- **相机**: Berxel 3D Camera
- **云台电机**: 待定
- **底盘电机**: 待定

## 快速开始

### 环境要求
- Ubuntu 22.04 LTS
- ROS2 Humble
- Python 3.10+
- CUDA 11.8+ (可选，用于GPU加速)

### 安装步骤

1. **克隆主仓库**
```bash
git clone https://github.com/zhuo001/Zhuo-RM-Main.git
cd Zhuo-RM-Main
```

2. **克隆子项目**
```bash
# 视觉系统
git clone https://github.com/zhuo001/Zhuo-RM-vision.git

# 其他子项目待添加
```

3. **安装依赖**
```bash
# 进入各个子项目目录，按照其README安装依赖
cd Zhuo-RM-vision
# 查看该项目的README进行安装
```

## 项目结构

```
Zhuo-RM-Main/
├── README.md                 # 本文件
├── docs/                     # 项目文档
│   ├── architecture.md      # 系统架构
│   ├── hardware.md          # 硬件设计
│   └── api.md              # API文档
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
- [ ] 装甲板识别

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
