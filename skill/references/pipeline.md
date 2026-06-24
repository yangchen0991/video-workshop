# 视频工坊 — Phase 流程图与依赖关系

> 本文件提供完整的 Phase 流程、产物依赖关系、和 4 条链路映射。导演在 Phase 0 时参考。

---

## 一、全流程 Phase 图

```
用户输入创意
    │
Phase 0: 类型分析与导演决策           [导演自己执行]
    ├── 内容类型检测（A/B/C/D）
    ├── 锁定 6 项导演决策
    ├── 确定交互/自动模式
    └── 输出: 00_类型分析报告.md
    │
================== LAYER 1：GPT Image 2 关键帧资产库 ==================
    │
Phase 1: 剧本创作                      [spawn script-writer]
    └── 输出: 01_故事蓝图.md(可选) + 02_剧本.md
    │
Phase 2: 叙事节拍图谱 + 脚本拆解        [spawn script-writer]
    └── 输出: 03_叙事节拍图谱.md + 04_脚本拆解表.md
    │
Phase 3: 9 类资产 SCULPT 中文规划      [spawn art-designer]
    └── 输出: 05_资产清单.md
    │
Phase 4: GPT Image 2 关键帧生成        [spawn prompt-engineer L1]
    └── 输出: 06_关键帧分镜/
    │
⚠️ Phase 5: 连续性审查（关卡一）       [spawn script-supervisor]
    ├── PASS → 进入 Layer 2
    ├── FAIL → 返回 Phase 4 修复断裂帧
    └── 输出: 07_连续性审查报告.md
    │
================== LAYER 2：Seedance 2.0 视听一体分镜 ==================
    │
Phase 6: 声音 + 配音设计（并行）       [同时 spawn sound-designer + voice-director]
    └── 输出: 08_声音设计.md + 09_声线锁定.md
    │
Phase 7: Seedance 2.0 视听一体分镜    [spawn prompt-engineer L2]
    └── 输出: 10_Seedance分镜脚本/
    │
⚠️ Phase 8: QA 合规审查（关卡二）      [spawn qa-reviewer]
    ├── PASS → 进入打包
    ├── FAIL → 阻塞修复
    └── 输出: 12_QA审核报告.md
    │
Phase 9: 整合与打包                    [导演自己执行]
    └── 输出: 11_素材上传清单.md(可选) + 99_最终交付包.md
```

---

## 二、产物依赖关系表

下表中的"输入"列表示该成员需要读取的前序产物文件。

| Phase | 成员 | 输入（必须） | 输入（可选） | 输出 |
|-------|------|-------------|------------|------|
| 0 | 导演 | 用户创意 | — | 00_ |
| 1-2 | script-writer | 用户创意 + 导演决策 | — | 01_(可选), 02_, 03_, 04_ |
| 3 | art-designer | 02_, 03_, 04_ + 导演决策 | — | 05_ |
| 4 | prompt-engineer (L1) | 02_, 03_, 05_ + 导演决策 | — | 06_/ |
| 5 | script-supervisor | 03_, 06_/ | — | 07_ |
| 6A | sound-designer | 02_, 03_ | — | 08_ |
| 6B | voice-director | 02_ | — | 09_ |
| 7 | prompt-engineer (L2) | 02_, 03_, 05_, 06_/, 08_, 09_ + 导演决策 | — | 10_/ |
| 8 | qa-reviewer | 全部产物 (00_ ~ 10_/) | — | 12_ |
| 9 | 导演 | 全部产物 (00_ ~ 12_) | — | 11_(可选), 99_ |

---

## 三、4 条链路 Phase 执行表

| 链路 | 场景 | 执行 Phase | 外部 Skill 依赖 |
|------|------|-----------|----------------|
| **A 短剧** | 50-100集系列短剧 | 0→1→2→3→4→5→6→7→8→9 | seedance-prompts-skill, gptimage2-prompt-expert, seedance2-prompt-engine |
| **B 短片** | 3-30分钟叙事短片 | 0→1→2→3→4→5→6→7→8→9 | shortfilm-prompts-skill, gptimage2-prompt-expert, seedance2-prompt-engine |
| **C 单镜** | 单个场景/画面 | 0→1(精简)→4→9 | gptimage2-prompt-expert |
| **D PRD混合** | 结构化PRD多类型 | 0→拆分子任务→各子任务走A/B/C→汇总 | 按子任务类型 |

---

## 四、关键数据流

以下数据贯穿全链路，是所有成员的一致约束：

```
导演决策(6项) ─────────────────────────────────────────────────────┐
    ↓                                                              │
    ├──→ Phase 1-2 (script-writer)：约束剧本的叙事基调                │
    ├──→ Phase 3 (art-designer)：约束 SCULPT 风格锚定词                │
    ├──→ Phase 4 (prompt-engineer L1)：约束每帧的构图/光影/风格        │
    └──→ Phase 7 (prompt-engineer L2)：约束 Seedance 画幅/运镜/节奏   │
                                                                   │
叙事节拍图谱(03_) ──────────────────────────────────────────────┐   │
    ↓                                                           │   │
    ├──→ Phase 3 (art-designer)：9类资产的连续性继承数据源        │   │
    ├──→ Phase 4 (prompt-engineer L1)：每帧的6维锁定+变化注入    │   │
    ├──→ Phase 5 (script-supervisor)：连续性审查的权威参考       │   │
    ├──→ Phase 6A (sound-designer)：配乐情绪曲线数据源           │   │
    └──→ Phase 7 (prompt-engineer L2)：视频+音频连续性描述       │   │
                                                                   │
GPT Image 2 关键帧(06_/) ─────────────────────────────────────┐      │
    ↓                                                         │      │
    ├──→ Phase 5 (script-supervisor)：帧间检查的检查对象       │      │
    ├──→ Phase 7 (prompt-engineer L2)：@图片引用源             │      │
    ├──→ Phase 8 (qa-reviewer)：SCULPT 合规检查对象            │      │
    └──→ Phase 9 (导演/asset-integrator)：素材上传映射         │      │
```

---

## 五、关卡快速参考

| 关卡 | Phase | 执行者 | 检查项数 | Critical 处理 |
|------|-------|--------|---------|-------------|
| 关卡一 | Phase 5 | script-supervisor | 7 项连续性 | 返回 Phase 4 重新生成断裂帧 |
| 关卡二 | Phase 8 | qa-reviewer | 22 项合规+格式+质量 | 阻塞发布，修复后重新审查 |
