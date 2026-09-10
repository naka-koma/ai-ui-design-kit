<!-- ui-design-kit:begin -->
## UI Design Kit

Web UIを実装・変更・レビューするときは `.claude/skills/ui-design/SKILL.md` を読み、必要なreferencesを使う。プロジェクトの設計意図は `docs/design/README.md` と関連文書、正確な値はコード・tokensを参照する。

既存のProduct Signatureを保ちながら、WCAG 2.2 AAを既定基準にする。読みやすさと視覚階層も別に確認し、主要画面の変更ではSubject Swapを使う。標準的な設定・フォーム等のNEUTRALを失敗扱いにしない。

`.ui-design-kit.yml` は配布元・導入版・所有区分の記録。Kit Syncでは共通Skillを更新し、この指示は既存内容に統合する。`docs/design/**` はプロジェクト所有であり、Syncで上書きしない。実装と文書の整合を見るDesign Auditは別作業。
<!-- ui-design-kit:end -->
