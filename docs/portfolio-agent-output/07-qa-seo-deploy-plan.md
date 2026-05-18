# QA, SEO & Deployment Plan

## 1. Playwright Screenshot Pipeline

### Overview

A TypeScript-based Playwright script captures consistent screenshots of projects that have real frontends (e.g., URВИ!, Cumock). For projects without a frontend, AI-generated mock screenshots are used instead. The pipeline ensures standardized dimensions, privacy-safe content, and automated output to the project's public assets directory.

### File: `scripts/capture-screenshots.ts`

```typescript
#!/usr/bin/env tsx
/**
 * Screenshot Capture Pipeline
 *
 * Usage:
 *   npx tsx scripts/capture-screenshots.ts              # Capture all
 *   npx tsx scripts/capture-screenshots.ts --project urvi  # Capture specific
 *   npx tsx scripts/capture-screenshots.ts --list       # List targets
 */

import { chromium, Browser, Page } from "playwright";
import { mkdir, readdir } from "fs/promises";
import { join, dirname, basename } from "path";
import { fileURLToPath } from "url";
import screenshotProjects, { ScreenshotTarget } from "../config/screenshot-projects";

const __filename = fileURLToPath(import.meta.url);
const __dirname = dirname(__filename);

const OUTPUT_DIR = join(__dirname, "..", "public", "images", "projects");
const VIEWPORT = { width: 1440, height: 900 };
const DEVICE_SCALE_FACTOR = 2;

async function ensureDir(dir: string): Promise<void> {
  await mkdir(dir, { recursive: true });
}

async function captureScreenshot(
  browser: Browser,
  target: ScreenshotTarget
): Promise<void> {
  const context = await browser.newContext({
    viewport: VIEWPORT,
    deviceScaleFactor: DEVICE_SCALE_FACTOR,
  });

  const page: Page = await context.newPage();

  try {
    console.log(`[capture] ${target.name}: navigating to ${target.url}`);
    await page.goto(target.url, {
      waitUntil: target.waitUntil ?? "networkidle",
      timeout: 30000,
    });

    // Execute pre-screenshot actions
    if (target.beforeScreenshot) {
      console.log(`[capture] ${target.name}: running beforeScreenshot hook`);
      await target.beforeScreenshot(page);
    }

    // Wait for specific selector if provided
    if (target.waitForSelector) {
      await page.waitForSelector(target.waitForSelector, { timeout: 10000 });
    }

    // Additional delay for animations/settling
    if (target.delayMs) {
      await page.waitForTimeout(target.delayMs);
    }

    // Capture full page or viewport
    const screenshotOptions = {
      path: join(OUTPUT_DIR, target.outputFileName),
      fullPage: target.fullPage ?? false,
      type: target.outputFileName.endsWith(".png") ? ("png" as const) : ("jpeg" as const),
    };

    await page.screenshot(screenshotOptions);
    console.log(`[capture] ${target.name}: saved to ${target.outputFileName}`);
  } catch (error) {
    console.error(`[capture] ${target.name}: FAILED —`, error);
    throw error;
  } finally {
    await context.close();
  }
}

async function listTargets(): Promise<void> {
  console.log("Available screenshot targets:\n");
  for (const target of screenshotProjects) {
    const outputPath = join(OUTPUT_DIR, target.outputFileName);
    let status = "PENDING";
    try {
      const files = await readdir(OUTPUT_DIR);
      if (files.includes(target.outputFileName)) status = "EXISTS";
    } catch {
      // Directory doesn't exist yet
    }
    console.log(`  [${status}] ${target.id}: ${target.name} → ${target.outputFileName}`);
  }
}

async function main(): Promise<void> {
  const args = process.argv.slice(2);
  const projectFilter = args.find((a) => a.startsWith("--project="))?.split("=")[1];
  const shouldList = args.includes("--list");

  await ensureDir(OUTPUT_DIR);

  if (shouldList) {
    await listTargets();
    return;
  }

  const targets = projectFilter
    ? screenshotProjects.filter((p) => p.id === projectFilter)
    : screenshotProjects;

  if (targets.length === 0) {
    console.error(`No targets found matching "${projectFilter}"`);
    process.exit(1);
  }

  console.log(`Starting screenshot capture for ${targets.length} target(s)...\n`);
  const browser = await chromium.launch({ headless: true });

  try {
    for (const target of targets) {
      await captureScreenshot(browser, target);
    }
    console.log("\nAll screenshots captured successfully.");
  } finally {
    await browser.close();
  }
}

main().catch((err) => {
  console.error(err);
  process.exit(1);
});
```

