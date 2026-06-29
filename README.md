# ineedjob-template

> **An AI-assisted, quality-gated template for job-hunting interview prep in Japan** (new-grad / international students). Fill in your profile once; an AI then researches each company and drafts native-level Japanese interview scripts, held to an enforced delivery standard and a pre-ship QA gate. The engine is reusable; your personal facts stay separate. *(Working docs are in Japanese.)*

日本での就職活動（**留学生・新卒**中心）のための面接準備テンプレート。企業別の調査レポートと面接稿を、AIが毎回**同じ高い品質基準**で作るための仕組みを、「エンジン（手順・標準・知識）」と「あなたのデータ（事実・素材）」に分けて管理する。

> このリポジトリは特定個人の中身を含まない**ひな形**。あなたの事実を入れて使う。データファイル（`profile/candidate-profile.md` ほか）は空の状態で入っている。

## はじめに（3ステップ）

1. **プロフィールを作る（初回のみ）** — `profile/candidate-profile.md` などは空。`workflow/profile-intake-workflow.md` に従い、AIに選択式＋STARで経歴を聞き取ってもらって正本を埋める。
   - 起動文: 「私のプロフィールをゼロから作りたいです。`workflow/profile-intake-workflow.md` に従ってください。」
2. **企業別に面接準備する（最頻）** — `workflow/company-interview-workflow.md` 末尾の起動文を使う。AIが会社調査 → あなたの経験との接続 → 面接稿まで作る。成果物は `docs/<会社>/` に2ファイル。
3. **面接後にふりかえる** — `workflow/feedback-template.md` で実問・反応を記録し、正本と面接稿を更新（PDCA）。

## 構造（エンジン vs あなたのデータ）

役割を混ぜず、各概念の正本は1か所だけに置く（他はコピーせずリンクで指す）。

- **魂／憲法** `CLAUDE.md` ≡ `AGENTS.md` — AIが誰で、どう動き、何を「完成」と呼ぶか。毎セッション最初に読む。2ファイルは常に同一で、`.githooks/pre-commit` が不一致のコミットを拒否する。
- **手順（エンジン）** `*-workflow.md` — プロフィール構築（intake）/ 企業別面接準備 / 応募書類 / 軸・志望動機整理 の step-by-step。
- **標準・知識（エンジン）** `standards/` `knowledge/` — 話し言葉の強制基準・出荷前検査・面接知識・声音層。
- **あなたのデータ（各自で埋める）** `profile/candidate-profile.md`（唯一の正本）/ `profile/career-criteria.md` / `profile/PR.md` / `profile/職務経歴書.md` / `profile/evidence-ledger.md`。
- **成果物** `docs/<会社>/` — 企業別の調査レポート＋面接稿。雛形は `docs/_templates/`。

エンジンは、あなたのデータを**スロットとして参照**する（例: 「`profile/candidate-profile.md` の差別化トークン」「Packaging Warnings」「Story Bank」）。だから中身を入れ替えれば、誰のデータでも同じ品質で動く。

## 使い方

| タスク | 起動方法 | 主に従うワークフロー | 受け取る成果物 |
| --- | --- | --- | --- |
| プロフィール構築（初回） | 「プロフィールをゼロから作りたい」と伝える | `workflow/profile-intake-workflow.md` | 埋まった `profile/candidate-profile.md` ほか正本 |
| 企業別の面接準備（最頻） | `workflow/company-interview-workflow.md` 末尾の起動文を貼り、企業名・職種・面接段階・形式を埋める | `workflow/company-interview-workflow.md`（Step 1〜13） | `docs/<会社>/` に調査レポート＋面接稿 |
| 応募書類 | 「履歴書/職務経歴書を作りたい」と伝える | `workflow/application-docs-workflow.md` | `docs/<会社>/` の履歴書・職務経歴書・送付状 |
| 軸・志望動機の整理 | 「軸を整理して」と伝える | `workflow/axis-motivation-workflow.md`（AI内部メソッド） | 調査レポート・面接稿に溶け込ませる |
| 面接後のふりかえり | 実際に聞かれた質問を伝える | `workflow/feedback-template.md` | フィードバック記録＋正本・面接稿の更新 |

面接準備で受け取る2ファイル:

1. **調査レポート** `docs/<会社>/<会社>_interview_<日付>.md` — 調査・分析・根拠の全記録（当日は読まない監査ログ）
2. **面接稿** `docs/<会社>/<会社>_interview_integrated_<日付>.md` — 当日読む純Q&A（回答 + ▼キーワード行 + 深掘りQ&A）

## 品質保証

面接稿は次を通すまで「完成」と呼ばない（完成の定義は `AGENTS.md` の Definition of Done が正本）:

- `standards/japanese-delivery-standard.md` — 話し言葉の強制基準（長さ・敬語・自然度Lint・キーワード設計）
- `standards/interview-qa-gate.md` — 出荷前検査（Gate A〜D ＋ 声音層。会社入れ替えテスト等を実測。重要面接は独立検証サブエージェント）
- `knowledge/japanese-interview-playbook.md` — 採点機構・段階戦略・当日プロトコル・最新トレンド
- `knowledge/native-delivery-pronunciation.md` — 声音層（発音・アクセント・イントネーション・発音リスクリスト手順）

## 対象と前提

- 主な想定: 日本での就職を目指す**留学生・新卒**。志望時期・地域・国籍などの属性は `profile/candidate-profile.md` を正本とする（このREADMEには書かない＝ドリフト防止）。
- 声音層（`knowledge/native-delivery-pronunciation.md`）は**中国語母語を既定**にしているが、§2 を自分の母語干渉に読み替えれば他の母語にも使える。
- 事実・面接リスク防御・包装境界の唯一の正本は `profile/candidate-profile.md`。
