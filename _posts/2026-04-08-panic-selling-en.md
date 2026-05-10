---
layout: post
title: "Decisions in times of crisis"
seo_title: "The cost of market timing and why you shouldn't sell during crashes"
date: 2026-04-08
categories: [finanza]
tags: [behavioral finance, investing, s&p500, panic selling, market timing]
description: "What to do when things go wrong"
pixel_icon: "panic.png"
smooth_image: true
lang: en
ref: panic-selling
---

I learned my strategy for moments of crisis from finance (maybe oversharing a bit here).

> “Time in the market beats timing the market.”
(Staying in the market is better than trying to slalom through crashes)

## What is Panic Selling and why to avoid it

Panic selling consists of compulsively selling your assets when things go wrong in the financial markets. Panic is a normal emotion, after all we are human, but giving in to fear and dismantling your investment portfolio to "salvage what you can" is the most expensive mistake an investor can make. Keeping a steady course during a crash is the real challenge of behavioral finance (and not only that).

## The real cost of Market Timing: S&P 500 Backtest

Below you will find an interactive backtest on the last 31 years of the S&P 500 (the global benchmark index, with the most convenient data, all in dollars). We are talking about a time horizon of roughly 11,700 market days.

One piece of data above all should make you think: almost all of the 10 best days (just 0.09% rounded up, practically the probability of finding a double-yolk egg) in the stock market occurred during a market crisis.

Sure, the opposite is also true, but the strategy of predicting the unpredictable in this game simply does not work. And if you make a mistake on the good days, you're in ~~deep shit~~ big trouble. There is only one very solid historical fact: in the long run, the market goes up. And this is why you are more likely to exit at the wrong time than at the right time.

What would have happened to your investments if you tried to time the market, ending up missing the 5, 10, or even 20 best days because of fear? And what would have happened if you sold right in the middle of a financial crash?

Play with the buttons in the interactive chart below and look at the numbers yourself, they speak volumes:

<div id="market-timing-widget">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,wght@0,300;0,400;0,500;0,700&family=DM+Mono:wght@400;500;600&display=swap" rel="stylesheet" />
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
#market-timing-widget {
--bg-gradient: linear-gradient(165deg, #0a0a0f 0%, #0f1118 40%, #0d0f16 100%);
--text-main: #e8e8ec;
--text-muted: rgba(255, 255, 255, 0.45);
--c-green: #00E676;
--c-orange: #FF6D00;
--c-red: #FF1744;
--c-blue: #4FC3F7;
--border-color: rgba(255, 255, 255, 0.08);
--card-bg: rgba(255, 255, 255, 0.025);

  background: var(--bg-gradient);
  color: var(--text-main);
  font-family: 'DM Sans', 'Helvetica Neue', sans-serif;
  padding: 32px 24px;
  border-radius: 16px;
  box-sizing: border-box;
  line-height: 1.5;
  margin: 32px 0;
  box-shadow: 0 12px 40px rgba(0,0,0,0.4);
}
#market-timing-widget * { box-sizing: border-box; }

