# DESIGN_SYSTEM

本ファイルは、今回の試作実装で使用する確定Design Tokenを定義する。

参考サイトの役割は次のとおりとし、表層的な見た目はコピーしない。

- Stripe Dashboard：情報設計、重要数値の優先順位
- Linear：UI密度、整列、一貫性、控えめな装飾
- Apple：視覚階層、情報の引き算、明快さ

全体の方向性は「静かな会計面」とする。ライト基調、規則的な整列、数字中心の階層を採用し、Card、Shadow、Gradient等の装飾に依存しない。

## 1. Typography

Font family：

"Noto Sans JP", "Hiragino Sans", "Yu Gothic UI", sans-serif

実装ではNext.jsのFont機能によるセルフホストを優先する。

数字には以下を適用する。

- font-variant-numeric: tabular-nums lining-nums
- 金額、残高、日時、Chart軸の桁位置を揃える
- 数字と日本語本文で同じFont familyを使用する

使用する情報階層：

- 主要数値
- ページタイトル
- セクションタイトル
- 本文・項目
- Label / Navigation
- 補助情報

確定ルール：

- タイポグラフィで情報階層を作る
- 主要数値はページタイトルより強く表示する
- 巨大なHero見出しは使用しない
- 同じ役割のTextは全ページで同じTokenを使用する
- 数字の読みやすさと比較しやすさを優先する

## 2. Font Size Scale

| Role | Desktop | Tablet | Mobile |
|---|---:|---:|---:|
| Major metric | 36px / 40px | 32px / 38px | 30px / 36px |
| Page title | 28px / 36px | 26px / 34px | 24px / 32px |
| Section title | 18px / 26px | 18px / 26px | 18px / 26px |
| Body | 14px / 22px | 14px / 22px | 14px / 22px |
| Label / Navigation | 13px / 20px | 13px / 20px | 13px / 20px |
| Supporting / Caption | 12px / 18px | 12px / 18px | 12px / 18px |

ルール：

- ページ固有のfont-sizeを追加しない
- Page titleをHero見出しのように巨大化しない
- Major metricはtabular numeralsを使用する

## 3. Font Weight / Letter Spacing

| Role | Weight | Letter spacing |
|---|---:|---:|
| Body / Supporting | 400 | 0 |
| Label / Navigation | 500 | 0 |
| Page / Section heading | 600 | -0.01em |
| Major metric | 600 | -0.02em |

ルール：

- 700以上のweightを常用しない
- すべてのTextを強調weightにしない
- 強調はsize、weight、spacingを組み合わせて表現する

## 4. Line Height

| Role | Line height |
|---|---:|
| Major metric | Desktop 40px / Tablet 38px / Mobile 36px |
| Page title | Desktop 36px / Tablet 34px / Mobile 32px |
| Section title | 26px |
| Body | 22px |
| Label / Navigation | 20px |
| Supporting / Caption | 18px |

## 5. Spacing Scale

| Token | Value | Primary use |
|---|---:|---|
| space-1 | 4px | IconとLabel、補助文 |
| space-2 | 8px | 同一Component内部 |
| space-3 | 12px | Control内部、近接項目 |
| space-4 | 16px | Component間、Mobile Grid |
| space-5 | 20px | Tablet Grid、複合Component |
| space-6 | 24px | Desktop Grid、Component group |
| space-8 | 32px | MobileのSection間 |
| space-10 | 40px | TabletのSection間 |
| space-12 | 48px | DesktopのSection間 |
| space-16 | 64px | 主要領域間に限定 |

相対階層：

主要領域 48px〜64px
>
Section 32px〜48px
>
Component 16px〜24px
>
Component内部 4px〜12px

ルール：

- 任意のspacing値をページごとに追加しない
- 同じ構造には同じspacing tokenを使用する
- space-16を装飾的な空白として多用しない

## 6. Container Width

Main Content max width：1200px

ルール：

- 全ページで1つの基本Containerを共有する
- ページごとに独自の最大幅を追加しない
- Main Contentにはmin-width: 0を適用し、GridやChartによるoverflowを防ぐ
- ContainerはMain Content内で中央配置する

## 7. Viewport Padding

