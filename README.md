# Awesome DeepSeek Harness Plugins

> **中文导读**：这是 DeepSeek Harness（DSH）生态的插件精选列表，英文为主维护，中文说明见各章节标题下方。想直接上手的高星插件评测请看 [Hands-on Notes](#hands-on-notes)。

A curated list of plugins, tools, skins, bridges, and extensions for
[DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) (DSH) — the
open-source agent framework from DeepSeek, built on the motto
**"Everything is a Plugin."**

DSH launched its developer preview on **2026-08-13** (MIT license, Cordis-based).
Within a day the community shipped a wave of plugins; this list tracks the
notable ones and points to the rest.

> Star counts are a launch-day snapshot (2026-08-13) and drift fast. For the
> unmoderated, auto-refreshed index of every repo tagged `dsh-plugin`, see
> [PLUGINS.md](PLUGINS.md) (regenerated daily by
> [update.yml](.github/workflows/update.yml)).

> **生态入口 / Ecosystem**：想找插件不想翻列表？去 **[WhaleHub](https://whalehub-dsh.vercel.app)** —— 基于本列表每日同步的可视化插件市场（搜索 / 分类 / 一键复制安装命令，还能装进 DSH Web 里点一下直装）。想零配置上手 DSH？试 **[DeepSeek Harness Desktop](https://dsh-desktop.vercel.app)** —— 自包含 macOS APP（内置 Node + dsh + Paseo），拖进「应用程序」即用。

## Contents

- [How to install a plugin](#how-to-install-a-plugin)
- [Official built-in plugins](#official-built-in-plugins)
- [Community plugins](#community-plugins)
  - [Web UI & Skins](#web-ui--skins)
  - [Terminal & Desktop](#terminal--desktop)
  - [Vision & Multimodal](#vision--multimodal)
  - [Tools & Editor UX](#tools--editor-ux)
  - [Agent orchestration & Workflow](#agent-orchestration--workflow)
  - [Integrations & Bridges](#integrations--bridges)
  - [Sidebar, Workspace & Ecosystem](#sidebar-workspace--ecosystem)
  - [Fun & Misc](#fun--misc)
- [Hands-on Notes](#hands-on-notes)
- [Other awesome lists (meta)](#other-awesome-lists-meta)
- [Contributing](#contributing)
- [License](#license)

## How to install a plugin

**中文**：DSH 把插件当作 [Cordis](https://github.com/cordiverse/cordis) bundle 加载，最常用的两条路：npm 包用 `dsh plugin add <npm-package>`，仓库托管（`.dsh-plugin` 形态）用 `github:<owner>/<repo>` 形式。

DSH loads plugins as [Cordis](https://github.com/cordiverse/cordis) bundles.
Two common paths:

```sh
# npm-scoped plugin (recommended)
dsh plugin add <npm-package>

# repo-hosted plugin (the .dsh-plugin format)
# add to your profile's cordis.yml, or via the CLI patch layer:
# github:<owner>/<repo>#<ref>&path:/.dsh-plugin
```

Start the Web UI and manage models/workspaces there:

```sh
dsh web            # http://127.0.0.1:3080
```

## Official built-in plugins

**中文**：框架本体在 `@deepseek-ai/dsh-*` 这个 npm scope 下自带约 50 个内部插件包，是所有社区插件的参考实现与"接缝"底座（llm / shell / fs / web / subagent / plan / sandbox / hooks / skill …）。

The framework itself ships ~50 internal plugin packages under the
`@deepseek-ai/dsh-*` npm scope. They are the reference implementations and the
building blocks every community plugin extends. Highlights:

- **`deepseek-ai/deepseek-harness`** — the framework and all built-in packages.
  See [`packages/README`](https://github.com/deepseek-ai/deepseek-harness/blob/master/packages/README.md)
  for the full map: `llm` (model adapters), `shell`/`terminal`/`code-runtime`
  (execution), `fs`/`lsp` (files & language servers), `web` (search/fetch),
  `subagent` (delegation), `plan`, `sandbox`, `hooks`, `skill`, `compaction`,
  `extensions` (runtime self-modifying plugins), and the `web`/`cli` apps.

Everything below is community-built and sits on top of these seams.

## Community plugins

### Web UI & Skins

**中文**：给 DSH 网页界面换肤、加任务看板、宠物、移动端远程等"界面增强"类插件。

- [zhu1090093659/dsh-web-ui](https://github.com/zhu1090093659/dsh-web-ui) (★300) — Plugin & skin collection for the DSH Web UI: task board, git graph, right-side panel, remote mobile UI, pet, live token stats, skin center.
- [bpc-oss/dsh-web-billing](https://github.com/bpc-oss/dsh-web-billing) (★9) — RMB/USD token billing for the DSH web: official-policy auto pricing (incl. peak/off-peak hours), per-message cost ledger, account balance, local-model savings tracking (¥/$ follows the UI language).
- [Small-tailqwq/dsh-deep-whale](https://github.com/Small-tailqwq/dsh-deep-whale) (★56) — "Whale-girl" skin series (maid-atelier), CC BY-NC-SA 4.0.
- [Tommy00748/dsh-theme-cyberpunk2077](https://github.com/Tommy00748/dsh-theme-cyberpunk2077) (★12) — Cyberpunk 2077 / Night City theme: NC yellow × neon cyan, CRT scanlines, Kiroshi hover lock-on, combat-state HUD, synthesized typewriter & message SFX, hidden easter eggs (relic / johnny).
- [Nagi-ovo/dsh-ads](https://github.com/Nagi-ovo/dsh-ads) (★61) — Tongue-in-cheek 2005-style Chinese-site ads in the sidebar / chat feed / popups.
- [alingalingling/ui-status-label](https://github.com/alingalingling/ui-status-label) (★18) — Customize the "deep diving" thinking-status label however you like.
- [omdsh-dev/dsh-genui](https://github.com/omdsh-dev/dsh-genui) (★9) — GenUI: interactive components (layout, charts, mermaid, 3D) rendered inline via the `dsh-ui` fence.
- [vlln/whale-girl](https://github.com/vlln/whale-girl) (★10) — Desktop-pet plugin (QQ-pet style): draggable, feedable, accumulative companion.
- [Nagi-ovo/dsh-visualize](https://github.com/Nagi-ovo/dsh-visualize) (★15) — Generative UI: the model draws interactive HTML cards straight into the chat stream.
- [ZSeven-W/dsh-openpencil](https://github.com/ZSeven-W/dsh-openpencil) (★19) — OpenPencil design preview & editing plugin.
- [omdsh-dev/dsh-annotation](https://github.com/omdsh-dev/dsh-annotation) (★9) — Select text → annotate → send as a message; bubble-hidden annotation blocks.
- [Anionex/dsh-computer-use](https://github.com/Anionex/dsh-computer-use) (★6) — Computer-use plugin for DSH.

### Terminal & Desktop

**中文**：把 DSH 从网页端带到终端、桌面，或做成独立 App / 启动器。

- [ccch1mneyyy/dsh-cc-tui](https://github.com/ccch1mneyyy/dsh-cc-tui) (★96) — Claude Code-style full-screen TUI: pixel-whale top bar, live status row, streaming thoughts, double-Esc rollback, context bar + TPS meter. One-line npm install.
- [huiliyi37/dsh-tianshu-tui](https://github.com/huiliyi37/dsh-tianshu-tui) (★53) — DSH terminal UI.
- [chen-001/dsh-grok-tui](https://github.com/chen-001/dsh-grok-tui) (★5) — Grok-style TUI.
- [hust-open-atom-club/oh-dsh-desktop](https://github.com/hust-open-atom-club/oh-dsh-desktop) (★46) — Extensible macOS workbench: native PTY, workspace tools, live bilingual plugins, isolated-preview plugin marketplace.
- [Ruler4396/dsh-launcher](https://github.com/Ruler4396/dsh-launcher) (★9) — Lightweight Windows launcher: silent logon autostart + a minimal WebView2 window instead of a full browser.
- [bitterSmilezzz/dsh-mac-desktop](https://github.com/bitterSmilezzz/dsh-mac-desktop) (★1) — macOS desktop wrapper.
- [hanelalo/browser-bridge](https://github.com/hanelalo/browser-bridge) (★17) — Let your agent drive your real browser window like you would.
- [Lum1104/dsh-browser](https://github.com/Lum1104/dsh-browser) (★16) — Chrome sidebar extension so DSH operates your browser directly, no vision needed.
- [whiteguo233/dsh-openbiliclaw](https://github.com/whiteguo233/dsh-openbiliclaw) (★4) — Bilibili integration for DSH.
- [vvlife/deepseek-harness-desktop](https://github.com/vvlife/deepseek-harness-desktop) — Self-contained macOS app: bundles the Node runtime + full dsh + full Paseo (daemon + Web UI + mobile pairing) into one APP — drag to Applications and go, zero pre-install. Mobile QR pairing, WhaleHub plugin marketplace, built-in HTML preview, one-click public deploy; isolated from any dsh/Paseo already on your machine.

- [Zhuchen00123/dsh-wsl-modes](https://github.com/Zhuchen00123/dsh-wsl-modes) (★1) — DSH WSL presets: minimal-wsl + code-wsl with WSL Linux bash + bwrap sandbox and anchored bootstrap.

### Vision & Multimodal

**中文**：让纯文本模型也能"看图"：图像问答、长截图 OCR、UI 还原、像素比对等。

- [Anionex/dsh-vision-toolkit](https://github.com/Anionex/dsh-vision-toolkit) (★106) — Vision toolkit for text-only models: intent-aware image Q&A, long-screenshot OCR, UI restoration, grounding, pixel diff, Artifacts, Web UI.
- [windyslime/DeepSee](https://github.com/windyslime/DeepSee) (★1) — DSH `0.1.0-rc.5` Web-profile vision integration: image turns go through a local DeepSee gateway with pluggable VLM backends while normal text routing stays in DSH.
- [zhouwumu2-lab/dsh-vision-fix](https://github.com/zhouwumu2-lab/dsh-vision-fix) (★10) — Vision fix / repair helper.
- [sjscy05/deepseek-harness-vision-plugin](https://github.com/sjscy05/deepseek-harness-vision-plugin) — Vision plugin for DSH.
- [good-boy4069/Deepseek-omnimodal](https://github.com/good-boy4069/Deepseek-omnimodal) (★2) — Omnimodal support.
- [YYTbit/dsh-plugin-vision-toolkit](https://github.com/YYTbit/dsh-plugin-vision-toolkit) — Vision-toolkit bridge.

### Tools & Editor UX

- [Zhangbo-cn/dsh-voice-input-plugin](https://github.com/Zhangbo-cn/dsh-voice-input-plugin) (★6) — Composer mic for the Web UI: tap-to-monitor live transcription and hold-to-talk, with host Edge TTS reply reading that streams while the model generates, echo-pause during reading, and tap-to-stop.

**中文**：编辑器体验增强、`@file` 引用、消息分支编辑、会话回滚等"好不好用全靠它"的小工具。

- [omdsh-dev/dsh-at-file](https://github.com/omdsh-dev/dsh-at-file) (★21) — Codex-style `@file` mentions: search workspace files in the composer and attach their contents to prompts.
- [omdsh-dev/dsh-custom-tool](https://github.com/omdsh-dev/dsh-custom-tool) (★17) — Create & manage sandboxed JavaScript tools with a Monaco editor and model-driven tool lifecycle.
- [Moeblack/dsh-message-edit](https://github.com/Moeblack/dsh-message-edit) (★9) — Branch-based message editing, reroll, retry, version timeline.
- [Anionex/dsh-turn-rewind](https://github.com/Anionex/dsh-turn-rewind) (★16) — Rewind conversation + workspace state via a persistent Change Ledger.
- [Electricitysheep/dsh-tool-turbo](https://github.com/Electricitysheep/dsh-tool-turbo) (★1) — Tool turbo.
- [LingLambda/dsh-undo](https://github.com/LingLambda/dsh-undo) (★1) — Undo support.
- [fakechris/dsh-track](https://github.com/fakechris/dsh-track) (★1) — Tracking helper.
- [omdsh-dev/dsh-plugin-skills](https://github.com/omdsh-dev/dsh-plugin-skills) (★1) — Skills plugin.
- [leechen298/Code2Skill](https://github.com/leechen298/Code2Skill) (★4) — Generates Function, MCP, Agent Skill, and offline test packages from existing code as an installable DSH bundle.
- [omdsh-dev/dsh-mnemon](https://github.com/omdsh-dev/dsh-mnemon) (★1) — Mnemonics plugin.
- [ArtificialNotImbecile/dsh-context-taxonomy](https://github.com/ArtificialNotImbecile/dsh-context-taxonomy) — Context taxonomy.

### Agent orchestration & Workflow

**中文**：多 Agent 团队、可治理的工作流、会话蒸馏等"把一次性调度变成工程资产"的编排类插件。

- [NanmiCoder/dsh-agent-teams](https://github.com/NanmiCoder/dsh-agent-teams) (★30) — AgentTeams plugin for DSH.
- [icetomoyo/dsh_workflow](https://github.com/icetomoyo/dsh_workflow) (★29) — Brings Claude Code's UltraCode to DSH; turns one-shot multi-agent dispatch into a generatable / savable / governable / observable / recoverable Workflow layer.
- [btspoony/mstar-harness](https://github.com/btspoony/mstar-harness) (★38) — Skill-driven Harness / Loop Engineering Workflow Agent Plugin.
- [LoserFox/distill](https://github.com/LoserFox/distill) (★11) — Automatic conversation distillation: background subagent reflection + skill create/update.
- [titanwings/dsh-plannotator](https://github.com/titanwings/dsh-plannotator) (★1) — Plan annotator.
- [yyh-001/dsh-companion](https://github.com/yyh-001/dsh-companion) (★2) — Companion plugin.
- [vibeinging/dsh-work](https://github.com/vibeinging/dsh-work) (★2) — Work plugin.
- [omdsh-dev/dsh-gomoku](https://github.com/omdsh-dev/dsh-gomoku) (★5) — Gomoku game plugin.
- [ZK-Andy/dsh-continual-evolve](https://github.com/ZK-Andy/dsh-continual-evolve) (★11) — Continual self-evolution: versioned, auditable, rollback-safe harness state (prompt notes, memories, skills, subagent specs) refined from session trajectories.

**DSH skill bundles (satan9394) — 20 Chinese skill packs**：苏格拉底追问 / 热点采集 / 前端设计 / 技能创作 / 合同审查 / 会议纪要 / 求职 / 去AI痕迹 / 工程方法论 / Karpathy 方法论 / PPT / 上下文工程 / 怀疑驱动开发 / 领域建模 / 合并冲突 / 安全加固 / 代码评审 / 会话交接 / 懒人开发 / 学术研究。全部为 skill 型插件（`skills/<name>/SKILL.md` 经 `ctx.skills` 注册），每个都是独立 GitHub 仓库并带 `dsh-plugin` topic：

- [satan9394/dsh-grill-me](https://github.com/satan9394/dsh-grill-me) (★0) — Socratic grill-me skill: interview until shared understanding via structured questions.
- [satan9394/dsh-hot-trends](https://github.com/satan9394/dsh-hot-trends) (★0) — China real-time hot lists tool+skill (Weibo/Baidu/Bilibili/Zhihu/App Store/QQ Music), no API key.
- [satan9394/dsh-frontend-design](https://github.com/satan9394/dsh-frontend-design) (★0) — Frontend design skill (adapted from Anthropic frontend-design, Apache-2.0).
- [satan9394/dsh-skill-creator](https://github.com/satan9394/dsh-skill-creator) (★1) — Skill creator: author SKILL.md per agentskills.io (adapted from Anthropic skill-creator, Apache-2.0).
- [satan9394/dsh-contract-review](https://github.com/satan9394/dsh-contract-review) (★0) — Chinese contract risk review with graded reports.
- [satan9394/dsh-meeting-minutes](https://github.com/satan9394/dsh-meeting-minutes) (★0) — Meeting minutes from transcripts: decisions, action items, owners, deadlines.
- [satan9394/dsh-career-ops](https://github.com/satan9394/dsh-career-ops) (★0) — Job-search command center: JD A-F scoring, resume optimization, interview prep.
- [satan9394/dsh-humanizer-zh](https://github.com/satan9394/dsh-humanizer-zh) (★0) — Remove AI-sounding patterns from Chinese text.
- [satan9394/dsh-superpowers-essentials](https://github.com/satan9394/dsh-superpowers-essentials) (★0) — Engineering methodology: classify & approve before coding (Spike/Bounded/Architectural) + systematic debugging.
- [satan9394/dsh-karpathy-methodology](https://github.com/satan9394/dsh-karpathy-methodology) (★0) — Karpathy coding methodology: think first, simplicity, surgical changes, goal-driven verification.
- [satan9394/dsh-ppt-creator](https://github.com/satan9394/dsh-ppt-creator) (★0) — Chinese deck generator: outline → visual design → HTML/PPTX output.
- [satan9394/dsh-context-engineering](https://github.com/satan9394/dsh-context-engineering) (★0) — Context engineering: five-level context hierarchy + rules-file discipline.
- [satan9394/dsh-doubt-driven-dev](https://github.com/satan9394/dsh-doubt-driven-dev) (★0) — Doubt-driven development: adversarial fresh-context review before non-trivial decisions land.
- [satan9394/dsh-domain-modeling](https://github.com/satan9394/dsh-domain-modeling) (★0) — Domain modeling: CONTEXT.md glossary + ADR decision records.
- [satan9394/dsh-merge-conflicts](https://github.com/satan9394/dsh-merge-conflicts) (★0) — Resolve git merge/rebase conflicts in five steps.
- [satan9394/dsh-security-hardening](https://github.com/satan9394/dsh-security-hardening) (★0) — Security hardening: STRIDE threat modeling + three-tier boundary system.
- [satan9394/dsh-code-review](https://github.com/satan9394/dsh-code-review) (★0) — Five-axis code review: correctness/readability/architecture/security/performance.
- [satan9394/dsh-handoff](https://github.com/satan9394/dsh-handoff) (★0) — Session handoff document: compact current conversation for the next session/agent.
- [satan9394/dsh-ponytail-dev](https://github.com/satan9394/dsh-ponytail-dev) (★0) — Lazy senior dev philosophy: YAGNI ladder + root-cause fixes.
- [satan9394/dsh-academic-research](https://github.com/satan9394/dsh-academic-research) (★0) — Academic research pipeline: question → literature → verification → synthesis → paper → review.
- [satan9394/dsh-a11y-audit](https://github.com/satan9394/dsh-a11y-audit) (★0) — WCAG 2.2 accessibility audit: POUR principles, conformance levels, automated + manual verification, remediation guidance.
- [satan9394/dsh-web-clone](https://github.com/satan9394/dsh-web-clone) (★0) — Web clone: extract fonts/colors/motion/component specs from a reference image/URL and generate a high-fidelity web project.
- [satan9394/dsh-database-design](https://github.com/satan9394/dsh-database-design) (★0) — Database table design: PK/normalization/indexes/data types/constraints/performance, PostgreSQL-focused + general rules.
- [satan9394/dsh-changelog](https://github.com/satan9394/dsh-changelog) (★0) — Changelog automation: Keep a Changelog + Conventional Commits + semantic versioning, generate release notes from commits/PRs.
- [satan9394/dsh-postmortem](https://github.com/satan9394/dsh-postmortem) (★0) — Blameless incident postmortems: root-cause analysis (5 Whys), timeline, action items, organizational learning.
- [satan9394/dsh-runbook](https://github.com/satan9394/dsh-runbook) (★0) — Incident runbooks: severity levels, detect→triage→mitigate→recover→communicate, escalation paths, on-call handoff.
- [satan9394/dsh-slo](https://github.com/satan9394/dsh-slo) (★0) — SLI/SLO/error budgets: measurable reliability targets, error-budget alerting, SRE practices.
- [satan9394/dsh-quant-backtest](https://github.com/satan9394/dsh-quant-backtest) (★0) — Quant backtesting & risk metrics: avoid look-ahead/survivorship bias, transaction costs, walk-forward, Sharpe/drawdown.
- [satan9394/dsh-api-design](https://github.com/satan9394/dsh-api-design) (★0) — API & interface design: Hyrum's Law, stable/hard-to-misuse interfaces, REST/GraphQL/module boundaries, change evaluation.
- [satan9394/dsh-performance](https://github.com/satan9394/dsh-performance) (★0) — Performance optimization: measure-first, bottleneck localization, caching/lazy-loading, performance budgets.
- [satan9394/dsh-git-workflow](https://github.com/satan9394/dsh-git-workflow) (★0) — Git workflow & versioning: trunk-based development, commit discipline, semantic versioning, release process.
- [satan9394/dsh-cicd](https://github.com/satan9394/dsh-cicd) (★0) — CI/CD automation: quality gates, shift-left, deployment pipelines & strategies, debugging CI failures.
- [satan9394/dsh-spec-driven](https://github.com/satan9394/dsh-spec-driven) (★0) — Spec-driven development: write a structured spec before coding, gated four-phase workflow (spec → approval → implement → verify).
- [satan9394/dsh-planning](https://github.com/satan9394/dsh-planning) (★0) — Planning & task breakdown: verifiable tasks, dependency ordering, estimation, milestones, progress tracking.
- [satan9394/dsh-deprecation](https://github.com/satan9394/dsh-deprecation) (★0) — Deprecation & migration: code is a liability, safe removal of old systems/APIs, migration lifecycle planning.
- [satan9394/dsh-observability](https://github.com/satan9394/dsh-observability) (★0) — Observability & instrumentation: logs/metrics/traces, structured logging, distributed tracing, alert design.
- [satan9394/dsh-tdd](https://github.com/satan9394/dsh-tdd) (★0) — Test-driven development: red-green-refactor loop, Prove-It pattern for bug fixes, tests as proof.
- [satan9394/dsh-shipping](https://github.com/satan9394/dsh-shipping) (★0) — Shipping & launch: pre-release checklist, canary/gradual rollout, rollback-first, post-launch monitoring.
- [satan9394/dsh-idea-refine](https://github.com/satan9394/dsh-idea-refine) (★0) — Idea refinement: structured divergent/convergent thinking, turn vague ideas into sharp actionable one-pagers.
- [satan9394/dsh-incremental](https://github.com/satan9394/dsh-incremental) (★0) — Incremental implementation: small verifiable steps, keep the system runnable, avoid big-bang changes.
- [satan9394/dsh-source-driven](https://github.com/satan9394/dsh-source-driven) (★0) — Source-driven development: back every framework decision with official docs, verify and cite sources, no coding from memory.
- [satan9394/dsh-code-simplify](https://github.com/satan9394/dsh-code-simplify) (★0) — Code simplification: remove redundancy, reduce complexity, drop unnecessary abstractions, keep behavior identical.
- [satan9394/dsh-docs-adr](https://github.com/satan9394/dsh-docs-adr) (★0) — Documentation & ADRs: record the why, ADR format, documentation strategy, when not to write docs.
- [satan9394/dsh-debug-recovery](https://github.com/satan9394/dsh-debug-recovery) (★0) — Debugging & error recovery: evidence-first, error classification, systematic root-cause, recovery strategies, regression prevention.
- [satan9394/dsh-browser-testing](https://github.com/satan9394/dsh-browser-testing) (★0) — Browser testing & UI verification: verify DOM/console/network/performance in a real browser instead of guessing.
- [satan9394/dsh-frontend-engineering](https://github.com/satan9394/dsh-frontend-engineering) (★0) — Frontend UI engineering: component design, state management, data fetching, performance & maintainability.
- [satan9394/dsh-rag](https://github.com/satan9394/dsh-rag) (★0) — RAG retrieval-augmented generation: vector databases, embedding, document pipelines, retrieval & citation, hallucination mitigation.
- [satan9394/dsh-llm-eval](https://github.com/satan9394/dsh-llm-eval) (★0) — LLM evaluation: faithfulness/relevance/correctness, test sets, hallucination detection, regression guarding.
- [satan9394/dsh-data-quality](https://github.com/satan9394/dsh-data-quality) (★0) — Data quality frameworks: validation rules, data contracts, quality monitoring, CI automation.
- [satan9394/dsh-bash-scripting](https://github.com/satan9394/dsh-bash-scripting) (★0) — Defensive Bash scripting: set -euo pipefail, argument validation, error handling, debuggability, security.
- [satan9394/dsh-gitops](https://github.com/satan9394/dsh-gitops) (★0) — GitOps workflow: declarative infrastructure, Git as source of truth, continuous reconciliation, progressive delivery (ArgoCD/Flux).
- [satan9394/dsh-pci-compliance](https://github.com/satan9394/dsh-pci-compliance) (★0) — PCI compliance: cardholder data protection, six-pillar security controls, scope reduction strategies.
- [satan9394/dsh-agent-teams](https://github.com/satan9394/dsh-agent-teams) (★0) — Multi-agent team collaboration: roles, task coordination, parallel workflows, communication protocols.
- [satan9394/dsh-parallel-dev](https://github.com/satan9394/dsh-parallel-dev) (★0) — Parallel feature development: file ownership, interface contracts first, vertical slices vs horizontal layers.
- [satan9394/dsh-prompt-engineering](https://github.com/satan9394/dsh-prompt-engineering) (★0) — Prompt engineering patterns: CoT/ToT, dynamic few-shot, templates, production optimization & debugging.
- [satan9394/dsh-dataset-curation](https://github.com/satan9394/dsh-dataset-curation) (★0) — Dataset curation: cleaning, quality filtering, diversity, train/val splits, annotation specs.
- [satan9394/dsh-data-storytelling](https://github.com/satan9394/dsh-data-storytelling) (★0) — Data storytelling: SCQA narrative structure, chart selection, title-as-conclusion, credibility.
- [satan9394/dsh-mlops](https://github.com/satan9394/dsh-mlops) (★0) — ML pipeline workflow: data→train→evaluate→deploy→monitor, reproducible & regression-guarded MLOps.
- [satan9394/dsh-microservices](https://github.com/satan9394/dsh-microservices) (★0) — Microservices architecture patterns: service boundaries, communication, distributed data (Saga), resilience, event-driven.
- [satan9394/dsh-terraform](https://github.com/satan9394/dsh-terraform) (★0) — Terraform module library: module design, variable/output conventions, IaC best practices.
- [satan9394/dsh-architecture](https://github.com/satan9394/dsh-architecture) (★0) — Architecture patterns: Clean/Hexagonal/DDD tactical patterns, dependency rules, test boundaries.
- [satan9394/dsh-db-migration](https://github.com/satan9394/dsh-db-migration) (★0) — Database migration: up/down scripts, expand-contract, zero-downtime changes, consistency checks.
- [satan9394/dsh-auth](https://github.com/satan9394/dsh-auth) (★0) — Auth & authorization implementation: JWT/OAuth2/session, RBAC/ABAC, security checklist.
- [satan9394/dsh-error-handling](https://github.com/satan9394/dsh-error-handling) (★0) — Error handling patterns: layered errors, typed formats, graceful degradation, observability, recovery.
- [satan9394/dsh-sql-optimization](https://github.com/satan9394/dsh-sql-optimization) (★0) — SQL optimization patterns: EXPLAIN analysis, indexing strategy, N+1 resolution, query rewriting, slow-query debugging.
- [satan9394/dsh-monorepo](https://github.com/satan9394/dsh-monorepo) (★0) — Monorepo management: repo structure, workspace dependency management, incremental builds & caching, CI strategy, changeset publishing.
- [satan9394/dsh-systems-programming](https://github.com/satan9394/dsh-systems-programming) (★0) — Systems programming: memory safety patterns (RAII/ownership/smart pointers), concurrency & async patterns, memory/race debugging tools (ASan/Valgrind/Miri/TSan).
- [satan9394/dsh-startup-business-analyst](https://github.com/satan9394/dsh-startup-business-analyst) (★0) — Startup business analysis: TAM/SAM/SOM market sizing, competitive landscape (Five Forces/positioning), financial modeling (runway/cash flow), startup metrics (north star/LTV-CAC).
- [satan9394/dsh-bazel-build-optimization](https://github.com/satan9394/dsh-bazel-build-optimization) (★0) — Bazel build optimization: monorepo build config, fine-grained targets, remote caching/execution, pinned deps, visibility governance, build-speed triage.
- [satan9394/dsh-payment-processing](https://github.com/satan9394/dsh-payment-processing) (★0) — Payment processing & subscription billing: billing lifecycle, dunning/proration/tax, Checkout vs PaymentIntent vs SetupIntent, webhook idempotency, PCI compliance, test cards.
- [satan9394/dsh-event-driven-architecture](https://github.com/satan9394/dsh-event-driven-architecture) (★0) — Event-driven architecture: CQRS read/write separation, event sourcing & event store design, projections, Saga distributed transactions with compensation.
- [satan9394/dsh-service-mesh](https://github.com/satan9394/dsh-service-mesh) (★0) — Service mesh: Istio/Linkerd traffic management, mTLS zero-trust, certificate hierarchy & rotation, mesh observability (RED/tracing/access logs).
- [satan9394/dsh-llm-finetuning](https://github.com/satan9394/dsh-llm-finetuning) (★0) — LLM fine-tuning router & recipes: off-ramps (RAG/prompting), method selection (SFT/DPO/ORPO/KTO/GRPO+RLVR/CPT), LoRA/QLoRA, eval-first, quantized export.
- [satan9394/dsh-cloud-cost-optimization](https://github.com/satan9394/dsh-cloud-cost-optimization) (★0) — Cloud cost optimization: visibility/tagging/budget alerts, right-sizing, pricing models (RI/Savings Plans/Spot), storage tiering, FinOps cadence.
- [satan9394/dsh-vector-search](https://github.com/satan9394/dsh-vector-search) (★0) — Vector search engineering: embedding model selection, chunking strategy, index tuning (HNSW/IVF), hybrid search fusion (RRF/rerank), recall evaluation.
- [satan9394/dsh-blockchain-web3](https://github.com/satan9394/dsh-blockchain-web3) (★0) — Blockchain & smart contract security: Solidity vulnerability prevention (reentrancy/overflow/access control), CEI pattern, DeFi protocol design, audit prep & attack-path testing.
- [satan9394/dsh-game-development](https://github.com/satan9394/dsh-game-development) (★0) — Game development patterns: Godot 4 scenes/signals/state machines & GDScript, Unity ECS (DOTS/Jobs/Burst), performance optimization.
- [satan9394/dsh-file-conversion](https://github.com/satan9394/dsh-file-conversion) (★0) — File format conversion: PDF/Word/HEIC/MP4/CSV/EPUB routes, local tools first (ffmpeg/LibreOffice/Calibre), free online service fallback (999 routes).
- [satan9394/dsh-signed-audit-trails](https://github.com/satan9394/dsh-signed-audit-trails) (★0) — Signed audit trails for agent tool calls: Cedar policy gating (default-deny), Ed25519 hash-chained receipts, offline verification, CI/CD & compliance (EU AI Act/SLSA).
- [satan9394/dsh-multi-cloud](https://github.com/satan9394/dsh-multi-cloud) (★0) — Multi-cloud architecture: cross-provider decision framework, service comparison, four patterns (DR/best-of-breed/geo/abstraction), vendor lock-in & data gravity.
- [satan9394/dsh-python-development](https://github.com/satan9394/dsh-python-development) (★0) — Python development patterns: src layout & module cohesion, __all__ public APIs, type safety (mypy/pyright), packaging (pyproject/uv), performance & anti-patterns.
- [satan9394/dsh-hybrid-cloud](https://github.com/satan9394/dsh-hybrid-cloud) (★0) — Hybrid cloud networking: on-prem↔cloud connectivity (VPN vs Direct Connect/ExpressRoute), BGP routing & redundancy, active-active DR drills, data residency & gradual migration.
- [satan9394/dsh-javascript-typescript](https://github.com/satan9394/dsh-javascript-typescript) (★0) — JS/TS development patterns: modern JS best practices, TS advanced types (generics/conditional/mapped/utility), type-safe API clients, Node backend patterns.
- [satan9394/dsh-social-publishing](https://github.com/satan9394/dsh-social-publishing) (★0) — Social media publishing: cross-platform content campaigns, platform-native copy (limits/hashtags/tone), scheduling & rate-limit avoidance, media cropping, analytics review.
- [satan9394/dsh-frontend-mobile](https://github.com/satan9394/dsh-frontend-mobile) (★0) — Frontend & mobile development: React Native/Expo architecture, Next.js App Router (Server Components/streaming/parallel routes/Server Actions), rendering mode selection.
- [satan9394/dsh-e2e-testing](https://github.com/satan9394/dsh-e2e-testing) (★0) — End-to-end testing (Playwright/Cypress): test pyramid boundaries, critical journeys, anti-flaky strategies, CI sharding, failure traces, a11y & responsive checks.
- [satan9394/dsh-review-agent-governance](https://github.com/satan9394/dsh-review-agent-governance) (★0) — Review-agent governance: human-approval windows gating agent PR reviews/merges/releases/CI edits, Cedar default-deny, Ed25519 receipts, offline chain verification.
- [satan9394/dsh-x-twitter-research](https://github.com/satan9394/dsh-x-twitter-research) (★0) — X/Twitter research: account research, timeline/trend monitoring, launch-signal tracking, giveaway audits, approval-gated posting (read-first workflow).
- [satan9394/dsh-codebase-scanner](https://github.com/satan9394/dsh-codebase-scanner) (★0) — Codebase scanner: generate project-doc.md (tech stack/architecture/style/data) & AGENTS.md, full + delta scans detecting drift, context-window-safe analysis.
- [satan9394/dsh-track-driven-dev](https://github.com/satan9394/dsh-track-driven-dev) (★0) — Track-driven development: tracks as work units (spec.md → plan.md → TDD implementation), phase checkpoints, quality gates, commit SHA records, testable acceptance criteria.
- [satan9394/dsh-data-engineering](https://github.com/satan9394/dsh-data-engineering) (★0) — Data engineering: Airflow DAG design (idempotent/atomic/incremental/observable), dbt layered modeling (staging/intermediate/marts), Spark optimization, pipeline debugging.
- [satan9394/dsh-kubernetes-operations](https://github.com/satan9394/dsh-kubernetes-operations) (★0) — Kubernetes operations: Helm chart scaffolding & templating, Pod Security Standards (restricted), NetworkPolicy & RBAC least-privilege, deploy troubleshooting.
- [satan9394/dsh-reverse-engineering](https://github.com/satan9394/dsh-reverse-engineering) (★0) — Reverse engineering: binary analysis (disassembly/control-flow patterns), memory forensics, protocol RE, anti-reversing awareness, legal boundaries.
- [satan9394/dsh-hr-legal-compliance](https://github.com/satan9394/dsh-hr-legal-compliance) (★0) — HR & legal compliance: employment contract/offer letter/NDA templates, employee vs contractor, GDPR data handling (consent/DSR/privacy by design).
- [satan9394/dsh-brand-landingpage](https://github.com/satan9394/dsh-brand-landingpage) (★0) — Brand-first landing page design: brand identity interview → design system tokens → generate/feedback loop → deployment-ready HTML (responsive + perf).
- [satan9394/dsh-framework-migration](https://github.com/satan9394/dsh-framework-migration) (★0) — Framework migration: AngularJS→Angular (hybrid/incremental), React modernization, dependency upgrade path (codemod/breaking changes), rollback-safe risk management.
- [satan9394/dsh-plugin-eval](https://github.com/satan9394/dsh-plugin-eval) (★0) — Plugin/skill quality evaluation: three layers (static analysis/LLM judge/Monte Carlo), ten scoring dimensions, composite formula, anti-pattern penalties, actionable improvement guide.
- [satan9394/dsh-bash-testing](https://github.com/satan9394/dsh-bash-testing) (★0) — Shell script testing with BATS: error-path & boundary tests with message assertions, fixtures & dependency stubs, CI integration, multi-shell dialect validation.
- [satan9394/dsh-kpi-dashboard-design](https://github.com/satan9394/dsh-kpi-dashboard-design) (★0) — KPI dashboard design: SMART metric selection, strategic/tactical/operational tiers, dashboard hierarchy (summary/dept/drilldown), visualization best practices, metric governance.
- [satan9394/dsh-dotnet-backend](https://github.com/satan9394/dsh-dotnet-backend) (★0) — .NET backend patterns: Clean Architecture layering, DI lifetimes, EF Core/Dapper (N+1 prevention), IOptions config, Redis caching, Polly resilience, xUnit testing.
- [satan9394/dsh-before-you-build](https://github.com/satan9394/dsh-before-you-build) (★0) — Pre-build risk review: seven-dimension pre-mortem (demand/positioning/monetization/retention/trust/distribution/adoption), risk verdict, key assumption, smallest validation step.
- [satan9394/dsh-threat-modeling](https://github.com/satan9394/dsh-threat-modeling) (★0) — Threat modeling: attack tree construction (OR/AND/leaf with cost/time/skill/detection), STRIDE classification, mitigation mapping & prioritization, residual risk.
- [satan9394/dsh-operating-kit](https://github.com/satan9394/dsh-operating-kit) (★0) — Session operating discipline: start briefing (state doc/live check/drift reconciliation), end finalization (lessons/issues/next steps), stale-state prevention.
- [satan9394/dsh-content-marketing](https://github.com/satan9394/dsh-content-marketing) (★0) — Content marketing: topical clusters & multi-format creation, SEO (SERP gaps/schema/technical), social/email automation, omnichannel distribution, GA4 & CRO review.
- [satan9394/dsh-observability-tools](https://github.com/satan9394/dsh-observability-tools) (★0) — Observability tools: Prometheus config (naming/scraping/recording rules), Grafana dashboards (RED/USE, hierarchy, SLO panels), OpenTelemetry distributed tracing (context propagation/sampling).
- [satan9394/dsh-distributed-debugging](https://github.com/satan9394/dsh-distributed-debugging) (★0) — Distributed debugging: incident-response flow, metrics/logs/traces correlation, K8s & network troubleshooting, perf profiling, microservices & message-queue issues.
- [satan9394/dsh-sales-automation](https://github.com/satan9394/dsh-sales-automation) (★0) — Sales automation & customer support: personalized cold-email sequences (3-5 touchpoints), follow-up cadence, proposals & objection scripts, empathetic support & closure, conversion tracking.
- [satan9394/dsh-ai-image-design](https://github.com/satan9394/dsh-ai-image-design) (★0) — AI image generation workflow: prompt quality rules (50-150 words/self-contained), style guides (photographic/anime/illustration), batch & derivative prompts, brand consistency, review iteration.
- [satan9394/dsh-functional-programming](https://github.com/satan9394/dsh-functional-programming) (★0) — Functional programming: immutability & pure functions, pattern matching, Elixir/OTP (let it crash/supervision), Haskell types (newtype/GADT/total functions), effect isolation.
- [satan9394/dsh-tech-debt](https://github.com/satan9394/dsh-tech-debt) (★0) — Tech debt governance: audit (deps/dead code/markers), interest-risk-cost prioritization, incremental payoff with tests-first, fencing, debt registry & prevention.
- [satan9394/dsh-api-documentation](https://github.com/satan9394/dsh-api-documentation) (★0) — API documentation & developer experience: OpenAPI 3.1, interactive platforms (Swagger UI/Redoc), SDK generation, tested examples, developer portals, lifecycle docs.
- [satan9394/dsh-full-stack-orchestration](https://github.com/satan9394/dsh-full-stack-orchestration) (★0) — Full-stack feature orchestration: state-machine driven delivery (state.json), step-by-step with phase checkpoints, per-step artifacts, halt-on-failure, session resume/archive.
- [satan9394/dsh-deployment-validation](https://github.com/satan9394/dsh-deployment-validation) (★0) — Deployment validation & config management: config analysis (type/consistency/security), validation schemas in CI, secret scanning, cross-env drift, post-deploy checks & rollback.
- [satan9394/dsh-web-scripting](https://github.com/satan9394/dsh-web-scripting) (★0) — PHP/Ruby web development: PHP 8+ (generators/SPL/type system/OOP), Ruby idioms (blocks/DSL), performance profiling, security & minimal dependencies.
- [satan9394/dsh-api-scaffolding](https://github.com/satan9394/dsh-api-scaffolding) (★0) — FastAPI project scaffolding: layered structure (api/core/models/schemas/services), async patterns, dependency injection, Pydantic validation, unified error handling, pytest/Alembic/deploy.
- [satan9394/dsh-security-compliance](https://github.com/satan9394/dsh-security-compliance) (★0) — Security audit & compliance: DevSecOps pipeline (SAST/DAST/dependency/container), OAuth2/OIDC/JWT & zero-trust, OWASP & risk management, cloud posture, GDPR/HIPAA/SOC2 mapping, SLSA/SBOM/secrets.
- [satan9394/dsh-writing-for-agents](https://github.com/satan9394/dsh-writing-for-agents) (★0) — Writing for agents: context pointers & trigger branches, two budgets (context/cognitive load), information hierarchy (steps/reference/progressive disclosure/co-location), completion criteria, leading words, positive phrasing, pruning.
- [satan9394/dsh-issue-triage](https://github.com/satan9394/dsh-issue-triage) (★0) — Issue/PR triage: state machine (bug/enhancement + needs-triage/needs-info/ready-for-agent/ready-for-human/wontfix), verification & grilling, agent-ready briefs.
- [satan9394/dsh-git-guardrails](https://github.com/satan9394/dsh-git-guardrails) (★0) — Git safety guardrails: block dangerous commands (push/--force/reset --hard/clean -f/branch -D/checkout .) via PreToolUse hooks, project/global install, human-confirmed overrides, safe alternatives.
- [satan9394/dsh-teach](https://github.com/satan9394/dsh-teach) (★0) — Teaching: stateful learning workspace (MISSION/reference/learning-records/lesson HTML/components), knowledge-skills-wisdom, fluency vs storage strength, desirable difficulty (retrieval/spacing/interleaving), zone of proximal development.
- [satan9394/dsh-codebase-design](https://github.com/satan9394/dsh-codebase-design) (★0) — Deep-module codebase design: small interface + deep implementation, exact vocabulary (module/interface/seam/adapter), interface-as-contract, leverage & locality, testability & AI-navigability.
- [satan9394/dsh-prototype](https://github.com/satan9394/dsh-prototype) (★0) — Prototyping: throwaway code that answers a design question (logic/state-model vs UI variants), one-command runnable, no persistence, surfaced state, archive as primary source after validation.
- [satan9394/dsh-to-questionnaire](https://github.com/satan9394/dsh-to-questionnaire) (★0) — Decision-to-questionnaire: turn unanswered decisions into an async questionnaire for the knowledge holder (grill the send: who/what you need back), gap-targeted questions, theme-grouped most-important-first.
- [satan9394/dsh-wayfinder](https://github.com/satan9394/dsh-wayfinder) (★0) — Wayfinding for huge work: shared decision map on the issue tracker, named destination, decision tickets resolved one at a time, name-based references, index-not-store map, hand off when the path is clear.
- [satan9394/dsh-setup-wizard](https://github.com/satan9394/dsh-setup-wizard) (★0) — Interactive setup wizard: bash wizard for human-only steps (provisioning/credentials/CI secrets/third-party dashboards), scoped stages, captured values to .env/secrets, confirmations, ephemeral by default.
- [satan9394/dsh-workflow-loop](https://github.com/satan9394/dsh-workflow-loop) (★0) — Delegable workflow design: loop lens for recurring patterns, workflow specs (trigger/checkpoint/push-right/brief), grilled until an implementer can build without questions.
- [satan9394/dsh-writing-shape](https://github.com/satan9394/dsh-writing-shape) (★0) — Writing shape: shape raw material into an article paragraph-by-paragraph, grounding discipline (prerequisites vs introduced concepts), 2-3 candidate openings, write-as-you-go.
- [satan9394/dsh-writing-beats](https://github.com/satan9394/dsh-writing-beats) (★0) — Beat-based writing: assemble material into a choose-your-own-adventure journey, one move per beat, grounding-set-driven reachability, candidate starting/next beats with previews.
- [satan9394/dsh-writing-fragments](https://github.com/satan9394/dsh-writing-fragments) (★0) — Writing explore: mine raw fragments (sharp sentences/claims/vignettes/leading words), no structure commitment, capture from the first line, single-file append.
- [satan9394/dsh-mcp-builder](https://github.com/satan9394/dsh-mcp-builder) (★0) — MCP server building: four-phase workflow (research & planning, protocol study, framework choice, implement & iterate), tool design (coverage/naming/context/actionable errors), real agent verification.
- [satan9394/dsh-document-generation](https://github.com/satan9394/dsh-document-generation) (★0) — Office document generation: Word (docx-js gotchas, render verification) & Excel (openpyxl/pandas, zero formula errors, recalc validation, spec-literal), editing existing files by convention.
- [satan9394/dsh-internal-comms](https://github.com/satan9394/dsh-internal-comms) (★0) — Internal communications: 3P updates, company newsletters, FAQ answers, status/leadership/project updates, incident reports (type → guideline → format/tone/gathering).
- [satan9394/dsh-brand-guidelines](https://github.com/satan9394/dsh-brand-guidelines) (★0) — Brand styling: palette (primary/secondary/accent) & typography pairing (heading/body with fallbacks), background-aware color choice, accent rotation for shapes, hierarchy & readability.
- [satan9394/dsh-algorithmic-art](https://github.com/satan9394/dsh-algorithmic-art) (★0) — Algorithmic art: two-step flow (create an algorithmic philosophy → express in p5.js), seeded randomness/noise fields/particle systems, interactive parameter exploration, originality discipline.
- [satan9394/dsh-theme-factory](https://github.com/satan9394/dsh-theme-factory) (★0) — Theme factory: 10 preset professional themes (palette + font pairing) for slides/docs/HTML, showcase→choose→confirm→apply, on-the-fly theme generation, contrast & readability.
- [satan9394/dsh-doc-coauthoring](https://github.com/satan9394/dsh-doc-coauthoring) (★0) — Doc co-authoring: three-stage workflow (context gathering with meta questions/templates/info-dump → refinement & structure → reader testing with a fresh no-context session), alt-text checks.
- [satan9394/dsh-discernment-nudge](https://github.com/satan9394/dsh-discernment-nudge) (★0) — Discernment nudge: after substantive answers, 2-3 content-bound follow-ups (check facts / question reasoning / notice missing context), at most once per conversation, with skip conditions.
- [satan9394/dsh-gif-creator](https://github.com/satan9394/dsh-gif-creator) (★0) — GIF creation: search via GIF APIs (keyword/licensing), custom text/frame animations, size/loop optimization, platform-fit (Slack) & share-ready output.
- [satan9394/dsh-llm-api-integration](https://github.com/satan9394/dsh-llm-api-integration) (★0) — LLM API integration patterns: SDK vs raw HTTP (no mixing), streaming default, thinking modes, tool use, prompt caching, drift verification (never guess SDK usage), model migration & prompt audit.
- [satan9394/dsh-prompt-audit](https://github.com/satan9394/dsh-prompt-audit) (★0) — Prompt audit & model migration: scan prompts/skills/tool descriptions for stale patterns, scope & target model, inventory & provenance, report (file:line/reason/confidence) + suggested diff.
- [satan9394/dsh-recsys-pipeline](https://github.com/satan9394/dsh-recsys-pipeline) (★0) — Recommendation/ranking pipeline: six-stage framework (Source→Hydrator→Filter→Scorer→Selector→SideEffect) for any top-K problem (feeds, search ranking, RAG rerankers, task prioritizers).
- [satan9394/dsh-webapp-testing](https://github.com/satan9394/dsh-webapp-testing) (★0) — Web app testing with Playwright: decision tree (static HTML vs dynamic server), recon-then-act (networkidle → screenshot/DOM → selectors → actions), server lifecycle helper, browser logs.
- [satan9394/dsh-sast-security](https://github.com/satan9394/dsh-sast-security) (★0) — SAST tooling: Semgrep/SonarQube/CodeQL config, custom rules, CI quality gates, false-positive tuning, scan performance, defense-in-depth with DAST/dependency scanning.
- [satan9394/dsh-security-requirements](https://github.com/satan9394/dsh-security-requirements) (★0) — Security requirement extraction: three-layer translation (business → security requirements → technical controls), types (functional/non-functional/constraint), traceability/testability/priority, user stories & acceptance criteria.
- [satan9394/dsh-pdf-processing](https://github.com/satan9394/dsh-pdf-processing) (★0) — PDF processing: read/extract text & tables, merge/split, rotate/watermark, create, fill forms, encrypt/decrypt, extract images, OCR (pypdf/pdfplumber/reportlab).
- [satan9394/dsh-canvas-design](https://github.com/satan9394/dsh-canvas-design) (★0) — Canvas visual design: create a design philosophy (form/space/color/composition) then express it as poster/art (90% visual + 10% text), original work only.
- [satan9394/dsh-commit-message](https://github.com/satan9394/dsh-commit-message) (★0) — Git commit message conventions: Conventional Commits (type(scope): subject), body/footers, BREAKING CHANGE, issue refs, atomic commits, semver linkage.
- [satan9394/dsh-web-artifacts](https://github.com/satan9394/dsh-web-artifacts) (★0) — Interactive web artifact building: React 18+TS+Tailwind+shadcn/ui scaffold → develop → bundle single HTML, anti-AI-slop design guidelines, responsive & accessible.
- [satan9394/dsh-pptx-engineering](https://github.com/satan9394/dsh-pptx-engineering) (★0) — PPTX engineering: pptxgenjs gotchas (layout/hex colors/shadow/lists/native charts), unzip-edit-zip editing, markitdown/thumbnail reading, schema validation & render checks.
- [satan9394/dsh-css-art-styles](https://github.com/satan9394/dsh-css-art-styles) (★0) — CSS art style recipes: reusable visual systems (liquid-glass variants, cinematic space) with design tokens, utility CSS, entrance animations, layout skeletons.
- [satan9394/dsh-diagram-design](https://github.com/satan9394/dsh-diagram-design) (★0) — Editorial diagram design: 38 diagram types as self-contained HTML/SVG (architecture/flow/sequence/ER/swimlane/Wardley/Sankey/fishbone), deletion-first philosophy, brand style gate, semantic patterns.
- [satan9394/dsh-screenshot-to-code](https://github.com/satan9394/dsh-screenshot-to-code) (★0) — Screenshot-to-code: analyze layout/components/tokens → generate HTML/Tailwind/React → render-and-compare iteration (pixel alignment/responsive/interaction) → deliver.
- [satan9394/dsh-agent-loop-engineering](https://github.com/satan9394/dsh-agent-loop-engineering) (★0) — Agent loop engineering: L1 auto/L2 assisted loop tiers, loop patterns (daily triage / PR babysitter / dependency sweeper / changelog drafter), multi-loop coordination, verifier + human gates, loop-audit (readiness/cost), anti-patterns.
- [satan9394/dsh-cad-modeling](https://github.com/satan9394/dsh-cad-modeling) (★0) — Parametric CAD modeling: STEP-first (build123d Python source or direct STEP import), natural-language specs / reference images / 2D drawings, assemblies with source-level joints & mating datums, geometry checks, STL/3MF/GLB exports.
- [satan9394/dsh-cli-anything](https://github.com/satan9394/dsh-cli-anything) (★0) — Make any software agent-native: 7-phase CLI harness pipeline (analyze→design→implement→test→publish), real-backend integration (no toy implementations), JSON output + REPL dual mode, refine gap analysis, output verification (never trust exit 0).
- [satan9394/dsh-personal-content-discovery](https://github.com/satan9394/dsh-personal-content-discovery) (★0) — Cross-platform personalized content discovery: five-layer soul portrait (event→preference→awareness→insight→soul), MBTI inference, active exploration breaking filter bubbles, cross-platform interest fusion, local-first, friend-style explainable recommendations.
- [satan9394/dsh-colleague-creation](https://github.com/satan9394/dsh-colleague-creation) (★0) — Distill a real person into an AI skill: source materials (chat/docs/email/screenshots) + subjective description → a skill that works like them (Work Skill + 5-layer persona, personality/company-culture/level tags, incremental evolution, version rollback).
- [satan9394/dsh-designmd](https://github.com/satan9394/dsh-designmd) (★0) — DESIGN.md design-system format for coding agents: YAML design tokens (colors/typography/rounded/spacing/components) + Markdown rationale, token references, lint/diff/export toolchain (Tailwind v3/v4, W3C DTCG), WCAG AA contrast checks.
- [satan9394/dsh-content-distillation](https://github.com/satan9394/dsh-content-distillation) (★0) — Distill books/videos/podcasts into callable AI skills: RIA-TV++ 7-phase pipeline (Adler analysis → 5 parallel extractors → triple verification 25-50% pass → RIA++ construction → Zettelkasten links → trap-question stress tests → DIGEST.md + installable skills).
- [satan9394/dsh-investment-research](https://github.com/satan9394/dsh-investment-research) (★0) — Personal investment research methodology (A-share/US/HK): five-dimension analysis (valuation/capital/financials/industry/catalyst-risk), bull-bear debate (fact sheet first → bull/bear → neutral moderator lists divergence + verification checklist), reflection audit, daily review — deliberately never outputs buy/sell calls.
- [satan9394/dsh-relationship-coach](https://github.com/satan9394/dsh-relationship-coach) (★0) — Relationship/dating coach: emotions first then solutions, fact/guess/unknown separation, reciprocity/reality/risk/opportunity-cost comparison, sendable scripts + observation windows + stop conditions, safety-first for dangerous situations.
- [satan9394/dsh-frontend-slides](https://github.com/satan9394/dsh-frontend-slides) (★0) — Zero-dependency HTML presentations: show-don't-tell visual style discovery (3 previews to pick from), PPT→web conversion preserving assets, anti-AI-slop curated styles, 34 bold design systems with progressive loading (index → preview cards → full design.md only when picked).
- [satan9394/dsh-html-ppt](https://github.com/satan9394/dsh-html-ppt) (★0) — HTML PPT Studio: 36 themes (token-driven reskin) × 31 layouts × 47 animations (27 CSS + 20 canvas FX) × 15 full-deck templates, presenter mode (S-key magnetic cards + speaker script + timer, BroadcastChannel-synced), keyboard navigation, zero build step.
- [satan9394/dsh-brand-design](https://github.com/satan9394/dsh-brand-design) (★0) — Brand design system: 5-step brand asset protocol (ask → search official brand pages → download assets → grep hex colors, never guess → freeze brand-spec.md), direction advisor (3 parallel logic subagents → 3 real visual options), Junior Designer workflow, anti-AI-slop rules, 5-dimension expert review.
- [satan9394/dsh-caveman-speak](https://github.com/satan9394/dsh-caveman-speak) (★0) — Terse token-saving output discipline: caveman-style answers (~65% fewer output tokens) while code/commands/errors stay byte-exact; token-sink audit (safe fix / offload / habit / load-bearing classes), progressive-disclosure recall.
- [satan9394/dsh-persistent-memory](https://github.com/satan9394/dsh-persistent-memory) (★0) — Cross-session persistent memory compression: lifecycle-hook observation capture, 3-layer retrieval workflow (search index → timeline → full details, ~10x token savings), progressive disclosure, private tags, hybrid vector+keyword search.
- [satan9394/dsh-planning-files](https://github.com/satan9394/dsh-planning-files) (★0) — Persistent 3-file planning: task_plan.md / findings.md / progress.md on disk re-injected every turn, plan survives /clear, crashes and compaction; session catchup recovery, isolated parallel-task dirs, opt-in completion gate.
- [satan9394/dsh-skill-seekers](https://github.com/satan9394/dsh-skill-seekers) (★0) — Knowledge data layer for AI systems: 18 source types (docs sites, GitHub repos, PDFs, videos, notebooks, wikis, chat exports) → structured assets, export to 22 targets (Claude/Gemini/OpenAI skills, RAG pipelines, coding assistants), AI-driven project scanning.
- [satan9394/dsh-scientific-research](https://github.com/satan9394/dsh-scientific-research) (★0) — Scientific skill pack: 100+ provenance-rich database lookups (PubChem/UniProt/ClinicalTrials.gov/FRED…), literature review + evidence-bounded hypothesis generation, costed experimental protocols, point-by-point peer-review rebuttals, method validation (ICH/USP/CLSI), publication-grade figures.
- [satan9394/dsh-marketing-growth](https://github.com/satan9394/dsh-marketing-growth) (★0) — Marketing growth skill tree: product-marketing foundation read first by all skills, seven clusters (SEO/CRO/copy/ads/retention/GTM/strategy), skill cross-references, marketing loops (recurring auto-run workflows), measurable experiment design.
- [satan9394/dsh-obsidian-vault](https://github.com/satan9394/dsh-obsidian-vault) (★0) — Obsidian vault operations: Obsidian Flavored Markdown (wikilinks/embeds/callouts/properties), Bases views (filters/formulas/summaries), JSON Canvas (nodes/edges/groups), Obsidian CLI, Defuddle clean-Markdown web extraction to save tokens.
- [satan9394/dsh-live-docs](https://github.com/satan9394/dsh-live-docs) (★0) — Live docs injection against hallucination: pull version-specific up-to-date docs before writing library/API code (CLI + MCP dual mode), library-ID direct fetch, explicit version pinning, rule-based auto-trigger — kills hallucinated APIs and stale examples.
- [satan9394/dsh-last30days](https://github.com/satan9394/dsh-last30days) (★0) — Cross-platform last-30-days research: 16+ sources (Reddit/X/YouTube/TikTok/HN/Polymarket/GitHub/arXiv) searched in parallel, scored by real engagement (upvotes/likes/real money), AI judge synthesizes one brief — pre-meeting people research, hiring signals, discovery of pre-peak topics, tool comparisons.
- [satan9394/dsh-repo-graphify](https://github.com/satan9394/dsh-repo-graphify) (★0) — Repository knowledge graph: multimodal extraction (AST/LLM/vision) of concepts & relationships, honest EXTRACTED/INFERRED/AMBIGUOUS edge tags, god nodes & surprising connections, ~71.5x token savings, wiki navigation, --watch auto-sync, git-commit hook rebuild.
- [satan9394/dsh-adhd-friendly](https://github.com/satan9394/dsh-adhd-friendly) (★0) — ADHD-friendly action-first outputs: lead with next action, numbered steps, end with one concrete next step, suppress tangents, restate state, specific time estimates, visible wins, matter-of-fact errors, lists capped at 5, no preamble/recap/closers.
- [satan9394/dsh-better-interface](https://github.com/satan9394/dsh-better-interface) (★0) — Interface quality skill series: six dimensions (UI polish/typography/colors/accessibility/layout/UX writing), variant (multiple genuinely different versions behind a picker, promote the winner), explain-interface (reverse-engineer any effect), interface-review (full-dimension review of changes/branch/PR).
- [satan9394/dsh-opinion-analysis](https://github.com/satan9394/dsh-opinion-analysis) (★0) — Multi-agent opinion analysis: 30+ domestic/global social platforms & millions of comments, four specialist agents (Query/Media/Insight/Report) + debate moderator, agent-forum chained deliberation against homogeneity, multimodal short-video parsing, public+private data fusion, interactive HTML report.
- [satan9394/dsh-office-cli](https://github.com/satan9394/dsh-office-cli) (★0) — Office suite designed for AI agents: single binary controls Word/Excel/PowerPoint (no Office install), path selectors (/slide[1]/shape[1]) for precise targeting, HTML rendering engine gives AI eyes (render→look→fix loop), live preview real-time feedback, outline/HTML/JSON views.
- [satan9394/dsh-swarm-prediction](https://github.com/satan9394/dsh-swarm-prediction) (★0) — Swarm intelligence prediction: build a high-fidelity parallel digital world from seed information, thousands of agents with independent personas/memory/behavior freely interact and socially evolve, inject variables god's-eye view to deduce future trajectories — rehearse the future in a digital sandbox.
- [satan9394/dsh-hallmark-design](https://github.com/satan9394/dsh-hallmark-design) (★0) — Anti-AI-slop UI design: 21 themes + macrostructure per brief, 57 slop-test gates + pre-emit self-critique, refuses on-distribution LLM defaults; four verbs (build / audit / redesign / study-DNA), Custom from-scratch mode.
- [satan9394/dsh-agent-reach](https://github.com/satan9394/dsh-agent-reach) (★0) — One-click internet capability for AI agents: 15+ platforms (web/YouTube subtitles/RSS/search/GitHub/X/Bilibili/Reddit/FB/IG/Xiaohongshu/LinkedIn/V2EX/Xueqiu/podcasts), zero-config first, multi-backend routing auto-failover, doctor diagnostics, cookies stay local.
- [satan9394/dsh-harness-os](https://github.com/satan9394/dsh-harness-os) (★0) — Agent harness config OS: four-layer separation (rules persistent / skills on-demand / agents specialized / hooks runtime), instincts continuous learning (+/evolve clustering), AgentShield security audit (secrets/hook-injection/MCP risk), Unified Memory Vault across harnesses, GateGuard destructive-command gate.

- [nortejiang-tech/dsh-req-miner](https://github.com/nortejiang-tech/dsh-req-miner) (★0) — Requirements-mining sidebar plugin: per-session floating interview window driven by a continuable subagent (decision tree + frontier questions), reads the bound session's workspace and recent context, one-click return of the summarized requirement prompt to the composer. Install: `github:nortejiang-tech/dsh-req-miner`.

### Integrations & Bridges

**中文**：把 DSH 接到 VS Code、桌面通知、或其它 Agent（Claude / Codex / Pi / OpenCode）的桥接类插件。

- [PandaPolo/dsh-voice-call](https://github.com/PandaPolo/dsh-voice-call) (★1) — Agent-initiated voice calls: `offer_call` rings the human (接听/拒接/稍后再说), accepted calls synthesize and play locally via CrispASR + Qwen3-TTS (9 speakers, 2 Chinese dialects), rejected calls return the decision to the agent.
- [omdsh-dev/dsh-open-in-vscode](https://github.com/omdsh-dev/dsh-open-in-vscode) (★28) — Open workspace directories in VS Code directly from the web GUI.
- [omdsh-dev/dsh-notification](https://github.com/omdsh-dev/dsh-notification) (★19) — Desktop notifications for turn completions, with per-outcome controls and include/exclude keyword rules.
- [Nagi-ovo/dsh-find-plugins](https://github.com/Nagi-ovo/dsh-find-plugins) (★12) — In-app plugin finder.
- [YYTbit/dsh-plugin-claude-bridge](https://github.com/YYTbit/dsh-plugin-claude-bridge) — Bridge to Claude.
- [YYTbit/dsh-plugin-codex-bridge](https://github.com/YYTbit/dsh-plugin-codex-bridge) — Bridge to Codex.
- [YYTbit/dsh-plugin-pi-bridge](https://github.com/YYTbit/dsh-plugin-pi-bridge) — Bridge to Pi.
- [YYTbit/dsh-plugin-opencode-bridge](https://github.com/YYTbit/dsh-plugin-opencode-bridge) — Bridge to OpenCode.
- [bobleer/deepseek-harness-plugin-mcp](https://github.com/bobleer/deepseek-harness-plugin-mcp) — MCP plugin.
- [labmimors/dsh-mcp-lens](https://github.com/labmimors/dsh-mcp-lens) (★5) — Progressive-disclosure MCP gateway for DSH: search remote tools, inspect exact input schemas on demand, then call an explicit server/tool pair.
- [yoke233/dsh-openai-codex-auth](https://github.com/yoke233/dsh-openai-codex-auth) (★1) — OpenAI Codex auth.
- [vvlife/dsh-agnes-paseo](https://github.com/vvlife/dsh-agnes-paseo) — Agnes AI model gateway (OpenAI-compatible) for dsh, plus a zero-dependency ACP bridge that registers DeepSeek Harness as a Paseo provider.
- [vvlife/dsh-paseo-mobile](https://github.com/vvlife/dsh-paseo-mobile) — Connect your phone to dsh via Paseo: one-command setup registers dsh as a Paseo provider (zero-dependency ACP bridge), then scan the pairing QR in the Paseo mobile app. Model-agnostic: follows your existing dsh model config; mirrors dsh web sessions to the phone with context-aware follow-ups.

- [SwainGao/dsh-plugin-ai-bridge](https://github.com/SwainGao/dsh-plugin-ai-bridge) (★1) — Bridge to external AI models (Codex / Claude / GPT / OpenAI-compatible relays) for read-only second-opinion code review, adversarial review, task delegation with resume threads, and non-blocking background jobs. `dsh plugin add dsh-plugin-ai-bridge@0.1.3`.

- [Nwflower/dsh-chat-import](https://github.com/Nwflower/dsh-chat-import) (★54) — Import Claude Code / Codex / ChatGPT / Cursor chat histories as resumable DeepSeek Harness sessions.

### Sidebar, Workspace & Ecosystem

**中文**：侧边栏工作台、`oh-my-dsh` 这类"插件库"、插件脚手架与注册表等生态基础设施。

- [omdsh-dev/DSH-better-sidebar](https://github.com/omdsh-dev/DSH-better-sidebar) (★66) — Full workbench sidebar with third-party tab registration: file render/edit, terminal, Git, subagent.
- [LaplaceYoung/oh-my-dsh](https://github.com/LaplaceYoung/oh-my-dsh) (★12) — Plugin ecosystem: 700+ plugins wired only through extension seams, no agent-loop changes.
- [kingjly/dsh-plugin-builder](https://github.com/kingjly/dsh-plugin-builder) (★1) — Plugin builder scaffolding.
- [vlln/plugin-registry](https://github.com/vlln/plugin-registry) (★6) — Plugin registry.
- [DeKrych/Dshell-plugins](https://github.com/DeKrych/Dshell-plugins) (★27) — Dshell plugin collection.
- [HackSing/dsh-plugins](https://github.com/HackSing/dsh-plugins) / [Yihong89/dsh-plugins](https://github.com/Yihong89/dsh-plugins) — Plugin collections.
- [coppynight/dsh-doctor](https://github.com/coppynight/dsh-doctor) (★2) — Diagnostics / doctor.
- [yyh-001/dsh-expression](https://github.com/yyh-001/dsh-expression) (★1) — Expression plugin.
- [Chinesezjc/dsh-interconnect](https://github.com/Chinesezjc/dsh-interconnect) (★8) — Cross-instance message/event handoff.

### Fun & Misc

**中文**：合影墙、音乐、框架类实验等"好玩 / 杂项"插件。

- [SenmuuuuW/dsh-group-photo](https://github.com/SenmuuuuW/dsh-group-photo) (★11) — Internal-test group-photo wall (GitHub OAuth, frozen allowlist).
- [syy-shark/dsh-music-plugin](https://github.com/syy-shark/dsh-music-plugin) — Music plugin.
- [unknowbug/RE-Framework](https://github.com/unknowbug/RE-Framework) (★5) / [unknowbug/anchorlaw](https://github.com/unknowbug/anchorlaw) (★4) — Frameworks.
- [hxs996-beep/deepAct](https://github.com/hxs996-beep/deepAct) (★7) — deepAct.
- [aga-j/dsh-mini-games](https://github.com/aga-j/dsh-mini-games) — Pure-frontend mini-game collection in the web details panel: guess-the-number, 2048, minesweeper (`dsh plugin --profile web add dsh-mini-games`).

## Hands-on Notes

**中文 · 实战评测**：下面挑了 6 个有代表性的高星插件，按"怎么装 / 怎么用 / 坑点"写成可直接照着做的短评测（star 数为 2026-08-13 当晚撰写时数据）。涉及 `dsh-external/*` 私有仓库的，已标注需要读取权限。

**English · hands-on notes**: short, copy-pasteable reviews of six representative
high-star plugins — install / use / gotchas. Star counts are from the night of
2026-08-13. Entries under `dsh-external/*` are private repos and need read
access.

### dsh-web-ui — Web UI 全家桶（★311）

**装**：npm 已发布到 `@linxin666` scope，推荐直接装聚合包：
`dsh plugin --profile web add @linxin666/dsh-web-ui-all`；只要皮肤就装
`@linxin666/dsh-skins`。装完重启 `dsh web`，侧边栏即出现全部入口。

**用**：任务看板（支持 cron 定时让 DSH 会话自动执行，如每天升级 DSH / 周一生成周报）、
Git 图谱、右侧预览面板（Markdown/HTML/代码/diff/CSV/PDF/Office/图片）、鲸鱼娘宠物、
实时 TPS 与令牌统计、移动端远程控制、以及 SSH 远程运维（xterm 终端 / SFTP / 端口转发 /
集群并发执行）。

**坑**：首次安装若报 `ERR_PNPM_IGNORED_BUILDS`，按提示把 `cloudflared` / `ssh2` 等加入
profile 的 `pnpm-workspace.yaml` 的 `allowBuilds` 再重跑。验证是否挂上可用
`dsh --profile web --dump-config`。

*Install `@linxin666/dsh-web-ui-all` to get the whole bundle (task board, git
graph, right panel, pet, live token stats, mobile remote, SSH ops). Add
`@linxin666/dsh-skins` for skins only. Restart `dsh web` after install. If you
hit `ERR_PNPM_IGNORED_BUILDS`, allowlist `cloudflared`/`ssh2` in the profile's
`allowBuilds`.*

### dsh-cc-tui — Claude Code 风格全屏终端（★103）

**装**：`dsh plugin --profile cc-tui add dsh-cc-tui`（会自动初始化 `cc-tui`
profile），然后 `dsh --profile cc-tui` 启动；或仓库根目录 `sh install.sh`
（Windows 用 `dsh-cc.cmd`，支持 `--resume` 恢复上次会话）。

**用**：像素鲸鱼顶栏 + 启动手绘动画、实时工作状态行（在跑哪个工具 / 思考文案）、
思考过程流式展开、双击 Esc 时间回溯（fork 重放历史消息）、底部蓝白上下文进度条 +
TPS 仪表、复刻 CC 的 `/` 命令菜单（`/plan` `/goal` `/compact` `/review` 等全部走官方链路）。

**坑**：需要官方 `dsh` CLI 与 `pnpm`；纯插件挂载，卸载即完全还原。它**不消费审批流**
（`/permissions` 仅说明现状）；`/model` 实时切换走"会话 fork 续聊"而非原位换模型。

*A Claude-Code-style full-screen TUI: pixel-whale banner, live status row,
streaming thinking, double-Esc rewind (fork + replay), context bar + TPS meter,
and CC-style `/` commands that all ride DSH's official services. Pure Cordis
mount — removing the plugin fully restores the host. No approval-flow UI yet.*

### DSH-better-sidebar — 侧边栏完整工作台（★71）

**装**：npm 已发布 `dsh-better-sidebar@0.10.2`：
`dsh plugin --profile web add dsh-better-sidebar@0.10.2`，装完重启 DSH 并硬刷新
（Cmd/Ctrl+Shift+R）。嫌麻烦可 `curl -fsSL <repo>/scripts/install.sh | bash`，脚本会
自动处理 `allowBuilds` 与旧挂载行。

**用**：右侧栏 + 底部面板双工作台——资源管理器（懒加载目录树、`@文件` 引用）、
CodeMirror 编辑预览（Office/PDF/HTML 沙箱 iframe）、内嵌浏览器（沙箱 iframe）、
xterm 真实终端（每会话最多 3 个）、Git 面板（真 diff + 暂存/提交）、后台任务页。
暴露 `ctx.betterSidebar` 服务，其它插件可注册侧边栏 Tab 与文件预览器。

**坑**：pnpm 11 的 `strict-dep-builds` 可能拦截 `node-pty` 构建，执行
`pnpm approve-builds --all` 再重跑；Git 面板无 push/pull/fetch；
`.xlsx` 不保留单元格样式，Office 预览约 23MB 首次较慢。

*Right-sidebar + bottom-panel workbench: file explorer, CodeMirror editor with
Office/PDF/HTML preview, sandboxed in-app browser, real xterm terminal, git
panel, background-task view. Exposes `ctx.betterSidebar` so other plugins can
register tabs/viewers. On pnpm 11 run `pnpm approve-builds --all` if node-pty's
build is ignored. Git panel has no push/pull; Office preview is ~23MB on first load.*

### dsh-vision-toolkit — 让纯文本模型"看见"（★110，私有仓库）

**装**：目前是 `dsh-external` 私有 GitHub release，需对该仓库的读取权限。
`git clone https://github.com/dsh-external/dsh-vision-toolkit.git` 后
`dsh plugin --profile web add "$PWD/dsh-vision-toolkit"`（Web 和 Headless 各加一次）。
Web 端进 **Settings → Vision Toolkit**，配一个 DSH Credential（如 `VISION_API_KEY`）
并点 **Test connection**。

**用**：会话里把图片放进 workspace 路径，调用 `/vision-tools` 激活，再让 Agent 用
`vision_glance`（图像问答）、`vision_ground`/`vision_detect`（定位框）、
`vision_crop`/`vision_trace`（裁剪/转 SVG）、`vision_pixel_diff`（像素比对）、
`vision_long_screenshot_ocr`（长截图 OCR）等 10 个工具。本地裁剪 / trace / 像素差
**不需要**视觉 API；远程识别需一个 OpenAI 兼容视觉端点（managed runtime 会自动装好
Python 3.11+ 环境）。

**坑**：私有仓库，没权限 `git clone` 会失败；远程工具需要配 Credential，否则只有本地
工具可用。

*Gives text-only DSH agents eyes via 10 structured vision tools (Q&A, grounding,
OCR, pixel diff, UI restoration…). Private `dsh-external` repo — needs read
access. Local crop/trace/diff need no vision API; remote recognition needs an
OpenAI-compatible endpoint configured as a DSH Credential. Managed runtime
auto-prepares Python 3.11+.*

### oh-my-dsh — 687 个插件的能力库（23 轮差距登记，5286 测试全绿）

**定位**：从 opencode / oh-my-pi / Codex / Claude Code / pi / Goose 等对照，把有用能力
以 DSH 插件形态重写——**只走扩展接缝**（`ctx.effect()` / `ctx.on()` / `ctx.tools`），
不改 agent-loop、不引入热路径开销。已登记 23 轮差距、687 个插件。

**用**：仓库按 `plugins/<gap-id>/` 组织，每个都是独立 DSH 插件。
`pnpm install && pnpm test` 跑全部；单个插件 `cd plugins/<gap-id> && pnpm test`。
端到端验证（`e2e/run-e2e.sh`）需要 `DSH_HOME/.env` 里的 `DEEPSEEK_API_KEY`。

**坑**：这是插件"**源码库 / 能力库**"，不是一条 `dsh plugin add` 就能装全家桶的聚合包；
要按需挑选具体插件单独安装。

*A capability library: 687 plugins rewritten from opencode / Claude Code / Codex /
pi / Goose etc., all through DSH's extension seams (no agent-loop changes). 5286
tests green. It's a source/ability repo, not a one-line aggregate — pick and
install individual plugins under `plugins/<gap-id>/`. e2e needs `DEEPSEEK_API_KEY`.*

### dsh_workflow — 把多 Agent 调度升级成可治理 Workflow（★30，私有仓库）

**装**：`dsh-external` 私有仓库，
`dsh plugin --profile web add "github:dsh-external/dsh_workflow#main"`，
`dsh --profile web --dump-config` 验证配置里出现 `dsh-external-workflow` 行后重启。

**用**：会话里 `/workflow list` 看内置/项目/个人 workflow；`/workflow parallel-investigation
{"question":"…"}` 跑并行调研；`/workflow create 设计一个并行安全评审流程` 现场生成；
`/workflow review --risk high --requirement "不得破坏公开 API" --wait` 跑受控评审。
支持命名/项目/个人 workflow、run graph、暂停/恢复/重跑/续跑、成本记录，以及
capability-only VM（QuickJS WASM）安全边界。

**坑**：需 Node >=22.19 且与 `compatibility.json` 一致的 DSH 快照；`github:` 安装需对该
私有仓库读取权限；`/workflow create` 形式**不接受** `--wait`，同步等待请用命名 workflow
的 `--wait`。同类多 Agent 主题另见 `dsh-agent-teams`。

*Upgrades one-shot multi-agent dispatch into a governable Workflow layer:
named/project/personal workflows, run graph, pause/resume/rerun, cost records,
and a QuickJS-WASM capability-only sandbox. Private `dsh-external` repo —
`github:` install needs read access and Node >=22.19. `/workflow create` does not
accept `--wait`; use it on named workflows. For teams of agents, see
`dsh-agent-teams`.*

## Other awesome lists (meta)

These are community "awesome" indexes for DSH — useful cross-references, some
with daily compatibility tracking:

- [AdamPlatin123/awesome-dsh-plugins](https://github.com/AdamPlatin123/awesome-dsh-plugins) (★187) — Directory with daily compatibility tracking.
- [0xsline/awesome-deepseek-harness](https://github.com/0xsline/awesome-deepseek-harness) (★84) — Curated plugins/tools/infra from `dsh-external/hub` and the `dsh-plugin` topic.
- [Alex-Yanggg/awesome-DSH-plugin](https://github.com/Alex-Yanggg/awesome-DSH-plugin) (★27)
- [awesome-dsh-plugin/awesome-dsh-plugin](https://github.com/awesome-dsh-plugin/awesome-dsh-plugin) (★19)
- [bruc3van/awesome-dsh-plugin](https://github.com/bruc3van/awesome-dsh-plugin) (★8)
- [walkinglabs/awesome-deepseek-harness-plugins](https://github.com/walkinglabs/awesome-deepseek-harness-plugins) (★1)

## Contributing

**中文**：两种方式让插件被收录，二选一即可——

**通道 A · 零维护（推荐）**：直接给你的 GitHub 仓库打上 **`dsh-plugin`** 话题。
[PLUGINS.md](PLUGINS.md) 由 [update.yml](.github/workflows/update.yml) 每天从
该话题自动抓取刷新，**无需提 PR**，约 24 小时内就会出现在快照里。

**通道 B · 进精选列表**：想进上面人工分类的精选 README？提一个 PR，把它加到合适的
分类（附一句话描述与当时的 star 数）。这个 PR 会被
[review-pr.yml](.github/workflows/review-pr.yml) **按规则自动审核**：

- ✅ 只能改 `README.md`（不能顺手改其他文件）；
- ✅ 新增的每个仓库必须公开存在；
- ✅ 必须明显是 DSH 插件——要么带 `dsh-plugin` 话题，要么名称/描述里出现
  DeepSeek Harness / DSH / Cordis / 外挂 / 插件 等字样；
- ✅ 不能与已有条目重复；
- ⚠️ `dsh plugin add <pkg>` 安装命令需格式正确。

全部通过会打 `auto-approved` 标签并**自动合并**；不通过会打 `changes-requested`
并指出原因，改完重推即可。维护者仍可随时人工覆盖。

完整规则见 [CONTRIBUTING.md](CONTRIBUTING.md)。

Found or built a plugin? Make it discoverable — pick either:

**Channel A · Zero maintenance (recommended):** just add the **`dsh-plugin`**
topic to your GitHub repo. [PLUGINS.md](PLUGINS.md) is fetched daily from that
topic by [update.yml](.github/workflows/update.yml) — no PR needed; it appears in
the snapshot within ~24h.

**Channel B · Curated list:** want it in the categorized README above? Open a PR
adding it to the right section (one-line description + star snapshot). The PR is
**auto-reviewed by rules** via [review-pr.yml](.github/workflows/review-pr.yml):

- ✅ Only `README.md` may be changed.
- ✅ Every added repo must exist and be public.
- ✅ Must be clearly DSH-related: carry the `dsh-plugin` topic, or mention
  DeepSeek Harness / DSH / Cordis / 外挂 / 插件 in name or description.
- ✅ No duplicates of existing entries.
- ⚠️ `dsh plugin add <pkg>` install commands must be well formed.

All checks pass → auto-labeled `auto-approved` and **auto-merged**. Otherwise
`changes-requested` with reasons; push a fix to re-run. A maintainer can still
override at any time.

Full rules: [CONTRIBUTING.md](CONTRIBUTING.md).

## License

The list content is released under [CC0 1.0](LICENSE). Individual plugins keep
their own licenses (mostly MIT, some CC BY-NC-SA for skins).