### File: `config/screenshot-projects.ts`

```typescript
import { Page } from "playwright";

export interface ScreenshotTarget {
  id: string;
  name: string;
  url: string;
  outputFileName: string;
  waitUntil?: "load" | "domcontentloaded" | "networkidle" | "commit";
  waitForSelector?: string;
  delayMs?: number;
  fullPage?: boolean;
  beforeScreenshot?: (page: Page) => Promise<void>;
}

const screenshotProjects: ScreenshotTarget[] = [
  {
    id: "urvi",
    name: "URВИ!",
    url: "https://urvi.app",
    outputFileName: "urvi-1.jpg",
    waitUntil: "networkidle",
    delayMs: 2000,
    fullPage: false,
  },
  {
    id: "cumock-frontend",
    name: "Cumock Frontend",
    url: "https://cumock.example.com", // Replace with real URL
    outputFileName: "cumock-frontend-1.jpg",
    waitUntil: "networkidle",
    waitForSelector: "[data-testid='game-board']",
    delayMs: 1500,
    fullPage: false,
  },
  {
    id: "chappi-ai-office",
    name: "AI Office",
    url: "https://chappi-ai-office.example.com", // Replace with real URL
    outputFileName: "ai-office-1.jpg",
    waitUntil: "networkidle",
    delayMs: 2000,
    fullPage: false,
  },
];

export default screenshotProjects;
```

### Screenshot Capture Rules

1. **No Private Data**
   - Never capture screenshots of environments containing real user data, production databases, or internal dashboards with sensitive information.
   - If a project only exists in a private environment, generate a mock UI instead.
   - For Telegram bots, CRMs, or backend-only projects: always use mock screenshots.

2. **Standardized Dimensions**
   - Viewport: 1440x900 (desktop standard).
   - Device scale factor: 2x for retina clarity.
   - Full-page screenshots are avoided unless specifically needed; viewport captures ensure consistent aspect ratios.

3. **Privacy Anonymization**
   - If a real screenshot contains personal data (names, emails, avatars), use Playwright to hide them before capture:
     ```typescript
     beforeScreenshot: async (page) => {
       // Hide user avatars and names
       await page.addStyleTag({
         content: `[data-testid="user-avatar"], [data-testid="user-name"] { visibility: hidden !important; }`,
       });
       // Replace with placeholder text if needed
       await page.evaluate(() => {
         document.querySelectorAll('[data-testid="user-name"]').forEach((el) => {
           (el as HTMLElement).textContent = "Developer Name";
         });
       });
     },
     ```

4. **Synthetic Data Overlay**
   - When capturing demos, ensure only synthetic/anonymized data is visible.
   - Use test accounts dedicated to portfolio demos.

5. **Naming Convention**
   - `{project-id}-{index}.{ext}`
   - Use `.jpg` for photos and complex UIs, `.png` for mock UIs with sharp edges.

6. **Automation**
   - Screenshots are regenerated on demand, not on every build, to keep CI fast.
   - Store a `screenshots-lock.json` with timestamps to detect stale screenshots.

### npm Scripts

```json
{
  "scripts": {
    "screenshots": "tsx scripts/capture-screenshots.ts",
    "screenshots:list": "tsx scripts/capture-screenshots.ts --list",
    "screenshots:project": "tsx scripts/capture-screenshots.ts --project=",
    "optimize-images": "node scripts/optimize-images.js",
    "prebuild": "npm run optimize-images"
  }
}
```

