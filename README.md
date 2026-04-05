<div align="center">

<img src="https://img.shields.io/badge/InvestIQ-v2.0-1a6ef0?style=for-the-badge&logoColor=white" alt="InvestIQ v2.0"/>

# InvestIQ

### A self-contained investment toolkit for the modern web

[![Live Demo](https://img.shields.io/badge/Live_Demo-GitHub_Pages-16c784?style=flat-square&logo=github)](https://yourusername.github.io/investiq)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)
[![No Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen?style=flat-square)](index.html)
[![Zero Build Step](https://img.shields.io/badge/build_step-none-blue?style=flat-square)](index.html)
[![Single File](https://img.shields.io/badge/app_size-1_file-orange?style=flat-square)](index.html)

<br/>

> Five interactive financial tools, a full investing education hub, and a chaos mode —
> all in a single `index.html`. No install. No config. Deploy in 60 seconds.

<br/>

![Dark mode screenshot placeholder](https://placehold.co/900x480/0e1219/1a6ef0?text=InvestIQ+Dark+Mode)

</div>

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Quick Start](#quick-start)
- [Tools Reference](#tools-reference)
- [Education Hub](#education-hub)
- [Architecture](#architecture)
- [Customisation](#customisation)
- [Limitations and Disclaimer](#limitations-and-disclaimer)
- [Contributing](#contributing)
- [Licence](#licence)

---

## Overview

InvestIQ is a zero-dependency, single-file web application that puts five professional-grade investment tools in the browser with no backend, no build pipeline, and no accounts to create. It is designed to be forked, deployed to GitHub Pages in under two minutes, and customised without touching a terminal.

The design language is inspired by Trading212 and Interactive Brokers — dark navy surfaces, gain green, institutional data density — with an optional **Fun Mode** that transforms the entire UI into a neon terminal aesthetic complete with animated headings, a live ticker tape, and floating decorators.

```
No npm install.   No webpack.   No Docker.   No API keys.   Just open index.html.
```

---

## Features

| Tool | Description |
|---|---|
| Investment Calculator | Compound growth modeller with live chart and year-by-year breakdown table |
| Portfolio Analyzer | Holdings tracker with allocation donut chart, sector bar chart, and concentration warnings |
| Monte Carlo Simulator | 500-path probabilistic retirement simulator with percentile fan chart |
| Fee and Tax Optimizer | Fee tier comparison plus ISA vs taxable account tax drag calculator |
| Education Hub | 16 topics from L100 foundations to L400 expert, each with a full modal deep-dive |
| Dark / Light Mode | Full theme toggle, persisted within the session |
| Fun Mode | Neon grid, CRT scanlines, Orbitron headings, animated ticker tape |
| Responsive | Usable on mobile, tablet, and desktop |

---

## Quick Start

### Deploy to GitHub Pages

```bash
# 1. Fork or clone
git clone https://github.com/yourusername/investiq.git
cd investiq

# 2. Push to your GitHub account
git remote set-url origin https://github.com/YOURNAME/investiq.git
git push -u origin main

# 3. Enable GitHub Pages
#    Repository -> Settings -> Pages
#    Source: Deploy from branch
#    Branch: main   /   Folder: / (root)
#    -> Save

# Live at https://YOURNAME.github.io/investiq in ~60 seconds
```

### Run locally

No server required — just open the file directly:

```bash
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

Or use any static file server:

```bash
npx serve .
# -> http://localhost:3000
```

### Required files

```
investiq/
├── index.html    <- entire application (~130 KB, self-contained)
├── .nojekyll     <- prevents GitHub Pages from running Jekyll (must exist, can be empty)
└── README.md
```

> **Why `.nojekyll`?**
> Without it, GitHub Pages processes your repo with Jekyll and may mangle script tags or files with underscored names. An empty file with this exact name disables that behaviour entirely.

---

## Tools Reference

### Investment Calculator

Model the long-run growth of any investment using the compound interest formula `A = P(1 + r/n)^(nt)`.

**Inputs**

| Parameter | Range | Default |
|---|---|---|
| Initial investment | 100 – 200,000 | 5,000 |
| Annual return rate | 0.5% – 30% | 7% |
| Time horizon | 1 – 50 years | 20 years |
| Monthly contribution | 0 – 10,000 | 0 |
| Compounding frequency | Annual / Quarterly / Monthly / Daily | Annual |
| Currency | GBP / USD / EUR | GBP |

**Outputs:** final balance, total invested, total interest earned, return multiple, CAGR, year-by-year breakdown table.

---

### Portfolio Analyzer

Enter holdings manually and get an instant visual breakdown of your allocation.

- **Donut chart** — allocation by asset class (ETF, Stocks, Bonds, Cash, Property, Commodities, Crypto, Other)
- **Horizontal bar chart** — sector exposure ranked by weight
- **Concentration warnings** — triggered if any single sector exceeds 50%, or if cash exceeds 30% of the portfolio

The tool ships pre-populated with a sample diversified portfolio (VWRP, CSPX, AAPL, VGOV, Cash ISA) so the charts render immediately on load.

---

### Monte Carlo Simulator

Runs 500 independent simulations of a portfolio using log-normally distributed annual returns generated with the Box-Muller transform.

**Inputs:** starting portfolio value, monthly contribution, time horizon, expected annual return, annual volatility (standard deviation).

**Outputs**

| Output | Description |
|---|---|
| Fan chart | 5th, 25th, 50th, 75th, and 95th percentile paths over time |
| Median outcome | 50th percentile final balance |
| 95th / 5th percentile | Best and worst 5% of simulated outcomes |
| Success probability | Percentage of simulations that exceed total contributions |
| Percentile table | P5 through P95 final balances |

---

### Fee and Tax Optimizer

**Tab 1 — Fee Impact**

Compares four expense ratio tiers against the same gross return assumption.

| Tier | Typical example | Annual fee |
|---|---|---|
| Passive ETF | VWRP, CSPX | 0.07% |
| Active ETF | Thematic or factor | 0.50% |
| Managed fund | Typical active | 1.00% |
| High-cost fund | Worst case | 1.75% |

Outputs the final portfolio value per tier and total money lost versus the cheapest option.

**Tab 2 — ISA vs Taxable Account**

Models the same investment inside a UK Stocks and Shares ISA (0% tax on gains and dividends) against a General Investment Account with approximately 20% effective tax drag on returns. Outputs the lifetime tax shelter benefit in pounds.

---

## Education Hub

Sixteen topics with card summaries and full modal deep-dives. Each modal includes: what it is, how it works, a real-world worked example, key risks, and actionable tips.

| Level | Topic | Core concept |
|---|---|---|
| L100 | Stocks (Equities) | Fractional ownership, dividends, price discovery |
| L100 | ETFs | Instant diversification, TER, accumulating vs distributing |
| L100 | Bonds | Coupons, duration, inverse relationship with interest rates |
| L100 | ISAs | 20,000 GBP annual allowance, tax-free growth, wrapper hierarchy |
| L100 | Compound Interest | A = P(1+r)^n, Rule of 72, time as the dominant variable |
| L100 | Inflation and Real Returns | CPI, real vs nominal return, cash erosion |
| L200 | Dollar Cost Averaging | Automating regular purchases, removing timing emotion |
| L200 | Averaging Down | When it helps vs when it destroys — the key distinction |
| L200 | Diversification | Uncorrelated assets, Modern Portfolio Theory, unsystematic risk |
| L200 | Asset Allocation | 60/40, age-based rules, Brinson et al return attribution |
| L200 | Rebalancing | Calendar vs threshold, selling high and buying low automatically |
| L300 | CFDs — Why to Avoid | Leverage mechanics, FCA loss warnings, 74–89% retail loss rate |
| L300 | Index Investing | SPIVA data, 90%+ active fund underperformance over 15 years |
| L300 | SIPPs and Pensions | 20–45% tax relief, salary sacrifice |
| L300 | Tax-Efficient Investing | Wrapper hierarchy, bed-and-ISA, CGT and dividend allowances |
| L400 | Factor Investing | Fama-French five-factor model, value / size / momentum premiums |
| L400 | Sequence-of-Returns Risk | Path dependency in drawdown, 4% rule, bucket strategy |
| L400 | Valuation Fundamentals | P/E, CAPE, PEG ratio, free cash flow yield |
| L400 | Advanced Risk Management | Kelly Criterion, Sharpe Ratio, max drawdown, correlation matrix |

---

## Architecture

All logic, styles, and markup live in a single HTML file. There is no bundler, no module system, and no separate asset files.

```
index.html
├── <style>
│   ├── CSS custom properties  (light / dark / fun mode design tokens)
│   ├── Keyframe animations    (glitch, neon-pulse, rainbow-border, shimmer, float...)
│   └── Component styles
│
└── <script type="text/babel">
    ├── Constants
    │   ├── FUN          (fun mode text translation map)
    │   ├── TOPICS       (all 16 education topics with full detail objects)
    │   ├── CURRENCIES   (GBP, USD, EUR locale config)
    │   └── FREQS        (compounding frequency definitions)
    │
    ├── Helpers
    │   ├── buildSchedule        (compound interest year-by-year)
    │   ├── runMC                (Monte Carlo 500-path simulation)
    │   ├── computeFeeSchedule   (after-fee growth projection)
    │   └── fmtN / fmtK          (number formatting)
    │
    ├── Components
    │   ├── Slider
    │   ├── FunFloaters
    │   ├── FunTape
    │   ├── CalculatorPage
    │   ├── PortfolioPage
    │   ├── MonteCarloPage
    │   ├── FeeTaxPage
    │   ├── TopicModal
    │   ├── EducationPage
    │   └── App             (nav, routing, theme and fun mode state)
    │
    └── ReactDOM.createRoot(document.getElementById('root')).render(<App/>)
```

**Runtime dependencies (all loaded from CDN, nothing installed)**

| Library | Version | Source |
|---|---|---|
| React + ReactDOM | 18.2.0 | cdnjs.cloudflare.com |
| Babel Standalone | 7.23.2 | cdnjs.cloudflare.com |
| Chart.js | 4.4.1 | cdnjs.cloudflare.com |
| Google Fonts | — | fonts.googleapis.com |

**Routing** is a single `page` state string — no React Router, no hash routing. The browser back button does not navigate between tools by design.

**Chart lifecycle** is managed via module-level singleton references (`chartInst`, `mcChart`, `feeChart`, `taxChart`, `portCharts`) that are destroyed and recreated on page transitions and theme changes to prevent Canvas reuse errors.

> **Performance note:** Babel Standalone compiles JSX in the browser on first load, adding approximately 200 ms cold-start overhead. This is acceptable for a personal finance tool. To remove it, pre-compile the JSX using `@babel/cli` and change `type="text/babel"` to `type="text/javascript"` on the script tag.

---

## Customisation

### Add a new education topic

Append an object to the `TOPICS` array in the script block:

```js
{
  id:      'my-topic',       // unique string, no spaces
  level:   'l200',           // l100 | l200 | l300 | l400
  icon:    '[icon]',
  title:   'My Topic',
  sub:     'One-line card subtitle',
  summary: 'Summary shown on the card grid (2–3 sentences).',
  points: [
    'Key point one',
    'Key point two',
    'Key point three',
  ],
  detail: {
    what:    'Full explanation of the concept.',
    how:     'How it works in practice.',
    example: 'A concrete real-world worked example.',
    risks:   ['Risk one', 'Risk two'],
    tips:    ['Actionable tip one', 'Actionable tip two'],
  }
}
```

### Add a new tool page

**Step 1** — Write a React component:

```jsx
function MyToolPage({ fun }) {
  return (
    <div className="page">
      <div className="tool-hero">
        <div className="tool-hero-left">
          <div className="tool-hero-tag">My Tool</div>
          <h2>My Tool Name</h2>
          <p>What this tool does.</p>
        </div>
      </div>
      {/* tool content */}
    </div>
  );
}
```

**Step 2** — Add an entry to the `PAGES` array:

```js
const PAGES = [
  {
    key: 'tools',
    label: 'Tools',
    funLabel: 'Tools',
    items: [
      // existing items...
      {
        key: 'mytool',
        icon: '[icon]',
        label: 'My Tool',
        sub:   'Short description',
        bg:    'var(--purple-dim)',
      },
    ],
  },
  // ...
];
```

**Step 3** — Add a render line in the `App` return:

```jsx
{page === 'mytool' && <MyToolPage fun={fun} />}
```

### Change colour tokens

All colours are CSS custom properties. Edit the relevant block at the top of `<style>`:

```css
[data-theme="dark"] {
  --blue:   #1a6ef0;   /* primary interactive colour  */
  --green:  #16c784;   /* gains and positive values   */
  --red:    #e5392b;   /* losses and warnings         */
  --amber:  #f59e0b;   /* secondary warnings          */
  --purple: #8b5cf6;   /* accent                      */
}
```

Fun mode overrides these in the `[data-fun="true"]` block immediately below.

### Add Fun Mode copy

Add a key–value pair to the `FUN` object near the top of the script:

```js
const FUN = {
  'My label': 'chaotic version of my label',
  // ...
};
```

Use it anywhere in a component with the `T()` helper:

```jsx
<span>{T('My label', fun)}</span>
// renders 'My label' normally, 'chaotic version of my label' in fun mode
```

---

## Limitations and Disclaimer

### Known limitations

- **No data persistence.** All entered data resets on page refresh. There is no localStorage, database, or authentication layer.
- **Manual data entry only.** The Portfolio Analyzer does not connect to any brokerage, bank, or open finance API.
- **UK-focused tax logic.** ISA allowances, SIPP tax relief rates, CGT and dividend allowances reflect 2024/25 UK rules. The currency selector changes the symbol only; tax calculations are not jurisdiction-aware.
- **Simplified Monte Carlo model.** Annual returns are drawn from a normal distribution. Real markets exhibit fat tails, volatility clustering, autocorrelation, and regime changes that this model does not capture. Results are illustrative, not predictive.
- **In-browser JSX compilation.** Babel Standalone is not suitable for high-traffic production deployments.
- **Requires an internet connection.** All CDN assets load at runtime. There is no offline mode.

### Disclaimer

> InvestIQ is an educational and illustrative tool only. Nothing in this application constitutes financial advice, investment advice, or a recommendation to buy or sell any security. All projections assume constant rates of return and simplified tax models. Actual results will differ. Past performance does not guarantee future results. Always conduct your own research and consult a regulated financial adviser before making any investment decisions.

---

## Contributing

Contributions, issues, and feature requests are welcome.

1. Fork the repository
2. Make your changes to `index.html`
3. Test by opening the file directly in a browser — no build step needed
4. Open a pull request with a clear description of what changed and why

There is intentionally no test suite, linter, or CI pipeline. The project philosophy is zero tooling overhead. If you add tooling, please keep it entirely opt-in and out of the basic open-and-run workflow.

For bug reports, please include your browser, operating system, and the exact steps to reproduce the issue.

---

## Licence

```
MIT License

Copyright (c) 2026 InvestIQ Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

<div align="center">

Built with React 18 · Chart.js 4 · zero build tools

**Star this repo if you find it useful**

</div>
