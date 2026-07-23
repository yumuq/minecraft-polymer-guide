---
layout: default
title: 文档导航
---

# Minecraft Polymer 适配指南

**完整的 Polymer 模组适配教程和参考手册**

---

## 📚 快速导航

### 🎯 核心文档

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; margin: 20px 0;">

<div style="border: 1px solid #ddd; padding: 15px; border-radius: 5px;">
<h4>📖 <a href="01-核心概念">核心概念</a></h4>
<p>Polymer 是什么、为什么需要、工作原理</p>
<span style="color: #666;">⭐ 入门必读</span>
</div>

<div style="border: 1px solid #ddd; padding: 15px; border-radius: 5px;">
<h4>📚 <a href="02-理论基础">理论基础</a></h4>
<p>深入理解 Mixin、注册表、网络协议</p>
<span style="color: #666;">⭐⭐ 进阶</span>
</div>

<div style="border: 1px solid #ddd; padding: 15px; border-radius: 5px;">
<h4>🔍 <a href="03-模组分类">模组分类</a></h4>
<p>判断模组类型、选择适配策略</p>
<span style="color: #666;">⭐⭐ 重要</span>
</div>

</div>

---

### 🔧 实战指南

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; margin: 20px 0;">

<div style="border: 1px solid #ddd; padding: 15px; border-radius: 5px;">
<h4>🛠️ <a href="04-环境准备">环境准备</a></h4>
<p>JDK、Gradle、IDE 配置</p>
<span style="color: #666;">⭐ 基础</span>
</div>

<div style="border: 1px solid #ddd; padding: 15px; border-radius: 5px;">
<h4>⚙️ <a href="05-适配流程">适配流程</a></h4>
<p>完整的 5 步适配流程</p>
<span style="color: #666;">⭐⭐ 实战</span>
</div>

<div style="border: 1px solid #ddd; padding: 15px; border-radius: 5px;">
<h4>📝 <a href="06-代码模板">代码模板</a></h4>
<p>可直接使用的代码模板</p>
<span style="color: #666;">⭐ 速查</span>
</div>

</div>

---

### 🐛 问题解决

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; margin: 20px 0;">

<div style="border: 1px solid #ddd; padding: 15px; border-radius: 5px;">
<h4>🔧 <a href="07-常见错误">常见错误</a></h4>
<p>错误排查矩阵和解决方案</p>
<span style="color: #666;">⭐⭐ 必备</span>
</div>

<div style="border: 1px solid #ddd; padding: 15px; border-radius: 5px;">
<h4>🔥 <a href="08-疑难杂症">疑难杂症</a></h4>
<p>复杂问题的深度解决</p>
<span style="color: #666;">⭐⭐⭐ 高级</span>
</div>

</div>

---

### 📦 案例分析

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin: 20px 0;">

<div style="border: 2px solid #4CAF50; padding: 20px; border-radius: 5px;">
<h4>🎯 <a href="09-案例-EasyAnvils">Easy Anvils</a></h4>
<p><strong>服务器端模组案例</strong></p>
<ul style="margin: 10px 0; padding-left: 20px;">
<li>自定义方块伪装</li>
<li>BlockEntity 处理</li>
<li>原版客户端 100% 可用</li>
</ul>
<span style="color: #666;">⭐⭐⭐ 难度：中等 | 时间：2-3小时</span>
<br><br>
<a href="https://github.com/yumuq/polymer-of-easy-anvils" style="color: #4CAF50;">🔗 GitHub 仓库</a>
</div>

<div style="border: 2px solid #2196F3; padding: 20px; border-radius: 5px;">
<h4>⚡ <a href="10-案例-QuickShulker">Quick Shulker</a></h4>
<p><strong>混合驱动模组案例</strong></p>
<ul style="margin: 10px 0; padding-left: 20px;">
<li>仅菜单注册</li>
<li>最小化适配</li>
<li>部分功能可用</li>
</ul>
<span style="color: #666;">⭐ 难度：极简 | 时间：30分钟</span>
<br><br>
<a href="https://github.com/yumuq/polymer-of-quickshulker" style="color: #2196F3;">🔗 GitHub 仓库</a>
</div>

</div>

---

### 💡 参考资料

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; margin: 20px 0;">

<div style="border: 1px solid #ddd; padding: 15px; border-radius: 5px;">
<h4>⭐ <a href="11-最佳实践">最佳实践</a></h4>
<p>代码规范、性能优化、测试策略</p>
<span style="color: #666;">⭐⭐ 提升</span>
</div>

<div style="border: 1px solid #ddd; padding: 15px; border-radius: 5px;">
<h4>🔖 <a href="12-快速参考">快速参考</a></h4>
<p>命令速查、API 速查、检查清单</p>
<span style="color: #666;">⭐ 速查</span>
</div>

</div>

---

## 🚀 推荐学习路径

### 路径 1：完全新手

1. [01-核心概念](01-核心概念) - 理解 Polymer
2. [03-模组分类](03-模组分类) - 学会判断
3. [09-案例-EasyAnvils](09-案例-EasyAnvils) 或 [10-案例-QuickShulker](10-案例-QuickShulker) - 学习案例
4. [05-适配流程](05-适配流程) - 开始实战

### 路径 2：有经验的开发者

1. [03-模组分类](03-模组分类) - 快速判断
2. [06-代码模板](06-代码模板) - 复制模板
3. [07-常见错误](07-常见错误) - 遇到问题查阅

### 路径 3：遇到问题

1. [07-常见错误](07-常见错误) - 查找常见问题
2. [08-疑难杂症](08-疑难杂症) - 复杂问题
3. [12-快速参考](12-快速参考) - 命令速查

---

## 📊 文档统计

- **文档数量：** 13 个
- **总行数：** 7,590+ 行
- **代码示例：** 100+ 个
- **完整案例：** 2 个
- **错误解决方案：** 50+ 个

---

## 🔗 相关资源

### 官方文档
- [Polymer 官网](https://polymer.pb4.eu/)
- [Polymer GitHub](https://github.com/Patbox/polymer)
- [Fabric 文档](https://fabricmc.net/wiki/)

### 案例项目
- [Easy Anvils Polymer](https://github.com/yumuq/polymer-of-easy-anvils)
- [Quick Shulker Polymer](https://github.com/yumuq/polymer-of-quickshulker)

---

## 📞 获取帮助

- **GitHub Issues:** [提交问题](https://github.com/yumuq/minecraft-polymer-guide/issues)
- **GitHub Repo:** [项目主页](https://github.com/yumuq/minecraft-polymer-guide)

---

<div style="text-align: center; margin: 40px 0; padding: 20px; background-color: #f5f5f5; border-radius: 5px;">
<h3>📖 准备好开始了吗？</h3>
<p>从 <a href="01-核心概念">核心概念</a> 开始您的 Polymer 适配之旅！</p>
</div>