### Dependencies

```json
{
  "devDependencies": {
    "@types/node": "^20.0.0",
    "playwright": "^1.40.0",
    "tsx": "^4.0.0",
    "typescript": "^5.0.0",
    "sharp": "^0.33.0"
  }
}
```

## 2. SEO Checklist

### Meta Tags

| Tag | Location | Value |
|-----|----------|-------|
| `<title>` | `layout.tsx` metadata | "Artem Sidnev — Frontend Engineer" |
| `meta description` | `layout.tsx` metadata | 150-160 char summary |
| `meta viewport` | `layout.tsx` | `width=device-width, initial-scale=1` |
| `meta robots` | `layout.tsx` | `index, follow` |
| `meta author` | `layout.tsx` | "Artem Sidnev" |
| `meta keywords` | `layout.tsx` | Relevant tech stack keywords |
| `link canonical` | `layout.tsx` alternates | `https://sidnev.dev` |
| `link icon` | `layout.tsx` | `/favicon.ico`, `/icon.svg` |

### OpenGraph

```typescript
openGraph: {
  type: "website",
  locale: "en_US",
  url: "https://sidnev.dev",
  siteName: "Artem Sidnev",
  title: "Artem Sidnev — Frontend Engineer",
  description: "Building AI-native tools and interfaces...",
  images: [
    {
      url: "/images/og-image.jpg",
      width: 1200,
      height: 630,
      alt: "Artem Sidnev Portfolio",
    },
  ],
}
```

### Twitter Cards

```typescript
twitter: {
  card: "summary_large_image",
  title: "Artem Sidnev — Frontend Engineer",
  description: "Building AI-native tools and interfaces...",
  creator: "@sidnevart",
  images: ["/images/og-image.jpg"],
}
```

### Semantic HTML Checklist

- [ ] Single `<h1>` per page (hero title).
- [ ] Logical heading hierarchy (`h1` -> `h2` -> `h3`).
- [ ] `<main>` wraps primary content.
- [ ] `<nav>` for site navigation with `aria-label`.
- [ ] `<article>` for each project card.
- [ ] `<section>` with `id` for each page section.
- [ ] `<time>` with `datetime` for project dates.
- [ ] `<figure>` / `<figcaption>` for screenshots.
- [ ] `<address>` for contact information.
- [ ] Skip-to-content link for keyboard users.

### Sitemap

```typescript
// app/sitemap.ts
import { MetadataRoute } from "next";
import { projects } from "@/lib/data";

export default function sitemap(): MetadataRoute.Sitemap {
  const baseUrl = "https://sidnev.dev";

  const projectPages = projects.map((project) => ({
    url: `${baseUrl}/#${project.id}`,
    lastModified: new Date(),
    changeFrequency: "monthly" as const,
    priority: 0.8,
  }));

  return [
    {
      url: baseUrl,
      lastModified: new Date(),
      changeFrequency: "weekly",
      priority: 1,
    },
    ...projectPages,
  ];
}
```

### robots.txt

```
# public/robots.txt
User-agent: *
Allow: /

Sitemap: https://sidnev.dev/sitemap.xml
```

### Additional SEO

- [ ] Structured data (JSON-LD Person schema) in layout.
- [ ] Google Search Console verification meta tag.
- [ ] All external links use `rel="noopener noreferrer"`.
- [ ] Internal anchor links for sections (`/#projects`, etc.).

## 3. Build / Lint Requirements

### Scripts

```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "lint:fix": "next lint --fix",
    "typecheck": "tsc --noEmit",
    "format": "prettier --write .",
    "format:check": "prettier --check .",
    "test": "playwright test",
    "test:ui": "playwright test --ui",
    "ci": "npm run typecheck && npm run lint && npm run build"
  }
}
```

### ESLint Configuration (`eslint.config.mjs` or `.eslintrc.json`)

