---
layout: post
title: "The science of tagliatelle"
seo_title: "The science of tagliatelle: rheology and chemistry of the perfect dough"
date: 2026-05-18
categories: [cucina, scienza]
tags: [reologia, pasta, glutine, chimica-applicata]
description: "Rheology and thermodynamics to achieve the perfect dough and texture."
pixel_icon: "tagliatelle.png"
smooth_image: true
lang: en
ref: tagliatelle
---

As you might have guessed: I like to cook. Why? I could make a whole speech about cooking as applied chemistry, but the reality is that I like to eat. *That's it.*

---
<br>
<img src="/assets/tagliatelle.jpeg" alt="Tagliatelle" style="border-radius: 16px; width: 100%;" />

---

## INGREDIENTS AND DOSES

Eggs and flour.

The goal is a tagliatella that:

**Is workable.** Here hydration is boss. Too much water and the dough will be worse than slime, too little and it will be impossible sand to knead. Temperature is also fundamental in this phase. The dough must be warm enough to be plastic, but not too warm to increase gliadin mobility and gluten relaxation (it becomes sticky and slips away).

**Is not a brick, but doesn't fall apart (chewy).** For this you need to control the strength (W) of the flour. It's not exactly correct, but we can roughly equate protein content and flour strength. Semolina flour has a gliadin/glutenin ratio that makes it tougher; it would give the right consistency, but is very difficult to work with. A 00 flour would be a good solution, but has other critical issues. (Emilian tradition dictates using only 00 or 0 flour, but it's clear I'm not passionate about traditions, but logic.)

**Has good roughness.** The tagliatella must be rough enough to hold the sauce. Here too, semolina flour would be ideal. 00 flour alone has too smooth a texture.

From this it is clear that the ideal is a mix of flours. Through reasoning on rheology, I empirically found that a **70% 00 flour and 30% semolina** is a good mix. Right total flour strength and good roughness.

Now the eggs: on average an egg (50 g) is 75% water by weight. Ideal hydration is around 30-35%. So just do egg weight × 2 and we have the weight of the flour mix to add.

<details markdown="1">
  <summary>Some chemistry nerdiness</summary>
Commercial flours have physiological residual moisture (around 12-14%). In 100 g of flour (mix), there is already about 13 g of water. By adding a medium 50 g egg (made up of 75% water), we introduce another 37.5 g of liquids. We reach a total of about 50.5 g of water for 150 g of total mass. This generates an absolute hydration of **33.6%**, positioning the system exactly in the middle of the optimal range.
</details>

<!-- ==================== RHEOLOGICAL SIMULATOR ==================== -->

<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600;700;800&family=DM+Sans:wght@400;500;600;700&display=swap">
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
#tagliatella-sim {
    --ts-bg: var(--card-bg, #ffffff);
    --ts-panel: var(--bg-color, #f9fafb);
    --ts-border: var(--border-color, #e5e5e5);
    --ts-border-light: var(--border-color, #d1d5db);
    --ts-text: var(--text-color, #222222);
    --ts-text-dim: var(--text-muted, #6b7280);
    --ts-text-bright: var(--text-color, #111111);
    --ts-accent: #3b82f6;
    --ts-green: #10b981;
    --ts-yellow: #eab308;
    --ts-mono: 'JetBrains Mono', ui-monospace, SFMono-Regular, monospace;
    --ts-sans: inherit;
}

#tagliatella-sim * { box-sizing: border-box; margin: 0; padding: 0; }

#tagliatella-sim {
    background: var(--ts-bg);
    color: var(--ts-text);
    border-radius: 16px;
    border: 1px solid var(--ts-border);
    font-family: var(--ts-sans);
    box-shadow: 0 4px 15px rgba(0,0,0,0.05);
    overflow: hidden;
    margin: 2.5rem auto;
}

#tagliatella-sim .ts-header {
    padding: 20px 24px 16px;
    border-bottom: 1px solid var(--ts-border);
}
#tagliatella-sim .ts-header h3 {
    font-size: 15px;
    font-weight: 700;
    color: var(--ts-text-bright);
    letter-spacing: -0.01em;
    line-height: 1.3;
}
#tagliatella-sim .ts-header p {
    font-size: 12px;
    color: var(--ts-text-dim);
    margin-top: 2px;
    line-height: 1.4;
}

#tagliatella-sim .ts-body {
    padding: 24px;
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 20px;
}
@media (max-width: 640px) {
    #tagliatella-sim .ts-body { grid-template-columns: 1fr; }
}

#tagliatella-sim .ts-controls {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

#tagliatella-sim .ts-panel {
    background: var(--ts-panel);
    border: 1px solid var(--ts-border);
    border-radius: 12px;
    padding: 20px;
}

