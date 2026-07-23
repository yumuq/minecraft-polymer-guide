# 10 - 案例分析：Quick Shulker

**文档版本：** 2.0.0  
**最后更新：** 2026-07-23  
**项目地址：** https://github.com/yumuq/polymer-of-quickshulker

---

## 项目概览

### 原始模组信息

| 属性 | 值 |
|------|-----|
| **名称** | Quick Shulker |
| **版本** | 3.0.1-26.1 |
| **Minecraft** | 26.1.2 |
| **作者** | kyrptonaught, MoRanpcy, Hao_cen, Grayer0113 |
| **功能** | 快速打开潜影盒、末影箱等容器 |
| **类型** | 混合驱动模组 |

### 核心功能

**两层功能架构：**

**第 1 层：基础右键功能**
- ✅ 右键手持潜影盒 → 打开
- ✅ 右键手持末影箱 → 打开
- ✅ 右键手持工作台 → 打开
- ✅ 右键手持铁砧 → 打开
- ✅ 右键手持捆绑物品 → 打开

**第 2 层：高级快捷键功能**
- ❌ 按键从背包快速打开
- ❌ 按键打开玩家背包
- ❌ 后台快速操作

---

## 模组架构分析

### 注册表项审计

**菜单类型注册：**
```java
// MenuTypes.java
public static final MenuType<BundleItemMenu> BUNDLE_ITEM = Registry.register(
    BuiltInRegistries.MENU,
    Identifier.fromNamespaceAndPath(QuickShulkerMod.MOD_ID, "bundle_item"),
    new MenuType<>(BundleItemMenu::new, FeatureFlagSet.of())
);
```

**网络包注册：**
```java
// QuickShulkerMod.java
PayloadTypeRegistry.clientboundPlay().register(OpenShulkerPacket.ID, OpenShulkerPacket.CODEC);
PayloadTypeRegistry.serverboundPlay().register(OpenShulkerPacket.ID, OpenShulkerPacket.CODEC);

PayloadTypeRegistry.clientboundPlay().register(OpenInventoryPacket.ID, OpenInventoryPacket.CODEC);
PayloadTypeRegistry.serverboundPlay().register(OpenInventoryPacket.ID, OpenInventoryPacket.CODEC);

PayloadTypeRegistry.clientboundPlay().register(QuickBundlePacket.ID, QuickBundlePacket.CODEC);
PayloadTypeRegistry.serverboundPlay().register(QuickBundlePacket.ID, QuickBundlePacket.CODEC);

PayloadTypeRegistry.clientboundPlay().register(EnderChestS2CSyncPacket.ID, EnderChestS2CSyncPacket.CODEC);
```

**关键发现：**
- ✅ 1 个自定义菜单类型
- ⚠️ 4 个自定义网络包
- ❌ 无自定义方块
- ❌ 无自定义物品
- ❌ 无 BlockEntity

**结论：** 极简的注册表结构，但有网络通信层

---

### 交互流程分析

#### 场景 A：右键手持潜影盒（原版客户端可用）

```
原版客户端                          服务器
     │                                │
     │ 1. 右键（手持潜影盒）              │
     ├────────────────────────────────►│
     │    原版 UseItemCallback 事件     │
     │                                 │ 2. Quick Shulker 拦截
     │                                 │    if (item instanceof ShulkerBoxItem)
     │                                 │
     │                                 │ 3. 打开容器菜单
     │                                 │    player.openMenu(...)
     │                                 │
     │ 4. 接收菜单数据包                 │
     │◄────────────────────────────────┤
     │    原版 OpenScreen 协议          │
     │                                 │
     │ 5. 显示容器 GUI                  │
     │                                 │
```

**关键点：**
- ✅ 使用原版 `UseItemCallback` 事件
- ✅ 使用原版 `openMenu` 方法
- ✅ 客户端-服务器通信全程使用原版协议
- ✅ **原版客户端完全可用**

---

#### 场景 B：快捷键快速打开（原版客户端不可用）

