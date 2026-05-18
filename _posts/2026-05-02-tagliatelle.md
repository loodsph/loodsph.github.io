---
layout: post
title: "La scienza della tagliatella"
seo_title: "La scienza della tagliatella: reologia e chimica dell'impasto perfetto"
date: 2026-05-18
categories: [cucina, scienza]
tags: [reologia, pasta, glutine, chimica-applicata]
description: "Reologia e termodinamica per ottenere l'impasto e la rugosità perfetta."
pixel_icon: "tagliatelle.png"
smooth_image: true
lang: it
ref: tagliatelle
---

Come credo si sia capito: mi piace cucinare. Perché? Potrei fare tutto un discorso sulla cucina come chimica applicata, ma la realtà è che mi piace mangiare. *That's it.*

---
<br>
<img src="/assets/tagliatelle.jpeg" alt="Tagliatelle" style="border-radius: 16px; width: 100%;" />

---

## INGREDIENTI E DOSI

Uova e farina.

L'obiettivo è una tagliatella che:

**Sia lavorabile.** Qui è l'idratazione a comandare. Troppa acqua e l'impasto sarà peggio di uno slime, poca e sarà una sabbia impossibile da impastare. Anche la temperatura è fondamentale in questa fase. L'impasto deve essere abbastanza caldo da essere plastico, ma non troppo da aumentare la mobilità della gliadina e il rilassamento del glutine (diventa appiccicoso e scivola via).

**Non sia un mattone, ma che non si sfaldi (masticabile).** Per questo bisogna controllare la forza (W) della farina. Non è proprio corretto, ma possiamo grossolanamente fare un'equivalenza tra il contenuto di proteine e la forza della farina. La farina di semola ha un rapporto gliadina/glutenina che la rende più tenace, darebbe la giusta consistenza, ma è difficilissima da lavorare. Una farina 00 sarebbe una buona soluzione, ma ha altre criticità. (La tradizione emiliana dovrebbe essere con sola farina 00 o farina 0, ma si è capito che non sono appassionato di tradizioni, ma di logica.)

**Abbia una buona rugosità.** La tagliatella deve essere abbastanza rugosa da trattenere il sugo. Anche qui la farina di semola sarebbe l'ideale. La farina 00 da sola ha una texture troppo liscia.

Da qui si è capito che l'ideale è un mix di farine. Da ragionamenti sulla reologia ho empiricamente trovato che un **70% di farina 00 e 30% di semola** sia un buon mix. Giusta forza totale della farina e buona rugosità.

Ora le uova: mediamente un uovo (50 g) ha il 75% di peso in acqua. L'idratazione ideale è intorno al 30-35%. Quindi basta fare il peso delle uova × 2 e abbiamo il peso del mix di farina da aggiungere.

<details markdown="1">
  <summary>Nerdate un po' chimiche</summary>
Le farine commerciali hanno un'umidità residua fisiologica (circa il 12-14%). Su 100 g di farina (mix), ci sono già circa 13 g di acqua. Aggiungendo un uovo medio da 50 g (costituito al 75% da acqua), inseriamo altri 37,5 g di liquidi. Arriviamo a un totale di circa 50,5 g di acqua su 150 g di massa complessiva. Questo genera un'idratazione assoluta del **33,6%**, posizionando il sistema esattamente al centro del range ottimale.
</details>

