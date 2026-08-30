# RESPONSIVE_RULES

対象は Desktop / Tablet / Mobile。

具体的なbreakpoint値、左右余白、列数、コンポーネント寸法はTBDとする。

本ファイルでは、これまで確定したレスポンシブ方針のみを定義する。

## 1. 共通原則

- Desktop / Tablet / Mobileすべてを対象とする
- MobileをDesktopの単純な縮小だけで処理しない
- 情報の優先順位をviewport間で維持する
- SITEMAPで確定したセクション順を維持する
- 意図しないhorizontal overflowを発生させない
- テキスト、フォーム、チャート、Navigationをviewport外へ欠落させない
- UI同士を意図せず重ねない
- ページごとに独自のレスポンシブルールを理由なく追加しない

## 2. Breakpoints

- Desktop：TBD
- Tablet：TBD
- Mobile：TBD

具体的なpixel値は未決定。

## 3. Desktop

確定済みレイアウト：

`Sidebar | Main Content`

Navigation：

- 左サイドナビゲーションを使用する
- 5ページへの導線を同じ順序で表示する
- 現在ページを識別可能にする

Main Content：

- 共通Container ruleを使用する
- 左右余白：TBD
- Max width：TBD
- Grid columns / gap：TBD

## 4. Tablet

具体的なNavigation方式：TBD。

具体的なLayout方式：TBD。

左右余白：TBD。

確定済み要件：

- 全ページを閲覧・操作可能にする
- 情報階層を維持する
- viewport外への意図しない欠落・overflowを発生させない

## 5. Mobile

Navigation：

- Desktopの左サイドナビゲーションをそのまま維持せず、簡略化する
- 具体方式はTBD
- Drawer / Bottom Navigation等の方式は未確定であり、事前に決めない

Layout：

- Desktopを単純縮小するだけの実装にしない
- 主要情報の優先順位を維持する
- 左右余白：TBD
- Grid列数：TBD
- コンポーネントの具体的な積み替え方：TBD

## 6. Typography

viewportごとの具体的なfont-size / line-height変更：TBD。

確定済み要件：

- ページタイトルを過度に巨大化しない
- 主要数値と補助情報の視覚的差を維持する
- テキストをviewport外へ欠落させない

## 7. Spacing

- Desktop：TBD
- Tablet：TBD
- Mobile：TBD

確定済みの相対階層：

主要領域間
>
セクション間
>
コンポーネント間
>
コンポーネント内部

viewportが変わってもこの相対階層を維持する。

## 8. Forms

具体的なfield構成はTBD。

確定済み要件：

- Mobileでも操作可能なサイズを確保する
- input等をviewport外へはみ出させない
- 横並びfieldを使用する場合のMobileでの変換方法はTBD

## 9. Cards / Metrics

具体的な列数・配置変更：TBD。

Card / Metric UI自体が未確定の場合は、レスポンシブ用のvariantを先回りして作らない。

## 10. Charts / Media

具体的なchart type・表示内容・Mobile変換方式：TBD。

確定済み要件：

- Containerから意図せずはみ出さない
- ラベル等の可読性を維持する
- 視覚情報だけに依存して主要情報を伝えない

## 11. Responsive Verification

最終的にDesktop / Tablet / Mobileの各区分で、全5ページを実ブラウザ確認する。

具体的な検証viewport pixel値はTBD。

判定条件は `09_ACCEPTANCE_CRITERIA.md` に従う。
