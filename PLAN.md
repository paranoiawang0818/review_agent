# 个人复盘 Agent 系统 — 实施计划

## Context

用户需要一个本地 Markdown + Claude Code subagents 的复盘工作区，不依赖任何外部 API 或数据库。核心目标是：支持日/周/月/事件四类复盘，每次都必须产出可执行行动，且服务于「AI/MLLM 科研 + 高GPA → 美国 Top20 CS/AI 硕」这一长期主线。

---

## 目录结构

```
.claude/agents/
  main-review-coordinator.md
  daily-review-agent.md
  weekly-review-agent.md
  monthly-review-agent.md
  event-review-agent.md

templates/
  daily-input.md
  weekly-input.md
  monthly-input.md
  event-input.md

outputs/
  daily/    ← 日复盘输出
  weekly/   ← 周复盘输出
  monthly/  ← 月复盘输出
  event/    ← 事件复盘输出

docs/
  long-term-direction.md  ← 长期主线方向
  review-rules.md        ← 复盘通用规则
  review-dimensions.md    ← 各类型复盘的关注维度

README.md
```

---

## 各文件核心内容

### 1. `.claude/agents/main-review-coordinator.md`
入口 agent。职责：
- 根据用户输入判断复盘类型（日/周/月/事件）
- 调用对应 subagent
- 终审输出：检查是否有具体行动项、是否服务长期主线
- 主动识别：维护任务伪装、逃避高价值任务

### 2. `.claude/agents/daily-review-agent.md`
日复盘 agent。必须：
- 使用 KISS 框架（Keep / Improve / Start / Stop）
- 基于每日输入模板收集信息
- 输出明日行动卡（具体、3条以内）

### 3. `.claude/agents/weekly-review-agent.md`
周复盘 agent。必须：
- 计算本周计划完成度（完成数/计划数 %）
- 识别关键问题（1-2个）
- 输出下周任务清单 + 四象限分类：
  - 主线任务（直接服务长期目标）
  - 维护任务（必要但不直接服务）
  - 探索任务（验证假设）
  - 暂缓任务（可推迟）

### 4. `.claude/agents/monthly-review-agent.md`
月复盘 agent。必须：
- 对照长期主线评估本月行动
- 计算主线匹配度
- 识别有效投入 vs 低价值消耗
- 输出下月战略重点（最多3条）

### 5. `.claude/agents/event-review-agent.md`
事件复盘 agent。必须：
- 对比原目标 vs 实际结果（量化）
- 拆解原因（可控因素 vs 不可控因素）
- 提取可复用经验（最多3条）
- 输出下一步行动表

### 6. `docs/long-term-direction.md`
长期主线锚定文档。包含：
- 核心目标（科研 + 高GPA + 美国Top20硕）
- 关键里程碑（按学期分解）
- 当前阶段重点

### 7. `docs/review-rules.md`
通用复盘规则。包含所有 agent 共同遵守的约束：
- 不空泛鼓励、不鸡汤
- 每次必须有可执行行动
- 信息不足先问问题
- 主动删减任务
- 识别维护任务伪装
- 识别逃避高价值任务

### 8. `docs/review-dimensions.md`
各类型复盘的关注维度清单。

### 9. `templates/daily-input.md` / `weekly-input.md` / `monthly-input.md` / `event-input.md`
四个输入模板，引导用户结构化地提供复盘所需信息。

### 10. `README.md`
项目说明文档，包含使用流程：
1. 填写对应输入模板
2. 调用 main-review-coordinator
3. 复盘结果存入 outputs/

---

## 执行顺序

1. 创建目录结构（`.claude/agents/`, `templates/`, `outputs/`, `outputs/daily/`, `outputs/weekly/`, `outputs/monthly/`, `outputs/event/`, `docs/`）
2. 创建 5 个 agent 文件
3. 创建 4 个输入模板
4. 创建 3 个 docs 文件
5. 创建 README.md

---

## 验证方式

创建完成后，用户可通过 `/agent` 调用任一 agent，例如：
```
/agent
帮我做日复盘：[粘贴 templates/daily-input.md 内容]
```
