# easy-product-builder

`easy-product-builder` 是一个通过连续追问，把一句话需求挖掘成产品规格文档的 skill。

它适合这样一类场景：用户脑子里已经有方向，但流程、规则、页面、状态、边界、视觉方向还没真正想清楚。这个 skill 的默认工作方式不是问两轮就写，也不是无休止盘问，而是：

- 先展示一份探讨计划，与用户对齐这次会从哪些方面推进
- 最先确认项目或产品名称
- 先建立会影响 spec 的问题矩阵
- 按主题持续追问必要问题
- 每轮固定只问 3 个问题，并在内部更新 spec 草稿
- 关键问题域覆盖完成后，再输出完整文档

默认输出仍然聚焦两类核心文档：
- `.easy-coding/spec/Product-Spec.md`
- `.easy-coding/spec/UI-Spec.md`

其中 `UI-Spec.md` 不再只写页面和交互，也会正式纳入：
- 视觉方向
- 主题色与色彩策略
- 风格关键词与界面气质
- 布局倾向与信息密度
- 组件表现偏好

## 核心特点

- 默认采用“深挖但有限”的追问方式
- 正式产品设计阶段前，会先展示一份可补充、可修改的探讨计划，并等待用户显式确认
- 项目或产品名称会被优先确认
- 每轮固定只问 3 个问题，可以问很多轮，但每轮都足够聚焦
- 选择题统一使用 `A/B/C/D` 形式，用户可以直接回复字母
- 所有 spec 默认统一写入 `.easy-coding/spec/`，不散落在项目根目录
- 文档采用“内部渐进草稿、最终集中展示”的方式
- 每轮提问前会先参考已完成文档，再决定下一轮最值得追问的 3 个问题
- 未定信息会被标记为 `[待确认]` 或 `当前假设`，而不是偷偷脑补
- 只要识别到有 UI，就会同时深挖信息架构、交互行为和视觉方向
- 当用户缺少 UI 想法时，AI 会基于产品类型给出 2-3 套方向建议和取舍，而不是静态猜测

## 适用场景

- 从 0 到 1 设计一个新产品、应用、工具或内部系统
- 对已有产品新增功能并更新产品规格
- 将聊天式需求讨论整理成结构化 spec
- 为有界面的产品补充页面结构、交互说明和视觉方向

## 不适用场景

- 市场分析、商业论证、立项判断
- 输出 MRD
- 编写代码、接口设计、技术实现方案
- 直接做开发任务拆解

## 工作方式

### 1. 先判断哪些问题会影响 spec

产品部分至少会检查：
- 项目或产品名称
- 目标与成功标准
- 用户与场景
- 范围与非目标
- 流程与分支
- 对象、字段、状态
- 规则、权限、异常
- 数据与系统约束

如果识别到有 UI，还会额外检查：
- 信息架构与页面承载
- 页面交互与状态
- 视觉方向与界面风格

### 2. 边追问边更新内部草稿

每轮对话后，skill 都会在内部更新 `Product-Spec.md` / `UI-Spec.md` 草稿：
- 新确认的内容写入对应章节
- 未定项标记为 `[待确认]`
- 用户允许 AI 先代补的内容标记为 `当前假设`

这些草稿默认都维护在 `.easy-coding/spec/` 下。

正式产品设计阶段中，每轮固定只问 3 个问题。下一轮提问前，会先回看当前草稿，再决定最值得继续问的 3 个问题。

对用户只同步当前理解、已锁定项、待确认项和下一轮问题主题，不会每轮都抛出整份半成品文档。

### 3. 有 UI 时，默认深挖三层问题

第一层：信息架构
- 页面范围
- 默认入口
- 导航结构
- 页面目标
- 页面之间的任务承载关系

第二层：交互行为
- 主操作、次操作、关键字段
- 零状态、空状态、加载态、错误态、权限态
- 列表、详情、编辑、批量操作联动
- 弹窗、抽屉、二级页触发条件

第三层：视觉方向
- 主题色组合
- 风格偏好
- 布局倾向
- 信息密度
- 组件气质
- 参考产品
- 品牌约束与视觉禁忌

### 4. 用户说不清时，AI 会给带取舍的 UI 建议

例如：
- 更偏效率工具：适合高频操作，但界面更硬核
- 更偏品牌体验：视觉记忆点更强，但信息承载较弱
- 更偏数据工作台：适合监控分析，但复杂度更高

AI 会给推荐结论，并把未拍板内容标记为 `当前假设`，而不是直接写成既定方案。

所有需要用户选择方向的地方，都会使用 `A/B/C/D` 选项格式，方便用户直接回字母。

## 当前模板

项目当前包含以下参考模板：

- [SKILL.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/SKILL.md)
- [references/product-spec-template.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/references/product-spec-template.md)
- [references/ui-spec-template.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/references/ui-spec-template.md)
- [references/changelog-template.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/references/changelog-template.md)
- [references/system-prompt-template.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/references/system-prompt-template.md)
- [references/ui-prompt-template.md](/Users/ysxiiun/Documents/agent-skill/easy-product-builder/references/ui-prompt-template.md)

## 使用示例

- “帮我把这个一句话需求梳理成 Product Spec”
- “我有个模糊的后台工具想法，帮我把流程、规则和 UI 一起问清楚”
- “帮我更新现有规格，同时把 UI 的视觉方向也补到 UI Spec”
- “先别写代码，先给我一份探讨计划，再一轮轮把产品、页面和风格方案问清楚”
