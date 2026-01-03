# Build vs Buy Calculator

Interactive web calculator to help CTOs and engineering leaders make data-driven decisions about building vs buying software tools.

**[🔗 Live Demo](https://sorinaw.github.io/saas-build-vs-buy-calculator)**

## Features

✅ **Real-time calculations** - Updates as you type
✅ **Optional fields** - Only fill in what you know
✅ **3-year TCO comparison** - See long-term costs
✅ **Smart recommendations** - Data-driven buy/build advice
✅ **Visual charts** - Compare costs at a glance
✅ **Print to PDF** - Save or share results
✅ **Mobile responsive** - Works on any device
✅ **No backend required** - Pure HTML/JS, deploy anywhere

## Deploy to GitHub Pages

### Quick Setup (5 minutes)

1. **Create a new repository:**
   - Go to https://github.com/new
   - Name: `saas-build-vs-buy-calculator`
   - Public
   - Click "Create repository"

2. **Upload the file:**
   - Click "uploading an existing file"
   - Drag `index.html` from `E:\ClaudeProjects\build-vs-buy-calculator\`
   - Commit

3. **Enable GitHub Pages:**
   - Go to Settings → Pages
   - Source: Deploy from a branch
   - Branch: `main` / `root`
   - Click Save

4. **Done!**
   - Your calculator will be live at: [https://sorinaw.github.io/saas-build-vs-buy-calculator](https://sorinaw.github.io/saas-build-vs-buy-calculator)
   - Takes 2-3 minutes to deploy

### Alternative: Deploy with Git

```bash
cd E:\ClaudeProjects\build-vs-buy-calculator
git init
git add index.html README.md
git commit -m "Initial commit: Build vs Buy Calculator"
git branch -M main
git remote add origin https://github.com/SorinaW/saas-build-vs-buy-calculator.git
git push -u origin main
```

Then enable GitHub Pages as described above.

## Usage

### Default Example (Pre-filled)

The calculator comes with a real-world example:
- **Build:** 6 engineer-months at $15K/month
- **Maintenance:** 20 hours/month at $150/hour
- **Opportunity cost:** $200K in delayed features
- **SaaS:** $120K/year
- **Implementation:** $10K one-time

**Result:** Buy saves ~$130K in Year 1, ~$210K over 3 years

### Required Fields

Only 4 fields are required:
1. Engineer-Months Required
2. Monthly Engineer Cost
3. Annual SaaS Cost
4. Time to Value (Build & Buy)

All other fields are optional and will default to 0.

### Optional Fields

- **Maintenance Hours** - Ongoing support time
- **Hourly Rate** - For calculating maintenance cost
- **Opportunity Cost** - Revenue impact of delayed features
- **Hidden Costs** - Infrastructure, security, compliance
- **Implementation Cost** - One-time setup for SaaS

## Customization

### Change Default Values

Edit `index.html`, find the input elements, and change `value="..."`:

```html
<input type="number" id="engineerMonths" value="6">
<!-- Change 6 to your default -->
```

### Change Colors

Modify the CSS gradients in the `<style>` section:

```css
/* Purple gradient (current) */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

/* Alternative: Blue */
background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);

/* Alternative: Green */
background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);
```

### Add Your Branding

Edit the footer:

```html
<p>Created by <a href="https://yoursubstack.com">Your Name</a> | 2026</p>
```

### Add Google Analytics

Add before `</head>`:

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

## Share Your Calculator

Once deployed, share the link:

**[https://sorinaw.github.io/saas-build-vs-buy-calculator](https://sorinaw.github.io/saas-build-vs-buy-calculator)**

**Pro tip:** Create a short link with bit.ly or your own domain!

Example:
- `buildorbuy.co` → redirect to GitHub Pages
- Post on LinkedIn, Twitter, Substack

## Technical Details

- **Size:** ~25KB (single HTML file)
- **Dependencies:** None (pure HTML/CSS/JS)
- **Browser support:** All modern browsers
- **Mobile:** Fully responsive
- **Loading time:** <1 second
- **Offline:** Works offline after first load

## Use Cases

- **Blog posts** - Embed as interactive content
- **Sales enablement** - Help prospects calculate ROI
- **Internal tool** - Share with engineering leadership
- **Consulting** - Use during discovery calls
- **Education** - Teach cost analysis frameworks

## Example Scenarios

### Scenario 1: Customer Data Platform
- 6 engineer-months to build
- $30K/year maintenance
- $200K opportunity cost
- vs $120K/year SaaS
- **Result:** Buy saves $130K Year 1

### Scenario 2: Internal CRM
- 12 engineer-months to build
- $60K/year maintenance
- $500K opportunity cost
- vs $40K/year SaaS
- **Result:** Buy saves $580K Year 1

### Scenario 3: Custom Algorithm (Core IP)
- 18 engineer-months to build
- $20K/year maintenance
- $0 opportunity cost (parallel work)
- vs $300K/year SaaS
- **Result:** Build saves $420K over 3 years

## FAQ

**Q: Can I use this commercially?**
A: Yes! It's free to use and modify.

**Q: Does it collect data?**
A: No. All calculations happen in your browser.

**Q: Can I white-label it?**
A: Yes, just change the footer branding.

**Q: Can I add more fields?**
A: Yes! Edit the HTML to add more inputs and update the `calculate()` function.

**Q: How do I add my logo?**
A: Add an `<img>` tag in the header section.

## Roadmap

Potential enhancements:
- [ ] Save/load scenarios
- [ ] Compare multiple vendors
- [ ] Export to CSV/Excel
- [ ] Team collaboration features
- [ ] API for embedding

## Contributing

Want to improve the calculator?
- Fork the repo
- Make your changes
- Submit a pull request

## License

MIT License - Free to use, modify, and distribute.

## Support

Questions? Issues?
- Open an issue on GitHub
- Email: your@email.com
- Twitter: @yourusername

## Credits

Created by Sorina Weber | 2026

Based on the "Build vs Buy" framework for engineering decision-making.

---

**Deploy yours in 5 minutes:** [https://github.com/SorinaW/saas-build-vs-buy-calculator](https://github.com/SorinaW/saas-build-vs-buy-calculator)
