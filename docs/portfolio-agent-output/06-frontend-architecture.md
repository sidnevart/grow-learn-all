# Frontend Architecture

## Overview

The portfolio is a statically-exported Next.js 14+ application using the App Router. It showcases projects with both real screenshots and AI-generated mock UIs. The primary goal is a high-performance, accessible, visually rich single-page experience with smooth animations.

## 1. Next.js App Router Structure

### Routing Strategy

We use a single-page application (SPA) architecture with smooth-scroll anchor navigation. The App Router is utilized for its performance benefits and modern React patterns, but the site itself is a single page with section anchors.

```
app/
├── layout.tsx              # Root layout with global providers, metadata, fonts
├── page.tsx                # Main page composing all sections
├── globals.css             # Global styles, Tailwind directives, CSS variables
├── sections/               # Page-level section components
│   ├── hero.tsx
│   ├── projects.tsx
│   ├── experience.tsx
│   ├── about.tsx
│   └── contact.tsx
├── components/             # Reusable components
│   ├── ui/                 # shadcn/ui base components
│   ├── project-card.tsx
│   ├── tag.tsx
│   ├── scroll-reveal.tsx
│   └── mobile-nav.tsx
├── lib/
│   ├── utils.ts            # cn() and other utilities
│   └── data.ts             # Project data and content
├── types/
│   └── index.ts            # Shared TypeScript interfaces
└── hooks/
    └── use-media-query.ts  # Responsive hook for JS logic
```

### Layout (`app/layout.tsx`)

- Loads Google Fonts via `next/font` (Inter for body, JetBrains Mono for code elements).
- Provides `framer-motion` layout animations via `AnimatePresence` if needed.
- Injects global metadata, JSON-LD structured data, and analytics (if applicable).

### Page (`app/page.tsx`)

- Composes all section components in order: Hero -> Projects -> Experience -> About -> Contact.
- Wraps sections in `<main>` with semantic structure.

## 2. TypeScript Strict Mode Setup

### Configuration (`tsconfig.json`)

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "lib": ["dom", "dom.iterable", "ES2022"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "plugins": [{ "name": "next" }],
    "paths": {
      "@/*": ["./*"]
    },
    "forceConsistentCasingInFileNames": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "noUncheckedIndexedAccess": true
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules", "out", "dist"]
}
```

### Key TypeScript Rules

- **Strict mode enabled**: All strict flags are active to catch potential runtime errors at compile time.
- **No unchecked indexed access**: Prevents `undefined` runtime errors when accessing array/object elements.
- **Unused locals/parameters**: Enforces clean code by preventing dead variables.
- **Path aliases**: `@/*` maps to the project root for clean imports.

## 3. Tailwind CSS Configuration

### Configuration (`tailwind.config.ts`)

```typescript
import type { Config } from "tailwindcss";

const config: Config = {
  darkMode: ["class"],
  content: [
    "./pages/**/*.{js,ts,jsx,tsx,mdx}",
    "./components/**/*.{js,ts,jsx,tsx,mdx}",
    "./app/**/*.{js,ts,jsx,tsx,mdx}",
  ],
  theme: {
    extend: {
      colors: {
        background: "hsl(var(--background))",
        foreground: "hsl(var(--foreground))",
        card: {
          DEFAULT: "hsl(var(--card))",
          foreground: "hsl(var(--card-foreground))",
        },
        popover: {
          DEFAULT: "hsl(var(--popover))",
          foreground: "hsl(var(--popover-foreground))",
        },
        primary: {
          DEFAULT: "hsl(var(--primary))",
          foreground: "hsl(var(--primary-foreground))",
        },
        secondary: {
          DEFAULT: "hsl(var(--secondary))",
          foreground: "hsl(var(--secondary-foreground))",
        },
        muted: {
          DEFAULT: "hsl(var(--muted))",
          foreground: "hsl(var(--muted-foreground))",
        },
        accent: {
          DEFAULT: "hsl(var(--accent))",
          foreground: "hsl(var(--accent-foreground))",
        },
        destructive: {
          DEFAULT: "hsl(var(--destructive))",
          foreground: "hsl(var(--destructive-foreground))",
        },
        border: "hsl(var(--border))",
        input: "hsl(var(--input))",
        ring: "hsl(var(--ring))",
      },
      borderRadius: {
        lg: "var(--radius)",
        md: "calc(var(--radius) - 2px)",
        sm: "calc(var(--radius) - 4px)",
      },
      fontFamily: {
        sans: ["var(--font-inter)", "system-ui", "sans-serif"],
        mono: ["var(--font-jetbrains-mono)", "monospace"],
      },
      animation: {
        "fade-in": "fadeIn 0.5s ease-out forwards",
        "slide-up": "slideUp 0.5s ease-out forwards",
        "float": "float 6s ease-in-out infinite",
      },
      keyframes: {
        fadeIn: {
          "0%": { opacity: "0" },
          "100%": { opacity: "1" },
        },
        slideUp: {
          "0%": { opacity: "0", transform: "translateY(20px)" },
          "100%": { opacity: "1", transform: "translateY(0)" },
        },
        float: {
          "0%, 100%": { transform: "translateY(0)" },
          "50%": { transform: "translateY(-10px)" },
        },
      },
    },
  },
  plugins: [require("tailwindcss-animate")],
};