.mtw-header { max-width: 920px; margin: 0 auto 36px; }
.mtw-eyebrow { font-size: 10px; letter-spacing: 3px; text-transform: uppercase; color: var(--c-orange); font-family: 'DM Mono', monospace; margin-bottom: 10px; font-weight: 500; }
.mtw-title { font-size: clamp(26px, 4vw, 38px); font-weight: 700; line-height: 1.15; margin: 0 0 10px; background: linear-gradient(135deg, #ffffff 30%, rgba(255,255,255,0.6)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; letter-spacing: -0.02em; }
.mtw-desc { font-size: 15px; color: var(--text-muted); line-height: 1.6; max-width: 660px; margin: 0; }
.mtw-mono { font-family: 'DM Mono', monospace; }

.mtw-controls { max-width: 920px; margin: 0 auto 28px; display: flex; flex-wrap: wrap; gap: 20px; }
.mtw-control-group { flex: 1 1 340px; }
.mtw-control-label { font-size: 10px; letter-spacing: 2px; text-transform: uppercase; color: rgba(255,255,255,0.35); margin-bottom: 10px; font-family: 'DM Mono', monospace; }
.mtw-btn-group { display: flex; flex-wrap: wrap; gap: 8px; }
.mtw-btn { padding: 8px 16px; border-radius: 6px; border: 1px solid var(--border-color); background: rgba(255,255,255,0.03); color: rgba(255,255,255,0.5); cursor: pointer; font-family: 'DM Mono', monospace; font-size: 13px; font-weight: 500; transition: all 0.2s; white-space: nowrap; }
.mtw-btn:hover { background: rgba(255,255,255,0.06); }
.mtw-btn.active-orange { border-color: var(--c-orange); background: rgba(255,109,0,0.12); color: var(--c-orange); }
.mtw-btn.active-red { border-color: var(--c-red); background: rgba(255,23,68,0.10); color: var(--c-red); }

.mtw-scorecards { max-width: 920px; margin: 0 auto 32px; display: flex; flex-wrap: wrap; gap: 12px; }
.mtw-card { flex: 1 1 200px; background: var(--card-bg); border: 1px solid rgba(255,255,255,0.06); border-radius: 10px; padding: 18px 20px; position: relative; overflow: hidden; }
.mtw-card-line { position: absolute; top: 0; left: 0; right: 0; height: 2px; opacity: 0.8; }
.mtw-card-title { font-size: 11px; color: rgba(255,255,255,0.4); margin-bottom: 8px; font-family: 'DM Mono', monospace; letter-spacing: 0.5px; }
.mtw-card-val { font-size: 28px; font-weight: 700; font-family: 'DM Mono', monospace; letter-spacing: -0.02em; }
.mtw-card-stats { display: flex; gap: 12px; margin-top: 8px; font-size: 11px; font-family: 'DM Mono', monospace; color: rgba(255,255,255,0.35); }
.mtw-card-diff { margin-top: 8px; font-size: 11px; font-family: 'DM Mono', monospace; color: var(--c-red); opacity: 0.8; }

.mtw-chart-container { 
  max-width: 920px; 
  margin: 0 auto 32px; 
  background: rgba(255,255,255,0.02); 
  border: 1px solid rgba(255,255,255,0.06); 
  border-radius: 12px; 
  padding: 24px 12px 16px; 
  height: 400px; 
  touch-action: pan-y;
}

.mtw-section { max-width: 920px; margin: 0 auto 32px; background: rgba(255,255,255,0.02); border: 1px solid rgba(255,255,255,0.06); border-radius: 12px; padding: 20px; }
.mtw-section-header { display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 14px; flex-wrap: wrap; gap: 8px; }
.mtw-days-grid { display: flex; flex-wrap: wrap; gap: 6px; }
.mtw-day-pill { border-radius: 6px; padding: 6px 12px; font-family: 'DM Mono', monospace; font-size: 12px; display: flex; gap: 10px; align-items: center; }
.mtw-day-pill.crisis { background: rgba(255,23,68,0.06); border: 1px solid rgba(255,23,68,0.18); }
.mtw-day-pill.normal { background: rgba(255,109,0,0.06); border: 1px solid rgba(255,109,0,0.15); }
.mtw-badge-new { font-size: 9px; color: var(--c-orange); background: rgba(255,109,0,0.12); padding: 1px 6px; border-radius: 3px; letter-spacing: 0.5px; }

.mtw-insight { margin-top: 16px; padding: 12px 16px; background: rgba(255,109,0,0.04); border: 1px solid rgba(255,109,0,0.1); border-radius: 8px; font-size: 13px; color: rgba(255,255,255,0.5); line-height: 1.6; }

.mtw-spotlight-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(130px, 1fr)); gap: 12px; }
.mtw-spot-card { background: rgba(255,255,255,0.025); border-radius: 8px; padding: 12px 16px; border: 1px solid rgba(255,255,255,0.05); }

.mtw-takeaway { max-width: 920px; margin: 0 auto 24px; padding: 20px 24px; background: linear-gradient(135deg, rgba(0,230,118,0.04), rgba(0,230,118,0.01)); border: 1px solid rgba(0,230,118,0.12); border-radius: 12px; font-size: 14px; line-height: 1.7; color: rgba(255,255,255,0.6); }

.mtw-footer { max-width: 920px; margin: 0 auto; text-align: center; font-size: 10px; color: rgba(255,255,255,0.2); font-family: 'DM Mono', monospace; letter-spacing: 1px; padding-top: 12px; border-top: 1px solid rgba(255,255,255,0.04); }

