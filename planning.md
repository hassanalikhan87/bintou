Theme Revamp Plan (Adorn “Precious” Inspired)
============================================

Goal
- Elevate the entire theme with an elegant, jewelry-inspired aesthetic: airy layouts, warm neutrals, refined typography, and subtle motion, while keeping Dawn’s performance/accessibility strengths.

Guiding Principles
- Preserve Dawn’s semantic, server-rendered Liquid approach; progressive enhancement only where it adds value.
- Maintain responsiveness and accessibility: clear focus states, proper heading hierarchy, aria labels for interactive elements.
- Keep performance in check: lazy-load media, defer non-critical JS, avoid excessive motion.

Phase 1 — Foundations (Tokens, Type, Base Styles) [IN PROGRESS]
- [x] Define design tokens: neutral palette + accent, spacing scale, shadow levels; map to color_scheme options. (Implemented in `assets/base.css` and `config/settings_schema.json`)
- [x] Typography: introduce serif display for headings and a clean sans for body/UI. (Added Work Sans and Playfair Display via Google Fonts in `base.css`)
- [ ] Buttons/links: refine hover/focus, thinner outlines or pill states; update global base styles to match palette.
- [ ] Update translation keys if new UI text appears.

Phase 2 — Header, Navigation, Search
- Refactor sections/header.liquid into utility bar + centered logo + balanced nav; maintain mega/drawer variants.
- Add search trigger/modal with predictive search support and “/” keyboard focus; slide-down search on mobile.
- Sticky behavior: shrink-on-scroll logo, subtle shadow/border; hide-on-scroll-down/reveal-on-up if feasible.
- Consolidate localization/account popovers; persistent cart bubble with count.
- Ensure mobile drawer locks body scroll and mirrors utility items.

Phase 3 — Homepage Experience [IN PROGRESS]
- [x] Hero: split layout or carousel with soft pagination, parallax mask option; concise headline + CTA. (Created `sections/hero-carousel.liquid` with split layout option and custom styling)
- [ ] Feature grids: staggered/masonry mix of lifestyle + product cards; hover alt image, badges (bestseller/new).
- Brand story + trust: craftsmanship highlights, sustainability badges, press logos.
- Product spotlight: curated set with swatches and quick add.
- Newsletter: elegant form with incentive and inline consent text.

Phase 4 — Collections & Search Results
- Filters: desktop left rail, mobile drawer; applied filter pills with clear reset.
- Grid: airy cards, hover alt image, quick add, price/compare; sort and per-page controls.
- Collection banner optional with breadcrumb and overlay.

Phase 5 — Product Detail (PDP)
- Media: stacked gallery with sticky summary; side thumbs or single column; smooth zoom; video slot.
- Info stack: materials/care badges, size guide modal, shipping/returns accordion, trust messaging.
- Purchase area: clear variant picker, inventory/lead time, add-to-cart feedback; complementary products/upsells styled to match.
- Social proof: reviews summary, UGC carousel slot, “pairs well with” recommendations.

Phase 6 — Cart Drawer/Page & Checkout Prep
- Cart drawer: thumb, variant chips, delivery estimate, coupon input, gift options toggles; mini-order summary; upsell slot.
- Empty state with inviting CTA.
- Notes and shipping estimates if needed.

Phase 7 — Footer & Content Pages
- Footer: minimal columns, newsletter, store info, social row; slim dividers; subdued payment/badge strip.
- About/story template with image + text blocks, timeline/values grid.
- Blog/article layout with lead image, pull quotes, related posts, and subscription prompt.

Phase 8 — QA, Performance, Settings Cleanup
- Verify desktop/mobile for nav, search, cart, localization, sticky behavior, and forms.
- Optimize media sizes; defer non-critical scripts; ensure Lighthouse-friendly patterns.
- Clean settings schema: add new options (search modal, utility bar, borders/shadows, hero options) and deprecate unused ones; update locales.
- Document new/changed settings and any migration notes.

Execution Notes
- Update/add CSS in assets (component header/nav/search/cart/footer/card/etc.) aligned to tokens.
- Add minimal JS tweaks for scroll behavior, search trigger, body lock, and popovers; reuse existing Dawn patterns where possible.
- Keep commits/changes scoped per phase to ease review and testing.

Brand Tokens (from provided brand book)
- Primary colors: Ivory Dust `#F9F2E8` (base background), Heirloom Saffron `#A9723E` (primary logo/CTA), Sacred Garnet `#813235` (accent for CTAs, stickers).
- Accent colors: Dust Rose `#C9A6A0`, Jewel Smoke `#B2B6B7`, Ash Plum `#564B53`, Indigo Prayer `#2B3A4F`, Aqeeq Green `#035851`, Shadowed Wine `#74364D`, Clay Ember `#994A3A`.
- Typography: Serif display (FreightDisp Pro per brand book; if unavailable on web, use a close licensed-friendly serif like Playfair/Wotfard/Libre Caslon as fallback). Sans for body/UI (Work Sans per brand book; can fall back to “Inter → system sans” until custom webfont is added).
- Voice reminders for copy: warm, poetic, grounded; emphasize legacy, ritual, story; avoid loud/salesy language.

Phase 2 — Header/Nav/Search (detailed plan)
- Layout targets (desktop): centered logo; balanced nav flanking logo; right-aligned utility bar (search trigger, account if enabled, cart bubble with count) atop/inline as needed; thin top border + shadow on scroll; Ivory Dust base with Saffron accents and Garnet sparingly (hover/focus).
- Layout targets (mobile): centered logo; hamburger left, cart right; slide-down search tray; drawer menu with body lock; utility items mirrored inside drawer; maintain color tokens.
- Markup updates (`sections/header.liquid` & snippets): reorganize DOM into utility bar + main nav shell; add search trigger/modal; compact localization/account triggers; ensure mega-menu/drawer options remain.
- Schema changes (`sections/header.liquid` schema): add toggles for search modal, top border/shadow, utility bar enable, mobile search tray; default color scheme stays theme-driven but map to Ivory Dust/Saffron/Garnet guidance.
- Styling (`assets/component-*`): extend header/nav/search CSS for spacing, thin dividers, hover/focus states, sticky shadow, logo shrink; mobile drawer/tray polish; use color tokens for backgrounds/borders/interactive states; adjust button/link styles to match luxe tone.
- Behavior (`assets/global.js` or new header script): scroll-based shrink/reveal; search trigger with `/` focus; body lock on drawer open; accessible popover toggles for localization/account; reuse predictive search when enabled.
- Rollout order: 1) adjust schema and header markup, 2) add CSS for new structure/states, 3) wire JS behaviors, 4) QA desktop/mobile for nav/search/cart/localization/sticky.