export default config;
```

### CSS Variables (`app/globals.css`)

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  :root {
    --background: 0 0% 100%;
    --foreground: 240 10% 3.9%;
    --card: 0 0% 100%;
    --card-foreground: 240 10% 3.9%;
    --popover: 0 0% 100%;
    --popover-foreground: 240 10% 3.9%;
    --primary: 240 5.9% 10%;
    --primary-foreground: 0 0% 98%;
    --secondary: 240 4.8% 95.9%;
    --secondary-foreground: 240 5.9% 10%;
    --muted: 240 4.8% 95.9%;
    --muted-foreground: 240 3.8% 46.1%;
    --accent: 240 4.8% 95.9%;
    --accent-foreground: 240 5.9% 10%;
    --destructive: 0 84.2% 60.2%;
    --destructive-foreground: 0 0% 98%;
    --border: 240 5.9% 90%;
    --input: 240 5.9% 90%;
    --ring: 240 5.9% 10%;
    --radius: 0.75rem;
  }

  .dark {
    --background: 240 10% 3.9%;
    --foreground: 0 0% 98%;
    --card: 240 10% 3.9%;
    --card-foreground: 0 0% 98%;
    --popover: 240 10% 3.9%;
    --popover-foreground: 0 0% 98%;
    --primary: 0 0% 98%;
    --primary-foreground: 240 5.9% 10%;
    --secondary: 240 3.7% 15.9%;
    --secondary-foreground: 0 0% 98%;
    --muted: 240 3.7% 15.9%;
    --muted-foreground: 240 5% 64.9%;
    --accent: 240 3.7% 15.9%;
    --accent-foreground: 0 0% 98%;
    --destructive: 0 62.8% 30.6%;
    --destructive-foreground: 0 0% 98%;
    --border: 240 3.7% 15.9%;
    --input: 240 3.7% 15.9%;
    --ring: 240 4.9% 83.9%;
  }
}
```

### Tailwind Conventions

- Use `hsl()` color format with CSS variables for easy dark mode support.
- Prefer utility classes over custom CSS; use `@apply` only for complex repeating patterns.
- Group related utilities with arbitrary values sparingly.

## 4. shadcn/ui Component Strategy

### Philosophy

Use shadcn/ui as a foundation for accessible, well-designed base components. Customize them via Tailwind classes and CSS variables to match the portfolio's aesthetic. Do not install unused components to keep bundle size minimal.

### Installation Pattern

```bash
npx shadcn add button badge card dialog separator
```

### Base Components Used

| Component | Purpose | Customization |
|-----------|---------|---------------|
| `button` | CTA links, external links | Remove default radius for pill shape if needed |
| `badge` | Tech stack tags, status labels | Custom color variants per category |
| `card` | Project cards, experience items | Enhanced with hover states and animations |
| `dialog` | Image lightbox for project screenshots | Backdrop blur, max-width constraints |
| `separator` | Visual dividers between sections | Subtle opacity |

