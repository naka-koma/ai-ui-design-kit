# Architecture

```text
Central repository (GitHub + immutable revision)
    |
    | SETUP / SYNC: retrieve, inspect, apply, validate
    v
Project repository
    |- managed: common Skill + license
    |- merge-owned: AGENTS.md / CLAUDE.md Kit block
    |- project-owned: docs/design/**
    `- .ui-design-kit.yml: source, version, revision, ownership
```

中央の `skill/` は製品に依存しない判断基準、`templates/` は初回導入の骨組み、`integrations/` は既存指示へ統合する断片。中央の `docs/` はKit自体の仕様であり、導入先の `docs/design/` とは所有者が異なる。

SETUPは対象を調べてから配布物を配置する。UIがない場合はBootstrap、ある場合はDiscoveryを先に行う。設計文書は配布元と同じ状態を保つ対象ではなく、導入後は製品の判断として育てる。

SYNCはmanifestから中央を解決し、旧版と更新先を比較して共通物だけ更新する。初回テンプレートの更新を、製品文書の上書きに流用しない。詳細な衝突・復旧規則は [SYNC](../SYNC.md)、データ形式は [manifest](manifest.md) を正本とする。

## コピーによる配布の理由

通常のUI作業はインストール済みSkillとプロジェクト文書だけで行える。submodule、永久clone、中央サーバーへの実行時依存を必要としない。固定revisionを記録するため、何を導入したかと旧版との差分を追跡できる。

## 拡張境界

配布物の取得とローカル適用を分けることで、将来 [MCP](mcp.md) を取得層に追加できる。Design Auditは実装・設計文書・画面を比べる別の処理として設計し、Kit Syncへ混ぜない。
