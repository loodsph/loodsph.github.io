---
layout: post
title: "Reverse engineering gnocchi"
seo_title: "The chemistry of perfect gnocchi: potatoes, starch, and thermodynamics"
date: 2026-03-16 15:00:00 +0100
categories: [science, cooking]
tags: [chemistry, thermodynamics, food-science, gnocchi]
description: "A practical analysis of tradition to get the best out of it"
pixel_icon: "gnocchi.png"
smooth_image: true
lang: en
ref: gnocchi
---

There is a scene in *Ratatouille* that perfectly illustrates the [neurobiology of memory](https://loodsph.github.io/complexity/filosofia/psychology/2026/01/13/bugs-bunny.html). A simple dish that, in a fraction of a second, physically brings him back to his childhood kitchen. It's the [Proust effect](https://en.wikipedia.org/wiki/Proustian_memory), pure biochemistry.

For me, that trigger has the shape and texture of gnocchi.

And when I want to do something, I do the only thing I know how to do: I break it down into its fundamental chemical-physical components.

(disclaimer: this post will contain several mentions of potatoes, if you are under 8 years old you might find it amusing)

---
<br>
> I've screwed up enough to know how to cook my own peace of mind.

<img src="/assets/gnocchi2.jpg" alt="Gnocchi" style="border-radius: 16px; width: 100%;" />

Let's start:

The goal is to create a solid structure that withstands boiling, but instantly collapses as soon as it touches the palate.

### The thermodynamics of starch gelatinization

Why do we cook potatoes? To trigger a specific process: **starch gelatinization**.

Raw starch is organized into compact, crystalline granules (amylose and amylopectin) that are insoluble in cold water. As the temperature rises above 60-70°C, in the presence of water, the hydrogen bonds between these molecules weaken. Water penetrates the granules, which swell enormously until they burst, releasing amylose and forming a viscous network: the gel.

Here lies the trick with gnocchi: **we need water to gelatinize the starch, but we want the absolute bare minimum**.

I've always seen potatoes boiled in water (though it works just fine in **other** preparations), a recipe dating back to when cooking methods could be counted on the fingers of one hand. I remember the somewhat uncomposed reactions when I questioned this sacred dogma.

If we boil potatoes in water, the starch granules become saturated, explode, and create a watery glue. You will have to add tons of flour to dry the dough, resulting in rubber bullets.
The *endogenous* water (the one naturally contained inside the potato) is thermodynamically perfect and sufficient to gelatinize the starch to the right point, provided no additional water enters from the outside. That's why the microwave is the answer.

### Microwave physics: standing waves and operational protocol

The microwave heating method acts directly on the water molecules inside the potato. But a microwave oven does not heat uniformly.

Microwaves are electromagnetic radiation that bounce off the metal walls of the oven, overlapping. This creates a pattern of **standing waves**: there will be points where the waves add up (constructive interference) creating *hotspots* of maximum energy, and points where they cancel each other out (destructive interference) creating *coldspots* where the food does not heat up at all. The turntable helps, but it's not always enough. For example, whatever is placed in the center of the plate moves very little. [resource 1](https://www.youtube.com/watch?v=DKgVxLaTyVg) [resource 2](https://www.youtube.com/watch?v=SCFOqr9R-LY)

To overcome this problem, the cooking protocol for 1 kg of raw potatoes must be well-thought-out:

These are the settings that work **for me**:

* **Power and Time:** 12 minutes at 850W.
* **The Rotation:** At 6 minutes, open the door. Turn the potatoes upside down and swap their places (the ones in the center go to the edges, the ones on the edges go to the center). This "smears" the exposure to hotspots and coldspots over the entire surface, ensuring uniform gelatinization.

I don't really like cooking times, they make little sense. They vary greatly based on the size of the food (different exposed area and so on). So these are just rough guidelines.

The temperature at the center should be 93-95 °C, it will then continue to cook through "thermal inertia". <br>
<small>Without a thermometer: the potato is cooked more or less when a toothpick reaches the core without putting up too much resistance.</small>

The potatoes (strictly with the skin pierced with a fork or toothpick to create a release valve for expanding gases) must be placed **directly on the rotating glass plate of the microwave**.

Putting them in a bowl or container is a mistake for two reasons:

1. **The greenhouse effect:** The bowl traps the steam escaping from the holes in the skin. A steam chamber is created and you will end up "boiling" the outside of the potato in its own moisture. On the open turntable, however, the steam disperses.
2. **Thermal shielding:** Many thick ceramic or glass containers absorb some of the microwaves or act as a thermal mass, altering the 12 minutes of ballistic calculation we just made.

### Cooking after cooking (Thermal inertia)

When the microwave stops at 12 minutes, the cooking does not.
Exactly like a steak taken off the grill, the potato has accumulated heat. The center continues to cook via **carryover cooking** (*inerzia termica*). If you open or mash the potato immediately, the steam will violently escape, dropping the temperature suddenly. Let them rest for a few minutes outside the oven: the residual moisture will redistribute uniformly and the gelatinized cellular structure will stabilize.

After mashing the potatoes, it is a good idea to spread them out for a few minutes on the work surface before incorporating the flour. They will lose a little more water through evaporation. Additionally, keeping the potatoes below 70 °C prevents the starch in the flour from immediately gelling when it comes into contact with the puree.

<details markdown="1">
  <summary>Some chemistry nerdiness</summary>

Potato cells are held together by pectin, a biological glue. The reaction of pectin depends on the pH of the environment:

* **Acidic environment:** strengthens the pectin. Potatoes remain firm.
* **Basic (alkaline) environment:** breaks down pectin rapidly, turning the potato into a slimy mush.

The exclusive use of the microwave keeps the chemical environment of the potato perfectly neutral, allowing the pectin to yield structurally in the most correct way for processing.

There is a detail that can ruin everything, masterfully popularized by Dario Bressanini. In potatoes, there is an enzyme called **pectinesterase** (PME). Its thermal "comfort zone" is between 50°C and 70°C.

If the potato lingers in this temperature range, the enzyme activates and starts removing methyl groups from the pectin, allowing it to bind tenaciously to calcium ions. The result? A literal molecular "reinforced concrete" forms between the cells. The structure sets and becomes irreversibly firm. Great for potato salad, the death star for gnocchi.

And here the microwave proves once again to be the ultimate weapon. By heating the internal water rapidly and violently, the microwave "punches through" the 70°C danger zone in a very short time, reaching temperatures where **the enzyme is denatured** (destroyed by heat) before it has time to do structural damage.

If external water is the enemy, dry heat is the solution. Many traditional cooks use a static oven or cook under the ashes. Better than boiling? Absolutely yes. Ideal? No.

This is also why the traditional oven (or cooking under the ashes, which I love) are fine, but not the best.
The traditional oven cooks by convection (from the outside in) and takes almost an hour. This thermodynamic slowness causes two problems: it dehydrates the outer layers creating a thick, unusable crust, and makes the core of the potato linger for a long time in the enzymatic "danger zone."

Traditional recipes often include egg. In engineering terms, the egg is not an ingredient, it is a way to fix a structural bug.
Egg proteins coagulate at about 65°C, creating a rigid scaffold that "saves" the gnocco from falling apart in the pot (usually caused by using overly watery potatoes or kneading poorly). It works very well, but has a cost: it adds toughness and weight. If you use the microwave method, the egg is completely redundant and adds more water (90% of egg white is water), which undoes all the efforts made so far.
</details>

### The pot equation: Osmosis, Kinetics, and Thermal Shock

The boiling moment is the final structural test. The variables are three: **Water, Pasta, and Salt**. The classic Italian proportion is 1 liter of water, 100g of pasta, 10g of salt. For gnocchi, physics forces us to make some small adjustments.

* **The ban on salt in the dough (Osmosis):** **Never** salt the dough. Salt is hygroscopic: it literally pulls water out of the potato cells. Once the dough is salted, a countdown starts. After a few minutes, it will start to "weep," forcing you to use more flour. You only salt the water.
* **The thermal mass (The Shock):** 1 liter of water for every 100g of gnocchi is not a waste, it is a requirement for thermal stability. Gnocchi cook in 90-120 seconds (when they "float back to the top"). When you plunge a cold mass into boiling water, the temperature of the system plummets. If you have little water, it will take a minute to return to a boil. During that minute at 90°C, the gnocco does not cook, but begins to disintegrate, dispersing starch. You need a huge thermal mass (abundant boiling water) to absorb the thermal shock without stopping boiling.
* **Hacking the salt concentration (Kinetics):** Dry pasta cooks in 10-12 minutes, having plenty of time to absorb the 10g of salt dissolved in the liter of water. Gnocchi float (and therefore are cooked, as thermal expansion has reduced their density) in 1-2 minutes. The exposure time is minimal. If you haven't salted the dough to avoid ruining it, you must increase the concentration gradient in the water to flavor them in such a short time. Bring the salt to **12-15g per liter of water**.

### Cavities and Porosity

The purpose of "indenting with your fingers" (or other evil methods like the gnocchi board or the tines of a fork) is not just an aesthetic requirement:

1. **Heat exchange:** The grooves drastically increase the surface/volume ratio. This allows the cooking water to transfer heat more quickly to the core of the gnocco, reducing the time spent in the pot (which is the moment we risk collapse). A bit like how coarse salt takes longer to dissolve because the water has less surface area to come into contact with compared to fine salt and therefore works with more "effort."
2. **Porosity:** The ridges act as micro-channels that alter the surface tension of the sauce, trapping it by capillarity. A smooth gnocco literally lets the condiment slide off due to reduced viscous friction (which is why those indented on a wooden board taste better). Exactly what happens with smooth and ridged penne pasta.

### Flour and the time variable (T)

Flour serves only as a binder, not as structure. Wheat contains gliadin and glutenin, which form **gluten** with water. Use a **weak 00 flour** (under 9% protein) to minimize this reaction.
And above all: the kneading must be **fast and brutal**. As soon as the flour is absorbed, stop. The less you touch it, the less strength you give the gluten network through mechanical action, the more the gnocco will melt in your mouth. (The amount of flour is indicated in the simulator at the bottom)

### The hardware: choosing the potato

All this engineering collapses if you get the starting material wrong. You need **old, white-fleshed potatoes** or floury varieties. Old potatoes have naturally lost moisture during storage. The drier and more starch-dense the base ingredient, the less flour you will have to add, triggering a virtuous cycle toward the perfect texture.

---
<br>
Let's go back to Anton Ego.
If we want to be precise, what bypassed his defenses was not a miracle of love fallen from the sky, but a Confit Byaldi: a deconstructed and meticulously redesigned version of the traditional recipe, calculated to optimize the thermodynamics of flavor.

Rigor, method, and physics are not sad ends in themselves: they are the only reliable tool we have to hack and reproduce an emotion on command.

Methodical cooking means replacing hope with understanding.

---

### The Simulator

To understand how interconnected the variables we talked about are, I wrote a predictive model. Play with the parameters below. You will immediately notice how the initial error (using a watery potato or letting it sit in boiling water too long) forces you to add flour and knead more, triggering a chain reaction that destroys the final structure by increasing the gluten load and mechanical damage to the starch.

The percentage of ingredients refers to the weight of the **cooked** potatoes. Microwave cooking causes them to lose some water (typically 20%). Therefore, potatoes should be weighed peeled **after** cooking.

<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600;700;800&family=DM+Sans:wght@400;500;600;700&display=swap">

<style>
    #gnocco-sim {
        --gs-bg: #0c0e12;
        --gs-panel: #13161c;
        --gs-border: #1e2230;
        --gs-border-light: #2a2f40;
        --gs-text: #c8cdd8;
        --gs-text-dim: #5a6178;
        --gs-text-bright: #eef0f5;
        --gs-accent: #3b82f6;
        --gs-green: #22d67a;
        --gs-yellow: #eab308;
        --gs-orange: #f97316;
        --gs-red: #ef4444;
        --gs-mono: 'JetBrains Mono', monospace;
        --gs-sans: 'DM Sans', sans-serif;
    }

    #gnocco-sim * { box-sizing: border-box; margin: 0; padding: 0; }

    #gnocco-sim {
        background: var(--gs-bg);
        color: var(--gs-text);
        border-radius: 16px;
        border: 1px solid var(--gs-border);
        font-family: var(--gs-sans);
        overflow: hidden;
        max-width: 780px;
        margin: 2.5rem auto;
    }

    /* ---- Header ---- */
    #gnocco-sim .gs-header {
        padding: 20px 24px 16px;
        border-bottom: 1px solid var(--gs-border);
        display: flex;
        align-items: center;
        gap: 12px;
    }
    #gnocco-sim .gs-header-text h3 {
        font-size: 15px;
        font-weight: 700;
        color: var(--gs-text-bright);
        letter-spacing: -0.01em;
        line-height: 1.3;
    }
    #gnocco-sim .gs-header-text p {
        font-size: 12px;
        color: var(--gs-text-dim);
        margin-top: 2px;
        line-height: 1.4;
    }

    /* ---- Body ---- */
    #gnocco-sim .gs-body {
        padding: 24px;
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 20px;
    }
    @media (max-width: 640px) {
        #gnocco-sim .gs-body { grid-template-columns: 1fr; }
    }

    /* ---- Controls ---- */
    #gnocco-sim .gs-controls {
        display: flex;
        flex-direction: column;
        gap: 18px;
    }

    #gnocco-sim .gs-field label {
        display: block;
        font-size: 10px;
        font-weight: 600;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--gs-text-dim);
        margin-bottom: 6px;
        line-height: 1.4;
    }
    #gnocco-sim .gs-field label .gs-val {
        font-family: var(--gs-mono);
        color: var(--gs-accent);
        font-weight: 700;
        font-size: 11px;
    }
    #gnocco-sim .gs-field label .gs-unit {
        color: var(--gs-text-dim);
    }

    #gnocco-sim select {
        width: 100%;
        padding: 8px 32px 8px 10px;
        background: var(--gs-panel);
        border: 1px solid var(--gs-border-light);
        border-radius: 8px;
        color: var(--gs-text-bright);
        font-family: var(--gs-sans);
        font-size: 13px;
        font-weight: 500;
        outline: none;
        transition: border-color 0.2s;
        appearance: none;
        -webkit-appearance: none;
        background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' fill='%235a6178' viewBox='0 0 16 16'%3E%3Cpath d='M8 11L3 6h10z'/%3E%3C/svg%3E");
        background-repeat: no-repeat;
        background-position: right 10px center;
        cursor: pointer;
    }
    #gnocco-sim select:hover,
    #gnocco-sim select:focus { border-color: var(--gs-accent); }

    /* Range */
    #gnocco-sim input[type="range"] {
        -webkit-appearance: none;
        appearance: none;
        width: 100%;
        height: 6px;
        background: var(--gs-border-light);
        border-radius: 3px;
        outline: none;
        cursor: pointer;
    }
    #gnocco-sim input[type="range"]::-webkit-slider-thumb {
        -webkit-appearance: none;
        width: 16px; height: 16px;
        background: var(--gs-text-bright);
        border-radius: 50%;
        border: 2.5px solid var(--gs-accent);
        cursor: pointer;
        transition: transform 0.15s, box-shadow 0.15s;
    }
    #gnocco-sim input[type="range"]::-webkit-slider-thumb:hover {
        transform: scale(1.2);
        box-shadow: 0 0 0 5px rgba(59,130,246,0.15);
    }
    #gnocco-sim input[type="range"]::-moz-range-thumb {
        width: 16px; height: 16px;
        background: var(--gs-text-bright);
        border-radius: 50%;
        border: 2.5px solid var(--gs-accent);
        cursor: pointer;
    }

    #gnocco-sim .gs-hint {
        font-size: 10px;
        font-family: var(--gs-mono);
        color: var(--gs-text-dim);
        margin-top: 5px;
        transition: color 0.2s;
    }
    #gnocco-sim .gs-hint.gs-warn { color: var(--gs-red); }
    #gnocco-sim .gs-hint.gs-ok { color: var(--gs-green); }

    /* ---- Output Panel ---- */
    #gnocco-sim .gs-output {
        background: var(--gs-panel);
        border: 1px solid var(--gs-border);
        border-radius: 12px;
        padding: 20px;
        display: flex;
        flex-direction: column;
    }

    #gnocco-sim .gs-output-label {
        font-size: 10px;
        font-weight: 600;
        text-transform: uppercase;
        letter-spacing: 0.1em;
        color: var(--gs-text-dim);
        text-align: center;
        margin-bottom: 20px;
    }

    /* Score */
    #gnocco-sim .gs-readout {
        text-align: center;
        margin-bottom: 20px;
    }
    #gnocco-sim .gs-score {
        font-family: var(--gs-mono);
        font-size: 52px;
        font-weight: 800;
        line-height: 1;
        color: var(--gs-green);
        transition: color 0.3s;
    }
    #gnocco-sim .gs-score-unit {
        font-family: var(--gs-mono);
        font-size: 18px;
        font-weight: 400;
        color: var(--gs-text-dim);
        margin-left: 2px;
    }
    #gnocco-sim .gs-verdict {
        margin-top: 10px;
        font-size: 12px;
        font-weight: 500;
        line-height: 1.5;
        min-height: 36px;
        color: var(--gs-green);
        transition: color 0.3s;
    }

    /* Gauge */
    #gnocco-sim .gs-gauge-wrap {
        margin-bottom: 6px;
    }
    #gnocco-sim .gs-gauge {
        position: relative;
        width: 100%;
        height: 6px;
        background: var(--gs-border-light);
        border-radius: 3px;
        overflow: visible;
    }
    #gnocco-sim .gs-gauge-fill {
        position: absolute;
        top: 0; left: 0;
        height: 100%;
        border-radius: 3px;
        transition: width 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94), background 0.3s;
        min-width: 3px;
    }
    #gnocco-sim .gs-gauge-marker {
        position: absolute;
        top: -3px;
        left: 20%;
        width: 1.5px;
        height: 12px;
        background: var(--gs-green);
        border-radius: 1px;
        opacity: 0.4;
    }
    #gnocco-sim .gs-gauge-labels {
        display: flex;
        justify-content: space-between;
        font-size: 9px;
        font-weight: 600;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--gs-text-dim);
        margin-top: 6px;
    }

    /* Diagnostics */
    #gnocco-sim .gs-diag {
        margin-top: auto;
        padding-top: 14px;
        border-top: 1px solid var(--gs-border);
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 8px 20px;
    }
    #gnocco-sim .gs-diag-item {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    #gnocco-sim .gs-diag-item .gs-dl {
        font-size: 10px;
        color: var(--gs-text-dim);
    }
    #gnocco-sim .gs-diag-item .gs-dv {
        font-family: var(--gs-mono);
        font-size: 11px;
        font-weight: 600;
        color: var(--gs-text);
    }