```
模组客户端                          服务器
     │                                │
     │ 1. 按下快捷键                    │
     │    (客户端代码)                  │
     │                                 │
     │ 2. 扫描背包                      │
     │    找到潜影盒在第 X 槽位           │
     │    (客户端代码)                  │
     │                                 │
     │ 3. 发送自定义网络包               │
     ├────────────────────────────────►│
     │    OpenShulkerPacket {slot: X}  │
     │                                 │ 4. 接收网络包
     │                                 │    从槽位 X 获取潜影盒
     │                                 │
     │                                 │ 5. 打开容器
     │                                 │    player.openMenu(...)
     │                                 │
     │ 6. 接收菜单数据包                 │
     │◄────────────────────────────────┤

原版客户端
     │
     ❌ 没有快捷键代码
     ❌ 无法扫描背包
     ❌ 无法发送 OpenShulkerPacket
     ❌ 功能完全不可用
```

**关键点：**
- ❌ 需要客户端快捷键绑定
- ❌ 需要客户端背包扫描逻辑
- ❌ 需要客户端发送自定义网络包
- ❌ **原版客户端完全不可用**

---

### 功能可用性评估

| 功能 | 触发方式 | 协议类型 | 原版客户端 |
|------|---------|---------|-----------|
| **右键潜影盒** | 右键 | 原版 | ✅ 可用 |
| **右键末影箱** | 右键 | 原版 | ✅ 可用 |
| **右键工作台** | 右键 | 原版 | ✅ 可用 |
| **右键铁砧** | 右键 | 原版 | ✅ 可用 |
| **右键捆绑物品** | 右键 | 原版 | ✅ 可用 |
| **快捷键快速打开** | 按键 | 自定义 | ❌ 不可用 |
| **快捷键打开背包** | 按键 | 自定义 | ❌ 不可用 |

**可用率：** 约 60% （5/7 功能可用）

---

## Polymer 适配过程

### Phase 1: 环境准备

#### 步骤 1.1: 获取源码

```bash
# 从 GitHub 下载
wget https://github.com/MoRanpcy/quickshulker/archive/refs/tags/3.0.1-26.1.zip

# 解压
unzip 3.0.1-26.1.zip -d quickshulker-src/
cd quickshulker-src/quickshulker-3.0.1-26.1/
```

#### 步骤 1.2: 验证原始构建

```bash
./gradlew build --no-daemon
```

**遇到问题：** ModMenu 依赖不可用

**错误信息：**
```
Could not find com.terraformersmc:modmenu:18.0.0-alpha.8
```

**解决方案：**
```gradle
// 注释掉 ModMenu 依赖
// implementation("com.terraformersmc:modmenu:18.0.0-alpha.8")
```

删除相关文件：
```bash
rm src/main/java/.../ModMenuIntegration.java
```

清理 fabric.mod.json：
```json
{
  "entrypoints": {
    "main": [...],
    "client": [...]
    // 删除 "modmenu" 入口点
  }
}
```

**结果：** ✅ 构建成功

---

### Phase 2: 添加 Polymer 依赖

**文件：** `build.gradle`

```gradle
repositories {
    maven { url 'https://maven.fabricmc.net' }
    // ... 其他仓库
    
    // 添加 Polymer 仓库
    maven {
        name = "Nucleoid"
        url = "https://maven.nucleoid.xyz"
    }
}

dependencies {
    minecraft "com.mojang:minecraft:${project.minecraft_version}"
    implementation "net.fabricmc:fabric-loader:${project.loader_version}"
    implementation "net.fabricmc.fabric-api:fabric-api:${project.fabric_api_version}"
    
    // 其他依赖...
    
    // Polymer Core
    implementation "eu.pb4:polymer-core:0.16.5+26.1.2"
    include "eu.pb4:polymer-core:0.16.5+26.1.2"
}
```

**关键点：**
- 使用 `implementation`（编译时需要）
- 使用 `include`（打包到 JAR）
- 版本号匹配 Minecraft 26.1.2

---

### Phase 3: 添加 Polymer 注册

**文件：** `src/main/java/.../QuickShulkerMod.java`

**修改前：**
```java
package net.kyrptonaught.quickshulker;

import net.fabricmc.api.ModInitializer;

public class QuickShulkerMod implements ModInitializer {
    
    @Override
    public void onInitialize() {
        // 注册网络包
        registerNetworkPackets();
        
        // 注册菜单类型
        if(getConfig().quickBundle) MenuTypes.registerMenuTypes();
        
        // 其他初始化...
    }
}
```

