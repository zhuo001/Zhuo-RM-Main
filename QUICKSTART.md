# 🚀 快速开始指南

## 初次克隆项目

如果你是第一次克隆整个项目（包含所有子模块）：

```bash
# 克隆主仓库及所有子模块
git clone --recurse-submodules https://github.com/zhuo001/Zhuo-RM-Main.git

# 或者，如果已经克隆但没有子模块
cd Zhuo-RM-Main
git submodule update --init --recursive
```

## 在VS Code中打开项目

### 方式1: 使用多仓库工作区（推荐）✨

```bash
cd Zhuo-RM-Main
code zhuo-rm-workspace.code-workspace
```

这会同时打开：
- 🤖 Zhuo-RM-Main (主仓库)
- 🎯 Zhuo-RM-decision (决策系统)
- 👁️ Zhuo-RM-vision (视觉系统)

每个子系统在独立的文件夹中，可以独立管理Git。

### 方式2: 单独开发某个系统

```bash
# 只开发决策系统
cd Zhuo-RM-decision
code .

# 只开发视觉系统
cd Zhuo-RM-vision
code .
```

## 快速部署决策系统（Ubuntu车载电脑）

```bash
# 1. 进入决策系统目录
cd Zhuo-RM-Main/Zhuo-RM-decision

# 2. 创建虚拟环境
python3 -m venv venv
source venv/bin/activate

# 3. 安装依赖
pip install -r requirements.txt

# 4. 编译Berxel SDK扩展（需要先安装SDK）
python setup.py build_ext --inplace

# 5. 测试相机
python test_camera.py --mode basic

# 6. 运行决策系统
python main_decision.py
```

详细部署说明请参考: [DEPLOYMENT.md](./Zhuo-RM-decision/DEPLOYMENT.md)

## 常见Git操作

### 更新子模块

```bash
# 更新所有子模块到最新版本
git submodule update --remote

# 只更新某个子模块
git submodule update --remote Zhuo-RM-decision
```

### 在子模块中工作

```bash
# 进入子模块
cd Zhuo-RM-decision

# 正常的Git操作
git checkout -b feature/new-algorithm
git add .
git commit -m "feat: 实现新算法"
git push origin feature/new-algorithm

# 返回主仓库
cd ..
git add Zhuo-RM-decision
git commit -m "chore: 更新决策系统子模块"
git push
```

### 克隆后忘记初始化子模块？

```bash
# 在主仓库目录执行
git submodule update --init --recursive
```

## VS Code任务快捷键

在工作区中使用：

- **Ctrl+Shift+B**: 编译Berxel扩展
- **F5**: 启动决策系统调试
- **Ctrl+Shift+P** → "Tasks: Run Task":
  - 🔨 编译 Berxel 扩展
  - 📦 安装依赖
  - 🚀 运行决策系统

## 项目结构

```
Zhuo-RM-Main/
├── 📂 Zhuo-RM-decision/     (子模块) - 决策系统
├── 📂 Zhuo-RM-vision/        (子模块) - 视觉系统
├── 📄 zhuo-rm-workspace.code-workspace
├── 📄 PROJECT_STRUCTURE.md
└── 📄 QUICKSTART.md         (本文件)
```

## 故障排查

### 问题1: 子模块文件夹是空的

```bash
git submodule update --init --recursive
```

### 问题2: VS Code无法识别工作区

重新打开工作区文件：
```bash
code zhuo-rm-workspace.code-workspace
```

### 问题3: 子模块Git冲突

```bash
cd Zhuo-RM-decision
git fetch origin
git reset --hard origin/main
```

## 更多文档

- 📖 [项目结构说明](./PROJECT_STRUCTURE.md)
- 🚀 [决策系统部署](./Zhuo-RM-decision/DEPLOYMENT.md)
- 🎯 [决策系统README](./Zhuo-RM-decision/README.md)
- 👁️ [视觉系统README](./Zhuo-RM-vision/README.md)

## 需要帮助？

- 提交Issue: https://github.com/zhuo001/Zhuo-RM-Main/issues
- 团队联系方式: (待添加)

---

**最后更新**: 2025-10-15
