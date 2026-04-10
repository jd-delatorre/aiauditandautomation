# Strategy: NJ AI Automation Website Redesign

## Goal
Replace the current light-themed landing page with the new dark glassmorphism design, while fixing all copy, branding, and pricing to target NJ small/mid-size business owners instead of enterprise CTOs. The site has 110 visitors and 0 conversions -- every change must serve the goal of getting SMB owners to book an AI Automation Audit via Calendly.

## Tech Stack & Architecture
- **Single file rewrite**: `/landing-page/index.html` (only file modified)
- **Tailwind CSS** via CDN (`cdn.tailwindcss.com`) with custom config for the design system color palette
- **Typography**: Space Grotesk (headings) + Inter (body) from Google Fonts
- **Icons**: Material Symbols Outlined from Google Fonts
- **Design patterns**: Glassmorphism (backdrop-blur), tonal depth (surface layers instead of borders), bento grid layouts
- **Deployment**: Static HTML on Vercel (existing `vercel.json` unchanged)
- **Analytics**: Vercel Web Analytics script preserved
- **SEO**: All existing meta tags, structured data, canonical URL preserved

## Key Risks & Open Questions
- [x] Risk: External Google-hosted images (`lh3.googleusercontent.com/aida-public/...`) could go down -- acceptable for now, replace with self-hosted later
- [ ] Open: Should the "founding member" free audit offer have an explicit deadline or cap?
- [ ] Risk: Tailwind CDN adds ~300KB to page load -- acceptable for launch, consider build step later

## Out of Scope
- No changes to `vercel.json`, `package.json`, or deployment config
- No new pages (about, contact, etc.) -- single landing page only
- No JavaScript frameworks or build tools
- No self-hosting images (use existing external URLs for now)
- No Calendly embed -- keep linking to external Calendly page
