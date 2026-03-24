# wideholy-embed

[![npm](https://img.shields.io/npm/v/wideholy-embed)](https://www.npmjs.com/package/wideholy-embed)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)](https://www.npmjs.com/package/wideholy-embed)
[![Size](https://img.shields.io/badge/size-~5KB-green)](https://bundlephobia.com/package/wideholy-embed)

Embed WideHoly multi-religion scripture widgets on any website. **Zero dependencies**, Shadow DOM style isolation, 3 built-in themes (light, dark, sepia), and automatic daily verse updates. Each widget includes a "Powered by WideHoly" backlink.

WideHoly is the unified API for **5 world religions** — Christianity (Bible), Islam (Quran), Judaism (Torah/Tanakh), Hinduism (Bhagavad Gita), and Buddhism (Pali Canon Sutras) — covering **236,000+ scripture records**, cross-religion concept comparison, and a single API endpoint for all sites. Each religion is also available as a standalone package (widebible-embed, widequran-embed, etc.).

> **Try the interactive widget builder at [widget.wideholy.com](https://widget.wideholy.com)**

<p align="center">
  <img src="demo.gif" alt="wideholy-embed demo — multi-religion scripture widget showing Bible, Quran, Torah, Gita, and Buddhist Sutra passages side by side" width="800">
</p>

## Table of Contents

- [Quick Start](#quick-start)
- [What You Can Do](#what-you-can-do)
  - [Verse Card — Single Scripture Passage Display](#verse-card--single-scripture-passage-display)
  - [Chapter Card — Full Chapter or Surah](#chapter-card--full-chapter-or-surah)
  - [Comparison Card — Cross-Religion Concept Comparison](#comparison-card--cross-religion-concept-comparison)
  - [Verse of the Day — Auto-Updating Daily Widget](#verse-of-the-day--auto-updating-daily-widget)
  - [Search Box — Cross-Religion Scripture Search](#search-box--cross-religion-scripture-search)
- [Supported Religions and References](#supported-religions-and-references)
- [Widget Options](#widget-options)
- [Themes](#themes)
- [CDN Options](#cdn-options)
- [Technical Details](#technical-details)
- [Learn More About World Scriptures](#learn-more-about-world-scriptures)
- [WideHoly Scripture Family](#wideholy-scripture-family)
- [License](#license)

## Quick Start

```html
<!-- Bible verse (Christianity) -->
<div data-wideholy="verse" data-ref="John 3:16" data-religion="bible" data-theme="light"></div>

<!-- Quran ayah (Islam) -->
<div data-wideholy="verse" data-ref="2:255" data-religion="quran" data-theme="light"></div>

<!-- Load the embed script once, anywhere on the page -->
<script src="https://cdn.jsdelivr.net/npm/wideholy-embed@1/dist/embed.min.js"></script>
```

That's it. The widget loads, fetches from the appropriate WideHoly API endpoint, and renders with full style isolation. One script tag. Five religions.

## What You Can Do

WideHoly brings together the scripture traditions of 5 world religions under a unified embed API. Whether you're building an interfaith study platform, a comparative religion tool, a meditation app, or a general spirituality website, wideholy-embed lets you display authentic scripture from any tradition with a single HTML attribute.

The unified API covers:
- **Bible** (Christianity): 66 books, 31,102 verses, 4 translations (KJV/ASV/BBE/YLT)
- **Quran** (Islam): 114 surahs, 6,236 ayahs, Arabic Uthmani + 5 English translations
- **Torah/Tanakh** (Judaism): 24 books, 23,145 verses, Hebrew Masoretic + JPS/KJV
- **Bhagavad Gita** (Hinduism): 18 chapters, 700 shlokas, Sanskrit Devanagari + 9 commentators
- **Pali Canon** (Buddhism): 5 Nikayas, 5,326 suttas, Pali + English

Total: **236,000+ scripture records** across 5 religions.

### Verse Card — Single Scripture Passage Display

A Verse Card renders a single passage from any scripture with its original language and English translation. The `data-religion` attribute routes the request to the correct underlying API. Each religion's widget retains its own original-language rendering: Hebrew for Torah, Arabic (RTL) for Quran, Sanskrit Devanagari for Gita, Pali romanization for Sutras, Greek for New Testament.

```html
<!-- Christianity: John 3:16 — KJV -->
<div data-wideholy="verse"
  data-ref="John 3:16"
  data-religion="bible"
  data-translation="kjv"
  data-theme="light">
</div>

<!-- Islam: Ayat al-Kursi (2:255) with Arabic script -->
<div data-wideholy="verse"
  data-ref="2:255"
  data-religion="quran"
  data-show-original="true"
  data-theme="sepia">
</div>

<!-- Judaism: The Shema — Deuteronomy 6:4 with Hebrew -->
<div data-wideholy="verse"
  data-ref="Deuteronomy 6:4"
  data-religion="torah"
  data-show-original="true"
  data-theme="light">
</div>

<!-- Hinduism: Bhagavad Gita 2:47 — Karma Yoga with Sanskrit -->
<div data-wideholy="verse"
  data-ref="2:47"
  data-religion="gita"
  data-show-original="true"
  data-theme="sepia">
</div>

<!-- Buddhism: Dhammapada 183 — Teaching of the Buddhas -->
<div data-wideholy="verse"
  data-ref="dhp:183"
  data-religion="sutra"
  data-theme="light">
</div>

<script src="https://cdn.jsdelivr.net/npm/wideholy-embed@1/dist/embed.min.js"></script>
```

**Available options for Verse Card:**

| Attribute | Values | Default |
|-----------|--------|---------|
| `data-ref` | Reference format depends on `data-religion` | required |
| `data-religion` | `bible`, `quran`, `torah`, `gita`, `sutra` | required |
| `data-translation` | Religion-specific translation codes | per-religion default |
| `data-show-original` | `true`, `false` | `false` |
| `data-theme` | `light`, `dark`, `sepia` | `light` |
| `data-size` | `default`, `compact` | `default` |

Learn more: [WideHoly Multi-Religion API — wideholy.com](https://wideholy.com) · [Interfaith Concept Comparisons](https://wideholy.com) · [Widget Builder](https://widget.wideholy.com)

### Chapter Card — Full Chapter or Surah

A Chapter Card renders a full chapter, surah, adhyaya, or sutta with navigation. The format adapts to the selected religion — Bible chapter navigation shows book/chapter numbers, Quran shows surah name and Meccan/Medinan classification, Torah shows chapter and parashah name, Gita shows adhyaya and yoga path name, Sutra shows collection and sutta title.

```html
<!-- Genesis Chapter 1 — Christian/Jewish creation account -->
<div data-wideholy="chapter"
  data-ref="Genesis 1"
  data-religion="bible"
  data-theme="light">
</div>

<!-- Al-Fatiha (Quran 1) — The Opening surah, 7 ayahs -->
<div data-wideholy="chapter"
  data-ref="1"
  data-religion="quran"
  data-translation="sahih"
  data-theme="sepia">
</div>

<!-- Bhagavad Gita Chapter 12 — Bhakti Yoga, 20 shlokas -->
<div data-wideholy="chapter"
  data-ref="12"
  data-religion="gita"
  data-theme="dark">
</div>

<script src="https://cdn.jsdelivr.net/npm/wideholy-embed@1/dist/embed.min.js"></script>
```

Learn more: [Cross-Religion Chapter Browser — wideholy.com](https://wideholy.com) · [Five World Religions Overview](https://wideholy.com) · [Scripture Structures Compared](https://wideholy.com)

### Comparison Card — Cross-Religion Concept Comparison

The Comparison Card is WideHoly's most distinctive feature — you can compare passages from different religions side by side. Compare how Christianity and Islam describe the creation, how the Torah and the Bhagavad Gita describe the eternal soul, or how Buddhist and Jewish wisdom literature treat the same moral question.

This is not available in the per-religion packages (widebible-embed, widequran-embed, etc.) — it requires the wideholy-embed unified package.

```html
<!-- Cross-religion comparison: Genesis 1:1 (Bible) vs Quran 2:255 (Throne Verse) -->
<div data-wideholy="compare"
  data-a="John 3:16"
  data-a-religion="bible"
  data-b="2:255"
  data-b-religion="quran"
  data-theme="light">
</div>

<!-- Torah vs Gita on the eternal soul: Deuteronomy 30:15 vs Bhagavad Gita 2:20 -->
<div data-wideholy="compare"
  data-a="Deuteronomy 30:15"
  data-a-religion="torah"
  data-b="2:20"
  data-b-religion="gita"
  data-theme="sepia">
</div>

<!-- Buddhist and Christian on loving-kindness: Dhammapada 1 vs Matthew 5:44 -->
<div data-wideholy="compare"
  data-a="dhp:1"
  data-a-religion="sutra"
  data-b="Matthew 5:44"
  data-b-religion="bible"
  data-theme="dark">
</div>

<script src="https://cdn.jsdelivr.net/npm/wideholy-embed@1/dist/embed.min.js"></script>
```

**Available options for Comparison Card:**

| Attribute | Values | Default |
|-----------|--------|---------|
| `data-a` | Scripture reference (first) | required |
| `data-a-religion` | `bible`, `quran`, `torah`, `gita`, `sutra` | required |
| `data-b` | Scripture reference (second) | required |
| `data-b-religion` | `bible`, `quran`, `torah`, `gita`, `sutra` | required |
| `data-theme` | `light`, `dark`, `sepia` | `light` |

Learn more: [Interfaith Comparisons — wideholy.com](https://wideholy.com) · [Golden Rule Across Religions](https://wideholy.com) · [Creation Accounts Compared](https://wideholy.com)

### Verse of the Day — Auto-Updating Daily Widget

The Verse of the Day widget displays a curated passage that changes daily. You can show a single religion's daily verse, or use the "all" mode to cycle through all 5 religions over successive days — ideal for interfaith websites and spirituality apps that serve diverse audiences.

```html
<!-- Daily verse from all 5 religions (cycles: Bible → Quran → Torah → Gita → Sutra) -->
<div data-wideholy="votd" data-religion="all" data-theme="light"></div>

<!-- Daily Bible verse only -->
<div data-wideholy="votd" data-religion="bible" data-theme="light"></div>

<!-- Daily Quran ayah — dark theme -->
<div data-wideholy="votd" data-religion="quran" data-theme="dark"></div>

<!-- Daily teaching from any tradition — sepia -->
<div data-wideholy="votd" data-religion="all" data-theme="sepia"></div>

<!-- Compact multi-religion daily verse for sidebars -->
<div data-wideholy="votd" data-religion="all" data-theme="light" data-size="compact"></div>

<script src="https://cdn.jsdelivr.net/npm/wideholy-embed@1/dist/embed.min.js"></script>
```

Learn more: [Daily Scripture — All Traditions](https://wideholy.com) · [Interfaith Daily Devotional](https://wideholy.com) · [Scripture Calendar](https://wideholy.com)

### Search Box — Cross-Religion Scripture Search

Embed a search box that queries across all 236,000+ scripture records simultaneously. Results show the matched passage, its religion, book/chapter/verse, and a highlighted snippet. The user can filter results by religion using a dropdown within the widget. Transliteration search works across all languages — searching "love" returns results from the Bible, Quran (Arabic transliteration), Torah (Hebrew transliteration), Gita (Sanskrit), and Pali Canon.

```html
<!-- Default cross-religion search -->
<div data-wideholy="search"
  data-placeholder="Search all scriptures…"
  data-theme="light">
</div>

<!-- Single-religion search scoped to Quran only -->
<div data-wideholy="search"
  data-placeholder="Search Quran…"
  data-religion="quran"
  data-theme="sepia">
</div>

<!-- Dark theme interfaith search -->
<div data-wideholy="search"
  data-placeholder="Search across 5 world religions…"
  data-theme="dark">
</div>

<script src="https://cdn.jsdelivr.net/npm/wideholy-embed@1/dist/embed.min.js"></script>
```

Learn more: [Cross-Religion Scripture Search — wideholy.com](https://wideholy.com) · [Concept Index Across Traditions](https://wideholy.com) · [API Search Endpoint](https://wideholy.com/developers/)

## Supported Religions and References

| Religion | `data-religion` | Reference Format | Example |
|----------|----------------|------------------|---------|
| Christianity | `bible` | `"Book Chapter:Verse"` | `John 3:16`, `Psalm 23:1` |
| Islam | `quran` | `"surah:ayah"` | `2:255`, `112:1` |
| Judaism | `torah` | `"Book Chapter:Verse"` | `Genesis 1:1`, `Deuteronomy 6:4` |
| Hinduism | `gita` | `"chapter:verse"` | `2:47`, `18:66` |
| Buddhism | `sutra` | `"collection:number"` | `dhp:1`, `mn:22`, `dn:22` |
| All religions | `all` | N/A (used for `votd` and `search` only) | — |

## Widget Options

All widget types share these common attributes:

| Attribute | Values | Default | Description |
|-----------|--------|---------|-------------|
| `data-wideholy` | `verse`, `chapter`, `compare`, `votd`, `search` | required | Widget type |
| `data-religion` | `bible`, `quran`, `torah`, `gita`, `sutra`, `all` | required | Which scripture to load |
| `data-ref` | Reference format depends on `data-religion` | — | Verse or chapter reference |
| `data-a` | scripture reference | — | First passage for comparison |
| `data-a-religion` | `bible`, `quran`, `torah`, `gita`, `sutra` | — | Religion for first comparison passage |
| `data-b` | scripture reference | — | Second passage for comparison |
| `data-b-religion` | `bible`, `quran`, `torah`, `gita`, `sutra` | — | Religion for second comparison passage |
| `data-theme` | `light`, `dark`, `sepia` | `light` | Visual theme |
| `data-size` | `default`, `compact` | `default` | Compact suits sidebars under 300px |
| `data-translation` | Religion-specific codes | per-religion default | Translation or commentator |
| `data-show-original` | `true`, `false` | `false` | Show original-language text |
| `data-placeholder` | any string | `"Search Scripture…"` | Search widget placeholder |

## Themes

WideHoly widgets support 3 themes:

```html
<!-- Light — white background, dark text, purple accent (interfaith neutral) -->
<div data-wideholy="votd" data-religion="all" data-theme="light"></div>

<!-- Dark — dark background, light text, purple accent -->
<div data-wideholy="votd" data-religion="all" data-theme="dark"></div>

<!-- Sepia — warm parchment background, evokes sacred manuscript traditions across cultures -->
<div data-wideholy="votd" data-religion="all" data-theme="sepia"></div>
```

All themes are self-contained inside Shadow DOM — they never affect or inherit from your site's CSS.

## CDN Options

### jsDelivr (recommended — global CDN, auto-updates with npm)

```html
<script src="https://cdn.jsdelivr.net/npm/wideholy-embed@1/dist/embed.min.js"></script>
```

Pin to a specific version for production stability:

```html
<script src="https://cdn.jsdelivr.net/npm/wideholy-embed@1.0.1/dist/embed.min.js"></script>
```

### R2 CDN (wideholy.com hosted)

```html
<script src="https://cdn.wideholy.com/embed.min.js"></script>
```

### npm (for bundlers — Webpack, Vite, Rollup)

```bash
npm install wideholy-embed
```

```javascript
// Import the embed script — handles all 5 religion data-wideholy elements
import 'wideholy-embed';
```

## Technical Details

- **Shadow DOM**: Complete style isolation — no CSS conflicts with your site. All widgets are fully encapsulated.
- **Zero dependencies**: No jQuery, React, Vue, or any external library. Pure browser APIs only.
- **Multi-script rendering**: Hebrew (RTL), Arabic (RTL), Sanskrit Devanagari, Pali diacritics — all handled via system fonts.
- **RTL support**: Arabic and Hebrew text renders correctly right-to-left. LTR and RTL can coexist in a Comparison Card.
- **CORS**: WideHoly API has CORS enabled for all origins — no proxy needed.
- **Caching**: Verse of the Day cached in localStorage per religion, refreshes daily at midnight UTC.
- **MutationObserver**: Works with dynamically added elements (React, Vue, Angular SPAs).
- **Bundle size**: ~5KB gzipped.
- **Accent color**: Purple (`#7C3AED`) — the WideHoly brand color, representing interfaith harmony.
- **API base**: `https://wideholy.com/api/v1/` — unified endpoint for all 5 religions.

## Learn More About World Scriptures

- **Compare**: [Interfaith Concept Comparisons — wideholy.com](https://wideholy.com) · [The Golden Rule Across 5 Religions](https://wideholy.com) · [Creation Accounts Compared](https://wideholy.com)
- **Browse**: [All 5 World Religions](https://wideholy.com) · [Scripture Structures by Tradition](https://wideholy.com) · [Cross-Religion Concept Index](https://wideholy.com)
- **Translations**: [Original Language Texts](https://wideholy.com) · [English Translations by Tradition](https://wideholy.com)
- **Tools**: [Multi-Religion Verse Lookup](https://wideholy.com) · [Cross-Religion Search](https://wideholy.com) · [Widget Builder](https://widget.wideholy.com)
- **API**: [Unified REST API Docs](https://wideholy.com/developers/) · [OpenAPI Spec](https://wideholy.com/api/openapi.json)

## WideHoly Scripture Family

**WideHoly** — Scripture for everyone. Each site is also available as a standalone embed package.

| Site | Domain | Scripture | Standalone Package |
|------|--------|-----------|-------------------|
| WideBible | [widebible.com](https://widebible.com) | 66 books, 31,102 verses, KJV/ASV/BBE/YLT | [widebible-embed](https://www.npmjs.com/package/widebible-embed) |
| WideQuran | [widequran.com](https://widequran.com) | 114 surahs, 6,236 ayahs, Arabic Uthmani + 5 translations | [widequran-embed](https://www.npmjs.com/package/widequran-embed) |
| WideTorah | [widetorah.com](https://widetorah.com) | 24 books, 23,145 verses, Hebrew Masoretic + English | [widetorah-embed](https://www.npmjs.com/package/widetorah-embed) |
| WideGita | [widegita.com](https://widegita.com) | 18 chapters, 700 shlokas, Sanskrit + 9 commentators | [widegita-embed](https://www.npmjs.com/package/widegita-embed) |
| WideSutra | [widesutra.com](https://widesutra.com) | 5 Nikayas, 5,326 suttas, Pali + English | [widesutra-embed](https://www.npmjs.com/package/widesutra-embed) |
| **WideHoly** | [wideholy.com](https://wideholy.com) | **5 religions, 236,000+ records, unified API** | **this package** |

## License

MIT — see [LICENSE](./LICENSE).

Built with care by [WideHoly](https://wideholy.com).
