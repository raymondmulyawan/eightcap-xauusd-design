# Handoff: Eightcap XAU/USD instrument page (Next.js + React)

## Overview
Upgraded Eightcap "Trade XAUUSD" instrument page (live: https://www.eightcap.com/en-au/traders/trade/xauusd/). Adds an SEO H1 + intro, a live price/trade panel with trader sentiment, three SEO content blocks and an FAQ accordion, while keeping every existing live-page section.

Target keywords: **XAUUSD price, XAUUSD live chart, trade XAUUSD, gold CFD trading**.

## About the design files
`Eightcap XAUUSD Page.dc.html` is a **design reference built in HTML** — not production code. Recreate it in the existing Eightcap project in the **"Intro vibe code"** folder using **Next.js (App Router) + React + TypeScript**, following that project's existing patterns (styling approach, component folders, fonts). If the folder has no established styling, use CSS Modules or Tailwind — whichever is already installed.

Open the HTML file in a browser to view it (keep `support.js` and `assets/` beside it). All copy and data live in the `renderVals()` object at the bottom of the file — lift it into `data/xauusd.ts`.

## Fidelity
**High-fidelity.** Recreate colours, type, spacing and copy exactly. Desktop is designed at **1440px**; build responsively (see Responsive).

## Suggested structure
```
app/traders/trade/xauusd/page.tsx        // server component, metadata, JSON-LD
components/instrument/
  SiteHeader.tsx  Hero.tsx  PriceSentimentPanel.tsx (client)
  SpecsTable.tsx  AboutInstrument.tsx  PriceDrivers.tsx  WhyTrade.tsx
  MarketDataTool/ (AiToolCard, Overview, Summary, NewsCarousel,
                   MarketCompanion, CalendarEvents, AssociatedAssets)
  FaqAccordion.tsx (client)  LearnTools.tsx  Disclaimer.tsx
  TradeNowMarquee.tsx  SiteFooter.tsx
data/xauusd.ts
public/images/xauusd/*   // from assets/
```
Use `next/image` for all images and `next/font/google` for Work Sans.

## Page order (top → bottom)
0 Header · 1 Hero · 2 Live price + sentiment · 3 More about XAUUSD (specs) · 4 What is XAU/USD? · 5 What moves the XAU/USD price? · 6 Why trade XAU/USD with Eightcap? · 7 AI-powered market data tool (grey container holding 8 Overview, 9 Summary, 10 Latest News, 11 Market Companion, 12 Calendar Events, 13 Associated Assets) · 14 FAQs · 15 Learn the tools of the trade · 16 Disclaimer · 17 Trade now marquee · 18 Footer

Horizontal content padding: **80px** (header/footer 48/64px). Sections 3–16 are separated by a 1px `#EBEBEB` top border; all on white.

## Sections

**0 Header** — white, `border-bottom: 3px solid #D5F1E1`, padding 20px 48px, flex space-between. Logo `eightcap-logo.png` 44px high. Right: search icon, globe + "EN" + chevron, Login (bg `#EBEBEB`), Trade now (bg `#694AFF`, white), both padding 14×18, radius 4, 17px/600; hamburger (2 bars 22×2px) 16px extra left. Use real icons (lucide or the project's icon set).

**1 Hero** — bg `#D5F1E1`, padding 28px 80px 48px. Breadcrumb 13px/500 `#1E3A2A` (Home / Markets / Commodities / XAU/USD — last item `#4E6B5A`), 48px below. **H1 "XAU/USD live price and chart"** 72px/700, letter-spacing −0.045em, line-height 0.95. Intro 19px/1.55, max-width 700px. Right-aligned pills "Commodity CFD", "Metals" (white, radius 999, 13px/600, 6×12).

**2 Live price + sentiment** — grid `1fr 400px`, gap 32, padding 40px 80px 24px.
- Left: price "4,070.59" 40px/700 + "USD" 16/600 + change "−17.68 (−0.43%)" red `#B42318`. TradingView chart (image now → replace with TradingView Advanced Chart widget, symbol `EIGHTCAP:XAUUSD`, client-only via `next/dynamic` ssr:false). Timeframe chips 15m/1H/4H/1D/1W/1M: 13/600, 8×12, radius 4; inactive `#EBEBEB`, active `#000`/white; default 1D; clicking sets widget interval.
- Right panel: 1px `#D9D9D9`, radius 4. Sell cell `#FDE8E8` (label `#A11D1D`), Buy cell `#D5F1E1` (label `#1B703F`), prices 22/700; "Spread 1.2" badge centred over the bottom edge. Low/High row 13px. "Trader sentiment" 14/700; 10px bar split long `#1B703F` / short `#D6453D`, 3px gap, radius 999; labels; sentence "**X%** of Eightcap client accounts are **long/short** XAU/USD" (uses majority side). Footer bg `#F6F6F6`: "Trade XAU/USD" (`#694AFF`, 16/600) and "Try on a free demo" (white, 1px border).
- Disclaimer 12px `#4A4A4A`.

**3 More about XAUUSD** — centred H2 48px; 18-row table (max-width 1000, cols `1fr 320px`, rows 14px padding, 1px `#E3E3E3`). Rows exactly as `specs` in the data.

**4 What is XAU/USD?** — grid `1fr 440px`, gap 80, padding 88/80. H2 48px, two 18px/1.65 paragraphs, CTAs Trade XAU/USD (violet) + Read gold news (`#EBEBEB`). Right: `#F6F6F6` key-facts list (6 rows, 15px, 1px `#DDDDDD`).

**5 What moves the XAU/USD price?** — H2 + 18px intro (max 820), 4-col cards bg `#F6F6F6`, radius 4, padding 28: number 14/700 `#1B703F`, title 20/600, body 15/1.6.

**6 Why trade XAU/USD with Eightcap?** — H2 56px + intro; CTAs Open an account / Compare accounts right-aligned. 4 cards bg `#D5F0E0`, padding 32/28/36, min-height 300: 56px white circle icon, stat 40/700, title 19/600, body 15.

**7–13 Market data tool** — H2 44px + 14px disclaimer. Grey container `#F6F6F6`, radius 8, padding 24, gap 24; inner cards white, 1px `#E3E3E3`, radius 8. Sub-headings 28/700.
- AI card: Gold title + "Au" badge, price, Commodity/Group/Unit row, "Opportunity" + Bearish pill, 5-segment gauge (active `#F0625A`, others `#E6E6E6`), "Ranking: #1 / 5 in Metals". AI chart image below.
- Overview: 10-row key/value list (cols 320px/1fr).
- Summary: 3 cards — Price Trend (Bearish, red), News Sentiment (Bullish, green `#3FBF6A`), Volatility (Neutral, `#F2C14E`), each with 5-segment gauge.
- Latest News: 4-col cards, square image (object-fit cover, top), currency tag pills; prev/next round buttons (make it a horizontal carousel).
- Market Companion: 4-col cards, image (484:300) + Impact/date row.
- Calendar Events: 5-col cards (date, ccy, title, Previous/Forecast).
- Associated Assets: 4-col cards (name, price, change coloured, Opportunity, sparkline — render a small SVG/line chart).
These are existing Eightcap data-tool widgets — wire to the same data source the live page uses.

**14 FAQs** — grid `400px 1fr`, gap 80. H2 "XAU/USD FAQs" 56px, intro, `#D5F1E1` support box. Accordion: rows 24px padding, 1px `#D9D9D9`, question 20/600, 32px round `#EBEBEB` +/− toggle. Single-open, first open by default. Emit **FAQPage JSON-LD** from the same data.

**15 Learn the tools** — grid `1fr 560px`; "Trader Toolkit" tag, H2 48px; image, copy, "Trader Toolkit →" link.

**16 Disclaimer** — H3 28px; three 13px notes (copy in file); "Connect with us" + social chips (`#D5F1E1`).

**17 Marquee** — two rows of "Trade now" 96px/700, −0.045em; animate as an infinite horizontal marquee (CSS, ~30s linear, rows opposite directions; respect `prefers-reduced-motion`). "Start trading" violet button.

**18 Footer** — bg `#000`, padding 64/64/80, gap 120. Grid `480px repeat(4,1fr)` gap 64: Company information (2 paragraphs, 17/1.6), Company / Go to / Legal / Follow us columns (heading `#8A8A8A` 17/500, links 17/600 white). Full-width white logo below (`eightcap-logo.png` with `filter: brightness(0) invert(1)`, or a white SVG if available).

## Interactions & state
- `PriceSentimentPanel` (client): `timeframe` (default "1D"); live bid/ask/high/low/sentiment via existing price feed / polling.
- `FaqAccordion` (client): `openIndex` (default 0; click toggles; one open at a time).
- News / Companion / Calendar / Assets: carousels with prev/next.
- Hover: links → `#694AFF`; buttons darken slightly; transitions 150ms ease.
- Sentiment `longPct` (design default 41) → short = 100 − long; sentence uses majority side.

## SEO
- `<title>`: "XAU/USD live price and chart | Trade gold CFDs | Eightcap"
- Single H1 (hero). Section H2s as listed. Meta description targeting the keywords above.
- JSON-LD: FAQPage + BreadcrumbList. Server-render all SEO copy (no client-only text).

## Responsive
≥1280: as designed. 768–1279: 4-col grids → 2, split layouts stack, hero H1 56px. <768: single column, padding 20px, H1 40px, H2 32px, trade panel below chart, footer columns 2-up.

## Design tokens
- Mint `#D5F1E1` (hero, panels) · Mint card `#D5F0E0` · Brand green `#36B66B` (logo) · Dark green text `#1B703F` · Bright green `#3EFE6A`
- Violet CTA `#694AFF` · Black `#000` · White `#FFF`
- Greys: `#F6F6F6` bg, `#EBEBEB` secondary button/borders, `#E3E3E3` card border, `#D9D9D9` lines, `#4A4A4A` muted text, `#8A8A8A` footer headings
- Red: `#B42318` text, `#D6453D` bar, `#FDE8E8` sell bg, `#F0625A` gauge
- Font: **Work Sans** 400/500/600/700/800. Headings 700, letter-spacing −0.045em, line-height ~1.
- Type scale: 72 / 56 / 48 / 44 / 40 / 28 / 22 / 20 / 19 / 18 / 17 / 16 / 15 / 14 / 13 / 12
- Spacing: section padding 88px (data sections 72px), side padding 80px, grid gaps 16 / 20 / 24 / 32 / 48 / 64 / 80
- Radius: 4 (buttons, cards), 8 (data-tool cards), 999 (pills). No shadows.

## Assets (`assets/` → `public/images/xauusd/`)
- `eightcap-logo.png` — official logo (supplied by client)
- `xau-tv-chart.png` — TradingView chart screenshot (placeholder for live widget)
- `xau-ai-chart.png` — AI tool chart screenshot (placeholder for live widget)
- `xau-news-1..3.png` — news card images (screenshots; include baked-in titles — swap for clean images from the CMS)
- `xau-comp-1..3.png` — Market Companion images (same note)
- `xau-learn-tools.png` — Trader Toolkit image

## Open items
- Live data: prices, spreads, sentiment, overview figures, news/calendar feeds are static values from a screenshot.
- Specs row "Leverage up to 1:500" is the global-entity value; ASIC retail gold leverage is capped at 20:1 — confirm with compliance for en-au.
- Replace text-glyph header icons with real icons.

## Files
- `Eightcap XAUUSD Page.dc.html` — full design (open in browser)
- `support.js` — runtime needed to view the HTML
- `assets/` — images
