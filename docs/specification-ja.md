# 📘 **AI BasePress – 公式仕様書（v1.0・日本語版）**

**ステータス:** Stable (v1.0)
**対象:** 開発者・AI活用者・WordPress制作者
**ライセンス:** MIT
**言語:** これは日本語版。英語版が公式であり、日本語版は補助文書。

---

# 1. 概要

**AI BasePress** は、以下の用途に最適化された **AI指向のミニマルWordPressスターターテーマ** です。

* 静的HTML/CSSサイトをWordPress化（移植）
* 軽量カスタムテーマをゼロから作成
* GPT / Claude / Gemini など **AIにテーマ構造を理解させて拡張・改修する**
* 既存の複雑な多機能テーマによるトラブルを回避
* プラグインとの干渉を最小限にしたサイト制作

**AI BasePress は “依存関係ゼロ・極限シンプル・AI最適化”** を思想としており、
必要最低限の構造だけを備えた「純粋なベーステーマ」です。

---

# 2. プロジェクト目標

## 2.1 コア目標

* **最小で分かりやすいWordPressテーマ構造**を提供
* 人間とAIの双方が**100%読み解ける構成**
* AIによるテーマ改修・派生テーマ作成を容易にする
* プラグインの動作を壊さないレイアウト
* WordPress移植案件の作業効率を最大化

## 2.2 非目標（やらないこと）

* デザインフレームワーク化
* 多機能テーマ化
* テーマビルダー化
* WooCommerce対応（別テーマとして提供予定）
* 複雑なJS・多数のアニメーション

---

# 3. 哲学：**「AI最適化されたミニマリズム」**

AI BasePressは以下の5原則に基づいて設計されている：

1. **単一責務**
   各ファイルは1つの役割のみ担当する。

2. **浅い構造**
   includeの連鎖や複雑な階層を避ける。

3. **明確な命名**
   クラス名・ファイル名は役割が一目で分かるように。

4. **予測可能なHTMLレイアウト**
   すべてのテンプレートで同じ構造を踏襲。

5. **非侵襲的なスタイル**
   `.entry-content` 内だけにデザインルールを適用し、プラグインを壊さない。

---

# 4. ディレクトリ構成（v1.0）

```
ai-basepress/
│
├── style.css                     ← テーマ情報 + 最小スタイル
├── functions.php                 ← テーマセットアップ / CSS/JS読み込み
│
├── header.php                    ← <head> + ヘッダー
├── footer.php                    ← フッター
├── sidebar.php                   ← サイドバー（任意）
│
├── index.php                     ← メインループ（フォールバック）
├── page.php                      ← 固定ページ
├── single.php                    ← 投稿ページ
├── 404.php                       ← 404ページ
│
├── /assets/
│    ├── /css/
│    │     └── base.css           ← タイポグラフィ・基本デザイン
│    └── /js/
│          └── main.js            ← 必要最小限のJS
│
└── /templates/                   ← 将来用のパーツ（v1.0では最小限）
```

---

# 5. テーマセットアップ（functions.php）

AI BasePressはWordPressの**必要最低限のサポートのみ**を宣言する。

* `title-tag`
* `post-thumbnails`
* `html5` (gallery, caption, forms, comment-list)
* メニュー1つ：`primary`
* ウィジェット1つ：`sidebar-1`

読み込むアセット：

* `style.css`
* `assets/css/base.css`
* `main.js`（必要に応じて）

外部ライブラリ・依存プラグインはゼロ。

---

# 6. HTMLレイアウト構造

すべてのテンプレートは共通構造を持つ：

```html
<body class="site-body">
  <div class="site-wrapper">

    <header class="site-header">
      <!-- ロゴ/ナビゲーション -->
    </header>

    <div class="site-main-wrapper">
      <main class="site-main">
        <!-- 各ページのメインコンテンツ -->
      </main>

      <aside class="site-sidebar" role="complementary">
        <?php get_sidebar(); ?>
      </aside>
    </div>

    <footer class="site-footer">
      <!-- フッター -->
    </footer>

  </div>
</body>
```

### ポイント：

* `.site-main` が必ずメイン領域
* `.entry-content` 内にWordPressとプラグインの出力を集約
* 不必要なdiv・ラッパーは設置しない
* レイアウトは“読む側とAI側”の両方に最適化

