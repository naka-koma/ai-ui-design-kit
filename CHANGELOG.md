# Changelog

## v0.5.0 — Unreleased

- Issue #2: 導線とナビゲーション、待ち・進み具合・中断、失敗と回復、空・読み込み中の状態、状態の保持と復帰、入力の負担、知らせ方、一貫性、実機でしか見えない挙動を、確認の観点として `ux-considerations` に追加。SKILL・visual-review・プロジェクトの `interaction.md` テンプレートから参照。
- Issue #1: 読む順番、素材の役割、統一感と均一化の区別、密度に合う整理、実物・実データ、文脈への適合を汎用原則として追加。Bootstrap / Discovery・レビュー・principlesテンプレートへ反映し、スタイルの最終判断は人間に残す。
- 参考サイト、ギャラリー、Pinterest等を「かっこいい」で終わらせず、印象・構成・文字組み・色・操作を設計判断へ翻訳するVisual Reference Analysisを追加。
- プロジェクトのreferencesテンプレートに、観察・採用/適応/不採用・対象画面・検証を残す表を追加。
- アンチパターンを、禁止する表層ではなく、問題・利用者への影響・修正判断を学ぶためのreferenceへ拡張。

## v0.4.0 — Initial implementation

UI Design Kit v4の初期実装。既存リポジトリはLICENSEのみで、v3のソース移行ではなく要件から構築した。

- README（概要）・SETUP（初回導入）・SYNC（更新）を分離。
- 共通Skillと用途別references、プロジェクト用designテンプレートを追加。
- manifestに配布元・導入版・固定revision・所有区分を定義。
- 新規のDesign Bootstrapと既存UIのDesign Discoveryを分離。
- Product Signatureの保持とアクセシビリティへの局所的な適応を規定。
- WCAG 2.2 AAを既定基準とし、読みやすさ・視覚階層も独立して確認。
- Subject SwapのPASS / NEUTRAL / FAILを導入し、不要な独創性の強制を防止。
- Syncでproject-owned文書を保護し、Design Auditと区別。
- 将来の読み取り専用MCP向けに取得・計画・適用の責務を分離。
