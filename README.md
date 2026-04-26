# Ink Card

**毎日1つ、思考を揺さぶる問いが届く。配信者のためのインスピレーションカード。**

> A daily card that stirs your thinking. Inspired by Oblique Strategies.

---

## これは何？

Ink Cardは、配信のマンネリを打破したい配信者・創作に行き詰まったクリエイターのための、日々のインスピレーションツールです。

オラクルカードでも、スピリチュアルでもない。  
「答え」を与えるのではなく、**思考の着火剤として機能する問い**を毎日1つ届けます。

3,700本以上のストックから、今日の問いが1つ選ばれます。  
カードをめくって、配信のヒントにしてください。

---

## 機能

- **今日の問い** — GitHub Actionsが毎日1問を自動生成してカードに表示
- **ランダム引き** — 3,700本以上のアーカイブからランダムに引ける
- **8テーマ対応** — 羊皮紙の間・真夜中の書斎・深夜ネイビー・深紅の刻・琥珀の燈火・森の奥処・黄金の問い・白銀の静寂
- **カードフリップ** — タップでカードをめくる演出
- **画像保存** — カード裏面をPNG画像としてダウンロード
- **Xへ投稿** — 問いの内容をそのままXに投稿できる

---

## 使い方

**→ [Ink Cardを開く](https://inkinc-official.github.io/ink-card/)**

1. カードをタップして問いを開く
2. 好みのテーマに切り替える
3. 「画像を保存する」でカード画像をダウンロード
4. 「Xに投稿する」で配信前にシェア

---

## 仕組み

```
GitHub Actions（毎日 00:05 JST）
　↓
Gemini API で問いを1問生成
　↓
docs/today.json に書き込み → commit & push
　↓
GitHub Pages で自動反映
```

3,700本以上のアーカイブ（`docs/questions.json`）から12問をサンプリングし、それを参照して毎回異なる問いを生成します。生成された問いはアーカイブにも追記されます。

---

## ファイル構成

```
ink-card/
├── .github/workflows/
│   └── daily.yml              # 毎日自動生成のワークフロー
├── docs/
│   ├── index.html             # カードUI本体
│   ├── today.json             # 今日の問い（自動更新）
│   └── questions.json         # 問いのアーカイブ（3,700本以上）
├── scripts/
│   ├── generate_daily_question.mjs  # 日次生成スクリプト
│   ├── extract_from_cards.mjs       # .cardsファイルからの抽出ツール
│   ├── extract_from_tsv.mjs         # TSVからの抽出ツール
│   └── extract_from_db.py           # SQLiteDBからの抽出ツール
└── assets/
    ├── ink-card-logo.png
    └── ink-inc-logo.png
```

---

## セットアップ（自分でホストする場合）

### 1. リポジトリをfork

### 2. GitHub Pagesを設定
Settings → Pages → Source を `main` / `docs` に設定

### 3. Gemini APIキーを登録
Settings → Secrets and variables → Actions で `GEMINI_API_KEY` を登録

### 4. GitHub Actionsを有効化
Actions タブ → `daily-question` を手動実行して動作確認

---

## 問いの生成について

Gemini APIを使い、3,700本以上のアーカイブからランダムにサンプリングした問いを参照して毎日1問を生成します。

生成の条件：
- 1文（長くても2文）
- 固有名詞・企業名・SNS名・時事ネタを避ける
- 番号・日付・ハッシュタグ・絵文字は禁止
- アーカイブとの重複は自動でチェック

---

## Ink Inc. について

Ink Card は **Ink Inc.** が制作・公開しているツールです。

Ink Inc. は IRIAM を中心に活動するAIライバー事務所です。  
「AIによる創造、人によるケア」をコンセプトに、配信者を支援するツール群（Ink Tools）を無償公開しています。

- 公式サイト：[https://inkinc-hp.vercel.app/](https://inkinc-hp.vercel.app/)
- X：[@InkInc_Info](https://x.com/InkInc_Info)
- YouTube：[@InkInc.official](https://www.youtube.com/@InkInc.official)

---

## ライセンス

© 2025-2026 黒井葉跡 / Ink Inc.

[Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/legalcode.ja)

- ✅ 個人・非商用目的での使用・改変・再配布
- ❌ 商用利用禁止
- ❌ Ink Inc. クレジットの削除禁止

---

*AI Creation, Human Care. The Future Drawn Together.*  
*[Ink Inc.](https://inkinc-hp.vercel.app/)*