</style>

<div id="gnocco-sim">
    <div class="gs-header">
        <div class="gs-header-text">
            <h3>Structural Degradation Index</h3>
            <p>Predictive model based on the physico-chemical variables of the dough.</p>
        </div>
    </div>

    <div class="gs-body">
        <div class="gs-controls">
            <div class="gs-field">
                <label>Raw material</label>
                <select id="sim-patata">
                    <option value="1">Old white potato — ideal</option>
                    <option value="2">Yellow potato — average</option>
                    <option value="4">New potato — critical</option>
                </select>
            </div>

            <div class="gs-field">
                <label>Cooking method</label>
                <select id="sim-cottura">
                    <option value="0.5">Microwave — dehydration</option>
                    <option value="1.5">Oven / Steam — neutral</option>
                    <option value="3">Boiling — saturation</option>
                </select>
            </div>

            <div class="gs-field">
                <label>Added flour · <span class="gs-val" id="val-farina">20</span><span class="gs-unit">% weight</span></label>
                <input type="range" id="sim-farina" min="10" max="60" value="20">
                <div class="gs-hint" id="farina-hint">min. required: ~15%</div>
            </div>

            <div class="gs-field">
                <label>Kneading time · <span class="gs-val" id="val-tempo">2</span><span class="gs-unit"> min</span></label>
                <input type="range" id="sim-tempo" min="1" max="15" value="2">
                <div class="gs-hint">gluten + starch damage ∝ 1 − e<sup style="font-size:9px">−t/τ</sup></div>
            </div>
        </div>

        <div class="gs-output">
            <div class="gs-output-label">Structural Output</div>

            <div class="gs-readout">
                <span class="gs-score" id="sim-score">20</span><span class="gs-score-unit">/100</span>
                <p class="gs-verdict" id="sim-feedback">Perfect thermodynamic balance. They will melt in your mouth.</p>
            </div>

            <div class="gs-gauge-wrap">
                <div class="gs-gauge">
                    <div class="gs-gauge-fill" id="sim-bar" style="width:20%; background:#22d67a;"></div>
                    <div class="gs-gauge-marker"></div>
                </div>
                <div class="gs-gauge-labels">
                    <span>Cloud</span>
                    <span>Bullet</span>
                </div>
            </div>

            <div class="gs-diag">
                <div class="gs-diag-item"><span class="gs-dl">H₂O load</span><span class="gs-dv" id="bd-water">0.5</span></div>
                <div class="gs-diag-item"><span class="gs-dl">Min. flour</span><span class="gs-dv" id="bd-minflour">~15%</span></div>
                <div class="gs-diag-item"><span class="gs-dl">Flour burden</span><span class="gs-dv" id="bd-burden">+4</span></div>
                <div class="gs-diag-item"><span class="gs-dl">Surplus → gluten</span><span class="gs-dv" id="bd-surplus">+5%</span></div>
                <div class="gs-diag-item"><span class="gs-dl">Gluten σ(t)</span><span class="gs-dv" id="bd-gluten">39%</span></div>
                <div class="gs-diag-item"><span class="gs-dl">Starch damage</span><span class="gs-dv" id="bd-starch">+1</span></div>
            </div>
        </div>
    </div>
