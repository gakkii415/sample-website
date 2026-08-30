# IMPLEMENTATION_PLAN

本ファイルは、家計簿Webアプリの試作実装における最終実装計画を定義する。

アプリ本体の実装は本ファイルの承認後に開始する。実装は一括で行わず、小さく検証可能な単位に分割し、Dashboard MVPのブラウザレビュー後に停止する。

## 1. Source of Truth

優先順位：

1. AGENTS.md
2. docs/01_PROJECT_BRIEF.md
3. docs/02_SCOPE.md
4. docs/03_SITEMAP.md
5. docs/04_DESIGN_DIRECTION.md
6. docs/05_DESIGN_SYSTEM.md
7. docs/06_COMPONENT_RULES.md
8. docs/07_RESPONSIVE_RULES.md
9. docs/08_CONTENT_MAP.md
10. docs/09_ACCEPTANCE_CRITERIA.md
11. 本ファイル

Visual references：

- references/stripe.JPG：情報設計、重要数値の優先順位
- references/linear.JPG：UI密度、整列、一貫性
- references/apple.JPG：視覚階層、情報の引き算

Provided production assets：

- public/assets/には現時点で実装用素材が存在しない
- Logoは[TBD_LOGO]を使用する
- 写真、Stock image、AI生成画像は追加しない

## 2. Scope

対象は個人向け家計簿WebアプリのFrontend試作である。

対象ページ：

- Dashboard
- Transactions
- New Transaction
- Reports
- Settings

実装しないもの：

- 未承認ページ
- Backend
- Database
- Authentication
- Payment
- Analytics
- 本番データ保存
- 未確定のForm項目
- 未確定のChart仕様
- 未確定のSettings項目
- Footer
- 未承認のModal / Drawer
- 架空のCopy、Data、事実、収支情報

## 3. Technical Architecture

| Item | Confirmed value |
|---|---|
| Framework | Next.js |
| Routing | App Router |
| Language | TypeScript |
| Styling | Tailwind CSS |
| Package manager | pnpm |
| Rendering | Server Componentsを基本とする |
| Client Components | Browser stateまたはinteractionが必要な最小範囲のみ |
| Deployment | Vercel |
| Backend | 今回は実装しない |
| Data persistence | 未確定のため実装しない |
| Chart library | Chart仕様確定まで導入しない |
| Icon library | Icon set確定まで導入しない |
| External runtime JavaScript | 必要最小限にする |

Architecture rule：

- Route page、Page Header、Section、静的なLayoutはServer Componentsとする
- Current routeの判定とMobile Menuの開閉は、小さなNavigation Client Componentへ限定する
- Tailwind ThemeをDesign Tokenの単一Source of Truthとする
- Component内で任意のColor、Spacing、Font Size、Radius、Shadow、Breakpointを追加しない
- Server ComponentsからClient Componentへ渡すPropsはSerializableな値に限定する
- 将来用途だけを理由に状態管理LibraryやData layerを追加しない

## 4. Routes

以下を正式Routeとして確定する。

| Route | Page | Role |
|---|---|---|
| / | Dashboard | 現在の家計状況を俯瞰する |
| /transactions | Transactions | 登録された収入・支出を確認する |
| /transactions/new | New Transaction | 収入または支出を入力する |
| /reports | Reports | 月単位で家計状況を確認する |
| /settings | Settings | 家計簿Webアプリの設定を扱う |

Navigation項目は上記順序を全ページで維持する。

上記以外の公開Routeは追加しない。存在しないRouteへの内部Linkも追加しない。

## 5. Global Layout

Desktop：

Sidebar 240px | Main Content

Tablet：

Compact Sidebar 72px | Main Content

Mobile：

Top Header 56px
Main Content

Global layout rule：

- Main Contentはmax-width 1200pxの共通Containerを使用する
- Viewport paddingはDesktop 32px、Tablet 24px、Mobile 16pxとする
- Main Contentにはmin-width: 0を適用する
- Page内はPage Headerの後にSitemapで指定されたSectionを順番どおり配置する
- Footerは作成しない
- 全ページでNavigationの位置、名称、順序を変更しない

## 6. Responsive / Navigation

Breakpoints：

- Mobile：768px未満
- Tablet：768px以上、1024px未満
- Desktop：1024px以上

Grid：

| Viewport | Columns | Gap |
|---|---:|---:|
| Mobile | 4 | 16px |
| Tablet | 8 | 20px |
| Desktop | 12 | 24px |

Navigation：