<!-- ==================== SIMULATORE REOLOGICO ==================== -->

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
    content: 'ottimale';
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
        <h3>Simulatore Reologico dell'Impasto</h3>
        <p>Analisi visco-elastica per pasta fresca all'uovo</p>
    </div>

    <div class="ts-body">
        <div class="ts-controls">
            <div class="ts-panel">
                <div class="ts-panel-title">Parametri Fisici</div>

                <div class="ts-field">
                    <label>Idratazione · <span class="ts-val" id="tw-hydration-val">33</span><span class="ts-unit">%</span></label>
                    <input type="range" id="tw-hydration" min="25" max="55" value="33" step="1">
                    <div class="ts-range-labels"><span>25% Secco</span><span>55% Liquido</span></div>
                </div>

                <div class="ts-field">
                    <label>Mix Farine (% Semola) · <span class="ts-val" id="tw-semola-val">30</span><span class="ts-unit">%</span></label>
                    <div class="ts-sweet-spot" style="margin-left: 30%;"></div>
                    <input type="range" id="tw-semola" min="0" max="100" value="30" step="5">
                    <div class="ts-range-labels"><span>0% solo 00</span><span>100% semola</span></div>
                </div>

                <div class="ts-field">
                    <label>Temperatura · <span class="ts-val" id="tw-temperature-val">22</span><span class="ts-unit">°C</span></label>
                    <input type="range" id="tw-temperature" min="4" max="40" value="22" step="1">
                    <div class="ts-range-labels"><span>4°C Frigo</span><span>40°C Caldo</span></div>
                </div>
            </div>

            <div class="ts-panel">
                <div class="ts-panel-title">Analisi Meccanica</div>

                <div class="ts-status" id="tw-status-box" style="background: #10b98115; border-color: #10b98140;">
                    <div class="ts-status-label">Stato Lavorabilità</div>
                    <div class="ts-status-text" id="tw-status-text" style="color: #10b981;">Range ottimale</div>
                    <div class="ts-status-desc" id="tw-status-desc">Bilanciamento corretto tra estensibilità e tenacità.</div>
                </div>

                <div class="ts-metrics">
                    <div class="ts-metric">
                        <span class="ts-metric-label">Elasticità</span>
                        <span class="ts-metric-val" id="tw-g-prime-val" style="color:#4f46e5;">5.0</span><span class="ts-metric-unit">/10</span>
                    </div>
                    <div class="ts-metric">
                        <span class="ts-metric-label">Adesività</span>
                        <span class="ts-metric-val" id="tw-stickiness-val" style="color:#f43f5e;">1.8</span><span class="ts-metric-unit">/10</span>
                    </div>
                    <div class="ts-metric">
                        <span class="ts-metric-label">Rugosità</span>
                        <span class="ts-metric-val" id="tw-roughness-val" style="color:#eab308;">3.7</span><span class="ts-metric-unit">/10</span>
                    </div>
                </div>
            </div>
        </div>

        <div class="ts-viz">
            <div class="ts-panel">
                <div class="ts-panel-title">Curve Reologiche</div>
                <div class="ts-chart-wrap">
                    <canvas id="tw-rheologyChart"></canvas>
                </div>
                <div class="ts-panel-footer">Curve calcolate al mix e temperatura attuali. I cerchi indicano lo stato corrente.</div>
            </div>

            <div class="ts-panel">
                <div class="ts-panel-title">Visione Microscopica — Maglia Glutinica & Granuli</div>
                <div class="ts-microscope-wrap">
                    <canvas id="tw-microscopeCanvas" style="position:absolute;top:0;left:0;width:100%;height:100%;"></canvas>
                    <div class="ts-legend">
                        <div><span class="ts-legend-dot" style="background:#94a3b8;"></span>glutine</div>
                        <div><span class="ts-legend-dot" style="background:#fcd34d;"></span>semola</div>
                        <div><span class="ts-legend-dot" style="background:#e5e7eb; border: 1px solid #d1d5db;"></span>amido 00</div>
                    </div>
                    <div class="ts-microscope-label">simulazione qualitativa</div>
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

    // ==== Modello fisico ====
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
            text: "Caldo eccessivo",
            desc: "La gliadina diventa più mobile e il glutine si rilassa: l'impasto si fa appiccicoso e perde tenacità. Non c'è denaturazione (succede sopra i 60°C), solo plasticizzazione eccessiva. Raffreddare prima di lavorare.",
            color: "#ef4444"
        };
        if (T < 14) return {
            text: "Troppo freddo",
            desc: "Glutine poco estensibile, impasto rigido. La sfoglia si straccerà durante la laminazione. Lasciare acclimatare a temperatura ambiente.",
            color: "#0ea5e9"
        };
        if (H < 30) return {
            text: "Sotto-idratato",
            desc: "Acqua insufficiente per sviluppare la maglia glutinica. Impasto farinoso, non coeso. Aggiungere liquido un cucchiaino alla volta.",
            color: "#f97316"
        };
        if (St > 6.5) return {
            text: "Adesività critica",
            desc: "Impasto colloso, strutturalmente collassato. Inlaminabile senza abbondante spolvero di semola, probabilmente non recuperabile a macchina.",
            color: "#ef4444"
        };
        if (St > 4.5) return {
            text: "Rischio adesività",
            desc: "Gestibile, ma richiede spolvero generoso e attenzione ai rulli. Considerare meno acqua o più semola nel mix.",
            color: "#f59e0b"
        };
        if (G > 8.5) return {
            text: "Troppo tenace",
            desc: "Maglia glutinica eccessivamente sviluppata: difficile da stendere, tendenza al ritiro. Tipico di mix con troppa semola. Allungare il riposo.",
            color: "#f59e0b"
        };
        if (G < 3) return {
            text: "Struttura debole",
            desc: "Elasticità insufficiente, la sfoglia si lacera facilmente. Aumentare la frazione di semola nel mix.",
            color: "#f97316"
        };
        return {
            text: "Range ottimale",
            desc: "Bilanciamento corretto tra estensibilità e tenacità. Sfoglia laminabile, e rugosità sufficiente per trattenere il sugo se il mix contiene almeno ~20% di semola.",
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
                    { label: "Elasticità", borderColor: '#4f46e5', backgroundColor: 'rgba(79,70,229,0.08)', borderWidth: 2, pointRadius: 0, tension: 0.4, yAxisID: 'y' },
                    { label: "Adesività", borderColor: '#f43f5e', backgroundColor: 'rgba(244,63,94,0.08)', borderWidth: 2, pointRadius: 0, tension: 0.4, yAxisID: 'y' },
                    { label: "Stato (Elasticità)", type: 'scatter', data: [], backgroundColor: '#4f46e5', borderWidth: 0, pointRadius: 6, showLine: false, yAxisID: 'y' },
                    { label: "Stato (Adesività)", type: 'scatter', data: [], backgroundColor: '#f43f5e', borderWidth: 0, pointRadius: 6, showLine: false, yAxisID: 'y' }
                ]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                interaction: { mode: 'index', intersect: false },
                scales: {
                    x: {
                        title: { display: true, text: 'Idratazione (%)', color: 'gray', font: { size: 10 } },
                        grid: { color: 'rgba(128,128,128,0.15)' },
                        ticks: { color: 'gray', font: { size: 9 } }
                    },
                    y: {
                        type: 'linear',
                        title: { display: true, text: 'Valore (0–10)', color: 'gray', font: { size: 10 } },
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

<!-- ==================== /SIMULATORE REOLOGICO ==================== -->

## IL SALE

Niente sale nell'impasto. Va nell'acqua di cottura. (In alcune ricette tradizionali un po' di sale nell'impasto c'è, ma è troppo poco per avere un effetto negativo e troppo poco per avere senso nel gusto.)

Le proteine del reticolo glutinico (gliadine e glutenine) hanno cariche elettriche superficiali che in soluzione si respingono leggermente. Aggiungendo NaCl, gli ioni Na⁺ e Cl⁻ si dispongono attorno alle proteine e schermano queste cariche (**effetto Debye**). La repulsione elettrostatica si riduce. Risultato: maglia glutinica più strutturata e meno estensibile.

Va bene per il pane, per una sfoglia da laminare no.

Secondo problema: il gradiente osmotico. Durante il riposo (che vedremo nel procedimento) l'acqua si redistribuisce per diffusione dalle zone più idratate a quelle meno. Il sale richiama acqua per osmosi e interferisce con la diffusione. La sfoglia arriva al matterello più disuniforme.

Il sapore lo recupero in cottura. Costo zero.

## PROCEDIMENTO

Difficile pensare a una planetaria: il gancio farebbe fatica a prelevare bene polveri e uova con quantitativi piccoli di impasto (per impasti più abbondanti non credo ci siano problemi, ma non ho mai provato). Anche robot tipo bimby non andrebbero bene, alzerebbe troppo la temperatura. Si può pensare di fare un primo passaggio a vel 5 o 6 per 20s, non credo nulla di più. Il resto va fatto a mano.

Le mani stirano e ripiegano la maglia glutinica allineando i legami proteici. Questa cosa risulterà importante anche dopo.

L'impasto sembrerà molto duro, non importa. L'importante è che non si sfaldi (nel caso aggiungere un cucchiaino d'acqua) e non sia colloso.

Ora, ottenuto il nostro impasto, va fatto riposare per 30 min a temperatura ambiente avvolto bene con la pellicola. Lo scopo è che l'impasto si idrati uniformemente per diffusione: senza pellicola l'acqua evaporerà formando una crosta. Per lo stesso motivo accennato sopra, niente sale: introdurrebbe un gradiente osmotico che competerebbe con la diffusione e renderebbe il riposo meno efficace.

Ora andiamo a tirare la pasta. Io uso un macchinario per tirare la pasta. Garantisce uno spessore omogeneo, evitando punti crudi e punti stracotti. Si parte dalla misura più spessa. Si tira la pasta, si piega e si gira di 90 gradi 2 o 3 volte. Questo permette un corretto allineamento della rete glutinica. Poi si passa via via alla misura dei cilindri più sottili. La gradualità è importante per non spezzare la rete glutinica. Un po' di semola sparsa qua e là non farà male. Lasciare asciugare un po' la sfoglia prima di fare le tagliatelle diminuisce la probabilità che si attacchino alla macchina.

Ciao.
