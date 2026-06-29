# ineedjob-template

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh.md)

<p align="center">
  <em>日本应届（新卒）面试，看的是 人柄・熱意・可能性（人品・热情・潜力），不是漂亮话。</em><br>
  <strong>这是一套 AI 教练：把你真实的经历，变成地道、经得起追问的日语面试稿——</strong><br>
  <strong>而且不让你夸大。</strong>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT License"></a>
  <a href="https://claude.com/claude-code"><img src="https://img.shields.io/badge/Built_for-Claude_Code-000?style=flat&logo=anthropic&logoColor=white" alt="Built for Claude Code"></a>
  <img src="https://img.shields.io/badge/market-Japan_新卒・留学生-brightgreen" alt="Market: Japan new-grad / international students">
  <img src="https://img.shields.io/badge/docs-日本語-d73a49" alt="Docs in Japanese">
</p>

## 这是什么

`ineedjob-template` 把一个 AI 编程 CLI（Claude Code，或任何会自动加载 `AGENTS.md` 的 agent）变成你专属的**日本就活**面试教练，面向新卒／留学生路线。它不给你那种就活网站上谁都能抄的通用答案，而是一条流水线：

- **建立你的档案**：通过 STAR 提问，从你*自己*的故事里建档——这条"写入路径"是大多数面试工具都跳过的一环
- **逐家公司调研**（官网／IR，加上 就活会議・ONE CAREER 的选考体验和历史问题）
- **起草面试稿**：自然的日语口语——结论先行、留钩子、每个回答配一行 `▼关键词`，让你不靠死记硬背
- **强制话术标准**：长度预算、敬語 NG 清单、12 项自然度 Lint
- **出货前 QA 闸门**：事实、结构、地道日语，外加"换公司测试"

> **这不是"模板吐出机"，也不是教你给经历注水。** 日本新卒录用看重的是 控えめ＋具体（克制＋具体）。整套系统的设计就是逼你诚实：每个主张都能追溯到你的档案，每个数字都过证据台账，明确的"包装边界"拦住你别吹过头。夸大会在面试官第一个追问下崩盘——所以引擎一开始就不让你往那走。

> **先把档案填好。** 引擎的好坏取决于你喂给它什么。先跑一遍 intake，把你真实的经历、数字、底线告诉它——就像带一个新教练入职，他得先了解你，才帮得上忙。第一次是你在教它认识你；之后就快了。

**引擎是可复用的，不含任何个人数据**——你的事实放在独立、可替换的文件里。所有工作文档和它产出的面试稿都是**日语**；这份 README 用英文／中文写，是为了让任何人都看懂它怎么运转。

## 功能

| 功能 | 说明 |
| --- | --- |
| **STAR 建档（写入路径）** | AI 主导的提问（`workflow/profile-intake-workflow.md`），从你自己的故事建档——大多数系统从不自动化的那一半 |
| **逐家公司准备** | 13 步流程：调研 → 要件抽取 → Fit Map → 面试稿 → QA，产出两个文件 |
| **故事库（Story Bank）** | 可复用的 STAR 故事；引擎按每场面试看重什么，挑约 3 个 |
| **话术标准** | 日语口语规则：长度表、敬語 NG 清单、12 项自然度 Lint、`▼关键词`行（记关键词而非整段） |
| **QA 闸门** | 出货前 Gate A–D ＋ 声音层，**实测**而非自报。含"换公司测试"，重要面试上独立校验子 agent |
| **发音层** | 音高重音／母语干扰矫正（默认中文母语，可改）＋ 逐家公司的"读法风险清单" |
| **两文件契约** | 一个你绝不照读的调研／审计文件，一个当天真正照读的纯 Q&A 面试稿 |
| **引擎 ⁄ 数据分离** | 去个人化的引擎把你的档案当"占位槽"引用；换数据，质量不变 |

## 快速开始

1. **获取模板**

   ```bash
   git clone https://github.com/RotteSya/ineedjob-template.git
   cd ineedjob-template
   ```

2. **在该目录打开你的 AI CLI**。它会自动加载 `CLAUDE.md` / `AGENTS.md`，规则它已经知道。

   ```bash
   claude   # 或任何读取 AGENTS.md 的 agent CLI
   ```

3. **建立档案（仅首次）**。只需对话，不用手动编辑：

   > 「私のプロフィールをゼロから作りたいです。`workflow/profile-intake-workflow.md` に従ってください。」
   > *（"我想从零建立我的档案——按 intake 流程来。"）*

   AI 会用选择题＋STAR 提问，帮你填好 `profile/*`。