- Desktop：240pxの左Sidebar。Text Labelを省略しない
- Tablet：72pxのCompact左Sidebar。5 Routeへの導線を維持する
- Mobile：56pxのTop HeaderとMenu Button
- Mobile Menu ButtonはNavigation listを開閉する
- Mobile Navigationは非Modal panelとしてTop Header直下に表示する
- Menu Buttonはaria-expandedとaria-controlsを持つ
- Current Pageは視覚状態とaria-current="page"の両方で示す
- NavigationはKeyboardだけで操作可能にする
- EscおよびNavigation Link選択後にMobile Menuを閉じる

Responsive rule：

- MobileをDesktopの単純な縮小として実装しない
- SitemapのSection順と情報優先順位を維持する
- Text、Navigation、Form、Chartをviewport外へ欠落させない
- 意図しないhorizontal scrollやUIの重なりを発生させない
- Breakpoint境界の767px、768px、1023px、1024pxを実ブラウザで確認する

## 7. Confirmed Design System

詳細と実装上の正本はdocs/05_DESIGN_SYSTEM.mdとする。

### Typography

- Font family："Noto Sans JP", "Hiragino Sans", "Yu Gothic UI", sans-serif
- 数字：tabular-nums lining-nums
- Major metric：Desktop 36px / Tablet 32px / Mobile 30px
- Page title：Desktop 28px / Tablet 26px / Mobile 24px
- Section title：18px
- Body：14px
- Label / Navigation：13px
- Supporting / Caption：12px
- Body weight：400
- Label / Navigation weight：500
- Heading / Major metric weight：600

### Spacing

- Scale：4、8、12、16、20、24、32、40、48、64px
- 主要領域：48〜64px
- Section：32〜48px
- Component：16〜24px
- Component内部：4〜12px

### Colors

- background：#F7F8FA
- surface：#FFFFFF
- surface-subtle：#F1F4F7
- text-primary：#1D2733
- text-secondary：#475467
- text-muted：#667085
- border-default：#DCE2E8
- border-strong：#B8C2CC
- accent：#275D8C
- accent-hover：#1E4B73
- positive：#18794E
- negative：#B42318
- neutral：#667085
- focus：#275D8C

### Border / Radius / Shadow

- Border：1px
- Radius：4px、6px、10px
- Static SectionやCardにはShadowを使用しない
- shadow-subtle：0 1px 2px rgba(16, 24, 40, 0.06)
- shadow-overlay：0 12px 32px rgba(16, 24, 40, 0.14)

### Controls

- Button height：Desktop / Tablet 40px、Mobile 44px
- Form control height：44px
- Button / Form radius：6px
- Button horizontal padding：16px
- Form horizontal padding：12px
- Focus ring：白2px相当とaccent 2px相当の二重Ring

### Motion

- Fast：120ms
- Default：180ms
- Slow：240ms
- Standard easing：cubic-bezier(0.2, 0, 0, 1)
- Emphasized easing：cubic-bezier(0.16, 1, 0.3, 1)
- prefers-reduced-motionでは移動、拡縮Animationを無効化する

Design direction rule：

- Stripe、Linear、Appleの表面的な見た目を混在させない
- 全要素をCard化しない
- Gradient、巨大見出し、大きなRadius、強いShadow、装飾Iconを追加しない
- Typography、整列、余白、数字によって品質を作る

## 8. Shared Components

最初から共通化するもの：

- AppShell
- Container
- Navigation
- PageHeader
- SharedPageTitle
- Section
- Link

必要性が確定した場合のみ追加するもの：

- Button variant
- Form control
- Error message

先行抽象化しないもの：

- Metric Display
- Chart Container
- Card
- Modal
- Drawer
- Tooltip
- Loading state
- Empty stateの専用Component

Metric DisplayとChart Containerは、DashboardとReportsで同じ意味、同じUIが実際に発生すると確定した場合だけ共通化する。

## 9. Page Structure

### Dashboard /

代表ページおよび最初のMVPとする。

Section order：

1. Page Header
2. 主要な家計指標
3. 家計推移グラフ
4. 収支情報

Content：

- Copy：[TBD_COPY]
- CTA：[TBD_CTA]
- Metric data：[TBD_DATA]
- Chart data：[TBD_CHART_DATA]

具体的な指標、Chart type、実データを推測しない。

### Transactions /transactions

Section order：

1. Page Header
2. 収支一覧

Content：

- Copy：[TBD_COPY]
- CTA：[TBD_CTA]
- Data：[TBD_DATA]

一覧項目、Filter、Sort、操作を推測しない。

### New Transaction /transactions/new

Section order：

1. Page Header
2. 収支入力Form

Content：

- Copy：[TBD_COPY]
- CTA：[TBD_CTA]
- Fields：[TBD_FORM_FIELDS]