@media (max-width: 600px) {
  #market-timing-widget {
    padding: 24px 16px;
    margin: 24px 0;
  }
  .mtw-btn {
    padding: 12px 14px; 
    font-size: 14px;
    flex: 1 1 auto;
    text-align: center;
  }
  .mtw-card {
    padding: 16px 12px;
  }
  .mtw-card-val {
    font-size: 24px;
  }
  .mtw-card-stats {
    flex-wrap: wrap;
    gap: 8px;
  }
  .mtw-eyebrow, .mtw-control-label {
    font-size: 11px;
  }
  .mtw-spotlight-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 8px;
  }
  .mtw-chart-container {
    height: 300px;
    padding: 16px 8px 12px;
  }
}
</style>

<div class="mtw-header">
<div class="mtw-eyebrow">Behavioral Finance Backtest · 1995–2025</div>
<h3 class="mtw-title" style="margin-bottom:0;">The cost of market timing</h3>
<p class="mtw-desc" style="margin-top:10px;">
S&P 500 Total Return, 1995–2025 (31 years). Initial investment: <span style="color:var(--c-green)" class="mtw-mono">$10,000</span>.
Includes the April 2025 Tariff Crash and the historic April 9 rally (+9.52%, third largest post-war).
</p>
</div>

<div class="mtw-controls">
<div class="mtw-control-group">
<div class="mtw-control-label">Best days missed</div>
<div class="mtw-btn-group" id="mtw-missed-btns">
<button class="mtw-btn active-orange" data-val="5">5</button>
<button class="mtw-btn" data-val="10">10</button>
<button class="mtw-btn" data-val="20">20</button>
<button class="mtw-btn" data-val="30">30</button>
</div>
</div>
<div class="mtw-control-group">
<div class="mtw-control-label">Panic sell scenario</div>
<div class="mtw-btn-group" id="mtw-panic-btns">
</div>
</div>
</div>

<div class="mtw-scorecards" id="mtw-scorecards">
</div>

<div class="mtw-chart-container">
<canvas id="mtw-chart"></canvas>
</div>

<div class="mtw-section">
<div class="mtw-section-header">
<div class="mtw-control-label" id="mtw-days-title" style="margin:0; color:rgba(255,255,255,0.35);">The best days missed</div>
<div class="mtw-mono" id="mtw-days-pct" style="font-size:12px; color:var(--c-orange);"></div>
</div>
<div class="mtw-days-grid" id="mtw-days-grid">
</div>
<div class="mtw-insight">
<span style="color:var(--c-orange); font-weight:600;">Pattern confirmed in 2025 too:</span> On April 9, 2025, the S&P 500 recorded a +9.52% — the third largest daily rally since the post-war period — the exact day of the tariff pause. Just 48 hours earlier, the market was at annual lows with a -19% drawdown. Whoever sold on April 7 missed the most explosive rebound of the last 17 years.
</div>
</div>

<div class="mtw-section">
<div class="mtw-control-label">Spotlight: 2025 Tariff Crash</div>
<div class="mtw-spotlight-grid">
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">Max drawdown</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-red)">-18.9%</div>
</div>
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">Apr 9 Rally</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-green)">+9.52%</div>
</div>
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">May 12 Rally</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-green)">+3.26%</div>
</div>
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">Recovery from low</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-green)">+39%</div>
</div>
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">2025 Total Ret</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-blue)">+17.9%</div>
</div>
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">New ATH</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-blue)">Jun 27</div>
</div>
</div>
<p style="margin-top:16px; font-size:13px; color:rgba(255,255,255,0.45); line-height:1.65; margin-bottom:0;">
2025 is the perfect case study: a -19% drawdown caused by the "Liberation Day" tariffs (April 2), followed by a +39% rally from the bottom to a new all-time high on June 27. The market then closed the year with a +17.9% total return, the third consecutive double-digit year. Whoever sold at the April bottom lost the entire rebound.
</p>
</div>

<div class="mtw-takeaway" id="mtw-takeaway-text">
</div>

<div class="mtw-footer">
Data based on historical S&P 500 Total Return 1995–2025. Simulation for illustrative purposes only, not financial advice.
</div>

