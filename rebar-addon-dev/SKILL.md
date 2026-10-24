---
name: rebar-addon-dev
description: >
  高效开发 Rebar / Pylon 附属插件（addon）。
  通过 LLM 与人类协作来构建性能高，健壮，可玩性高的附属插件。
---

# Rebar 附属开发

## 概览

创建 Rebar 附属，让玩家能够于附属中体验到用户的创作表达。

适用：`Rebar 0.44.4-26.2 / Pylon 0.42.2-26.2 / Paper 26.2 / Java 25` 或自行适配的更新。

---

# 初始化项目

**创建出一个能编译的 jar。**

## 1.1 环境

在中国大陆，开发环境较为重要。

检测本机环境：Java 25、Gradle

若本机无 Java 25，请协助用户下载，并配置环境变量。若机器有其余版本 Java，可以下载到合适目录并在后续配置。

若本机无 Gradle，请检测 Gradle 服务的网络连通性，注意超时。若不通或超时，请协助用户下载离线 ZIP 包至本地。

## 1.2 确立项目根本

| 项 | 说明 |
|---|---|
| 项目名 | 项目的英文和中文名 |
| 主类，group 及 包名 | 例如 `io.github.you.myaddon.MyAddon` |
| 目标版本 | 默认使用 https://github.com/pylonmc/rebar/releases 最新版 |
| 插件设定 | 用户希望此插件添加什么物品或实现哪些功能 |
| 前置依赖 | 是否依赖 Pylon 或其余插件，可以推荐，若无必须不要有前置依赖 |

## 1.3 拉取并配置模板

拉取官方模板：https://github.com/pylonmc/rebar-addon-template

若模板环境与当前最新版本不符，请更改 `build.gradle.kts` 和 `gradle.properties`。

更改 `settings.gradle.kts` 的 `rootProject.name`，以及 `io.github.username.exampleaddon` 以适配用户需求。

询问用户是否使用 Kotlin，若使用则添加 `kotlin("jvm")` 插件、删除 Lombok、并把 `src/main/java` 挪到 `src/main/kotlin`。

## 1.4 编译验证

使用 Gradle 真实编译项目，若遇到问题必须在此步解决。

## 1.5 开发辅助

拉取 Rebar 及 Pylon 源码至本地，作为后续开发时的 API 全权参考。

## 1.6 做开发分析

与用户讨论此项目的设想，讨论其存在的合理性与各处可能用到的细节的设计。

# 跑通第一个流程

## 2.1 基本架构

根据用户的设想，做出最小可行版本，产出有一个方块或一种行为的版本。

## 2.2 注册链路

确保以下链路均存在且正确。

- 方块类实现 `RebarBlock`，新放置 `(Block, BlockCreateContext)`，存档加载 `(Block, PersistentDataContainer)`。
- `RebarBlock.register(key, material, clazz)` 注册类型。
- `onEnable` 调用 `initialize()`。
- `settings/<方块名>.yml` 提供合适数值，使用 `命名空间:方块名`。
- `lang/en.yml`、`lang/zh.yml` 提供名称和 lore。

写法和示例参考官方模板 `ExampleAddonBlocks` 和 `ExampleBlock`。

## 2.3 指南页

使用 `SimpleStaticGuidePage`，`addItem` 挂载内容，并挂载到 `RebarGuide.rootPage` 下。

## 2.4 装进服务器

搭建或使用 runServer 启动服务器并确认无日志报错。

## 2.5 验收

回复用户，协助用户进入游戏完成验收：

- 能够于指南书中拿到名字及 lore 正常的物品
- 在放置后外观正常
- 行为正确
- **服务器重启后，方块及状态正常**
- 控制台无报错

# 迭代循环

明确双方优势：用户需要进入到游戏中得到具体反馈，体验以及感受。

## 3.1 迭代循环

用户描述现象 → 定位具体代码并修改 → 构建和部署 → 用户进入游戏中实测 → 继续迭代。

## 3.2 相同问题多次修改无果。

重新定位并与用户讨论猜测，添加更详细日志以发掘深层原因。

## 3.3 用户明确表达错误时，需要复述理解

描述自己理解的"用户所见和期望"，经用户确认和符合后继续修改。

## 3.4 改动后反馈

修改内容，预期发生。使用户据此判断是否有效。

# 发布

## 4.1 基础准备

- 与用户商量并划定版本号格式和内容
- README 需参考成熟插件编写
- 商量并创建合适的 LICENSE

## 4.3 CI

与用户商量是否构建 workflows 以及什么功能的 workflows

## 4.4 发布Release

用合适的方法发布 Release
