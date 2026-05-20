# agents/ — 跨 agent 平台界面元数据

本目录存放本 Skill 在不同 agent 平台上的**界面元数据**（display name、简介、默认 prompt 等）。

## 重要规则

**触发逻辑只由 SKILL.md 的 `description` 字段控制。** 本目录下任何文件都不影响 Claude / Cowork 环境的触发判断，仅用于在对应平台 UI 上展示。

也就是说：
- Claude / Cowork 用户安装本 Skill 后，触发由 `../SKILL.md` 的 frontmatter description 决定。
- OpenAI / Codex 用户安装本 Skill 后，UI 显示由 `openai.yaml` 决定，但触发判断仍由该平台自己的机制处理（通常也是读 SKILL.md description）。

## 当前文件

| 文件 | 用途 | 在哪里生效 |
|---|---|---|
| `openai.yaml` | OpenAI / Codex agent 环境的界面元数据 | OpenAI 系产品 |

## 如何新增平台支持

1. 在本目录下新建一个对应平台的元数据文件（如 `cursor.yaml`、`windsurf.yaml`）。
2. **不要改 `../SKILL.md`** 的触发逻辑——它是平台无关的。
3. 在本 README 的「当前文件」表里加一行说明。

## 三个字段保持一致的原则

各平台元数据文件的 `display_name`、`short_description`、`default_prompt` 三个字段，措辞可以根据平台习惯调整，但**含义必须与 SKILL.md description 一致**。如果你修改了 SKILL.md description，记得回头同步本目录下所有文件。
