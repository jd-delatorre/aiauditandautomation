# Deployment Guide — NJ AI Automation Landing Page

## Project Structure

```
landing-page/
├── index.html      # Main page
├── logo.png        # Logo
├── og-image.png    # Social sharing image (1200x630)
├── og-image.svg    # Editable source
├── package.json    # Project metadata
└── vercel.json     # Vercel config (headers, caching, clean URLs)
```

## Vercel Configuration

The `vercel.json` includes:
- **Security headers** — X-Frame-Options, XSS protection, Content-Type-Options
- **Asset caching** — 1 year cache for images, CSS, JS
- **Clean URLs** — No `.html` extension needed
- **No trailing slashes** — Cleaner URLs

---

## Deployment Options

### Option 1: Vercel CLI

```bash
cd /Users/johndelatorre/clawd/projects/openclaw-services/landing-page
npx vercel
```

Follow the prompts to link to your Vercel account and deploy.

### Option 2: Git + Vercel Dashboard

1. Push the project to GitHub
2. Go to [vercel.com/new](https://vercel.com/new)
3. Import your GitHub repository
4. Set **Root Directory** to `landing-page`
5. Click Deploy

---

## Post-Deployment Checklist

### 1. Update URLs in `index.html`

Once you have your Vercel URL or custom domain, update:

```html
<!-- Canonical URL -->
<link rel="canonical" href="https://njaiautomation.com/">

<!-- Open Graph URL -->
<meta property="og:url" content="https://njaiautomation.com/">
<meta property="og:image" content="https://njaiautomation.com/og-image.png">

<!-- Twitter URL -->
<meta name="twitter:url" content="https://njaiautomation.com/">
<meta name="twitter:image" content="https://njaiautomation.com/og-image.png">

<!-- Structured Data -->
"url": "https://njaiautomation.com"
```

### 2. Update Calendly Link

Replace the placeholder in the CTA section (set up "Book AI Audit" as the booking type):

```html
<a href="https://calendly.com/YOUR_CALENDLY_LINK" ...>
```

### 3. Update Email Address

If using a different email, update:

```html
<a href="mailto:john@njaiautomation.com">john@njaiautomation.com</a>
```

### 4. Add Favicon Files

Generate favicons from `logo.png` using [realfavicongenerator.net](https://realfavicongenerator.net) and add:

- `favicon-32x32.png`
- `favicon-16x16.png`
- `apple-touch-icon.png`
- `favicon.ico` (optional)

### 5. Custom Domain (Optional)

In Vercel Dashboard:
1. Go to Project Settings → Domains
2. Add `njaiautomation.com`
3. Update DNS records as instructed

---

## Testing After Deploy

- [ ] Page loads correctly
- [ ] Mobile navigation doesn't overlap
- [ ] All CTAs say "Book Your AI Audit" (not "Free Consultation")
- [ ] Audit pricing section displays correctly above implementation tiers
- [ ] All links work (especially CTA buttons)
- [ ] Test social sharing preview: [opengraph.xyz](https://www.opengraph.xyz/)
- [ ] Check structured data: [Google Rich Results Test](https://search.google.com/test/rich-results)
- [ ] Verify meta title/description reference AI Automation Audit
- [ ] Verify favicon appears in browser tab

---

## Local Development

To preview locally:

```bash
cd landing-page
npx serve .
```

Then open [http://localhost:3000](http://localhost:3000)

---

*Last updated: February 2026*
