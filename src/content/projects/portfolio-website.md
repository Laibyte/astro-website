---
title: "Portfolio Website"
description: "A minimalistic portfolio website built with Astro, featuring blog posts, project showcase, and dark mode."
publishDate: 2024-03-15
tags: ["astro", "typescript", "css"]
github: "https://github.com/yourusername/portfolio"
link: "https://yourname.dev"
---

# Portfolio Website

This is the website you're currently viewing! Built with Astro to showcase my work and share my thoughts on software development.

## Design Philosophy

- **Minimalistic**: Clean design inspired by GitHub's color system
- **Fast**: Zero JavaScript by default, blazing fast page loads
- **Accessible**: Semantic HTML, proper ARIA labels, keyboard navigation
- **Responsive**: Mobile-first design that works on all devices

## Features

### Content Collections

Three distinct content types:

1. **Blog**: Long-form articles about development and technology
2. **Posts**: Quick thoughts and updates (Twitter/LinkedIn style)
3. **Projects**: Detailed project showcases with demos and source code

### Theme Toggle

Implemented a lightweight theme switcher:

```typescript
const theme = (() => {
  if (typeof localStorage !== 'undefined' && localStorage.getItem('theme')) {
    return localStorage.getItem('theme');
  }
  if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
    return 'dark';
  }
  return 'light';
})();

document.documentElement.setAttribute('data-theme', theme);
```

### SEO Optimization

- Meta tags with Open Graph and Twitter Cards
- Automatic sitemap generation
- Semantic HTML structure
- Fast Core Web Vitals scores

## Tech Stack

- **Framework**: Astro 5.x
- **Language**: TypeScript (strict mode)
- **Styling**: Pure CSS with CSS variables
- **Deployment**: Cloudflare Pages
- **CI/CD**: GitHub Actions

## Performance

Lighthouse scores across the board:

- Performance: 100
- Accessibility: 100
- Best Practices: 100
- SEO: 100

## Key Learnings

1. Content Collections provide excellent type safety
2. CSS variables make theming simple and performant
3. Astro's island architecture is perfect for mostly-static sites
4. Zero-JS approach significantly improves loading times

## Future Plans

- [ ] RSS feed for blog
- [ ] Search functionality
- [ ] Reading time estimates
- [ ] Table of contents for long articles
- [ ] Social share buttons
