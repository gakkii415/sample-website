# ACCEPTANCE_CRITERIA

完成判定は原則 PASS / FAIL で行う。

TBD仕様に依存する項目は、該当仕様が確定するまで判定対象外とし、勝手に補完してPASS扱いしない。

## 1. 全ページ共通

### PASS

- SITEMAPで確定した5ページが存在する
- 各ページのURLと役割が `03_SITEMAP.md` と一致する
- 各ページのセクションがSITEMAPの指定順で存在する
- 共通UIが `06_COMPONENT_RULES.md` に従う
- DESIGN_DIRECTION / DESIGN_SYSTEMから理由なく逸脱した独自ルールを追加していない
- 意図しないhorizontal overflowがない
- UI操作を妨げる表示崩れ・重なり・欠落がない

上記を1項目でも満たさない場合はFAIL。

## 2. Visual Quality

### PASS

- Stripe Dashboard由来の情報設計、Linear由来のUI密度・一貫性、Apple由来の視覚階層・引き算という役割分担を維持している
- 同じ役割のコンポーネントは全ページで同じ視覚ルールを使用する
- 意味のないCard、Gradient、Shadow、大きなRadius、装飾Icon、Hero、画像を追加していない
- 全要素をCardで囲む構成になっていない
- デザイン目的だけのSectionを追加していない

以下は具体的Design System値確定後に判定する。

- 主情報と補助情報の具体的な視覚差
- 色、フォント、数値寸法に依存する視覚評価

## 3. Typography

### PASS

- 主要数値、ページタイトル、セクションタイトル、本文、補助情報に共通Typography ruleを使用している
- 同じ役割のテキストが全ページで同じtokenを使用している
- ページ固有のfont-sizeを理由なく追加していない
- Hero型の巨大見出しを使用していない
- すべてのテキストを強調weightにしていない

具体的font family / size / weight / line-heightに関する判定は値確定までTBD。

## 4. Spacing

### PASS

- 同じ構造に同じspacing ruleを使用している
- ページ固有の任意spacing値を理由なく追加していない
- 余白の相対階層が以下の順序を維持している

主要領域間
>
セクション間
>
コンポーネント間
>
コンポーネント内部

具体的spacing値に関する判定はTBD。

## 5. Layout

### PASS

Desktopで基本構造が以下になっている。

`Sidebar | Main Content`

さらに以下を満たす。

- 共通Container ruleを使用している
- ページごとに無関係なContainer widthを追加していない
- 同種コンテンツの整列ルールがページ間で一貫している
- SITEMAPの情報順序を維持している
- 不要なBento Gridを使用していない

具体的Container width / Grid / Gapは値確定までTBD。

## 6. Responsive

Desktop / Tablet / Mobileすべてを検証する。

### PASS

- 3区分すべてで5ページを閲覧できる
- 必要な操作要素を利用できる
- 意図しないhorizontal scrollがない
- テキスト、フォーム、チャートがviewport外へ意図せず欠落しない
- UI同士が意図せず重ならない
- MobileをDesktopの単純な縮小だけで処理していない
- Mobileでも情報の優先順位を維持している

具体的breakpoint、viewport pixel値、列数、左右余白に依存する判定はTBD。

## 7. Navigation

### PASS

- 5ページすべてへの導線がある
- Desktopでは左サイドナビゲーションを使用している
- Navigation項目の名称・順序が全ページで一致する
- 現在ページを視覚的に識別できる
- 現在ページを支援技術でも識別できる
- キーボードだけでNavigationを操作できる
- 未承認ページへのNavigation項目が存在しない

Mobile Navigationの具体方式はTBD。

## 8. Forms

具体的なfield構成はTBD。

確定したFormが実装された場合、以下を判定する。

### PASS

- 各入力controlに識別可能なLabelがある
- placeholderだけをLabelとして使用していない
- キーボードで操作できる
- Focus状態を視覚的に識別できる
- Error状態が存在する場合、色だけに依存していない
- Mobileで入力controlがviewportから意図せずはみ出さない
- 未確定の入力項目を推測で追加していない

具体的field / validation ruleはTBD。

## 9. Images / Media

### PASS

- 写真を使用していない
- ストック写真、AI生成画像、装飾3D、不要なイラストを使用していない
- ロゴ確定前は仮プレースホルダーを使用している
- 意味のある画像を将来追加する場合は適切な代替テキストを持つ
- Chartを実装する場合、色だけで主要な意味を伝えていない
- Chartの主要情報へ視覚表現以外でもアクセス可能である

具体的Chart仕様はTBD。

## 10. Accessibility

目標：WCAG 2.2 Level AA。

### PASS

実装内容に適用されるWCAG 2.2 Level AおよびLevel AAのSuccess Criteriaを満たす。