```json
{
  "extends": ["next/core-web-vitals", "next/typescript", "plugin:jsx-a11y/recommended"],
  "plugins": ["jsx-a11y"],
  "rules": {
    "jsx-a11y/alt-text": "error",
    "jsx-a11y/anchor-is-valid": "warn",
    "@typescript-eslint/no-unused-vars": ["error", { "argsIgnorePattern": "^_" }],
    "react/no-unescaped-entities": "off"
  }
}
```

### Prettier Configuration (`.prettierrc`)

```json
{
  "semi": true,
  "singleQuote": false,
  "tabWidth": 2,
  "trailingComma": "es5",
  "printWidth": 100,
  "plugins": ["prettier-plugin-tailwindcss"]
}
```

### Pre-Build Checks (CI Pipeline)

1. **TypeScript compilation** (`npm run typecheck`): Zero errors, strict mode.
2. **ESLint** (`npm run lint`): Zero errors, minimal warnings.
3. **Prettier** (`npm run format:check`): All files formatted.
4. **Accessibility**: `axe-core` scan in Playwright tests.
5. **Performance**: Lighthouse CI budget:
   - Performance: >= 90
   - Accessibility: 100
   - Best Practices: >= 90
   - SEO: 100

### Playwright E2E Tests

```typescript
// e2e/portfolio.spec.ts
import { test, expect } from "@playwright/test";

test.describe("Portfolio", () => {
  test.beforeEach(async ({ page }) => {
    await page.goto("/");
  });

  test("has correct title and meta", async ({ page }) => {
    await expect(page).toHaveTitle(/Artem Sidnev/);
    const metaDescription = page.locator('meta[name="description"]');
    await expect(metaDescription).toHaveAttribute("content", /Frontend Engineer/);
  });

  test("hero section is visible", async ({ page }) => {
    await expect(page.locator("#hero")).toBeVisible();
    await expect(page.locator("h1")).toContainText("Artem Sidnev");
  });

  test("navigation scrolls to sections", async ({ page }) => {
    await page.locator('a[href="#projects"]').click();
    await expect(page.locator("#projects")).toBeInViewport();
  });

  test("project cards are rendered", async ({ page }) => {
    const cards = page.locator("[data-testid='project-card']");
    await expect(cards).toHaveCount(>0);
  });

  test("images have alt text", async ({ page }) => {
    const images = page.locator("img");
    for (const img of await images.all()) {
      const alt = await img.getAttribute("alt");
      expect(alt).not.toBeNull();
      expect(alt?.trim()).not.toBe("");
    }
  });

  test("respects reduced motion", async ({ page }) => {
    await page.emulateMedia({ reducedMotion: "reduce" });
    await page.goto("/");
    // Assert no motion-based layout shifts
  });
});
```

## 4. Vercel Deployment Config

### `vercel.json`

```json
{
  "$schema": "https://openapi.vercel.sh/vercel.json",
  "buildCommand": "next build",
  "devCommand": "next dev",
  "installCommand": "npm install",
  "framework": "nextjs",
  "regions": ["fra1"],
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "X-Content-Type-Options",
          "value": "nosniff"
        },
        {
          "key": "X-Frame-Options",
          "value": "DENY"
        },
        {
          "key": "X-XSS-Protection",
          "value": "1; mode=block"
        },
        {
          "key": "Referrer-Policy",
          "value": "strict-origin-when-cross-origin"
        }
      ]
    },
    {
      "source": "/images/(.*)",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=31536000, immutable"
        }
      ]
    }
  ],
  "redirects": [
    {
      "source": "/resume",
      "destination": "/resume.pdf",
      "permanent": true
    }
  ]
}
```

### Environment Variables

| Variable | Value | Required |
|----------|-------|----------|
| `NEXT_PUBLIC_SITE_URL` | `https://sidnev.dev` | Yes |
| `NEXT_PUBLIC_GA_ID` | Google Analytics ID | No |

