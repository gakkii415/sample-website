# COMPONENT_RULES

再利用が実際に発生するものだけを共通化する。

「将来使うかもしれない」を理由にコンポーネントを作らない。

具体値は `05_DESIGN_SYSTEM.md` に従い、未決定値はTBDとする。

## 1. Header

### 用途

各ページ上部でページタイトルと、必要な場合のページ固有操作を配置する。

### バリエーション

具体的なvariant：TBD。

### 使用条件

- SITEMAPで定義された各ページのページヘッダーとして使用する
- ページタイトルを明確に示す

### 使用禁止条件

- Hero的な巨大ヘッダーとして使用しない
- 装飾目的で高さを大きくしない

### サイズ

TBD。

### 余白

DESIGN_SYSTEMのspacing ruleに従う。具体値はTBD。

### 状態

Header自体の状態は不要。

ページ固有CTAの有無・状態はTBD。

### Hover / Focus / Active

Header自体には不要。内部のinteractive elementに適用する。

### Responsive behavior

- Desktop / Tablet / Mobileでページタイトルの役割を維持する
- 具体的な配置変更はTBD

### Accessibility requirements

- ページタイトルに適切な見出しを使用する
- 内部の操作要素はキーボード操作可能にする

---

## 2. Navigation

### 用途

確定済み5ページ間の移動。

対象：

- ダッシュボード
- 収支一覧
- 収支入力
- 月次レポート
- 設定

### バリエーション

- Desktop：左サイドナビゲーション
- Mobile：簡略化ナビゲーション。具体方式TBD
- Tablet：TBD

### 使用条件

- 全ページ共通
- ページ順序を全ページで維持する

### 使用禁止条件

- 未確定ページを追加しない
- 不要な階層を追加しない
- ページごとにNavigation構造を変更しない

### サイズ

TBD。

### 余白

TBD。

### 状態

- Default
- Hover
- Focus
- Active / Current page

### Hover / Focus / Active

- 現在ページを識別できるActive状態を持つ
- Hoverだけで状態を伝えない
- Focusを視覚的に識別できるようにする

### Responsive behavior

`07_RESPONSIVE_RULES.md` に従う。

### Accessibility requirements

- Navigationとして意味付けする
- 現在ページを支援技術でも識別可能にする
- キーボード操作可能にする
- アイコンのみのNavigationを原則避ける

---

## 3. Footer

現時点で必要性が確定していない。

作成しない。

必要性が確定した場合のみ仕様化する。

---

## 4. Button

### 用途

ユーザー操作を実行する。

### バリエーション

具体的variantはTBD。

候補分類：

- Primary
- Secondary
- Tertiary / Text

必要性が確定したvariantのみ実装する。

### 使用条件

- 明確な操作が存在する場合
- CTAまたはフォーム操作として必要な場合

### 使用禁止条件

- 単なるページ遷移を理由なくButton化しない
- すべてをPrimaryにしない
- 装飾目的で配置しない

### サイズ

TBD。

### 余白

TBD。

### 状態

- Default
- Hover
- Focus
- Active / Pressed
- Disabled：必要な場合
- Loading：必要性TBD

### Hover / Focus / Active

- Hoverは主情報を妨げない
- Focusは明確に表示する
- Active / Pressed状態が必要な場合は識別可能にする
- 状態表現を色だけに依存させない

### Responsive behavior

- Mobileでも操作可能なサイズを確保する
- Mobileでの幅変更ルールはTBD

### Accessibility requirements

- 明確なラベルを持つ
- キーボード操作可能にする
- Focus状態を表示する
- Disabledを使用する場合は状態を適切に伝える

---

## 5. Link

### 用途

ページ・ビュー間の移動。

### バリエーション

- Navigation link
- Inline / Text link

その他は必要性が確定した場合のみ追加する。

### 使用条件

移動・遷移を目的とする場合。

### 使用禁止条件

- 処理実行には使用しない
- 意味を曖昧にするButton風Linkを理由なく作らない

### サイズ

Typography ruleに従う。

### 余白

TBD。

### 状態

- Default
- Hover
- Focus
- Active / Current：該当する場合

### Hover / Focus / Active

- 通常テキストと識別可能にする
- Hoverだけに依存しない
- Focusを明確に表示する

### Responsive behavior

Navigation内ではNavigation仕様を優先する。

### Accessibility requirements

- リンク先が理解できるラベルを使用する
- キーボード操作可能にする

---

## 6. Form

### 用途

- 収支入力
- 確定した設定項目

### バリエーション

具体的なinput type・field構成はTBD。

必要性が確定したものだけ実装する。

### 使用条件

- 収支入力ページ
- 設定ページで具体項目が確定した場合

### 使用禁止条件

- 未確定の入力項目を推測で追加しない
- placeholderをLabel代わりにしない
- 不要な入力形式を事前実装しない

### サイズ

TBD。

### 余白

- Field間：TBD
- Label / Field間：TBD

### 状態

- Default
- Hover：必要なcontrolのみ
- Focus
- Filled
- Disabled：必要な場合
- Error：必要な場合
- Success：必要性TBD

### Hover / Focus / Active

- Focusを明確に表示する
- Errorを色だけで表現しない

### Responsive behavior

- Mobileでviewportからはみ出さない
- 横並びfieldを使用する場合のMobile変換方法はTBD

