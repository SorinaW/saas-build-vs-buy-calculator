# Build vs Buy Calculator - Complete Feature List

## Basic Metrics (Required)

### Build Costs
- **Engineer-Months Required** - How long to build
- **Monthly Engineer Cost** - Fully loaded cost (salary + benefits + overhead)
- **Annual SaaS Cost** - Yearly subscription
- **Time to Value** - Months to production (Build) vs Weeks to deployment (Buy)

### Optional Basic Metrics
- **Maintenance Hours/Month** - Ongoing support, updates, bug fixes
- **Hourly Rate** - For calculating maintenance costs
- **Opportunity Cost** - Lost revenue from delayed features
- **Hidden Costs** - Infrastructure, security, etc.
- **Implementation Cost** - One-time SaaS setup

---

## Advanced "Reality Check" Metrics

Click **"⚠️ Reality Check: Advanced Factors"** to reveal these fields.

### Build Reality Check

**1. Probability Build Runs Over Budget (%)**
- Default: 30%
- Industry reality: 70% of projects run over budget
- Used to calculate expected overrun costs
- Formula: `(Probability / 100) × Overrun Cost = Expected Cost`

**2. Cost Overrun if Delayed**
- Default: $50,000
- Extra engineering cost when build takes longer than planned
- Includes: Extended engineer time, delayed launch costs

**3. Bus Factor Cost (Engineer Quits)**
- Default: $30,000
- What happens when the builder leaves?
- Includes: Recruiter fees, training replacement, documenting undocumented code
- Calculator assumes 33% chance this happens

**4. Support Hours/Month**
- Default: 10 hours
- Separate from maintenance
- User questions, Slack pings, bug reports, onboarding
- Cost = `Support Hours × 12 × Hourly Rate`

**5. Annual Compliance Tax**
- Default: $15,000/year
- SOC 2 audits, GDPR compliance, security patches, pen testing
- SaaS vendors eat this cost; you don't
- Recurring yearly cost

**6. Cost to Scale at 10x Users**
- Default: $40,000
- Infrastructure upgrades when usage explodes
- Performance optimization
- Database scaling

**7. Team Velocity Loss (%)**
- Default: 15%
- How much slower is the REST of the team while 1 person builds this?
- Blockers, waiting for the tool, using janky workarounds
- Applied to opportunity cost: `(Velocity % / 100) × Opportunity Cost`

### Additional Costs

**8. Need to Hire Someone?**
- Default: $0 (assuming you have capacity)
- If you need to hire: $20K recruiter fee + 3-5 months delay
- One-time cost added to build initial

**9. Competitive Disadvantage (months)**
- Default: 5 months
- How long are you behind competitors who bought SaaS and shipped faster?
- Used in recommendation logic (high risk if >3 months)

**10. Exit Cost: Build (Switch Later)**
- Default: $60,000
- Cost to migrate away if your homegrown tool sucks
- Migration engineering, data cleanup, downtime

**11. Exit Cost: Buy (Vendor Lock-in)**
- Default: $20,000
- Cost to export data and switch vendors
- Usually lower than build exit cost

**12. Feature Completeness: Build (%)**
- Default: 60%
- What % of needed features will v1 actually have?
- Used in recommendation: <70% = warning flag

**13. Worst-Case Maintenance Hours/Month**
- Default: 40 hours
- When things break, feature requests pile up, someone quits
- Used to calculate worst-case scenario costs

**14. Worst-Case Build Time (months)**
- Default: 12 months
- Scope creep, bugs, delays, rewrites
- "Everything goes wrong" scenario

---

## How Advanced Metrics Affect Calculations

### Base Case (Realistic)
```
Build Year 1 =
  Initial Build Cost +
  Maintenance (12 months) +
  Support (12 months) +
  Opportunity Cost +
  Hidden Costs +
  Compliance Cost +
  Expected Overrun (Risk-Adjusted) +
  Bus Factor (33% probability) +
  Velocity Impact Cost +
  Hiring Cost (if needed)
```

### Worst Case
```
Build Year 1 Worst =
  Initial Build Cost +
  Worst-Case Maintenance (12 months) +
  Support (12 months) +
  Opportunity Cost +
  Hidden Costs +
  Compliance Cost +
  FULL Overrun Cost (not risk-adjusted) +
  FULL Bus Factor Cost +
  Velocity Impact Cost +
  Scale Cost +
  Hiring Cost (if needed)
```

