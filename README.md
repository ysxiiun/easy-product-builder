# easy-product-builder

`easy-product-builder` 是一个用于产品设计澄清与规格文档生成的 skill。

它面向这样一类问题：用户只有一句话级别的需求，方向大致明确，但流程、规则、页面、状态、边界还没有展开。这个 skill 的作用，是通过多轮结构化追问，把这些模糊想法收束成一份清晰、可执行的 `PRD` 或 `Product Spec`。

这个 skill 负责产品设计，不负责 `MRD`，也不进入实现开发。

## 亮点

- 基于一句话需求启动，而不是要求用户先写长篇需求说明
- 通过多轮高价值追问，逐步补齐用户、场景、流程、规则、页面与边界
- 内置决策记录机制，能沉淀已确认项、待确认项、被排除方案和关键假设
- 当产品包含用户界面时，可继续生成线框说明和 AI 原型提示词
- AI 功能按需启用，不会默认把所有产品都写成 AI 项目
- 明确限制在产品设计层，不滑向代码实现、接口设计和技术方案

## 适用场景

- 从 0 到 1 设计一个新产品、应用、工具或内部系统
- 对已有产品新增功能并更新 `PRD` 或 `Product Spec`
- 将聊天式需求讨论整理成结构化规格文档
- 为有界面的产品补充页面结构、线框说明和原型提示词

## 不适用场景

- 进行市场分析、商业价值判断、立项论证
- 输出 `MRD`
- 编写代码、接口方案、技术实现方案
- 将产品需求直接推进到开发任务拆解

## 核心能力

### 1. 一句话需求展开

从一句话需求出发，优先确认：
- 这是什么产品或功能
- 谁会使用
- 用户要完成的核心任务是什么
- 一期必须覆盖的范围是什么
- 是否包含用户界面

### 2. 核心流程与规则设计

通过追问补齐：
- 主路径
- 关键对象
- 状态定义
- 触发条件
- 业务规则
- 边界情况

### 3. 决策收束与记录

在多轮对话中，维护轻量决策账本，至少记录：
- 原始一句话需求
- 已确认决策
- 待确认项
- 被否决方案
- 关键假设
- 术语定义

### 4. UI / 原型分支

当产品包含用户界面时，继续澄清：
- 核心页面
- 导航结构
- 页面目标
- 页面字段与动作
- 零状态、空状态、加载态、错误态
- 桌面端与移动端差异

并可产出：
- `Wireframe.md`
- `UI-Prototype-Prompt.md`

### 5. 规格文档生成与迭代

支持两种工作模式：
- 0-1 模式：生成新的 `Product-Spec.md` 或 `PRD.md`
- 迭代模式：直接更新已有规格文档，并在必要时追加 `Product-Spec-CHANGELOG.md`

## 工作方式

### 0-1 模式

当目录下没有现成规格文档时，skill 会：

1. 确认产品设计骨架
2. 抽取核心流程
3. 补齐可执行细节
4. 按需展开 UI / 原型分支
5. 按需展开 AI 分支
6. 生成完整规格文档

### 迭代模式

当目录下已经存在规格文档时，skill 会：

1. 识别这次改动影响什么
2. 按变更深度继续追问
3. 原地更新现有规格文档
4. 必要时追加变更记录
5. 如果影响界面结构，同步更新 `Wireframe.md` 或 `UI-Prototype-Prompt.md`

## 默认产物

根据任务不同，可能输出：
- `Product-Spec.md`
- `PRD.md`
- 现有规格文档更新稿
- `Product-Spec-CHANGELOG.md`
- `Product-Decision-Log.md`
- `Wireframe.md`
- `UI-Prototype-Prompt.md`

## 仓库结构

```text
easy-product-builder/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    ├── changelog-template.md
    ├── product-spec-template.md
    ├── system-prompt-template.md
    ├── ui-prompt-template.md
    └── wireframe-template.md
```

## 文件说明

- `SKILL.md`
  技能主体定义，包含范围边界、工作原则、工作流、提问策略和完成标准。

- `references/product-spec-template.md`
  默认 `PRD / Product Spec` 模板。

- `references/changelog-template.md`
  规格文档在迭代过程中的变更记录模板。

- `references/system-prompt-template.md`
  产品包含 AI 功能时使用的系统提示词模板。

- `references/wireframe-template.md`
  界面线框说明模板。

- `references/ui-prompt-template.md`
  AI 可识别的原型提示词模板。

- `agents/openai.yaml`
  用于描述 skill 的展示元数据。

## 使用方法

将 skill 放在可被 Codex 发现的 skills 目录中，然后直接用自然语言触发与产品规格相关的任务，例如：

- “帮我把这个一句话需求整理成 Product Spec”
- “我有一个后台工具需求，帮我梳理一期 PRD”
- “帮我更新现有 PRD，补上界面结构和线框说明”

## 推荐交互方式

为了让输出质量更高，建议用户尽量先提供这些信息中的一部分：
- 产品大致是什么
- 谁会使用
- 用户要完成什么核心任务
- 已经确定的功能点
- 是否包含用户界面
- 当前最不清楚的部分

即使信息不完整，skill 也会通过追问继续补齐。

## 当前状态

当前项目已包含：
- 一份中文 skill 定义
- 五份参考模板
- 一份基础元数据配置

可以直接作为一个独立的产品规格与原型构建 skill 使用。