具体的な入力項目、Category、Validation、保存方法を推測しない。

### Reports /reports

Section order：

1. Page Header
2. 月次主要指標
3. 月次グラフ
4. その他の月次情報

Content：

- Copy：[TBD_COPY]
- CTA：[TBD_CTA]
- Metric data：[TBD_DATA]
- Chart data：[TBD_CHART_DATA]

具体的な月次指標、Chart type、比較方法を推測しない。

### Settings /settings

Section order：

1. Page Header
2. 設定項目

Content：

- Copy：[TBD_COPY]
- CTA：[TBD_CTA]
- Settings：[TBD_SETTINGS]

具体的な設定項目を推測しない。

## 10. Content Integrity

未決定内容にはdocs/08_CONTENT_MAP.mdのPlaceholderをそのまま使用する。

- [TBD_COPY]
- [TBD_IMAGE]
- [TBD_CTA]
- [TBD_DATA]
- [TBD_CHART_DATA]
- [TBD_FORM_FIELDS]
- [TBD_SETTINGS]
- [TBD_LOGO]
- [TBD_ICON]
- [TBD_COLOR]
- [TBD_FONT]

今回確定したColorとFontについて、実装上はdocs/05_DESIGN_SYSTEM.mdの値を使用する。ContentとしてBrand Color名やFont名を表示する必要がある場合は、Content仕様が確定するまでPlaceholderを維持する。

架空の本番収支データ、説明文、CTA Label、Category、Settingsを作成しない。

## 11. Implementation Order

### Phase 0：Documentation

- docs/05_DESIGN_SYSTEM.mdへ確定Tokenを反映する
- docs/10_IMPLEMENTATION_PLAN.mdを作成する
- アプリ本体は変更しない

### Phase 1：Foundation

小さな単位：

1. Next.js、TypeScript、Tailwind CSS、pnpmの最小構成
2. App Routerの5 Route
3. Build、Type check、Lint、Development command
4. Vercelで解釈可能な標準構成

確認：

- pnpm install
- pnpm build
- Type check
- Lint
- 5 Routeの直接表示と再読込
- Browser consoleにErrorがないこと

### Phase 2：Design System

小さな単位：

1. FontとTypography
2. Color
3. SpacingとLayout
4. Border、Radius、Shadow
5. FocusとMotion
6. Button / Formの基礎Token

確認：

- docs/05_DESIGN_SYSTEM.mdとのToken照合
- Page固有値が存在しないこと
- Contrast
- Focus visibility
- Reduced motion

### Phase 3：Global Layout

小さな単位：

1. Container
2. PageHeader / SharedPageTitle
3. Desktop Sidebar
4. Tablet Compact Sidebar
5. Mobile Top Header / Menu Button
6. Current Page状態

確認：

- Navigationの名称と順序
- aria-current
- Keyboard操作
- Sidebar / Main Contentの整列
- Footerや未承認Routeが存在しないこと

### Phase 4：Dashboard MVP

小さな単位：

1. Page Header
2. 主要な家計指標のPlaceholder構造
3. 家計推移グラフのPlaceholder構造
4. 収支情報のPlaceholder構造
5. Desktop確認
6. Tablet確認
7. Mobile確認
8. Accessibility確認

Dashboard MVP完了後は必ず停止し、Browser screenshotとAcceptance Criteriaの結果を提示してレビューを待つ。

残りページ、UI polish、Backendへ自動的に進まない。

### Phase 5：Shared Components

Dashboardと次のPageで実際の再利用が確認できたUIだけを抽出する。

確認：

- 抽出前後の視覚差分
- 全利用箇所のFocusとResponsive状態
- 不要なVariantが存在しないこと

### Phase 6：Remaining Pages

実装順：

1. Transactions
2. New Transaction
3. Reports
4. Settings

各Pageを個別に実装、Build、Browser確認、Reviewする。

### Phase 7：Responsive Refinement

- 5 Page × 3 Viewportを確認する
- Breakpoint境界を確認する
- Horizontal overflow、重なり、欠落、意図しない折返しを修正する
- Mobileで情報優先順位が維持されていることを確認する

### Phase 8：Accessibility / Performance

Accessibility：

- Keyboard
- Focus
- Heading hierarchy
- Semantic landmarks
- aria-current
- Labels
- Error identification
- Reflow
- Target size
- Contrast
- Reduced motion

Performance：

- 不要なClient Componentを削減する
- 未使用Dependencyを追加しない
- Layout shiftを防ぐ
- Font loadingを確認する
- Lighthouse等のlab測定を実施する

