# Personal Website

A minimalistic personal website built with Astro, featuring blog posts, quick updates, and project showcases.

## Features

- **Blog**: Long-form articles with tag filtering
- **Posts**: Quick thoughts and updates (Twitter/LinkedIn style)
- **Projects**: Portfolio showcase with live demos and source code
- **Dark/Light Mode**: Theme toggle with system preference detection
- **SEO Optimized**: Meta tags, sitemap, Open Graph support
- **Fast**: Zero JavaScript by default, excellent Core Web Vitals

## Tech Stack

- **Astro 5.x**: Static site generator
- **TypeScript**: Strict type checking
- **Content Collections**: Type-safe content management
- **CSS Variables**: GitHub-inspired color system
- **Cloudflare Pages**: Deployment

## Getting Started

### Prerequisites

- Node.js 24 LTS
- npm

### Installation

```bash
# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Project Structure

```
/
├── src/
│   ├── content/
│   │   ├── blog/          # Blog posts (long-form)
│   │   ├── posts/         # Quick updates
│   │   ├── projects/      # Project showcases
│   │   └── config.ts      # Content collections config
│   ├── components/
│   │   ├── Header.astro
│   │   ├── Footer.astro
│   │   └── ThemeToggle.astro
│   ├── layouts/
│   │   └── BaseLayout.astro
│   ├── pages/
│   │   ├── index.astro
│   │   ├── blog/
│   │   ├── posts/
│   │   └── projects/
│   └── styles/
│       └── global.css
├── public/
│   ├── favicon.svg
│   └── robots.txt
└── astro.config.mjs
```

## Content Collections

### Blog Posts

Located in `src/content/blog/`:

```markdown
---
title: "Post Title"
description: "Post description"
publishDate: 2024-01-15
tags: ["tag1", "tag2"]
---

Content here...
```

### Posts (Updates)

Located in `src/content/posts/`:

```markdown
---
publishDate: 2024-03-15
---

Quick thought or update...
```

### Projects

Located in `src/content/projects/`:

```markdown
---
title: "Project Name"
description: "Project description"
publishDate: 2024-01-10
tags: ["react", "typescript"]
link: "https://demo.com"
github: "https://github.com/user/repo"
image: "/project-image.png"
---

Project details...
```

## Customization

### Update Site Information

1. **Site URL**: Update `site` in `astro.config.mjs`
2. **Name**: Replace "Your Name" in components and content
3. **Social Links**: Update URLs in `Footer.astro`
4. **Favicon**: Replace `public/favicon.svg` with your own
5. **OG Image**: Replace `public/og-image.png` with a 1200x630 image

### Color Theme

Colors are defined in `src/styles/global.css` using CSS variables:

```css
:root {
  --color-bg: #ffffff;
  --color-text: #24292f;
  --color-accent: #0969da;
  /* ... */
}

[data-theme="dark"] {
  --color-bg: #0d1117;
  --color-text: #e6edf3;
  --color-accent: #58a6ff;
  /* ... */
}
```

## Deployment

### Cloudflare Pages

1. Push to GitHub
2. Connect repository to Cloudflare Pages
3. Set build command: `npm run build`
4. Set output directory: `dist`
5. Deploy

### Other Platforms

Works with any static hosting:
- Vercel
- Netlify
- GitHub Pages
- AWS S3 + CloudFront

## License

MIT
