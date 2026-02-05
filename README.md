# pencil-slide

Pencil MCP を使って、テーマ指定から以下を自動生成するためのワークスペースです。

- スライド（`.pen` + 設計ドキュメント）
- プロダクト UI（`.pen` + 設計ドキュメント）
- カラーパレット（必要に応じて）

このリポジトリでは、`AGENTS.md` と `skills/*/SKILL.md` の手順に従って作業します。

## できること

1. `slide:` 指示で、調査・構成・デザインまで含めたスライド作成
2. `product:` 指示で、UI/UX 設計を含むプロダクト画面作成
3. 色設計が必要な場合のカラーパレット生成

## ディレクトリ構成

```text
.
├── AGENTS.md
├── CLAUDE.md
├── README.md
├── skills/
│   ├── generate_slides_by_pencil/SKILL.md
│   ├── generate_product_by_pencil/SKILL.md
│   └── generate_color_palette/SKILL.md
├── tasks/
└── templates/  # テンプレート・コンポーネント用の .pen ファイルを配置
```

## 実行例

### Codex

```bash
codex --full-auto "slide:白米に合うおかずについて"
```

### Claude Code

```bash
claude --dangerously-skip-permissions "product:ジビエ専門店のECサイト"
```

## タスク出力ルール

### スライド生成時

- 出力先: `tasks/slide_{number}_{task-name}/`
- 主要ファイル:
  - `theme.md`
  - `slide.md`
  - `theory-of-slide-design.md`
  - `slide.pen`

### プロダクト生成時

- 出力先: `tasks/product_{number}_{task-name}/`
- 主要ファイル:
  - `theme.md`
  - `product.md`
  - `theory-of-product-design.md`
  - `product.pen`
  - `images/`（必要な場合）

## 作業フロー（概要）

1. テーマと独立した設計セオリーを作成
2. テーマ調査と要件整理
3. スライド/画面構成ドキュメント作成
4. Pencil MCP で `BaseComponents` を作成
5. 本文スライド/画面を実装
6. レイアウト崩れ・配色バランスを検証して修正

詳細手順は下記を参照してください。

- `skills/generate_slides_by_pencil/SKILL.md`
- `skills/generate_product_by_pencil/SKILL.md`
- `skills/generate_color_palette/SKILL.md`

## AGENTS.md の適用ルール

- `slide` / `スライド` 系の依頼: `skills/generate_slides_by_pencil/SKILL.md` を使用
- `product` / `プロダクト` 系の依頼: `skills/generate_product_by_pencil/SKILL.md` を使用
- `dev` 系の依頼: `skills/dev/SKILL.md` を参照（存在する場合）

## 補足

- `tasks/*` は生成物置き場です（`.gitignore` 対象）。
- `templates/*` にはテンプレートやコンポーネントの `.pen` ファイルを配置します。
