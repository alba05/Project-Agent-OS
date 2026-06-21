# Decision Log

## 2026-06-22

- Decision: 由主线程 A 负责 `Project-Agent-OS` 的 GitHub 创建、仓库定位与结构更新决策。
- Why: 避免多线程并行时出现 README、docs 分层和公开叙事漂移。
- Impact: 辅助线程只能承担受控的样本、草稿或子任务工作。

## 2026-06-22

- Decision: 为元仓库自身启用 `knowledge-base/` 与 `thread-summaries/`。
- Why: 方法论仓库应首先把自身作为实践对象，而不是只要求示例项目这样做。
- Impact: 后续线程应先读取本仓库自己的 memory，再继续推进 GitHub 和 docs 层工作。

## 2026-06-22

- Decision: 用 `repository-roadmap`、`issue-milestone-guide` 作为当前公开协作结构的基线文档。
- Why: 需要把 GitHub 层的长期方向、任务分类和阶段节奏从聊天中抽离出来。
- Impact: 后续 roadmap / issues / milestones 设计应优先对齐这两份文档。

## 2026-06-22

- Decision: `B / C / D / E / F / G` 等辅助线程的产出，默认先停留在样本层或示例层，不自动上升为主方法论。
- Why: 开源仓库当前阶段的重点是稳定框架和边界，而不是让并行线程的局部经验直接扩张主仓库叙事。
- Impact: 辅助线程产出需要先经主线程 A 审核，再决定是否进入 `README`、`docs/system/` 或其他核心方法文件。
