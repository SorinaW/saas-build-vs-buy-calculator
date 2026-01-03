# Deploy to GitHub Pages - Step by Step

## Method 1: GitHub Web Interface (Easiest)

### Step 1: Create Repository
1. Go to https://github.com/new
2. Repository name: `build-vs-buy-calculator`
3. Description: "Interactive calculator for build vs buy decisions"
4. Public ✅
5. Click **Create repository**

### Step 2: Upload File
1. Click **uploading an existing file**
2. Navigate to: `E:\ClaudeProjects\build-vs-buy-calculator\`
3. Drag and drop `index.html` and `README.md`
4. Commit message: "Initial commit"
5. Click **Commit changes**

### Step 3: Enable GitHub Pages
1. Go to **Settings** tab
2. Click **Pages** in left sidebar
3. Under "Source":
   - Branch: `main`
   - Folder: `/ (root)`
4. Click **Save**

### Step 4: Get Your Link
- GitHub will show: "Your site is live at https://username.github.io/build-vs-buy-calculator"
- Takes 2-3 minutes to deploy
- Refresh the Settings → Pages to see the link

### Step 5: Test
- Open your link in browser
- Calculator should work immediately
- Share the link!

---

## Method 2: Git Command Line

```bash
# Navigate to project folder
cd E:\ClaudeProjects\build-vs-buy-calculator

# Initialize git
git init

# Add files
git add index.html README.md DEPLOY.md

# Commit
git commit -m "Initial commit: Build vs Buy Calculator"

# Rename branch to main
git branch -M main

# Add remote (replace 'yourusername' with your GitHub username)
git remote add origin https://github.com/yourusername/build-vs-buy-calculator.git

# Push to GitHub
git push -u origin main
```

Then follow **Step 3** above to enable GitHub Pages.

---

## Method 3: Deploy to Netlify (Alternative)

1. Go to https://app.netlify.com/drop
2. Drag the `build-vs-buy-calculator` folder
3. Done! Instant link like: `yoursite.netlify.app`

**Pros:**
- Instant deployment (no waiting)
- Custom domain easier
- Better performance (CDN)

**Cons:**
- Not on your GitHub profile
- One more account to manage

---

## Customize Before Deploying

### 1. Change Footer Link
Edit `index.html`, line ~450:

```html
<p>Created by <a href="https://yoursubstack.com" target="_blank">Your Name</a> | 2026</p>
```

### 2. Update Share Link
Edit `index.html`, line ~452:

```html
<span id="shareLink">https://yourusername.github.io/build-vs-buy-calculator</span>
```

### 3. Add Your Branding Colors
Edit `index.html`, find the `<style>` section and change:

```css
/* Header gradient */
background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%);

/* Button gradient */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

---

## Test Locally First

Open `index.html` directly in your browser:
- Right-click → Open with → Chrome/Edge
- Make sure calculator works
- Try printing to PDF
- Test on mobile (Chrome DevTools → Toggle device toolbar)

---

## After Deployment

### Share Your Calculator

**On LinkedIn:**
```
I built an interactive Build vs Buy calculator for engineering leaders.

Calculate the TRUE cost of building vs buying tools - includes opportunity cost, maintenance burden, and 3-year TCO.

Try it: https://yourusername.github.io/build-vs-buy-calculator

Thoughts? What features should I add?
```

**On Twitter/X:**
```
New tool: Build vs Buy Calculator 🧮

CTOs: Stop guessing. Calculate the real cost of building vs buying tools.

Includes maintenance burden, opportunity cost, and smart recommendations.

Free: https://yourusername.github.io/build-vs-buy-calculator
```

**In Your Substack:**
```html
<iframe src="https://yourusername.github.io/build-vs-buy-calculator"
        width="100%"
        height="1200px"
        frameborder="0">
</iframe>
```

### Analytics (Optional)

Add Google Analytics to track usage:

1. Get GA4 tracking ID from https://analytics.google.com
2. Add before `</head>` in `index.html`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Custom Domain (Optional)

Want `buildorbuy.com` instead of `.github.io`?

1. Buy domain on Namecheap/GoDaddy ($10-15/year)
2. GitHub Settings → Pages → Custom domain
3. Enter your domain
4. Add DNS records (GitHub provides instructions)

---

## Troubleshooting

**Calculator not showing:**
- Wait 2-3 minutes after enabling Pages
- Check Settings → Pages for deployment status
- Make sure `index.html` is in root, not a folder

**Charts not working:**
- Check browser console (F12) for errors
- Make sure JavaScript is enabled
- Try different browser

**Print doesn't work:**
- Use Chrome or Edge
- Firefox has print-to-PDF built in
- Safari: File → Export as PDF

---

## Update After Deployment

Made changes to `index.html`?

**Via GitHub Web:**
1. Go to your repo
2. Click `index.html`
3. Click pencil icon (Edit)
4. Make changes
5. Commit

**Via Git:**
```bash
git add index.html
git commit -m "Update: [what you changed]"
git push
```

Changes appear in 1-2 minutes.

---

## Need Help?

**Common issues:**
- "404 Page Not Found" → Check Pages is enabled, wait 3 minutes
- "File not found" → Make sure `index.html` is in root
- "Calculations wrong" → Open browser console (F12) for errors

**Resources:**
- GitHub Pages docs: https://pages.github.com
- This repo: https://github.com/yourusername/build-vs-buy-calculator

---

**You're ready to deploy!** Follow Method 1 above for the easiest path.
