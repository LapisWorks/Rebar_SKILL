# Rebar_SKILL

给 AI 用的 Rebar 附属开发契约。

不是教程，也不是 API 文档。它约束 AI 在写 Rebar 附属时怎么干活：怎么起工程、怎么确认一个 API 真的存在、改不动的时候怎么办、什么情况下不许自己判断。

## 为什么需要

Rebar 官方目前不提供附属开发文档。文档站原话：

> Currently, addon development is not supported due to how rapidly Pylon and Rebar are still changing.

API 也是每个版本都变：

> THE NEXT REBAR VERSION WILL PROBABLY NOT BE COMPATIBLE WITH THE PREVIOUS ONE.

所以这里不写死 API。写死的内容半年就过期，过期了还不报错，只会让人用错。

## 里面有什么

```
rebar-addon-dev/
├── SKILL.md          契约本体
└── references/       按需加载的资料
```

`SKILL.md` 分四个环节：

| 环节 | 做什么 |
|---|---|
| 初始化项目 | 环境检测、确立项目根本、拉官方模板、编译出 jar |
| 跑通第一个流程 | 注册链路、指南页、装进服务器、验收 |
| 迭代循环 | 人机怎么来回改，改不动了怎么办 |
| 发布 | 版本号、CI、打标签 |

## 怎么用

**Claude Code / WorkBuddy 等支持 skills 的工具**

把 `rebar-addon-dev` 整个目录拷进 skills 目录：

```
~/.claude/skills/rebar-addon-dev/
~/.workbuddy-ai/skills/rebar-addon-dev/
```

目录名不要改。`SKILL.md` 的 `name` 字段必须和目录名一致，改了加载不上。

**其他 AI 工具**

直接把 `SKILL.md` 丢进上下文，或者并进项目的 `AGENTS.md`。

## 适用范围

`Rebar 0.44.4-26.2 / Pylon 0.42.2-26.2 / Paper 26.2 / Java 25`

Rebar 升级后，`SKILL.md` 里的 API 名字要重新核对。契约本身（怎么工作）不用改。

## License

MIT