| Viewport | Horizontal padding |
|---|---:|
| Desktop | 32px |
| Tablet | 24px |
| Mobile | 16px |

ルール：

- 同一viewport区分では全ページで同じ値を使用する
- Mobileでコンテンツを画面端へ詰めすぎない
- Desktopで不必要に広い余白を作らない

## 8. Layout / Grid / Navigation Size

Desktopの基本構造：

Sidebar | Main Content

| Viewport | Grid | Gap | Navigation size |
|---|---|---:|---:|
| Desktop | 12 columns | 24px | Sidebar 240px |
| Tablet | 8 columns | 20px | Compact Sidebar 72px |
| Mobile | 4 columns | 16px | Top Header 56px |

ルール：

- Gridは情報をCard化する目的ではなく、数値、Chart、一覧の整列基準として使用する
- ページ間でColumn位置を揃える
- 不要なBento Gridを使用しない
- MobileではSidebarを表示しない

## 9. Colors

| Token | Value | Role |
|---|---|---|
| background | #F7F8FA | Page background |
| surface | #FFFFFF | Primary content surface |
| surface-subtle | #F1F4F7 | 選択行、Chart背景、補助的な情報領域 |
| text-primary | #1D2733 | 見出し、主要Text、主要数値 |
| text-secondary | #475467 | 本文、補助Label |
| text-muted | #667085 | Caption、日時、低優先度情報 |
| border-default | #DCE2E8 | 通常のDivider、Surface分離 |
| border-strong | #B8C2CC | Form、選択状態、強い区切り |
| accent | #275D8C | Primary action、Link、Focus |
| accent-hover | #1E4B73 | AccentのHover / Active |
| positive | #18794E | 収入、増加、Success |
| negative | #B42318 | 支出、減少、Error |
| neutral | #667085 | 変化なし、未分類、補助状態 |
| focus | #275D8C | Keyboard focus |

Contrast確認値：

- text-primary on surface：15.11:1
- text-secondary on surface：7.69:1
- text-muted on surface：4.97:1
- accent on surface：6.93:1
- positive on surface：5.41:1
- negative on surface：6.57:1

ルール：

- 必要以上に暗いUIにしない
- 色よりTypographyと配置による情報階層を優先する
- 装飾目的のGradientを使用しない
- Positive / Negativeは色だけで伝えず、符号、Label、Icon等を併用する

## 10. Border

- border-width-default：1px
- border-color-default：#DCE2E8
- border-color-strong：#B8C2CC
- border-default：1px solid #DCE2E8
- border-strong：1px solid #B8C2CC

ルール：

- 情報分離に必要な場合のみ使用する
- すべての要素を枠で囲まない
- ShadowとBorderを同時に過剰使用しない

## 11. Radius

- radius-sm：4px
- radius-md：6px
- radius-lg：10px

用途：

- radius-sm：小要素、Compact control
- radius-md：Button、Input、Select
- radius-lg：独立性が必要な大きな情報領域、Overlay

ルール：

- 大きな丸角を全面的に使用しない
- Pill型は必要性が確定した要素に限定する
- ページ固有のradiusを追加しない

## 12. Shadow

- shadow-subtle：0 1px 2px rgba(16, 24, 40, 0.06)
- shadow-overlay：0 12px 32px rgba(16, 24, 40, 0.14)

ルール：

- 通常のSectionや静的CardにはShadowを使用しない
- shadow-subtleは浮上が必要なMenu、Tooltip等に限定する
- shadow-overlayは実際にOverlayが必要な場合だけ使用する
- 情報階層はShadowより余白、Border、背景差を優先する

## 13. Button

Variant候補：

- Primary
- Secondary
- Tertiary / Text

必要性が確定したVariantだけを実装する。

| Property | Desktop / Tablet | Mobile |
|---|---:|---:|
| Height | 40px | 44px |
| Horizontal padding | 16px | 16px |
| Font | 14px / 20px / 500 | 14px / 20px / 500 |
| Radius | 6px | 6px |
| Icon gap | 8px | 8px |
| Icon-only target | 40px × 40px | 44px × 44px |

Vertical paddingは独立Tokenを持たず、Height、line-height、中央配置で制御する。

