---
layout: post
title: "The only safe investment (?)"
seo_title: "Investing in real estate: is buying a house worth it? ISTAT data analysis"
date: 2026-01-11 22:00:00 +0100
categories: [economia, coding]
tags: [immobiliare, inflazione, dataviz, javascript]
description: "I'm demolishing the property myth."
pixel_icon: "mario.png"
smooth_image: true
lang: en
ref: real-estate
---

I'll try to tread carefully on this topic. In Italy, property ownership is almost a religion. A creed is dogmatic by definition, and analysing dogmas is one of the objectives here.
<br>
<br>
I don't understand this idea that a house is a fundamental thing, a life goal, because with renting you're "throwing money away." There are a thousand resources, even quite accessible ones, that debunk this myth (for example **Ben Felix** has made various [videos](https://www.youtube.com/watch?v=lBG-g1CKfgs) and articles on the subject). It was pretty true in the '80s. That world no longer exists.
<br>
<br>
So I wanted to run the numbers with official data in hand and built an interactive tool out of it.

### The Interactive Observatory

Below I've embedded the script I wrote.
The chart shows the brutal difference between **Nominal Value** (what you read on the cheque) and **Real Value** (what actually matters, stripped of inflation).

<script src="https://cdn.jsdelivr.net/npm/chart.js@4.5.1/dist/chart.umd.min.js"
        integrity="sha384-jb8JQMbMoBUzgWatfe6COACi2ljcDdZQ2OxczGA3bGNeWe+6DChMTBJemed7ZnvJ"
        crossorigin="anonymous"></script>
<link rel="stylesheet" href="/assets/css/widgets.css">

<div id="chart-container-wrapper" class="not-prose my-8 bg-gray-900 text-gray-100 rounded-xl overflow-hidden shadow-2xl border border-gray-700 font-sans">
    
    <div class="p-6 md:p-8">
        <div class="text-center mb-6">
            <h3 class="text-2xl font-bold text-white mb-1">Market Simulator</h3>
            <p class="text-gray-400 text-sm">Nominal vs Real (Data source: ISTAT)</p>
        </div>

        <div class="bg-gray-800 rounded-xl border border-gray-700 p-5 mb-6">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-5 items-end">
                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-gray-400 mb-2">Geographic Area</label>
                    <div class="relative text-gray-900">
                        <select id="areaSelect" class="w-full p-2 bg-gray-700 border border-gray-600 rounded text-white focus:ring-2 focus:ring-blue-500"></select>
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-gray-400 mb-2">Type</label>
                    <div class="relative text-gray-900">
                        <select id="typeSelect" class="w-full p-2 bg-gray-700 border border-gray-600 rounded text-white focus:ring-2 focus:ring-blue-500">
                            <option value="Totale">Total Dwellings</option>
                            <option value="Nuove">New Dwellings</option>
                            <option value="Esistenti">Existing Dwellings</option>
                        </select>
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-blue-400 mb-2">Base Year</label>
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
                <h4 class="font-bold text-blue-400 mb-1">Convergence</h4>
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
    // Chart.js configuration
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
            document.getElementById('trendText').innerText = "Data not available.";
            return;
        }

        const rebasedData = rebaseData(filteredData, selectedBaseYear);
        const labels = rebasedData.map(d => d.anno);
        const nominalData = rebasedData.map(d => d.nominale);
        const realData = rebasedData.map(d => d.reale);

        document.getElementById('trendText').innerHTML = `Cumulative inflation visible as gap between the lines starting from ${selectedBaseYear}.`;
        document.getElementById('convergenceText').innerHTML = `Base year: ${selectedBaseYear}. Forced contact point at 100.`;

        const ctx = document.getElementById('myChart');
        const context = ctx.getContext('2d');
        if (myChart) myChart.destroy();

        myChart = new Chart(context, {
            type: 'line',
            data: {
                labels: labels,
                datasets: [
                    {
                        label: `Nominal`,
                        data: nominalData,
                        borderColor: '#3b82f6', backgroundColor: 'rgba(59, 130, 246, 0.2)', borderWidth: 3,
                        pointBackgroundColor: '#1f2937', tension: 0.3, fill: false
                    },
                    {
                        label: `Real`,
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
    window.setChartParams = function(area, year) {
        const areaSelect = document.getElementById('areaSelect');
        const yearSelect = document.getElementById('baseYearSelect');
        
        if (area) areaSelect.value = area;
        if (year) yearSelect.value = year;

        areaSelect.dispatchEvent(new Event('change'));

        document.getElementById('chart-container-wrapper').scrollIntoView({ 
            behavior: 'smooth', 
            block: 'center' 
        });
    };
</script>
### How to read the data

1.  **The Blue Line (Nominal Value):** It's the "sticker price." It's the figure you write on the cheque. If you bought a house in 2010 for €200,000 and today it's worth €210,000, the blue line tells you that you've made a profit. Hooray!
2.  **The Red Line (Real Value):** This is the line that really matters. It's the value of the house stripped of inflation.
<br>
<br>
We see a higher number and think we're rich. But if in the meantime the cost of bread, petrol, and utility bills has doubled...
<br>
<br>
In many parts of Italy, the real value of property has **dropped by more than 20–30 percentage points** compared to 2010. This means that, in terms of purchasing power, those who kept their money "in bricks and mortar" have become poorer, not richer.
<br>
<br>
### "Yeah, but Milan..."
<button onclick="setChartParams('Milano', '2023')" class="inline-flex items-center px-2 py-1 border border-transparent text-xs font-medium rounded shadow-sm text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 ml-2 transition-all">
    👉 See Milan chart
</button>
<br>
If we look at the Milan chart, the blue line shoots upward. Those who bought got a great deal, right? Yes, but much less than it appears. Even in Italy's hottest market, inflation (especially post-2021) has "eaten" a huge chunk of that profit. The *real* gain is drastically lower than the *nominal* gain you read about in the papers.
<br>
<br>
Without even considering that an investment plays out over at least twenty years. How do you predict the property market of a place — indeed, of a neighbourhood — twenty years ahead?
<br>
<br>
And if we leave Milan and look at Rome or the South? The situation is dramatic: nominal prices flat or declining, and real prices plummeting.
<button onclick="setChartParams('Roma', '2023')" class="inline-flex items-center px-2 py-1 border border-transparent text-xs font-medium rounded shadow-sm text-white bg-red-600 hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 ml-2 transition-all">
    📉 See Rome
</button>
<br>
<br>
---

### Conclusions

I'm not saying you shouldn't buy a house or that there aren't situations — financial or personal — where it makes economic sense. Having a roof over your head is emotional security and a real convenience, but it's not automatically a "great investment." In fact, *imho*, it shouldn't really be considered an investment at all: **it's an expense**.
<br>
<br>
The next time someone tells you "I sold my house for the same price I bought it for 10 years ago, at least I didn't lose anything," show them the red line. In reality, inflation ate a quarter of their savings without them noticing. And that's without accounting for taxes and the property's loss of value over time (after 30 years, do we want to redo this roof?).
<br>
<br>
_There'd be a thousand other considerations to make: the usefulness of historical series for predicting the future, the idea of tying yourself hand and foot to a single asset..._

#### Sources
* **House Prices (IPAB):** ISTAT data on the House Price Index for dwellings purchased by households.
* **Inflation:** ISTAT data on the national consumer price index (NIC).
