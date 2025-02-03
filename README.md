# ResForge 🔧

![CMake](https://img.shields.io/badge/CMake-3.20+-brightgreen)
![License](https://img.shields.io/badge/License-MIT-blue)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey)

**自动化图标资源嵌入工具**  
通过 CMake 将多个 `.ico` 图标文件一键打包到 Windows DLL 中，简化动态链接库开发流程。

---

## 目录
- [🚩 功能特性](#-功能特性)
- [🚀 快速开始](#-快速开始)
  - [环境要求](#环境要求)
  - [项目结构](#项目结构)
  - [基础用法](#基础用法)
- [🤝 贡献与协议](#-贡献与协议)
  - [贡献指南](#贡献指南)
  - [开源协议](#开源协议)

---

## 🚩 功能特性
✅ **批量图标嵌入**  
自动打包 `resources/icons/` 目录下所有图标文件  
✅ **智能资源管理**  
自动生成唯一资源 ID 和 `.rc` 脚本  
✅ **跨工具链支持**  
兼容 MinGW-w64 和 MSVC 编译器  
✅ **开箱即用**  
提供 CLion 项目模板和完整 CMake 配置

---

## 🚀 快速开始

### 环境要求
- Windows 10/11 系统
- CLion 2021.3+ 或 VS 2019+
- CMake ≥ 3.20
- MinGW-w64 (gcc 11.2+) 或 MSVC v143+

### 项目结构
```plaintext
IconDLLight/
├── CMakeLists.txt              # 主构建配置
├── src/
│   └── main.cpp                # 主函数（无内容）
├── resources/                  # 图标存放目录        
├── cmake-build-debug/          # 构建输出目录
│   └── libAutoIconDLL.dll      # 自动生成的资源文件
└── generated/                  
│   └── auto_resources.rc       # 自动生成的资源脚本
├── .gitignore                  # Git 忽略文件
├── README.md                   # 项目说明文档
└── LICENSE                     # 开源协议
```

### 基础用法
1. 将所有图标文件（`.ico`）放入 `resources/` 目录
2. 构建项目并运行，将自动生成 `libAutoIconDLL.dll` 和 `auto_resources.rc`
3. 在`cmake-build-debug/`目录下找到生成的DLL文件

---

## 🤝 贡献与协议

### 贡献指南
1. Fork 本仓库
2. 创建特性分支 (git checkout -b feature/新功能)
3. 提交修改 (git commit -m '添加新功能')
4. 推送分支 (git push origin feature/新功能)
5. 创建 Pull Request

### 开源协议
本项目基于 MIT 协议开源，详细内容请参阅 [LICENSE](LICENSE) 文件。 