<script>
(function() {
const SP500_YEARLY = [
{ year: 1995, ret: 0.3743 }, { year: 1996, ret: 0.2296 }, { year: 1997, ret: 0.3336 },
{ year: 1998, ret: 0.2858 }, { year: 1999, ret: 0.2104 }, { year: 2000, ret: -0.0910 },
{ year: 2001, ret: -0.1189 }, { year: 2002, ret: -0.2210 }, { year: 2003, ret: 0.2868 },
{ year: 2004, ret: 0.1088 }, { year: 2005, ret: 0.0491 }, { year: 2006, ret: 0.1579 },
{ year: 2007, ret: 0.0549 }, { year: 2008, ret: -0.3700 }, { year: 2009, ret: 0.2646 },
{ year: 2010, ret: 0.1506 }, { year: 2011, ret: 0.0211 }, { year: 2012, ret: 0.1600 },
{ year: 2013, ret: 0.3239 }, { year: 2014, ret: 0.1369 }, { year: 2015, ret: 0.0138 },
{ year: 2016, ret: 0.1196 }, { year: 2017, ret: 0.2183 }, { year: 2018, ret: -0.0438 },
{ year: 2019, ret: 0.3149 }, { year: 2020, ret: 0.1840 }, { year: 2021, ret: 0.2871 },
{ year: 2022, ret: -0.1811 }, { year: 2023, ret: 0.2624 }, { year: 2024, ret: 0.2502 },
{ year: 2025, ret: 0.1790 },
];

  const BEST_DAYS = [
    { date: "2025-04-09", ret: 0.0952, year: 2025 }, { date: "2008-10-13", ret: 0.1180, year: 2008 },
    { date: "2008-10-28", ret: 0.1079, year: 2008 }, { date: "2020-03-24", ret: 0.0938, year: 2020 },
    { date: "2020-03-13", ret: 0.0932, year: 2020 }, { date: "2008-11-13", ret: 0.0692, year: 2008 },
    { date: "2008-11-21", ret: 0.0651, year: 2008 }, { date: "2020-03-26", ret: 0.0624, year: 2020 },
    { date: "2009-03-23", ret: 0.0723, year: 2009 }, { date: "2008-09-30", ret: 0.0581, year: 2008 },
    { date: "2009-03-10", ret: 0.0640, year: 2009 }, { date: "2002-07-24", ret: 0.0581, year: 2002 },
    { date: "2002-07-29", ret: 0.0544, year: 2002 }, { date: "2001-01-03", ret: 0.0505, year: 2001 },
    { date: "2022-11-10", ret: 0.0536, year: 2022 }, { date: "2020-04-06", ret: 0.0715, year: 2020 },
    { date: "2009-03-26", ret: 0.0565, year: 2009 }, { date: "2000-03-16", ret: 0.0484, year: 2000 },
    { date: "1997-10-28", ret: 0.0509, year: 1997 }, { date: "1998-09-08", ret: 0.0506, year: 1998 },
    { date: "2008-12-16", ret: 0.0441, year: 2008 }, { date: "2025-05-12", ret: 0.0326, year: 2025 },
    { date: "2011-08-09", ret: 0.0440, year: 2011 }, { date: "2011-10-27", ret: 0.0336, year: 2011 },
    { date: "2015-08-26", ret: 0.0335, year: 2015 }, { date: "2019-01-04", ret: 0.0340, year: 2019 },
    { date: "2018-12-26", ret: 0.0496, year: 2018 }, { date: "2023-01-06", ret: 0.0225, year: 2023 },
    { date: "2016-11-07", ret: 0.0225, year: 2016 }, { date: "2003-03-17", ret: 0.0336, year: 2003 },
    { date: "2003-03-21", ret: 0.0282, year: 2003 },
  ];

  const CRASH_BOTTOMS = [
    { name: "Dot-com (Oct '02)", sellYear: 2002, sellDrawdown: -0.49, reentryYear: 2003 },
    { name: "GFC (Mar '09)", sellYear: 2008, sellDrawdown: -0.57, reentryYear: 2009 },
    { name: "COVID (Mar '20)", sellYear: 2020, sellDrawdown: -0.34, reentryYear: 2020, reentryPartial: 0.60 },
    { name: "Bear 2022 (Oct '22)", sellYear: 2022, sellDrawdown: -0.25, reentryYear: 2023 },
    { name: "Tariff (Apr '25)", sellYear: 2025, sellDrawdown: -0.19, reentryYear: 2025, reentryPartial: 0.55 },
  ];

  const INITIAL_INVESTMENT = 10000;
  const CRISIS_YEARS = new Set([2000, 2001, 2002, 2008, 2009, 2020, 2022, 2025]);

  let state = { missedDays: 5, panicIdx: 1 };
  let myChart = null;

  function formatCurrency(v) {
    if (v >= 1000000) return `$${(v / 1000000).toFixed(1)}M`;
    if (v >= 1000) return `$${(v / 1000).toFixed(1)}K`;
    return `$${Math.round(v)}`;
  }
  function cagr(start, end, years) {
    if (start <= 0 || end <= 0) return 0;
    return (Math.pow(end / start, 1 / years) - 1) * 100;
  }

  function computeScenarios() {
    const data = [];
    let invested = INITIAL_INVESTMENT, missedBest = INITIAL_INVESTMENT, panicSeller = INITIAL_INVESTMENT;
    const bestDaysSorted = [...BEST_DAYS].sort((a, b) => b.ret - a.ret).slice(0, state.missedDays);
    const panicScenario = CRASH_BOTTOMS[state.panicIdx];
    
    let panicSold = false, panicReentered = false;
    const missedImpactByYear = {};
    for (const d of bestDaysSorted) {
      if (!missedImpactByYear[d.year]) missedImpactByYear[d.year] = 1;
      missedImpactByYear[d.year] *= (1 + d.ret);
    }

    data.push({ year: 1994, invested, missedBest, panicSeller });

    for (const { year, ret } of SP500_YEARLY) {
      invested *= (1 + ret);
      
      const yearDivisor = missedImpactByYear[year] || 1;
      const adjustedRet = ((1 + ret) / yearDivisor) - 1;
      missedBest *= (1 + adjustedRet);

      if (!panicSold && year === panicScenario.sellYear) {
        panicSeller *= (1 + panicScenario.sellDrawdown);
        panicSold = true;
        if (panicScenario.reentryYear === year) {
          panicSeller *= (1 + ret * (panicScenario.reentryPartial || 1));
          panicReentered = true;
        }
      } else if (panicSold && !panicReentered && year >= panicScenario.reentryYear) {
        panicSeller *= (1 + ret);
        panicReentered = true;
      } else if (panicSold && !panicReentered) {
      } else {
        panicSeller *= (1 + ret);
      }

      data.push({ year, invested: Math.round(invested), missedBest: Math.round(missedBest), panicSeller: Math.round(panicSeller) });
    }
    return { data, bestDaysSorted };
  }

  function initButtons() {
    const pCont = document.getElementById('mtw-panic-btns');
    CRASH_BOTTOMS.forEach((c, i) => {
      const btn = document.createElement('button');
      btn.className = `mtw-btn ${i === state.panicIdx ? 'active-red' : ''}`;
      btn.textContent = c.name;
      btn.onclick = () => { state.panicIdx = i; updateAll('panic'); };
      pCont.appendChild(btn);
    });

    document.querySelectorAll('#mtw-missed-btns .mtw-btn').forEach(btn => {
      btn.onclick = (e) => {
        state.missedDays = parseInt(e.target.dataset.val);
        updateAll('missed');
      };
    });
  }

  function updateAll(changedBy = 'init') {
    document.querySelectorAll('#mtw-missed-btns .mtw-btn').forEach(b => {
      b.className = `mtw-btn ${parseInt(b.dataset.val) === state.missedDays ? 'active-orange' : ''}`;
    });
    document.querySelectorAll('#mtw-panic-btns .mtw-btn').forEach((b, i) => {
      b.className = `mtw-btn ${i === state.panicIdx ? 'active-red' : ''}`;
    });

    const { data, bestDaysSorted } = computeScenarios();
    const finalRow = data[data.length - 1];
    const years = SP500_YEARLY.length;
    const crisisDaysCount = bestDaysSorted.filter(d => CRISIS_YEARS.has(d.year)).length;
    const crisisPct = bestDaysSorted.length ? Math.round((crisisDaysCount / bestDaysSorted.length) * 100) : 0;

    const cardsData = [
      { key: "invested", label: "Buy & Hold", color: "#00E676", value: finalRow.invested },
      { key: "missedBest", label: `Without top ${state.missedDays} days`, color: "#FF6D00", value: finalRow.missedBest },
      { key: "panicSeller", label: `Sold at bottom (${CRASH_BOTTOMS[state.panicIdx].name.split(' ')[0]})`, color: "#FF1744", value: finalRow.panicSeller },
    ];

    document.getElementById('mtw-scorecards').innerHTML = cardsData.map(s => {
      const cagrVal = cagr(INITIAL_INVESTMENT, s.value, years);
      const totalRet = ((s.value / INITIAL_INVESTMENT - 1) * 100);
      const diff = s.value - finalRow.invested;
      const diffStr = s.key !== "invested" ? `<div class="mtw-card-diff">${diff < 0 ? "" : "+"}${formatCurrency(diff)} vs Buy&Hold</div>` : '';
      return `
        <div class="mtw-card">
          <div class="mtw-card-line" style="background: ${s.color}"></div>
          <div class="mtw-card-title">${s.label}</div>
          <div class="mtw-card-val" style="color: ${s.color}">${formatCurrency(s.value)}</div>
          <div class="mtw-card-stats">
            <span>CAGR <span style="color:${cagrVal >= 0 ? '#4caf50' : '#ef5350'}">${cagrVal.toFixed(1)}%</span></span>
            <span>Tot <span style="color:${totalRet >= 0 ? '#4caf50' : '#ef5350'}">${totalRet >= 0 ? '+' : ''}${totalRet.toFixed(0)}%</span></span>
          </div>
          ${diffStr}
        </div>
      `;
    }).join('');

    document.getElementById('mtw-days-title').textContent = `The best ${state.missedDays} days you would have missed`;
    document.getElementById('mtw-days-pct').textContent = `${crisisPct}% fall during crises`;
    document.getElementById('mtw-days-grid').innerHTML = bestDaysSorted.map(d => {
      const isCrisis = CRISIS_YEARS.has(d.year);
      const badge = d.date === "2025-04-09" ? `<span class="mtw-badge-new">NEW</span>` : '';
      return `
        <div class="mtw-day-pill ${isCrisis ? 'crisis' : 'normal'}">
          <span style="color:rgba(255,255,255,0.4)">${d.date}</span>
          <span style="color:#00E676; font-weight:600">+${(d.ret * 100).toFixed(1)}%</span>
          ${badge}
        </div>
      `;
    }).join('');

    document.getElementById('mtw-takeaway-text').innerHTML = `
      <span style="color:#00E676; font-weight:600; font-size:15px;">Takeaway:</span> 
      Missing the best <span style="color:#FF6D00; font-weight:600">${state.missedDays} days</span> out of ${years} years 
      turns <span class="mtw-mono" style="color:#fff">$10,000</span> into 
      <span class="mtw-mono" style="color:#FF6D00">${formatCurrency(finalRow.missedBest)}</span> instead 
      of <span class="mtw-mono" style="color:#00E676">${formatCurrency(finalRow.invested)}</span>.
      Panic selling during the ${CRASH_BOTTOMS[state.panicIdx].name.split(' ')[0]} crash brings the total 
      to <span class="mtw-mono" style="color:#FF1744">${formatCurrency(finalRow.panicSeller)}</span>.
      <span style="color:rgba(255,255,255,0.7)">${crisisPct}% of the best days fall during the worst crises</span> — 
      the market rewards those who stay, not those who guess the timing.
    `;

    updateChart(data, changedBy);
  }

  function updateChart(data, changedBy) {
    const ctx = document.getElementById('mtw-chart').getContext('2d');

    if (myChart) {
      if (changedBy === 'missed') {
        myChart.data.datasets[1].data = data.map(d => d.missedBest);
        myChart.data.datasets[1].label = `Without top ${state.missedDays} days`;
      } else if (changedBy === 'panic') {
        myChart.data.datasets[2].data = data.map(d => d.panicSeller);
      } else {
        myChart.data.datasets[0].data = data.map(d => d.invested);
        myChart.data.datasets[1].data = data.map(d => d.missedBest);
        myChart.data.datasets[2].data = data.map(d => d.panicSeller);
      }
      myChart.update();
      return;
    }

    const labels = data.map(d => d.year);
    let gradGreen = ctx.createLinearGradient(0, 0, 0, 400);
    gradGreen.addColorStop(0, 'rgba(0, 230, 118, 0.2)'); gradGreen.addColorStop(1, 'rgba(0, 230, 118, 0)');
    let gradOrange = ctx.createLinearGradient(0, 0, 0, 400);
    gradOrange.addColorStop(0, 'rgba(255, 109, 0, 0.1)'); gradOrange.addColorStop(1, 'rgba(255, 109, 0, 0)');
    let gradRed = ctx.createLinearGradient(0, 0, 0, 400);
    gradRed.addColorStop(0, 'rgba(255, 23, 68, 0.1)'); gradRed.addColorStop(1, 'rgba(255, 23, 68, 0)');

    const datasets = [
      { label: 'Buy & Hold', data: data.map(d => d.invested), borderColor: '#00E676', backgroundColor: gradGreen, borderWidth: 2, fill: true, pointRadius: 0, pointHoverRadius: 5, tension: 0.4 },
      { label: `Without top ${state.missedDays} days`, data: data.map(d => d.missedBest), borderColor: '#FF6D00', backgroundColor: gradOrange, borderWidth: 2, borderDash: [6, 4], fill: true, pointRadius: 0, pointHoverRadius: 5, tension: 0.4 },
      { label: 'Panic Seller', data: data.map(d => d.panicSeller), borderColor: '#FF1744', backgroundColor: gradRed, borderWidth: 2, borderDash: [2, 4], fill: true, pointRadius: 0, pointHoverRadius: 5, tension: 0.4 }
    ];

    {
      Chart.defaults.color = 'rgba(255, 255, 255, 0.4)';
      Chart.defaults.font.family = "'DM Mono', monospace";
      
      myChart = new Chart(ctx, {
        type: 'line',
        data: { labels, datasets },
        options: {
          responsive: true, maintainAspectRatio: false,
          interaction: { mode: 'index', intersect: false },
          plugins: {
            legend: { display: false },
            tooltip: {
              backgroundColor: 'rgba(15,15,20,0.95)', titleColor: 'rgba(255,255,255,0.5)', bodyColor: '#fff',
              borderColor: 'rgba(255,255,255,0.08)', borderWidth: 1, padding: 12, boxPadding: 6,
              caretPadding: 10, intersect: false, 
              callbacks: { label: function(context) { return context.dataset.label + ': ' + formatCurrency(context.parsed.y); } }
            }
          },
          scales: {
            x: { grid: { color: 'rgba(255, 255, 255, 0.04)', drawBorder: false } },
            y: { type: 'logarithmic', grid: { color: 'rgba(255, 255, 255, 0.04)', drawBorder: false },
                 ticks: { callback: function(val) { return formatCurrency(val); } } }
          }
        }
      });
    }
  }

  window.addEventListener('load', function() {
    initButtons();
    updateAll();
  });

})();
</script>
</div>