---

# 7. テンプレート要件

## 7.1 page.php / single.php

```html
<article id="post-<?php the_ID(); ?>" <?php post_class('entry'); ?>>
  <header class="entry-header">
    <h1 class="entry-title"><?php the_title(); ?></h1>
  </header>

  <div class="entry-content">
    <?php the_content(); ?>
  </div>
</article>
```

### 意図：

* `.entry-content` が **プラグインの安全地帯**
* Gutenbergブロック、ショートコード、フォームなどすべてがここに入る
* テーマは“最低限の器”だけ提供し、干渉しない

---

# 8. CSSガイドライン

## 8.1 基本思想

* `style.css` は最小限（テーマ情報中心）
* 実質的なスタイルは `base.css` に集約
* プラグインのデザインを壊さない
* デザインは `.entry-content` 内の要素に限定して適用

例：

```css
.entry-content h2 { ... }
.entry-content blockquote { ... }
.entry-content table { ... }
.entry-content code { ... }
```

## 8.2 BEM風命名（AI向け）

* レイアウト：`.site-header`, `.site-main`
* コンテンツ：`.entry`, `.entry__title`
* 汎用：`.section`, `.section--narrow`

AIに「`.section--inverted` の背景を黒にして」などの指示が容易。

---

# 9. JavaScriptガイドライン

* JSは必須ではない（テーマ自体はJSなしで動く）
* `main.js` は空、または最小機能（例えばモバイルメニュートグル）
* jQuery・React・Vue 等のフレームワークは使わない

---

# 10. プラグインに関する方針（重要仕様）

AI BasePress v1.0 は：

### ❌ 特定プラグインへの依存なし

### ❌ プラグイン用CSSなし

### ❌ プラグイン用JSなし

### ❌ WooCommerce非対応（別版で提供）

### ✔ `.entry-content` にプラグイン出力を集約

### ✔ プラグインはそのまま表示可能

### ✔ 追加対応は “Addonパック” として別提供

### ✔ WooCommerce版は将来の派生テーマ

---

# 11. AI最適化要件

AI BasePressの価値の中心。

AIに完全理解させるための仕様：

1. 各ファイルの冒頭に「このファイルの役割」をコメントで記載
2. includeのネストは浅くする
3. すべてのテンプレートでHTML構造を統一
4. 明確な命名規則
5. 不要な抽象化を排除
6. コメントは“なぜ”を書く
7. 可読性の高いCSSセレクタ
8. 自動生成・minifyコードは使わない

---

# 12. 国際化（i18n）

* すべてのテキストは `__()` / `_e()` を使用
* テキストドメイン：`ai-basepress`
* 将来的に `languages/ai-basepress.pot` を提供予定

---

# 13. バージョニング

Semantic Versioning:

```
v1.x.x → 安定版（構造に破壊的変更なし）
v2.x.x → 大型追加（テンプレート増加など）
v0.x.x → 実験的
```

初期安定版：**v1.0.0**

---

# 14. ロードマップ

### v1.0.0（本リリース）

* 最小テーマ構造
* AI最適化設計
* 基本CSS / レイアウト
* メニュー1つ / サイドバー1つ

### v1.1.x

* `search.php` / `archive.php` の追加
* AIプロンプトサンプルの追加

### v2.0.0 – Addon Pack

* PluginPack Lite（汎用プラグイン対応）
* WooEdition（WooCommerce対応テーマ）

### v3.0.0

* 追加レイアウトブロック
* AI向け HTMLパターン集

---

# 15. 対象ユーザー

* 静的サイトからのWordPress移植を行う制作者
* 小規模サイト制作のフリーランス
* AIでテーマを作りたい人
* 既存テーマのカスタマイズ地獄を避けたい人
* プラグインと喧嘩しないベーステーマが欲しい人

---

# 16. 限界（あえて削っているポイント）

AI BasePressは以下を含まない：

* カスタマイザーUI
* グローバルスタイルパネル
* Block Patterns
* WooCommerceテンプレート
* jQuery / 大型JS
* CSSフレームワーク（Tailwind, Bootstrap 等）

理由：
**ベーステーマは“何も足さない・何も壊さない” が最強だから。**

---

# 17. ライセンス

**MIT License**

商用利用・改変・再配布すべて自由。

---