### Accessibility requirements

- 明示的Labelを持つ
- Error messageが存在する場合は対象fieldと関連付ける
- キーボード操作可能にする
- 意味に適したinput typeを使用する
- 必須項目を設定する場合は状態を明確に伝える

---

## 7. Card

### 用途

独立した情報グループを視覚的にまとめる必要がある場合のみ使用する。

### バリエーション

TBD。

### 使用条件

Card化することで情報の区切りが明確になる場合。

### 使用禁止条件

- 全要素をCard化しない
- Layoutを作るだけの目的で使用しない
- Bento Grid的な大量配置をしない
- SectionとCardを無意味に二重で囲まない

### サイズ

TBD。

### 余白

TBD。

### 状態

基本は静的。

Interactive Cardは必要性未確定のため事前実装しない。

### Hover / Focus / Active

静的Cardには不要。

### Responsive behavior

複数列を使用する場合の再配置・列数はTBD。

### Accessibility requirements

- 視覚的なContainerとして使うだけの場合は不要なARIAを付けない
- 内部の見出し階層を維持する

---

## 8. Section

### 用途

ページ内の主要な情報グループを分離する。

### バリエーション

原則1種類。特殊なSectionは必要性が確定した場合のみ追加する。

### 使用条件

情報の意味単位が変わる場合。

### 使用禁止条件

- 見た目の余白だけを目的としてSectionを増やさない
- 1要素ごとにSection化しない

### サイズ

コンテンツに従う。

### 余白

DESIGN_SYSTEMのSection spacing ruleに従う。具体値TBD。

### 状態

なし。

### Hover / Focus / Active

なし。

### Responsive behavior

- 画面サイズに応じたspacing具体値はTBD
- SITEMAPで確定した情報順序を維持する

### Accessibility requirements

- 必要に応じて見出しを持つ
- 論理的な見出し階層を維持する

---

## 9. Container

### 用途

全ページのメインコンテンツ幅と左右余白のルールを統一する。

### バリエーション

原則1種類。

必要性が確定しない限り複数のContainerを作らない。

### 使用条件

各ページの主要コンテンツ。

### 使用禁止条件

- ページごとに独自幅を作らない
- 不要な多重Containerを避ける

### サイズ

Max width：TBD。

### 余白

- Desktop：TBD
- Tablet：TBD
- Mobile：TBD

### 状態

なし。

### Hover / Focus / Active

なし。

### Responsive behavior

`07_RESPONSIVE_RULES.md` に従う。

### Accessibility requirements

特別な追加要件なし。

---

## 10. Image / Media

### 用途

写真は原則使用しない。

現時点で確定しているMedia：

- ロゴ：仮プレースホルダー
- 家計情報を表示するチャート

### バリエーション

チャート種別：TBD。

### 使用条件

仕様で確定した情報を表示する場合のみ使用する。

### 使用禁止条件

- ストック写真
- AI生成画像
- 装飾イラスト
- 意味のない3D画像
- 不要な背景画像

### サイズ

TBD。

### 余白

TBD。

### 状態

チャートのTooltip等は必要性TBD。

### Hover / Focus / Active

具体的interactionはTBD。

### Responsive behavior

- Containerから意図せずはみ出さない
- チャートの具体的なMobile表示方式はTBD

### Accessibility requirements

- 意味のある画像を追加する場合は適切な代替テキストを持つ
- チャートを色だけに依存して理解させない
- チャートの主要情報へ視覚表現以外でもアクセス可能にする

---

## 11. Modal / Drawer

現時点で必要性が確定していない。

事前実装しない。

Mobile NavigationでDrawerを採用するかどうかもTBD。

方式が確定するまで抽象コンポーネントを作らない。

---

## 12. Shared Page Title

### 用途

全5ページのページ名を表示する。

### バリエーション

原則1種類。

### 使用条件

全5ページ。

### 使用禁止条件

ページごとの装飾目的のvariantを追加しない。

### サイズ

TBD。

### 余白

TBD。

### 状態

なし。

### Hover / Focus / Active

なし。

### Responsive behavior

具体的なfont-size・spacing変更はTBD。

### Accessibility requirements

各ページの主要見出しとして適切なheadingを使用する。

---

## 13. Metric Display

ダッシュボードと月次レポートで主要指標の表示領域がSITEMAP上に存在する。

ただし、具体的な指標・UIがTBDのため、現時点では共通コンポーネントとして実装確定しない。

同一UIが複数ページで実際に発生すると確定した場合のみ共通化する。

詳細仕様：TBD。

---

## 14. Chart Container

ダッシュボードと月次レポートでグラフ領域がSITEMAP上に存在する。

ただし、グラフ種類・表示内容・UIがTBDのため、現時点では共通コンポーネントとして実装確定しない。

同一UIが複数ページで実際に発生すると確定した場合のみ共通化する。

詳細仕様：TBD。

---

## 15. 共通実装原則

- 再利用が実際に発生するものだけ共通化する
- 「将来使うかもしれない」を理由にcomponentを作らない
- variantを先に大量定義しない
- 同じ見た目でも意味が異なる場合は無理に共通化しない
- 同じ意味・同じUIが複数ページに現れることが確定した場合のみ抽象化する
- DESIGN_SYSTEMのtokenを使用し、component内部で任意値を増やさない