#tagliatella-sim .ts-panel-title {
    font-size: 10px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--ts-text-dim);
    padding-bottom: 12px;
    margin-bottom: 16px;
    border-bottom: 1px solid var(--ts-border);
}

#tagliatella-sim .ts-field {
    margin-bottom: 16px;
}
#tagliatella-sim .ts-field:last-child { margin-bottom: 0; }

#tagliatella-sim .ts-field label {
    display: block;
    font-size: 10px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--ts-text-dim);
    margin-bottom: 7px;
    line-height: 1.4;
}
#tagliatella-sim .ts-val {
    font-family: var(--ts-mono);
    color: var(--ts-accent);
    font-weight: 700;
    font-size: 11px;
}
#tagliatella-sim .ts-unit {
    font-family: var(--ts-mono);
    font-size: 10px;
    color: var(--ts-text-dim);
}

#tagliatella-sim input[type="range"] {
    -webkit-appearance: none;
    appearance: none;
    width: 100%;
    height: 6px;
    background: var(--ts-border-light);
    border-radius: 3px;
    outline: none;
    cursor: pointer;
}
#tagliatella-sim input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 16px; height: 16px;
    background: var(--ts-bg);
    border-radius: 50%;
    border: 2.5px solid var(--ts-accent);
    cursor: pointer;
    transition: transform 0.15s, box-shadow 0.15s;
}
#tagliatella-sim input[type="range"]::-webkit-slider-thumb:hover {
    transform: scale(1.2);
    box-shadow: 0 0 0 5px rgba(59,130,246,0.15);
}
#tagliatella-sim input[type="range"]::-moz-range-thumb {
    width: 16px; height: 16px;
    background: var(--ts-bg);
    border-radius: 50%;
    border: 2.5px solid var(--ts-accent);
    cursor: pointer;
}

#tagliatella-sim .ts-range-labels {
    display: flex;
    justify-content: space-between;
    font-size: 9px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: var(--ts-text-dim);
    margin-top: 5px;
}

#tagliatella-sim .ts-sweet-spot {
    position: relative;
    height: 0;
    pointer-events: none;
}
#tagliatella-sim .ts-sweet-spot::before {
    content: '';
    position: absolute;
    top: -10px;
    width: 1.5px;
    height: 8px;
    background: var(--ts-green);
    border-radius: 1px;
    opacity: 0.5;
}
#tagliatella-sim .ts-sweet-spot::after {
    content: '';
    position: absolute;
    top: -27px;
    transform: translateX(-50%);
    font-size: 8px;
    font-family: var(--ts-mono);
    color: var(--ts-green);
    font-weight: 600;
    white-space: nowrap;
    opacity: 0.6;
}

#tagliatella-sim .ts-status {
    padding: 12px 14px;
    border-radius: 8px;
    border: 1px solid var(--ts-border);
    transition: all 0.3s;
    margin-bottom: 14px;
}
#tagliatella-sim .ts-status-label {
    font-size: 9px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--ts-text-dim);
    margin-bottom: 3px;
}
#tagliatella-sim .ts-status-text {
    font-family: var(--ts-mono);
    font-size: 13px;
    font-weight: 700;
    transition: color 0.3s;
    margin-bottom: 6px;
}
#tagliatella-sim .ts-status-desc {
    font-size: 11px;
    color: var(--ts-text);
    line-height: 1.5;
}

#tagliatella-sim .ts-metrics {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 8px;
}
#tagliatella-sim .ts-metric {
    background: var(--ts-bg);
    border: 1px solid var(--ts-border);
    border-radius: 8px;
    padding: 10px 8px;
    text-align: center;
}
#tagliatella-sim .ts-metric-label {
    font-size: 9px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--ts-text-dim);
    display: block;
    margin-bottom: 4px;
}
#tagliatella-sim .ts-metric-val {
    font-family: var(--ts-mono);
    font-size: 20px;
    font-weight: 800;
}
#tagliatella-sim .ts-metric-unit {
    font-family: var(--ts-mono);
    font-size: 10px;
    color: var(--ts-text-dim);
}

