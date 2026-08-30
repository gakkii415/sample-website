# DESIGN_SYSTEM

具体値が未確定の項目はTBDとする。

参考サイトから得た方向性を、確定した具体値として扱わない。

## 1. Typography

Font family：TBD

使用する情報階層：

- 主要数値
- ページタイトル
- セクションタイトル
- 本文・項目
- 補助情報

確定済みルール：

- タイポグラフィで情報階層を作る
- 主要数値は補助情報より強く表示する
- ページタイトルと主要数値の相対的優先順位はTBD
- 巨大すぎる見出しは使わない
- 同じ役割のテキストは同じスタイルを使用する
- 数字の読みやすさを優先する

## 2. Font Size Scale

- Major metric：TBD
- Page title：TBD
- Section title：TBD
- Body：TBD
- Label：TBD
- Supporting / Caption：TBD

ルール：

- ページ固有のfont-sizeを理由なく追加しない
- ページタイトルをHero見出しのように巨大化しない

## 3. Font Weight

具体値：TBD

- Body：TBD
- Label / Navigation：TBD
- Heading：TBD
- Major metric：TBD

ルール：

- すべての文字を強調weightにしない
- 強調はTypography全体の階層で表現する

## 4. Line Height

- Major metric：TBD
- Heading：TBD
- Body：TBD
- Supporting：TBD

## 5. Spacing Scale

具体値：TBD

必要なspacing token：TBD。

相対階層：

主要領域間
>
セクション間
>
コンポーネント間
>
コンポーネント内部

ルール：

- 任意のspacing値をページごとに増やさない
- 同じ構造には同じspacing ruleを使用する
- 過剰な大余白を使用しない

## 6. Container Width

Max width：TBD

ルール：

- 全ページで基本となるContainerルールを共有する
- ページごとに独自の最大幅を理由なく追加しない

## 7. Desktop / Tablet / Mobile の左右余白

- Desktop：TBD
- Tablet：TBD
- Mobile：TBD

ルール：

- 同一viewport区分ではページ間で共通ルールを使用する
- Mobileでコンテンツを画面端へ詰めすぎない
- Desktopで不必要に広い余白を作らない

## 8. Grid

Desktopの基本構造：

`Sidebar | Main Content`

- Columns：TBD
- Gutter：TBD
- Gap：TBD

ルール：

- 数値・グラフ・一覧は共通の整列原則に従う
- ページ間で列位置を揃える
- 不要なBento Grid化をしない

## 9. Colors

具体的な色値：TBD

必要な色の役割：

- background：TBD
- surface：TBD
- surface-subtle：TBD
- text-primary：TBD
- text-secondary：TBD
- text-muted：TBD
- border-default：TBD
- border-strong：TBD
- accent：TBD
- accent-hover：TBD
- positive：TBD
- negative：TBD
- neutral：TBD

確定済みルール：

- 必要以上に暗いUIにしない
- 色より情報階層を優先する
- 装飾目的のグラデーションを原則使わない

## 10. Border

- border-width-default：TBD
- border-color-default：TBD
- border-color-strong：TBD

ルール：

- 情報分離に必要な場合のみ使用する
- すべての要素を枠で囲まない
- shadowとborderを同時に過剰使用しない

## 11. Radius

- radius-sm：TBD
- radius-md：TBD
- radius-lg：TBD

ルール：

- 大きな丸角を全面的に使用しない
- pill型は必要な要素に限定する
- ページごとに異なるradiusを乱造しない

## 12. Shadow

- shadow-subtle：TBD
- shadow-overlay：TBD

ルール：

- 原則として最小限にする
- 情報階層はshadowより余白・border・背景差を優先する
- 全カードを浮かせない
- 強いdrop shadowを装飾目的で使用しない

## 13. Button

具体的なvariant構成：TBD

候補分類：

- Primary
- Secondary
- Tertiary / Text

必要性が確定したvariantだけを実装する。

- Height：TBD
- Horizontal padding：TBD
- Vertical padding：TBD
- Radius：TBD
- Font size：TBD

ルール：

- 主操作だけを最も強くする
- すべてのボタンをPrimaryにしない
- 同じ役割は全ページで同じスタイルを使用する
- 不要なpill形状を避ける

## 14. Link

具体スタイル：TBD

ルール：

- 通常テキストと識別可能にする
- Hoverだけに依存しない
- 同種リンクは一貫した見た目にする

## 15. Form

具体的な入力項目：TBD

共通ルール：

- Labelを明示する
- placeholderだけをLabel代わりにしない
- input / select / textareaを使用する場合の高さ・radiusは共通化する
- Focus状態を明確にする
- Error状態を色だけに依存させない
- Mobileでも操作可能なサイズを確保する

具体寸法：TBD

## 16. Icon

アイコンセット：TBD

Icon size：TBD

ルール：

- 意味のある場所だけに使用する
- 装飾目的で乱用しない
- 同じ意味には同じiconを使用する
- Navigation等で使用する場合もtext labelを優先する
- stroke / sizeを統一する

## 17. Motion

- duration-fast：TBD
- duration-default：TBD
- duration-slow：TBD
- easing-standard：TBD
- easing-emphasized：TBD

確定済みルール：

- 大きな演出アニメーションを使わない
- 演出的スクロールを採用しない
- 情報把握を妨げるmotionを使わない

`prefers-reduced-motion` の具体的対応仕様：TBD。

## 18. Breakpoints

対象区分：

- Desktop
- Tablet
- Mobile

具体的breakpoint値：TBD

確定済みルール：

- Desktopでは左サイドナビゲーションを使用する
- Mobileではナビゲーションを簡略化する
- Tabletの具体的なナビゲーション・レイアウト方式はTBD

詳細は `07_RESPONSIVE_RULES.md` を参照する。
