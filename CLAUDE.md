# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Astro starter project using the basics template. Astro is a modern static site builder that allows you to build faster websites with less client-side JavaScript.

## Common Development Commands

```bash
# Install dependencies
npm install

# Start development server (runs on localhost:4321)
npm run dev

# Build for production (outputs to ./dist/)
npm run build

# Preview production build locally
npm run preview

# Run Astro CLI commands
npm run astro -- --help
```

## Code Architecture

### Project Structure
- `/src/pages/` - File-based routing; each `.astro` file becomes a route
- `/src/components/` - Reusable Astro components
- `/src/layouts/` - Page layout templates
- `/src/assets/` - Processed assets (images, styles)
- `/public/` - Static assets served as-is
- `/dist/` - Production build output (gitignored)

### Key Technologies
- **Astro Components** (.astro files) - Component format combining HTML, CSS, and JavaScript
- **TypeScript** - Strict TypeScript configuration enabled
- **ES Modules** - Project uses type: "module" in package.json

### Component Structure
Astro components use a fence (---) to separate the component script from the component template:

```astro
---
// Component Script (JavaScript/TypeScript)
const { title } = Astro.props;
---

<!-- Component Template (HTML) -->
<h1>{title}</h1>
<style>
  /* Component styles */
</style>
```

### Routing
Pages are created by adding `.astro` files to `src/pages/`. The file path determines the route:
- `src/pages/index.astro` → `/`
- `src/pages/about.astro` → `/about`
- `src/pages/blog/[slug].astro` → `/blog/:slug` (dynamic route)