### 3-Year TCO
```
Build 3-Year =
  Year 1 Cost +
  (Maintenance × 2) +
  (Support × 2) +
  (Compliance × 2)

Build 3-Year Worst =
  Worst Year 1 +
  (Worst Maintenance × 2) +
  (Support × 2) +
  (Compliance × 2) +
  Exit Cost (if you give up and buy SaaS anyway)
```

---

## Recommendation Logic

The calculator now uses **intelligent decision logic** based on risk factors:

### Scenario 1: BUY is cheaper (Base + TCO)
**Result:** "BUY"
- Clear winner on costs
- Additional reasons if:
  - Faster time to value
  - Eliminates maintenance
  - Feature completeness low
  - High failure risk

### Scenario 2: BUILD is cheaper BUT high risk
**Result:** "BUY (despite TCO)"

Triggered if ANY of these are true:
- Failure risk > 50%
- Worst case costs 1.5x+ base case
- Velocity impact > 20%
- Competitive delay > 3 months
- Feature completeness < 70%

**Message:** "Build is cheaper on paper (saves $X), BUT risk factors make it a bad bet. Worst-case costs $Y - way more than buying."

### Scenario 3: BUILD is cheaper AND low risk
**Result:** "BUILD (maybe)"

Shows:
- 3-year savings
- Worst-case scenario as warning
- Questions to consider:
  - Is this core IP?
  - Can you handle X months if it goes wrong?

### Scenario 4: Close call
**Result:** "BUY"
- Costs are similar
- Buying eliminates execution risk
- Factors in velocity impact, opportunity cost

---

## Visual Outputs

### Result Cards
- **Build: Year 1 Total** (Base case with risk-adjustment)
- **Buy: Year 1 Total**
- Detailed breakdown showing all cost components

### 3-Year Comparison Table
- Build (3 years) - Base case
- Buy (3 years)
- Difference (color-coded: green = savings, red = more expensive)

### Cost Visualization Chart
- Bar charts comparing Year 1 and 3-Year costs
- Scales automatically based on highest cost
- Build bars = red/pink gradient
- Buy bars = blue gradient

### Smart Recommendation Box
- Color-coded:
  - Green = BUY (clear winner)
  - Orange = BUILD (maybe) or BUY (despite TCO)
- Bullet points explaining why
- Direct language: no corporate BS

---

## Example Scenarios

### Scenario A: Typical Internal Tool
- 6 engineer-months, $15K/month
- 30% failure risk
- Result: **BUY** - Saves $190K Year 1, eliminates risk

### Scenario B: High-Risk Build
- 12 engineer-months, $20K/month
- 70% failure risk
- Feature completeness: 50%
- Result: **BUY (despite TCO)** - Worst case costs $600K vs $130K for SaaS

### Scenario C: Core IP
- 6 engineer-months
- Low failure risk (10%)
- Feature completeness: 90%
- No opportunity cost (parallel work)
- Result: **BUILD (maybe)** - Saves $150K over 3 years, low risk

---

## What Makes This Calculator Different

**Most calculators:**
- Assume everything goes perfectly
- Ignore failure risk
- Don't account for team velocity impact
- Miss compliance and support costs
- No worst-case scenarios

**This calculator:**
- Risk-adjusted costs (expected value of failures)
- Worst-case scenario calculations
- Team velocity impact
- Compliance burden
- Bus factor costs
- Intelligent recommendations based on risk profile

**Result:** You get realistic numbers, not optimistic BS.

---

## Mobile Responsive

All fields work on mobile:
- 2-column layout on desktop
- Single column on mobile
- Touch-friendly inputs
- Print-friendly output

---

## Export Options

**Print to PDF:**
- Click "Print / Export PDF"
- Save as PDF from browser print dialog
- Clean layout for sharing with stakeholders

**Calculate Button:**
- Updates in real-time as you type
- Or click Calculate to force refresh

**Reset Button:**
- Resets all fields to defaults
- Including all advanced fields

---

## Coming Soon (Potential Features)

- [ ] Save/load scenarios
- [ ] Compare multiple vendors
- [ ] Export to Excel
- [ ] Team collaboration (shareable links with pre-filled values)
- [ ] API for embedding in other tools

---

**Bottom Line:** This calculator tells you the truth about build vs buy, not what you want to hear.
