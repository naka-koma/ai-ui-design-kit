# Future read-only MCP

これは将来設計であり、v5にサーバー実装・デプロイは含まれない。GitHubとSETUP/SYNCだけで利用できることを維持する。

```text
GitHub: 正本、履歴、リリース
MCP: 公開ファイルと導入・更新情報の取得
Coding agent: 対象調査、差分準備、ローカル適用、検証
```

## 候補インターフェース

| 操作 | 入力 | 出力 |
| --- | --- | --- |
| get_latest_version | なし | 最新安定タグ、解決revision、変更概要。未公開なら明示 |
| get_setup_instructions | 任意version | SETUP本文、schema版、解決revision |
| get_sync_plan | 導入版/revision、任意の更新先 | 版差分、移行説明、managed集合、merge指針、project-owned除外 |
| get_file | 許可path、任意version | 内容、解決revision、内容hash |
| get_manifest_template | 任意version | manifestテンプレートとschema説明 |

`get_file` は公開済みの `skill/`、`templates/`、`integrations/`、Kit仕様文書とLICENSE等のallowlistに限定する。パストラバーサル、任意URLの取得、サーバー内ファイルの参照を許容しない。version省略時もレスポンスに解決revisionを付け、同じ操作内で版を混在させない。

## 責務と制約

公開の基本取得は認証不要を想定するが、運用時の制限やキャッシュは別途検討する。MCPは対象リポジトリへ書き込まず、プロジェクト固有の設計文書を保存しない。GitHub全体のsource-control APIの代替にしない。

更新計画だけではローカル変更や所有衝突を判定できないため、エージェントがmanifestと実ファイルを確認し、SYNCと同じ保護規則で適用する。MCPが停止してもGitHub取得とインストール済みSkillを利用できる。

将来はmanifest検証、導入版比較、移行計画、Subject Swapチェックリストの取得を追加できる。製品固有のDesign Auditと、書き込み権限を持つ操作は別の設計課題とする。