ルール：

- Primaryはページの主操作が確定した場合だけ使用する
- SecondaryはBorder、TertiaryはText主体とする
- すべてのButtonをPrimaryにしない
- Navigation目的にはLinkを使用する
- Pill形状にしない

## 14. Link

具体的なUnderlineの適用範囲とNavigation Link以外のLink用途は未確定。

確定済みルール：

- Colorはaccentを基本とする
- Hover / Activeではaccent-hoverを使用する
- 通常Textと常時識別可能にし、Hoverだけに依存しない
- Focus Styleは本ファイルのFocus Tokenを使用する
- 同種Linkは一貫した見た目にする

## 15. Form

具体的な入力項目、validation、保存方法は未確定。以下の寸法と状態ルールのみ確定する。

| Property | Value |
|---|---:|
| Input / Select height | 44px |
| Horizontal padding | 12px |
| Text | 14px / 22px / 400 |
| Label | 13px / 20px / 500 |
| Label–Control gap | 8px |
| Field gap | 16px |
| Group gap | 24px |
| Textarea min-height | 120px |
| Border | 1px solid #B8C2CC |
| Radius | 6px |
| Error message gap | 4px |

ルール：

- Labelを明示する
- PlaceholderだけをLabel代わりにしない
- Focus状態を明確にする
- Error状態を色だけに依存させない
- Mobileでもviewportからはみ出さない
- 未確定のFieldを推測で実装しない

## 16. Icon

Icon setと具体的なIcon用途は未確定。

確定済みルール：

- 意味のある場所だけに使用する
- 装飾目的で乱用しない
- 同じ意味には同じIconを使用する
- NavigationではText labelを優先する
- StrokeとSizeを統一する
- Icon-only ButtonはButtonのTarget sizeに従う

## 17. Focus

- focus-color：#275D8C
- focus-ring：0 0 0 2px #FFFFFF, 0 0 0 4px #275D8C
- Form focus border：#275D8C
- Ringと対象要素の視覚的な間隔：2px相当

ルール：

- Keyboard操作ではfocus-visibleを基本とする
- Focus Indicatorを無効化しない
- SurfaceとAccentの双方で視認できる二重Ringを使用する
- Error、Current、Selected等の状態とFocusを同時に識別可能にする

## 18. Motion

- duration-fast：120ms
- duration-default：180ms
- duration-slow：240ms
- easing-standard：cubic-bezier(0.2, 0, 0, 1)
- easing-emphasized：cubic-bezier(0.16, 1, 0.3, 1)

用途：

- duration-fast：Color、Border、Hover
- duration-default：Disclosure、Menu状態
- duration-slow：Mobile Menuの開閉に限定
- easing-emphasized：Menu表示等の限定的な移動

ルール：

- Hoverでの拡大を使用しない
- 常時Animationを使用しない
- Scroll演出を使用しない
- Chartの装飾Animationを使用しない
- prefers-reduced-motionでは移動、拡縮Animationを無効化し、Transitionを実質即時化する

## 19. Breakpoints / Navigation

- Mobile：768px未満
- Tablet：768px以上、1024px未満
- Desktop：1024px以上

Navigation：

- Desktop：240pxの左Sidebar
- Tablet：72pxのCompact左Sidebar
- Mobile：56pxのTop HeaderとMenu Button

Mobile Menuの実装は、非ModalのNavigation panelをTop Header直下で開閉する方式を基本とする。Menu Buttonはaria-expandedとaria-controlsを持ち、EscおよびLink選択で閉じる。

ルール：

- DesktopとTabletではMain Contentの左側にSidebarを配置する
- MobileではSidebarを表示しない
- Navigation項目の名称と順序を全ページで維持する
- Current Pageを視覚的にも支援技術でも識別可能にする
- すべてのNavigationをKeyboard操作可能にする

## 20. Implementation Rule

- 本ファイルのTokenをTailwind CSSのThemeへ一元登録する
- Component内部で任意値を追加しない
- Page固有Tokenを作らない
- 再利用が実際に発生したUIだけをComponent化する
- Copy、Data、Chart、Form項目、Settings等の未確定仕様は対応するTBD Placeholderを維持する
