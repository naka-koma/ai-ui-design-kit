# v4 acceptance review

## 検証の範囲

添付のv4受入条件をこの実装に対応させた記録。配布物は文書・Skill・テンプレートであり、自動インストーラーやMCPサーバーではない。シナリオ検証は手順のウォークスルーで、実製品への導入実績やUIのWCAG適合を意味しない。

| 受入区分 | 対応と確認結果 |
| --- | --- |
| Repository architecture | READMEを概要に限定し、SETUP・SYNC・CHANGELOGを独立配置。既存MITを維持。個人のローカルパスや非公開製品情報を含めない |
| Skill | skill/ui-design/SKILL.mdと9つのreferencesを配置。WCAG 2.2 AA、独立した読みやすさ・階層レビュー、signature保持、既定表示と設定の関係を記述 |
| Subject Swap | 専用referenceをSkill、product-signature、visual-reviewから参照。交換後の特徴、PASS/NEUTRAL/FAIL、汎用画面の許容、過剰装飾を避ける手順を定義 |
| Setup | BootstrapとDiscoveryを分離。既存文書の保持、再設計禁止、manifest作成と検証を規定 |
| Sync | manifestから取得元を解決。managed置換・指示統合・project-owned不変を規定。成功後だけ版を更新。Design Auditと区別 |
| Manifest | 読めるYAMLにsource/version/revisionと所有mappingを記録。絶対パスや機械情報を不要とし、衝突・未公開タグの扱いも定義 |
| Future MCP | docs/mcp.mdに読み取り専用API候補と責務を定義。submodule、実行時中央接続、MCP展開は不要 |

## シナリオのウォークスルー

### A. 新規プロジェクト

入力は中央URLとSETUP.mdのみ。安定リリースが未公開でも固定コミットで取得できる。UIなしを確認してBootstrapを選び、共通SkillとLICENSE、設計テンプレート、指示、実値を入れたmanifestを作成する。設計が不明な項目は未決定のまま残せる。手順上の欠落なし。

### B. 成熟したUIのあるプロジェクト

先に既存指示・設計・CSS・tokens・画面等をDiscoveryで調べる。文書は不足箇所だけ統合し、既存のsignatureを根拠付きで保持する。既存の同名Skillは衝突を解決するまで置換しない。UIコードに変更を加えず導入できる。手順上の欠落なし。

### C. 導入済みKitの更新

manifestの旧revisionと更新先を取得し、managedのローカル編集を検出する。共通物だけを更新し、指示は3者比較で統合。project-ownedは更新前後に不変を確認し、検証成功後にmanifestを更新する。手順上の欠落なし。

### 追加の境界確認

- manifestなし・未知schema: 推測で上書きしない。
- 未公開タグ: 存在しないv0.4.0を導入済みと記録しない。
- ローカル編集・未知の追加ファイル: 黙って破棄しない。
- managedとproject-ownedの重複・外部パス: 適用前に拒否。
- 部分失敗: 今回分だけ復旧し、導入済み版を進めない。
- 通常の設定画面: Subject SwapのNEUTRALを許容。

## 機械検証

Skill Creatorの `quick_validate.py` は `Skill is valid!` で成功。ローカルMarkdownリンク44件、manifestのYAML構文、配布元の参照、managedの12個の宛先の重複なし、snippet境界、行末空白、機械固有のローカルパスがないことを検査し、すべて成功した。

これらは文書どおりに未知のエージェントが振る舞うことまで保証するものではない。
