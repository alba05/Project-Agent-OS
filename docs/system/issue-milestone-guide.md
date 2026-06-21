# Issue And Milestone Guide

## 目的

本文档定义 `Project-Agent-OS` 在 GitHub 上如何组织 `issues`、`labels` 和 `milestones`，避免后续任务堆积成无结构待办。

## 基本原则

1. `Roadmap` 负责方向
2. `Issues` 负责具体任务
3. `Milestones` 负责阶段节奏
4. 一个 issue 只表达一个清楚的工作单位
5. issue 标题应能直接看懂，不依赖聊天上下文

## 推荐 Issue 分类

### 1. Core Method

用于影响核心方法论定义的工作，例如：

1. 术语定义补充
2. 系统结构调整
3. 核心原则澄清
4. 仓库定位修正

推荐标签：

- `area:core-method`

### 2. Docs

用于文档优化与补充，例如：

1. README 改写
2. 文档导航优化
3. 中英结合表达修订
4. 缺失文档补齐

推荐标签：

- `area:docs`

### 3. Memory

用于 memory 结构、写回规则、元仓库自用 memory 的工作。

推荐标签：

- `area:memory`

### 4. SOP

用于 SOP 增补、调整和规范化。

推荐标签：

- `area:sop`

### 5. Handoff

用于 thread handoff 模板、规则和跨线程续接机制。

推荐标签：

- `area:handoff`

### 6. Templates

用于模板文件优化、模板扩展、模板可复用性增强。

推荐标签：

- `area:templates`

### 7. Examples

用于示例项目、示例结构、示例 README、示例边界管理。

推荐标签：

- `area:examples`

### 8. GitHub Ops

用于 GitHub 层运营结构，例如：

1. roadmap
2. labels
3. issue 模板
4. milestones
5. release 节奏

推荐标签：

- `area:github-ops`

## 推荐状态标签

建议未来在 GitHub 建立以下状态标签：

- `status:ready`
- `status:in-progress`
- `status:blocked`
- `status:review-needed`

## 推荐优先级标签

- `priority:p0`
- `priority:p1`
- `priority:p2`

解释建议：

1. `p0` 影响仓库基本可读性或核心定位
2. `p1` 影响结构稳定性或协作效率
3. `p2` 有价值但不阻塞当前阶段

## 推荐 Milestone

### `v0.2 Structure Stabilization`

用于承接当前最关键的一批任务：

1. roadmap 固化
2. issue taxonomy 固化
3. 元仓库 memory 初始化
4. README 双语化首轮推进

### `v0.3 Example Expansion`

用于示例层规范化和扩展。

### `v1.0 Reusable Operating Methodology`

用于最终形成稳定仓库框架。

## 首批建议 Issue

建议尽快建立以下首批 issues：

1. 建立元仓库 `knowledge-base/` 与 `thread-summaries/`
2. 将 README 进一步整理为更完整的中英结合首页
3. 设计 issue labels 与 milestone 结构
4. 规范 `examples/` 的准入标准
5. 设计“如何新增一个新示例项目”的说明

## 写法规范

一个好 issue 至少应包含：

1. 背景
2. 目标
3. 完成标准
4. 不在本次范围内的内容

## 判断规则

如果一个工作会长期复用，就进 issue；如果只是一次性灵感或临时想法，先留在 thread summary 或 open loops，不要直接污染 GitHub 任务面。
