---
layout: default
title: 文档导航
---

<style>
  .hero { text-align: center; padding: 40px 20px; background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 10px; margin-bottom: 30px; }
  .hero h1 { font-size: 2.5em; margin-bottom: 10px; }
  .hero p { font-size: 1.2em; opacity: 0.9; margin-bottom: 20px; }
  .hero .badges { display: flex; justify-content: center; gap: 10px; flex-wrap: wrap; }
  .hero .badge { background: rgba(255,255,255,0.2); padding: 5px 15px; border-radius: 20px; font-size: 0.9em; }

  .section-title { font-size: 1.5em; margin: 30px 0 15px; padding-bottom: 5px; border-bottom: 2px solid #667eea; display: flex; align-items: center; gap: 10px; }

  .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 16px; margin: 15px 0 30px; }

  .card { border: 1px solid #e0e0e0; border-radius: 8px; padding: 20px; transition: all 0.2s; background: white; text-decoration: none; display: block; color: inherit; }
  .card:hover { transform: translateY(-3px); box-shadow: 0 8px 25px rgba(0,0,0,0.12); border-color: #667eea; }
  .card .icon { font-size: 2em; margin-bottom: 8px; }
  .card h4 { margin: 0 0 8px; font-size: 1.1em; }
  .card h4 a { color: #667eea; text-decoration: none; }
  .card p { margin: 0 0 8px; color: #555; font-size: 0.95em; line-height: 1.5; }
  .card .tag { display: inline-block; background: #f0f0f0; padding: 3px 10px; border-radius: 12px; font-size: 0.8em; color: #777; }

  .case-study { border: 2px solid #e0e0e0; padding: 25px; border-radius: 8px; margin: 15px 0 30px; background: #fafafa; }
  .case-study.easy { border-left: 4px solid #4CAF50; }
  .case-study.quick { border-left: 4px solid #2196F3; }
  .case-study h3 { margin-top: 0; }
  .case-study ul { margin: 10px 0; padding-left: 20px; }
  .case-study li { margin: 5px 0; }
  .case-study .links { margin-top: 15px; display: flex; gap: 10px; flex-wrap: wrap; }
  .case-study .links a { display: inline-block; padding: 8px 18px; border-radius: 5px; text-decoration: none; font-weight: bold; font-size: 0.9em; }
  .btn-primary { background: #667eea; color: white !important; }
  .btn-outline { border: 2px solid #667eea; color: #667eea !important; }

  .path { background: #fff; border: 1px solid #e0e0e0; border-radius: 8px; padding: 20px; margin: 15px 0; }
  .path h4 { margin-top: 0; }
  .path ol { margin: 10px 0 0; padding-left: 20px; }
  .path ol li { margin: 6px 0; }

  .footer { text-align: center; margin: 40px 0 20px; padding: 30px; background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; border-radius: 10px; }
  .footer h3 { margin: 0 0 10px; font-size: 1.4em; }
  .footer p { margin: 0; opacity: 0.9; }
  .footer a { color: white; font-weight: bold; }

  @media (max-width: 600px) {
    .hero h1 { font-size: 1.8em; }
    .grid { grid-template-columns: 1fr; }
  }
</style>

<div class="hero">
  <h1>📚 Minecraft Polymer 适配指南</h1>
  <p>完整的 Polymer 模组适配教程和参考手册</p>
  <div class="badges">
    <span class="badge">📖 13 个文档</span>
    <span class="badge">💻 100+ 代码示例</span>
    <span class="badge">📦 2 个完整案例</span>
    <span class="badge">🐛 50+ 错误解决方案</span>
  </div>
</div>

---

## 🎯 核心文档

<div class="grid" markdown="0">
  <a class="card" href="01-核心概念">
    <div class="icon">📖</div>
    <h4>核心概念</h4>
    <p>Polymer 是什么、为什么需要、工作原理和架构</p>
    <span class="tag">⭐ 入门必读</span>
  </a>
  <a class="card" href="02-理论基础">
    <div class="icon">📚</div>
    <h4>理论基础</h4>
    <p>深入理解 Mixin 软实现、注册表同步和网络协议</p>
    <span class="tag">⭐⭐ 进阶</span>
  </a>
  <a class="card" href="03-模组分类">
    <div class="icon">🔍</div>
    <h4>模组分类</h4>
    <p>学习判断模组类型，选择正确的适配策略</p>
    <span class="tag">⭐⭐ 重要</span>
  </a>
</div>

---

## 🔧 实战指南

<div class="grid" markdown="0">
  <a class="card" href="04-环境准备">
    <div class="icon">🛠️</div>
    <h4>环境准备</h4>
    <p>JDK 25、Gradle 9.x、IDE 配置和依赖管理</p>
    <span class="tag">⭐ 基础</span>
  </a>
  <a class="card" href="05-适配流程">
    <div class="icon">⚙️</div>
    <h4>适配流程</h4>
    <p>从分析到测试的完整 5 步适配操作流程</p>
    <span class="tag">⭐⭐ 实战</span>
  </a>
  <a class="card" href="06-代码模板">
    <div class="icon">📝</div>
    <h4>代码模板</h4>
    <p>PolymerBlock、Menu、BlockEntity 等可复用模板</p>
    <span class="tag">⭐ 速查</span>
  </a>
</div>

---

## 🐛 问题解决

<div class="grid" markdown="0">
  <a class="card" href="07-常见错误">
    <div class="icon">🐛</div>
    <h4>常见错误</h4>
    <p>错误分类、排查矩阵和快速解决方案</p>
    <span class="tag">⭐⭐ 必备</span>
  </a>
  <a class="card" href="08-疑难杂症">
    <div class="icon">🔥</div>
    <h4>疑难杂症</h4>
    <p>构建冲突、性能问题、兼容性等深度问题</p>
    <span class="tag">⭐⭐⭐ 高级</span>
  </a>
</div>

---

## 📦 案例分析

<div class="case-study easy" markdown="1">
<h3>🎯 Easy Anvils — <small>服务器端模组</small></h3>
<p><strong>学习重点：</strong>自定义方块伪装、BlockEntity 过滤、属性映射、复杂 Mixin 实现</p>

| 核心特征 | 说明 |
|---------|------|
| **自定义方块** | ✅ 3 个（需要 PolymerBlock） |
| **BlockEntity** | ✅ 1 个（需要 NBT 过滤） |
| **自定义菜单** | ✅ 1 个（需要隐藏） |
| **原版客户端** | ✅ 100% 功能可用 |
| **适配难度** | ⭐⭐⭐ 中等 |
| **预计时间** | 2-3 小时 |

<div class="links">
  <a class="btn-primary" href="09-案例-EasyAnvils">📖 阅读案例分析</a>
  <a class="btn-outline" href="https://github.com/yumuq/polymer-of-easy-anvils">🔗 GitHub 仓库</a>
</div>
</div>

<div class="case-study quick" markdown="1">
<h3>⚡ Quick Shulker — <small>混合驱动模组</small></h3>
<p><strong>学习重点：</strong>最小化适配、菜单注册、功能可用性评估</p>

| 核心特征 | 说明 |
|---------|------|
| **自定义方块** | ❌ 无 |
| **自定义菜单** | ✅ 1 个（仅需注册） |
| **网络包** | ✅ 4 个（不影响连接） |
| **原版客户端** | ⚠️ 约 60% 功能可用 |
| **适配难度** | ⭐ 极简 |
| **预计时间** | 20-30 分钟 |

<div class="links">
  <a class="btn-primary" href="10-案例-QuickShulker">📖 阅读案例分析</a>
  <a class="btn-outline" href="https://github.com/yumuq/polymer-of-quickshulker">🔗 GitHub 仓库</a>
</div>
</div>

---

## 💡 参考资料

<div class="grid" markdown="0">
  <a class="card" href="11-最佳实践">
    <div class="icon">⭐</div>
    <h4>最佳实践</h4>
    <p>代码规范、性能优化、测试策略和发布流程</p>
    <span class="tag">⭐⭐ 提升</span>
  </a>
  <a class="card" href="12-快速参考">
    <div class="icon">🔖</div>
    <h4>快速参考</h4>
    <p>命令速查、API 速查、检查清单、版本对照</p>
    <span class="tag">⭐ 速查</span>
  </a>
</div>

---

## 🚀 推荐学习路径

<div class="grid" markdown="0">
  <div class="path">
    <h4>🌱 完全新手</h4>
    <ol>
      <li><a href="01-核心概念">核心概念</a> — 理解 Polymer</li>
      <li><a href="03-模组分类">模组分类</a> — 学会判断</li>
      <li><a href="10-案例-QuickShulker">Quick Shulker 案例</a> — 先看简单的</li>
      <li><a href="09-案例-EasyAnvils">Easy Anvils 案例</a> — 再看复杂的</li>
      <li><a href="05-适配流程">适配流程</a> — 开始实战</li>
    </ol>
  </div>
  <div class="path">
    <h4>🔥 有经验的开发者</h4>
    <ol>
      <li><a href="03-模组分类">模组分类</a> — 快速判断类型</li>
      <li><a href="06-代码模板">代码模板</a> — 复制粘贴</li>
      <li><a href="07-常见错误">常见错误</a> — 遇到问题查阅</li>
    </ol>
  </div>
  <div class="path">
    <h4>🐛 排查问题中</h4>
    <ol>
      <li><a href="07-常见错误">常见错误</a> — 查找错误匹配</li>
      <li><a href="08-疑难杂症">疑难杂症</a> — 深度问题</li>
      <li><a href="12-快速参考">快速参考</a> — 命令速查</li>
    </ol>
  </div>
</div>

---

## 📊 文档统计

| 类别 | 文档数 | 内容覆盖 |
|------|--------|---------|
| 核心理论 | 3 | Polymer 原理、Mixin 机制、架构 |
| 实战操作 | 3 | 环境配置、适配流程、代码模板 |
| 问题排查 | 2 | 常见错误、疑难杂症 |
| 案例学习 | 2 | Easy Anvils、Quick Shulker |
| 参考文档 | 2 | 最佳实践、快速参考 |
| **合计** | **13** | **完整知识体系** |

---

<div class="footer">
  <h3>📖 准备好开始了吗？</h3>
  <p>从 <a href="01-核心概念">核心概念</a> 开始您的 Polymer 适配之旅！</p>
</div>
