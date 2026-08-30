# AGENTS.md

## Mission

Build this greenfield website to the highest practical standard of visual quality, usability, accessibility, responsiveness, and implementation quality.

This repository is for a new small-to-medium-sized website.

Do not expand the project beyond the approved scope.

## Source of truth

Before planning or implementing anything, read the relevant documents in `/docs`.

The source-of-truth documents are:

- `/docs/01_PROJECT_BRIEF.md`
- `/docs/02_SCOPE.md`
- `/docs/03_SITEMAP.md`
- `/docs/04_DESIGN_DIRECTION.md`
- `/docs/05_DESIGN_SYSTEM.md`
- `/docs/06_COMPONENT_RULES.md`
- `/docs/07_RESPONSIVE_RULES.md`
- `/docs/08_CONTENT_MAP.md`
- `/docs/09_ACCEPTANCE_CRITERIA.md`

Visual references are stored in `/references`.

Provided production assets are stored in `/public/assets`.

If this file conflicts with a more specific approved document in `/docs`, follow the specific document unless it violates Scope.

## Scope discipline

Do not:

- add pages not listed in the sitemap
- add features that were not requested
- invent future functionality
- generate or rewrite site copy
- invent facts, testimonials, statistics, company information, or product information
- create substitute content when production content is missing
- introduce dependencies without a clear need
- deviate from the approved design direction merely to make implementation easier

When content is missing, preserve the intended layout using clearly identifiable placeholders defined in the project documentation.

## Planning rule

For any non-trivial implementation, plan before coding.

The plan must reference the relevant source-of-truth documents and describe:

- routes
- page structure
- shared layout
- component boundaries
- design tokens
- responsive behavior
- implementation order
- validation method
- acceptance criteria

Do not begin implementation until the plan is internally consistent with the documentation.

## Frontend quality

Treat the supplied visual references as implementation constraints, not loose inspiration.

Prioritize:

1. visual hierarchy
2. typography
3. spacing rhythm
4. layout composition
5. responsive behavior
6. interaction clarity
7. accessibility
8. performance

Avoid generic AI-generated UI patterns when they are not justified by the design direction.

Do not overuse:

- cards
- pills
- gradients
- excessive border radius
- excessive shadows
- decorative containers
- unnecessary icons
- unnecessary animation

Prefer semantic HTML and native interactive elements.

## Design-system discipline

Use the tokens and rules defined in `/docs/05_DESIGN_SYSTEM.md`.

Do not create arbitrary one-off:

- colors
- spacing values
- font sizes
- radii
- shadows
- breakpoints

unless required by an approved visual reference and documented.

Shared visual patterns should become reusable components only when actual reuse is established.

Do not create abstractions for elements that are genuinely unique.

## Responsive implementation

The website must be intentionally designed for desktop, tablet, and mobile.

Do not treat mobile as a scaled-down desktop layout.

Follow `/docs/07_RESPONSIVE_RULES.md`.

Check representative viewport sizes in a real browser before considering a page complete.

## Accessibility

Target WCAG 2.2 Level AA where applicable, as defined in `/docs/09_ACCEPTANCE_CRITERIA.md`.

Use semantic HTML first.

Preserve keyboard operation, visible focus, proper labels, logical heading order, sufficient contrast, and reduced-motion preferences where applicable.

## Performance

Follow the performance and Core Web Vitals requirements in `/docs/09_ACCEPTANCE_CRITERIA.md`.

Avoid unnecessary client-side JavaScript.

Prefer appropriate image sizing and loading behavior when images are used.

Avoid layout shifts caused by media, fonts, or late-rendered UI.

## Verification

A page is not complete merely because it builds.

Before considering each implementation slice complete:

1. run the relevant checks
2. open the actual page in a browser
3. inspect desktop, tablet, and mobile layouts as applicable
4. compare the result with the approved design direction and available references
5. verify the applicable acceptance criteria
6. refine discrepancies before moving to the next slice

## Implementation style

Keep the implementation simple, legible, and conventional.

Prefer boring, well-supported technology over clever abstractions.

Keep components focused.

Do not introduce complexity for hypothetical future requirements.

## Completion rule

The website is complete only when all approved routes satisfy `/docs/09_ACCEPTANCE_CRITERIA.md`.

Do not interpret “complete” as permission to add anything outside the approved scope.

Unresolved TBD items must not be invented or silently treated as approved values.
