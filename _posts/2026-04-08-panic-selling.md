---
layout: post
title: "Decisioni nei momenti di crisi"
seo_title: "Il costo del market timing e perché non vendere durante i crolli"
date: 2026-04-08
categories: [finanza]
tags: [finanza comportamentale, investimenti, s&p500, panic selling, market timing]
description: "Cosa fare quando le cose vanno male"
pixel_icon: "panic.png"
smooth_image: true
---

La mia strategia per i momenti di crisi l'ho imparata dalla finanza (forse un po' troppo oversharing qui).

>“Time in the market beats timing the market.”
(Restare nel mercato è meglio che cercare di fare la gincana dei crolli)

## Cos'è il Panic Selling e perché evitarlo

Il panic selling consiste nel vendere compulsivamente i propri asset quando le cose vanno male sui mercati finanziari. Il panico è un'emozione normale, dopotutto siamo umani, ma cedere alla paura e smantellare il proprio portafoglio di investimenti per "salvare il salvabile" è l'errore più costoso che un investitore possa fare. Tenere la barra dritta durante un crollo è la vera sfida della finanza comportamentale (e non solo).

## Il vero costo del Market Timing: Backtest sull'S&P 500

Di seguito trovi un backtest interattivo sugli ultimi 31 anni dell’S&P 500 (l'indice di riferimento globale, con i dati più comodi e tutti in dollari). Parliamo di un orizzonte temporale di circa 11.700 giorni di mercato.

Un dato su tutti dovrebbe farti riflettere: la quasi totalità dei 10 giorni migliori (appena lo 0,09% arrotondato per eccesso, praticamente la probabilità di trovare un uovo con due tuorli) in borsa è avvenuta durante una crisi di mercato.

Certo è vero anche il contrario, ma la strategia di prevedere l'imprevedibile in questo gioco non funziona. E se sbagli nei giorni buoni sono ~~cazzi amari~~ dolori. C'è un solo dato storico solidissimo: alla lunga il mercato sale. Ed è per questo che è più probabile uscire al momento sbagliato che a quello giusto.

Cosa sarebbe successo ai tuoi investimenti cercando di fare market timing, finendo per perdere i 5, 10, o anche 20 giorni migliori per colpa della paura? E cosa sarebbe successo vendendo nel bel mezzo di un crash finanziario?

Gioca con i bottoni nel grafico interattivo qui sotto e guarda tu stesso i numeri, parlano da soli:

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
  touch-action: pan-y; /* Permette lo scroll verticale nativo su mobile */
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

/* --- OTTIMIZZAZIONI MOBILE --- */
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
<h3 class="mtw-title" style="margin-bottom:0;">Il costo del market timing</h3>
<p class="mtw-desc" style="margin-top:10px;">
S&P 500 Total Return, 1995–2025 (31 anni). Investimento iniziale: <span style="color:var(--c-green)" class="mtw-mono">$10,000</span>.
Include il Crollo dei Dazi di aprile 2025 e il rally storico del 9 aprile (+9.52%, terzo più grande dal dopoguerra).
</p>
</div>

<div class="mtw-controls">
<div class="mtw-control-group">
<div class="mtw-control-label">Giorni migliori persi</div>
<div class="mtw-btn-group" id="mtw-missed-btns">
<button class="mtw-btn active-orange" data-val="5">5</button>
<button class="mtw-btn" data-val="10">10</button>
<button class="mtw-btn" data-val="20">20</button>
<button class="mtw-btn" data-val="30">30</button>
</div>
</div>
<div class="mtw-control-group">
<div class="mtw-control-label">Scenario panic sell</div>
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
<div class="mtw-control-label" id="mtw-days-title" style="margin:0; color:rgba(255,255,255,0.35);">I giorni migliori saltati</div>
<div class="mtw-mono" id="mtw-days-pct" style="font-size:12px; color:var(--c-orange);"></div>
</div>
<div class="mtw-days-grid" id="mtw-days-grid">
</div>
<div class="mtw-insight">
<span style="color:var(--c-orange); font-weight:600;">Pattern confermato anche nel 2025:</span> Il 9 aprile 2025 l'S&P 500 ha registrato un +9.52% — il terzo rally giornaliero più grande dal dopoguerra — il giorno esatto della pausa sui dazi. Solo 48 ore prima, il mercato era ai minimi annuali con un drawdown del -19%. Chi ha venduto il 7 aprile ha perso il rimbalzo più esplosivo degli ultimi 17 anni.
</div>
</div>

<div class="mtw-section">
<div class="mtw-control-label">Spotlight: Crollo dei Dazi 2025</div>
<div class="mtw-spotlight-grid">
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">Drawdown max</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-red)">-18.9%</div>
</div>
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">Rally 9 Apr</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-green)">+9.52%</div>
</div>
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">Rally 12 Mag</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-green)">+3.26%</div>
</div>
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">Recupero dal low</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-green)">+39%</div>
</div>
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">Total Ret 2025</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-blue)">+17.9%</div>
</div>
<div class="mtw-spot-card">
<div class="mtw-control-label" style="font-size:10px; margin-bottom:4px">Nuovo ATH</div>
<div class="mtw-mono" style="font-size:22px; font-weight:700; color:var(--c-blue)">27 Giu</div>
</div>
</div>
<p style="margin-top:16px; font-size:13px; color:rgba(255,255,255,0.45); line-height:1.65; margin-bottom:0;">
Il 2025 è il caso studio perfetto: un drawdown del -19% causato dai dazi del "Liberation Day" (2 aprile), seguito da un rally del +39% dal minimo al nuovo massimo storico il 27 giugno. Il mercato ha poi chiuso l'anno con un total return del +17.9%, il terzo anno consecutivo a doppia cifra. Chi ha venduto al bottom di aprile ha perso l'intero rimbalzo.
</p>
</div>

<div class="mtw-takeaway" id="mtw-takeaway-text">
</div>

<div class="mtw-footer">
Dati basati su rendimenti storici S&P 500 Total Return 1995–2025. Simulazione a scopo illustrativo, non è consulenza finanziaria.
</div>

<script>
(function() {
// Dati S&P 500
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

  // Stato
  let state = { missedDays: 5, panicIdx: 1 };
  let myChart = null;

  // Utility
  function formatCurrency(v) {
    if (v >= 1000000) return `$${(v / 1000000).toFixed(1)}M`;
    if (v >= 1000) return `$${(v / 1000).toFixed(1)}K`;
    return `$${Math.round(v)}`;
  }
  function cagr(start, end, years) {
    if (start <= 0 || end <= 0) return 0;
    return (Math.pow(end / start, 1 / years) - 1) * 100;
  }

  // Motore Logico
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
        // cash
      } else {
        panicSeller *= (1 + ret);
      }

      data.push({ year, invested: Math.round(invested), missedBest: Math.round(missedBest), panicSeller: Math.round(panicSeller) });
    }
    return { data, bestDaysSorted };
  }

  // Inizializza Pulsanti
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

  // Aggiorna UI
  function updateAll(changedBy = 'init') {
    // Aggiorna classi bottoni
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

    // Scorecards
    const cardsData = [
      { key: "invested", label: "Buy & Hold", color: "#00E676", value: finalRow.invested },
      { key: "missedBest", label: `Senza i migliori ${state.missedDays} gg`, color: "#FF6D00", value: finalRow.missedBest },
      { key: "panicSeller", label: `Venduto al bottom (${CRASH_BOTTOMS[state.panicIdx].name.split(' ')[0]})`, color: "#FF1744", value: finalRow.panicSeller },
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

    // Lista giorni
    document.getElementById('mtw-days-title').textContent = `I ${state.missedDays} giorni migliori che avresti saltato`;
    document.getElementById('mtw-days-pct').textContent = `${crisisPct}% cadono durante crisi`;
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

    // Takeaway
    document.getElementById('mtw-takeaway-text').innerHTML = `
      <span style="color:#00E676; font-weight:600; font-size:15px;">Takeaway:</span> 
      Perdere i migliori <span style="color:#FF6D00; font-weight:600">${state.missedDays} giorni</span> su ${years} anni 
      trasforma <span class="mtw-mono" style="color:#fff">$10,000</span> in 
      <span class="mtw-mono" style="color:#FF6D00">${formatCurrency(finalRow.missedBest)}</span> invece 
      di <span class="mtw-mono" style="color:#00E676">${formatCurrency(finalRow.invested)}</span>.
      Il panic selling durante il crash ${CRASH_BOTTOMS[state.panicIdx].name.split(' ')[0]} porta il totale 
      a <span class="mtw-mono" style="color:#FF1744">${formatCurrency(finalRow.panicSeller)}</span>.
      <span style="color:rgba(255,255,255,0.7)">Il ${crisisPct}% dei giorni migliori cade durante le crisi peggiori</span> — 
      il mercato premia chi resta, non chi azzecca il timing.
    `;

    // Aggiorna Grafico
    updateChart(data, changedBy);
  }

  function updateChart(data, changedBy) {
    const ctx = document.getElementById('mtw-chart').getContext('2d');

    if (myChart) {
      if (changedBy === 'missed') {
        myChart.data.datasets[1].data = data.map(d => d.missedBest);
        myChart.data.datasets[1].label = `Senza top ${state.missedDays} gg`;
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

    // Prima inizializzazione
    const labels = data.map(d => d.year);
    let gradGreen = ctx.createLinearGradient(0, 0, 0, 400);
    gradGreen.addColorStop(0, 'rgba(0, 230, 118, 0.2)'); gradGreen.addColorStop(1, 'rgba(0, 230, 118, 0)');
    let gradOrange = ctx.createLinearGradient(0, 0, 0, 400);
    gradOrange.addColorStop(0, 'rgba(255, 109, 0, 0.1)'); gradOrange.addColorStop(1, 'rgba(255, 109, 0, 0)');
    let gradRed = ctx.createLinearGradient(0, 0, 0, 400);
    gradRed.addColorStop(0, 'rgba(255, 23, 68, 0.1)'); gradRed.addColorStop(1, 'rgba(255, 23, 68, 0)');

    const datasets = [
      { label: 'Buy & Hold', data: data.map(d => d.invested), borderColor: '#00E676', backgroundColor: gradGreen, borderWidth: 2, fill: true, pointRadius: 0, pointHoverRadius: 5, tension: 0.4 },
      { label: `Senza top ${state.missedDays} gg`, data: data.map(d => d.missedBest), borderColor: '#FF6D00', backgroundColor: gradOrange, borderWidth: 2, borderDash: [6, 4], fill: true, pointRadius: 0, pointHoverRadius: 5, tension: 0.4 },
      { label: 'Panic Seller', data: data.map(d => d.panicSeller), borderColor: '#FF1744', backgroundColor: gradRed, borderWidth: 2, borderDash: [2, 4], fill: true, pointRadius: 0, pointHoverRadius: 5, tension: 0.4 }
    ];

    {
      // Inizializza Chart.js se non esiste
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
              caretPadding: 10, intersect: false, /* Fix Mobile */
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

  // Start
  // Wait for chart.js to load just in case
  window.addEventListener('load', function() {
    initButtons();
    updateAll();
  });

})();


</script>

</div>

## Quindi, cosa fare durante un crollo finanziario?

**Niente.**

Risposta controintuitiva, ma statisticamente dimostrata. In finanza si chiama *buy and hold*.

Oh, siamo tutti umani, tutti partiamo per la tangente anche nei momenti buoni, figuriamoci nelle crisi. Pure a me piacerebbe avere una strategia di [stop loss](https://it.wikipedia.org/wiki/Stop_loss) che funzioni, una formula magica per i momenti di crisi, ma *non c'è*. Possiamo solo soffrire in silenzio vedendo il conto sgonfiarsi (al massimo ribilanciare, ma questa è un po' una finezza).

I portafogli di investimento vengono costruiti con obiettivi e orizzonti temporali precisi quando le cose vanno bene (in "tempo di pace"). E sai già che, prima o poi, le cose andranno male: il ciclo economico funziona così. I crolli dei mercati sono fisiologici, non si scappa.

## Resilienza
Se c'è un concetto che proprio mi sta sulle ~~palle~~ scatole è proprio la Resilienza. Quindi, quando ho elaborato la mia strategia di "crisis management" questa è la prima obiezione che mi sono fatto: se il mondo ti "suggerisce" in tutti i modi che stai sbagliando, forse, incredibilmente, stai sbagliando. È la realtà che detta le regole. L'idea che andiamo bene così come siamo non mi appartiene. Se una cosa *non funziona*, allora non funziona. Qual è la differenza? Il momento. Nei momenti di crisi la resilienza serve. Non dico che l'allocazione che hai deciso con logica e criterio, in tempi di pace, sia necessariamente corretta. Dico che i momenti di crisi **non** sono i momenti adatti per rivedere la strategia. Stai andando verso il basso, sapevi che sarebbe successo. È inevitabile. Le cose andranno statisticamente meglio. È a quel punto che potrai fare un'analisi a ritroso e cambiare, eventualmente.

Restare sui binari quando i grafici sono rossi vuol dire fare bene. Se la tua strategia di investimento era strutturata correttamente, nella crisi reggerà il colpo (e getterà le basi per i rendimenti futuri). Se era fatta male, il bel mezzo di un crollo finanziario non è assolutamente il momento adatto per prendere decisioni ~~a cazzo di cane~~ mossi dall'emotività.

Ogni eventuale analogia con la vita è lasciata al lettore.
