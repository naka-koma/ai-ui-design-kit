# SETUP — 初回導入プロトコル

対象プロジェクトで作業するエージェント向け。依頼された導入の範囲で実施し、既存UIのリデザインは行わない。

## 1. 配布元と対象を確認

中央の既定URLは `https://github.com/naka-koma/ai-ui-design-kit`。ユーザーが別のforkを指定した場合はそれを使用する。対象プロジェクトのルート、既存指示、作業差分、manifest、既存Skill、設計文書を確認する。

既に `.ui-design-kit.yml` がある場合は [SYNC.md](SYNC.md) を使う。壊れたmanifestや管理先の衝突は上書きせず報告する。

指定タグ、指定コミット、または最新の非prereleaseリリースを一時ディレクトリへ取得する。安定リリースがまだない場合は既定ブランチのHEADを固定コミットとして取得し、未リリースのスナップショットであることを報告する。取得した同一コミットの手順・Skill・テンプレートを使い、途中でHEADを取り直さない。

## 2. Design Bootstrap / Design Discovery

UIのない新規プロジェクト・視覚方針が未定の製品は **Design Bootstrap**。現在の依頼から確認できる目的、利用者、主要タスクだけ記録する。未決定欄を想像で埋めず「未決定」と残す。

既存UIがある場合は文書を作る前に **Design Discovery** を行う。

- CSS、tokens、テーマ、共通コンポーネント、フォントと文字組み
- 余白、角丸、境界、影、透過、ぼかし、効果、モーション
- ナビゲーション、情報密度、画面構成、反復される特徴
- レスポンシブ挙動、キーボード・フォーカス、状態、アクセシビリティ
- 既存の設計文書、代表画面やStorybookが利用可能なら実際の表示

観察事実・推定・未確認を分け、根拠のコードパスを記録する。繰り返し現れる表現を候補にしても、根拠のない設計意図を断定しない。実行できないUIは未検証と記す。導入だけを理由にCSS・コンポーネント・テーマを修正しない。

## 3. 共通Skillを配置

`skill/ui-design/` を対象の `.claude/skills/ui-design/` にコピーする。別の配置先を使う既存規約がある場合はそれに合わせ、manifestと指示内のパスを同じ値にする。自動発見に依存せず、指示ファイルからSKILL.mdを明示参照する。

既に同名ディレクトリがあり、Kitによる管理が確認できなければ置換しない。内容を比較し、競合する部分だけ解決を求める。中央の `LICENSE` を配置先の `LICENSE` に同梱する。インストール対象にテンプレート以外の中央 `docs/` や一時cloneを含めない。

## 4. プロジェクト文書を作成・統合

`templates/docs/design/` を骨組みとして使う。既存の `docs/design/**` は盲目的に上書きしない。新規はテンプレートを作り、既存は必要な不足箇所だけ証拠に基づいて追記する。既存内容や構成に合わせ、同義の文書を重複作成しない。

`signature.md` の Must preserve / May adapt / Must not compromise / Accessibility adaptations / Canonical implementation references を記録する。確定できない場合は未決定のままにする。正確なCSS値はコード・tokensが正本であり、Markdownへ値一覧を転記しない。

既存のsignatureを保持する。発見した問題は別作業の候補として記録し、導入作業に改善や再設計を混ぜない。

## 5. エージェント指示を統合

[AGENTS snippet](integrations/AGENTS.md.snippet.md) を `AGENTS.md` に、CLAUDE.mdを利用する対象では [CLAUDE snippet](integrations/CLAUDE.md.snippet.md) も統合する。`ui-design-kit:begin/end` ブロックは1つだけ配置する。ファイル全体を置換せず、既存ルールとの意味の競合を確認する。配置先を変更した場合はスニペットのパスも調整する。

## 6. manifestを作成

[テンプレート](templates/manifest/.ui-design-kit.yml) と [仕様](docs/manifest.md) に従い、プロジェクトルートへ `.ui-design-kit.yml` を作る。

- `source.repository`: 実際の中央URL
- `source.version`: 存在を確認したタグ、または `commit:<full SHA>`
- `source.revision`: 取得コミットの40桁SHA
- `managed`: 実際の配置先とソースの対応（LICENSEも含む）
- `merge`: 実際に統合した指示ファイルだけ
- `project_owned`: `docs/design` と対象固有の保護先

テンプレートの未解決値を残して完了扱いにしない。配置先に絶対パスや親ディレクトリ参照を使わない。

## 7. 検証と報告

リンク先と配置先の存在、Skill frontmatter、manifestの値と所有範囲、スニペット重複がないことを確認する。共通SkillとLICENSEが取得元に一致すること、既存の設計判断と導入前のUIコードが保持されたことを差分で確認する。

完了報告には取得元・タグ/コミット、Bootstrap/Discoveryの選択、追加/統合したファイル、保持した設計、未決定/未確認事項を含める。自動テストのみで視覚品質やWCAG適合を断定しない。