## So, what to do during a financial crash?

**Nothing.**

A counterintuitive answer, but statistically proven. In finance it's called *buy and hold*.

Oh, we are all human, we all go off on a tangent even in good times, let alone in crises. I would also love to have a stop loss strategy that works, a magic formula for moments of crisis, but *there isn't one*. We can only suffer in silence watching our account deflate (at most rebalance, but that's a bit of a refinement).

Investment portfolios are built with precise goals and time horizons when things are going well (in "peacetime"). And you already know that, sooner or later, things will go wrong: the economic cycle works like this. Market crashes are physiological, there's no escaping them.

## Resilience
If there is a concept that gets on my ~~balls~~ nerves it's exactly Resilience. So, when I developed my "crisis management" strategy this was the first objection I raised to myself: if the world "suggests" to you in every way that you are doing it wrong, maybe, incredibly, you are doing it wrong. Reality dictates the rules. The idea that we are fine just the way we are doesn't belong to me. If something *doesn't work*, then it doesn't work. What's the difference? Timing. In moments of crisis, resilience is needed. I'm not saying that the allocation you logically and carefully decided upon in peacetime is necessarily correct. I'm saying that moments of crisis are **not** the right times to review your strategy. You're going down, you knew it would happen. It's inevitable. Things will statistically get better. It's at that point that you can do a backward analysis and eventually change it.

Staying on the tracks when the charts are red means doing well. If your investment strategy was properly structured, it will withstand the blow during the crisis (and lay the foundations for future returns). If it was poorly made, the middle of a financial crash is absolutely not the right time to make emotionally-driven decisions ~~half-assed~~.

Any possible analogy with life is left to the reader.