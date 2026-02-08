# 4Rolls.com - Deployment Guide

## Project Overview
Complete static food blog website for 4rolls.com featuring:
- Modern, responsive design with warm food-themed color palette
- SEO optimized with structured data and meta tags
- AdSense compliant with clear legal pages
- Performance optimized for 90+ Lighthouse scores
- Ready for Cloudflare Pages deployment

## Folder Structure
```
4rolls-website/
├── assets/
│   ├── css/
│   │   └── styles.css          # Main stylesheet with design system
│   ├── js/
│   │   └── main.js             # Interactive JavaScript features
│   └── images/                 # Placeholder for images
├── pages/
│   ├── recipes/
│   │   ├── cinnamon-rolls.html
│   │   ├── bread-rolls.html
│   │   ├── sushi-rolls.html
│   │   └── spring-rolls.html
│   └── guides/
│       └── baking-basics.html
├── index.html                  # Homepage
├── about.html                  # About page
├── contact.html               # Contact page
├── privacy-policy.html        # Privacy Policy
├── terms.html                 # Terms of Service
├── recipe-template.html       # Template for new recipes
├── sitemap.xml               # XML sitemap for SEO
├── robots.txt                # Robots.txt file
├── _headers                  # Cloudflare headers configuration
└── _redirects                # Cloudflare redirects configuration
```

## Local Development

### View Website Locally
```bash
# Navigate to project directory
cd /path/to/4rolls-website

# Start local server
python -m http.server 8000

# Visit http://localhost:8000
```

### Alternative Server Options
```bash
# Node.js http-server
npx http-server

# PHP built-in server
php -S localhost:8000

# Live Server (VS Code extension)
# Right-click index.html → "Open with Live Server"
```

## Cloudflare Pages Deployment

### Step-by-Step Deployment

1. **Sign Up/Login to Cloudflare**
   - Go to [dash.cloudflare.com](https://dash.cloudflare.com)
   - Create account or login

2. **Create New Pages Project**
   - Navigate to Workers & Pages → Pages
   - Click "Create a project"
   - Select "Connect to Git"

3. **Connect Git Repository**
   - Connect your GitHub/GitLab/Bitbucket account
   - Select your 4rolls.com repository
   - Configure build settings:
     ```
     Build command: (leave empty - static site)
     Build output directory: (leave empty - root directory)
     ```

4. **Configure Custom Domain**
   - Go to "Custom domains" tab
   - Add your domain: `4rolls.com`
   - Follow DNS configuration instructions
   - Enable "Auto SSL certificate" (included)

5. **Deployment Settings**
   - Branch: `main` (or your default branch)
   - Framework preset: None (Static HTML)
   - Build command: Leave empty
   - Build output directory: Leave empty

### Cloudflare Configuration Files

#### _headers
Controls caching and security headers:
```
/assets/css/styles.css
  Cache-Control: public, max-age=31536000, immutable

/assets/js/main.js
  Cache-Control: public, max-age=31536000, immutable

/assets/images/*
  Cache-Control: public, max-age=2592000
```

#### _redirects
Handles URL redirections:
```
https://www.4rolls.com/* https://4rolls.com/$1 301
/recipes /pages/recipes 301
/guides /pages/guides 301
```

### Post-Deployment Checklist

1. **Verify Deployment**
   - Check that all pages load correctly
   - Test navigation between pages
   - Verify mobile responsiveness

2. **SEO Verification**
   - Submit sitemap.xml to Google Search Console
   - Verify robots.txt is accessible
   - Test structured data with Google Rich Results Test

3. **Performance Testing**
   - Run Lighthouse audit (aim for 90+ scores)
   - Test Core Web Vitals
   - Verify image optimization

4. **Security Checks**
   - Ensure HTTPS is enforced
   - Verify security headers are applied
   - Test contact forms (if backend implemented)

## Performance Optimization

### Current Optimizations Implemented
- ✅ Critical CSS in external file
- ✅ Lazy loading for images
- ✅ Minified and efficient CSS/JS
- ✅ Proper caching headers
- ✅ Semantic HTML5 structure
- ✅ Mobile-first responsive design

### Additional Performance Tips
1. **Image Optimization**
   ```html
   <!-- Add to images -->
   <img src="image.jpg" alt="Description" loading="lazy" width="800" height="600">
   ```

2. **Font Loading**
   - Current implementation uses Google Fonts with preconnect
   - Consider self-hosting fonts for better performance

3. **Asset Compression**
   - Cloudflare automatically compresses assets
   - Enable Brotli compression in Cloudflare settings

## AdSense Compliance

### Implemented Requirements
- ✅ Clear About page with business information
- ✅ Clear Contact page with email address
- ✅ Comprehensive Privacy Policy
- ✅ Detailed Terms of Service
- ✅ No popups or intrusive elements
- ✅ No auto-playing videos or audio
- ✅ Professional, clean design

### Additional AdSense Tips
1. **Content Quality**
   - Maintain regular publishing schedule
   - Focus on original, high-quality content
   - Ensure proper recipe testing and documentation

2. **Site Structure**
   - Keep clear navigation hierarchy
   - Maintain consistent URL structure
   - Ensure fast loading times

3. **Policy Compliance**
   - Regularly review AdSense policies
   - Monitor for policy violations
   - Maintain transparent disclosure practices

## Maintenance

### Adding New Recipes
1. Copy `recipe-template.html`
2. Update metadata and content
3. Add to navigation and sitemap
4. Test on all devices

### Updating Content
1. Edit HTML files directly
2. Push changes to Git repository
3. Cloudflare Pages auto-deploys on push

### Monitoring
- Set up Cloudflare Analytics
- Monitor uptime and performance
- Track visitor statistics
- Regular security audits

## Troubleshooting

### Common Issues

1. **CSS Not Loading**
   - Check file paths in HTML
   - Verify _headers configuration
   - Clear browser cache

2. **JavaScript Errors**
   - Check browser console for errors
   - Verify file paths are correct
   - Test in multiple browsers

3. **Mobile Responsiveness**
   - Test with Chrome DevTools mobile emulator
   - Check viewport meta tag
   - Verify CSS media queries

4. **SEO Issues**
   - Validate with Google Search Console
   - Test structured data
   - Check robots.txt accessibility

## Support
For questions or issues:
- Email: hello@4rolls.com
- GitHub Issues (if using version control)

---
Built with ❤️ for food lovers everywhere