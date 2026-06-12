# Academic Reference Matcher Skill

通用智能体文献匹配 Skill：把论文段落、学术 claim 或已有引用列表，转成可核验的文献匹配结果。

> 中文为主，English version below.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Agent Skill](https://img.shields.io/badge/Agent%20Skill-SKILL.md-green.svg)](SKILL.md)

## 它解决什么问题

写论文、综述、基金、答辩材料或 rebuttal 时，最麻烦的常常不是“找几篇文献”，而是：

- 哪些句子真的需要引用？
- 搜到的论文到底支不支持这句话？
- 收费论文只能看到题名、关键词或摘要时，能不能先作为候选？
- 多个 claim 怎么逐句对应参考文献？
- 怎么避免 agent 编 DOI、编作者、编年份？

这个 skill 的目标不是下载论文，也不是绕过付费墙，而是提升 **文献检索、匹配、验证和输出** 的质量。

## 核心能力

- 识别需要引用支撑的学术论断。
- 为多 claim 文本建立 `S001`、`S002` 等稳定编号。
- 为每个 claim 设计独立检索式，避免一个宽泛关键词搜到底。
- 按学科、证据类型和来源可靠性选择检索源。
- 正确使用收费论文的题名、关键词、摘要、DOI 和出版社元数据做候选发现。
- 区分 `Discovery-only`、`Abstract-supported`、`Snippet-supported`、`Fulltext-supported`、`Bibliographic-only` 等证据等级。
- 输出 claim-to-reference 表、引用格式、检索记录和无法验证说明。
- 支持 APA、GB/T 7714、Vancouver、IEEE、BibTeX、RIS 等格式。

## 不做什么

- 不自带搜索引擎或付费数据库账号。
- 不下载或破解付费全文。
- 不绕过验证码、登录墙、Cloudflare 或机构权限。
- 不把 metadata-only 候选夸大成强支撑。
- 不承诺穷尽所有文献，除非用户提供了限定数据库、检索式或文献库。

## 适用场景

- 给 introduction、abstract、discussion 或 grant text 补引用。
- 检查已有引用是否真的支持原文。
- 替换弱引用、错引用、过时引用或撤稿文献。
- 给中文论文段落匹配 GB/T 7714 参考文献。
- 为综述或系统综述前期准备可复查的检索记录。
- 把 DOI、BibTeX、RIS、Zotero/Mendeley 导出或用户 PDF 作为本地候选库来匹配 claim。

## 检索深度

| 深度 | 适用情况 | 输出侧重 |
|---|---|---|
| `quick` | 少量 claim，快速找 3-5 篇强相关文献 | 简短推荐与置信度 |
| `standard` | 默认；段落或短小节补引用 | claim-reference 表 |
| `deep` | 长文本、综述背景、争议主题 | 分段 ID、source routing、search audit |
| `audit` | 系统综述准备或高风险稿件 | 可复查检索日志、限制说明、拒绝理由 |

## 任务模式

| 模式 | 用途 |
|---|---|
| `add` | 给未引用的 claim 找文献 |
| `verify` | 检查已有引用是否支撑对应 claim |
| `replace` | 为弱引用或错误引用找更合适替代 |
| `format` | 只格式化已知参考文献 |
| `extract` | 只识别需要引用的 claim，暂不检索 |

## 快速使用

把仓库复制到支持 skills 或 agent instructions 的运行环境，然后调用：

```text
使用 $academic-reference-matcher 为这段文字查找并验证学术参考文献。
```

英文示例：

```text
Use $academic-reference-matcher to find and verify scholarly references for this paragraph.
```

如果你的 agent 没有正式的 skill loader，可以直接把 `SKILL.md` 作为系统说明或上下文提供给它。

## 安装方法

### Claude Code

```bash
git clone https://github.com/keros68/academic-reference-matcher-skill.git \
  ~/.claude/skills/academic-reference-matcher
```

然后新开一个 Claude Code 窗口，直接说：

```text
使用 $academic-reference-matcher 为下面这段话找参考文献，并输出 claim-reference 表。
```

### Codex / 通用 agent 目录

```bash
git clone https://github.com/keros68/academic-reference-matcher-skill.git \
  ~/.agents/skills/academic-reference-matcher
```

如果你的运行环境支持项目级 skills，也可以放到项目目录：

```bash
git clone https://github.com/keros68/academic-reference-matcher-skill.git \
  ./.agents/skills/academic-reference-matcher
```

### 不支持 skill loader 的 agent

把 `SKILL.md` 和需要的 `references/*.md` 作为上下文上传或粘贴给 agent。最小用法是只提供 `SKILL.md`；如果要做更严格的检索质量测试，再补充：

- `references/query-planning.md`
- `references/source-routing.md`
- `references/verification-rubric.md`
- `references/search-audit.md`
- `references/paywall-aware-access.md`

## 新窗口测试建议

建议在一个新窗口或新线程里测试，这样更接近真实用户使用场景，避免当前开发上下文影响 agent。

测试 prompt：

```text
使用 $academic-reference-matcher，按 standard depth 跑完整流程：
1. 给下面段落拆分 Segment ID；
2. 规划 query families；
3. 查找并验证参考文献；
4. 输出 claim-reference 表；
5. 给出 suggested cited revision；
6. 附 compact search audit；
7. 不要编造 DOI、作者、年份；metadata-only 只能标 Discovery-only。

段落：
Conventional assessments usually identify exceedances using drinking-water limits or groundwater quality standards. This threshold-based approach is useful for rapid screening, but it does not explain why a given NO₃⁻ concentration occurs. The same concentration may represent a screened background state, external input disturbance, or a low-NO₃⁻ state modified by aquifer processes. In heterogeneous shallow groundwater systems, NO₃⁻ assessment therefore needs to move from exceedance judgement to status interpretation.
```

理想表现：

- 能把文本拆成 `S001`、`S002` 等 claim。
- 能区分 official standard、background value、source tracing、aquifer process 文献。
- 能说明哪些引用是 High / Medium / Low。
- 能指出 “status interpretation” 更像作者概念综合，而不是现成标准术语。
- 能给出查了哪些来源、哪些候选被拒绝、有什么访问限制。

## 输出示例

对于多 claim 任务，skill 会倾向于输出这种结构：

| Segment | Claim | Query families | Accepted reference | Evidence basis | Confidence | Notes |
|---|---|---|---|---|---|---|
| S001 | 原文 claim | 关键词组 / DOI / 来源路径 | Author et al., year, title, DOI | Abstract-supported | Medium | 全文未检查 |

如果找不到可靠支撑，会明确说明：

```text
Could not verify:
- Claim: ...
  Checked: source and query summary
  Best candidates rejected: title/year/why rejected
  Reason: no direct scholarly support found / access unavailable / candidates only weakly related
  Next step: ask user for bibliography/PDF/corpus or revise the claim
```

## 文件结构

- `SKILL.md` - 主 skill 说明和触发描述。
- `references/query-planning.md` - claim 拆分、检索式设计、query drift 检查。
- `references/source-routing.md` - 按学科和证据需求选择检索源。
- `references/paywall-aware-access.md` - 收费论文 metadata 的合法使用和证据等级。
- `references/search-audit.md` - 可复查检索记录模板。
- `references/search-sources.md` - 数据源选择和查询模式。
- `references/verification-rubric.md` - 支撑关系评分规则。
- `references/output-formats.md` - 输出格式和失败模板。
- `examples/example-requests.md` - 常见请求模板。
- `agents/openai.yaml` - 兼容运行时的 UI 元数据。

## 已知局限

- 检索质量取决于宿主 agent 能访问的搜索、浏览器、数据库、PDF 或本地文献库能力。
- 付费墙、摘要缺失、元数据不完整和访问频率限制会降低验证质量。
- 题名、关键词、引用量和索引元数据只能作为候选发现信号，不能证明强 claim。
- 复杂期刊格式、团体作者、预印本与正式发表版本对应关系、中英文混排参考文献，仍可能需要人工终审。

## English

Academic Reference Matcher is a portable agent skill for matching scholarly references to academic claims. It helps an agent identify citation-worthy claims, plan better searches, route sources by evidence need, verify whether a candidate paper actually supports the claim, and format the result for academic writing.

It is not a paper downloader and does not bypass paywalls. Paywalled metadata can be used for discovery and candidate ranking, but metadata-only visibility must not be overstated as strong support.

### Main Features

- Claim extraction and stable segment IDs.
- Claim-specific query planning.
- Field-aware source routing.
- Paywall-aware evidence tiers.
- Claim-to-reference mapping.
- Support grading and search audit logs.
- APA, GB/T 7714, Vancouver, IEEE, BibTeX, and RIS output.

### Quick Start

```text
Use $academic-reference-matcher to find and verify scholarly references for this paragraph.
```

For runtimes without a formal skill loader, provide `SKILL.md` as agent instructions.

### Installation

```bash
git clone https://github.com/keros68/academic-reference-matcher-skill.git \
  ~/.claude/skills/academic-reference-matcher
```

For generic agent runtimes, copy the repository into the runtime's skill directory or provide `SKILL.md` as instruction context.

## License

MIT
