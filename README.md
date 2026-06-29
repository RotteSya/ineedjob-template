# ineedjob-template

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh.md)

<p align="center">
  <em>Japanese new-grad interviews are won on 人柄・熱意・可能性 — character, drive, potential — not buzzwords.</em><br>
  <strong>This is the AI coach that turns your real stories into native-level, deep-dive-proof interview scripts —</strong><br>
  <strong>and refuses to let you exaggerate.</strong>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT License"></a>
  <a href="https://claude.com/claude-code"><img src="https://img.shields.io/badge/Built_for-Claude_Code-000?style=flat&logo=anthropic&logoColor=white" alt="Built for Claude Code"></a>
  <img src="https://img.shields.io/badge/market-Japan_新卒・留学生-brightgreen" alt="Market: Japan new-grad / international students">
  <img src="https://img.shields.io/badge/docs-日本語-d73a49" alt="Docs in Japanese">
</p>

## What Is This

`ineedjob-template` turns an AI coding CLI (Claude Code or any agent that auto-loads `AGENTS.md`) into a personal interview-prep coach for the **Japanese job market**, on the new-grad / international-student track. Instead of the generic answers you can copy off any job-hunting site, you get a pipeline that:

- **Builds your profile** from *your own* stories through a STAR-based intake — the "write path" most prep tools skip
- **Researches each company** (official site / IR, plus 就活会議・ONE CAREER experience reports and past questions)
- **Drafts interview scripts** in natural spoken Japanese — conclusion-first, with hooks and a `▼keyword` line per answer so you never recite from memory
- **Enforces a delivery standard** — length budget, a 敬語 NG list, and a 12-point naturalness lint
- **Runs a pre-ship QA gate** — facts, structure, native Japanese, and a company-swap test

> **This is NOT a template-spitter, and NOT about inflating your story.** Japanese new-grad hiring rewards 控えめ＋具体 — modest and concrete. The whole system is built to keep you honest: every claim traces back to your profile, every number to an evidence ledger, and explicit *packaging boundaries* stop you from overstating. Exaggeration collapses on the first follow-up question — so the engine is designed not to let you go there.

> **Fill your profile first.** The engine is only as good as what you feed it. Run the intake once and give it your real experiences, numbers, and limits — like onboarding a coach who has to learn your story before they can be useful. The first session is you teaching it about you; after that, it's fast.

The **engine is reusable and contains no personal data** — your facts live in separate, swappable files. All working docs and the interview scripts it produces are in **Japanese**; this README is in English so anyone can see how the system works.

## Features

| Feature | Description |
| --- | --- |
| **STAR intake (write path)** | AI-led discovery (`workflow/profile-intake-workflow.md`) that builds your profile from your own stories — the half most prep systems never automate |
| **Per-company prep** | A 13-step workflow: research → requirement extraction → fit map → script → QA, output as two files |
| **Story Bank** | Reusable STAR episodes; the engine picks ~3 per company by what each interview rewards |
| **Delivery standard** | Spoken-Japanese rules: length table, 敬語 NG list, 12-point naturalness lint, `▼keyword` lines (memorize keywords, not paragraphs) |
| **QA gate** | Pre-ship Gates A–D + a voice layer, **measured** not self-reported. Includes a *company-swap test* and an independent-verifier sub-agent for important interviews |
| **Pronunciation layer** | Pitch-accent / mother-tongue-interference guide (Chinese-L1 by default, adaptable) + a per-company 読み (reading) risk list |
| **Two-file contract** | A research/audit file you never read aloud, and a clean Q&A script you actually read on the day |
| **Engine ⁄ data split** | The de-personalized engine references your profile as *slots*; swap the data, keep the quality |

## Quick Start

1. **Get the template**

   ```bash
   git clone https://github.com/RotteSya/ineedjob-template.git
   cd ineedjob-template
   ```

2. **Open your AI CLI in this directory.** It auto-loads `CLAUDE.md` / `AGENTS.md`, so it already knows the rules.

   ```bash
   claude   # or any agent CLI that reads AGENTS.md
   ```

3. **Build your profile (first time only).** Just chat — nothing to edit by hand:

   > 「私のプロフィールをゼロから作りたいです。`workflow/profile-intake-workflow.md` に従ってください。」
   > *(“I want to build my profile from scratch — follow the intake workflow.”)*

   The AI asks multiple-choice + STAR questions and fills `profile/*` for you.