### Component Customization Rules

1. **Never modify node_modules**: Copy shadcn components to `app/components/ui/` and modify there.
2. **Theme via CSS variables**: All color changes go through `globals.css` variables.
3. **Composition over configuration**: Build complex components by composing base shadcn primitives rather than adding props.

## 5. Framer Motion Animation Patterns

### Philosophy

Animations enhance the experience without hindering performance or accessibility. All motion follows a consistent timing system and respects `prefers-reduced-motion`.

### Timing Tokens

```typescript
const transitions = {
  fast: { duration: 0.15, ease: "easeOut" },
  default: { duration: 0.3, ease: [0.25, 0.1, 0.25, 1] },
  slow: { duration: 0.5, ease: [0.25, 0.1, 0.25, 1] },
  spring: { type: "spring", stiffness: 300, damping: 30 },
};
```

### Patterns

**1. Scroll Reveal (Viewport Entry)**

```tsx
import { motion } from "framer-motion";

export function ScrollReveal({ children, delay = 0 }) {
  return (
    <motion.div
      initial={{ opacity: 0, y: 24 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true, margin: "-50px" }}
      transition={{ duration: 0.5, delay, ease: [0.25, 0.1, 0.25, 1] }}
    >
      {children}
    </motion.div>
  );
}
```

**2. Staggered Children**

```tsx
const container = {
  hidden: { opacity: 0 },
  show: {
    opacity: 1,
    transition: { staggerChildren: 0.1 },
  },
};

const item = {
  hidden: { opacity: 0, y: 16 },
  show: { opacity: 1, y: 0 },
};

// Usage for project grid
<motion.div variants={container} initial="hidden" whileInView="show">
  {projects.map((p) => (
    <motion.div key={p.id} variants={item}>
      <ProjectCard project={p} />
    </motion.div>
  ))}
</motion.div>
```

**3. Hover Micro-interactions**

```tsx
<motion.div
  whileHover={{ y: -4, scale: 1.01 }}
  transition={{ type: "spring", stiffness: 400, damping: 25 }}
>
  <ProjectCard />
</motion.div>
```

**4. Page Load Sequence**

Hero elements animate in a choreographed sequence on initial load:
- Title: fade up, 0ms delay
- Subtitle: fade up, 150ms delay
- CTA buttons: fade up, 300ms delay

### Performance Rules

- Use `will-change: transform` on animated elements (handled by Framer Motion).
- Animate only `transform` and `opacity` to stay on the compositor thread.
- Use `viewport={{ once: true }}` to prevent re-triggering animations on scroll back.
- Respect `prefers-reduced-motion: reduce` by disabling non-essential animations.

## 6. Content Model

### MDX vs TypeScript

**Decision**: Use TypeScript data files for structured content and static TypeScript strings for simple text. MDX is not required for this portfolio since content is relatively static and structured.

**Rationale**:
- Project data is highly structured (name, description, tech stack, screenshots, links).
- No need for markdown rendering within project descriptions.
- Type safety is paramount; TypeScript objects provide compile-time checking.
- Simpler build pipeline without MDX processing.

**Content Strategy**:

| Content Type | Format | Location |
|-------------|--------|----------|
| Project data | TypeScript objects | `lib/data.ts` |
| Site copy (hero, about) | TypeScript strings | `lib/data.ts` or inline in sections |
| Static metadata | `next.config.js` / `layout.tsx` | App-level config |

### Future-Proofing

If blog or dynamic content is needed later, introduce `contentlayer` or MDX with a `content/` directory without disrupting existing architecture.

## 7. Project Data Structure

### TypeScript Interface

