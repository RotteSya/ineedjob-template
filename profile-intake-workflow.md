# Profile Intake Workflow（プロフィール初期構築 — STAR聞き取り）

Last updated: <YYYY-MM-DD>

## これは何か / これは何でないか

利用者本人から経歴を聞き取り、空の `candidate-profile.md`（と `evidence-ledger.md` / `career-criteria.md` / `PR.md` の種）を埋めるための標準手順。

- これは**書く側（write path）**。`company-interview-workflow.md` と `application-docs-workflow.md` は、ここで作った正本を**使う側（read path）**。
- **AIが主導して質問し、AIが正本ファイルに書き込む。** ユーザーに空欄テンプレを丸投げしない。
- 一度しっかり作れば、あとは企業別準備のたびに使い回す。新しい事実が出たら都度ここに追記する。

## 原則（5つ）

1. **事実をつくらない。** 本人が言っていないことは書かない。曖昧な所は `[仮説]` / `[情報不足]` と明記し、後で確認する。
2. **盛らない。** 各経験について「どこまで正直に言えるか」の境界を本人と一緒に決め、`candidate-profile.md` の **Packaging Warnings** に登録する。誇張は面接の深掘り一発で崩れる。
3. **1ラウンド2〜3問。** 選択式を基本にして答えやすくする（白紙より選ぶ方が出てくる）。ただしストーリーは自由回答で引き出す。
4. **会話は本人の母語**（中国語など、本人が楽な言語）。**成果物（profile 等）は日本語**で書く。
5. **数字は測定方法とセット。** 数字が出たら必ず「期間・母数・測定方法・本人の担当範囲」を確認し、`evidence-ledger.md` に Status つきで登録する。

## 進め方（ラウンド構成）

### Round 0: 基本属性（選択式中心・速い）

志望時期/枠・希望勤務地・志望職種・在留資格・語学/資格・学歴を確認。
→ 書き込み先: `candidate-profile.md` の Job Search Conditions / Education / Language and Certificates。

### Round 1: 経歴の棚卸し（広く浅く）

職歴・主要プロジェクト・個人制作・課外活動（学生団体・コミュニティ運営・アルバイト等）を時系列で**列挙だけ**する（各1〜2行）。深掘りはまだしない。
→ 書き込み先: Work Experience / Major Projects / Personal Projects の**見出しと1行概要**を先に作る。

### Round 2: Core Positioning と差別化トークン

Round 1 の一覧を見て、**AIが「あなたの強みの掛け算」を2〜3案 仮提案** → 本人が選ぶ/直す。「誰にでも言える」案は捨て、本人にしか言えない組み合わせに寄せる。
→ 書き込み先: Core Positioning ＋ 差別化トークン3〜4個（QA Gate D2 が参照する正本）。

### Round 3: STAR深掘り（1エピソードずつ・ここが本体）

コンピテンシー別に、本人の具体例を1つずつ STAR で掘る。1回1エピソード。

掘る順（各1本は欲しい）:
1. リーダーシップ / チームの意見対立を整理した経験
2. 失敗・頓挫から学んだ経験
3. 報連相 / トラブルを未然に防いだ経験
4. 主体性 / 自分でやり方を変えた・課題を解決した経験
5. ストレス耐性 / 批判やプレッシャーに対処した経験
6. 素直さ / フィードバックを受けて改善した経験

各エピソードで掘る順番（コンピテンシーチェーン。`knowledge/japanese-interview-playbook.md` §1.3）:
> 状況は? → あなたの役割は? → **なぜ**その方法を選んだ? → 他の選択肢は? → 周囲の反応は? → 結果は数字で? → 何を学んだ? → **今ならどうする?**

各エピソードで必ず:
- 数字が出たら → 測定方法・担当範囲を確認 → `evidence-ledger.md` に登録。
- 「これ以上は盛れない」境界を確認 → `candidate-profile.md` Packaging Warnings に登録。
→ 書き込み先: Story Bank に1見出しずつ（STAR ＋ Interview use ＋ Safe phrasing）。

### Round 4: リスク防御

弱点になりうる点（キャリアの空白・新卒枠と職歴のギャップ・過去の失敗・在留資格/ビザ・専門の深掘り・数字の測定）を洗い出し、**守り方を一緒に作る**（隠さず、前向きに、短く）。
→ 書き込み先: Interview Risk Defense テーブル。

### Round 5: 就活軸とPRの種

Story Bank と Core Positioning から、AIが母軸2〜3個と主PR1本を**仮組み** → 本人確認・微調整。各軸は「満たされる状態」と「なぜ自分が求めるか」まで（`axis-motivation-workflow.md` の方法論）。
→ 書き込み先: `career-criteria.md`（母軸）/ `PR.md`（主PR）。

## discovery形式（質問の作り方）

- **1ラウンド2〜3問**。各問に選択肢を2〜4個用意して選ばせる。必ず「その他（自由記述）」を残す。
- ストーリーは選択式にできない。AIが**呼び水の例**を1〜2個出し、本人が自分の言葉で語る → AIが STAR に再構成して**本人に確認を取ってから**書く。
- 本人にしか分からない事実だけを聞く。調べれば分かること（業界知識・面接マナー等）は聞かない。

## 書き込み先マップ

| 聞いたこと | 書き込み先ファイル / セクション |
| --- | --- |
| 志望条件・学歴・語学 | `candidate-profile.md`: Job Search Conditions / Education / Language |
| 強みの掛け算・固有要素 | `candidate-profile.md`: Core Positioning / 差別化トークン |
| 職歴・プロジェクト | `candidate-profile.md`: Work Experience / Major Projects / Personal Projects |
| STARエピソード | `candidate-profile.md`: Story Bank |
| 数字・受賞 | `evidence-ledger.md`: Numeric Claims / Awards（Status つき） |
| 盛れない境界 | `candidate-profile.md`: Packaging Warnings |
| 弱点と守り方 | `candidate-profile.md`: Interview Risk Defense |
| 就活軸 | `career-criteria.md`: Mother Criteria |
| 自己PRの核 | `PR.md`: Core PR Positioning / PR Option |

## Definition of Done（intake 完了の定義）

以下が揃えば `company-interview-workflow.md` を回せる:

1. `candidate-profile.md`: Core Positioning ＋ 差別化トークン / Job Search Conditions / Education / 最低2件の Work Experience または Major Projects / **Story Bank 最低4本**（うちチーム系・失敗系を各1本）/ Interview Risk Defense / Packaging Warnings が埋まっている。
2. `evidence-ledger.md`: 使いそうな数字が最低数件、Status つきで登録されている。
3. `career-criteria.md`: 母軸2〜3個。`PR.md`: 主PR1本。
4. 各ファイルの `Last updated` を更新済み。

埋めきれない欄は `[仮説]` / `[情報不足]` を残してよい（後の面接準備時の逆質問TODO・discovery で埋める）。

## New Thread Starter Prompt（そのまま使える起動文）

```text
私のプロフィールをゼロから作りたいです。profile-intake-workflow.md に従って、
選択式2〜3問のラウンド形式で私の経歴を聞き取り、STARで主要エピソードを掘り、
その結果を candidate-profile.md / evidence-ledger.md / career-criteria.md / PR.md に書き込んでください。
会話は中国語（または私が指定する言語）で、成果物は日本語でお願いします。
事実は私が言ったことだけ書き、盛れない境界は一緒に決めて Packaging Warnings に登録してください。
まず Round 0（基本属性）から始めてください。
```
