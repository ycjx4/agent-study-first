# 2sigma 工作区收敛与发布同步设计

> 日期：2026-07-17
> 状态：已确认，等待书面审阅
> 范围：归档外层旧副本，并明确唯一活跃仓库与运行目录的边界。

## 1. 背景

2sigma 目前同时存在于 Codex 安装目录、外层桌面工作区和嵌套 Git 仓库中。它们曾分别承担运行、试验和版本控制职责，但副本并存后，开发真源与运行副本不再一目了然。

本设计将 Git 仓库设为唯一开发真源；Codex 安装目录仅是运行副本；真实课程记录独立于两者。

## 2. 目标与非目标

### 目标

- 唯一活跃 Git 仓库固定为 `C:\Users\ycjx\Desktop\study_agent\agent-study-first`。
- 只在仓库内修改 `skill\2sigma`，再显式同步到 Codex 安装目录。
- 将外层的旧 `skill`、`examples`、`docs` 归档而不是直接删除。
- 通过外层入口说明，避免从归档副本或运行目录开发。

### 非目标

- 不移动或纳入 Git 真实课程目录 `C:\Users\ycjx\Desktop\study\思考快与慢`。
- 不改变 2sigma 的教学逻辑、课程记录格式或测试结论。
- 本次不新增同步脚本、目录链接或自动发布机制。
- 本次不移动仓库内部文档，也不改变测试证据的 Git 跟踪状态。

## 3. 目标结构

```text
C:\Users\ycjx\Desktop\study_agent\
├── agent-study-first\              # 唯一活跃 Git 仓库
│   ├── skill\2sigma\               # 唯一开发真源
│   ├── examples\                    # 可发布示例
│   └── docs\                        # 设计、计划与验证证据
│
└── archive\
    └── legacy-root-copy\           # 外层旧副本，只读归档
```

Codex 的运行副本固定在 `C:\Users\ycjx\.codex\skills\2sigma`，不作为开发真源，也不嵌入该 Git 仓库。

## 4. 日常边界

1. 所有 skill 源码修改只发生在 `agent-study-first\skill\2sigma`。
2. `C:\Users\ycjx\.codex\skills\2sigma` 是 Codex 的运行副本；修改仓库不会自动更新它。
3. 真实课程 `C:\Users\ycjx\Desktop\study\思考快与慢` 独立保存，不纳入仓库或归档。
4. 后续需要同步时，由用户明确要求后再采用简单、可审阅的复制流程；本次不实现自动化。

## 5. 归档

- 外层 `C:\Users\ycjx\Desktop\study_agent\skill`、`examples`、`docs` 迁至 `archive\legacy-root-copy`，保留其原始相对结构。
- 归档根增加说明文件：来源、归档日期、冻结状态、唯一活跃仓库路径，以及不得从归档副本发布 skill 的规则。
- 外层 README 只保留工作区地图：唯一活跃仓库、冻结归档、运行副本与真实课程位置。
- 不移动外层 `.git`、`.agents`、`.codex` 或嵌套活跃仓库。

## 7. 验收

- `agent-study-first` 是唯一活跃仓库，Git 状态不再被外层旧副本干扰。
- 归档目录包含旧副本与冻结说明，真实课程目录未受影响。
- 外层 README 明确指向唯一活跃仓库，归档 README 明确标为冻结。
- 外层根目录不再有活跃的 `skill`、`examples`、`docs` 副本。
- 归档后的三棵目录与移动前的文件清单和 SHA-256 一致。
- 真实课程目录保持存在且未改动。