```typescript
// types/index.ts

export interface Project {
  id: string;
  name: string;
  category: "work" | "freelance" | "personal" | "university";
  description: string;
  longDescription?: string;
  techStack: string[];
  screenshots: Screenshot[];
  links: {
    demo?: string;
    github?: string;
    caseStudy?: string;
  };
  featured: boolean;
  startDate: string; // ISO date
  endDate?: string;
  status: "completed" | "in-progress" | "maintained";
}

export interface Screenshot {
  src: string;
  alt: string;
  caption?: string;
  type: "real" | "mock";
}

export interface Experience {
  id: string;
  company: string;
  role: string;
  period: string;
  description: string;
  achievements: string[];
  technologies: string[];
}
```

### Data Organization (`lib/data.ts`)

```typescript
export const projects: Project[] = [
  {
    id: "ai-code-review",
    name: "AI Code Review for GitLab",
    category: "work",
    description: "AI-powered merge request review system.",
    techStack: ["React", "TypeScript", "GitLab API", "OpenAI"],
    screenshots: [
      { src: "/images/projects/ai-code-review-1.jpg", alt: "Dashboard", type: "mock" },
    ],
    links: { github: "https://github.com/sidnevart/..." },
    featured: true,
    startDate: "2024-01",
    status: "completed",
  },
  // ... more projects
];

export const experience: Experience[] = [
  // ... experience items
];

export const siteConfig = {
  name: "Artem Sidnev",
  title: "Frontend Engineer",
  description: "Building AI-native tools and interfaces at T-Bank.",
  url: "https://sidnev.dev",
  email: "artem@sidnev.dev",
  social: {
    github: "https://github.com/sidnevart",
    linkedin: "https://linkedin.com/in/sidnevart",
    telegram: "https://t.me/sidnevart",
  },
};
```

### Screenshot Naming Convention

- Format: `{project-id}-{index}.{ext}`
- Examples: `ai-code-review-1.png`, `cumock-frontend-2.jpg`
- All screenshots stored in `public/images/projects/`

## 8. Component Hierarchy

### Top-Level Composition

```
RootLayout
└── Page
    ├── Navigation (fixed, blur backdrop)
    ├── HeroSection
    │   ├── HeroText (animated)
    │   └── CTAGroup
    ├── ProjectsSection
    │   ├── SectionHeader
    │   └── ProjectGrid
    │       └── ProjectCard (xN)
    │           ├── ScreenshotCarousel
    │           ├── ProjectMeta
    │           └── TechStack (Tag[])
    ├── ExperienceSection
    │   ├── SectionHeader
    │   └── ExperienceTimeline
    │       └── ExperienceCard (xN)
    ├── AboutSection
    │   ├── BioText
    │   └── SkillsCloud
    └── Footer
        ├── SocialLinks
        └── Copyright
```

### Component Categories

| Category | Path | Responsibility |
|----------|------|----------------|
| Sections | `app/sections/` | Full-width page sections, compose layout |
| UI Primitives | `app/components/ui/` | shadcn/ui base components |
| Domain Components | `app/components/` | Portfolio-specific reusable components |
| Hooks | `app/hooks/` | Shared custom React hooks |
| Utilities | `app/lib/` | Data, helpers, constants |
| Types | `app/types/` | Shared TypeScript definitions |

### Component Rules

1. **Sections are page-specific**: They are not reused across pages and live in `sections/`.
2. **Components are domain-agnostic within their scope**: A `ProjectCard` knows about projects but not about section layout.
3. **Props interfaces are co-located**: Each component file exports its own props interface unless shared across multiple components.
4. **Client vs Server**: Mark components with `"use client"` only when they use browser APIs, hooks, or Framer Motion. Default to Server Components for static content.

## 9. File/Folder Structure

