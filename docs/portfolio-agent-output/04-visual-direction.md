# 04 Visual Direction

## Design Philosophy

The portfolio communicates technical depth and engineering credibility without decorative noise. The visual language is **instrumental**: every element serves a purpose, every animation signals state change, every color carries semantic weight. The aesthetic borrows from developer tooling, observability dashboards, and systems monitoring interfaces — dark environments where information density is high and visual hierarchy is established through luminosity, not hue.

The core principles are:
- **Darkness as default**: The canvas is near-black because engineering work happens in dark environments (IDEs, terminals, dashboards).
- **Color as signal, not decoration**: Color appears only to indicate status, state, or category. No gradients, no decorative blobs.
- **Typography as structure**: Type does the heavy lifting of hierarchy. The typeface must perform at small sizes in dense interfaces.
- **Space as breath**: Dense information needs room to be legible. Generous internal spacing within components, measured gaps between sections.
- **Motion as feedback**: Animations are fast, functional, and minimal. They confirm interactions, reveal state changes, or guide attention — never entertain.

## Color System

### Base Palette

| Token | Hex | Usage |
|---|---|---|
| `--bg-primary` | `#0A0A0B` | Page background, deepest layer |
| `--bg-secondary` | `#141416` | Cards, elevated surfaces, sidebar |
| `--bg-tertiary` | `#1C1C1F` | Hover states, active backgrounds, input fields |
| `--bg-quaternary` | `#232326` | Borders, dividers, subtle separators |

### Text Colors

| Token | Hex | Usage |
|---|---|---|
| `--text-primary` | `#F0F0F2` | Headings, primary content, code keywords |
| `--text-secondary` | `#A1A1AA` | Body text, descriptions, inactive items |
| `--text-tertiary` | `#71717A` | Metadata, timestamps, placeholders, disabled |
| `--text-inverse` | `#0A0A0B` | Text on accent backgrounds |

### Semantic Colors

| Token | Hex | Usage |
|---|---|---|
| `--accent-primary` | `#E8E8EC` | Primary buttons, active nav, important highlights |
| `--accent-success` | `#4ADE80` | Success states, passing CI, resolved issues, positive metrics |
| `--accent-warning` | `#FBBF24` | Warnings, pending states, medium severity |
| `--accent-error` | `#F87171` | Errors, failed pipelines, high severity, incidents |
| `--accent-info` | `#60A5FA` | Information, links, neutral highlights, code strings |
| `--accent-purple` | `#A78BFA` | AI-generated content, agent actions, RAG retrieved context |
| `--accent-orange` | `#FB923C` | n8n workflows, automation nodes, cashback campaigns |

### Usage Rules

- **No gradients anywhere**. Not on buttons, not on backgrounds, not on text. The only permitted gradient is a subtle linear fade on hero section overlays (`rgba(10,10,11,0)` to `rgba(10,10,11,1)`).
- **No blur effects** (glassmorphism). Elevation is communicated through border color and shadow, not backdrop-filter.
- **Color is sparse**: 90% of the interface is grayscale. Semantic colors appear as small indicators (dots, badges, 1px borders) or single-word labels.
- **Links** use `--accent-info` at rest, `--text-primary` on hover, with a 150ms transition.
- **Code blocks** use a custom dark theme with minimal color: comments in `--text-tertiary`, strings in `--accent-info`, keywords in `--accent-success`, functions in `--text-primary`.

## Typography System

### Font Family

**Primary**: `Inter` (Google Fonts, weights 400, 500, 600). A neo-grotesque sans-serif engineered for screen legibility at small sizes. Its tall x-height and open apertures make it ideal for dense technical interfaces.

**Monospace**: `JetBrains Mono` (Google Fonts, weights 400, 500). Used exclusively for code snippets, terminal outputs, API paths, and metric values. Its increased letter height and distinctive ligatures improve code readability.

### Type Scale

| Token | Size | Weight | Line Height | Letter Spacing | Usage |
|---|---|---|---|---|---|
| `display` | 48px | 600 | 1.1 | -0.02em | Hero name, section titles (max 2 per page) |
| `h1` | 32px | 600 | 1.2 | -0.02em | Page titles, major section headers |
| `h2` | 24px | 600 | 1.3 | -0.01em | Project names, subsection headers |
| `h3` | 18px | 500 | 1.4 | -0.01em | Card titles, feature names, metric labels |
| `body` | 14px | 400 | 1.6 | 0 | Paragraphs, descriptions, general content |
| `body-sm` | 13px | 400 | 1.5 | 0 | Card descriptions, secondary content |
| `caption` | 12px | 500 | 1.4 | 0.01em | Labels, badges, tags, overlines, metadata |
| `mono` | 13px | 400 | 1.5 | 0 | Code, terminal output, paths, metric values |
| `mono-sm` | 11px | 400 | 1.4 | 0 | Inline code, small terminal readouts |

### Typography Rules

