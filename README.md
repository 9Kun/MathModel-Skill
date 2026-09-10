# 2026 数学建模比赛项目

本仓库已经初始化为可直接使用 **MathModel-Skill Standard 2.3.0 + Codex** 的数学建模比赛工作区。

## 目录

```text
.
├─ .agents/skills/          # 已安装的 MathModel-Skill（不要写比赛代码到这里）
├─ problem_files/           # 放赛题与官方附件
├─ paper_output/            # 建模代码、结果、图表、论文和 QA 输出
├─ docs/                    # MathModel-Skill 配套规范与说明
├─ AGENTS.md                # Codex 项目级执行规则
├─ requirements.txt         # Python 依赖
├─ MATHMODEL_BUILD.json     # 当前 Skill 安装信息
└─ VERSION                  # MathModel-Skill 版本
```

## 1. 上传赛题

把本次比赛的题面和所有官方附件放入 `problem_files/`。例如：

```text
problem_files/
├─ A题.pdf
├─ 附件1.xlsx
└─ 附件2.csv
```

如果最终选择 B/C/D/E 题，也只需把对应题目与附件放在这里。不要把自己的中间结果伪装成官方附件放入该目录。

## 2. 安装依赖

```bash
python -m pip install -r requirements.txt
python -m pip check
```

正式生成 Word/PDF 前建议安装 LibreOffice，用于最终渲染与版式检查。

## 3. 启动完整流程

在 Codex 中从仓库根目录启动：

```text
Use $paper-workflow-orchestrator to complete this mathematical-modeling project. Run preflight and workflow status first, keep all contest code and artifacts under paper_output/, and follow S0-S8. After S6 passes, use the Standard section-authoring path; only use micro repair when repair_queue.json requests it. Globally revise the assembled paper before producing formal Word and required PDF render QA.
```

总控会按状态推进：

`S0 输入检查 → S1 题目分析 → S2 模型与评分策略 → S3 数据与可视化 → S4 建模代码 → S5 实际运行 → S6 证据门禁 → S7 正式论文 → S8 Word/PDF 格式检查`

## 4. 手动检查状态

```bash
python .agents/skills/paper-workflow-orchestrator/scripts/preflight_check.py
python .agents/skills/paper-workflow-orchestrator/scripts/workflow_guard.py --status
```

正式工作成果均应进入 `paper_output/`。不要修改 `.agents/skills/` 中的 Skill 文件来塞入某一道题的专用代码。