```
my-portfolio/
├── app/                          # Next.js App Router
│   ├── sections/                 # Page sections
│   │   ├── hero.tsx
│   │   ├── projects.tsx
│   │   ├── experience.tsx
│   │   ├── about.tsx
│   │   └── contact.tsx
│   ├── components/               # Reusable components
│   │   ├── ui/                   # shadcn/ui components (auto-generated)
│   │   │   ├── button.tsx
│   │   │   ├── badge.tsx
│   │   │   ├── card.tsx
│   │   │   └── dialog.tsx
│   │   ├── project-card.tsx
│   │   ├── experience-card.tsx
│   │   ├── tag.tsx
│   │   ├── screenshot-carousel.tsx
│   │   ├── scroll-reveal.tsx
│   │   ├── mobile-nav.tsx
│   │   └── social-links.tsx
│   ├── hooks/
│   │   └── use-media-query.ts
│   ├── lib/
│   │   ├── utils.ts              # cn() utility
│   │   └── data.ts               # All content data
│   ├── types/
│   │   └── index.ts
│   ├── globals.css
│   ├── layout.tsx
│   └── page.tsx
├── public/                       # Static assets
│   ├── images/
│   │   ├── projects/             # Project screenshots
│   │   │   ├── ai-code-review-1.png
│   │   │   ├── cumock-frontend-1.jpg
│   │   │   └── ...
│   │   └── og-image.jpg          # OpenGraph image
│   └── resume.pdf
├── docs/                         # Documentation
│   └── portfolio-agent-output/   # Agent outputs
├── scripts/                      # Automation scripts
│   └── capture-screenshots.ts
├── config/                       # Configuration files
│   └── screenshot-projects.ts
├── tailwind.config.ts
├── tsconfig.json
├── next.config.js
├── package.json
└── README.md
```

## 10. SEO Implementation

### Metadata Strategy

Next.js 14 App Router metadata API is used for all SEO-related tags.

```typescript
// app/layout.tsx
import { Metadata } from "next";

export const metadata: Metadata = {
  title: {
    default: "Artem Sidnev — Frontend Engineer",
    template: "%s | Artem Sidnev",
  },
  description:
    "Building AI-native tools and interfaces. Portfolio of frontend engineering work at T-Bank and beyond.",
  keywords: [
    "Frontend Engineer",
    "React",
    "Next.js",
    "TypeScript",
    "AI Tools",
    "T-Bank",
  ],
  authors: [{ name: "Artem Sidnev" }],
  creator: "Artem Sidnev",
  openGraph: {
    type: "website",
    locale: "en_US",
    url: "https://sidnev.dev",
    siteName: "Artem Sidnev",
    images: [
      {
        url: "/images/og-image.jpg",
        width: 1200,
        height: 630,
        alt: "Artem Sidnev — Frontend Engineer",
      },
    ],
  },
  twitter: {
    card: "summary_large_image",
    creator: "@sidnevart",
    images: ["/images/og-image.jpg"],
  },
  robots: {
    index: true,
    follow: true,
    googleBot: {
      index: true,
      follow: true,
      "max-video-preview": -1,
      "max-image-preview": "large",
      "max-snippet": -1,
    },
  },
  verification: {
    google: "google-site-verification-code",
  },
  alternates: {
    canonical: "https://sidnev.dev",
  },
};
```

### Structured Data (JSON-LD)

```tsx
// Inside layout.tsx <head>
<script
  type="application/ld+json"
  dangerouslySetInnerHTML={{
    __html: JSON.stringify({
      "@context": "https://schema.org",
      "@type": "Person",
      name: "Artem Sidnev",
      jobTitle: "Frontend Engineer",
      url: "https://sidnev.dev",
      sameAs: [
        "https://github.com/sidnevart",
        "https://linkedin.com/in/sidnevart",
        "https://t.me/sidnevart",
      ],
      worksFor: {
        "@type": "Organization",
        name: "T-Bank",
      },
    }),
  }}
/>
```

### Semantic HTML

- Use `<header>`, `<main>`, `<footer>`, `<section>`, `<article>`, `<nav>`, `<time>`.
- Each section has an `id` for anchor navigation (`#projects`, `#experience`, etc.).
- Heading hierarchy is strictly maintained: single `<h1>`, logical `<h2>` -> `<h3>` progression.

## 11. Image Optimization Strategy

### Next.js Image Component

All images use `next/image` for automatic optimization:

```tsx
import Image from "next/image";

<Image
  src="/images/projects/ai-code-review-1.png"
  alt="AI Code Review Dashboard"
  width={1200}
  height={800}
  className="rounded-lg object-cover"
  placeholder="blur"
  blurDataURL="data:image/jpeg;base64,..."
  priority={featured}
/>
```