**修改后：**
```java
package net.kyrptonaught.quickshulker;

import eu.pb4.polymer.core.api.other.PolymerMenuUtils;  // ← 添加导入
import net.fabricmc.api.ModInitializer;

public class QuickShulkerMod implements ModInitializer {
    
    @Override
    public void onInitialize() {
        // 注册网络包
        registerNetworkPackets();
        
        // 注册菜单类型
        if(getConfig().quickBundle) MenuTypes.registerMenuTypes();
        
        // Polymer 适配：注册自定义菜单类型
        // 防止 quickshulker:bundle_item 同步到原版客户端
        // 允许原版客户端连接服务器而不会出现 RemapException
        PolymerMenuUtils.registerType(MenuTypes.BUNDLE_ITEM);  // ← 添加这行
        
        // 其他初始化...
    }
}
```

**就这么简单！** 只需要：
1. 添加 1 行 import
2. 添加 1 行注册代码

---

### Phase 4: 构建和验证

```bash
./gradlew clean build --no-daemon
```

**结果：** ✅ BUILD SUCCESSFUL in 2m 7s

**验证 JAR：**
```bash
# 检查 Polymer 依赖
unzip -l build/libs/quickshulker-3.0.1-26.1.jar | grep polymer
# 输出：META-INF/jars/polymer-core-0.16.5+26.1.2.jar

# 检查文件大小
ls -lh build/libs/quickshulker-3.0.1-26.1.jar
# 906 KB (vs 原始 275 KB)
# 增加是因为包含了 Polymer Core (704 KB)
```

---

## 测试结果

### 模组客户端测试

**环境：**
- Minecraft 26.1.2 + Fabric Loader 0.18.4
- Quick Shulker 3.0.1-Polymer

**测试项：**
- ✅ 可以连接服务器
- ✅ 右键手持潜影盒 → 打开
- ✅ 右键手持末影箱 → 打开
- ✅ 右键手持工作台 → 打开
- ✅ 右键手持铁砧 → 打开
- ✅ 右键手持捆绑物品 → 打开
- ✅ 快捷键从背包快速打开 → 正常
- ✅ 快捷键打开玩家背包 → 正常
- ✅ 所有快捷键功能正常

**结论：** 100% 功能正常

---

### 原版客户端测试

**环境：** 原版 Minecraft 26.1.2（无任何模组）

**测试项：**

**1. 连接测试**
- ✅ 可以连接服务器
- ✅ 无注册表错误
- ✅ 无 RemapException
- ✅ 无断开连接

**2. 基础功能测试（右键）**

测试手持潜影盒右键：
- ✅ 潜影盒 GUI 正常打开
- ✅ 可以查看内部物品
- ✅ 可以存取物品
- ✅ 物品数据保存正确
- ✅ 关闭后潜影盒保持在手中

测试手持末影箱右键：
- ✅ 末影箱 GUI 正常打开
- ✅ 可以访问末影箱内容
- ✅ 物品同步正确

测试手持工作台右键：
- ✅ 工作台 GUI 正常打开
- ✅ 可以进行合成
- ✅ 配方正常工作

测试手持铁砧右键：
- ✅ 铁砧 GUI 正常打开
- ✅ 可以修复物品
- ✅ 可以重命名物品
- ✅ 经验消耗正常

测试手持捆绑物品右键：
- ✅ 捆绑物品 GUI 正常打开
- ✅ 可以查看内容
- ✅ 可以添加/移除物品

**3. 高级功能测试（快捷键）**

尝试使用快捷键：
- ❌ 无法绑定快捷键（游戏中没有快捷键选项）
- ❌ 按任何键都无法触发快速打开
- ❌ 无法从背包直接打开潜影盒

**原因分析：**
- 原版客户端没有 Quick Shulker 的客户端代码
- 没有快捷键绑定系统
- 没有背包扫描逻辑
- 无法发送自定义网络包

**结论：** 基础功能 100% 可用，高级功能不可用

---

## 功能对比

