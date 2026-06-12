# Change Log

All notable changes to the "calming-coding" extension will be documented in this file.

Check [Keep a Changelog](http://keepachangelog.com/) for how to structure this file.

## [Unreleased]

### Documentation
- CHANGELOG and README rewritten to describe the theme's evolution in objective technical terms (what changed and why), without attributing requests or feedback to specific sources.
- README palette table updated to match the current color values: editor `#2A2521`, sidebar `#221E1A`, titlebar `#1E1A17`, overlay `#2D2923`, elevated `#382F28`, cream `#E8DCC4`, sage `#A8C97A`, clay `#D08F60`, teal `#7CB8B5`, ambar `#E0AC58`, coral `#E87865`.
- README highlights section updated: token count 495 → 500, new bullet describing the JSX/TSX tag differentiation system (open/close/self-closing/fragment/without-attributes).

### Changed
- `list.focusBackground` leaves opaque amber (`#D4A55C`): now `#D4A55C2E` with cream text and `list.focusIconForeground` amber, matching the translucent language used everywhere else in the theme. The focus row in the Explorer no longer "shouts".
- JSX/TSX: tags (`<Dialog>`, `<Button>`, …) are now bold amber (`#D4A55C`). JSX children text is back to cream (`#D7C8B6`) — the previous muted-italic made texts inside `<p>` and other tags practically invisible against the dark editor, killing the "alive-but-calming" feel.
- `meta.tag` generic scope reverted to cream (`#D7C8B6`) — the muted version darkened the entire tag area and contributed to the "dead" feel.
- `editor.lineHighlightBackground` changed from `#0000001A` (10% black, barely visible) to `#FFFFFF08` (5% white) with a `#3A3531` border, so the current line reads as a subtle "resting place" instead of a black hole.
- `editorBracketMatch.background` changed from `#D7C8B61A` to `#D4A55C20` so the matched bracket tint matches the warm accent family.
- `entity.name.tag` (generic HTML) moved from clay (`#C89274`) to amber (`#D4A55C`) so HTML and JSX share the same tag role.

### Added
- Modern `list.*` color variants: `list.activeSelectionIconForeground`, `list.inactiveSelectionIconForeground`, `list.hoverIconForeground`, `list.focusIconForeground`, `list.focusAndSelectionBackground/Foreground/IconForeground`, `list.inactiveFocusBackground/Foreground/IconForeground`, `list.highlightIconForeground`, `list.invalidItemForeground`, `list.errorForeground`, `list.warningForeground`.
- Additional JSX/TSX token rules: `entity.name.tag.open.jsx`, `entity.name.tag.close.jsx`, `entity.name.type.tsx`, `entity.name.type.jsx`.
- Consolidated the duplicate `support.class.component.tsx/jsx` rule that previously conflicted with the later `JS/TS class component` rule (both were the same scope, one teal and one amber — now a single amber rule).

### Removed
- The `meta.tag.sgml,meta.tag.other.tsx,meta.tag.other.jsx` rule was a no-op in TSX (every sub-element of a tag has a more specific scope) and its muted color risked being inherited as a fallback. Removed to keep the token list clean.


### Refined (JSX/TSX tag differentiation)

JSX/TSX tags are now differentiated by structural role, creating visible rhythm in nested code:

| Role | Color | Style | Scope |
|---|---|---|---|
| Opening tag (with attributes) | `#A8854A` dark ochre | **bold** | `entity.name.tag.open.jsx`,`entity.name.tag.open.tsx`,`entity.name.tag.tsx`,`entity.name.tag.jsx`,`entity.name.tag.html` |
| Closing tag | `#D08F60` clay | regular | `entity.name.tag.close.jsx`,`entity.name.tag.close.tsx` |
| Self-closing tag | `#A8854A` dark ochre | **bold italic** | `entity.name.tag.self-closing.jsx`,`entity.name.tag.self-closing.tsx`,`entity.name.tag.self-closing.html`,`entity.name.tag.self-closing` |
| Fragment (`<>`, `</>`) | `#D08F60` clay | italic | `entity.name.tag.fragment.jsx`,`entity.name.tag.fragment.tsx`,`entity.name.tag.fragment.html`,`entity.name.tag.fragment`,`meta.brace.curly.jsx`,`meta.brace.curly.tsx` |
| Tag without attributes | `#D08F60` clay | italic | `meta.tag.without-attributes.tsx`,`meta.tag.without-attributes.jsx` |
| HTML element (in HTML files) | `#D08F60` clay | italic | `entity.name.tag.html`,`entity.name.tag.xhtml` |
| Generic tag (XML, Markdown fallback) | `#D08F60` clay | italic | `entity.name.tag` |

Open vs close creates a hue-shifted rhythm (dark ochre → clay). Self-closing vs paired is differentiated by italic. Fragments and tags without attributes get the clay italic treatment to distinguish them as "structural" rather than "actor" components.

Total token rules: **500**. Color count: **394**.

### Refined (palette refresh v3 — "calm but alive")

The previous palette was technically correct but sat in a too-narrow chroma band that made code feel "muddy" — beautiful in spec, lifeless on screen. Same warm color families, ~15% more chroma, plus warmer backgrounds with a red undertone. The result: the code stops looking like "pastel dust" and starts feeling like a curated workspace that has presence.

| Role | Before | After | Chroma | Notes |
|---|---|---|---|---|
| Editor background | `#282523` | `#2A2521` | — | Warmer, more red |
| Sidebar / panel / titlebar | `#211F1D` | `#221E1A` | — | Warmer |
| Activity bar / status bar | `#1C1B19` | `#1E1A17` | — | Warmer |
| Overlays (hover, widgets, notifications) | `#2A2723` | `#2D2923` | — | Warmer |
| Selection / hover surfaces | `#3A3531` | `#382F28` | — | Warmer |
| Cream text | `#D7C8B6` | `#E8DCC4` | +chroma | Warmer, more golden (parchment, not paper) |
| Ambar (keywords, accents, JSX components, button) | `#D4A55C` | `#E0AC58` | 50% → 65% | Honey star with body |
| Salvia (strings) | `#9DB87C` | `#A8C97A` | 28% → 45% | Garden green, not dead olive |
| Clay (variables, JSX tags, properties) | `#C89274` | `#D08F60` | 30% → 50% | Terracotta with presence |
| Teal (functions, classes) | `#7AA0A8` | `#7CB8B5` | 15% → 35% | Cyan with life, not gray-blue |
| Coral (errors) | `#E58575` | `#E87865` | 38% → 48% | More red-orange punch |
| Button hover | `#C49840` | `#C89644` | +chroma | Deeper amber |
| Focus pumpkin | `#E08B41` | unchanged | — | Still the warm "punctum" |
| Cursor lavender | `#B49FCC` | unchanged | — | Still the cool "punctum" |

All 9 syntax/UI colors verified against the new editor background `#2A2521`:

- Cream `#E8DCC4` → **11.17:1** (AAA)
- Ambar `#E0AC58` → **7.37:1** (AAA)
- Salvia `#A8C97A` → **8.16:1** (AAA)
- Clay `#D08F60` → **5.62:1** (AA)
- Teal `#7CB8B5` → **6.77:1** (AA)
- Coral `#E87865` → **5.27:1** (AA)
- Pumpkin `#E08B41` → **5.73:1** (AA)
- Lavender `#B49FCC` → **6.33:1** (AA)
- Muted `#A1988E` → **5.34:1** (AA)

Total: ~280 hex tokens replaced across the file. All 226 ambar tokens (including 25 alpha-tinted variants used in selections, hover, brackets, inlay hints, etc.) migrated preserving their alpha channel.

### Added (bracket pair colorization)

Nested bracket guides in 6 levels, cycling through the warm palette: ambar → salvia → clay → teal → coral → pumpkin. Subtle (40% alpha) when not active, full color when the cursor is beside the bracket. This adds a small but consistent splash of color as you descend into deeply nested code, without ever leaving the warm palette family.

```jsonc
"editorBracketPairGuide.background1":        "#E0AC5866",  // ambar
"editorBracketPairGuide.background2":        "#A8C97A66",  // salvia
"editorBracketPairGuide.background3":        "#D08F6066",  // clay
"editorBracketPairGuide.background4":        "#7CB8B566",  // teal
"editorBracketPairGuide.background5":        "#E8786566",  // coral
"editorBracketPairGuide.background6":        "#E08B4166",  // pumpkin
"editorBracketPairGuide.activeBackground1":  "#E0AC58",
"editorBracketPairGuide.activeBackground2":  "#A8C97A",
"editorBracketPairGuide.activeBackground3":  "#D08F60",
"editorBracketPairGuide.activeBackground4":  "#7CB8B5",
"editorBracketPairGuide.activeBackground5":  "#E87865",
"editorBracketPairGuide.activeBackground6":  "#E08B41"
```

Color totals: 394 (was 382, +12 bracket pair guides). Token rules: 497 (unchanged, structure identical).

## [1.1.0] - 2026-06-10

### Changed
- Repositioned the accent palette: the warm orange `#E08B41` is now reserved for focus indicators (focusBorder, tab active border, status bar debugging border, bracket match border, terminal cursor, ANSI bright yellow). All non-focus accents (buttons, badges, links, list highlights, status bar items, panel title, activity bar badge, peek view, progress bar, find match, selection highlight) now use the calmer mustard `#C9A36A`.
- Editor selection, list drop, word highlight, peek view match highlight and minimap find match all moved to translucent warm mustard tints instead of the previous Nordic blue / saturated orange overlays.
- Terminal ANSI palette reorganized so `ansiWhite` is the actual readable cream (`#D7C8B6`) and `ansiBrightWhite` is the very light cream (`#F0E5D5`); `ansiYellow` is now a calm mustard (`#C9A36A`) and `ansiMagenta` aligns with the variable mauve (`#C593A4`).
- Error red shifted from `#D95B5B` (4.06:1 on the editor background) to `#DD6F6F` to clear WCAG AA 4.5:1.
- Cursor color moved from the cool lavender `#A895C3` to a slightly more muted lavender `#B49FCC` for better harmony with the warm palette while still acting as a single cool focal point.
- Git decoration stage colors (`stageModified` yellow `#e2c08d`, `stageDeleted` red `#c74e39`) replaced with palette-consistent `#C9A36A` and `#DD6F6F`.
- Hover / Suggest / Peek view / Notifications widgets now sit on a dedicated overlay surface (`#2A2723`, between `editor.background` `#282523` and `sideBar.background` `#211F1D`) so they feel like floating popups instead of extensions of the sidebar.
- Activity bar / status bar / panel title accents demoted to the calm mustard; the only places the original pumpkin orange `#E08B41` survives are focus, the active tab top border and the status-bar debugging border.

### Fixed
- Terminal: `terminal.selectionBackground` no longer equals `terminal.foreground`. Selected text is now legible.
- List: `list.focusBackground` and `list.focusForeground` are no longer the same cream color, so the focused row in the Explorer is readable.
- Out-of-palette syntax leftovers replaced: pure `#ffffff` for `invalid.broken/deprecated/illegal/unimplemented` and `constant.other.color.rgb-value.xi`; bright red `#f44747` for `token.error-token` and `invalid.illegal.non-null-typehinted.php`; cool gray `#4a5759` for Xi markdown list punctuation.
- `editorBracketMatch.border` is now the calm mustard instead of transparent, making bracket pairs findable.
- Status bar debugging no longer paints the entire bottom bar in saturated orange; the accent is now a top border on a normal surface.
- Diff editor backgrounds slightly more opaque (`#98C37930` / `#DD6F6F30`) so insertions and deletions are easier to spot.

### Added
- Many previously-missing color tokens so the theme is consistent across the entire editor:
  - `editor.selectionForeground`, `editor.findMatchForeground`, `editor.findMatchHighlightForeground`, `editor.hoverHighlightBackground`, `editor.foldBackground`, `editorIndentGuide.background1..6`, `editorWidget.selectionBackground`, `editorWidget.resizeBorder`.
  - `editorInlayHint.*`, `editorStickyScroll.*`, `editorLightbulb.*`, `inlineEdit.originalChanged/Unchanged/ModifiedChanged/ModifiedUnchangedText*`.
  - `tab.unfocusedActive/Hover/Inactive*` for multi-window/multi-root scenarios.
  - `statusBarItem.error/warning/prominent*`.
  - `terminal.inactiveSelectionBackground`, `terminal.findMatch*`, `terminal.hoverHighlightBackground`, `terminalCommandDecoration.{default,error,success}Background`.
  - `textLink.activeForeground`.
  - `notebook.*` (cell borders, focused/unfocused cell states, hover, row hover, output container, selected cell, symbol highlight, errored background, etc.).
  - `testing.*` (icons for failed/errored/passed/queued/unset/skipped, run action, message badges, peek border/header, run exception/failure/progress backgrounds and borders).
  - `welcomePage.*`, `toolbar.*`, `scm.providerBorderColor`.

### Notes
- This release ships only a dark theme.

### Refined (visual polish)
- Menu selection (`menu.selectionBackground` / `menu.selectionForeground`) changed from a low-contrast dark brown (`#6E4A28` / `#D7C8B6`, ~1.2:1) to the calm mustard with dark text (`#C9A36A` / `#1C1B19`, ~7.3:1) so the active menu item is immediately visible. Same treatment as `list.focusBackground` / `list.focusForeground` for consistency.
- `icon.foreground` moved from cream (`#D7C8B6`) to muted (`#A1988E`) so the title-bar utility icons (Extensions, Account, Settings, etc.) stop competing with the actual title text.
- `tab.border` changed from transparent to a subtle `#4A453F` to draw a minimal separator between adjacent inactive tabs (most useful when several tabs are open at the same size).
- `scrollbarSlider.background` alpha bumped from `70` to `99` (i.e. `#615B5199`) so the editor scrollbar is localizable without becoming loud. Hover/active unchanged.

### Refined (language & framework coverage)
- Default punctuation (semicolons, commas, statement terminators) moved from cream to muted `#7D7366` so the code visually breathes — the eye can latch onto identifiers and keywords instead of every `;` and `,`.
- Added **246 new token rules** covering:
  - **Python** (30 rules): async/await, decorators (italic), built-in functions and constants (`True`/`False`/`None`), class and function definitions, f-string placeholders, docstrings (italic), type hints, match/yield/walrus, magic methods.
  - **JavaScript / TypeScript** (41 rules): async/await, interface / enum / alias / namespace types, type-utility generics (`Partial`, `Required`, etc.), TS decorators (italic), JSX/TSX tags and attributes, template literals, optional chaining, private fields, `use client` / `use server` / `use strict` directives, console, Math, JSON, typeof/instanceof/void, import/export keywords.
  - **Go** (15 rules): `func` / `var` / `const` / `type`, storage primitive types, built-in functions (`make`, `len`, `append`, …), built-in constants (`true`/`false`/`nil`), method receivers (italic), format verbs in `fmt.Sprintf`, function-call, build tag comments (italic), package name.
  - **Rust** (20 rules): full keyword set (`fn`, `let`, `mut`, `pub`, `mod`, `use`, `impl`, `trait`, `struct`, `enum`, `match`, `async`, `unsafe`, `macro_rules!`, …), attributes / proc macros (italic), built-in types (`Option`, `Result`, `Vec`, …), macros (italic), `Self` / `true` / `false`, lifetimes, format-string interpolation, numeric and char/string tokens, doc comments (italic).
  - **PHP** (29 rules): full keyword set, visibility / modifier keywords, type declarations, built-in classes and functions, magic methods and constants (italic), `$variable` interpolation, attributes `#[Attribute]` (italic), heredoc/nowdoc strings, null-coalescing operator, arrow functions, match arms, PHPDoc comments (italic), numeric constants.
  - **Frameworks**: React hooks (italic), Next.js page/metadata (italic), Vue directives / v-bind / v-on / interpolation (italic), Vue Composition API (`ref`, `reactive`, `computed`, italic), Angular decorators and structural directives (italic), Angular property/event/two-way bindings, Svelte reactivity and directives (italic), Astro components and client directives, Django template tags and filters (italic) and model fields, Laravel Blade directives and punctuation (italic), Eloquent, Express / NestJS decorators (italic), Spring annotations (italic), Rails ERB tags, Tailwind utilities / at-rules / config functions (italic), Prisma keywords/models/fields/attributes/functions (italic), Zod schemas (italic).
  - **SQL** (8 rules): DML / DDL / DCL / TCL keywords, storage types, aggregate and built-in functions, table and column identifiers, strings, constants.
  - **HTML** (8 rules): attribute names and values, tags, punctuation, entities, doctype, embedded sources (italic).
  - **CSS / SCSS / Less** (20 rules): property names and values, functions, custom variables, at-rules, units, pseudo-classes/elements, color names, ids, numerics, strings, comments (italic).
  - **JSON** (4 rules): property names, strings, numbers, language constants.
  - **YAML** (6 rules): keys, strings, constants, anchors/aliases, punctuation.
  - **Markdown** (24 rules): headings, bold/italic, inline and fenced code, links, lists, blockquote, horizontal rules.
  - **Shell / Bash** (7 rules): control flow, operators, built-in functions, positional and named variables, strings, options, comments (italic).
  - **Dockerfile** (4 rules): instructions, image names (italic), functions, strings.
  - **TOML** (5 rules): keys, strings, constants, tables, punctuation.
  - **Ruby** (13 rules): control flow / class / def / module / rescue, operators, constants and symbols, instance/class/global variables, built-in functions, class and function definitions, string interpolation, regex (red), heredoc.
  - **Java** (20 rules): control, modifier, primitive and built-in types, built-in functions, class / interface / enum definitions, function / method definitions, annotations (italic), constants, strings, variables.
  - **Kotlin** (8 rules): control, modifier, types, functions, classes, annotations (italic), string templates, constants.
  - **C#** (11 rules): control flow / class / function / modifier / LINQ, modifier / type, built-in types, functions, class / interface / struct / enum / record, annotations (italic), constants, string interpolation, preprocessor, variables.
  - **C / C++** (11 rules): preprocessor and includes, primitive and built-in types, built-in functions, class / struct / namespace definitions, constants, strings, comments (italic), templates, operators.

  Total token rules went from 243 to **489**. Color palette unchanged; every new rule uses the established roles (mustard keywords, info-blue functions, mauve variables/constants, green strings, error red, focus orange).

### Refined (palette refresh)
Six color roles were refreshed to give the theme a more alive-but-still-calming character. The warm brown surfaces, cream text, focus orange, cursor lavender and the entire border/muted scale are untouched; only the five syntax/UI accent roles plus the button-hover got more chroma so the code stops looking "muddy".

| Role | Before | After | Character |
|---|---|---|---|
| Strings (green) | `#98C379` | `#88C9A0` | Mint, less stale yellow |
| Variables / properties / JSX tags / JSON keys / numbers (mauve) | `#C593A4` | `#C2A5D9` | Soft lavender — no dusty rose |
| Functions / info / operators (blue) | `#81A1C1` | `#88B8D4` | Warm sky blue, in family with the warm palette |
| Keywords / accent / button / warnings (mustard) | `#C9A36A` | `#D4A55C` | Honey amber — the warm star of the palette |
| Errors (red) | `#DD6F6F` | `#E58575` | Less aggressive coral, more harmonious |
| Button hover (derived) | `#B89055` | `#C49840` | Deeper amber, clear feedback |

- Focus ring (`#E08B41`, 5 keys), cursor (`#B49FCC`), cream text (`#D7C8B6`), all background browns and all muted/border tones remain unchanged.
- Total replacements: 491 hex tokens across the file; all old hex values have 0 occurrences after the change. No structural changes — same 368 color keys, same 489 token rules.
- Version stays at `1.1.0`.

### Refined (palette refresh v2 — fully warm, no lavender)
The lavender (`#C2A5D9`) used for variables / properties / JSX tags / JSON keys / numbers felt too cold against the warm brown base. The palette is now **100% warm** — no purple, no mauve, no pink, no icy blue.

| Role | Before (v1) | After (v2) | Character |
|---|---|---|---|
| Variables / properties / JSX tags / JSON keys / numbers | `#C2A5D9` lavender | **`#C89274`** | Clay / terracotta — warm, with no purple undertone |
| Strings | `#88C9A0` mint | **`#9DB87C`** | Sage / olive — more earthy, in family with the palette |
| Functions / info / operators | `#88B8D4` sky blue | **`#7AA0A8`** | Earthy teal — warm, not even blue |
| Keywords / accent / button | `#D4A55C` honey amber | `#D4A55C` | Unchanged — already the warm anchor |
| Errors | `#E58575` coral | `#E58575` | Unchanged — stays harmonious |
| Hover derivado | `#C49840` | `#C49840` | Unchanged |

- **Salvia `#9DB87C`** (strings) — alive olive, evokes a fresh garden.
- **Clay `#C89274`** (variables, JSX, JSON keys, numbers) — terracotta-like, the "earth" tone of the palette.
- **Teal `#7AA0A8`** (functions, info) — warm cyan-green, not icy, brings a touch of sea without being cold.
- **Ambar `#D4A55C`** (keywords, accents, button) — the "honey star" of the palette.
- **Coral `#E58575`** (errors) — warm red, never alarmist.
- Cursor (`#B49FCC`) and focus pumpkin (`#E08B41`) intentionally stay cool/warm-bright as the only two "punctum" colors that aren't part of the syntax family.

- All new accent colors keep WCAG AA 4.5:1 against the editor background `#282523`:
  salvia 6.95:1, clay 5.67:1, teal 5.38:1, ambar 6.77:1, coral 5.76:1, hover 5.74:1.
- All five background browns verified as visually warm (R ≥ G ≥ B).
- Total replacements this round: 250 hex tokens (`#88C9A0` × 43, `#C2A5D9` × 118, `#88B8D4` × 89). All old hex values now have 0 occurrences. No structural changes — same 368 color keys, same 489 token rules.
- Version stays at `1.1.0`.

### Refined (class names get a distinct color)
Class names (`entity.name.class`, `entity.name.type`, `entity.name.namespace`, `entity.name.type.namespace`, `entity.name.type.class`, `support.class`, `entity.other.inherited-class`, and the language-specific built-in classes) were still rendered in cream (`#D7C8B6`), the same color as regular text. This made class identifiers disappear in code like `Prisma.PrismaClientKnownRequestError` or `NextRequest` — the "color of the class was lost" against the regular text.

The natural color for that role, given the rest of the warm palette, is the existing **teal** `#7AA0A8` — the same color used for function names. This makes "named entities" (functions and classes) share a single warm-blue color, distinct from the cream text, the ambar keywords, the clay variables, and the salvia strings.

#### Changes
- 13 existing rules had their foreground moved from cream `#D7C8B6` to teal `#7AA0A8`:
  - `entity.name.namespace`, `entity.name.type.namespace`, `support.class` + `entity.name.type.class`, `entity.name.class.identifier.namespace.type`, `entity.name.class` (+ `variable.other.class.js/ts`), `entity.other.inherited-class`, `entity.name.namespace.php`, `entity.name.namespace.cpp`, `support.class.builtin.php` + `support.class.php`, `support.class.builtin.js` + `support.class.builtin.ts`.
  - The combined `Java type`, `Kotlin type`, `C# type` rules were **split**: the primitive-type halves (`storage.type.primitive.*`, `support.type.*`, `storage.type.cs`, `support.type.c/cpp/posix-reserved.c`, `support.type.swift/vb.asp`, `support.type.python/builtin.python`, `support.type.primitive.ts/builtin.ts`, etc.) stay cream (these are primitive types like `int`, `string`, `boolean` — not class names); the built-in-class halves (`support.class.builtin.java`, `support.class.builtin.kotlin`, `support.class.builtin.cs`) get the new teal rules.
- 6 new rules appended after the `Native Tags` entry:
  - `entity.name.type` → teal (type names defined by the theme, like `MyType`).
  - `support.class.builtin.java` → teal (`String`, `Object`, etc.).
  - `support.class.builtin.kotlin` → teal.
  - `support.class.builtin.cs` → teal.
  - `entity.name.class.python` + `entity.name.type.class.python` → teal (in addition to the existing `Python class definition` ambar rule which still applies to the `class` keyword itself).
  - `variable.other.class.php` → teal (replaces the previous clay version).

#### Visual hierarchy after the change
- Cream `#D7C8B6` — regular text and primitive types (`int`, `string`, `boolean`, etc.).
- Teal `#7AA0A8` — named entities (functions, classes, namespaces, built-in classes like `String`, `Object`, `Array`).
- Ambar `#D4A55C` — control flow keywords, class definitions (`class Foo {}`), accents, button.
- Clay `#C89274` — variables, properties, JSX tags, JSON keys, numbers.
- Salvia `#9DB87C` — strings.
- Coral `#E58575` — errors.

#### Verification
- Total replacements: 13 rule foregrounds changed + 6 new rules appended.
- Final token count: 495 (was 489). Final color count: 368 (unchanged).
- The 3 combined "Java/Kotlin/C# type" rules now have shorter scopes (no built-in class part). Built-in types like `String`, `Object`, `Array`, `List` now use teal through dedicated rules, so they no longer "leak" through the primitive-type rules.
- WCAG AA contrast for teal `#7AA0A8` on editor bg `#282523` remains 5.38:1.
- Version stays at `1.1.0`.

## [1.0.0] - 2025-XX-XX

### Added
- Initial release of "Calming Coding" dark theme.
