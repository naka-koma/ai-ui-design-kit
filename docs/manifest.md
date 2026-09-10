# Manifest schema 1

`.ui-design-kit.yml` は導入先のルートに置く人間が読めるYAML。テンプレートは [こちら](../templates/manifest/.ui-design-kit.yml)。時刻・ユーザー名・絶対パスなど機械固有の情報は不要。

| フィールド | 型・意味 |
| --- | --- |
| schema_version | 整数。現在は1。未知の版は適用前に移行仕様を確認 |
| source.repository | 実際に取得した公開GitHubリポジトリのHTTPS URL。forkも可 |
| source.version | 存在を検証したタグ（例 `v0.4.0`）か `commit:<40桁SHA>` |
| source.revision | 必須の40桁コミットSHA。versionがタグならその解決先 |
| managed | `path`（導入先相対パス）と `source`（中央相対パス）の配列 |
| merge | `path`（対象指示ファイル）と `source`（中央snippet）の配列 |
| project_owned | Syncで保護する相対パスの配列。ディレクトリなら全子孫を含む |

## 配置と所有

ディレクトリmappingはソースツリーを配置先に対応させる。追加のLICENSE mappingは同梱するファイルを表す。配布元のSkill直下にはLICENSEを置かず、ルートLICENSEを正本とする。

親mappingの展開結果と子のファイルmappingが同じ宛先を持たない場合に限り、包含を許す。テンプレートの `skill/ui-design` と `LICENSE` がその例。将来Skill側にLICENSEが追加された場合はmappingを移行し、二重宛先を解消してから適用する。

全パスを対象ルート内へ解決し、絶対パス、`..`、`.git`、symlink経由の外部参照、OSの大文字小文字規則で衝突する宛先を拒否する。mergeとmanagedの重複、project-ownedとの重複も拒否する。`docs/design` は必須の保護先で、managed指定があっても書き込みを拒否する。

managedは置換可能な共通配布物。ただし導入済みrevisionと比較して発見したローカル編集は衝突として扱う。未知の追加ファイルを黙って消さない。独自ルールはproject-ownedへ記す。

mergeはファイル全体を中央所有にしない。`<!-- ui-design-kit:begin -->` と `<!-- ui-design-kit:end -->` の間を旧snippetと比較して統合し、外側を保持する。配置パスの置換は導入先mappingに従う。ブロック欠落・重複・意味の競合は再構築前に解決する。

## バージョンと移行

`v4` はKitの設計世代、`v0.4.0` は予定する配布タグ、`schema_version: 1` はmanifest形式。これらを混同しない。タグが未公開なら `v0.4.0` を導入済みと記録せず、固定コミットを使う。

manifestは導入先を表し、中央リポジトリ自体へテンプレートをそのままコピーしない。更新後の検証が成功した時だけversion/revisionを書き換える。未知の追加フィールドは保持するが、未知のschemaや所有操作を推測で実行しない。
