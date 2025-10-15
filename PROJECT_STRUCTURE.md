# 🤖 卓越 RM 机器人项目架构

## 📁 项目结构

本项目采用**模块化架构**，各子系统独立开发维护：

```
Zhuo-RM-Main/                      # 主仓库（协调中心）
│
├── 📂 Zhuo-RM-decision/           # 决策系统子仓库 ⭐
│   ├── src/
│   │   ├── depth_slam_obstacle.py    # SLAM避障核心算法
│   │   ├── berxel_camera.py          # P100R相机接口
│   │   └── berxel_wrapper.cpp        # SDK C++封装
│   ├── main_decision.py              # 决策系统主程序
│   ├── test_camera.py                # 相机测试
│   ├── test_slam.py                  # SLAM测试
│   ├── DEPLOYMENT.md                 # Ubuntu部署指南
│   └── README.md
│
├── 📂 Zhuo-RM-vision/             # 视觉系统子仓库
│   ├── berxel_wrapper.cpp            # (原始开发版本)
│   ├── depth_slam_obstacle.py        # (原始开发版本)
│   └── ...
│
├── 📂 Zhuo-RM-control/            # 控制系统 (待开发)
├── 📂 Zhuo-RM-hardware/           # 硬件接口 (待开发)
│
└── 📄 zhuo-rm-workspace.code-workspace   # VS Code 多仓库工作区配置

```

## 🎯 各子系统说明

### 1. Zhuo-RM-decision (决策系统) ⭐ 新建

**仓库地址**: https://github.com/zhuo001/Zhuo-RM-decision

**功能**: 基于P100R深度SLAM的实时避障与路径规划

**主要模块**:
- 深度图SLAM算法
- P100R相机SDK封装
- 障碍物检测
- 导航决策输出

**运行平台**: Ubuntu 20.04/22.04 (车载电脑)

**快速开始**:
```bash
cd Zhuo-RM-decision
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python setup.py build_ext --inplace
python main_decision.py
```

### 2. Zhuo-RM-vision (视觉系统)

**仓库地址**: https://github.com/zhuo001/Zhuo-RM-vision

**功能**: 视觉识别与图像处理

**状态**: 
- 包含P100R初步开发代码
- 决策系统已独立至 Zhuo-RM-decision

### 3. Zhuo-RM-control (控制系统) - 规划中

**功能**: 运动控制、底盘驱动

### 4. Zhuo-RM-hardware (硬件层) - 规划中

**功能**: 电机、传感器底层接口

## 🚀 使用VS Code多仓库工作区

### 方法1: 使用工作区文件（推荐）

```bash
cd Zhuo-RM-Main
code zhuo-rm-workspace.code-workspace
```

这会在VS Code中同时打开所有子仓库，每个子仓库独立管理Git。

### 方法2: 单独打开

```bash
# 只开发决策系统
cd Zhuo-RM-decision
code .

# 只开发视觉系统
cd Zhuo-RM-vision
code .
```

## 🔧 开发工作流

### 添加新的子仓库

1. 在GitHub创建新仓库
2. 克隆到Zhuo-RM-Main目录
3. 更新 `zhuo-rm-workspace.code-workspace` 添加新文件夹

```bash
cd Zhuo-RM-Main
git clone https://github.com/zhuo001/Zhuo-RM-新系统.git
```

### Git操作

每个子仓库独立管理版本：

```bash
# 在decision目录
cd Zhuo-RM-decision
git status
git add .
git commit -m "更新决策算法"
git push

# 在vision目录
cd ../Zhuo-RM-vision
git status
git add .
git commit -m "优化图像处理"
git push
```

## 📊 系统集成

### 数据流

```
[P100R相机] 
    ↓ (深度+彩色)
[Zhuo-RM-decision] 
    ↓ (决策指令)
[Zhuo-RM-control] 
    ↓ (控制信号)
[Zhuo-RM-hardware]
    ↓
[底盘/电机]
```

### 通信接口

各系统间通过以下方式通信：
- ROS2 Topics (推荐)
- ZMQ Socket
- 共享内存

## 🛠️ VS Code 任务

在工作区中可以直接使用快捷任务：

- **Ctrl+Shift+B**: 编译Berxel扩展
- **F5**: 运行决策系统调试
- 在命令面板搜索 "Tasks: Run Task":
  - 🔨 编译 Berxel 扩展
  - 📦 安装依赖
  - 🚀 运行决策系统

## 📝 开发规范

### Git Commit 规范

```
类型: 简短描述

详细说明

类型包括:
- feat: 新功能
- fix: 修复bug
- docs: 文档更新
- refactor: 重构代码
- test: 测试相关
- perf: 性能优化
```

示例:
```bash
git commit -m "feat: 实现A*路径规划算法

- 添加A*算法核心逻辑
- 集成到决策系统
- 测试通过"
```

### 代码风格

- Python: PEP 8
- C++: Google Style Guide
- 使用 Black 格式化Python代码
- 使用 clang-format 格式化C++代码

## 🚧 当前进度

| 系统 | 状态 | 进度 | 说明 |
|------|------|------|------|
| **Zhuo-RM-decision** | ✅ 开发中 | 60% | SLAM避障已完成，路径规划开发中 |
| **Zhuo-RM-vision** | ✅ 已有代码 | 40% | 基础功能完成，需整合 |
| **Zhuo-RM-control** | ⏳ 预备中 | 0% | 即将开始 |
| **Zhuo-RM-hardware** | ⏳ 预备中 | 0% | 即将开始 |

## 📚 文档

- [决策系统部署指南](./Zhuo-RM-decision/DEPLOYMENT.md)
- [决策系统README](./Zhuo-RM-decision/README.md)
- [视觉系统文档](./Zhuo-RM-vision/README.md)

## 🤝 协作开发

### 分支策略

每个子仓库独立使用Git Flow:

```
main       (稳定版本)
  ↓
develop    (开发版本)
  ↓
feature/*  (功能分支)
```

### Pull Request流程

1. Fork子仓库
2. 创建功能分支
3. 提交PR到develop分支
4. Code Review
5. 合并到develop
6. 定期合并到main

## 📧 联系方式

- 团队: 卓越RM机器人团队
- GitHub: https://github.com/zhuo001
- 邮箱: (待添加)

---

**最后更新**: 2025-10-15  
**版本**: v1.0