</div>

<script>
document.addEventListener('DOMContentLoaded', () => {
    const el = id => document.getElementById(id);
    const inputPatata  = el('sim-patata');
    const inputCottura = el('sim-cottura');
    const inputFarina  = el('sim-farina');
    const inputTempo   = el('sim-tempo');
    const valFarina    = el('val-farina');
    const valTempo     = el('val-tempo');
    const bar          = el('sim-bar');
    const scoreDisplay = el('sim-score');
    const feedback     = el('sim-feedback');
    const farinaHint   = el('farina-hint');
    const bdWater      = el('bd-water');
    const bdMinFlour   = el('bd-minflour');
    const bdSurplus    = el('bd-surplus');
    const bdGluten     = el('bd-gluten');
    const bdStarch     = el('bd-starch');
    const bdBurden     = el('bd-burden');

    const C = { green:'#22d67a', yellow:'#eab308', orange:'#f97316', red:'#ef4444', blue:'#3b82f6' };

    // Ideal flour threshold: ~15% (old potato in microwave)
    const IDEAL_FLOUR = 15;

    function calc() {
        const pF = parseFloat(inputPatata.value);
        const cF = parseFloat(inputCottura.value);
        const fV = parseInt(inputFarina.value);
        const tV = parseInt(inputTempo.value);

        valFarina.innerText = fV;
        valTempo.innerText  = tV;

        const waterLoad = pF * cF;
        const minFlour  = Math.round(10 + waterLoad * 4);
        const isLiquid  = fV < minFlour;
        const surplus   = Math.max(0, fV - minFlour);

        // ── Contribution 1: Base water load (non-linear) ──
        // waterLoad^1.3 penalizes extreme values (6, 12) more
        // compared to previous linear version
        const waterContrib = Math.pow(waterLoad, 1.3) * 1.2;

        // ── Contribution 2: Mass of flour burden ──
        // All flour above the ideal ~15% adds mass, density
        // and heaviness to the gnocco, EVEN if it is "necessary" for the
        // water load. This is the cost of the chain reaction:
        // wrong potato → wrong cooking → too much water →
        // too much forced flour → dense and heavy gnocco.
        const flourBurden = Math.max(0, fV - IDEAL_FLOUR) * 0.8;

        // ── Contribution 3: Gluten development (surplus × time) ──
        // Only the flour OVER the structural minimum contributes
        // to the development of the gluten network.
        // τ₁ = 4 min
        const sigmaGluten   = 1 - Math.exp(-tV / 4);
        const glutenContrib = surplus * sigmaGluten * 1.4;

        // ── Contribution 4: Mechanical damage to starch granules ──
        // Depends ONLY on time, independent of flour.
        // τ₂ = 5 min, k = 15
        const sigmaStarch   = 1 - Math.exp(-tV / 5);
        const starchDamage  = 15 * sigmaStarch;

        // ── Composite Score ──
        let score = waterContrib + flourBurden + glutenContrib + starchDamage;
        score = Math.min(100, Math.max(0, Math.round(score)));

        // ── Diagnostics ──
        bdWater.innerText    = waterLoad.toFixed(1);
        bdMinFlour.innerText = `~${minFlour}%`;
        bdBurden.innerText   = isLiquid ? '—' : `+${Math.round(flourBurden)}`;
        bdSurplus.innerText  = isLiquid ? '—' : (surplus > 0 ? `+${surplus}%` : '0');
        bdGluten.innerText   = isLiquid ? '—' : `${Math.round(sigmaGluten * 100)}%`;
        bdStarch.innerText   = isLiquid ? '—' : `+${Math.round(starchDamage)}`;

        // ── Flour Hint ──
        farinaHint.innerText = isLiquid
            ? `⚠ you need ≥${minFlour}% for H₂O ${waterLoad.toFixed(1)}`
            : fV <= IDEAL_FLOUR
                ? `~${IDEAL_FLOUR}% ideal ✓`
                : `+${fV - IDEAL_FLOUR}% above ideal → mass and density`;
        farinaHint.className = 'gs-hint' + (isLiquid ? ' gs-warn' : fV <= IDEAL_FLOUR ? ' gs-ok' : '');

        // ── UI ──
        if (isLiquid) {
            bar.style.width = '100%';
            bar.style.background = `repeating-linear-gradient(120deg, ${C.blue}22, ${C.blue}44 6px, ${C.blue}22 12px)`;
            scoreDisplay.innerText = 'ERR';
            scoreDisplay.style.color = C.blue;
            feedback.innerText = `Impossible dough. You need ≥${minFlour}% flour for this water load.`;
            feedback.style.color = C.blue;
        } else {
            bar.style.width = `${Math.max(3, score)}%`;

            // Identify the dominant mechanism for feedback
            const dominant = Math.max(flourBurden, glutenContrib, starchDamage);
            const domType = dominant === flourBurden ? 'burden'
                          : dominant === glutenContrib ? 'gluten' : 'starch';

            let c, msg;
            if (score < 20) {
                c = C.green;
                msg = 'Perfect thermodynamic balance. They will melt in your mouth.';
            } else if (score < 45) {
                c = C.yellow;
                msg = domType === 'burden'  ? 'Acceptable structure, but the mass of flour is heavy.'
                    : domType === 'gluten'  ? 'Acceptable structure. The gluten network is noticeable.'
                    :                         'Acceptable structure. Slight mechanical damage to the granules.';
            } else if (score < 70) {
                c = C.orange;
                msg = domType === 'burden'  ? 'Too much flour. Dense and heavy like river stones.'
                    : domType === 'gluten'  ? 'Gluten network out of control. Chewy and heavy.'
                    :                         'Free amylose due to over-kneading. Sticky texture.';
            } else {
                c = C.red;
                msg = 'Pure ballistics. Excellent for shooting with a slingshot.';
            }
            bar.style.background   = c;
            scoreDisplay.innerText = score;
            scoreDisplay.style.color = c;
            feedback.innerText     = msg;
            feedback.style.color   = c;
        }
    }

    inputPatata.addEventListener('change', calc);
    inputCottura.addEventListener('change', calc);
    inputFarina.addEventListener('input', calc);
    inputTempo.addEventListener('input', calc);
    calc();
});
</script>