| 功能 | 模组客户端 | 原版客户端 | 可用性 |
|------|-----------|-----------|--------|
| **右键手持潜影盒** | ✅ | ✅ | 100% |
| **右键手持末影箱** | ✅ | ✅ | 100% |
| **右键手持工作台** | ✅ | ✅ | 100% |
| **右键手持铁砧** | ✅ | ✅ | 100% |
| **右键手持捆绑物品** | ✅ | ✅ | 100% |
| **快捷键快速打开** | ✅ | ❌ | 0% |
| **快捷键打开背包** | ✅ | ❌ | 0% |
| **总体可用率** | **100%** | **~60%** | - |

---

## 与 Easy Anvils 的对比

### 架构差异

| 维度 | Easy Anvils | Quick Shulker |
|------|-------------|---------------|
| **注册项数量** | 多（方块+实体+菜单） | 少（仅菜单） |
| **自定义方块** | ✅ 3 个 | ❌ 无 |
| **BlockEntity** | ✅ 1 个 | ❌ 无 |
| **自定义菜单** | ✅ 1 个 | ✅ 1 个 |
| **网络包** | ❌ 无 | ✅ 4 个 |
| **Mixin 需求** | ✅ 需要（方块伪装） | ❌ 不需要 |

---

### 适配难度

| 维度 | Easy Anvils | Quick Shulker |
|------|-------------|---------------|
| **代码修改量** | ~100 行 | ~10 行 |
| **Mixin 配置** | 需要 | 不需要 |
| **PolymerBlock** | 需要实现 | 不需要 |
| **时间成本** | 2-3 小时 | 30 分钟 |
| **难度等级** | ⭐⭐⭐ 中等 | ⭐ 极简 |

---

### 功能可用性

| 维度 | Easy Anvils | Quick Shulker |
|------|-------------|---------------|
| **原版客户端** | 100% | ~60% |
| **触发方式** | 纯服务器端 | 混合驱动 |
| **交互协议** | 全原版 | 原版+自定义 |
| **视觉效果** | 原版材质 | 原版（无影响） |

---

## 关键技术点总结

### 1. 为什么适配如此简单？

**Easy Anvils 需要：**
```
1. 创建 Mixin 配置文件
2. 实现 PolymerBlock 接口（方块伪装）
3. 注册 BlockEntity
4. 注册菜单类型
5. 处理属性映射
6. 大量代码（~100 行）
```

**Quick Shulker 只需要：**
```
1. 注册菜单类型
2. 一行代码
```

**原因：**
- ❌ 没有自定义方块 → 不需要 PolymerBlock
- ❌ 没有 BlockEntity → 不需要 PolymerBlockUtils
- ✅ 只有 1 个菜单类型 → 只需 PolymerMenuUtils

---

### 2. 网络包为什么不影响连接？

**关键理解：** Polymer 解决的是**注册表同步**问题，不是网络包问题。

**注册表同步发生在：**
```
客户端连接时：
1. 服务器发送注册表列表（方块、物品、菜单等）
2. 客户端对比自己的注册表
3. 不匹配 → RemapException
```

**网络包发生在：**
```
游戏运行时：
1. 客户端/服务器发送数据包
2. 对方处理数据包
3. 如果对方不认识 → 忽略或日志警告（不断开连接）
```

**Quick Shulker 的情况：**
- ✅ 菜单类型 `quickshulker:bundle_item` 会同步 → Polymer 隐藏
- ⚠️ 网络包 `OpenShulkerPacket` 不会同步 → 不影响连接
- ✅ 原版客户端不发送网络包 → 服务器不处理 → 没问题
- ✅ 模组客户端发送网络包 → 服务器处理 → 功能正常

---

### 3. 功能分层设计

**设计良好的分层：**
```
第 1 层（基础层）：
- 使用原版事件（UseItemCallback）
- 使用原版协议
- 原版客户端可用 ✅

第 2 层（增强层）：
- 使用自定义快捷键
- 使用自定义网络包
- 需要模组客户端 ❌
```

**为什么重要？**
- 基础功能对所有玩家可用
- 高级功能是可选增强
- 不会让原版玩家感到"缺失"核心功能

---