- **No all-caps text** except for 2-letter status badges ("OK", "MR", "CI").
- **Line length** is capped at 65 characters for body text.
- **Code blocks** have `font-variant-ligatures: none` to prevent ligature confusion in technical content.
- **Metric values** ("5x faster", "$600K+") use monospace font at `mono` size with `--text-primary` color for emphasis.

## Spacing Scale

Based on an 8px grid with 4px half-steps for fine adjustments.

| Token | Value | Usage |
|---|---|---|
| `space-1` | 4px | Icon gaps, inline element spacing |
| `space-2` | 8px | Tight component padding, badge gaps |
| `space-3` | 12px | Button padding, input internal spacing |
| `space-4` | 16px | Card padding, list item gaps |
| `space-5` | 24px | Section internal spacing, card gaps in grids |
| `space-6` | 32px | Subsection spacing |
| `space-7` | 48px | Major section internal padding |
| `space-8` | 64px | Section vertical margins |
| `space-9` | 96px | Major section breaks |
| `space-10` | 128px | Hero section padding |

### Layout Constraints

- **Max content width**: 1200px, centered.
- **Content padding**: `space-5` (24px) on mobile, `space-6` (32px) on tablet, `space-7` (48px) on desktop.
- **Card grid**: 2 columns on desktop (`space-5` gap), 1 column on mobile.
- **Mockup grids**: 1-column for Browser/MacBook mockups, 2-column for iPhone mockups.

## Component Styling

### Cards

- Background: `--bg-secondary`
- Border: 1px solid `--bg-quaternary`
- Border radius: 8px
- Padding: `space-4` (16px) or `space-5` (24px) for feature cards
- Hover: border color transitions to `--text-tertiary`, 200ms ease
- Shadow: none by default. On hover: `0 4px 12px rgba(0,0,0,0.3)`
- No gradient overlays, no glass effects.

### Buttons

**Primary**:
- Background: `--accent-primary`
- Text: `--text-inverse`
- Padding: `space-3` vertical, `space-4` horizontal
- Border radius: 6px
- Font: `caption` size, weight 500
- Hover: opacity 0.9, 150ms ease

**Secondary**:
- Background: transparent
- Border: 1px solid `--bg-quaternary`
- Text: `--text-secondary`
- Hover: background `--bg-tertiary`, border `--text-tertiary`, text `--text-primary`

**Tertiary (Link style)**:
- Background: transparent
- Text: `--accent-info`
- Hover: text `--text-primary`, underline appears

### Tags / Badges

- Background: `--bg-tertiary`
- Border: 1px solid `--bg-quaternary`
- Text: `--text-secondary`, `caption` size
- Padding: `space-1` vertical, `space-2` horizontal
- Border radius: 4px
- Status badges use semantic colors for left border (3px) or dot indicator.

### Code Blocks

- Background: `--bg-secondary`
- Border: 1px solid `--bg-quaternary`
- Border radius: 8px
- Padding: `space-4`
- Font: `mono` size
- Syntax highlighting: minimal palette (4 colors max)
- Line numbers: `mono-sm`, `--text-tertiary`, right-aligned in 40px gutter

### Terminal / Log Outputs

- Background: `#0D0D0F` (slightly darker than page bg)
- Border: 1px solid `--bg-quaternary`
- Border radius: 8px
- Font: `mono-sm`
- Color coding: timestamps in `--text-tertiary`, paths in `--accent-info`, success in `--accent-success`, errors in `--accent-error`
- Scrollable with custom scrollbar (4px width, `--bg-quaternary` track, `--text-tertiary` thumb)

## Animation Guidelines

### Philosophy

Animations are **functional, not decorative**. They reduce cognitive load by signaling state changes and spatial relationships. Every animation must have a purpose: revealing content, confirming an interaction, or indicating loading/processing.

### Timing

| Context | Duration | Easing |
|---|---|---|
| Hover states | 150ms | `ease` |
| Color transitions | 150ms | `ease` |
| Height/opacity reveals | 200ms | `cubic-bezier(0.4, 0, 0.2, 1)` |
| Page transitions | 300ms | `cubic-bezier(0.4, 0, 0.2, 1)` |
| Staggered list items | 50ms delay each | `cubic-bezier(0.4, 0, 0.2, 1)` |
| Skeleton loading | 1.5s infinite | `linear` pulse |

### Specific Patterns

**Scroll Reveals**:
- Elements fade in and translate Y from 12px to 0.
- Triggered at 10% viewport intersection.
- Only applied to major sections, not every card.

**Card Hover**:
- Border color transition only.
- No scale transforms, no lift animations.
- Terminal/cursor blinking inside mock cards is permitted as it simulates live systems.

**Mockup Loading States**:
- Skeleton screens use `--bg-tertiary` pulsing to `--bg-quaternary`.
- Progress bars fill with `--accent-success` or `--accent-info`.
- Typing indicators: 3 dots pulsing sequentially, 400ms each.

**Terminal Typing**:
- Simulated terminal output reveals character by character at 15ms per character.
- Cursor blink: 530ms interval, `--accent-success` color.

**No particle effects, no floating elements, no parallax, no decorative animated backgrounds.**

## Device Mockup Styles

