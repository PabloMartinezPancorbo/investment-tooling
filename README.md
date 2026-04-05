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

> Five interactive financial tools, a full investing education hub, and a chaos mode \u2014  
> all in a single `index.html`. No install. No config. Deploy in 60 seconds.

<br/>

![Dark mode screenshot placeholder](https://placehold.co/900x480/0e1219/1a6ef0?text=InvestIQ+%E2%80%94+Dark+Mode)

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
- [Limitations & Disclaimer](#limitations--disclaimer)
- [Contributing](#contributing)
- [Licence](#licence)

---

## Overview

InvestIQ is a zero-dependency, single-file web application that puts five professional-grade investment tools in the browser with no backend, no build pipeline, and no accounts to create. It is designed to be forked, deployed to GitHub Pages in under two minutes, and customised without touching a terminal.

The design language is inspired by Trading212 and Interactive Brokers \u2014 dark navy surfaces, gain green, institutional data density \u2014 with an optional **Fun Mode** that transforms the entire UI into a neon terminal aesthetic.

```
No npm install.   No webpack.   No Docker.   No API keys.   Just open index.html.
```

---

## Features

| Feature | Description |
|---|---|
| \ud83d\udcca **Investment Calculator** | Compound growth modeller with live chart and year-by-year table |
| \ud83d\uddc2\ufe0f **Portfolio Analyzer** | Holdings tracker with allocation donut, sector heatmap, concentration warnings |
| \ud83c\udfb2 **Monte Carlo Simulator** | 500-path probabilistic retirement simulator with fan chart |
| \ud83d\udcb8 **Fee & Tax Optimizer** | Fee tier comparison + ISA vs taxable account tax drag calculator |
| \ud83d\udcda **Education Hub** | 16 topics from L100 foundations to L400 expert, with modal deep-dives |
| \ud83c\udf13 **Dark / Light Mode** | Full theme toggle, persisted within session |
| \ud83e\udd13 **Fun Mode** | Neon grid, CRT scanlines, Orbitron headings, floating emoji, chaotic copy |
| \ud83d\udcf1 **Responsive** | Usable on mobile, tablet, and desktop |

---

## Quick Start

### Deploy to GitHub Pages

```bash
# 1 \u2014 Fork or clone
git clone https://github.com/yourusername/investiq.git
cd investiq

# 2 \u2014 Push to your GitHub account
git remote set-url origin https://github.com/YOURNAME/investiq.git
git push -u origin main

# 3 \u2014 Enable GitHub Pages
#     Repository \u2192 Settings \u2192 Pages
#     Source: Deploy from branch
#     Branch: main   /   Folder: / (root)
#     \u2192 Save

# \u2705 Live at https://YOURNAME.github.io/investiq in ~60 seconds
```

### Run locally

No server required:

```bash
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

Or serve with any static file server:

```bash
npx serve .
# \u2192 http://localhost:3000
```

### Required files

```
investiq/
\u251c\u2500\u2500 index.html    \u2190 entire application (self-contained, ~130 KB)
\u251c\u2500\u2500 .nojekyll     \u2190 prevents GitHub Pages from running Jekyll (must exist, can be empty)
\u2514\u2500\u2500 README.md
```

> **Why `.nojekyll`?** Without it, GitHub Pages processes your repo with Jekyll and may mangle `<script>` tags or files with underscored names. An empty file with this name disables that behaviour entirely.

---

## Tools Reference

### \ud83d\udcca Investment Calculator

Model the long-run growth of any investment using the compound interest formula `A = P(1 + r/n)^(nt)`.

**Inputs**

| Parameter | Range | Default |
|---|---|---|
| Initial investment | \u00a3100 \u2013 \u00a3200,000 | \u00a35,000 |
| Annual return rate | 0.5% \u2013 30% | 7% |
| Time horizon | 1 \u2013 50 years | 20 years |
| Monthly contribution | \u00a30 \u2013 \u00a310,000 | \u00a30 |
| Compounding frequency | Annual / Quarterly / Monthly / Daily | Annual |
| Currency | \u00a3 / $ / \u20ac | \u00a3 |

**Outputs:** final balance, total invested, total interest, return multiple, CAGR, year-by-year breakdown table.

---

### \ud83d\uddc2\ufe0f Portfolio Analyzer

Enter your holdings manually and get an instant visual breakdown.

- **Donut chart** \u2014 allocation by asset class (ETF, Stocks, Bonds, Cash, Property, Commodities, Crypto, Other)
- **Horizontal bar chart** \u2014 sector exposure ranked by weight
- **Concentration warnings** \u2014 triggers if any single sector exceeds 50% or cash exceeds 30%
- Pre-loaded with a sample portfolio for instant visualisation

> Comes pre-populated with a diversified sample portfolio (VWRP, CSPX, AAPL, VGOV, Cash) so the charts render immediately on load.

---

### \ud83c\udfb2 Monte Carlo Simulator

Runs 500 independent simulations of your portfolio using log-normally distributed annual returns (Box-Muller transform).

**Inputs:** starting portfolio value, monthly contribution, time horizon, expected annual return, annual volatility (standard deviation).

**Outputs**

| Output | Description |
|---|---|
| Fan chart | Visualises the 5th, 25th, 50th, 75th, and 95th percentile paths |
| Median outcome | 50th percentile final balance |
| 95th / 5th percentile | Best and worst 5% of simulated outcomes |
| Success probability | % of simulations that beat total contributions |
| Percentile breakdown | P5 through P95 in a results table |

---

### \ud83d\udcb8 Fee & Tax Optimizer

**Tab 1 \u2014 Fee Impact**

Compares four expense ratio tiers against the same gross return assumption:

| Tier | Typical example | Annual fee |
|---|---|---|
| Passive ETF | VWRP, CSPX | 0.07% |
| Active ETF | Thematic / factor | 0.50% |
| Managed fund | Typical active | 1.00% |
| High-cost fund | Worst case | 1.75% |

Outputs final value per tier and total money lost vs the cheapest option.

**Tab 2 \u2014 ISA vs Taxable Account**

Models the same investment in a UK Stocks & Shares ISA (0% tax on gains and dividends) against a General Investment Account (~20% effective tax drag on returns). Outputs the lifetime tax shelter benefit in pounds.

---

### \ud83d\udcda Education Hub

Sixteen topics with card summaries and full modal deep-dives. Each modal includes: what it is, how it works, a real-world example, risks to know, and actionable tips.

---

## Education Hub

| Level | Topic | Key concept |
|---|---|---|
| **L100** | Stocks (Equities) | Fractional ownership, dividends, price discovery |
| **L100** | ETFs | Instant diversification, TER, accumulating vs distributing |
| **L100** | Bonds | Coupons, duration, inverse relationship with rates |
| **L100** | ISAs (UK) | \u00a320k annual allowance, tax-free growth, wrapper hierarchy |
| **L100** | Compound Interest | A = P(1+r)\u207f, Rule of 72, time as the key variable |
| **L100** | Inflation & Real Returns | CPI, real vs nominal, cash erosion |
| **L200** | Dollar Cost Averaging | Automating regular purchases, removing timing emotion |
| **L200** | Averaging Down | When it helps, when it destroys \u2014 the distinction |
| **L200** | Diversification | Uncorrelated assets, MPT, eliminating unsystematic risk |
| **L200** | Asset Allocation | 60/40, age-based rules, Brinson et al attribution |
| **L200** | Rebalancing | Calendar vs threshold, selling high / buying low automatically |
| **L300** | CFDs \u2014 Why to Avoid | Leverage mechanics, FCA warnings, 74\u201389% loss rate |