### 4. 最小化适配原则

**Easy Anvils：** 必须完整适配
- 有自定义方块 → 必须伪装
- 有 BlockEntity → 必须过滤
- 不适配 = 原版客户端完全不可用

**Quick Shulker：** 最小化适配
- 无自定义方块 → 不需要伪装
- 只有菜单 → 只注册菜单
- 适配成本极低，收益明显

**原则：**
- 只修改必要的部分
- 不要过度工程化
- 保持代码简洁

---

## 经验教训

### 成功经验

1. **快速判断模组类型**
   - 查找注册表项 → 只有菜单
   - 查找交互方式 → 右键 + 快捷键
   - 快速分类 → 混合驱动模组

2. **准确评估功能可用性**
   - 右键功能 → 原版协议 → 可用
   - 快捷键功能 → 自定义协议 → 不可用
   - 清晰告知用户 → 避免误解

3. **最小化修改**
   - 只添加必要的注册
   - 不引入复杂的 Mixin
   - 保持代码简洁

4. **充分测试分层功能**
   - 测试基础功能（右键）
   - 测试高级功能（快捷键）
   - 分别验证两个客户端

---

### 遇到的挑战

1. **ModMenu 依赖问题**
   - 原因：alpha 版本不可用
   - 解决：直接移除依赖
   - 教训：可选依赖应该优雅降级

2. **功能描述的准确性**
   - 初始误判：完全不可用
   - 实际测试：60% 可用
   - 教训：必须实际测试，不能假设

3. **README 的清晰度**
   - 初版：含糊其辞
   - 修正：明确列出可用/不可用功能
   - 教训：用户需要清晰的预期

---

## 适配时间统计

| 阶段 | 时间 | 说明 |
|------|------|------|
| **架构分析** | 15 分钟 | 查找注册项，判断类型 |
| **环境配置** | 10 分钟 | 添加依赖，处理 ModMenu 问题 |
| **代码修改** | 5 分钟 | 添加 1 行注册代码 |
| **构建测试** | 5 分钟 | 构建 JAR，验证内容 |
| **功能测试** | 30 分钟 | 两种客户端详细测试 |
| **文档编写** | 30 分钟 | README 和功能说明 |
| **总计** | **~1.5 小时** | 包含修正 README |

**后续类似项目预计：** 20-30 分钟

---

## 适用模式

### 适合此方案的模组

✅ **混合驱动模组：**
- 基础功能使用原版交互
- 高级功能需要客户端代码
- 可以分层使用

✅ **示例：**
- 快捷操作增强模组
- 可选便利功能模组
- UI 增强模组（有基础交互）

---

### 不适合此方案的模组

❌ **纯快捷键模组：**
- 没有原版交互方式
- 完全依赖客户端
- 适配价值低

❌ **核心功能客户端驱动：**
- 主要功能需要客户端
- 原版客户端体验极差
- 不推荐适配

---

## 文档建议

### README 结构

```markdown
## Vanilla Client Support

⚠️ **Partial functionality for vanilla clients**

### ✅ Works
- Right-click held shulker box to open
- Right-click held ender chest to open
- Right-click held crafting table to use
- Right-click held anvil to use
- Right-click held bundle to open

### ❌ Requires Client Mod
- Hotkey to quick-open from inventory
- Hotkey to open player inventory
- Background quick-access features

### 📊 Summary
- **Basic features:** 100% functional
- **Advanced features:** Requires client mod
- **Recommended:** Install mod on client for full experience
```

### 关键要点

1. **明确可用功能**
   - 列出具体功能
   - 不要含糊其辞

2. **解释限制原因**
   - 为什么快捷键不可用
   - 帮助用户理解

3. **提供解决方案**
   - 推荐安装客户端模组
   - 说明如何获得完整体验

---

## 下一步

- 💡 **[11-最佳实践.md](./11-最佳实践.md)** - 学习优化技巧
- 🔍 **[12-快速参考.md](./12-快速参考.md)** - 命令速查
- 📖 **[02-理论基础.md](./02-理论基础.md)** - 深入理解原理

---

**两个案例都学完了？恭喜！现在您已经掌握了 Polymer 适配的核心技能！** 🎉