4. **准备一家公司**。贴上公司名＋JD，按 `workflow/company-interview-workflow.md` 走。你会在 `docs/<公司>/` 拿到两个文件：调研／审计报告，和一份可直接照读的面试稿。

> **这套系统就是设计成让 AI 自己来改的。** 不同母语、目标职种、地区——直接让它改。它读的就是它要改的那些文件，知道该动哪里。

## 工作原理

```
(首次)     你 ──► STAR 建档 ──► profile/  (事实 · 故事 · 证据 · 边界)
                                    │
(每家公司)                          ▼
  公司名 / JD ──► 调研 ──► Fit Map ──► 起草面试稿
    (官网/IR,      (Must/Want/  (你的       (日语口语,
     选考体验)      Hidden/Risk) 证据)        结论先行 · 留钩子)
                                    │
                                    ▼
                      话术标准  +  QA 闸门
                   (长度 · 敬語 · 自然度 ·
                    换公司测试 · 声音层)
                                    │
                   ┌────────────────┴────────────────┐
                   ▼                                 ▼
            调研 / 审计文件                       面试稿
       <公司>_interview_<日期>.md    <公司>_interview_integrated_<日期>.md
          (出处 · 评分 · 追问树            (回答 · ▼关键词行 ·
           ——你绝不照读)                   嵌套的深掘 Q&A)
```

## 项目结构

```
ineedjob-template/
├── CLAUDE.md  AGENTS.md     # "宪法"：角色、原则、完成的定义（Definition of Done）。
│                            #   自动加载；由 pre-commit 钩子保证两文件逐字节一致。
├── README.md / .ja / .zh    # 英文 / 日文 / 中文
├── profile/                 # 你的数据 —— 待填的空白模板
│   ├── candidate-profile.md   #   唯一正本：事实、故事库、包装边界
│   ├── career-criteria.md     #   你的就活轴
│   ├── PR.md                  #   自我 PR 母库
│   ├── evidence-ledger.md     #   数字 + 每个数字怎么防御
│   └── 職務経歴書.md           #   履历母版
├── workflow/                # 引擎 —— 逐步流程
│   ├── profile-intake-workflow.md      #   STAR 建档（写入路径）
│   ├── company-interview-workflow.md   #   调研 → 面试稿（13 步）
│   ├── application-docs-workflow.md     #   履歴書 / 職務経歴書 / 送付状
│   ├── axis-motivation-workflow.md      #   志望动机 4 层方法
│   └── feedback-template.md             #   面试后 PDCA
├── standards/               # 强制质量基线
│   ├── japanese-delivery-standard.md
│   └── interview-qa-gate.md
├── knowledge/               # 参考知识（读，别复制）
│   ├── japanese-interview-playbook.md
│   └── native-delivery-pronunciation.md
└── docs/
    ├── _templates/          # 空白 base + 面试稿模板
    └── <公司>/              # 你逐家公司生成的成果
```

## 重质不重量

面试稿不过这两道闸门，就不叫"完成"——而且是实测，不是凭感觉：

- **`standards/japanese-delivery-standard.md`**——长度真的去数，敬語 NG 零容忍，12 项自然度 Lint 全过，每个回答都有 `▼关键词`行。
- **`standards/interview-qa-gate.md`**——Gate A–D 加声音层。它的招牌检查是**换公司测试**：把公司名换成竞品再读一遍；如果照样成立，说明太通用，打回重写。

重要面试（大手／最终轮），闸门由**独立校验子 agent**来跑，它的任务是*找出*问题，不是盖章放行。

## 适合谁

为日本就业市场打造，新卒／留学生路线。发音层默认中文母语者，但可改适配任何母语（见该文件 §2）。你的时间线、地区、国籍、背景都不写死——它们存在你的档案里。

## 免责声明

这是一套**本地、开源的提示词／工作流模板——不是托管服务，也不是专业职业建议。**

1. **你的数据归你。** 你在本地填 `profile/*`，它们只发给你选用的 AI 提供商。本仓库不收集任何东西。
2. **最终拍板的是你。** AI 起草并自检；说什么由*你*决定，面试前逐条核对准确与诚实。
3. **不作保证。** 它是准备工具，不是结果承诺。面试里别说你撑不住的话——整套系统就是围着这条原则（控えめ＋具体）设计的。

## 许可证

[MIT](LICENSE) © 2026 RotteSya。由一名求职者为自己的日本就活而做，之后去个人化成模板。引擎不含个人数据——fork 它，填上你自己的。
