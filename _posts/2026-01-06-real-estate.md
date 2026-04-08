---
layout: post
title: "L'unico investimento sicuro (?)"
date: 2026-01-11 22:00:00 +0100
categories: [economia, coding]
tags: [immobiliare, inflazione, dataviz, javascript]
description: "Rompo il mattone."
pixel_icon: "mario.png"
smooth_image: true
---

Cerco di entrare in punta di piedi in questo argomento. In Italia, la proprietà immobiliare è quasi una religione. Un credo è dogmatico per definizione e analizzare i dogmi è uno degli obiettivi qui.
<br>
<br>
Non capisco quest'idea per la quale la casa sia una cosa fondamentale, un obiettivo di vita, perché con l'affitto si "regalano soldi". Ci sono mille risorse anche molto divulgative che smontano questo mito (ad esempio **Ben Felix** ha fatto vari [video](https://www.youtube.com/watch?v=lBG-g1CKfgs) e articoli a riguardo). Era una cosa abbastanza vera negli anni '80. Quel mondo non esiste più.
<br>
<br>
Allora ho voluto fare i conti con dati ufficiali alla mano e ne ho tirato fuori un tool interattivo.

### L'Osservatorio Interattivo

Qui sotto ho integrato lo script che ho scritto.
Il grafico mostra la differenza brutale tra il **Valore Nominale** (quello che leggi sull'assegno) e il **Valore Reale** (quello che conta davvero, pulito dall'inflazione).

<script src="https://cdn.jsdelivr.net/npm/chart.js@4.5.1/dist/chart.umd.min.js"
        integrity="sha384-jb8JQMbMoBUzgWatfe6COACi2ljcDdZQ2OxczGA3bGNeWe+6DChMTBJemed7ZnvJ"
        crossorigin="anonymous"></script>
<link rel="stylesheet" href="/assets/css/widgets.css">

<div id="chart-container-wrapper" class="not-prose my-8 bg-gray-900 text-gray-100 rounded-xl overflow-hidden shadow-2xl border border-gray-700 font-sans">
    
    <div class="p-6 md:p-8">
        <div class="text-center mb-6">
            <h3 class="text-2xl font-bold text-white mb-1">Simulatore Mercato</h3>
            <p class="text-gray-400 text-sm">Nominale vs Reale (Fonte dati: ISTAT)</p>
        </div>

        <div class="bg-gray-800 rounded-xl border border-gray-700 p-5 mb-6">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-5 items-end">
                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-gray-400 mb-2">Area Geografica</label>
                    <div class="relative text-gray-900">
                        <select id="areaSelect" class="w-full p-2 bg-gray-700 border border-gray-600 rounded text-white focus:ring-2 focus:ring-blue-500"></select>
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-gray-400 mb-2">Tipologia</label>
                    <div class="relative text-gray-900">
                        <select id="typeSelect" class="w-full p-2 bg-gray-700 border border-gray-600 rounded text-white focus:ring-2 focus:ring-blue-500">
                            <option value="Totale">Totale Abitazioni</option>
                            <option value="Nuove">Abitazioni Nuove</option>
                            <option value="Esistenti">Abitazioni Esistenti</option>
                        </select>
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-blue-400 mb-2">Anno Base</label>
                    <div class="relative text-gray-900">
                        <select id="baseYearSelect" class="w-full p-2 bg-gray-700 border border-blue-500/50 rounded text-white focus:ring-2 focus:ring-blue-500">
                            <option value="2010">2010 (Standard)</option>
                            <option value="2015">2015</option>
                            <option value="2020">2020 (Post-Covid)</option>
                            <option value="2023" selected>2023</option>
                        </select>
                    </div>
                </div>
            </div>
        </div>

        <div class="bg-gray-800 rounded-xl border border-gray-700 p-4 mb-6 relative" style="height: 350px;">
            <canvas id="myChart"></canvas>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
            <div class="bg-gray-800 p-4 rounded-lg border border-gray-700">
                <h4 class="font-bold text-blue-400 mb-1">Convergenza</h4>
                <p class="text-gray-400 text-xs" id="convergenceText">Loading...</p>
            </div>
            <div class="bg-gray-800 p-4 rounded-lg border border-gray-700">
                <h4 class="font-bold text-purple-400 mb-1">Trend</h4>
                <p class="text-gray-400 text-xs" id="trendText">Loading...</p>
            </div>
        </div>
    </div>
</div>

<script>
    // Configurazione Chart.js
    Chart.defaults.color = '#9ca3af'; 
    Chart.defaults.borderColor = '#374151';

    const rawData = [
        { anno: 2010, area: "Italia", tipo: "Totale", nominale: 100.0, reale: 100.0 }, { anno: 2011, area: "Italia", tipo: "Totale", nominale: 98.5, reale: 95.7 }, { anno: 2012, area: "Italia", tipo: "Totale", nominale: 94.2, reale: 88.3 }, { anno: 2013, area: "Italia", tipo: "Totale", nominale: 88.5, reale: 81.9 }, { anno: 2014, area: "Italia", tipo: "Totale", nominale: 84.6, reale: 77.2 }, { anno: 2015, area: "Italia", tipo: "Totale", nominale: 82.4, reale: 75.0 }, { anno: 2016, area: "Italia", tipo: "Totale", nominale: 81.7, reale: 74.4 }, { anno: 2017, area: "Italia", tipo: "Totale", nominale: 81.1, reale: 73.0 }, { anno: 2018, area: "Italia", tipo: "Totale", nominale: 80.6, reale: 71.7 }, { anno: 2019, area: "Italia", tipo: "Totale", nominale: 80.5, reale: 70.9 }, { anno: 2020, area: "Italia", tipo: "Totale", nominale: 82.0, reale: 72.1 }, { anno: 2021, area: "Italia", tipo: "Totale", nominale: 84.1, reale: 72.6 }, { anno: 2022, area: "Italia", tipo: "Totale", nominale: 87.3, reale: 69.8 }, { anno: 2023, area: "Italia", tipo: "Totale", nominale: 88.4, reale: 67.2 },
        { anno: 2010, area: "Italia", tipo: "Nuove", nominale: 100.0, reale: 100.0 }, { anno: 2012, area: "Italia", tipo: "Nuove", nominale: 98.5, reale: 92.3 }, { anno: 2015, area: "Italia", tipo: "Nuove", nominale: 98.0, reale: 89.1 }, { anno: 2018, area: "Italia", tipo: "Nuove", nominale: 99.5, reale: 88.5 }, { anno: 2020, area: "Italia", tipo: "Nuove", nominale: 103.2, reale: 90.7 }, { anno: 2021, area: "Italia", tipo: "Nuove", nominale: 108.5, reale: 93.7 }, { anno: 2022, area: "Italia", tipo: "Nuove", nominale: 115.3, reale: 92.1 }, { anno: 2023, area: "Italia", tipo: "Nuove", nominale: 120.5, reale: 91.6 },
        { anno: 2010, area: "Italia", tipo: "Esistenti", nominale: 100.0, reale: 100.0 }, { anno: 2012, area: "Italia", tipo: "Esistenti", nominale: 92.3, reale: 86.5 }, { anno: 2015, area: "Italia", tipo: "Esistenti", nominale: 76.2, reale: 69.3 }, { anno: 2018, area: "Italia", tipo: "Esistenti", nominale: 73.5, reale: 65.4 }, { anno: 2020, area: "Italia", tipo: "Esistenti", nominale: 74.5, reale: 65.5 }, { anno: 2022, area: "Italia", tipo: "Esistenti", nominale: 77.8, reale: 62.1 }, { anno: 2023, area: "Italia", tipo: "Esistenti", nominale: 77.5, reale: 58.9 },
        { anno: 2010, area: "Nord-ovest", tipo: "Totale", nominale: 100.0, reale: 100.0 }, { anno: 2012, area: "Nord-ovest", tipo: "Totale", nominale: 95.0, reale: 89.0 }, { anno: 2015, area: "Nord-ovest", tipo: "Totale", nominale: 83.5, reale: 76.0 }, { anno: 2020, area: "Nord-ovest", tipo: "Totale", nominale: 83.0, reale: 73.0 }, { anno: 2023, area: "Nord-ovest", tipo: "Totale", nominale: 90.5, reale: 68.8 },
        { anno: 2010, area: "Nord-ovest", tipo: "Nuove", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Nord-ovest", tipo: "Nuove", nominale: 95.0, reale: 86.4 }, { anno: 2023, area: "Nord-ovest", tipo: "Nuove", nominale: 108.0, reale: 82.1 }, { anno: 2010, area: "Nord-ovest", tipo: "Esistenti", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Nord-ovest", tipo: "Esistenti", nominale: 79.5, reale: 72.3 }, { anno: 2023, area: "Nord-ovest", tipo: "Esistenti", nominale: 86.0, reale: 65.4 },
        { anno: 2010, area: "Nord-est", tipo: "Totale", nominale: 100.0, reale: 100.0 }, { anno: 2012, area: "Nord-est", tipo: "Totale", nominale: 94.0, reale: 88.1 }, { anno: 2015, area: "Nord-est", tipo: "Totale", nominale: 80.0, reale: 72.8 }, { anno: 2020, area: "Nord-est", tipo: "Totale", nominale: 84.5, reale: 74.3 }, { anno: 2023, area: "Nord-est", tipo: "Totale", nominale: 95.0, reale: 72.2 },
        { anno: 2010, area: "Nord-est", tipo: "Nuove", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Nord-est", tipo: "Nuove", nominale: 94.0, reale: 85.5 }, { anno: 2023, area: "Nord-est", tipo: "Nuove", nominale: 112.0, reale: 85.1 }, { anno: 2010, area: "Nord-est", tipo: "Esistenti", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Nord-est", tipo: "Esistenti", nominale: 76.0, reale: 69.1 }, { anno: 2023, area: "Nord-est", tipo: "Esistenti", nominale: 90.0, reale: 68.4 },
        { anno: 2010, area: "Centro", tipo: "Totale", nominale: 100.0, reale: 100.0 }, { anno: 2012, area: "Centro", tipo: "Totale", nominale: 94.0, reale: 88.1 }, { anno: 2015, area: "Centro", tipo: "Totale", nominale: 80.0, reale: 72.8 }, { anno: 2020, area: "Centro", tipo: "Totale", nominale: 75.5, reale: 66.4 }, { anno: 2023, area: "Centro", tipo: "Totale", nominale: 78.0, reale: 59.3 },
        { anno: 2010, area: "Centro", tipo: "Nuove", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Centro", tipo: "Nuove", nominale: 96.0, reale: 87.3 }, { anno: 2023, area: "Centro", tipo: "Nuove", nominale: 102.0, reale: 77.5 }, { anno: 2010, area: "Centro", tipo: "Esistenti", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Centro", tipo: "Esistenti", nominale: 75.0, reale: 68.2 }, { anno: 2023, area: "Centro", tipo: "Esistenti", nominale: 72.0, reale: 54.7 },
        { anno: 2010, area: "Mezzogiorno", tipo: "Totale", nominale: 100.0, reale: 100.0 }, { anno: 2012, area: "Mezzogiorno", tipo: "Totale", nominale: 93.0, reale: 87.1 }, { anno: 2015, area: "Mezzogiorno", tipo: "Totale", nominale: 78.5, reale: 71.5 }, { anno: 2020, area: "Mezzogiorno", tipo: "Totale", nominale: 74.0, reale: 65.1 }, { anno: 2023, area: "Mezzogiorno", tipo: "Totale", nominale: 79.0, reale: 60.1 },
        { anno: 2010, area: "Mezzogiorno", tipo: "Nuove", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Mezzogiorno", tipo: "Nuove", nominale: 92.0, reale: 83.7 }, { anno: 2023, area: "Mezzogiorno", tipo: "Nuove", nominale: 98.0, reale: 74.5 }, { anno: 2010, area: "Mezzogiorno", tipo: "Esistenti", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Mezzogiorno", tipo: "Esistenti", nominale: 74.0, reale: 67.3 }, { anno: 2023, area: "Mezzogiorno", tipo: "Esistenti", nominale: 74.0, reale: 56.2 },
        { anno: 2010, area: "Milano", tipo: "Totale", nominale: 100.0, reale: 100.0 }, { anno: 2011, area: "Milano", tipo: "Totale", nominale: 100.8, reale: 97.5 }, { anno: 2012, area: "Milano", tipo: "Totale", nominale: 95.5, reale: 89.0 }, { anno: 2013, area: "Milano", tipo: "Totale", nominale: 92.0, reale: 84.5 }, { anno: 2014, area: "Milano", tipo: "Totale", nominale: 88.5, reale: 80.0 }, { anno: 2015, area: "Milano", tipo: "Totale", nominale: 85.5, reale: 77.8 }, { anno: 2016, area: "Milano", tipo: "Totale", nominale: 87.2, reale: 79.0 }, { anno: 2017, area: "Milano", tipo: "Totale", nominale: 89.5, reale: 80.5 }, { anno: 2018, area: "Milano", tipo: "Totale", nominale: 96.0, reale: 85.4 }, { anno: 2019, area: "Milano", tipo: "Totale", nominale: 102.5, reale: 90.1 }, { anno: 2020, area: "Milano", tipo: "Totale", nominale: 108.0, reale: 95.0 }, { anno: 2021, area: "Milano", tipo: "Totale", nominale: 114.5, reale: 98.9 }, { anno: 2022, area: "Milano", tipo: "Totale", nominale: 122.0, reale: 97.5 }, { anno: 2023, area: "Milano", tipo: "Totale", nominale: 125.8, reale: 95.6 },
        { anno: 2010, area: "Milano", tipo: "Nuove", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Milano", tipo: "Nuove", nominale: 95.0, reale: 86.4 }, { anno: 2018, area: "Milano", tipo: "Nuove", nominale: 105.0, reale: 93.4 }, { anno: 2020, area: "Milano", tipo: "Nuove", nominale: 118.0, reale: 103.8 }, { anno: 2022, area: "Milano", tipo: "Nuove", nominale: 135.0, reale: 107.9 }, { anno: 2023, area: "Milano", tipo: "Nuove", nominale: 142.0, reale: 108.0 },
        { anno: 2010, area: "Milano", tipo: "Esistenti", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Milano", tipo: "Esistenti", nominale: 82.0, reale: 74.6 }, { anno: 2018, area: "Milano", tipo: "Esistenti", nominale: 92.0, reale: 81.8 }, { anno: 2020, area: "Milano", tipo: "Esistenti", nominale: 103.0, reale: 90.6 }, { anno: 2022, area: "Milano", tipo: "Esistenti", nominale: 115.0, reale: 91.9 }, { anno: 2023, area: "Milano", tipo: "Esistenti", nominale: 118.0, reale: 89.7 },
        { anno: 2010, area: "Roma", tipo: "Totale", nominale: 100.0, reale: 100.0 }, { anno: 2012, area: "Roma", tipo: "Totale", nominale: 93.5, reale: 87.0 }, { anno: 2015, area: "Roma", tipo: "Totale", nominale: 82.1, reale: 74.7 }, { anno: 2018, area: "Roma", tipo: "Totale", nominale: 77.0, reale: 68.5 }, { anno: 2020, area: "Roma", tipo: "Totale", nominale: 76.5, reale: 67.3 }, { anno: 2021, area: "Roma", tipo: "Totale", nominale: 77.0, reale: 66.5 }, { anno: 2022, area: "Roma", tipo: "Totale", nominale: 78.2, reale: 62.5 }, { anno: 2023, area: "Roma", tipo: "Totale", nominale: 77.5, reale: 58.9 },
        { anno: 2010, area: "Roma", tipo: "Nuove", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Roma", tipo: "Nuove", nominale: 90.0, reale: 81.8 }, { anno: 2023, area: "Roma", tipo: "Nuove", nominale: 95.0, reale: 72.2 }, { anno: 2010, area: "Roma", tipo: "Esistenti", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Roma", tipo: "Esistenti", nominale: 79.0, reale: 71.9 }, { anno: 2023, area: "Roma", tipo: "Esistenti", nominale: 74.0, reale: 56.2 },
        { anno: 2010, area: "Torino", tipo: "Totale", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Torino", tipo: "Totale", nominale: 80.5, reale: 73.0 }, { anno: 2020, area: "Torino", tipo: "Totale", nominale: 79.0, reale: 69.5 }, { anno: 2023, area: "Torino", tipo: "Totale", nominale: 85.0, reale: 64.6 },
        { anno: 2010, area: "Torino", tipo: "Nuove", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Torino", tipo: "Nuove", nominale: 90.0, reale: 81.8 }, { anno: 2023, area: "Torino", tipo: "Nuove", nominale: 105.0, reale: 79.8 }, { anno: 2010, area: "Torino", tipo: "Esistenti", nominale: 100.0, reale: 100.0 }, { anno: 2015, area: "Torino", tipo: "Esistenti", nominale: 78.0, reale: 70.9 }, { anno: 2023, area: "Torino", tipo: "Esistenti", nominale: 80.0, reale: 60.8 },
    ];

    let myChart = null;
    
    // Inizializza non appena il DOM è pronto (o subito se iniettato post-caricamento)
    if (document.readyState === 'loading') {
        document.addEventListener('DOMContentLoaded', initApp);
    } else {
        initApp();
    }

    function initApp() {
        const areaSelect = document.getElementById('areaSelect');
        const typeSelect = document.getElementById('typeSelect');
        const baseYearSelect = document.getElementById('baseYearSelect');
        if(!areaSelect) return; 

        // Popola menu aree
        const areas = [...new Set(rawData.map(item => item.area))];
        areaSelect.innerHTML = '';
        areas.forEach(area => {
            const option = document.createElement('option');
            option.value = area; option.text = area;
            if (area === "Italia") option.selected = true; 
            areaSelect.appendChild(option);
        });

        areaSelect.addEventListener('change', updateChart);
        typeSelect.addEventListener('change', updateChart);
        baseYearSelect.addEventListener('change', updateChart);
        updateChart();
    }

    function rebaseData(dataArray, baseYear) {
        const baseRecord = dataArray.find(d => d.anno == baseYear);
        if (!baseRecord) return dataArray;
        const baseNominal = baseRecord.nominale; const baseReal = baseRecord.reale;
        return dataArray.map(d => ({
            anno: d.anno, area: d.area, tipo: d.tipo,
            nominale: (d.nominale / baseNominal) * 100, reale: (d.reale / baseReal) * 100
        }));
    }

    function updateChart() {
        const areaSelect = document.getElementById('areaSelect');
        const typeSelect = document.getElementById('typeSelect');
        const baseYearSelect = document.getElementById('baseYearSelect');
        
        const selectedArea = areaSelect.value;
        const selectedType = typeSelect.value;
        const selectedBaseYear = parseInt(baseYearSelect.value);

        let filteredData = rawData.filter(d => d.area === selectedArea && d.tipo === selectedType);
        filteredData.sort((a, b) => a.anno - b.anno);

        if (filteredData.length === 0) {
            if(myChart) { myChart.destroy(); myChart = null; }
            document.getElementById('trendText').innerText = "Dati non disponibili.";
            return;
        }

        const rebasedData = rebaseData(filteredData, selectedBaseYear);
        const labels = rebasedData.map(d => d.anno);
        const nominalData = rebasedData.map(d => d.nominale);
        const realData = rebasedData.map(d => d.reale);

        document.getElementById('trendText').innerHTML = `Inflazione cumulativa visibile come gap tra le linee a partire dal ${selectedBaseYear}.`;
        document.getElementById('convergenceText').innerHTML = `Anno base: ${selectedBaseYear}. Punto di contatto forzato a 100.`;

        const ctx = document.getElementById('myChart');
        const context = ctx.getContext('2d');
        if (myChart) myChart.destroy();

        myChart = new Chart(context, {
            type: 'line',
            data: {
                labels: labels,
                datasets: [
                    {
                        label: `Nominale`,
                        data: nominalData,
                        borderColor: '#3b82f6', backgroundColor: 'rgba(59, 130, 246, 0.2)', borderWidth: 3,
                        pointBackgroundColor: '#1f2937', tension: 0.3, fill: false
                    },
                    {
                        label: `Reale`,
                        data: realData,
                        borderColor: '#ef4444', backgroundColor: 'rgba(239, 68, 68, 0.2)', borderWidth: 3, borderDash: [5, 5],
                        pointBackgroundColor: '#1f2937', tension: 0.3, fill: false
                    }
                ]
            },
            options: {
                responsive: true, maintainAspectRatio: false,
                plugins: { legend: { display: false }, tooltip: { mode: 'index', intersect: false } },
                scales: { x: { ticks: { color: '#9ca3af' }, grid: { color: '#374151' } }, y: { ticks: { color: '#9ca3af' }, grid: { color: '#374151' } } },
                interaction: { mode: 'nearest', axis: 'x', intersect: false }
            }
        });
    }
// --- FUNZIONE PER I BOTTONI NEL TESTO ---
    window.setChartParams = function(area, year) {
        const areaSelect = document.getElementById('areaSelect');
        const yearSelect = document.getElementById('baseYearSelect');
        
        // 1. Cambia i valori delle select (se passati)
        if (area) areaSelect.value = area;
        if (year) yearSelect.value = year;

        // 2. Simula l'evento "change" per far scattare l'aggiornamento del grafico
        areaSelect.dispatchEvent(new Event('change'));

        // 3. (Opzionale) Scorre la pagina dolcemente fino al grafico per farlo vedere
        document.getElementById('chart-container-wrapper').scrollIntoView({ 
            behavior: 'smooth', 
            block: 'center' 
        });
    };
</script>
### Come leggere i dati

1.  **La Linea Blu (Valore Nominale):** È il prezzo "da vetrina". È la cifra che scrivi sull'assegno. Se hai comprato casa nel 2010 a 200.000€ e oggi vale 210.000€, la linea blu ti dice che hai guadagnato. Evviva!
2.  **La Linea Rossa (Valore Reale):** Questa è la linea che conta davvero. È il valore della casa depurato dall'inflazione.
<br>
<br>
Vediamo un numero più alto e pensiamo di essere ricchi. Ma se nel frattempo il costo del pane, della benzina e delle bollette è raddoppiato...
<br>
<br>
In molte zone d'Italia, il valore reale degli immobili è **crollato di oltre 20-30 punti percentuali** rispetto al 2010. Significa che, in termini di potere d'acquisto, chi ha tenuto i soldi "nel mattone" è diventato più povero, non più ricco.
<br>
<br>
### "Eh, ma Milano..."
<button onclick="setChartParams('Milano', '2023')" class="inline-flex items-center px-2 py-1 border border-transparent text-xs font-medium rounded shadow-sm text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 ml-2 transition-all">
    👉 Vedi grafico Milano
</button>
<br>
Se guardiamo il grafico su Milano, la linea blu schizza verso l'alto. Chi ha comprato ha fatto un affare, giusto? Sì, ma molto meno di quanto sembri. Anche nel mercato più caldo d'Italia, l'inflazione (specialmente quella post-2021) ha "mangiato" una fetta enorme di quel profitto. Il guadagno *reale* è drasticamente inferiore al guadagno *nominale* che si legge sui giornali.
<br>
<br>
Senza considerare che un investimento si vede almeno a vent'anni di distanza. Come si fa a prevedere il mercato immobiliare di un posto, anzi di un quartiere, a vent'anni di distanza?
<br>
<br>
E se usciamo da Milano e guardiamo a Roma o al Sud? La situazione è drammatica: prezzi nominali fermi o in calo e prezzi reali che sprofondano.
<button onclick="setChartParams('Roma', '2023')" class="inline-flex items-center px-2 py-1 border border-transparent text-xs font-medium rounded shadow-sm text-white bg-red-600 hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 ml-2 transition-all">
    📉 Vedi Roma
</button>
<br>
<br>
---

### Conclusioni

Non sto dicendo che non si debba comprare casa o che non ci siano situazioni, di portafoglio o di vita, in cui sia economicamente sensato. Avere un tetto sopra la testa è una sicurezza emotiva e una bella comodità, ma non è automaticamente un "grande investimento". Anzi, *imho* non è proprio da considerarsi come un investimento: **è una spesa**.
<br>
<br>
La prossima volta che qualcuno vi dice "Ho venduto casa allo stesso prezzo a cui l'ho comprata 10 anni fa, almeno non ci ho perso niente", fategli vedere la linea rossa. In realtà, l'inflazione si è mangiata un quarto dei suoi risparmi senza che se ne accorgesse. Questo senza considerare le tasse e la perdita di valore dell'immobile nel tempo (dopo 30 anni, lo vogliamo rifare questo tetto?).
<br>
<br>
_Poi ci sarebbero altre mille considerazioni da fare: l'utilità delle serie storiche per la previsione del futuro, l'idea di legarsi mani e piedi ad un solo asset..._

#### Fonti
* **Prezzi delle Abitazioni (IPAB):** Dati ISTAT relativi all'Indice dei prezzi delle abitazioni acquistate dalle famiglie.
* **Inflazione:** Dati ISTAT relativi all'Indice nazionale dei prezzi al consumo (NIC).