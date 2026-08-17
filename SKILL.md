---
name: resume-builder
description: This skill should be used when a user wants to create, write, optimize, review, or translate a resume/CV (简历/履历), especially for software/tech roles. It provides the resume section structure, the FAB persuasion model, quantified achievement writing, ATS optimization rules, categorized action verbs, and fillable Markdown/YAML templates. Triggers include "帮我写简历", "优化我的简历", "生成一份程序员简历", "简历模板", "简历怎么写", "润色简历", "简历排版", "resume template", "ATS 过不了".
---

# Resume Builder

## Overview
本技能把多个高星开源简历项目的优秀实践浓缩成一套可复用工作流，用于快速产出**专业、可过 ATS、内容有说服力**的简历：
- **OpenResume**（xitanggg/open-resume）：ATS 友好规范（单栏、无照片、不写 references、核心章节）。
- **geekcompany/ResumeSample**：中文程序员简历模板，提出 **FAB 写作法**（Feature/Advantage/Benefit）与「量化 + 点到为止」原则，并附从 JD 统计出的技能关键词。
- **RenderCV**（rendercv/rendercv）：把简历当作数据（YAML）管理的结构化思路，便于版本控制与按岗微调。
- 多所高校职业中心的**力量动词表**：用强动词替代「负责 / 参与」。

## When to use
- 用户要求写新简历、改简历、优化 / 润色简历、做简历模板。
- 用户是程序员 / 工程师 / 学生，需要技术类简历。
- 用户提到 ATS、简历被刷、关键词不匹配、排版混乱等。

## Workflow

### 1. 澄清背景（先问，再写）
开始前确认（可一次性用 AskUserQuestion 或自然语言提问）：
- 目标岗位与方向（如「Java 后端」「前端」「算法」「架构师」「应届生」）。
- 工作年限 / 求职阶段（应届、1–3 年、资深、管理）。
- 投递地区与习惯（中文简历默认单栏、无照片；欧美岗遵循 OpenResume 规范）。
- 已有素材：是否基于用户提供的旧简历 / 经历改写（若是，先读取原文）。

### 2. 选择格式
- **Markdown 模板**（`assets/resume-template.md`）：最通用、易编辑、易转 PDF，适合绝大多数中文技术简历。**默认首选**。
- **结构化 YAML**（`assets/cv-template.yaml`）：适合工程师做版本管理、按岗位微调、追求精美排版（源自 RenderCV 思路）。当用户说「像写代码一样管简历」「要 LaTeX 级排版」时选用。

### 3. 采集内容
依据 `references/structure.md` 的章节清单逐项收集信息。重点在**工作经历**与**项目经历**——这是简历核心，也最需要量化与 FAB。

### 4. 写作铁律（务必遵守）
加载并遵循 `references/writing-guide.md`：
- **FAB 模型**：每个项目 / 经历讲清 Feature（做了什么）、Advantage（比别人好在哪）、Benefit（给雇主带来什么价值）。
- **量化**：用数字说话（性能从 X QPS 提升到 Y、服务器从 10 台减到 3 台、用户增长 Z%）。没有显赫成绩就写「成长」——解决了什么问题、方案好在哪、效果如何。
- **强动词开头**：每条 bullet 以动作动词起头（见 `references/writing-guide.md` 分类动词表），避免「负责 / 参与」这类弱表达。
- **点到为止**：提供论据，把结论留给阅读者自己得出，不过度自夸。

### 5. ATS 优化检查
写完后对照 `references/ats-checklist.md` 逐项检查：单栏布局、无照片 / 无年龄歧视信息（视地区）、关键词与 JD 对齐、无表格 / 图形 / 特殊符号、可被纯文本提取。

### 6. 关键词对齐（技术岗重点）
参考 `references/skill-keywords.md`：从目标 JD 抽取 5–10 个高频技能关键词，融入技能清单与经历描述，提升机器分选通过率。

### 7. 产出
- 生成最终 Markdown 简历文件，写入用户工作区（便于导出 PDF）。
- 可选：附一段「优化说明」，指出改了什么、为什么、还建议补充什么。

## Resources
- `references/structure.md` — 简历标准章节结构与每节写法
- `references/writing-guide.md` — FAB、量化、分类强动词、前后对照范例
- `references/ats-checklist.md` — ATS 通过率检查清单
- `references/skill-keywords.md` — 从 JD 抽取关键词的方法 + 示例词表
- `assets/resume-template.md` — 可直接填写的通用中文简历 Markdown 模板
- `assets/cv-template.yaml` — 工程师结构化 YAML 简历模板（RenderCV 风格）
- `assets/resume-template-party-hr.md` — 党务人事 / HR 岗位专属模板（按岗细分范例，命名约定 `resume-template-<岗位>.md`）