4. **Prep a company.** Paste a company name + job description and follow `workflow/company-interview-workflow.md`. You get two files in `docs/<company>/`: a research/audit report and a ready-to-read interview script.

> **The system is meant to be adapted by the AI itself.** Different mother tongue, target roles, or region — just ask it to change them. It reads the same files it edits, so it knows exactly what to touch.

## How It Works

```
(first time)   You ──► STAR intake ──► profile/  (facts · stories · evidence · boundaries)
                                          │
(each company)                            ▼
  Company name / JD ──► Research ──► Fit Map ──► Draft script
    (official IR,         (Must/Want/   (your        (spoken JP,
     experience reports)   Hidden/Risk)  evidence)    conclusion-first, hooks)
                                          │
                                          ▼
                          Delivery Standard  +  QA Gate
                        (length · 敬語 · naturalness ·
                         company-swap test · voice layer)
                                          │
                         ┌────────────────┴────────────────┐
                         ▼                                 ▼
               research / audit file               interview script
          <company>_interview_<date>.md    <company>_interview_integrated_<date>.md
             (sources, scoring, trees           (answers · ▼keyword lines ·
              — you never read aloud)             nested deep-dive Q&A)
```

## Project Structure

```
ineedjob-template/
├── CLAUDE.md  AGENTS.md     # "Constitution": role, principles, Definition of Done.
│                            #   Auto-loaded; kept byte-identical by a pre-commit hook.
├── README.md / .ja / .zh    # English / 日本語 / 简体中文
├── profile/                 # YOUR data — blank templates to fill
│   ├── candidate-profile.md   #   single source of truth: facts, Story Bank, boundaries
│   ├── career-criteria.md     #   your job-search axes
│   ├── PR.md                  #   self-PR master
│   ├── evidence-ledger.md     #   numbers + how you'd defend each one
│   └── 職務経歴書.md           #   résumé master
├── workflow/                # the ENGINE — step-by-step procedures
│   ├── profile-intake-workflow.md      #   STAR intake (write path)
│   ├── company-interview-workflow.md   #   research → script (13 steps)
│   ├── application-docs-workflow.md     #   履歴書 / 職務経歴書 / 送付状
│   ├── axis-motivation-workflow.md      #   motivation 4-layer method
│   └── feedback-template.md             #   post-interview PDCA
├── standards/               # enforced quality bars
│   ├── japanese-delivery-standard.md
│   └── interview-qa-gate.md
├── knowledge/               # reference knowledge (read, don't copy)
│   ├── japanese-interview-playbook.md
│   └── native-delivery-pronunciation.md
└── docs/
    ├── _templates/          # blank base + script templates
    └── <company>/           # your generated prep, per company
```

## Quality, Not Volume

A script is never called "done" until it passes both gates — measured, not eyeballed:

- **`standards/japanese-delivery-standard.md`** — length actually counted, zero 敬語 NG, the 12-point naturalness lint clean, a `▼keyword` line on every answer.
- **`standards/interview-qa-gate.md`** — Gates A–D plus a voice layer. Its signature check is the **company-swap test**: replace the company name with a competitor's and re-read; if the answer still works, it's too generic and gets rewritten.

For important interviews (大手 / final rounds), the gate is run by an **independent verifier sub-agent** whose job is to *find* failures, not to rubber-stamp.

## Who It's For

Built for the Japanese job market, new-grad / international-student track. The pronunciation layer defaults to Chinese-L1 speakers but adapts to any mother tongue (see §2 of that file). Your timing, region, nationality, and background are not hard-coded — they live in your profile.

## Disclaimer

This is a **local, open-source prompt/workflow template — not a hosted service, and not professional career advice.**

1. **Your data stays yours.** You fill the `profile/*` files locally; they go only to whichever AI provider you run. This repo collects nothing.
2. **You have the final call.** The AI drafts and checks; *you* decide what to actually say, and review every answer for accuracy and honesty before an interview.
3. **No guarantees.** It is a preparation aid, not a promise of results. Never say anything in an interview you can't back up — the entire system is designed around that principle (控えめ＋具体).

## License

[MIT](LICENSE) © 2026 RotteSya. Built by one job-seeker for their own Japanese job hunt, then de-personalized into a template. The engine carries no personal data — fork it and fill in your own.
