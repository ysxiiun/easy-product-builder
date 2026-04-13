# easy-product-builder

`easy-product-builder` 是一个通过连续追问，把一句话需求挖掘成产品规格文档的 skill。

它面向这样一类问题：用户脑子里已经有方向，但流程、规则、页面、状态、边界还没真正想清楚。这个 skill 不靠一次性脑补，而是通过多轮高价值追问，把这些模糊想法逐步逼成两类可执行文档：

- `Product-Spec.md`
- `UI-Spec.md`

它的重点不是“多生成几份材料”，而是把关键产品决策问出来、定下来、写清楚。

## 核心目标

- 从一句话需求启动，不要求用户先写长篇 PRD
- 通过连续追问，挖掘用户真实想法，而不是替用户空想
- 把产品层决策和界面层决策拆清楚，但不重复写
- 默认沉淀成一份产品规格和一份 UI 规格，而不是一组膨胀的文档包

## 默认输出

默认只围绕两类核心文档工作：

- `Product-Spec.md`
- `UI-Spec.md`：仅在产品包含用户界面时生成或更新

兼容但不默认新增：

- `PRD.md`：可以作为历史输入或用户指定格式参考，但不再默认与 `Product-Spec.md` 同时生成
- `Product-Spec-CHANGELOG.md`：仅在用户明确要求保留迭代记录时追加
- AI 提示词附录：仅在产品确实有 AI 功能，或用户明确要求生成原型提示词时补充

## 适用场景

- 从 0 到 1 设计一个新产品、应用、工具或内部系统
- 对已有产品新增功能并更新产品规格
- 将聊天式需求讨论整理成结构化 spec
- 为有界面的产品补充页面结构和交互说明

## 不适用场景

- 市场分析、商业论证、立项判断
- 输出 MRD
- 编写代码、接口设计、技术实现方案
- 直接做开发任务拆解

## 工作方式

### 1. 先把产品定义问出来

优先确认：
- 这是什么产品或功能
- 谁会使用
- 用户要完成什么核心任务
- 一期必须覆盖什么
- 现有方式为什么不够用

### 2. 再把主流程和规则问清楚

重点逼近：
- 核心对象
- 状态定义
- 触发条件
- 业务规则
- 边界与异常情况

### 3. 有界面时再展开 UI 分支

只有当产品真的包含界面时，才继续追问：
- 核心页面
- 导航结构
- 页面目标
- 字段和动作
- 零状态、空状态、加载态、错误态
- 桌面端 / 移动端差异

然后沉淀到 `UI-Spec.md`。

### 4. 最终输出双文档或单文档

- 无界面产品：输出 `Product-Spec.md`
- 有界面产品：输出 `Product-Spec.md` + `UI-Spec.md`

## 文档边界

`Product-Spec.md` 负责：
- 产品定位
- 用户与场景
- 一期范围
- 主流程
- 核心对象与状态
- 业务规则
- 验收标准

`UI-Spec.md` 负责：
- 页面结构
- 导航与入口
- 页面级字段与动作
- 页面状态
- 关键交互约束

这样做的目的，是避免一份主文档已经写了页面说明，外面又再套一份线框文档和一份原型提示词，导致内容重复。

## 当前模板

项目当前包含以下参考模板：

- [SKILL.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/SKILL.md)
- [references/product-spec-template.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/references/product-spec-template.md)
- [references/ui-spec-template.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/references/ui-spec-template.md)
- [references/changelog-template.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/references/changelog-template.md)
- [references/system-prompt-template.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/references/system-prompt-template.md)
- [references/ui-prompt-template.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/references/ui-prompt-template.md)

`wireframe-template.md` 已不再作为默认主流程模板使用。

## 使用示例

- “帮我把这个一句话需求梳理成 Product Spec”
- “我只有一个很模糊的后台工具想法，帮我通过追问整理成 spec”
- “帮我更新现有规格，并把 UI 部分单独沉淀成 UI Spec”
- “先别写代码，先把产品和页面方案问清楚”
