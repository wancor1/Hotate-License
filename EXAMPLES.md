# Hotate License 1.0 適用・通知の記載例

> Hotate License 1.0の説明用サンプルです。ここに示す文言は新たな許諾条件を追加しません。第2・4〜7・12〜14条および付属規定A〜Dを確認してください。以下の著作権者名・URL・ファイル名はすべて架空の例です。

## 1. ファイルごとの指定

例えば、自分が権利を持つRustファイル冒頭に記載する場合。

```rust
// SPDX-License-Identifier: LicenseRef-Hotate-1.0
// Copyright (c) 2026 Example Author
// Original license: Hotate License 1.0
// Applied license: Hotate License 1.0
```

`LicenseRef-Hotate-1.0` は独自のSPDX形式識別子です。SPDX公式登録済みIDではありません。対応するライセンス全文を受領者が無料で取得できるようにしてください。

## 2. プロジェクト単位の一括指定

一括指定は、ファイル単位の指定がないファイルを含め、権利者が許諾できる範囲で適用します。例として管理ファイルに次のように書けます。

```text
License: Hotate License 1.0
License identifier: LicenseRef-Hotate-1.0
Scope: src/**, scripts/**
Excluded: src/vendor/**
License text: LICENSE.md
```

この形式は**Hotate向けの説明例**であり、SPDX・REUSE共通の標準構文ではありません。管理用ツールにはそのツールが解釈できる形式で最終結果を記録してください。

通常の指定の優先順位は `特記個別 > 個別 > 特記一括 > 一括`。正当な権利者の有効な優先順位変更特記がある場合は、その指定に従います。第三者の権利は上書きできません。

## 3. 適用バージョンを新版へ変更した場合

Now / New方式で正式な最新バージョンを選択した場合、元の許諾版と現在の適用版を区別します。以下は将来3.0が正式発行され、それを適法に選択できる場合の**仮想例**です。

```text
Original license: Hotate License 1.0
Original identifier: LicenseRef-Hotate-1.0
Selected applied license: Hotate License 3.0
Applied identifier: LicenseRef-Hotate-3.0
Selection: New
```

元のライセンス通知は保持してください。存在しない将来版を現時点で選択できるという意味ではありません。また、バージョン履歴を単純にSPDXの`AND`や`OR`へ変換しないでください。

## 4. 対象コードを改変して配布する場合の変更履歴

対象ファイルと具体的な変更を記載します。下記の例は、あくまで説明用です。

```markdown
## 1.2.0 (2026-10-09)

- `src/renderer.rs`: 描画順の計算を深度ソート方式に変更。
- `src/cache.rs`: キャッシュ失効時の再取得処理を追加。
- 関連機能: 独立したUIファイルから描画品質設定を切り替える機能を追加（Hotate対象ファイルの改変に伴う連携機能）。
- Modified by: Example Developer
```

対象コードを改変せず、完全に独立したファイルのみ追加した場合は、そのことだけでHotateの変更履歴義務は発生しません。過去の履歴の保持義務には引き続き注意してください。

## 5. バイナリ配布時の対応ソース

完全なソースを案内する例。

```text
Hotate-covered components: src/core/**
Corresponding source: https://example.invalid/releases/1.2.0/source.zip
License: LICENSE.md
Change history: CHANGELOG.md
```

差分方式の例。

```text
Original source revision: v1.1.0 (commit: <exact revision>)
Original source: https://example.invalid/releases/v1.1.0/source.zip
Patch: https://example.invalid/releases/v1.2.0/hotate.patch
Reconstruction: apply the patch to the stated original revision
License: LICENSE.md
Change history: CHANGELOG.md
```

元ソース・差分から完全に復元できる必要があります。実際に配布する場合は、上記のダミーURLを利用可能なURLに置き換えてください。ソースは配布中に無料で取得できるようにします。

## 6. 別ライセンスを同じファイルに含む場合

同一ファイルの中に異なる権利者・異なるライセンスの部分があるときは、適用部分と各通知を明確に分けます。`SPDX-License-Identifier: LicenseRef-Hotate-1.0` を書いただけで第三者コードがHotateへ変更されるわけではありません。

同一のコード全体について選択式の複数許諾がある場合と、別々の部分に別々の許諾が必要な場合も区別してください。`AND`や`OR`のみで対象部分を確定できないときは、部分別の対応表を添付します。

## 7. GNU系へ追加許諾する場合

GPL系との私的な結合・改変では、第三者に配布していない時点で配布時の通知やソース提供は発生しません。実際に配布する場合は、選択したGNU系のライセンス本文、法的表示、対応ソースなど、そのライセンスが要求する条件に従ってください。Hotate由来であることや追加許諾の根拠をREADME等に記載するのは推奨ですが、GNU系配布の独立した必須条件ではありません。

GNU系ライセンスを選んだ経路では、Hotate独自の変更履歴、独自ソース提供方式、原許諾版と適用版の二重通知を重ねて課しません。一方、Hotate通常経路で配布する場合は、通常のHotate条項を守ってください。

## 8. 公式配布がStoppedになった場合

公式が配布終了を宣言した場合、公式の新規配布は停止します。ただし、過去の正当な受領者による利用や第三者の再配布は、それぞれ成立済みの許諾に従います。第三者の再配布を `Stopped` として扱う必要はありません。

## 9. ライセンス全文の同梱

正式に発行されたHotate Licenseの全文（本文と付属規定）を、自分のプロジェクトの`LICENSE.md`に内容を変更せずに同梱できます（第18.15項）。ファイル形式や改行の変更は、意味と内容が変わらない範囲に限ります。コードへの適用指定と、ライセンス本文そのものの転載許可は別です。

## 注意

- `QUICK_GUIDE.md` は便利な概説ですが、正式な法的条件ではありません。
- GPL・LGPL・AGPLを組み合わせるときは、第12条と付属規定Dに加え、相手ライセンス自体の義務を確認してください。
- 実際の利用時は、正式原文と各権利者の有効な許諾条件を確認してください。公式原文: https://github.com/wancor1/Hotate-License 。