#tagliatella-sim .ts-viz {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

#tagliatella-sim .ts-chart-wrap {
    position: relative;
    height: 210px;
    width: 100%;
}

#tagliatella-sim .ts-panel-footer {
    font-size: 9px;
    font-family: var(--ts-mono);
    color: var(--ts-text-dim);
    margin-top: 8px;
}

#tagliatella-sim .ts-microscope-wrap {
    position: relative;
    width: 100%;
    height: 190px;
    background: var(--ts-bg);
    border-radius: 8px;
    overflow: hidden;
    border: 1px solid var(--ts-border);
}

#tagliatella-sim .ts-legend {
    position: absolute;
    top: 8px;
    left: 10px;
    font-size: 9px;
    font-family: var(--ts-mono);
    color: var(--ts-text-dim);
    background: var(--ts-panel);
    padding: 4px 8px;
    border-radius: 4px;
    line-height: 1.9;
    border: 1px solid var(--ts-border);
    box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}
#tagliatella-sim .ts-legend-dot {
    display: inline-block;
    width: 8px; height: 8px;
    border-radius: 50%;
    margin-right: 4px;
    vertical-align: middle;
}
#tagliatella-sim .ts-microscope-label {
    position: absolute;
    bottom: 6px;
    right: 8px;
    font-size: 9px;
    font-family: var(--ts-mono);
    color: var(--ts-text-dim);
    background: var(--ts-panel);
    padding: 2px 6px;
    border-radius: 3px;
    border: 1px solid var(--ts-border);
}
</style>

<div id="tagliatella-sim">
    <div class="ts-header">
        <h3>Dough Rheology Simulator</h3>
        <p>Viscoelastic analysis for fresh egg pasta</p>
    </div>

    <div class="ts-body">
        <div class="ts-controls">
            <div class="ts-panel">
                <div class="ts-panel-title">Physical Parameters</div>

                <div class="ts-field">
                    <label>Hydration · <span class="ts-val" id="tw-hydration-val">33</span><span class="ts-unit">%</span></label>
                    <input type="range" id="tw-hydration" min="25" max="55" value="33" step="1">
                    <div class="ts-range-labels"><span>25% Dry</span><span>55% Liquid</span></div>
                </div>

                <div class="ts-field">
                    <label>Flour Mix (% Semolina) · <span class="ts-val" id="tw-semola-val">30</span><span class="ts-unit">%</span></label>
                    <div class="ts-sweet-spot" style="margin-left: 30%;"></div>
                    <input type="range" id="tw-semola" min="0" max="100" value="30" step="5">
                    <div class="ts-range-labels"><span>0% only 00</span><span>100% semolina</span></div>
                </div>

                <div class="ts-field">
                    <label>Temperature · <span class="ts-val" id="tw-temperature-val">22</span><span class="ts-unit">°C</span></label>
                    <input type="range" id="tw-temperature" min="4" max="40" value="22" step="1">
                    <div class="ts-range-labels"><span>4°C Fridge</span><span>40°C Hot</span></div>
                </div>
            </div>

            <div class="ts-panel">
                <div class="ts-panel-title">Mechanical Analysis</div>

                <div class="ts-status" id="tw-status-box" style="background: #10b98115; border-color: #10b98140;">
                    <div class="ts-status-label">Workability Status</div>
                    <div class="ts-status-text" id="tw-status-text" style="color: #10b981;">Optimal range</div>
                    <div class="ts-status-desc" id="tw-status-desc">Correct balance between extensibility and toughness.</div>
                </div>

                <div class="ts-metrics">
                    <div class="ts-metric">
                        <span class="ts-metric-label">Elasticity</span>
                        <span class="ts-metric-val" id="tw-g-prime-val" style="color:#4f46e5;">5.0</span><span class="ts-metric-unit">/10</span>
                    </div>
                    <div class="ts-metric">
                        <span class="ts-metric-label">Stickiness</span>
                        <span class="ts-metric-val" id="tw-stickiness-val" style="color:#f43f5e;">1.8</span><span class="ts-metric-unit">/10</span>
                    </div>
                    <div class="ts-metric">
                        <span class="ts-metric-label">Roughness</span>
                        <span class="ts-metric-val" id="tw-roughness-val" style="color:#eab308;">3.7</span><span class="ts-metric-unit">/10</span>
                    </div>
                </div>
            </div>
        </div>

        <div class="ts-viz">
            <div class="ts-panel">
                <div class="ts-panel-title">Rheological Curves</div>
                <div class="ts-chart-wrap">
                    <canvas id="tw-rheologyChart"></canvas>
                </div>
                <div class="ts-panel-footer">Curves calculated at current mix and temperature. Circles indicate current state.</div>
            </div>

            <div class="ts-panel">
                <div class="ts-panel-title">Microscopic View — Gluten Network & Granules</div>
                <div class="ts-microscope-wrap">
                    <canvas id="tw-microscopeCanvas" style="position:absolute;top:0;left:0;width:100%;height:100%;"></canvas>
                    <div class="ts-legend">
                        <div><span class="ts-legend-dot" style="background:#94a3b8;"></span>gluten</div>
                        <div><span class="ts-legend-dot" style="background:#fcd34d;"></span>semolina</div>
                        <div><span class="ts-legend-dot" style="background:#e5e7eb; border: 1px solid #d1d5db;"></span>00 starch</div>
                    </div>
                    <div class="ts-microscope-label">qualitative simulation</div>
                </div>
            </div>
        </div>
    </div>
