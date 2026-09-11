---
name: ui-design
description: Web UIの実装・変更・視覚レビューで、既存のプロダクトらしさを保ち、アクセシビリティ、読みやすさ、情報階層を改善する。画面設計や主要ワークフローの変更に使用する。
---

# UI Design

依頼されたUIの範囲で使う。共通ルールを理由に、依頼外の全体リデザインやブランド変更を始めない。

## 作業の進め方

1. 対象のエージェント指示、`docs/design/`、実装とtokensを読む。導入場所や設計文書が不明なら [project-integration](references/project-integration.md) を参照する。
2. 既存UIでは設計意図と根拠を確認。新規では現在のタスクに必要な方針だけ決める。[design-principles](references/design-principles.md) と [product-signature](references/product-signature.md) を使い、未確認の意図を断定しない。
3. 参考サイト、画像、Pinterestボードなどが与えられた場合は、実装前に [visual-reference-analysis](references/visual-reference-analysis.md) で観察を設計判断へ翻訳する。見た目を複製せず、取り入れる要素・使う場所・採用しない理由を決める。
4. 実装時は [accessibility](references/accessibility.md)、文字中心の画面では [readability](references/readability.md)、画面構成では [visual-hierarchy](references/visual-hierarchy.md) を参照する。WCAG 2.2 AAを既定基準とし、適合だけで読みやすさや視覚品質が十分と判断しない。
5. 変更規模に応じて [visual-review](references/visual-review.md) を実施する。主要画面や大きな再設計では [subject-swap](references/subject-swap.md) でPASS / NEUTRAL / FAILを判定する。小修正にフルレビューを強制しない。
6. 意図しない一般化や装飾過多を [anti-patterns](references/anti-patterns.md) で確認。変更、確認方法、未検証状態を報告する。

## 保持する境界

`docs/design/**` はプロジェクト所有。正確な値はコード・tokensを参照し、文書と二重管理しない。共通Skillの更新はKit Sync、実装と文書の整合確認はDesign Auditとして扱う。

Distinctive != Inaccessible。Accessible != Generic。signatureの問題は、意図を保った実装修正・局所調整・適切なユーザー設定から検討する。OS設定や任意モードは、アクセシブルでない既定表示の免罪符にしない。
