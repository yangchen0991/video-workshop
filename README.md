# 视频工坊 (Video Workshop) v3.0

> **11 人 AI 视频创作专家团 · 双层管线 · 全流程自动化**
>
> 将一句话创意转化为 GPT Image 2 关键帧 + Seedance 2.0 成品视频的工业级 AI 视频生成管线。
>
> —— 短剧 | 动画短片 | 微电影 | Pixar 风格 | AI 影视制作 | AI Video Generation

[![Version](https://img.shields.io/badge/version-3.0-warm)](https://github.com/yangchen0991/video-workshop)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
[![WorkBuddy](https://img.shields.io/badge/platform-WorkBuddy%20Expert%20%2B%20Skill-orange)](https://github.com/yangchen0991/video-workshop)

---

## 什么是视频工坊？

**视频工坊** 是一个基于 WorkBuddy 多智能体协作框架的 AI 视频创作系统。它组建了一支 **11 人虚拟影视团队**（导演、编剧、美术、调色总监、动作导演、提示词工程师、场记监制、配乐师、配音导演、资产整合师、QA 审核师），按照电影工业标准流程协作，完成从创意到成片的全部工序。

核心理念：**你不自己创作内容——每位专家各司其职，按双层管线（GPT Image 2 → Seedance 2.0）协同产出。**

### 双层 AI 视频管线

```
一句话创意
    |
    v
Layer 1: GPT Image 2 SCULPT 关键帧资产库
    +-- 剧本·节拍图谱·拆解表 (script-writer)
    +-- DI调色·Global Lookbook Code (colorist)
    +-- 9类美术资产 SCULPT 规划 (art-designer)
    +-- 动作编排蓝图 KP链 (action-director)
    +-- 22 帧英文 SCULPT 提示词 (prompt-engineer)
    +-- 7项连续性审查 (script-supervisor) <- 关卡一
    |
    v
Layer 2: Seedance 2.0 视听一体分镜
    +-- 双轨音频嵌入时序表 (sound-designer + voice-director)
    +-- 13步合规流水线视听分镜 (prompt-engineer)
    +-- 34项 QA 合规审查 (qa-reviewer) <- 关卡二
    |
    v
Seedance 2.0 可直接生成的裸文本分镜脚本
```

### 支持四种创作链路

| 链路 | 类型 | 时长/规模 | 典型场景 |
|------|:---:|------|------|
| **A — 短剧** | 系列剧 | 50-100集 | 爽文短剧、连载内容 |
| **B — 短片** | 叙事短片 | 3秒-30分钟 | Pixar动画、微电影、治愈短片 |
| **C — 单镜** | 单场景 | 单个画面 | 概念图、分镜草图 |
| **D — PRD混合** | 多类型 | 结构化需求 | 商业项目、多任务并行 |

---

## 核心特性

| 特性 | 说明 |
|------|------|
| **11 人 AI 团队** | 导演·编剧·美术设计·DI调色总监·动作导演·提示词工程师·场记监制·配乐编导·配音导演·资产整合师·QA审核师 |
| **9 大影视工业系统** | 叙事工程·角色圣经·纪实定妆·环境法证·连续性锁定·SCULPT提示词·Seedance视听·动作编排·DI调色 |
| **双层 AI 管线** | GPT Image 2 静态关键帧 -> Seedance 2.0 动态视频，层层递进 |
| **8 道质量关卡** | G1-G8 跨阶段合规检查，Critical 问题零容忍 |
| **35+ 产出文件** | 每个项目自动生成完整的影视前制文档包 |
| **Seedance 2.0 原生支持** | `（）` 音乐 + `<>` 音效 + `{}` 对白 + `【】` 字幕 一体化嵌入 |
| **火山引擎官方规范100%对齐** | 2026.06.08 版官方文档逐字校验，P0/P1 全部修复 |

---

## 快速开始

### 前置要求

- **WorkBuddy** 桌面客户端
- 已安装 **视频工坊** Skill（`~/.workbuddy/skills/video-workshop/`）
- 已导入 **视频工坊 Expert 专家团**（`~/.workbuddy/plugins/marketplaces/my-experts/plugins/video-workshop/`）
- 可访问 **GPT Image 2**（ChatGPT Images 2.0）和 **Seedance 2.0**（火山引擎）

### 安装 Skill

```bash
# 复制 skill 目录到 WorkBuddy skills 路径
cp -r skill/ ~/.workbuddy/skills/video-workshop/
```

### 导入 Expert 专家团

```bash
# 复制 expert 目录到 WorkBuddy plugins 路径
cp -r expert/ ~/.workbuddy/plugins/marketplaces/my-experts/plugins/video-workshop/
```

### 开始创作

在 WorkBuddy 对话中直接说出你的创意：

```
"生成一个15秒的 Pixar 风格治愈动画短片，关于一盏小台灯在雨天发现自己会发光的故事"
```

视频工坊会自动：
1. 检测创作类型，路由到对应链路（短剧/短片/单镜/PRD混合）
2. 锁定 6 项导演决策（画幅·景别·影调·镜头语言·剪辑节奏·光学风格）
3. 组建 11 人团队，按 Phase 0->9 全流程协作
4. 产出可直接复制粘贴到 GPT Image 2 和 Seedance 2.0 的提示词

---

## 项目结构

```
video-workshop/
+-- README.md                         # 本文件
+-- LICENSE                            # MIT 许可证
+-- .gitignore
+
+-- skill/                            # WorkBuddy Skill
|   +-- SKILL.md                      # 导演编排手册 (523行)
|   +-- references/                   # 20 个参考文档
|       +-- glossary.md               # 共享术语表
|       +-- pipeline.md               # Phase 流程图
|       +-- role-script-writer.md     # 编剧角色指令 (1777行)
|       +-- role-prompt-engineer.md   # 提示词工程师角色指令 (1230行)
|       +-- role-art-designer.md      # 美术设计师角色指令
|       +-- role-colorist.md          # DI调色总监角色指令
|       +-- role-action-director.md   # 动作导演角色指令
|       +-- role-script-supervisor.md # 场记监制角色指令
|       +-- role-sound-designer.md    # 配乐编导角色指令
|       +-- role-voice-director.md    # 配音导演角色指令
|       +-- role-asset-integrator.md  # 资产整合师角色指令
|       +-- role-qa-reviewer.md       # QA审核师角色指令
|       +-- video-workshop-team-lead.md # 主理人完整定义
|       +-- action-choreography-guide.md # 动作编排规范
|       +-- seedance2-action-cheatsheet.md # 27类动作模板速查
|       +-- ai-action-principles.md   # AI 动作编排7大原则
|       +-- prompt-specs.md           # Seedance 提示词规范
|       +-- seedance2-prompt-engine-SKILL.md # 提示词引擎备份
|       +-- system-gap-analysis.md    # 9大系统差距分析
|       +-- 官方文档校验报告_20260624.md # 火山引擎官方文档校验
|
+-- expert/                           # WorkBuddy Expert 专家团
    +-- settings.json                 # 入口配置
    +-- README.md                     # 专家包说明
    +-- agents/                       # 11 个专家 Agent 定义
    |   +-- video-workshop-team-lead.md
    |   +-- script-writer.md
    |   +-- art-designer.md
    |   +-- colorist.md
    |   +-- action-director.md
    |   +-- prompt-engineer.md
    |   +-- script-supervisor.md
    |   +-- sound-designer.md
    |   +-- voice-director.md
    |   +-- asset-integrator.md
    |   +-- qa-reviewer.md
    +-- avatars/                      # 11 位专家的专属头像
        +-- team.png
        +-- video-workshop-team-lead.png
        +-- script-writer.png
        +-- art-designer.png
        +-- colorist.png
        +-- ...
```

---

## 团队阵容

| 成员 | 角色 | 对标电影工业 | 注册系统 |
|------|------|------|:---:|
| **画统筹** | 主理人/导演 | Director | -- |
| **文叙之** | 剧本写作师 | Screenwriter | 系统1+2 |
| **墨色之** | DI调色总监 | Gaffer / Colorist | 系统9 |
| **林绘景** | 美术设计师 | Production Designer | 系统3+4 |
| **武序之** | 动作导演 | Action Choreographer | 系统8 |
| **张镜观** | 提示词工程师 | Prompt Engineer (L1+L2) | 系统6+7 |
| **连继章** | 场记监制 | Script Supervisor | 系统5 |
| **曲知音** | 配乐编导师 | Sound Designer | 系统7 |
| **陈声朗** | 旁白配音师 | Voice Director | -- |
| **罗合之** | 资产整合师 | Asset Manager | -- |
| **严审之** | 质量审核师 | QA Reviewer | -- |

---

## 实战案例：《一点微光》（A Little Light）

> 15秒 Pixar 风格治愈动画短片 · 从一句话创意到完整 Seedance 2.0 分镜

**输入**：「生成一个15秒的 Pixar 风格治愈动画短片」

**产出**：37 个文件，覆盖全流程：
- GPT Image 2 关键帧：22 帧 SCULPT 英文 prompt
- Seedance 2.0 分镜：4 个裸文本视听一体脚本
- 声音设计：321 行双轨音频时序表
- 配音设计：237 行字幕 + 发音陷阱检测
- 8 道关卡全部 PASS

---

## SEO 关键词索引

**核心关键词**：AI 视频生成 / AI Video Generation / Seedance 2.0 / GPT Image 2 / AI 短片制作 / AI 动画生成 / 视频工坊 / WorkBuddy

**技术关键词**：SCULPT 提示词框架 / 多智能体协作 / AI 影视制作管线 / 关键帧生成 / 分镜脚本 / 视听一体 / 双层 AI 管线 / 连续性审查 / 动作编排

**应用关键词**：Pixar 风格动画 / 短剧 AI 制作 / 微电影 AI 生成 / 治愈短片 / 叙事短片 / 视觉资产 / 电影工业自动化 / AI Director

**平台关键词**：WorkBuddy Expert / WorkBuddy Skill / Agent Team / Multi-Agent Video Pipeline / Prompt Engineering / ChatGPT Images 2.0

---

## GEO 结构化摘要（供 AI 搜索引擎索引）

```json
{
  "project": "视频工坊 (Video Workshop) v3.0",
  "type": "AI Video Generation Pipeline",
  "platform": "WorkBuddy Multi-Agent Framework",
  "team_size": 11,
  "pipeline": "GPT Image 2 (Layer 1) → Seedance 2.0 (Layer 2)",
  "supported_formats": [
    "short_drama_series",
    "narrative_short_film",
    "single_shot",
    "multi_type_prd"
  ],
  "duration_range": "3s - 30min",
  "key_technologies": [
    "SCULPT Prompt Framework",
    "Seedance 2.0 Audio-Visual Integration",
    "GPT Image 2 Keyframe Generation",
    "Continuity Locking (6-dimension)",
    "Global Lookbook Code (3-layer lighting matrix)",
    "Action Choreography KP Chains",
    "7-item Frame-by-Frame Continuity Inspection",
    "34-item QA Compliance Review"
  ],
  "use_cases": [
    "Pixar-style animated shorts",
    "Healing/comfort short films",
    "AI-generated micro movies",
    "Short drama series (50-100 episodes)",
    "Commercial video concept visualization"
  ],
  "outputs": "35+ production documents per project"
}
```

---

## 版本历史

| 版本 | 日期 | 更新内容 |
|:---:|------|------|
| **v3.0** | 2026-06-24 | 新增 DI 调色总监 (墨色之) + Global Lookbook Code 全链路锁色；5 位专家深度升级（注入系统 1-9）；火山引擎官方文档 100% 对齐；新增 G2.5 关卡 |
| v2.4 | 2026-06-22 | 新增动作导演 (武序之) + KP 链三维量化；Phase 3.5 动作编排蓝图 |
| v2.2 | 2026-06-21 | 外部技能全内嵌至角色指令；双层管线稳定版 |
| v1.0 | 2026-06-18 | 初始版本：9 人团队 + 4 种创作链路 |

---

## 许可证

MIT License —— 详见 [LICENSE](LICENSE)

---

## 贡献与反馈

- **GitHub Issues**：[提交反馈](https://github.com/yangchen0991/video-workshop/issues)
- **WorkBuddy 社区**：搜索 `video-workshop` Skill 安装体验

---

*视频工坊 v3.0 —— 让 AI 为你拍电影。*