</div>

<script>
(function () {
    // ==== DOM ====
    const hydrInput = document.getElementById('tw-hydration');
    const semolaInput = document.getElementById('tw-semola');
    const tempInput = document.getElementById('tw-temperature');
    const hydrVal = document.getElementById('tw-hydration-val');
    const semolaValEl = document.getElementById('tw-semola-val');
    const tempVal = document.getElementById('tw-temperature-val');
    const statusBox = document.getElementById('tw-status-box');
    const statusText = document.getElementById('tw-status-text');
    const statusDesc = document.getElementById('tw-status-desc');
    const gPrimeText = document.getElementById('tw-g-prime-val');
    const stickinessText = document.getElementById('tw-stickiness-val');
    const roughnessText = document.getElementById('tw-roughness-val');
    const canvas = document.getElementById('tw-microscopeCanvas');
    const ctx = canvas.getContext('2d');

    // ==== State ====
    const state = { H: 33, S: 30, T: 22, G: 0, St: 0, R: 0 };
    let chartInstance = null;
    let lastSemolaForNodes = -1;

    // ==== Physical model ====
    function proteinPct(S) { return 10 + S * 0.035; }

    function calcG(H, S, T) {
        const p = proteinPct(S);
        const val = 5 + (p - 11.05) * 1.4 - (H - 33) * 0.18 - (T - 22) * 0.06;
        return Math.max(0.2, Math.min(10, val));
    }

    function calcSt(H, S, T) {
        let base;
        if (H <= 36) base = Math.max(0, (H - 25) * 0.18);
        else base = Math.min(10, 1.98 + Math.pow(H - 36, 2.2) * 0.04);
        const tempMod = Math.max(0, (T - 22)) * 0.18;
        const semolaMod = -(S - 30) * 0.012;
        return Math.max(0, Math.min(10, base + tempMod + semolaMod));
    }

    function calcR(S) { return Math.min(10, 1 + S * 0.09); }

    function deriveStatus(H, S, T, G, St) {
        if (T > 32) return {
            text: "Excessive heat",
            desc: "Gliadin becomes more mobile and gluten relaxes: the dough becomes sticky and loses toughness. There is no denaturation (happens above 60°C), just excessive plasticization. Cool before working.",
            color: "#ef4444"
        };
        if (T < 14) return {
            text: "Too cold",
            desc: "Poorly extensible gluten, rigid dough. The sheet will tear during lamination. Let it acclimatize to room temperature.",
            color: "#0ea5e9"
        };
        if (H < 30) return {
            text: "Under-hydrated",
            desc: "Insufficient water to develop the gluten network. Crumbly, non-cohesive dough. Add liquid a teaspoon at a time.",
            color: "#f97316"
        };
        if (St > 6.5) return {
            text: "Critical stickiness",
            desc: "Gluey dough, structurally collapsed. Un-rollable without abundant dusting of semolina, probably unrecoverable by machine.",
            color: "#ef4444"
        };
        if (St > 4.5) return {
            text: "Stickiness risk",
            desc: "Manageable, but requires generous dusting and attention to the rollers. Consider less water or more semolina in the mix.",
            color: "#f59e0b"
        };
        if (G > 8.5) return {
            text: "Too tough",
            desc: "Overdeveloped gluten network: difficult to roll out, tendency to shrink. Typical of mixes with too much semolina. Extend the resting time.",
            color: "#f59e0b"
        };
        if (G < 3) return {
            text: "Weak structure",
            desc: "Insufficient elasticity, the sheet tears easily. Increase the semolina fraction in the mix.",
            color: "#f97316"
        };
        return {
            text: "Optimal range",
            desc: "Correct balance between extensibility and toughness. Rollable sheet, and sufficient roughness to hold the sauce if the mix contains at least ~20% semolina.",
            color: "#10b981"
        };
    }

    // ==== Chart ====
    function initChart() {
        const ctxChart = document.getElementById('tw-rheologyChart').getContext('2d');
        chartInstance = new Chart(ctxChart, {
            type: 'line',
            data: {
                labels: Array.from({ length: 31 }, (_, i) => i + 25),
                datasets: [
                    { label: "Elasticity", borderColor: '#4f46e5', backgroundColor: 'rgba(79,70,229,0.08)', borderWidth: 2, pointRadius: 0, tension: 0.4, yAxisID: 'y' },
                    { label: "Stickiness", borderColor: '#f43f5e', backgroundColor: 'rgba(244,63,94,0.08)', borderWidth: 2, pointRadius: 0, tension: 0.4, yAxisID: 'y' },
                    { label: "State (Elasticity)", type: 'scatter', data: [], backgroundColor: '#4f46e5', borderWidth: 0, pointRadius: 6, showLine: false, yAxisID: 'y' },
                    { label: "State (Stickiness)", type: 'scatter', data: [], backgroundColor: '#f43f5e', borderWidth: 0, pointRadius: 6, showLine: false, yAxisID: 'y' }
                ]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                interaction: { mode: 'index', intersect: false },
                scales: {
                    x: {
                        title: { display: true, text: 'Hydration (%)', color: 'gray', font: { size: 10 } },
                        grid: { color: 'rgba(128,128,128,0.15)' },
                        ticks: { color: 'gray', font: { size: 9 } }
                    },
                    y: {
                        type: 'linear',
                        title: { display: true, text: 'Value (0–10)', color: 'gray', font: { size: 10 } },
                        grid: { color: 'rgba(128,128,128,0.15)' },
                        ticks: { color: 'gray', font: { size: 9 } },
                        min: 0, max: 10
                    }
                },
                plugins: {
                    legend: { position: 'top', labels: { color: 'gray', font: { size: 10 }, boxWidth: 12, padding: 12 } },
                    tooltip: { enabled: false }
                }
            }
        });
    }

    function updateChart() {
        const dataG = [], dataSt = [];
        for (let h = 25; h <= 55; h++) {
            dataG.push(calcG(h, state.S, state.T));
            dataSt.push(calcSt(h, state.S, state.T));
        }
        chartInstance.data.datasets[0].data = dataG;
        chartInstance.data.datasets[1].data = dataSt;
        const xIdx = state.H - 25;
        chartInstance.data.datasets[2].data = [{ x: xIdx, y: state.G }];
        chartInstance.data.datasets[3].data = [{ x: xIdx, y: state.St }];
        chartInstance.update('none');
    }

    // ==== Canvas ====
    let nodes = [], waterDrops = [];

    function resizeCanvas() {
        const rect = canvas.parentElement.getBoundingClientRect();
        canvas.width = rect.width;
        canvas.height = rect.height;
        initNodes();
    }

    function initNodes() {
        nodes = [];
        const glutenCount = Math.floor(30 + state.S * 0.35);
        const semolaGranules = Math.floor(state.S * 0.25);
        const flour00Granules = Math.floor((100 - state.S) * 0.25);

        for (let i = 0; i < glutenCount; i++) {
            nodes.push({ x: Math.random() * canvas.width, y: Math.random() * canvas.height, vx: (Math.random() - 0.5) * 0.5, vy: (Math.random() - 0.5) * 0.5, type: 'gluten' });
        }
        for (let i = 0; i < semolaGranules; i++) {
            nodes.push({ x: Math.random() * canvas.width, y: Math.random() * canvas.height, vx: (Math.random() - 0.5) * 0.3, vy: (Math.random() - 0.5) * 0.3, type: 'semola', r: 4 + Math.random() * 2 });
        }
        for (let i = 0; i < flour00Granules; i++) {
            nodes.push({ x: Math.random() * canvas.width, y: Math.random() * canvas.height, vx: (Math.random() - 0.5) * 0.3, vy: (Math.random() - 0.5) * 0.3, type: 'starch00', r: 2 + Math.random() });
        }
        lastSemolaForNodes = state.S;
        initWaterDrops();
    }

    function initWaterDrops() {
        waterDrops = [];
        const count = Math.floor(state.St * 4);
        for (let i = 0; i < count; i++) {
            waterDrops.push({ x: Math.random() * canvas.width, y: Math.random() * canvas.height, vx: (Math.random() - 0.5) * 0.8, vy: (Math.random() - 0.5) * 0.8, r: 3 + Math.random() * 2 });
        }
    }

    function drawNetwork() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        const wetness = (state.H - 25) / 30;
        ctx.fillStyle = `rgba(128, 128, 128, ${wetness * 0.15})`;
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        let connectDist = 60;
        if (state.H < 30) connectDist = 35;
        else if (state.H > 40) connectDist = 90;

        const bondStrength = state.G / 10;
        ctx.lineWidth = Math.max(0.2, bondStrength * 2);

        for (let i = 0; i < nodes.length; i++) {
            if (nodes[i].type !== 'gluten') continue;
            for (let j = i + 1; j < nodes.length; j++) {
                if (nodes[j].type !== 'gluten') continue;
                const dx = nodes[i].x - nodes[j].x, dy = nodes[i].y - nodes[j].y;
                const dist = Math.sqrt(dx * dx + dy * dy);
                if (dist < connectDist) {
                    const alpha = (1 - dist / connectDist) * bondStrength;
                    ctx.strokeStyle = `rgba(136, 136, 136, ${alpha})`;
                    ctx.beginPath();
                    ctx.moveTo(nodes[i].x, nodes[i].y);
                    ctx.lineTo(nodes[j].x, nodes[j].y);
                    ctx.stroke();
                }
            }
        }

        nodes.forEach(n => {
            ctx.beginPath();
            if (n.type === 'gluten') { ctx.arc(n.x, n.y, 3, 0, Math.PI * 2); ctx.fillStyle = '#94a3b8'; }
            else if (n.type === 'semola') { ctx.arc(n.x, n.y, n.r, 0, Math.PI * 2); ctx.fillStyle = '#fcd34d'; }
            else { ctx.arc(n.x, n.y, n.r, 0, Math.PI * 2); ctx.fillStyle = '#e5e7eb'; }
            ctx.fill();

            const tempFactor = Math.max(0.1, state.T / 22);
            n.x += n.vx * (1 + wetness * 1.5) * tempFactor;
            n.y += n.vy * (1 + wetness * 1.5) * tempFactor;
            if (n.x < 0 || n.x > canvas.width) n.vx *= -1;
            if (n.y < 0 || n.y > canvas.height) n.vy *= -1;
        });

        const dropAlpha = Math.min(1, state.St / 6);
        waterDrops.forEach(d => {
            ctx.beginPath();
            ctx.arc(d.x, d.y, d.r, 0, Math.PI * 2);
            ctx.fillStyle = `rgba(56, 189, 248, ${dropAlpha})`;
            ctx.fill();
            d.x += d.vx; d.y += d.vy;
            if (d.x < 0 || d.x > canvas.width) d.vx *= -1;
            if (d.y < 0 || d.y > canvas.height) d.vy *= -1;
        });
    }

    function updateUI() {
        state.H = parseInt(hydrInput.value);
        state.S = parseInt(semolaInput.value);
        state.T = parseInt(tempInput.value);

        state.G = calcG(state.H, state.S, state.T);
        state.St = calcSt(state.H, state.S, state.T);
        state.R = calcR(state.S);

        hydrVal.textContent = state.H;
        semolaValEl.textContent = state.S;
        tempVal.textContent = state.T;

        gPrimeText.textContent = state.G.toFixed(1);
        stickinessText.textContent = state.St.toFixed(1);
        roughnessText.textContent = state.R.toFixed(1);

        const st = deriveStatus(state.H, state.S, state.T, state.G, state.St);
        statusText.textContent = st.text;
        statusDesc.textContent = st.desc;
        statusText.style.color = st.color;
        statusBox.style.borderColor = st.color + '40';
        statusBox.style.background = st.color + '15';

        updateChart();

        if (state.S !== lastSemolaForNodes) initNodes();
        const targetDrops = Math.floor(state.St * 4);
        while (waterDrops.length < targetDrops) {
            waterDrops.push({ x: Math.random() * canvas.width, y: Math.random() * canvas.height, vx: (Math.random() - 0.5) * 0.8, vy: (Math.random() - 0.5) * 0.8, r: 3 + Math.random() * 2 });
        }
        if (waterDrops.length > targetDrops) waterDrops.length = targetDrops;
    }

    function animate() {
        drawNetwork();
        requestAnimationFrame(animate);
    }

    hydrInput.addEventListener('input', updateUI);
    semolaInput.addEventListener('input', updateUI);
    tempInput.addEventListener('input', updateUI);
    window.addEventListener('resize', () => {
        const rect = canvas.parentElement.getBoundingClientRect();
        canvas.width = rect.width;
        canvas.height = rect.height;
    });

    function bootstrap() {
        if (typeof Chart === 'undefined') {
            setTimeout(bootstrap, 50);
            return;
        }
        initChart();
        resizeCanvas();
        updateUI();
        animate();
    }
    bootstrap();
})();
</script>