### Browser Mockup

Use for: Web dashboards, GitLab interfaces, admin panels, analytics platforms.

- **Outer frame**: `--bg-secondary` background, 1px `--bg-quaternary` border, 12px border radius.
- **Title bar**: 36px height, `--bg-tertiary` background, contains:
  - Left: 3 traffic light dots (12px each): `--accent-error`, `--accent-warning`, `--accent-success`.
  - Center: address bar, `--bg-primary` background, 6px radius, `--text-tertiary` text showing URL.
  - Right: minimal icons (reload, menu) in `--text-tertiary`.
- **Content area**: `--bg-primary` background, no border-radius on bottom corners (connects to frame).
- **Overflow**: Content inside can scroll; show 8px custom scrollbar if scrollable.
- **Shadow**: `0 25px 50px -12px rgba(0, 0, 0, 0.5)` for elevation.

### MacBook Mockup

Use for: Full application demos, IDE screenshots, complex dashboards.

- **Device frame**: 16px border-radius on outer corners, `--bg-quaternary` bezel (8px).
- **Camera notch**: Centered at top, 12px wide, 4px tall, `--bg-primary`.
- **Screen**: Inside bezel, 8px border-radius, `--bg-primary` background.
- **Keyboard base**: Optional. If shown, subtle gradient from `#1C1C1F` to `#141416`, 20px height, perspective transform.
- **Shadow**: `0 32px 64px -16px rgba(0, 0, 0, 0.6)`.

### iPhone Mockup

Use for: Telegram Mini App demos, mobile dashboards, chat interfaces.

- **Device frame**: 40px border-radius, 12px border in `--bg-quaternary`.
- **Dynamic Island**: Centered at top, 126px wide, 37px tall, `--bg-primary` with `--bg-quaternary` border.
- **Screen**: Inside frame, 36px border-radius, `--bg-primary` background.
- **Home indicator**: Bottom center, 134px wide, 5px tall, `--bg-quaternary`, 3px radius.
- **Buttons**: Silent switch, volume buttons, power button on frame edges (subtle, 2px `--bg-quaternary`).
- **Shadow**: `0 20px 40px -12px rgba(0, 0, 0, 0.5)`.
- **Orientation**: Portrait only for Telegram Mini Apps; landscape optional for games/demos.

## Screenshot Gallery Design

### Layout

- **Grid**: 2-column on desktop, 1-column on mobile.
- **Gap**: `space-5` (24px).
- **Container**: Full width within content bounds, no max-width restriction on images themselves.

### Thumbnail Treatment

- **Aspect ratio**: 16:9 for dashboards, 9:16 for mobile apps.
- **Border**: 1px solid `--bg-quaternary`.
- **Border radius**: 8px (for raw screenshots), 12px (for device mockups).
- **Hover**: Opacity reduces to 0.85, overlay appears with "Expand" text in `--text-primary`.

### Lightbox

- **Backdrop**: `rgba(10, 10, 11, 0.95)` with 200ms fade-in.
- **Image**: Max 90vw / 90vh, centered, 8px border-radius.
- **Caption**: Below image, `caption` size, `--text-secondary`.
- **Navigation**: Arrow keys supported. On-screen arrows are 48px circles, `--bg-secondary` background, `--text-secondary` icon.
- **Close**: Top-right X, 48px hit area. Escape key supported.

### Grouping

- Screenshots are grouped by project.
- Group header: Project name in `h2`, tech stack tags in row below.
- Each group can mix device mockup types (e.g., Browser + iPhone for responsive projects).

## Engineering-Focused Visual Language

### Decorative Elements

- **Grid lines**: Very subtle (`rgba(255,255,255,0.03)`), 1px, can overlay hero sections to evoke blueprints / system architecture diagrams.
- **Corner brackets**: 12px L-shapes in `--bg-quaternary` at corners of feature cards, suggesting focus areas or measurement points.
- **Status dots**: 8px circles, filled with semantic colors, pulsing softly (2s interval) for "live" or "active" indicators.

### Data Visualization

- **Charts**: Minimalist. Single-color bars/lines using `--accent-info` or `--accent-success`. No chart background, no grid lines except horizontal dashed lines at `--bg-quaternary`.
- **Metrics**: Large monospace numbers (`display` size if standalone, `h1` if in grid) with `--text-primary`, label in `caption` with `--text-secondary`.
- **Progress bars**: 4px height, `--bg-tertiary` track, semantic color fill, no border-radius on track, 2px on fill ends.

### Icons

- **Source**: `lucide-react` or similar line-icon set.
- **Style**: 1.5px stroke width, no fill, rounded caps.
- **Color**: `--text-secondary` by default, `--text-primary` on hover, semantic colors for status indicators.
- **Size**: 16px inline, 20px in buttons, 24px in feature cards.

### Texture

- **Noise**: Optional very subtle static grain overlay (`opacity: 0.02`, `mix-blend-mode: overlay`) on the entire page to reduce banding and add tactile quality.
- **No gradients, no blur, no glass, no decorative shapes.**