確認対象の代表例：

- Keyboard accessibility
- Focus visibility
- Contrast
- Labels
- Heading structure
- Link purpose
- Error identification
- Reflow
- Target size
- Reduced motion：該当する場合

上記リストは代表例であり、判定対象をこの項目だけに限定しない。

適用されるAまたはAA基準に未対応が確認された場合はFAIL。

## 11. Semantic HTML

### PASS

- ページの主要領域に適切なsemantic HTMLを使用している
- NavigationをNavigationとして意味付けしている
- ページ主要見出しを適切なheadingとして実装している
- 見出し階層が論理的である
- 操作実行にはButtonを使用している
- ページ遷移にはLinkを使用している
- Form controlとLabelを関連付けている
- `div`だけで意味のあるinteractive controlを再実装していない
- 不要なARIAをsemantic HTMLの代替として使用していない

## 12. Performance

### PASS

- 不要なclient-side JavaScriptを追加していない
- 使用していない大規模dependencyを導入していない
- 不要な画像・フォント・animationを読み込んでいない
- media等による予期しないlayout shiftがない
- 初期表示に不要なresourceが主要表示を著しく妨げていない

具体的bundle-size上限：TBD。

## 13. Core Web Vitals

Good基準：

| 指標 | PASS基準 |
|---|---:|
| LCP | 2.5秒以下 |
| INP | 200ms以下 |
| CLS | 0.1以下 |

実ユーザーデータが利用可能な場合は、Mobile / Desktopそれぞれで75パーセンタイルを基準に判定する。

新規サイトの初回公開前などfield dataが存在しない場合は、lab測定を事前品質ゲートとして使用する。

lab PASSは将来のfield PASSを保証するものではない。

## 14. Technical SEO

公開方式・認証方式・indexing方針がTBDのため、indexing / robots / canonical / metadataの具体判定はTBD。

公開アクセス可能なページに適用できる確定済み判定：

### PASS

- HTML document titleが存在する
- viewport設定が適切である
- heading構造が論理的である
- semantic HTMLを使用している
- 内部リンクが正常に機能する
- 存在しないURLを内部リンクしていない
- 画像を使用する場合はImage / Media方針に従う

SEO目的で未提供の本文・コピーを新規生成しない。

## 15. Browser Verification

Build成功だけでは完成扱いにしない。

### PASS

- 5ページすべてを実ブラウザで開いている
- Desktop / Tablet / Mobileの3区分で全5ページを確認している
- Navigationを実際に操作している
- Formの具体仕様が存在する場合は対象操作を実際に確認している
- overflow、重なり、欠落、意図しない折返しを確認している
- `04_DESIGN_DIRECTION.md` と実装結果を比較している
- 発見した不一致を修正した後に再確認している

具体的viewport pixel値：TBD。

## 16. Content Integrity

### PASS

`08_CONTENT_MAP.md` と実装を照合し、以下をすべて満たす。

- 提供されていない本文を生成していない
- 架空の事実を追加していない
- 架空の本番収支データを追加していない
- 未決定コピーを `[TBD_COPY]` として扱っている
- 未決定画像を `[TBD_IMAGE]` として扱っている
- 未決定CTAを `[TBD_CTA]` として扱っている
- その他TBDもCONTENT_MAPのplaceholder ruleを維持している
- 提供済みコンテンツを無断でリライトしていない

未承認コンテンツの補完が1件でもある場合はFAIL。

## 17. Scope Compliance

対象ページ：

- `/`
- `/transactions`
- `/transactions/new`
- `/reports`
- `/settings`

### PASS

- 上記以外の未承認ページを追加していない
- 未承認機能を追加していない
- 将来用途だけを理由にした機能・componentを実装していない
- Footerを必要性未確定のまま追加していない
- Modal / Drawerを必要性未確定のまま追加していない
- CONTENT_MAPにないコンテンツを追加していない
- SITEMAPのページ役割を変更していない
- Stripe / Linear / Appleのデザインそのものをコピーしていない

スコープ外実装が1件でも存在する場合はFAIL。

## 18. Definition of Done

以下の判定可能な項目をすべてPASSした時点で完成とする。

- [ ] 全ページ共通
- [ ] Visual Quality
- [ ] Typography
- [ ] Spacing
- [ ] Layout
- [ ] Responsive
- [ ] Navigation
- [ ] Forms：該当する確定仕様がある場合
- [ ] Images / Media
- [ ] WCAG 2.2 AA
- [ ] Semantic HTML
- [ ] Performance
- [ ] Core Web Vitals
- [ ] Technical SEO：確定済み適用範囲
- [ ] Browser Verification
- [ ] Content Integrity
- [ ] Scope Compliance

TBDに依存する項目は勝手に確定せず、該当仕様が確定してから判定する。