<!-- ==================== /RHEOLOGICAL SIMULATOR ==================== -->

## THE SALT

No salt in the dough. It goes in the cooking water. (Some traditional recipes have a bit of salt in the dough, but it's too little to have a negative effect and too little to make sense for taste.)

The proteins of the gluten network (gliadins and glutenins) have surface electrical charges that slightly repel each other in solution. Adding NaCl, Na⁺ and Cl⁻ ions arrange themselves around the proteins and shield these charges (**Debye effect**). Electrostatic repulsion is reduced. Result: a more structured and less extensible gluten network.

Fine for bread, not for dough to be rolled out.

Second problem: the osmotic gradient. During resting (which we will see in the procedure) the water redistributes by diffusion from the more hydrated areas to the less ones. Salt draws water by osmosis and interferes with diffusion. The dough arrives at the rolling pin more uneven.

I recover the flavor during cooking. Zero cost.

## PROCEDURE

Hard to think of a stand mixer: the dough hook would struggle to pick up powders and eggs well with small amounts of dough (for larger doughs I don't think there are problems, but I've never tried). Even robots like Thermomix wouldn't be good, they would raise the temperature too much. You could think of doing a first step at speed 5 or 6 for 20s, I think nothing more. The rest must be done by hand.

Hands stretch and fold the gluten network, aligning the protein bonds. This will be important later too.

The dough will seem very hard, it doesn't matter. The important thing is that it doesn't fall apart (if so, add a teaspoon of water) and isn't sticky.

Now, having obtained our dough, it must be rested for 30 min at room temperature tightly wrapped in cling film. The goal is for the dough to hydrate uniformly by diffusion: without cling film the water will evaporate forming a crust. For the same reason mentioned above, no salt: it would introduce an osmotic gradient that would compete with diffusion and make resting less effective.

Now let's roll out the pasta. I use a pasta machine. It guarantees an even thickness, avoiding raw and overcooked spots. Start from the thickest setting. Roll out the pasta, fold it and turn it 90 degrees 2 or 3 times. This allows a correct alignment of the gluten network. Then gradually move on to thinner cylinder sizes. Gradualness is important so as not to break the gluten network. A little semolina scattered here and there won't hurt. Letting the pasta sheet dry a little before making the tagliatelle decreases the probability that they will stick to the machine.

Bye.
