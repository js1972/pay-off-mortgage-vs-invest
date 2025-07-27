# Mortgage vs Invest — Break-Even Calculator

A sophisticated single-page financial calculator that helps you make informed decisions about whether to pay down your mortgage faster or invest spare money in the market. Built specifically for the Australian tax environment with comprehensive Monte Carlo analysis.

## 🎯 The Problem

One of the most common financial dilemmas: *"Should I use my extra $1000/month to pay off my mortgage faster, or invest it in shares?"*

This tool provides a data-driven answer by comparing:
- **Guaranteed savings** from paying down debt (your mortgage rate)
- **Expected returns** from investing (accounting for tax, dividends, and volatility)

## 📊 What It Shows

The interactive chart visualizes your decision across different mortgage rate scenarios:

* **🟢 Green solid line** — Expected after-tax investment return  
* **🔴 Pink dashed line** — Guaranteed mortgage "return" from extra payments  
* **⚪ White dashed marker** — Your current mortgage rate (the decision point)  
* **🟢 Green confidence bands** — Investment uncertainty from Monte Carlo simulation:
  * **Darkest band** — 50% confidence (25th–75th percentile)  
  * **Medium band** — 80% confidence (10th–90th percentile)  
  * **Lightest band** — 90% confidence (5th–95th percentile)

### 📈 Decision Logic
- **When green line is above pink** → Investing typically wins
- **When pink line is above green bands** → Pay the mortgage  
- **When lines intersect** → Consider risk tolerance and liquidity needs

<img src="screenshot.png" alt="App screenshot showing chart-first mobile layout" width="750"/>

---

## 🧮 How It Works

### Australian Tax Calculations
The calculator implements sophisticated tax modeling for accurate comparisons:

**Investment Returns:**
- **Dividend income** with franking credit benefits (30% corporate tax rate)
- **Capital gains** with 50% CGT discount for assets held >1 year
- **Marginal tax rates** applied to your income bracket

**Mortgage Savings:**
- **After-tax equivalent** of interest payments avoided
- **Guaranteed return** with no market risk

### Monte Carlo Simulation
Each calculation runs **5,000 random market scenarios** to model investment uncertainty:
- Uses Box-Muller transformation for realistic normal distribution
- Applies geometric compounding over your time horizon
- Incorporates your specified volatility (standard deviation)
- Generates confidence intervals to visualize risk ranges

### Key Formula
```
Investment Return = Dividend Yield (after franking) + Capital Growth (after CGT)
Mortgage Return = Interest Rate × (1 - Tax Rate)
```

---

## ⚙️ Input Parameters

| Parameter | Description | Typical Values |
|-----------|-------------|----------------|
| **Marginal Tax Rate** | Your highest tax bracket (inc. Medicare levy) | 47% (top), 37% (middle), 32.5% (average) |
| **Mortgage Rate** | Current home loan interest rate | 5-7% (as of 2024-25) |
| **Dividend Yield** | Expected annual dividend income | ASX 200: ~4%, REITs: ~6%, Growth: ~2% |
| **Franking %** | Portion of fully-franked dividends | Major ASX: 100%, International: 0% |
| **Capital Growth** | Expected annual price appreciation | Conservative: 4-5%, Moderate: 6-7%, Aggressive: 8-10% |
| **Volatility (σ)** | Annual price standard deviation | ASX: ~17%, International: ~15%, Bonds: ~5% |
| **Time Horizon** | Investment timeframe in years | Longer favors investing due to compounding |

---

## ✨ Features

| Feature | Details |
|---------|---------|
| **Pure front-end** | Vanilla HTML + CSS + Chart.js 4, no build step or framework bloat |
| **Monte-Carlo engine** | 5,000 paths per refresh, volatility and horizon configurable |
| **Interactive inputs** | Tax rate, dividend yield, franking %, cap-growth, σ, horizon |
| **Local-storage recall** | Your last inputs are remembered automatically |
| **Mobile-optimized** | Chart-first layout, smart tooltip positioning, touch-friendly |
| **Custom tooltip** | Dark pill shows return spread + verdict at the cursor |
| **Help system** | Interactive tooltips explain each parameter with examples |

---

## 📱 Mobile-First Design

The app prioritizes mobile usability with a **chart-first layout**:

1. **📊 Chart** — Immediate visual results on page load
2. **🎯 Verdict** — Clear decision summary  
3. **📖 Explanation** — Educational content about the analysis
4. **⚙️ Parameters** — Input controls below with gear icon

This ensures users see the most important information (the comparison visualization) immediately on small screens.

---

## 🚀 Quick Start

```bash
# Clone or download the single HTML file
wget https://github.com/you/mortgage-vs-invest/raw/main/pay-off-mortgage-vs-invest.html

# Serve locally (optional - can open directly in browser)
python -m http.server 8000
# or
npx serve .
```

Open `pay-off-mortgage-vs-invest.html` in any modern browser. No installation or build process required!

---

## 🔧 Technical Details

**Technologies:**
- Pure HTML5/CSS3/ES6+ JavaScript
- Chart.js 4.4.1 with annotation plugin
- CSS Grid for responsive layout
- Local Storage for parameter persistence

**Calculations:**
- Monte Carlo simulation with 5,000 iterations
- Box-Muller normal distribution sampling
- Australian tax system modeling (franking credits, CGT discount)
- Geometric return compounding over time horizon

**Browser Support:**
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile Safari and Chrome on iOS/Android
- Progressive enhancement for older browsers

---

## 💡 Example Scenarios

### Scenario 1: High Income, Low Rate
- Tax: 47%, Mortgage: 3.5%, Expected return: 7.2%
- **Result:** 📈 Investing wins by ~2.8% p.a.

### Scenario 2: Medium Income, High Rate  
- Tax: 37%, Mortgage: 6.5%, Expected return: 6.8%
- **Result:** 🏠 Pay mortgage - saves ~0.6% p.a.

### Scenario 3: Break-Even Territory
- Tax: 32.5%, Mortgage: 5.2%, Expected return: 5.8%
- **Result:** ⚖️ Very close - consider risk tolerance

---

## ⚖️ Disclaimers

- **Educational tool only** - not personal financial advice
- **Past performance** doesn't guarantee future returns
- **Consider liquidity** - mortgage payments reduce flexibility
- **Risk tolerance** matters beyond pure mathematics
- **Consult professionals** for personalized advice

This calculator provides mathematical analysis to inform your decision-making process, but your personal circumstances, risk tolerance, and goals should ultimately guide your choice.