---
name: resume-builder
description: This skill should be used when a user wants to create, write, optimize, review, or translate a resume/CV (简历/履历), and also when they need adjacent career help: ATS scoring, cover-letter (求职信) generation, interview preparation, or matched job recommendations. It provides the resume section structure, the FAB persuasion model, quantified achievement writing, ATS optimization rules, categorized action verbs, fillable Markdown/YAML templates, a 0–100 ATS scorer, a cover-letter builder, an interview question bank, and a job-matching workflow (web-search based). Triggers include "帮我写简历", "优化我的简历", "生成一份程序员简历", "简历模板", "简历怎么写", "润色简历", "简历排版", "ATS 打分/过不了", "帮我写求职信", "面试准备", "推荐岗位", "有什么岗位适合我", "resume template".
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
- 用户要**ATS 打分 / 体检**：评估简历机筛通过率并给出扣分点。
- 用户要**求职信 / Cover Letter**：基于简历 + 目标 JD 自动生成。
- 用户要**面试准备**：根据简历推导可能被问的问题与 STAR 回答。
- 用户要**岗位推荐 / 匹配**：基于简历画像检索匹配岗位并生成推荐清单。

## Workflow

### 1. 澄清背景（先问，再写）
开始前确认（可一次性用 AskUserQuestion 或自然语言提问）：
- 目标岗位与方向（如「Java 后端」「前端」「算法」「架构师」「应届生」）。
- 工作年限 / 求职阶段（应届、1–3 年、资深、管理）。
- 投递地区与习惯（中文简历默认单栏、无照片；欧美岗遵循 OpenResume 规范）。
- 已有素材：是否基于用户提供的旧简历 / 经历改写（若是，先读取原文）。

### 2. 选择格式与模板
- **Markdown 模板**（`assets/resume-template.md`）：最通用、易编辑、易转 PDF，适合绝大多数中文技术简历。**默认首选**。
- **结构化 YAML**（`assets/cv-template.yaml`）：适合工程师做版本管理、按岗位微调、追求精美排版（源自 RenderCV 思路）。当用户说「像写代码一样管简历」「要 LaTeX 级排版」时选用。
- **按岗细分模板**（`assets/resume-template-<岗位>.md`）：党务人事 / HR、考公·事业单位·选调、国企·事业单位党建人事岗等已内置，直接套用更符合目标岗位语境。

### 3. 采集内容
依据 `references/structure.md` 的章节清单逐项收集信息。重点在**工作经历**与**项目经历**——这是简历核心，也最需要量化与 FAB。

### 4. 写作铁律（务必遵守）
加载并遵循 `references/writing-guide.md`：
- **FAB 模型**：每个项目 / 经历讲清 Feature（做了什么）、Advantage（比别人好在哪）、Benefit（给雇主带来什么价值）。
- **量化**：用数字说话（性能从 X QPS 提升到 Y、服务器从 10 台减到 3 台、用户增长 Z%）。没有显赫成绩就写「成长」——解决了什么问题、方案好在哪、效果如何。
- **强动词开头**：每条 bullet 以动作动词起头（见 `references/writing-guide.md` 分类动词表），避免「负责 / 参与」这类弱表达。
- **点到为止**：提供论据，把结论留给阅读者自己得出，不过度自夸。

### 5. ATS 优化检查 + 打分
- 写完后对照 `references/ats-checklist.md` 逐项检查：单栏布局、无照片 / 无年龄歧视信息（视地区）、关键词与 JD 对齐、无表格 / 图形 / 特殊符号、可被纯文本提取。
- 用 `references/ats-scoring.md` 的 0–100 评分表给出**机筛通过率分数**与逐条扣分项（弱动词、缺量化、关键词缺失等），让用户直观看到短板。

### 6. 关键词对齐（技术岗 / 投递岗重点）
参考 `references/skill-keywords.md`：从目标 JD 抽取 5–10 个高频技能关键词，融入技能清单与经历描述，提升机器分选通过率。

### 7. 产出简历
- 生成最终 Markdown 简历文件，写入用户工作区（便于导出 PDF）。
- 可选：附一段「优化说明」，指出改了什么、为什么、还建议补充什么。

### 8. 求职信（Cover Letter）生成
当用户要投具体岗位（给了 JD 或目标单位）时，加载 `references/cover-letter.md`：
- 从简历抽取 2–3 个与目标最匹配的亮点，按「开头（岗位+来源）→ 中段（FAB 论证为什么是你）→ 结尾（行动呼吁）」结构生成。
- 党务 / HR 等方向可直接套用模板中的范例。
- 产出可独立成文，便于随简历一并投递。

### 9. 面试准备
加载 `references/interview-prep.md`：
- 用 **STAR 框架**（Situation/Task/Action/Result）把简历里每条经历转成可被追问的回答底稿。
- 按主题推导高频题：自我认知、岗位认知（为何选党务 / HR）、经历深挖、情景题（组织冲突 / 合规两难）、时政政策（党务岗常考）。
- 输出「可能被问的 10 题 + 每题回答要点」。

### 10. 岗位匹配与推荐（Job Matching）
当用户问「有什么岗位适合我 / 帮我推荐岗位」时，加载 `references/job-matching.md` 工作流：
- **抽取简历画像**：目标岗、技能标签、城市、学历、政治面貌、经验年限。
- **构造检索式**：组合「岗位关键词 + 地区 + 2026 校招/社招/应届 + 国企/事业单位/民企」，用**联网搜索**检索主流招聘平台公开岗位。
- **筛选排序**：仅保留真实在招、与画像匹配度 ≥ 阈值者，按匹配度排序。
- **输出推荐清单**：每条含「岗位 + 单位类型 + 地区 + 匹配度 + 为什么匹配 + 简历微调建议 + 投递渠道」。
- **边界声明**：结果属「研究级」——非实时库存、可能漏招、绝不代投；建议以官方招聘渠道最终为准。

## Resources
- `references/structure.md` — 简历标准章节结构与每节写法
- `references/writing-guide.md` — FAB、量化、分类强动词、前后对照范例
- `references/ats-checklist.md` — ATS 通过率检查清单
- `references/ats-scoring.md` — 0–100 ATS 打分表（权重 + 计分 + 示例）
- `references/skill-keywords.md` — 从 JD 抽取关键词的方法 + 示例词表
- `references/cover-letter.md` — 求职信结构 + 通用 / 党务HR 范例
- `references/interview-prep.md` — 面试 STAR 框架 + 分类题库
- `references/job-matching.md` — 岗位匹配与推荐工作流规范（含检索式与产出格式）
- `assets/resume-template.md` — 可直接填写的通用中文简历 Markdown 模板
- `assets/cv-template.yaml` — 工程师结构化 YAML 简历模板（RenderCV 风格）
- `assets/resume-template-party-hr.md` — 党务人事 / HR 岗位专属模板
- `assets/resume-template-civil-servant.md` — 考公 / 事业单位 / 选调 岗位模板
- `assets/resume-template-state-org.md` — 国企 / 事业单位 党建人事岗模板