### Build Settings (Vercel Dashboard)

- **Framework Preset**: Next.js
- **Root Directory**: `./` (or monorepo subpath if applicable)
- **Build Command**: `next build`
- **Output Directory**: `out` (for static export)

### Static Export (`next.config.js`)

```javascript
/** @type {import('next').NextConfig} */
const nextConfig = {
  output: "export",
  distDir: "dist",
  images: {
    unoptimized: true, // Required for static export
  },
  trailingSlash: true,
};

module.exports = nextConfig;
```

### Deployment Branches

| Branch | Environment | URL Pattern |
|--------|-------------|-------------|
| `main` | Production | `https://sidnev.dev` |
| `develop` | Preview | `https://develop.sidnev.dev` |
| Pull Requests | Preview | `https://{project}-git-{branch}.vercel.app` |

### Post-Deployment Verification

1. Lighthouse CI runs on production URL.
2. Sitemap is accessible at `/sitemap.xml`.
3. `robots.txt` is accessible at `/robots.txt`.
4. OG image is accessible at `/images/og-image.jpg`.
5. All project screenshot links resolve (200 OK).

## 5. README Requirements

The repository README must include the following sections with exact content structure.

### `README.md`

```markdown
# Artem Sidnev — Portfolio

A high-performance, accessible portfolio showcasing frontend engineering work.

## Install

```bash
git clone https://github.com/sidnevart/portfolio.git
cd portfolio
npm install
```

## Run Locally

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Build

```bash
npm run build
```

Outputs static files to `dist/`.

## Add a Project

1. Add project data to `app/lib/data.ts`:
   ```typescript
   {
     id: "new-project",
     name: "New Project Name",
     category: "work",
     description: "Short description.",
     techStack: ["React", "TypeScript"],
     screenshots: [
       { src: "/images/projects/new-project-1.png", alt: "Dashboard", type: "mock" }
     ],
     links: { github: "https://github.com/sidnevart/new-project" },
     featured: false,
     startDate: "2024-01",
     status: "completed",
   }
   ```
2. Add screenshot images to `public/images/projects/`.
3. Run `npm run typecheck` to verify.

## Add Screenshots

### Option A: Real Screenshots (Playwright)

1. Update `config/screenshot-projects.ts` with the target URL and settings.
2. Run the capture script:
   ```bash
   npm run screenshots
   ```
3. Images are saved to `public/images/projects/`.

### Option B: AI-Generated Mock Screenshots

For projects without a real frontend, generate mock UIs via an AI image generator and save them to `public/images/projects/`.

## Capture Screenshots with Playwright

### Prerequisites

```bash
npx playwright install chromium
```

### Capture All

```bash
npm run screenshots
```

### Capture Specific Project

```bash
npm run screenshots:project=urvi
```

### List Available Targets

```bash
npm run screenshots:list
```

### Privacy Guidelines

- Do not capture screenshots containing real user data, PII, or production secrets.
- Use test accounts and synthetic data for all demos.
- Anonymize names, emails, and avatars before capture using the `beforeScreenshot` hook in `config/screenshot-projects.ts`.
- For backend-only projects (Telegram bots, CRMs), use mock screenshots only.

## Deploy to Vercel

### Automatic Deployments

1. Connect the GitHub repository to Vercel.
2. Push to `main` triggers production deployment.
3. Pull requests generate preview deployments.

### Manual Deployment

```bash
npm i -g vercel
vercel --prod
```

### Environment Variables

Set in Vercel dashboard or via CLI:

```bash
vercel env add NEXT_PUBLIC_SITE_URL
```

## Tech Stack

- [Next.js 14](https://nextjs.org/) (App Router)
- [React 18](https://react.dev/)
- [TypeScript](https://www.typescriptlang.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [shadcn/ui](https://ui.shadcn.com/)
- [Framer Motion](https://www.framer.com/motion/)
- [Playwright](https://playwright.dev/)

## License

MIT
```
