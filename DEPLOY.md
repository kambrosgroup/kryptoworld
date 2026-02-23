# KryptoWorld Site Deployment Guide

## Site Structure

```
site/
├── hugo.toml              # Site configuration
├── content/
│   ├── posts/
│   │   ├── best-crypto-exchanges-beginners.md
│   │   ├── how-to-buy-bitcoin-safely.md
│   │   └── crypto-wallet-types-explained.md
│   └── disclosure.md
├── layouts/               # HTML templates
├── static/                # Static assets
│   ├── _redirects         # Affiliate link cloaking
│   └── robots.txt
└── public/                # Generated site (after build)
```

## Deployment Steps

### 1. Install Hugo

**macOS:**
```bash
brew install hugo
```

**Windows:**
```bash
winget install Hugo.Hugo.Extended
```

**Linux:**
```bash
sudo apt install hugo
```

### 2. Create GitHub Repository

1. Go to https://github.com/new
2. Name it `kryptoworld` (or your preference)
3. Make it public
4. Don't initialize with README (we have our own)

### 3. Push Site to GitHub

```bash
# Navigate to site directory
cd site

# Initialize git
git init
git add .
git commit -m "Initial site setup"

# Add remote (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/kryptoworld.git
git branch -M main
git push -u origin main
```

### 4. Enable GitHub Pages

1. Go to your repo on GitHub
2. Settings → Pages
3. Source: Deploy from a branch
4. Branch: main, Folder: / (root)
5. Save

Wait 2-5 minutes. Your site will be at:
`https://YOUR_USERNAME.github.io/kryptoworld/`

### 5. Connect Custom Domain

1. In GitHub Pages settings, add custom domain: `kryptoworld.space`
2. Check "Enforce HTTPS"
3. Add these DNS records at your domain registrar:

| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | YOUR_USERNAME.github.io |

Wait for DNS propagation (up to 24 hours, usually 15 minutes).

### 6. Update Affiliate Links

Before going live, replace placeholder redirect URLs in `static/_redirects` with your actual affiliate links:

```
# Current (placeholders):
/go/coinbase https://www.coinbase.com/join 301

# Replace with your actual affiliate URL:
/go/coinbase https://www.coinbase.com/join?ref=YOUR_REF_CODE 301
```

### 7. Build Locally (Optional)

```bash
cd site
hugo server -D
```

Visit http://localhost:1313 to preview.

### 8. Deploy Updates

After making changes:

```bash
git add .
git commit -m "Description of changes"
git push
```

GitHub automatically rebuilds and deploys.

## Post-Launch Checklist

- [ ] Site loads at kryptoworld.space
- [ ] HTTPS is working
- [ ] All 3 articles display correctly
- [ ] Disclosure page is accessible
- [ ] Affiliate redirect links work
- [ ] Mobile responsive (test on phone)
- [ ] Submit sitemap to Google Search Console

## Next Steps After Deployment

1. **Apply to affiliate programs** with your live site
2. **Update affiliate links** in `_redirects` file
3. **Submit to Google Search Console**
4. **Create social media accounts** (X, LinkedIn)
5. **Publish 2 more articles** this week

## Adding New Articles

1. Create new file in `content/posts/`
2. Use this frontmatter template:

```yaml
---
title: "Article Title"
description: "SEO description (150-160 chars)"
keywords: "keyword1, keyword2, keyword3"
date: 2026-02-23
type: posts
slug: article-url-slug
categories: ["exchanges"]
tags: ["beginners", "reviews"]
---
```

3. Write content in Markdown
4. Commit and push

## Support

- Hugo docs: https://gohugo.io/documentation/
- GitHub Pages docs: https://docs.github.com/en/pages
