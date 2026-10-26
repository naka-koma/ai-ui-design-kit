# UX considerations

導線・待ち・失敗・状態の確認観点。ルールや数値の標準ではなく、変更範囲に合わせて該当する観点だけ使う。製品ごとの値・部品・既定はプロジェクトの `docs/design/interaction.md` に従い、一般論で上書きしない。見た目の品質は [accessibility](accessibility.md)、[readability](readability.md)、[visual-hierarchy](visual-hierarchy.md) で別に確認する。

## 導線とナビゲーション

- 主要な行き先は見えるか。NN/gの調査では、隠したナビ（ハンバーガーなど）は使われにくく、内容の見つけやすさも下がった。狭い画面で行き先が少なければ見せ、多くて隠す場合は、ページ内に重要な入口を置いて補う。
- 並び合う区画の切り替え、順番のある手順、単発の操作を区別する。別の役割の部品に混ぜない。
- 画面幅と行き先の数に合う形か。幅ごとに見せ方を変えるとき、各幅で主要な行き先へ届くかを確認する。
- 今いる場所が分かり、戻る・やり直す手段があるか。初回と再訪で入口が違ってよいかも考える（続きから始める）。
- 片手で主要な操作に届くか。親指の届きやすさの研究は絶対の規則ではない。持ち方も変わるので、実機で確かめる。

## 待ち・進み具合・中断

- 目安として、約0.1秒は即時、約1秒は思考が途切れない限界、約10秒を超えると終わる見込みと中断の手段が要る。
- 長い待ちでは進み具合を示す。割合が分からなければ処理中の項目を示す。待たずに他の作業へ移れるか、終わりを見逃さず知れるか、結果がどこに戻るかを確認する。
- 中断・取り消しで入力と途中結果がどうなるかを決める。

## 失敗と回復

- エラーは原因の近くに、普通の言葉で具体的に、次の手とともに示す。利用者のせいにせず、重大度に合う強さにする。
- 入力を消さない。再試行で同じ状態へ戻れるか、失敗の通知を見逃してもあとから確認できるかを見る。
- 元に戻す、ゴミ箱、破壊的な操作の確認など、試すことを怖がらせない仕組みを必要な範囲で用意する。

## 空・読み込み中・失敗の状態

- 空白のまま残さない。読み込み中、何もない、失敗を区別し、読み込み中に「何もない」を出さない。
- 空の状態では、何ができるかと、最初の一歩へ直接進む操作を示す。

## 状態の保持と復帰

- 途中で離れても作業が残るか、戻ったとき続きから始められるかを確認する。未保存の警告は、失うものがあるときだけ出す。
- 通信の切断・遅延・オフラインで、壊れずに状況が分かり、再試行しても重複や取りこぼしが起きないかを確認する。

## 入力の負担

- 既定値、選ぶ形への置き換え、適切なキーボード、検証のタイミングで、タイプと迷いを減らす。
- 何度も変える値と、めったに触らない値を分け、後者を奥へ回す（段階的な開示）。頻繁に使うものは隠さない。

## 知らせ方と初めて使う人

- 通知・トーストは重要なものに絞り、見逃しと過多の両方を避ける。
- 初めての利用は、文脈の中のヒントと空の状態の案内で学べるようにする。強制の説明を先に置かない。

## 一貫性と言葉

- 同じことは同じ見た目・動き・言葉にする。一般的な慣習に従う理由と、外れる理由を説明できるようにする。
- 画面の言葉を利用者の言葉に合わせる。専門用語、略語、文末の揺れを確認する。

## 実機でしか見えない挙動

固定・粘着要素の透過やぼかし、キーボードを出したときの固定要素、画面の端のスクロール、重ね表示が画面端に出る位置、タッチの当たり判定は、PCのブラウザーや自動検査で見きれない。該当する変更では実機確認を依頼し、確認していなければ未確認と報告する。

## 根拠

- NN/g [Hamburger Menus and Hidden Navigation Hurt UX Metrics](https://www.nngroup.com/articles/hamburger-menus/)
- NN/g [Response Times: The 3 Important Limits](https://www.nngroup.com/articles/response-times-3-important-limits/)
- NN/g [Error-Message Guidelines](https://www.nngroup.com/articles/error-message-guidelines/)
- NN/g [Designing Empty States in Complex Applications](https://www.nngroup.com/articles/empty-state-interface-design/)
- NN/g [10 Usability Heuristics for User Interface Design](https://www.nngroup.com/articles/ten-usability-heuristics/)
- 親指の届きやすさ（二次的な資料。絶対の規則として扱わない）: [Smashing Magazine](https://www.smashingmagazine.com/2016/09/the-thumb-zone-designing-for-mobile-users/)、[Addy Osmani](https://addyosmani.com/blog/touch-friendly-design/)
