# job-resume-tailor · 求职简历定制助手

An Agent Skills-compatible resume tailoring skill that uses target job descriptions to produce PDF resumes, recruiter greetings, industry terminology, learning roadmaps, work frameworks, and practical skill applications.

Licensed under the [MIT License](LICENSE).

优先根据用户提供的目标岗位 JD 定制 PDF 简历，默认同时交付 PDF 岗位配套指南和可复制打招呼语。指南包括行业黑话清单、技能清单、学习步骤与资源、工作思维框架、技能应用和岗位要求核对。

采用 [Agent Skills 标准](https://agentskills.io/specification)，使用必需的 `name`、`description` 元数据，不依赖特定厂商的工具名或配置扩展。

## 下载与安装

含 MIT 许可的 v3 安装包：[job-resume-tailor-skill-v3-mit.zip](dist/job-resume-tailor-skill-v3-mit.zip)。在 GitHub 的文件页面点击下载按钮获取实际 ZIP，解压后得到可安装的 `job-resume-tailor` 文件夹。

ZIP 的 SHA-256 校验值见 [dist/SHA256SUMS](dist/SHA256SUMS)。该安装包保留用户确认的 v3 技能指令与配套资源，新增 LICENSE 和 README 许可说明。原始确认版也保存在 dist/ 中。

也可以使用 GitHub 的 Code → Download ZIP 下载整个仓库。仓库解压后的文件夹通常带分支名后缀，安装前将其重命名为 `job-resume-tailor`。技能入口 `SKILL.md` 在仓库根目录，`examples/` 和 `references/` 与入口一起安装。

本仓库的发布附加文件为 `.gitignore`、`.gitattributes` 和 `dist/`；无需将这些文件作为 Agent 指令加载。它们不改变技能工作流程。

## 文件结构

```text
job-resume-tailor/
├── SKILL.md
├── README.md
├── USAGE.md
├── examples/
│   ├── 打招呼语开头重点句示例.md
│   └── 岗位技能清单-学习资源示例.md
└── references/
    ├── html-to-pdf.md
    └── resume-template.html
```

安装时保留整个文件夹及其名称 `job-resume-tailor`，不要只复制 `SKILL.md`。本仓库根目录就是技能目录；通过 GitHub 的 Download ZIP 获取时，解压后的文件夹可能带分支名后缀，安装前请将其重命名为 `job-resume-tailor`。

## 在不同 Agent 中使用

### Codex

将完整文件夹放到 `$CODEX_HOME/skills/job-resume-tailor/`；未设置 `CODEX_HOME` 时，使用 `~/.codex/skills/job-resume-tailor/`。确认入口路径为 `skills/job-resume-tailor/SKILL.md`，在新会话中调用：

```text
使用 $job-resume-tailor，根据我提供的岗位 JD 和个人信息定制简历。
```

### Claude Code

将完整文件夹放到 `~/.claude/skills/job-resume-tailor/`（个人技能），或者项目中的 `.claude/skills/job-resume-tailor/`（项目技能）。调用：

```text
/job-resume-tailor 根据我提供的岗位 JD 和个人信息定制简历。
```

安装路径和调用方式参见 [Claude Code 官方技能文档](https://code.claude.com/docs/en/skills)。

### 其他支持 Agent Skills 的 Agent

将完整文件夹放入该 Agent 文档规定的技能目录，或使用其技能导入功能。具体目录、自动发现机制与调用语法由该 Agent 决定，本包不要求 Codex 或 Claude 专用字段。

### 不支持技能导入的 AI 助手

手动提供 `SKILL.md` 作为指令，再提供个人信息和目标岗位 JD。需要排版、转换或示例时，一并提供相应的 `references/`、`examples/` 文件。该方式复用指令，不保证自动发现或读取本地文件。

## 能力要求

- 指令读取不需要执行脚本或安装第三方库。
- 岗位检索与学习链接查证需要当前 Agent 具备联网能力；无法联网时，应说明限制，使用用户提供的材料，不声称已完成联网查证。
- 简历统一交付 PDF，需要当前环境具备 PDF 生成工具、中文字体和预览或渲染能力。生成前检查环境，生成后检查全部页面；无法生成时说明具体限制并保留内容草稿，不以其他格式替代已完成的 PDF 交付。
- 姓名必须在生成简历前由用户填写；教育时间按用户提供的日期与精度填写，不按学制推算。
- 打招呼语使用配套示例的组织格式，内容从用户当前简历和已确认信息提取，不继承示例中的事实。
- 完整简历定制默认交付全部配套内容，并在结束前逐项核对。用户明确缩小范围时按其指定范围执行；工具能力不足时明确列出未完成项，继续提供其余内容。
- 个人信息填写说明见 [USAGE.md](USAGE.md)；完整工作流程见 [SKILL.md](SKILL.md)。

## 已完成的修正

补齐标准 YAML 元数据，重新制作真正的 ZIP，并检查中文文件名、配套相对路径和解压后的内容一致性。同步统一目标 JD 来源、姓名与教育时间填写规则、PDF 交付与版式检查要求，以及依据用户简历生成打招呼语的格式。补齐默认配套交付清单、可执行的学习与应用内容要求，以及结束前的完整性核对。兼容性验证针对文件格式和资源路径，该 v3 版本由使用者在其他 Agent 中检查后确认；本仓库整理仅验证文件格式和资源完整性。

## License

本项目采用 [MIT License](LICENSE)。允许使用、修改、分发和商业使用；分发时须保留版权声明和许可声明。
