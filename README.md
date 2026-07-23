# Minecraft Polymer 适配指南

**完整的 Polymer 模组适配教程和参考手册**

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)](https://github.com/yumuq/minecraft-polymer-guide)

---

## 📚 关于本指南

本指南是基于 **Easy Anvils** 和 **Quick Shulker** 两个真实项目的完整 Polymer 适配经验编写的全面教程。

### 适用对象

- 🤖 **AI 助手** - 作为 Minecraft 模组适配的知识库
- 👨‍💻 **模组开发者** - 学习如何适配 Polymer
- 🔧 **服务器管理员** - 了解 Polymer 的工作原理

### 核心特点

✅ **实战驱动** - 基于两个真实项目的完整经验  
✅ **全面覆盖** - 从理论到实践的完整流程  
✅ **AI 友好** - 结构化、精确、可直接使用的代码模板  
✅ **持续更新** - 基于实战持续完善

---

## 🚀 快速开始

### 第一次使用？

**推荐阅读顺序：**
1. [00-导航.md](./00-导航.md) - 了解文档结构
2. [01-核心概念.md](./01-核心概念.md) - 理解 Polymer 是什么
3. [03-模组分类.md](./03-模组分类.md) - 学会判断模组类型
4. 选择案例学习：
   - [09-案例-EasyAnvils.md](./09-案例-EasyAnvils.md) - 复杂适配
   - [10-案例-QuickShulker.md](./10-案例-QuickShulker.md) - 简单适配
5. [05-适配流程.md](./05-适配流程.md) - 开始实战

### 已经熟悉 Polymer？

**快速参考：**
- [06-代码模板.md](./06-代码模板.md) - 复制粘贴代码
- [12-快速参考.md](./12-快速参考.md) - 命令速查
- [07-常见错误.md](./07-常见错误.md) - 错误排查

### 遇到问题？

**排查流程：**
1. [07-常见错误.md](./07-常见错误.md) - 查找常见错误
2. [08-疑难杂症.md](./08-疑难杂症.md) - 复杂问题
3. 案例分析 - 查看相似问题的解决方案

---

## 📖 文档目录

### 核心文档

| 文档 | 内容 | 难度 |
|------|------|------|
| [00-导航.md](./00-导航.md) | 文档索引和使用指南 | ⭐ |
| [01-核心概念.md](./01-核心概念.md) | Polymer 是什么、为什么需要 | ⭐ |
| [02-理论基础.md](./02-理论基础.md) | 工作原理、Mixin 机制 | ⭐⭐ |
| [03-模组分类.md](./03-模组分类.md) | 判断模组类型、适配策略 | ⭐⭐ |

### 实战指南

| 文档 | 内容 | 难度 |
|------|------|------|
| [04-环境准备.md](./04-环境准备.md) | 开发环境配置 | ⭐ |
| [05-适配流程.md](./05-适配流程.md) | 完整适配步骤 | ⭐⭐ |
| [06-代码模板.md](./06-代码模板.md) | 可复用代码模板 | ⭐ |

### 问题解决

| 文档 | 内容 | 难度 |
|------|------|------|
| [07-常见错误.md](./07-常见错误.md) | 错误排查矩阵 | ⭐⭐ |
| [08-疑难杂症.md](./08-疑难杂症.md) | 复杂问题处理 | ⭐⭐⭐ |

### 案例分析

| 文档 | 内容 | 类型 |
|------|------|------|
| [09-案例-EasyAnvils.md](./09-案例-EasyAnvils.md) | 完整适配过程 | 服务器端模组 |
| [10-案例-QuickShulker.md](./10-案例-QuickShulker.md) | 完整适配过程 | 混合驱动模组 |

### 参考资料

| 文档 | 内容 | 用途 |
|------|------|------|
| [11-最佳实践.md](./11-最佳实践.md) | 优化和规范 | 提升质量 |
| [12-快速参考.md](./12-快速参考.md) | 命令和 API 速查 | 快速查找 |

---

## 🎯 案例项目

### Easy Anvils - 服务器端模组案例

**项目地址：** https://github.com/yumuq/polymer-of-easy-anvils

**特点：**
- ✅ 自定义方块伪装
- ✅ BlockEntity 数据过滤
- ✅ 原版客户端 100% 功能可用
- ⭐⭐⭐ 适配难度：中等

**适用场景：**
- 有自定义方块的模组
- 服务器端逻辑模组
- 需要完整功能支持

---

### Quick Shulker - 混合驱动模组案例

**项目地址：** https://github.com/yumuq/polymer-of-quickshulker

**特点：**
- ✅ 仅菜单类型注册
- ✅ 基础功能原版客户端可用
- ⚠️ 高级功能需要客户端模组
- ⭐ 适配难度：极简

**适用场景：**
- 无自定义方块的模组
- 混合驱动功能模组
- 快速适配需求

---

## 📊 文档统计

- **文档数量：** 13 个
- **总行数：** ~7,590 行
- **代码示例：** 100+ 个
- **完整案例：** 2 个
- **错误解决方案：** 50+ 个

---

## 🔗 相关资源

### 官方文档

- **Polymer 官网：** https://polymer.pb4.eu/
- **Polymer GitHub：** https://github.com/Patbox/polymer
- **Fabric 文档：** https://fabricmc.net/wiki/

### 案例项目

- **Easy Anvils Polymer：** https://github.com/yumuq/polymer-of-easy-anvils
- **Quick Shulker Polymer：** https://github.com/yumuq/polymer-of-quickshulker

### 工具

- **Nucleoid Maven：** https://maven.nucleoid.xyz/
- **Fabric 版本查询：** https://fabricmc.net/versions.html

---

## 🤝 贡献

欢迎贡献！如果您：
- 发现文档错误或不清晰
- 有新的案例可以分享
- 发现新的问题和解决方案

请提交 Issue 或 Pull Request！

---

## 📜 许可证

本文档采用 [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) 许可证。

**您可以自由地：**
- **分享** - 复制、发行本文档
- **演绎** - 修改、转换或基于本文档创作

**惟须遵守：**
- **署名** - 必须给出适当的署名
- **相同方式共享** - 基于本文档的创作必须以相同许可协议分发

---

## 🙏 致谢

- **Polymer 作者：** [Patbox](https://github.com/Patbox)
- **Easy Anvils 原作者：** ChampionAsh5357
- **Quick Shulker 原作者：** kyrptonaught, MoRanpcy, Hao_cen, Grayer0113
- **所有贡献者和反馈者**

---

## 📞 联系方式

- **GitHub Issues：** [提交问题](../../issues)
- **项目主页：** https://github.com/yumuq/minecraft-polymer-guide

---

**准备好开始学习 Polymer 适配了吗？从 [00-导航.md](./00-导航.md) 开始吧！** 🚀
