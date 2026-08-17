# resume-builder（简历制作技能 / Resume Builder Skill）

一个供 WorkBuddy / 类智能体使用的简历制作技能：按 **FAB 写作法**、**量化表达**、**强动词**、**ATS 规范**与 **JD 关键词对齐**，产出专业中文简历。

A reusable resume/CV-building skill for WorkBuddy-style agents. It turns multiple high-star open-source resume projects into one practical workflow that produces **professional, ATS-friendly, persuasive** resumes using the **FAB model**, **quantified achievements**, **strong action verbs**, **ATS rules**, and **JD keyword alignment**.

## 目录内容 / Contents

- `SKILL.md`：触发词 + 7 步工作流 / Triggers + 7-step workflow
- `references/`：章节结构、写作指南、ATS 检查清单、技能关键词 / Structure, writing guide, ATS checklist, skill keywords
- `assets/`：可填写模板 / Fillable templates
  - `resume-template.md` — 通用中文简历模板（默认首选）/ General Chinese resume template
  - `cv-template.yaml` — 工程师结构化 YAML 模板（RenderCV 风格）/ Engineer YAML template
  - `resume-template-party-hr.md` — 党务人事 / HR 岗位专属模板 / Party-affairs & HR template

## 用法 / Usage

将本目录整体放入 WorkBuddy 的 `skills/` 目录（用户级或项目级），对话中说  
Copy this directory into WorkBuddy's `skills/` folder (user-level or project-level), then say in chat:

> “帮我写简历 / 优化简历 / 程序员简历模板 / 简历排版”

即可触发。 / to trigger it.

## 许可与署名 / License & Attribution

- 本技能以 **MIT 许可证**发布（见 `LICENSE`）。/ Licensed under **MIT** (see `LICENSE`).
- 内容提炼自多个开源 / 公开项目，详见 `ATTRIBUTIONS.md`。/ Content is synthesized from several open-source / public projects; see `ATTRIBUTIONS.md`.

## 衍生模板 / Derived Templates

`assets/` 下可按岗位继续细分模板，命名约定：`resume-template-<岗位英文>.md`。当前已含 `party-hr`（党务人事）。  
Add more job-specific templates under `assets/` using the naming `resume-template-<role>.md`. `party-hr` is included as a starting example.
