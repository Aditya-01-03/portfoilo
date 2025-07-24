# Deployment Guide

This guide will help you deploy your portfolio website to various hosting platforms.

## 🚀 Quick Deploy Options

### 1. GitHub Pages (Free)

**Step 1: Create GitHub Repository**
```bash
# Initialize git repository
git init
git add .
git commit -m "Initial commit"

# Create new repository on GitHub.com
# Then push your code
git remote add origin https://github.com/yourusername/portfolio-website.git
git branch -M main
git push -u origin main
```

**Step 2: Enable GitHub Pages**
1. Go to your repository on GitHub
2. Click "Settings" tab
3. Scroll down to "Pages" section
4. Select "Deploy from a branch"
5. Choose "main" branch and "/ (root)" folder
6. Click "Save"

Your site will be available at: `https://yourusername.github.io/portfolio-website`

### 2. Netlify (Free)

**Option A: Drag & Drop**
1. Go to [netlify.com](https://netlify.com)
2. Sign up/Login
3. Drag your entire project folder to the deploy area
4. Your site is live instantly!

**Option B: Connect GitHub**
1. Go to [netlify.com](https://netlify.com)
2. Click "New site from Git"
3. Choose GitHub and select your repository
4. Deploy settings: Build command (leave empty), Publish directory: `/`
5. Click "Deploy site"

### 3. Vercel (Free)

**Option A: Vercel CLI**
```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel

# Follow the prompts
# - Set up and deploy? Y
# - Which scope? Select your account
# - Link to existing project? N
# - What's your project's name? portfolio-website
# - In which directory is your code located? ./
```

**Option B: Vercel Dashboard**
1. Go to [vercel.com](https://vercel.com)
2. Sign up/Login with GitHub
3. Click "New Project"
4. Import your GitHub repository
5. Deploy settings: Framework Preset (Other), Root Directory: `./`
6. Click "Deploy"

### 4. Firebase Hosting (Free)

**Step 1: Install Firebase CLI**
```bash
npm install -g firebase-tools
```

**Step 2: Initialize Firebase**
```bash
firebase login
firebase init hosting

# Select your project or create new one
# Public directory: ./
# Configure as single-page app: N
# Set up automatic builds: N
```

**Step 3: Deploy**
```bash
firebase deploy
```

## 🔧 Custom Domain Setup

### GitHub Pages
1. Go to repository Settings > Pages
2. Add custom domain in "Custom domain" field
3. Create CNAME record pointing to `yourusername.github.io`
4. Enable HTTPS (automatic)

### Netlify
1. Go to Site settings > Domain management
2. Click "Add custom domain"
3. Enter your domain
4. Update DNS records as instructed
5. Enable HTTPS (automatic)

### Vercel
1. Go to Project settings > Domains
2. Add your domain
3. Update DNS records as instructed
4. HTTPS is automatic

## 📱 Performance Optimization

### Before Deployment
1. **Optimize Images**
   ```bash
   # Use tools like TinyPNG or ImageOptim
   # Convert to WebP format when possible
   # Compress all images
   ```

2. **Minify Code** (Optional)
   ```bash
   # Install minification tools
   npm install -g html-minifier cssnano uglify-js

   # Minify HTML
   html-minifier --collapse-whitespace --remove-comments --remove-optional-tags --remove-redundant-attributes --remove-script-type-attributes --remove-tag-whitespace --use-short-doctype --minify-css true --minify-js true index.html > index.min.html

   # Minify CSS
   cssnano styles.css > styles.min.css

   # Minify JS
   uglifyjs script.js -o script.min.js
   ```

3. **Enable GZIP Compression**
   - Most hosting platforms enable this automatically
   - For custom servers, configure GZIP in your web server

### Performance Checklist
- [ ] Images are optimized and compressed
- [ ] CSS and JS are minified (optional)
- [ ] GZIP compression is enabled
- [ ] Browser caching is configured
- [ ] CDN is used for external resources
- [ ] Lazy loading is implemented
- [ ] Critical CSS is inlined

## 🔍 SEO Optimization

### Meta Tags
Ensure these are properly set in both HTML files:
```html
<meta name="description" content="Your portfolio description">
<meta name="keywords" content="your, keywords, here">
<meta name="author" content="Your Name">
<meta name="robots" content="index, follow">
```

### Open Graph Tags
Add these for better social sharing:
```html
<meta property="og:title" content="Your Name - Portfolio">
<meta property="og:description" content="Your description">
<meta property="og:image" content="https://yoursite.com/assets/profile.jpg">
<meta property="og:url" content="https://yoursite.com">
<meta property="og:type" content="website">
```

### Sitemap
Create a `sitemap.xml` file:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://yoursite.com/</loc>
    <lastmod>2024-01-01</lastmod>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://yoursite.com/projects.html</loc>
    <lastmod>2024-01-01</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
</urlset>
```

## 🔒 Security Considerations

### HTTPS
- Most platforms provide free SSL certificates
- Ensure HTTPS is enabled
- Redirect HTTP to HTTPS

### Content Security Policy
Add this meta tag for additional security:
```html
<meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self' 'unsafe-inline' https://unpkg.com; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src 'self' https://fonts.gstatic.com; img-src 'self' data:;">
```

### Security Headers
For custom servers, add these headers:
```
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block
Referrer-Policy: strict-origin-when-cross-origin
```

## 📊 Analytics Setup

### Google Analytics
1. Create Google Analytics account
2. Add tracking code to both HTML files:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

### Google Search Console
1. Add your site to Google Search Console
2. Verify ownership (usually via HTML file or DNS)
3. Submit sitemap.xml
4. Monitor search performance

## 🐛 Troubleshooting

### Common Issues

**Images Not Loading**
- Check file paths are correct
- Ensure images are in the assets folder
- Verify file permissions

**CSS/JS Not Loading**
- Check file paths
- Clear browser cache
- Verify file names match exactly

**Contact Form Not Working**
- Check browser console for errors
- Verify form integration is set up correctly
- Test with different email services

**Mobile Responsiveness Issues**
- Test on different devices
- Check viewport meta tag
- Verify CSS media queries

### Performance Issues
- Use browser dev tools to identify bottlenecks
- Check network tab for slow resources
- Optimize images and code
- Enable caching

## 📈 Monitoring

### Uptime Monitoring
- Set up uptime monitoring (UptimeRobot, Pingdom)
- Monitor response times
- Set up alerts for downtime

### Performance Monitoring
- Use Google PageSpeed Insights
- Monitor Core Web Vitals
- Track user experience metrics

## 🔄 Continuous Deployment

### GitHub Actions (Optional)
Create `.github/workflows/deploy.yml`:
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./
```

## 📞 Support

If you encounter issues:
1. Check the platform's documentation
2. Review error logs
3. Test locally first
4. Contact platform support if needed

---

**Happy Deploying! 🚀**

Your portfolio website is now ready to go live and showcase your work to the world! 