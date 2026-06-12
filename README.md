# んーこ💩

> んこ　んこ　うんちゆ！

AIとも遊べる、うんちゆ回避チキンレースゲーム。

## Language / 言語

* 🇯🇵 [日本語](#日本語)
* 🇺🇸 [English](#english)

---

# 日本語

## 概要

「んーこ💩んこ　んこ　うんちゆ」は、3人で順番に「んこ」「んーこ」「んーーこ」「長んこ」などを出しながら、個人腹圧・部屋の空気・場うんち蓄積を管理して生き残るゲームです。
v29では、これまで混ざっていた「個人うんち」と「場うんち」を分離しています。個人うんちは本人の減点として抱えるもの、場うんちは部屋全体が爆発する敗北トリガーです。

複数のAIを対戦相手として遊べます。Gemini、ChatGPT、Claude、Grokなどに手番ログを貼り付けながら進行します。

HTML単体で動作します。ブラウザでhtmlを開けば遊べます。サーバーや外部ライブラリは不要です。

## 基本用語

**汚水** はゲーム全体のHPです。0%になるとゲーム終了です。v29では、基本的に場うんち爆発で固定ダメージを受けます。

**んーこ得点** はプラス得点です。長めの入力や危険な場面で行動を通すほど伸びます。名前はそのまま「んーこ得点」です。

**個人うんち** は本人の減点です。個人腹圧が限界を超えると発生し、本人に個人うんち減点が乗ります。同時に、その量が場うんち蓄積へ追加されます。個人うんちは汚水を直接削りません。

**場うんち** は通常ルールの敗北トリガーです。場うんち蓄積が限界を超えると発生し、引いた人が負け候補になります。場うんちは汚水に固定ダメージを与え、ターンを強制終了します。

**チキン減点** は、危険な場面で「んこ」だけで逃げ続けた時などに増える軽い減点です。生存はできますが、総合点は下がります。

## 基本ルール

3人プレイです。P1、P2、P3の名前は画面内で変更できます。標準では `Gemini`、`Player2`、`Player3` になっています。

基本入力は「んーこ」ボタンの長押しです。押す長さによって「んこ」「んーこ」「んーーこ」「長んこ」になります。毎ターン、裏で4種類の入力に「出る出る」「ひっこみ」「普通」「普通」が割り当てられます。どの入力がどれなのかは見えません。

個人腹圧は自分の入力で上がったり下がったりします。部屋の空気は全員の入力や一部イベントで重くなります。判定は、個人腹圧に部屋の空気補正をかけた危険度が限界を超えたら「個人うんちゆ！💩」です。

個人うんちが出ても、その時点で即負けではありません。本人に個人うんち減点がつき、場うんち蓄積にも同量が溜まります。場うんち蓄積が100%を超えると「場うんちゆ！！💩🌫️」が発生し、通常ルールではそれを引いた人が負け候補になります。

## 特殊行動

**お茶ゆ☕** は1人2回まで使えます。「んこ」と一緒に使えません。入力義務を免除しますが、腹圧が少し増えます。連続使用はできません。

**すかしっぺ💨** は1人1回まで使えます。「んこ」と一緒に使えません。本人の腹圧を下げますが、部屋の空気を大きく重くします。

**んちジョーカー💣** は1人1回まで使えます。自分のターン中、最低1回入力したあとに裏で仕込めます。次の人の「んこ」「んーこ」「んーーこ」「長んこ」のどれかを裏ジョーカー化します。仕込み宣言はAIログに出ません。

ジョーカーが命中すると、対象の腹圧と部屋の空気が上がります。不発すると、仕掛け人の腹圧と部屋の空気が上がります。v29では、仕掛け人は非公開のまま、命中・不発の結果だけが「直近小事件」としてAI貼り付けログに出ます。

## んこ逃げ対策

部屋の空気が「かなりやばい」時に、同じ人が「んこ」だけで逃げると、弱気圧がたまります。2回目は+3、3回目は+7、4回目以降は+12の腹圧ペナルティです。

全員が1周「んこ」だけで回した場合、部屋が腐ります。部屋の空気が上がり、全員腹圧が少し増え、場うんち蓄積も増えます。

v29では、「んこ逃げ」はまだ生存手段ですが、ずっと続けるとチキン減点や場うんち蓄積によって詰みます。

## 勝敗とスコア

通常ルールでは、まず場うんちを引いた人が負け候補です。場うんち犯が複数いる場合は、場うんち回数が多い人が下になります。

場うんちを引いていない人同士、または場うんち回数が同じ人同士は、総合点で比べます。総合点は、おおむね `んーこ得点 − 個人うんち減点 − チキン減点 − 場うんちペナルティ` です。

個人うんちは順位を即固定するものではなく、減点として効きます。個人うんちを抱えても、んーこ得点を稼げばある程度は取り返せます。ただし、場うんちを引くと通常ルールで大きく不利になります。

## AIと遊ぶ時の貼り方

初回だけ「初手案内コピー」または「ルール説明コピー」をAIに貼ってください。ルール全文は毎ターン貼らなくて大丈夫です。

2ターン目以降は「次の手を聞く（軽量）」を使うのがおすすめです。軽量コピーには、現在状態、汚水、場うんち蓄積、直近大事件、直近小事件、スコア、直近発話だけが入ります。これでチャットログが肥大化しにくくなります。

AIの返答を貼る欄に、AIの回答を貼って「AI返答を保存してハイライト」を押すと、入力候補を拾ってハイライトします。v29では `T25/Gemini:` や `T23/じぴぴ:` のような名前付きターンログも最新ターンとして拾いやすくしています。

「AI会話ログコピー（軽量）」は直近のAI返答だけを短くまとめます。全ログ保存や検証をしたい時以外は、長い公開ログを毎回AIに貼らないでください。

## おすすめ運用

ゲーム開始時に、各AIごとのチャットへ初回ルールを貼ります。その後は、手番ごとに軽量コピーだけを貼ります。AIの返答から行動を読み取り、HTML側で実行します。事件が起きた時だけ「うんちゆ速報」や「場うんち速報」を貼ると、AI側も状況を理解しやすいです。

全ログを毎回貼ると、AIが古いターンの「んこ」を拾ったり、チャットが重くなったりします。通常プレイでは軽量コピー方式を使ってください。

## v29の主な変更点

v29では、個人うんちと場うんちを分離しました。個人うんちは本人の減点として扱い、場うんち蓄積にも加算されます。場うんちは汚水固定ダメージと通常敗北トリガーとして扱います。

ジョーカー命中・不発は、仕掛け人を伏せたまま直近小事件として公開されるようにしました。

AI貼り付けログを軽量化しました。毎ターンルール全文を貼らなくても遊べるように、現在盤面中心のコピーを追加しています。

## ファイル

メインファイルは `nko_belly_air_joker_v31.html` です。このREADMEは `README_nko_v29.md` です。


---

# English

## Overview

# NKO💩

> NKO, NKO, UNCHIYU!

An AI-compatible party game about avoiding UNCHIYU.

## Overview

**NKO💩** is a three-player chicken-race party game where players take turns choosing actions such as **NKO**, **N-KO**, **NN-KO**, and **Long NKO** while managing personal pressure, room atmosphere, and shared UNCHI accumulation.

Players can compete against humans or AI opponents such as ChatGPT, Gemini, Claude, and Grok by copying game logs into AI chats and using their responses as actions.

The game runs entirely in the browser. No installation, server, or external libraries are required.

## Core Concepts

### Dirty Water

The shared HP of the game.

If Dirty Water reaches 0%, the game ends.

Most damage comes from Shared UNCHI explosions.

### N-KO Score

Your positive score.

Longer and riskier actions generally earn more points.

### Personal UNCHI

An individual penalty.

If your personal pressure exceeds its limit, you trigger a Personal UNCHI event and receive penalty points.

The same amount is also added to the Shared UNCHI accumulation.

Personal UNCHI does not directly damage Dirty Water.

### Shared UNCHI

The primary defeat trigger.

When Shared UNCHI accumulation reaches its limit, a Shared UNCHI event occurs.

It damages Dirty Water and may determine the losing player.

### Chicken Penalty

A small penalty for repeatedly choosing overly safe actions.

Playing cautiously can keep you alive, but it reduces your final score.

## Basic Rules

The game is designed for three players.

Player names can be customized.

The primary action is performed by holding the NKO button.

Different hold lengths produce different actions:

* NKO
* N-KO
* NN-KO
* Long NKO

Each turn secretly assigns hidden outcomes to these actions.

Players never know which choice is currently safe or dangerous.

Personal pressure changes based on your actions.

Room atmosphere changes based on the actions of all players.

If the resulting danger exceeds the limit, a Personal UNCHI event occurs.

A Personal UNCHI event does not immediately eliminate a player.

Instead, it applies penalty points and increases Shared UNCHI accumulation.

When Shared UNCHI reaches 100%, a Shared UNCHI event is triggered.

## Special Actions

### Tea☕

Available twice per player.

Cannot be used together with NKO.

Skips the action requirement but slightly increases personal pressure.

### Silent Fart💨

Available once per player.

Cannot be used together with NKO.

Reduces personal pressure but significantly worsens the room atmosphere.

### UNCHI Joker💣

Available once per player.

After performing at least one action during your turn, you may secretly plant a Joker.

One of the next player's possible NKO actions becomes trapped.

If the trap succeeds, the target gains pressure and the room atmosphere worsens.

If it fails, the penalty affects the player who planted it.

The identity of the Joker user remains hidden.

## Anti-Stalling Rules

Repeatedly escaping with only NKO during dangerous situations builds a cowardice penalty.

If every player chooses only NKO for an entire round, the room atmosphere deteriorates, pressure rises, and Shared UNCHI accumulation increases.

Playing safely is possible, but relying on it for too long will eventually become a losing strategy.

## Winning and Scoring

Shared UNCHI events are the primary loss condition.

Among players with the same Shared UNCHI status, ranking is determined by score.

Final score is approximately:

N-KO Score − Personal UNCHI Penalty − Chicken Penalty − Shared UNCHI Penalty

Risk and survival must be balanced carefully.

## Playing With AI

At the start of the game, send the rules or setup prompt to each AI participant.

After that, use the lightweight turn summary instead of reposting the full rules every turn.

The recommended setup is one chat conversation per AI player.

This keeps context size small and prevents AIs from reacting to outdated turns.

## Recommended Setup

1. Open a separate chat for each AI participant.
2. Send the initial rules once.
3. Use lightweight turn summaries for future turns.
4. Paste AI responses back into the game.
5. Continue until somebody triggers UNCHIYU.

## Files

Japanese version:

`nko_belly_air_joker_v31_public.html`

English version:

`nko_belly_air_joker_v31_english.html`

Discord version:

`nko_belly_air_joker_v31_discord.html`

Repository homepage:

`index.html`

README:

`README.md`
