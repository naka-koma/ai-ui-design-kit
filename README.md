# AI UI Design Kit

AIエージェントによるWeb UI実装で、プロダクト固有の表現を保ち、アクセシビリティ・読みやすさ・操作性を整えるための共通Skillと導入プロトコルです。

画面を一律のSaaS風デザインに揃えるためのコンポーネント集ではありません。各プロジェクトのコードと設計意図を読み、必要な変更を判断するための配布元です。

## はじめる

- 初回導入: [SETUP.md](SETUP.md)
- 共通Kitの更新: [SYNC.md](SYNC.md)
- Skill: [skill/ui-design/SKILL.md](skill/ui-design/SKILL.md)
- 設計: [architecture](docs/architecture.md) / [manifest仕様](docs/manifest.md)
- 検証記録: [validation](docs/validation.md)

```text
https://github.com/naka-koma/ai-ui-design-kit の SETUP.md を読み、
現在のリポジトリにUI Design Kitを導入してください。
```

導入後の更新依頼:

```text
.ui-design-kit.yml の取得元を確認し、その SYNC.md に従ってKitを更新してください。
```

## 考え方

- **Design Bootstrap / Discovery**: 新規UIでは必要な方針だけ決め、既存UIでは証拠から設計意図を抽出します。
- **Product Signature**: 密度、構成、操作、質感など、プロダクトらしさを保持します。
- **Subject Swap**: 名前やコピーを交換しても残る特徴を確認。汎用的な設定画面などはNEUTRALとして認めます。
- **品質**: WCAG 2.2 AAをWebの既定基準にし、読みやすさと視覚的な階層も別途レビューします。

## 所有と配布

```text
中央リポジトリ ── SETUP / SYNC ──> 各プロジェクト
                                  ├─ managed: 共通Skill
                                  ├─ merge-owned: エージェント指示
                                  └─ project-owned: docs/design/**
```

Skillはコピーして使います。submoduleや中央リポジトリへの実行時接続は不要です。Kit Syncは共通ルールの更新であり、製品UIと設計文書の整合を調べるDesign Auditとは別です。

## 状態とライセンス

v4仕様の初期実装（予定バージョン `v0.4.0`）。公開済みタグの存在を前提にしません。[CHANGELOG](CHANGELOG.md)を参照してください。既存の[MIT License](LICENSE)を継承します。将来の[読み取り専用MCP](docs/mcp.md)は設計のみで、現在の導入には不要です。
