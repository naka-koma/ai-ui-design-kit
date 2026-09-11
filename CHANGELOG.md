# Changelog

## v0.5.0 — Unreleased

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