Quality gate：

- LCP 2.5秒以下
- INP 200ms以下
- CLS 0.1以下

### Phase 9：Preview Verification

Vercel Previewで以下を確認する。

- 5 Pageの直接URL
- Navigation
- 再読込
- Desktop / Tablet / Mobile
- Content Integrity
- Accessibility
- Browser console
- Core Web Vitalsのlab測定
- 発見事項修正後の再確認

## 12. Browser Verification Matrix

代表Viewport：

- Mobile：390px × 844px
- Tablet：834px × 1112px
- Desktop：1440px × 900px

Boundary：

- 767px
- 768px
- 1023px
- 1024px

各Implementation sliceで確認するもの：

| Phase | Browser verification |
|---|---|
| Foundation | Route、直接表示、再読込、Title、Viewport、Console |
| Design System | Typography、Color、Spacing、Focus、Contrast |
| Global Layout | Sidebar、Header、Navigation、Current state |
| Dashboard MVP | Section order、Hierarchy、Placeholder、Overflow |
| Shared Components | 抽出前後のVisual difference |
| Remaining Pages | URL、Role、Section order、Content Map |
| Responsive | 3区分、Boundary、Continuous resize |
| Accessibility | Keyboard、Focus、Semantics、Reflow |
| Performance | Lighthouse、Font、Client JS、Layout shift |
| Preview | 5 Page × 3 Viewportの全15組合せ |

Build成功だけをPage完了条件にしない。

## 13. Acceptance Criteria Mapping

| Acceptance Criteria | Implementation / Verification |
|---|---|
| 全ページ共通 / Scope | Routes、Page Structure、各Page Review |
| Visual Quality | Design System、Dashboard Review、Reference比較 |
| Typography | docs/05 Token、Page固有値の禁止 |
| Spacing | Spacing scale、共通Section rule |
| Layout | AppShell、Container、Grid |
| Responsive | 3 Viewport、Breakpoint Boundary |
| Navigation | 5 Route、Current state、Keyboard |
| Forms | Field仕様確定後に適用 |
| Images / Media | 写真不使用、Chart仕様確定後に適用 |
| Accessibility | 全Phase＋専用Review |
| Semantic HTML | Server ComponentとNative elementを基本とする |
| Performance | Server Components、最小Client JS、Lighthouse |
| Core Web Vitals | Lab quality gate、公開後はField data |
| Technical SEO | Title、Viewport、Heading、内部Link。Indexingは未確定 |
| Browser Verification | 全15組合せ |
| Content Integrity | docs/08 Placeholder照合 |
| Scope Compliance | 未承認Page、機能、Contentの禁止 |
| Definition of Done | 判定可能項目をすべてPASS |

TBD仕様に依存する項目は、確定前にPASS扱いしない。

## 14. Remaining TBD

構造実装を妨げないが、該当機能の完成を妨げる未決定事項：

- App name
- Logo
- 各画面のCopy
- CTA Labelと優先順位
- Dashboardの具体的指標
- Transactionsの一覧項目と操作
- New TransactionのField、Category、Validation
- Reportsの指標、Chart、比較内容
- Settings項目
- 実際の収支Data
- Chart library
- Icon set
- Data persistence
- Authentication
- Currency、Language、Locale
- Indexing、robots、canonical
- Field dataによるCore Web Vitals

これらを推測して実装しない。該当箇所ではdocs/08_CONTENT_MAP.mdのPlaceholderを維持する。

## 15. Implementation Risks

- 未確定Dataを仮作成するとContent Integrity違反になる
- DashboardでComponent抽象化を急ぐと不要なVariantが発生する
- Client Componentを広げるとServer Components基本方針とPerformance要件を損なう
- Compact SidebarでTextを完全に失うとNavigationの理解とAccessibilityを損なう
- Mobile MenuのFocus、aria-expanded、閉じる操作が不足するとNavigation要件を満たさない
- 全要素のCard化、強いShadow、大きなRadiusはDesign Directionから逸脱する
- Font payloadが大きい場合はLCPに影響するため、実装時に読み込み範囲を検証する
- Placeholderを本番Contentのように見せるとTBDが誤認される

## 16. Completion Gate

各Phaseは次を満たした場合のみ完了とする。

1. 対象変更がBuildと検査を通過する
2. 実ブラウザで対象Viewportを確認する
3. 適用されるAcceptance Criteriaを確認する
4. Content Integrityを確認する
5. 発見した不一致を修正して再確認する
6. 未判定のTBDを記録する

Dashboard MVP完了後は、ユーザーの明示的な承認があるまでPhase 5以降を開始しない。