### Screenshot Handling

| Aspect | Rule |
|--------|------|
| Format | PNG for mock UIs (sharp edges), JPEG for photos |
| Dimensions | Standardize to 1200x800 or 16:10 aspect ratio |
| Quality | 85% for JPEG, max compression for PNG |
| Loading | `loading="lazy"` for below-fold; `priority` for hero |
| Placeholder | Generate blurDataURL for above-fold images |

### Screenshot Pipeline

1. Capture or generate screenshots at 1440x900 viewport.
2. Batch optimize using `sharp` or Squoosh CLI.
3. Store originals in `scripts/assets/`; optimized versions in `public/images/projects/`.
4. Do not commit unoptimized images.

## 12. Responsive Breakpoints

### Tailwind Default Breakpoints

| Breakpoint | Width | Usage |
|-----------|-------|-------|
| `sm` | 640px | Minor adjustments |
| `md` | 768px | Tablet layout, mobile nav appears |
| `lg` | 1024px | Desktop layout, side-by-side sections |
| `xl` | 1280px | Wide desktop, max content width |
| `2xl` | 1536px | Ultra-wide, expanded grids |

### Layout Strategy

- **Mobile-first**: Base styles target mobile; use `md:` and `lg:` for larger screens.
- **Container**: Max-width `1280px` (`max-w-7xl`) centered with `mx-auto` and responsive padding.
- **Project Grid**: 1 column mobile, 2 columns tablet (`md:grid-cols-2`), 3 columns desktop (`lg:grid-cols-3`).
- **Hero**: Stacked on mobile, side-by-side on desktop (`lg:flex-row`).
- **Navigation**: Hamburger menu on mobile (`md:hidden`), horizontal links on desktop.

### Custom Breakpoints (if needed)

```typescript
// tailwind.config.ts
screens: {
  'xs': '475px',
  // ... defaults
}
```

## 13. Accessibility Requirements

### WCAG 2.1 Level AA Compliance

1. **Color Contrast**
   - Text on background: minimum 4.5:1 ratio.
   - Large text (18px+ bold, 24px+ regular): minimum 3:1 ratio.
   - Test all color combinations with a contrast checker.

2. **Keyboard Navigation**
   - All interactive elements are reachable via `Tab`.
   - Visible focus rings using `focus-visible:ring-2`.
   - Skip-to-content link for keyboard users.

3. **ARIA Labels**
   - Navigation landmarks with `aria-label`.
   - Image alt text is descriptive and contextual.
   - Icon-only buttons have `aria-label`.
   - Live regions for dynamic content updates.

4. **Motion Preferences**
   - Wrap Framer Motion in `useReducedMotion` hook.
   - Provide instant state changes when `prefers-reduced-motion: reduce` is active.

```tsx
import { useReducedMotion } from "framer-motion";

function AnimatedSection({ children }) {
  const shouldReduceMotion = useReducedMotion();

  return (
    <motion.div
      initial={shouldReduceMotion ? false : { opacity: 0, y: 24 }}
      // ...
    >
      {children}
    </motion.div>
  );
}
```

5. **Semantic HTML**
   - Correct heading hierarchy (no skipped levels).
   - Lists (`<ul>`, `<ol>`) for grouped items.
   - `<time>` with `datetime` attribute for dates.
   - `<figure>` and `<figcaption>` for screenshots with captions.

6. **Images**
   - All screenshots have meaningful `alt` text.
   - Decorative images have empty `alt=""`.
   - Complex diagrams include extended descriptions if necessary.

7. **Forms (if applicable)**
   - Labels explicitly associated with inputs.
   - Error messages linked via `aria-describedby`.
   - Sufficient touch targets (minimum 44x44px).

8. **Testing Checklist**
   - [ ] Lighthouse accessibility audit: 100 score.
   - [ ] Keyboard-only navigation test.
   - [ ] Screen reader test (VoiceOver / NVDA).
   - [ ] Color contrast audit.
   - [ ] Reduced motion preference test.
