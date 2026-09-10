<!-- ui-design-kit:begin -->
## UI Design Kit

Web UIの作業時は `.claude/skills/ui-design/SKILL.md` と `docs/design/README.md` を入口にする。関連する設計文書とコード・tokensに従い、Product Signatureを保つ。アクセシビリティ（既定はWCAG 2.2 AA）、読みやすさ、視覚階層を個別に確認する。

主要画面や大幅な再設計ではSkillのSubject Swapを実施し、PASS / NEUTRAL / FAILと根拠を記す。小修正に強制せず、一般的な設定画面等のNEUTRALを許容する。

共通Kitの更新は `.ui-design-kit.yml` の取得元のSYNC.mdに従う。指示ファイルを丸ごと置換せず、project-ownedの `docs/design/**` は上書きしない。Design AuditはKit Syncに含めない。
<!-- ui-design-kit:end -->
